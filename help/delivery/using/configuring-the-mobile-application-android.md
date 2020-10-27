---
title: Konfigurera Android-mobilprogrammet i Adobe Campaign
description: Lär dig hur du konfigurerar ditt mobilprogram för Android
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9844616f417608051bbff2593d6124d8ff83008c
workflow-type: tm+mt
source-wordcount: '1516'
ht-degree: 1%

---


# Konfigurationssteg för Android

När paketet har installerats kan du definiera dina Android-appinställningar i Adobe Campaign Classic.

>[!NOTE]
>
>Mer information om hur du konfigurerar din app för iOS och hur du skapar en leverans för iOS finns i det här [avsnittet](../../delivery/using/configuring-the-mobile-application.md).


## Konfigurera externt Android-konto {#configuring-external-account-android}

För Android finns två anslutningar:

* V1-anslutningen som tillåter en anslutning per underordnad MTA.
* V2-anslutningen som tillåter samtidiga anslutningar till FCM-servern för att förbättra genomströmningen.

Så här väljer du vilken koppling du vill använda:

1. Gå till **[!UICONTROL Administration > Platform > External accounts]**.
1. Select the **[!UICONTROL Android routing]** external account.
1. På **[!UICONTROL Connector]** fliken fyller du i **[!UICONTROL JavaScript used in the connector]** fältet:

   För Android V2: https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > Du kan även konfigurera den enligt https://localhost:8080/nms/jsp/androidPushConnector.js, men vi rekommenderar att du använder version 2 av kopplingen.

   ![](assets/nmac_connectors3.png)

1. För Android V2 finns ytterligare en parameter i konfigurationsfilen för Adobe Server (serverConf.xml):

   * **maxGCMConnectPerChild**: Maximal gräns för parallella HTTP-begäranden till FCM som initieras av varje underordnad server (8 som standard).

## Konfigurera Android-tjänsten {#configuring-android-service}

