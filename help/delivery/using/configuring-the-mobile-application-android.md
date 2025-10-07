---
product: campaign
title: Konfigurera Android mobilprogram i Adobe Campaign
description: Lär dig hur du konfigurerar ditt mobilprogram för Android
feature: Push
role: User, Developer
level: Intermediate, Experienced
hide: true
hidefromtoc: true
exl-id: 32c35e61-d0a3-478f-b73b-396e2becf7f9
source-git-commit: 89e350c727fb9379d28916f79d9749f22fd4974f
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 9%

---

# Konfigurationssteg för Android

När paketet har installerats kan du definiera dina programinställningar för Android i Adobe Campaign Classic.

Viktiga steg är:

1. [Konfigurera Android externa konto](#configuring-external-account-android)
1. [Konfigurera Android-tjänsten](#configuring-android-service)
1. [Skapa mobilappen i Campaign](#creating-android-app)
1. [Utöka appschemat med ytterligare data](#extend-subscription-schema)

Du kan sedan [skapa ett omfattande Android-meddelande](create-notifications-android.md).

>[!IMPORTANT]
>
>Vissa viktiga ändringar av tjänsten Android Firebase Cloud Messaging (FCM) kommer att släppas 2024 och kan komma att påverka din Adobe Campaign-implementering. Konfigurationen för prenumerationstjänster för push-meddelanden för Android kan behöva uppdateras för att den här ändringen ska fungera. Du kan redan kontrollera och vidta åtgärder. Läs mer i den här [Adobe Campaign v8-tekniken](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=sv){target="_blank"}.


## Konfigurera Android externa konto {#configuring-external-account-android}

För Android finns två anslutningsmöjligheter:

* V1-anslutningen som tillåter en anslutning per underordnad MTA.
* V2-anslutningen som tillåter samtidiga anslutningar till FCM-servern för att förbättra genomströmningen.

Så här väljer du vilken koppling du vill använda:

1. Gå till **[!UICONTROL Administration > Platform > External accounts]**.
1. Välj det **[!UICONTROL Android routing]** externa kontot.
1. På fliken **[!UICONTROL Connector]** fyller du i fältet **[!UICONTROL JavaScript used in the connector]**:

   För Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > Du kan även konfigurera den enligt https://localhost:8080/nms/jsp/androidPushConnector.js, men vi rekommenderar att du använder version 2 av anslutningsprogrammet.

   ![](assets/nmac_connectors3.png)

1. För Android V2 finns ytterligare en parameter i konfigurationsfilen för Adobe Server (serverConf.xml):

   * **maxGCMConnectPerChild**: Maximal gräns för parallella HTTP-begäranden till FCM som initieras av varje underordnad server (8 som standard).

## Konfigurera en Android-tjänst {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [Lär dig hur du konfigurerar en Android-tjänst i en video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign){target="_blank"}.

1. Gå till noden **[!UICONTROL Profiles and Targets > Services and subscriptions]** och klicka på **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Definiera en **[!UICONTROL Label]** och en **[!UICONTROL Internal name]**.
1. Gå till fältet **[!UICONTROL Type]** och välj **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >Standardmålmappningen **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** är länkad till mottagartabellen. Om du vill använda en annan målmappning måste du skapa en ny målmappning och ange den i fältet **[!UICONTROL Target mapping]** för tjänsten. Mer information om hur du skapar målmappning finns i [det här avsnittet](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Klicka sedan på knappen **[!UICONTROL Add]** för att välja programtyp.

   ![](assets/nmac_service_2.png)

1. Skapa ett Android-program. Mer information om detta finns i [det här avsnittet](configuring-the-mobile-application-android.md#creating-android-app).

## Skapa Android mobilprogram {#creating-android-app}

När du har skapat tjänsten måste du nu skapa ett Android-program:

1. Klicka på knappen **[!UICONTROL Add]** för att välja programtyp i den nya tjänsten.

   ![](assets/nmac_service_2.png)

1. Välj **[!UICONTROL Create an Android application]** och ange en **[!UICONTROL Label]**.

   ![](assets/nmac_android.png)

1. Se till att samma **[!UICONTROL Integration key]** har definierats i Adobe Campaign och i programkoden via SDK. <!--For more on this, refer to [this section](integrating-campaign-sdk-into-the-mobile-application.md).-->

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** är helt anpassningsbar med strängvärde, men måste vara exakt densamma som den som anges i SDK.

1. Välj **[!UICONTROL API version]**: HTTP v1 eller HTTP (äldre). Dessa konfigurationer beskrivs i [det här avsnittet](#select-api-version)

1. Fyll i fälten **[!UICONTROL Firebase Cloud Messaging the Android connection settings]**.

1. Klicka på **[!UICONTROL Finish]** och sedan på **[!UICONTROL Save]**. Ditt Android-program kan nu användas i Campaign Classic.

Som standard sparar Adobe Campaign en nyckel i fältet **[!UICONTROL User identifier]** (@userKey) i tabellen **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**. Med den här nyckeln kan du länka en prenumeration till en mottagare. Om du vill samla in ytterligare data (till exempel en komplex avstämningsnyckel) måste du använda följande konfiguration:

### Konfigurera API-versionen{#select-api-version}

>[!IMPORTANT]
>
>Vissa viktiga ändringar av tjänsten Android Firebase Cloud Messaging (FCM) kommer att släppas 2024 och kan komma att påverka din Adobe Campaign-implementering. Som en del av Google kontinuerliga arbete med att förbättra sina tjänster kommer de äldre FCM-API:erna att upphöra den **20 juni 2024**. Läs mer i den här [Adobe Campaign v8-tekniken](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=sv){target="_blank"}.

När du har skapat en tjänst och ett nytt mobilprogram måste du konfigurera ditt mobilprogram. API:t **HTTP (äldre)** bör inte väljas eftersom det har tagits bort av Google.

Följ stegen nedan för att konfigurera API-versionen för HTTP v1:

1. I **[!UICONTROL Mobile application creation wizard]**-fönstret väljer du **[!UICONTROL HTTPV1]** i listrutan **[!UICONTROL API version]**.

1. Klicka på **[!UICONTROL Load project json file to extract project details...]** om du vill läsa in JSON-nyckelfilen direkt. Mer information om hur du extraherar JSON-filen finns på [den här sidan](https://firebase.google.com/docs/admin/setup#initialize-sdk).

   Du kan även ange följande manuellt:
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. Klicka på **[!UICONTROL Test the connection]** om du vill kontrollera att konfigurationen är korrekt och att marknadsföringsservern har åtkomst till FCM.

   >[!CAUTION]
   >
   >Knappen **[!UICONTROL Test connection]** kontrollerar inte om MID-servern har åtkomst till FCM-servern för distributionen med mellanresurser.

   ![](assets/nmac_android_11.png)

1. Som ett alternativ kan du utöka ett push-meddelandeinnehåll med vissa **[!UICONTROL Application variables]** vid behov. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.

1. Klicka på **[!UICONTROL Finish]** och sedan på **[!UICONTROL Save]**. Ditt Android-program kan nu användas i Campaign Classic.

Nedan visas FCM-nyttolastsnamnen för att ytterligare anpassa ditt push-meddelande:

| Meddelandetyp | Konfigurerbart meddelandeelement (FCM-nyttolastnamn) | Konfigurerbara alternativ (FCM-nyttolastnamn) |
|:-:|:-:|:-:|
| datameddelande | N/A | validate_only |
| meddelandemeddelande | title, body, android_channel_id, icon, sound, tag, color, click_action, image, ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |

## Utöka appsubscriptionRcp-schemat {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [Lär dig hur du utökar appsubscriptionRcp-schemat i video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html#extending-the-app-subscription-schema-to-personalize-push-notifications)

Du måste utöka **appsubscriptionRcp** för att definiera nya fält för att lagra parametrar från appen i Campaign-databasen. De här fälten används till exempel för personalisering. Så här gör du:

1. Skapa ett tillägg till **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**-schemat och definiera de nya fälten. Läs mer om schematillägget på [den här sidan](../../configuration/using/about-schema-edition.md)

1. Definiera mappningen på fliken **[!UICONTROL Subscription parameters]**.

   >[!CAUTION]
   >
   >Kontrollera att konfigurationsnamnen på fliken **[!UICONTROL Subscription parameters]** är samma som de i mobilprogramkoden. <!--Refer to [this section](integrating-campaign-sdk-into-the-mobile-application.md).-->
