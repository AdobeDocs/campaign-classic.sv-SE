---
product: campaign
title: Konfigurera Android-mobilprogrammet i Adobe Campaign
description: Lär dig hur du konfigurerar ditt mobilprogram för Android
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
index: y
internal: n
snippet: y
exl-id: 32c35e61-d0a3-478f-b73b-396e2becf7f9
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1648'
ht-degree: 2%

---

# Konfigurationssteg för Android

När paketet har installerats kan du definiera dina Android-appinställningar i Adobe Campaign Classic.

>[!NOTE]
>
>Mer information om hur du konfigurerar din app för iOS och hur du skapar en leverans för iOS finns i det här [avsnittet](../../delivery/using/configuring-the-mobile-application.md).

Viktiga steg är:

1. [Konfigurera det externa Android-kontot](#configuring-external-account-android)
1. [Konfigurera Android-tjänsten](#configuring-android-service)
1. [Skapa mobilappen i Campaign](#creating-android-app)
1. [Utöka appschemat med ytterligare data](#extend-subscription-schema)

Du kan sedan [skapa ett omfattande Android-meddelande](#creating-android-delivery).

## Android-externt konto {#configuring-external-account-android} konfigureras

För Android finns två anslutningar:

* V1-anslutningen som tillåter en anslutning per underordnad MTA.
* V2-anslutningen som tillåter samtidiga anslutningar till FCM-servern för att förbättra genomströmningen.

Så här väljer du vilken koppling du vill använda:

1. Gå till **[!UICONTROL Administration > Platform > External accounts]**.
1. Välj det externa **[!UICONTROL Android routing]**-kontot.
1. På fliken **[!UICONTROL Connector]** fyller du i fältet **[!UICONTROL JavaScript used in the connector]**:

   För Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > Du kan även konfigurera den enligt https://localhost:8080/nms/jsp/androidPushConnector.js, men vi rekommenderar att du använder version 2 av kopplingen.

   ![](assets/nmac_connectors3.png)

1. För Android V2 finns ytterligare en parameter i konfigurationsfilen för Adobe Server (serverConf.xml):

   * **maxGCMConnectPerChild**: Maximal gräns för parallella HTTP-begäranden till FCM som initieras av varje underordnad server (8 som standard).

## Konfigurerar Android-tjänsten {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [Lär dig hur du konfigurerar en Android-tjänst i video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=en#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign)

1. Gå till noden **[!UICONTROL Profiles and Targets > Services and subscriptions]** och klicka på **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Definiera en **[!UICONTROL Label]** och en **[!UICONTROL Internal name]**.
1. Gå till fältet **[!UICONTROL Type]** och välj **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >Standardmålmappningen för **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** är länkad till mottagartabellen. Om du vill använda en annan målmappning måste du skapa en ny målmappning och ange den i fältet **[!UICONTROL Target mapping]** för tjänsten. Mer information om hur du skapar målmappning finns i [Konfigurationshandboken](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Klicka sedan på knappen **[!UICONTROL Add]** för att välja programtyp.

   ![](assets/nmac_service_2.png)

1. Skapa ett Android-program. Mer information om detta hittar du i det här [avsnittet](../../delivery/using/configuring-the-mobile-application-android.md#creating-android-app).

## Skapar Android-mobilprogram {#creating-android-app}

När du har skapat tjänsten måste du nu skapa ditt Android-program:

1. Klicka på knappen **[!UICONTROL Add]** för att välja programtyp i den nya tjänsten.

   ![](assets/nmac_service_2.png)

1. Välj **[!UICONTROL Create an Android application]** och ange en **[!UICONTROL Label]**.

   ![](assets/nmac_android.png)

1. Se till att samma **[!UICONTROL Integration key]** är definierat i Adobe Campaign och i programkoden via SDK. Mer information finns i: [Integrera Campaign SDK i mobilprogrammet](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md).

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** är helt anpassningsbar med strängvärde, men måste vara exakt densamma som den som anges i SDK:n.

1. Välj **[!UICONTROL API version]**: HTTP v1 eller HTTP (äldre). Dessa konfigurationer beskrivs i [det här avsnittet](#select-api-version)

1. Fyll i **[!UICONTROL Firebase Cloud Messaging the Android connection settings]**-fälten.

1. Klicka **[!UICONTROL Finish]** och sen **[!UICONTROL Save]**. Android-programmet kan nu användas i Campaign Classic.

Som standard sparar Adobe Campaign en nyckel i fältet **[!UICONTROL User identifier]** (@userKey) i tabellen **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**. Med den här nyckeln kan du länka en prenumeration till en mottagare. Om du vill samla in ytterligare data (till exempel en komplex avstämningsnyckel) måste du använda följande konfiguration:

### Välj API-version{#select-api-version}

När du har skapat en tjänst och ett nytt mobilprogram måste du konfigurera ditt mobilprogram beroende på den valda API-versionen.

* **HTTP v1** -konfigurationen beskrivs i det här  [avsnittet](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1).
* **HTTP-** konfiguration (äldre) beskrivs i det här  [avsnittet](../../delivery/using/configuring-the-mobile-application-android.md#android-service-http).

#### Konfigurera HTTP v1 API{#android-service-httpv1}

Följ stegen nedan för att konfigurera API-versionen för HTTP v1:

1. I **[!UICONTROL Mobile application creation wizard]**-fönstret väljer du **[!UICONTROL HTTPV1]** i listrutan **[!UICONTROL API version]**.

1. Klicka på **[!UICONTROL Load project json file to extract projet details...]** om du vill läsa in JSON-nyckelfilen direkt. Mer information om hur du extraherar JSON-filen finns på den här [sidan](https://firebase.google.com/docs/admin/setup#initialize-sdk).

   Du kan även ange följande manuellt:
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. Klicka på **[!UICONTROL Test the connection]** för att kontrollera att konfigurationen är korrekt och att marknadsföringsservern har åtkomst till FCM.

   >[!CAUTION]
   >
   >Knappen **[!UICONTROL Test connection]** kontrollerar inte om MID-servern har åtkomst till FCM-servern för att kontrollera om det finns en MID-server.

   ![](assets/nmac_android_11.png)

1. Som ett alternativ kan du utöka ett push-meddelandeinnehåll med **[!UICONTROL Application variables]** om det behövs. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.

1. Klicka **[!UICONTROL Finish]** och sen **[!UICONTROL Save]**. Android-programmet kan nu användas i Campaign Classic.

Nedan visas FCM-nyttolastsnamnen för att ytterligare anpassa ditt push-meddelande:

| Meddelandetyp | Konfigurerbart meddelandeelement (FCM-nyttolastnamn) | Konfigurerbara alternativ (FCM-nyttolastnamn) |
|:-:|:-:|:-:|
| datameddelande | N/A | validate_only |
| meddelande | title, body, android_channel_id, icon, sound, tag, color, click_action, image, ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |

<br>
<br>

#### Konfigurera HTTP-API (äldre){#android-service-http}

Följ stegen nedan för att konfigurera API-versionen för HTTP (äldre):

1. I **[!UICONTROL Mobile application creation wizard]**-fönstret väljer du **[!UICONTROL HTTP (legacy)]** i listrutan **[!UICONTROL API version]**.

1. Ange **[!UICONTROL Project key]** som tillhandahålls av utvecklaren av mobilprogrammet.

1. Som ett alternativ kan du utöka ett push-meddelandeinnehåll med **[!UICONTROL Application variables]** om det behövs. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.

   I följande exempel lägger vi till **title**, **imageURL** och **iconURL** för att skapa ett omfattande push-meddelande och förser sedan programmet med bilden, titeln och ikonen som ska visas i meddelandet.

   ![](assets/nmac_android_2.png)

1. Klicka **[!UICONTROL Finish]** och sen **[!UICONTROL Save]**. Android-programmet kan nu användas i Campaign Classic.

Nedan visas FCM-nyttolastsnamnen för att ytterligare anpassa ditt push-meddelande:

| Meddelandetyp | Konfigurerbart meddelandeelement (FCM-nyttolastnamn) | Konfigurerbara alternativ (FCM-nyttolastnamn) |
|:-:|:-:|:-:|
| datameddelande | Ej tillämpligt | dryRun |
| meddelande | title, body, android_channel_id, icon, sound, tag, color, click_action <br> | dryRun |

<br>

## Utöka appsubscriptionRcp-schemat {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [Lär dig hur du utökar appsubscriptionRcp-schemat i en video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=en#extending-the-app-subscription-schema-to-personalize-push-notifications)

Du måste utöka **appsubscriptionRcp** för att definiera nya fält för att lagra parametrar från appen i Campaign-databasen. Dessa fält kommer till exempel att användas för personalisering. Så här gör du:

1. Skapa ett tillägg till **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**-schemat och definiera de nya fälten. Läs mer om schematillägget i [den här sidan](../../configuration/using/about-schema-edition.md)

1. Definiera mappningen på fliken **[!UICONTROL Subscription parameters]**.

   >[!CAUTION]
   >
   >Kontrollera att konfigurationsnamnen på fliken **[!UICONTROL Subscription parameters]** är samma som i mobilprogramkoden. Se avsnittet [Integrera Campaign SDK i mobilappen](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md).

## Skapa ett meddelande i Android om hög kvalitet {#creating-android-delivery}

Med Firebase Cloud Messaging kan du välja mellan två typer av meddelanden:

* **[!UICONTROL Data message]**, hanteras av klientprogrammet.
   <br>Meddelanden skickas direkt till mobilprogrammet som genererar och visar android-meddelandet till enheten. Datameddelanden innehåller bara dina anpassade programvariabler.

* **[!UICONTROL Notification message]**, hanteras automatiskt av FCM SDK.
   <br> FCM visar automatiskt meddelandet på användarnas enheter för klientprogrammets räkning. Meddelanden innehåller en fördefinierad uppsättning parametrar och alternativ, men de kan fortfarande anpassas ytterligare med anpassade programvariabler.

Mer information om meddelandetyper i Firebase Cloud finns i [FCM-dokumentation](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages).

### Skapar ett datameddelande {#creating-data-message}

1. Gå till **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klicka på **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Välj **[!UICONTROL Deliver on Android (android)]** i listrutan **[!UICONTROL Delivery template]**. Lägg till en **[!UICONTROL Label]** i leveransen.

1. Klicka på **[!UICONTROL To]** för att definiera målpopulationen. Som standard används målmappningen **[!UICONTROL Subscriber application]**. Klicka på **[!UICONTROL Add]** för att välja tjänsten.

   ![](assets/nmac_android_7.png)

1. I fönstret **[!UICONTROL Target type]** väljer du **[!UICONTROL Subscribers of an Android mobile application]** och klickar på **[!UICONTROL Next]**.

1. I listrutan **[!UICONTROL Service]** väljer du den tjänst du skapade tidigare och sedan programmet och klickar på **[!UICONTROL Finish]**.
**[!UICONTROL Application variables]** läggs till automatiskt beroende på vad som lades till under konfigurationsstegen.

   ![](assets/nmac_android_6.png)

1. Välj **[!UICONTROL data message]** som **[!UICONTROL Message Type]**.

1. Redigera dina meddelanden.

   ![](assets/nmac_android_5.png)

1. Du kan lägga till information i din tidigare konfigurerade **[!UICONTROL Application variables]** om det behövs. **[!UICONTROL Application variables]** måste konfigureras i Android-tjänsten och är en del av den meddelandenyttolast som skickas till den mobila enheten.

1. Klicka på **[!UICONTROL Save]** och skicka leveransen.

Bilden och webbsidan ska visas i push-meddelandet när de tas emot på prenumerantens mobila Android-enheter.

![](assets/nmac_android_4.png)

### Skapar ett meddelande {#creating-notification-message}

>[!NOTE]
>
>Ytterligare alternativ för meddelanden är bara tillgängliga med HTTP v1 API-konfiguration. Mer information om detta hittar du i det här [avsnittet](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1).

![](assets/do-not-localize/how-to-video.png) [Lär dig hur du skapar ett push-meddelande för Android i en video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html?lang=en#additional-resources)

1. Gå till **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klicka på **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Välj **[!UICONTROL Deliver on Android (android)]** i listrutan **[!UICONTROL Delivery template]**. Lägg till en **[!UICONTROL Label]** i leveransen.

1. Klicka på **[!UICONTROL To]** för att definiera målpopulationen. Som standard används målmappningen **[!UICONTROL Subscriber application]**. Klicka på **[!UICONTROL Add]** för att välja tjänsten.

   ![](assets/nmac_android_7.png)

1. I fönstret **[!UICONTROL Target type]** väljer du **[!UICONTROL Subscribers of an Android mobile application]** och klickar på **[!UICONTROL Next]**.

1. I listrutan **[!UICONTROL Service]** väljer du den tjänst du skapade tidigare och sedan programmet och klickar på **[!UICONTROL Finish]**.

   ![](assets/nmac_android_6.png)

1. Välj **[!UICONTROL notification message]** som **[!UICONTROL Message Type]**.

1. Lägg till en titel och redigera meddelandet. Anpassa ditt push-meddelande med **[!UICONTROL Notification options]**:

   * **[!UICONTROL Channel ID]**: Ange meddelandets kanal-ID. Appen måste skapa en kanal med detta channel-id innan något meddelande med detta channel-id tas emot.
   * **[!UICONTROL Sound]**: Ställ in ljudet som ska spelas upp när enheten får ditt meddelande.
   * **[!UICONTROL Color]**: Ange ikonfärgen för meddelandet.
   * **[!UICONTROL Icon]**: Ange meddelandeikonen som ska visas på dina profilers enheter.
   * **[!UICONTROL Tag]**: Ange den identifierare som ska användas för att ersätta befintliga meddelanden i meddelandelådan.
   * **[!UICONTROL Click action]**: Ange åtgärden som är associerad med en användare genom att klicka på meddelandet.

   Mer information om **[!UICONTROL Notification options]** och hur du fyller i dessa fält finns i [FCM-dokumentationen](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_8.png)

1. Om ditt program är konfigurerat med HTTP v1 API-protokollet kan du anpassa ditt push-meddelande ytterligare med följande **[!UICONTROL HTTPV1 additional options]**:

   * **[!UICONTROL Ticker]**: Ange anteckningstexten för meddelandet. Endast tillgängligt för enheter med inställningen Android 5.0 Lollipop.
   * **[!UICONTROL Image]**: Ange bildens URL som ska visas i meddelandet.
   * **[!UICONTROL Notification Count]**: Ange antalet nya olästa uppgifter som ska visas direkt på programikonen.
   * **[!UICONTROL Sticky]**: Ange som true eller false. Om värdet är false ignoreras meddelandet automatiskt när användaren klickar på det. Om värdet är true visas meddelandet fortfarande även när användaren klickar på det.
   * **[!UICONTROL Notification Priority]**: Ange prioritetsnivåerna för dina meddelanden till standard, minimum, low eller high. Mer information finns i [FCM-dokumentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**: Ange visningsnivåerna för meddelandet till public, private eller secrets. Mer information finns i [FCM-dokumentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   Mer information om **[!UICONTROL HTTP v1 additional options]** och hur du fyller i dessa fält finns i [FCM-dokumentationen](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_9.png)

1. Du kan lägga till information i din tidigare konfigurerade **[!UICONTROL Application variables]** om det behövs. **[!UICONTROL Application variables]** måste konfigureras i Android-tjänsten och är en del av den meddelandenyttolast som skickas till den mobila enheten.

1. Klicka på **[!UICONTROL Save]** och skicka leveransen.

Bilden och webbsidan ska visas i push-meddelandet när de tas emot på prenumerantens mobila Android-enheter.
