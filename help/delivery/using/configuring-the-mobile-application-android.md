---
product: campaign
title: Konfigurera Android-mobilprogrammet i Adobe Campaign
description: Lär dig hur du konfigurerar ditt mobilprogram för Android
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Push
exl-id: 32c35e61-d0a3-478f-b73b-396e2becf7f9
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 4%

---

# Konfigurationssteg för Android



När paketet har installerats kan du definiera dina Android-appinställningar i Adobe Campaign Classic.

>[!NOTE]
>
>Mer information om hur du konfigurerar din app för iOS och hur du skapar en leverans för iOS finns i [section](configuring-the-mobile-application.md).

Viktiga steg är:

1. [Konfigurera det externa Android-kontot](#configuring-external-account-android)
1. [Konfigurera Android-tjänsten](#configuring-android-service)
1. [Skapa mobilappen i Campaign](#creating-android-app)
1. [Utöka appschemat med ytterligare data](#extend-subscription-schema)

Då kan du [skapa ett omfattande meddelande för Android](create-notifications-android.md).

## Konfigurera externt Android-konto {#configuring-external-account-android}

För Android finns två anslutningar:

* V1-anslutningen som tillåter en anslutning per underordnad MTA.
* V2-anslutningen som tillåter samtidiga anslutningar till FCM-servern för att förbättra genomströmningen.

Så här väljer du vilken koppling du vill använda:

1. Gå till **[!UICONTROL Administration > Platform > External accounts]**.
1. Välj **[!UICONTROL Android routing]** externt konto.
1. I **[!UICONTROL Connector]** -flik, fylla i **[!UICONTROL JavaScript used in the connector]** fält:

   För Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > Du kan även konfigurera den enligt https://localhost:8080/nms/jsp/androidPushConnector.js, men vi rekommenderar att du använder version 2 av kopplingen.

   ![](assets/nmac_connectors3.png)

1. För Android V2 finns ytterligare en parameter i konfigurationsfilen för Adobe Server (serverConf.xml):

   * **maxGCMConnectPerChild**: Maximal gräns för parallella HTTP-begäranden till FCM som initieras av varje underordnad server (8 som standard).

## Konfigurera en Android-tjänst {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [Lär dig hur du konfigurerar en Android-tjänst i video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=en#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign)

1. Gå till **[!UICONTROL Profiles and Targets > Services and subscriptions]** nod och klicka **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Definiera en **[!UICONTROL Label]** och **[!UICONTROL Internal name]**.
1. Gå till **[!UICONTROL Type]** fält och markera **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >Standardvärdet **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** målmappningen är länkad till mottagartabellen. Om du vill använda en annan målmappning måste du skapa en ny målmappning och ange den i **[!UICONTROL Target mapping]** tjänstens fält. Mer information om hur du skapar målmappning finns i [det här avsnittet](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Klicka sedan på **[!UICONTROL Add]** för att välja programtyp.

   ![](assets/nmac_service_2.png)

1. Skapa ett Android-program. Mer information om detta finns i [det här avsnittet](configuring-the-mobile-application-android.md#creating-android-app).

## Skapa Android-mobilprogrammet {#creating-android-app}

När du har skapat tjänsten måste du nu skapa ditt Android-program:

1. Klicka på **[!UICONTROL Add]** för att välja programtyp.

   ![](assets/nmac_service_2.png)

1. Välj **[!UICONTROL Create an Android application]** och ange **[!UICONTROL Label]**.

   ![](assets/nmac_android.png)

1. Se till att samma **[!UICONTROL Integration key]** definieras i Adobe Campaign och i programkoden via SDK. Mer information om detta finns i [det här avsnittet](integrating-campaign-sdk-into-the-mobile-application.md).

   >[!NOTE]
   >
   > The **[!UICONTROL Integration key]** är helt anpassningsbart med strängvärde, men måste vara exakt densamma som den som anges i SDK:n.

1. Välj **[!UICONTROL API version]**: HTTP v1 eller HTTP (äldre). Dessa konfigurationer beskrivs i [det här avsnittet](#select-api-version)

1. Fyll i **[!UICONTROL Firebase Cloud Messaging the Android connection settings]** fält.

1. Klicka **[!UICONTROL Finish]** och sen **[!UICONTROL Save]**. Android-programmet kan nu användas i Campaign Classic.

Som standard sparar Adobe Campaign en tangent i **[!UICONTROL User identifier]** (@userKey) i fältet **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** tabell. Med den här nyckeln kan du länka en prenumeration till en mottagare. Om du vill samla in ytterligare data (till exempel en komplex avstämningsnyckel) måste du använda följande konfiguration:

### Välj API-version{#select-api-version}

När du har skapat en tjänst och ett nytt mobilprogram måste du konfigurera ditt mobilprogram beroende på den valda API-versionen.

* **HTTP v1** konfigurationen anges i [det här avsnittet](configuring-the-mobile-application-android.md#android-service-httpv1).
* **HTTP (äldre)** konfigurationen anges i [det här avsnittet](configuring-the-mobile-application-android.md#android-service-http).

#### Konfigurera HTTP v1 API{#android-service-httpv1}

Följ stegen nedan för att konfigurera API-versionen för HTTP v1:

1. I **[!UICONTROL Mobile application creation wizard]** fönster, markera **[!UICONTROL HTTPV1]** i **[!UICONTROL API version]** nedrullningsbar meny.

1. Klicka **[!UICONTROL Load project json file to extract project details...]** för att läsa in JSON-nyckelfilen direkt. Mer information om hur du extraherar JSON-filen finns i [den här sidan](https://firebase.google.com/docs/admin/setup#initialize-sdk).

   Du kan även ange följande manuellt:
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. Klicka **[!UICONTROL Test the connection]** för att kontrollera att konfigurationen är korrekt och att marknadsföringsservern har åtkomst till FCM.

   >[!CAUTION]
   >
   >För resursdistributionen kan du **[!UICONTROL Test connection]** kommer inte att kontrollera om MID-servern har åtkomst till FCM-servern.

   ![](assets/nmac_android_11.png)

1. Som ett alternativ kan du utöka ett push-meddelandeinnehåll med **[!UICONTROL Application variables]** vid behov. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.

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

1. I **[!UICONTROL Mobile application creation wizard]** fönster, markera **[!UICONTROL HTTP (legacy)]** i **[!UICONTROL API version]** nedrullningsbar meny.

1. Ange **[!UICONTROL Project key]** som tillhandahålls av utvecklaren av mobilapplikationen.

1. Som ett alternativ kan du utöka ett push-meddelandeinnehåll med **[!UICONTROL Application variables]** vid behov. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.

   I följande exempel lägger vi till **title**, **imageURL** och **iconURL** för att skapa omfattande push-meddelanden och sedan förse programmet med bilden, titeln och ikonen som ska visas i meddelandet.

   ![](assets/nmac_android_2.png)

1. Klicka **[!UICONTROL Finish]** och sen **[!UICONTROL Save]**. Android-programmet kan nu användas i Campaign Classic.

Nedan visas FCM-nyttolastsnamnen för att ytterligare anpassa ditt push-meddelande:

| Meddelandetyp | Konfigurerbart meddelandeelement (FCM-nyttolastnamn) | Konfigurerbara alternativ (FCM-nyttolastnamn) |
|:-:|:-:|:-:|
| datameddelande | N/A | dryRun |
| meddelande | title, body, android_channel_id, icon, sound, tag, color, click_action <br> | dryRun |

<br>

## Utöka appsubscriptionRcp-schemat {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [Lär dig hur du utökar appsubscriptionRcp-schemat i en video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=en#extending-the-app-subscription-schema-to-personalize-push-notifications)

Du måste utöka **appsubscriptionRcp** om du vill definiera nya ytterligare fält för att lagra parametrar från appen i Campaign-databasen. Dessa fält kommer till exempel att användas för personalisering. Så här gör du:

1. Skapa ett tillägg till **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** och definiera de nya fälten. Läs mer om schemautökning i [den här sidan](../../configuration/using/about-schema-edition.md)

1. Definiera mappningen i **[!UICONTROL Subscription parameters]** -fliken.

   >[!CAUTION]
   >
   >Kontrollera konfigurationsnamnen i **[!UICONTROL Subscription parameters]** -fliken är densamma som i mobilprogramkoden. Se [det här avsnittet](integrating-campaign-sdk-into-the-mobile-application.md).