1. Gå till **[!UICONTROL Profiles and Targets > Services and subscriptions]** noden och klicka på **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Define a **[!UICONTROL Label]** and an **[!UICONTROL Internal name]**.
1. Gå till **[!UICONTROL Type]** fältet och välj **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >Standardmålmappningen **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** är länkad till mottagartabellen. Om du vill använda en annan målmappning måste du skapa en ny målmappning och ange den i **[!UICONTROL Target mapping]** fältet för tjänsten. Mer information om hur du skapar målmappning finns i [konfigurationsguiden](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Klicka sedan på **[!UICONTROL Add]** knappen för att välja programtyp.

   ![](assets/nmac_service_2.png)

1. Skapa ett Android-program. Mer information om detta hittar du i det här [avsnittet](../../delivery/using/configuring-the-mobile-application-android.md#creating-android-app).

## Skapa Android-mobilprogram {#creating-android-app}

När du har skapat tjänsten måste du nu skapa ditt Android-program:

1. Klicka på knappen för att välja programtyp i den nya tjänsten **[!UICONTROL Add]** .

   ![](assets/nmac_service_2.png)

1. Markera **[!UICONTROL Create an Android application]** och ange en **[!UICONTROL Label]**.

   ![](assets/nmac_android.png)

1. Se till att samma **[!UICONTROL Integration key]** är definierat i Adobe Campaign och i programkoden via SDK. Mer information finns i: [Integrera Campaign SDK i mobilapplikationen](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md).

   >[!NOTE]
   >
   > Det går **[!UICONTROL Integration key]** att anpassa med strängvärde, men det måste vara exakt detsamma som det som anges i SDK:n.

1. Välj något av **[!UICONTROL API version]**:
   * HTTP. For more information refer to this [section](../../delivery/using/configuring-the-mobile-application-android.md#android-service-http).
   * HTTPV1. For more information refer to this [section](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1).

1. Fill in the **[!UICONTROL Firebase Cloud Messaging settings for the Android connection]** fields.

1. Klicka **[!UICONTROL Finish]** och sen **[!UICONTROL Save]**. Android-programmet kan nu användas i Campaign Classic.

Som standard sparar Adobe Campaign en nyckel i **[!UICONTROL User identifier]** (@userKey)-fältet i **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** tabellen. Med den här nyckeln kan du länka en prenumeration till en mottagare. Om du vill samla in ytterligare data (till exempel en komplex avstämningsnyckel) måste du använda följande konfiguration:

1. Skapa ett tillägg till **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** schemat och definiera de nya fälten.

1. Definiera mappningen på **[!UICONTROL Subscription parameters]** fliken.

   >[!CAUTION]
   >
   >Kontrollera att konfigurationsnamnen på fliken **[!UICONTROL Subscription parameters]** är desamma som de i mobilprogramkoden. Se avsnittet [Integrera Campaign SDK i mobilappen](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md) .

### Välj API-version{#select-api-version}

När du har skapat en tjänst och ett nytt mobilprogram måste du konfigurera ditt mobilprogram beroende på den valda API-versionen.

Mer information om tjänster och mobilapplikationer finns i det här [avsnittet](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service)

#### Använd HTTP v1 API-version{#android-service-httpv1}

Följ stegen nedan för att konfigurera API-versionen för HTTP v1:

1. I **[!UICONTROL Mobile application creation wizard]** fönstret väljer du **[!UICONTROL HTTPV1]** i **[!UICONTROL API version]** listrutan.

1. Klicka **[!UICONTROL Load project json file to extract projet details...]** för att läsa in JSON-nyckelfilen direkt. Mer information om hur du extraherar JSON-filen finns på den här [sidan](https://firebase.google.com/docs/admin/setup#initialize-sdk).

1. Du kan även ange följande manuellt:
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. Klicka **[!UICONTROL Test the connection]** för att kontrollera att konfigurationen är korrekt och att marknadsföringsservern har åtkomst till FCM.

   >[!CAUTION]
   >
   >För Distribuering med mellankällor kommer knappen inte att kontrollera om MID-servern har åtkomst till FCM-servern **[!UICONTROL Test connection]** .

   ![](assets/nmac_android_11.png)

1. Som ett alternativ kan du utöka ett push-meddelandeinnehåll med vissa **[!UICONTROL Application variables]** om det behövs. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.

1. Klicka **[!UICONTROL Finish]** och sen **[!UICONTROL Save]**. Android-programmet kan nu användas i Campaign Classic.

Nedan visas FCM-nyttolastsnamnen för att ytterligare anpassa ditt push-meddelande:

| Meddelandetyp | Konfigurerbart meddelandeelement (FCM-nyttolastnamn) | Konfigurerbara alternativ (FCM-nyttolastnamn) |
|:-:|:-:|:-:|
| datameddelande | N/A | validate_only |
| meddelande | title, body, android_channel_id, icon, sound, tag, color, click_action, image, ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |

<br>
<br>

#### HTTP API-version{#android-service-http}

Följ stegen nedan för att konfigurera API-versionen för HTTP (äldre):

1. I **[!UICONTROL Mobile application creation wizard]** fönstret väljer du **[!UICONTROL HTTP (legacy)]** i **[!UICONTROL API version]** listrutan.

1. Ange det **[!UICONTROL Project key]** som utvecklaren av mobilprogrammet har angett.

1. Som ett alternativ kan du utöka ett push-meddelandeinnehåll med vissa **[!UICONTROL Application variables]** om det behövs. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.

   I följande exempel lägger vi till **title**, **imageURL** och **iconURL** för att skapa ett omfattande push-meddelande och förser sedan programmet med bilden, titeln och ikonen som ska visas i meddelandet.

   ![](assets/nmac_android_2.png)

1. Klicka **[!UICONTROL Finish]** och sen **[!UICONTROL Save]**. Android-programmet kan nu användas i Campaign Classic.

Nedan visas FCM-nyttolastsnamnen för att ytterligare anpassa ditt push-meddelande:

| Meddelandetyp | Konfigurerbart meddelandeelement (FCM-nyttolastnamn) | Konfigurerbara alternativ (FCM-nyttolastnamn) |
|:-:|:-:|:-:|
| datameddelande | N/A | dryRun |
| meddelande | title, body, android_channel_id, icon, sound, tag, color, click_action <br> | dryRun |

<br>

## Skapa ett multimediemeddelande från Android {#creating-android-delivery}

Med Firebase Cloud Messaging kan du välja mellan två typer av meddelanden:

* **[!UICONTROL Data message]**, hanteras av klientprogrammet.
   <br>Meddelanden skickas direkt till mobilprogrammet som genererar och visar android-meddelandet till enheten. Datameddelanden innehåller bara dina anpassade programvariabler.

* **[!UICONTROL Notification message]**, hanteras automatiskt av FCM SDK.
   <br> FCM visar automatiskt meddelandet på användarnas enheter för klientprogrammets räkning. Meddelanden innehåller en fördefinierad uppsättning parametrar och alternativ, men de kan fortfarande anpassas ytterligare med anpassade programvariabler.

Mer information om meddelandetyper i Firebase Cloud finns i [FCM-dokumentationen](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages).

### Skapa ett datameddelande {#creating-data-message}

1. Gå till **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klicka på **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Välj **[!UICONTROL Deliver on Android (android)]** i **[!UICONTROL Delivery template]** listrutan. Lägg till en **[!UICONTROL Label]** till leveransen.

1. Klicka **[!UICONTROL To]** för att definiera målpopulationen. Som standard används **[!UICONTROL Subscriber application]** målmappningen. Klicka **[!UICONTROL Add]** för att välja tjänsten.

   ![](assets/nmac_android_7.png)

1. I **[!UICONTROL Target type]** fönstret markerar du **[!UICONTROL Subscribers of an Android mobile application]** och klickar **[!UICONTROL Next]**.

1. I **[!UICONTROL Service]** listrutan väljer du en tjänst som du skapat tidigare och klickar sedan på **[!UICONTROL Finish]**.
De **[!UICONTROL Application variables]** läggs automatiskt till beroende på vad som lades till under konfigurationsstegen.

   ![](assets/nmac_android_6.png)

1. Välj **[!UICONTROL data message]** som **[!UICONTROL Message Type]**.

1. Redigera dina meddelanden.

   ![](assets/nmac_android_5.png)

1. Du kan vid behov lägga till information i den tidigare konfigurationen **[!UICONTROL Application variables]** . **[!UICONTROL Application variables]** måste konfigureras i Android-tjänsten och är en del av den meddelandenyttolast som skickas till den mobila enheten.

1. Klicka **[!UICONTROL Save]** och skicka leveransen.

Bilden och webbsidan ska visas i push-meddelandet när de tas emot på prenumerantens mobila Android-enheter.

![](assets/nmac_android_4.png)

### Skapa ett meddelande {#creating-notification-message}

>[!NOTE]
>
>Ytterligare alternativ för meddelanden är bara tillgängliga med HTTP v1 API-konfiguration. Mer information om detta hittar du i det här [avsnittet](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1).

1. Gå till **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klicka på **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Välj **[!UICONTROL Deliver on Android (android)]** i **[!UICONTROL Delivery template]** listrutan. Lägg till en **[!UICONTROL Label]** till leveransen.

1. Klicka **[!UICONTROL To]** för att definiera målpopulationen. Som standard används **[!UICONTROL Subscriber application]** målmappningen. Klicka **[!UICONTROL Add]** för att välja tjänsten.

   ![](assets/nmac_android_7.png)

1. I **[!UICONTROL Target type]** fönstret markerar du **[!UICONTROL Subscribers of an Android mobile application]** och klickar **[!UICONTROL Next]**.

1. I **[!UICONTROL Service]** listrutan väljer du en tjänst som du skapat tidigare och klickar sedan på **[!UICONTROL Finish]**.

   ![](assets/nmac_android_6.png)

1. Välj **[!UICONTROL notification message]** som **[!UICONTROL Message Type]**.

1. Lägg till en titel och redigera meddelandet. Anpassa push-meddelanden med **[!UICONTROL Notification options]**:

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
   * **[!UICONTROL Notification Priority]**: Ange prioritetsnivåerna för dina meddelanden till standard, minimum, low eller high. For more on this, refer to [FCM documentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**: Ange visningsnivåerna för meddelandet till public, private eller secrets. For more on this, refer to [FCM documentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   Mer information om **[!UICONTROL HTTP v1 additional options]** och hur du fyller i dessa fält finns i [FCM-dokumentationen](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_9.png)

1. Du kan vid behov lägga till information i den tidigare konfigurationen **[!UICONTROL Application variables]** . **[!UICONTROL Application variables]** måste konfigureras i Android-tjänsten och är en del av den meddelandenyttolast som skickas till den mobila enheten.

1. Klicka **[!UICONTROL Save]** och skicka leveransen.

Bilden och webbsidan ska visas i push-meddelandet när de tas emot på prenumerantens mobila Android-enheter.
