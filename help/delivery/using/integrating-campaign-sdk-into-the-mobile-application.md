---
product: campaign
title: Integrera Campaign SDK
description: Lär dig hur du integrerar Campaign SDK med din mobilapp
feature: Mobile SDK Integration, Push
role: User, Developer
hide: true
hidefromtoc: true
exl-id: a5f6b82d-5561-4e56-b2ed-7fd6fd8c2b55
source-git-commit: 81b47231b027a189bc8b9029b7d48939734d08ed
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 0%

---

# Integrera Campaign SDK med er app {#integrating-campaign-sdk-into-the-mobile-application}

>[!CAUTION]
>
>Adobe rekommenderar att du använder Adobe Experience Platform Mobile SDK genom att konfigurera Adobe Campaign-tillägget i användargränssnittet för datainsamling. Adobe Experience Platform Mobile SDK hjälper er att driva lösningar och tjänster från Adobe Experience Cloud i era mobilappar. SDK-konfigurationen hanteras via användargränssnittet för datainsamling för flexibel konfiguration och utbyggbara, regelbaserade integreringar. [Läs mer i Adobe Developer-dokumentationen](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic){target="_blank"}.

Om du vill hämta Campaign SDK (tidigare kallat Neolane SDK) kontaktar du [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.

Mer information om vilka olika Android- och iOS-versioner som stöds finns i [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md#MobileSDK).

Du hittar stegen under integreringen för Campaign SDK.

+++**Läser in kampanj-SDK**

* **I Android**: **neolane_sdk-release.aar** filen måste vara länkad till projektet.

  Följande behörighet ger åtkomst till Adobe Campaign-servern:

  ```
  Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
  Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
  Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/");
  ```

  Med följande behörighet kan du återställa en mobils unika ID:

  ```
  <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
  ```

  Från och med version 1.0.24 av SDK används den här behörigheten endast för versioner äldre än Android 6.0.

  Från och med version 1.0.26 av SDK används inte längre den här behörigheten.

* **I IOS**: **libNeolaneSDK.a** och **Neolane_SDK.h** filer måste länkas till projektet. Från version 1.0.24 av SDK, alternativet **ENABLE_BITCODE** är aktiverat.

  >[!NOTE]
  >
  >De fyra arkitekturerna finns i **Neolane_SDK.h** -fil.

+++

+++**Deklarera integrationsinställningar**

För att integrera Campaign SDK i mobilappen måste den funktionella administratören lämna följande information till utvecklaren:

* **En integreringsnyckel**: för att Adobe Campaign-plattformen ska kunna identifiera mobilapplikationen.

  >[!NOTE]
  >
  >Integreringsnyckeln anges i Adobe Campaign-konsolen i **[!UICONTROL Information]** fliken med tjänster som är dedikerade till mobilprogrammet. Se [Konfigurera ett mobilprogram i Adobe Campaign](configuring-the-mobile-application.md).

* **En spårnings-URL**: som matchar adressen för Adobe Campaign spårningsserver.
* **En marknadsförings-URL**: för att aktivera insamling av prenumerationer.

* **I Android**:

  ```
  Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
  Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
  Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/"); 
  ```

* **I IOS**:

  ```
  Neolane_SDK *nl = [Neolane_SDK getInstance];
  [nl setMarketingHost:strMktHost];
  [nl setTrackingHost:strTckHost];
  [nl setIntegrationKey:strIntegrationKey];
  ```

+++

+++**Registreringsfunktion**

Med registreringsfunktionen kan du:

* skicka meddelande-ID eller push-ID (deviceToken för iOS och registrationID för Android) till Adobe Campaign.
* återskapa avstämningsnyckeln eller userKey (till exempel e-post eller kontonummer)

* **I Android**:

  ```
  void registerInNeolane(String registrationId, String userKey, Context context)
  {
   try{
    Neolane.getInstance().registerDevice(registrationToken, userKey, null, context);
   } catch (NeolaneException e){
    //...
   } catch (IOException e){
    //...
   }
  }
  ```

  Om du använder FCM (Firebase Cloud Messaging) rekommenderar vi att du använder **registerDevice** funktionen vid anrop av **onTokenRefresh** för att meddela Adobe Campaign om ändringen i användarens mobilenhetstoken.

  ```
  public class NeoTripFirebaseInstanceIDService extends FirebaseInstanceIdService {
    @Override
    public void onTokenRefresh() {
      String registrationToken = FirebaseInstanceId.getInstance().getToken();
      NeolaneAsyncRunner neolaneAs = new NeolaneAsyncRunner(Neolane.getInstance());
      ...
      ...
      // Neolane Registration
      neolaneAs.registerDevice(registrationToken, userKey, additionnalParam, this, new NeolaneAsyncRunner.RequestListener() {
      public void onComplete(String e, Object state) { ... }
      public void onNeolaneException(NeolaneException e, Object state) { ... }
      public void onIOException(IOException e, Object state) { ... }
      });
      ...
      ...
    }
  }
  ```

* **I IOS**:

  ```
  // Callback called on successful registration to the APNs
  - (void)application:(UIApplication*)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData*)deviceToken
  {
      // Pass the token to Adobe Campaign
      Neolane_SDK *nl = [Neolane_SDK getInstance];
      [nl registerDevice:tokenString:self.userKey:dic];
  }
  ```

+++

+++**Spårningsfunktion**

* **I Android**:

  Med spårningsfunktionerna kan du spåra meddelandeaktiveringar (öppnar) och meddelandeskärmar (skärmbild).

  Spåra visningen av meddelanden (klart genom att anropa **notifyReceive** SDK:s funktion), följ implementeringen nedan. Observera att om du använder FCM (Firebase Cloud Messaging) rekommenderar vi att du använder **notifyReceive** funktionen när **onMessageReceived** -funktionen anropas av Android-systemet.

  ```
  package com.android.YourApplication;
  
  import android.content.Context;
  import android.content.SharedPreferences;
  import android.os.Bundle;
  import android.util.Log;
  
  import com.google.firebase.messaging.FirebaseMessagingService;
  import com.google.firebase.messaging.RemoteMessage;
  
  import java.util.Iterator;
  import java.util.Map;
  import java.util.Map.Entry;
  
  public class YourApplicationFirebaseMessagingService extends FirebaseMessagingService {
    private static final String TAG = "MyFirebaseMsgService";
  
    @Override
    public void onMessageReceived(RemoteMessage message) {
      Log.d(TAG, "Receive message from: " + message.getFrom());
      Map<String,String> payloadData = message.getData();
      final Bundle extras = new Bundle();
      final Iterator<Entry<String, String>> iter = payloadData.entrySet().iterator();
      while(iter.hasNext())
      {
        final Entry<String, String>  entry =iter.next();
        extras.putString(entry.getKey(), entry.getValue());
      }
  
      SharedPreferences settings = this.getSharedPreferences(YourApplicationActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
      String mesg = payloadData.get("_msg");
      String title = payloadData.get("title");
      String url = payloadData.get("url");
      String messageId = payloadData.get("_mId");
      String deliveryId = payloadData.get("_dId");
      YourApplicationActivity.handleNotification(this, mesg, title, url, messageId, deliveryId, extras);
    }
  }
  ```

  ```
  public static void handleNotification(Context context, String message, String title, String url, String messageId, String deliveryId, Bundle extras){
      if( message == null ) message = "No Content";
      if( title == null )   title = "No title";
      if( url == null )     url = "https://www.tripadvisor.fr";
      int iconId = R.drawable.notif_neotrip;
  
    // notify Neolane that a notification just arrived
    SharedPreferences settings = context.getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
    Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
    Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));
    Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
  
    NeolaneAsyncRunner nas = new NeolaneAsyncRunner(Neolane.getInstance());
    nas.notifyReceive(Integer.valueOf(messageId), deliveryId, new NeolaneAsyncRunner.RequestListener() {
      public void onNeolaneException(NeolaneException arg0, Object arg1) {}
      public void onIOException(IOException arg0, Object arg1) {}
      public void onComplete(String arg0, Object arg1){}
    });
    if (yourApplication.isActivityVisible())
      {
        Log.i("INFO", "The application has the focus" );
        ...
      }
      else
      {
        // notification creation :
        NotificationManager notificationManager = (NotificationManager) context.getSystemService(Context.NOTIFICATION_SERVICE);
        Notification notification;
  
        // Activity to start :
        Intent notifIntent = new Intent(context.getApplicationContext(), NotificationActivity.class);
        notifIntent.putExtra("notificationText", message);
        notifIntent.putExtra(NotificationActivity.NOTIFICATION_URL_KEYNAME, url);
        notifIntent.putExtra("_dId", deliveryId);
        notifIntent.putExtra("_mId", messageId);
        notifIntent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
        PendingIntent contentIntent = PendingIntent.getActivity(context, 1, notifIntent, PendingIntent.FLAG_UPDATE_CURRENT);
  
        notification = new Notification.Builder(context)
                .setContentTitle(title)
                .setContentText(message)
                .setSmallIcon(iconId)
                .setContentIntent(contentIntent)
                .build();
  
        // launch the notification :
        notification.flags |= Notification.FLAG_AUTO_CANCEL;
        notificationManager.notify(Integer.valueOf(messageId), notification);
      }
  }
  ```

  Här är ett implementeringsexempel för att spåra ett meddelande som är öppet (som körs genom att anropa **notifyOpening** SDK:s funktion). The **NotificationActivity** motsvarar den som används för att skapa **notifIntent** i föregående exempel.

  ```
  public class NotificationActivity extends Activity {
  public void onCreate(Bundle savedBundle) {
    [...]
    Bundle extra = getIntent().getExtras();
    if (extra != null) {
      // reinit the acc sdk
      SharedPreferences settings = getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
      Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
      Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));               
      Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
  
      // Get the messageId and the deliveryId to do the tracking
      String deliveryId = extra.getString("_dId");
      String messageId = extra.getString("_mId");
      if (deliveryId != null && messageId != null) {
        try {
          Neolane.getInstance().notifyOpening(Integer.valueOf(messageId), Integer.valueOf(deliveryId));
        } catch (NeolaneException e) {
          // ...
        } catch (IOException e) {
          // ...
        }
      }
    }
   }
  }
  ```

* **I IOS**:

  Med spårningsfunktionen kan du spåra när meddelanden aktiveras (öppnas).

  ```
  (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
  fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
  {
  if( launchOptions ) { // Retrieve notification parameters here ... // Track application opening Neolane_SDK
  *nl = [Neolane_SDK getInstance]; [nl track:launchOptions:NL_TRACK_CLICK]; } 
  ...  
  completionHandler(UIBackgroundFetchResultNoData);
  }
  ```

  >[!NOTE]
  >
  >Från version 7.0, en gång **`application:didReceiveRemoteNotification:fetchCompletionHandler`** -funktionen är implementerad och operativsystemet anropar bara den här funktionen. The **`application:didReceiveRemoteNotification`** funktionen anropas därför inte.

+++

+++**Spårning av tyst meddelande**

Med iOS kan du skicka tysta meddelanden, ett meddelande eller data som skickas direkt till ett mobilprogram utan att det visas. Med Adobe Campaign kan du spåra dem.

Följ exemplet nedan för att spåra ditt tysta meddelande:

```
// AppDelegate.m
...
...
#import "AppDelegate.h"
#import "Neolane_SDK.h"
...
...
// Callback called when the application is already launched (whether the application is running foreground or background)
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
{
 NSLog(@"IN didReceiveRemoteNotification:fetchCompletionHandler");
 if (launchOptions) NSLog(@"IN launchOptions: %@", [launchOptions description]);
 NSLog(@"Application state: %ld", (long)application.applicationState);

 // Silent Notification (specific case, can use NL_TRACK_RECEIVE as the user doesn't have click/open the notification)
 if ([launchOptions[@"aps"][@"content-available"] intValue] == 1 )
       {
  NSLog(@"Silent Push Notification");
  ...  
  ...
  //Call receive tracking
        Neolane_SDK *nl = [Neolane_SDK getInstance];
  [nl track:launchOptions:NL_TRACK_RECEIVE];

  completionHandler(UIBackgroundFetchResultNoData); //Do not show notification
  return;
 }  
 ...
 ...
        completionHandler(UIBackgroundFetchResultNoData);
}
```

+++

+++**RegisterDeviceStatus-delegat**

>[!NOTE]
>
>Observera att detta endast gäller iOS.

I iOS kan du med delegatprotokollet få resultatet av **registerDevice** anrop och kan användas för att ta reda på om ett fel uppstod under registreringen.

The **registerDeviceStatus** prototypen är:

```
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status:(NSString *) errorReason;
```

**Status** gör att du kan ta reda på om en registrering lyckades eller om ett fel uppstod.

**ErrorReason** innehåller mer information om felen. Mer information om tillgängliga fel och deras beskrivningar finns i tabellen nedan.

<table> 
 <thead>
  <tr>
   <th> Status<br /> </th>
   <th> Beskrivning<br /> </th>
   <th> ErrorReason<br /> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td> ACCRegisterDeviceStatusSuccess <br /> </td>
   <td> Registreringen lyckades<br /> </td>
   <td> TOM<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty <br /> </td>
   <td> Värdnamnet för ACC-marknadsföringsservern är tomt eller har inte angetts.<br /> </td>
   <td> TOM<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureIntegrationKeyEmpty <br /> </td>
   <td> Integreringsnyckeln är tom eller inte inställd.<br /> </td>
   <td> TOM<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureConnectionIssue<br /> </td>
   <td> Anslutningsproblem med ACC<br /> </td>
   <td> Mer information (på operativsystemets aktuella språk)<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnknownUUID<br /> </td>
   <td> Angivet UUID (integrationsnyckel) är okänt.<br /> </td>
   <td> TOM<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnexpectedError<br /> </td>
   <td> Ett oväntat fel returnerades till ACC-servern.<br /> </td>
   <td> Felmeddelandet returnerades till ACC.<br /> </td>
  </tr>
 </tbody>
</table>

**Neolane_SDKDelegate** protokoll och **registerDeviceStatus** Delegatdefinitionen är följande:

```
//  Neolane_SDK.h
//  Neolane SDK
..
.. 
// Register Device Status Enum
typedef NS_ENUM(NSUInteger, ACCRegisterDeviceStatus) {
 ACCRegisterDeviceStatusSuccess,                               // Resistration Succeed
 ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty,   // The ACC marketing server hostname is Empty or not set
 ACCRegisterDeviceStatusFailureIntegrationKeyEmpty,            // The integration key is empty or not set
 ACCRegisterDeviceStatusFailureConnectionIssue,                // Connection issue with ACC, more information in errorReason
 ACCRegisterDeviceStatusFailureUnknownUUID,                    // The provided UUID (integration key) is unknown
 ACCRegisterDeviceStatusFailureUnexpectedError                 // Unexpected error returned by ACC server, more information in errorReason
};
// define the protocol for the registerDeviceStatus delegate
@protocol Neolane_SDKDelegate <NSObject>
@optional
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason;
@end
@interface Neolane_SDK: NSObject {
} 
...
...
// registerDeviceStatus delegate
@property (nonatomic, weak) id <Neolane_SDKDelegate> delegate;
...
...
@end
```

Att implementera **registerDeviceStatus** delegat, följ dessa steg:

1. Implementera **setDelegate** under SDK-initieringen.

   ```
   // AppDelegate.m
   ...
   ... 
   - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
   {
   ...
   ...
    // Get the stored settings
   
    NSUserDefaults *defaults = [NSUserDefaults standardUserDefaults];
    NSString *strMktHost = [defaults objectForKey:@"mktHost"];
    NSString *strTckHost = [defaults objectForKey:@"tckHost"];
    NSString *strIntegrationKey = [defaults objectForKey:@"integrationKey"];
    userKey = [defaults objectForKey:@"userKey"];
   
    // Configure Neolane SDK on first launch
    Neolane_SDK *nl = [Neolane_SDK getInstance];
    [nl setMarketingHost:strMktHost];
    [nl setTrackingHost:strTckHost];
    [nl setIntegrationKey:strIntegrationKey];
    [nl setDelegate:self];    // HERE
   ...
   ...
   }
   ```

1. Lägg till protokollet i **@interface** av din klass.

   ```
   //  AppDelegate.h
   
   #import <UIKit/UIKit.h>
   #import <CoreLocation/CoreLocation.h>
   #import "Neolane_SDK.h"
   
   @class LandingPageViewController;
   
   @interface AppDelegate : UIResponder <UIApplicationDelegate, CLLocationManagerDelegate, Neolane_SDKDelegate> {
       CLLocationManager *locationManager;
       NSString *userKey;
       NSString *mktServerUrl;
       NSString *tckServerUrl;
       NSString *homeURL;
       NSString *strLandingPageUrl;
       NSTimer *timer;
   }
   ```

1. Implementera delegaten i **AppDelegate**.

   ```
   //  AppDelegate.m
   
   #import "AppDelegate.h"
   #import "Neolane_SDK.h"
   #import "LandingPageViewController.h"
   #import "RootViewController.h"
   ...
   ...
   - (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason
   {
       NSLog(@"registerStatus: %lu",status);
   
       if ( errorReason != nil )
           NSLog(@"errorReason: %@",errorReason);
   
       if( status == ACCRegisterDeviceStatusSuccess )
       {
           // Registration successful
           ...
           ...
       }
       else { // An error occurred
           NSString *message;
           switch ( status ){
               case ACCRegisterDeviceStatusFailureUnknownUUID:
                   message = @"Unkown IntegrationKey (UUID)";
                   break;
               case ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty:
                   message = @"Marketing URL not set or Empty";
                   break;
               case ACCRegisterDeviceStatusFailureIntegrationKeyEmpty:
                   message = @"Integration Key not set or empty";
                   break;
               case ACCRegisterDeviceStatusFailureConnectionIssue:
                   message = [NSString stringWithFormat:@"%@ %@",@"Connection issue:",errorReason];
                   break;
               case ACCRegisterDeviceStatusFailureUnexpectedError:
               default:
                   message = [NSString stringWithFormat:@"%@ %@",@"Unexpected Error",errorReason];
                   break;
           }
    ...
    ...
       }
   }
   @end
   ```

+++

+++**Variabel**

Med variablerna kan du definiera mobilprogrammets beteende efter att ha tagit emot ett meddelande. Dessa variabler måste definieras i mobilprogramkoden och i Adobe Campaign-konsolen i **[!UICONTROL Variables]** i det dedikerade mobilprogrammet (se [Konfigurera ett mobilprogram i Adobe Campaign](configuring-the-mobile-application.md)). Här är ett exempel på en kod som gör att ett mobilprogram kan samla in tillagda variabler i ett meddelande. I vårt exempel använder vi variabeln&quot;VAR&quot;.

* **I Android**:

  ```
  public void onReceive(Context context, Intent intent) {
       ...
      String event = intent.getStringExtra("VAR");
       ...
  }
  ```

* **I IOS**:

  ```
  - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
  {
      ....
      if( launchOptions )
      {
          // When application is not already launched, the notification data if any are stored in the key 'UIApplicationLaunchOptionsRemoteNotificationKey'
          NSDictionary *localLaunchOptions = [launchOptions objectForKey:@"UIApplicationLaunchOptionsRemoteNotificationKey"];
          if( localLaunchOptions )
          {
           ...
           [localLaunchOptions objectForKey:@"VAR"];
          ...
          }
     }
  }
  
  // Callback called when the application is already launched (whether the application is running foreground or background)
  - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
  {
      if( launchOptions )
      {
       ...
          [launchOptions objectForKey:@"VAR"];
      }
  }
  ```

>[!CAUTION]
>
>Adobe rekommenderar att du väljer korta variabelnamn eftersom meddelandestorleken är begränsad till 4kB för iOS och Android.

+++

+++**Meddelandetjänsttillägg**

**För iOS**

Mediet måste hämtas på meddelanditjänstens tilläggsnivå.

```
#import "NotificationService.h"

@interface NotificationService ()

@property (nonatomic, strong) void (^contentHandler)(UNNotificationContent *contentToDeliver);
@property (nonatomic, strong) UNMutableNotificationContent *bestAttemptContent;

@end

@implementation NotificationService

- (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
    NSDictionary *userInfo = nil;
    NSString *url = nil;

    self.contentHandler = contentHandler;
    self.bestAttemptContent = [request.content mutableCopy];

    userInfo = request.content.userInfo;
    if ( userInfo != nil )
    {
        url = userInfo[@"mediaUrl"];  // Get the url of the media to download (Adobe Campaign additional variable)
    }
    ...
    // Perform the download to local storage
```

+++

+++**Tillägg för meddelandeinnehåll**

**För iOS**

På den här nivån måste du:

* Koppla ditt innehållstillägg till kategorin som skickats av Adobe Campaign:

  Om du vill att mobilprogrammet ska visa en bild kan du ange kategorivärdet som &quot;image&quot; i Adobe Campaign och i mobilprogrammet skapar du ett meddelandetillägg med **UNNotificationExtensionCategory** parametern inställd på &quot;image&quot;. När push-meddelandet tas emot på enheten anropas tillägget enligt det definierade kategorivärdet.

* Definiera meddelandelayout

  Du måste definiera en layout med relevanta widgetar. Widgeten namnges för en bild **UImageView**.

* Visa dina mediefiler

  Du måste lägga till kod för att mata in mediedata i widgeten. Här är ett exempel på kod för en bild:

  ```
  #import "NotificationViewController.h"
  #import <UserNotifications/UserNotifications.h>
  #import <UserNotificationsUI/UserNotificationsUI.h>
  
  @interface NotificationViewController () <UNNotificationContentExtension>
  
  @property (strong, nonatomic) IBOutlet UIImageView *imageView;
  @property (strong, nonatomic) IBOutlet UILabel *notifContent;
  @property (strong, nonatomic) IBOutlet UILabel *label;
  
  @end
  
  @implementation NotificationViewController
  
  - (void)viewDidLoad {
      [super viewDidLoad];
      // Do any required interface initialization here.
  }
  
  - (void)didReceiveNotification:(UNNotification *)notification {
      self.label.text = notification.request.content.title;
      self.notifContent.text = notification.request.content.body;
      UNNotificationAttachment *attachment = [notification.request.content.attachments objectAtIndex:0];
      if ([attachment.URL startAccessingSecurityScopedResource])
      {
        NSData * imageData = [[NSData alloc] initWithContentsOfURL:attachment.URL];
        self.imageView.image =[UIImage imageWithData: imageData];
        [attachment.URL stopAccessingSecurityScopedResource];
      }
  }
  @end
  ```

+++
