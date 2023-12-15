---
product: campaign
title: Skapa ett push-meddelande för Android-enheter
description: Lär dig hur du skapar push-meddelanden för Android
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Push
role: User, Developer, Data Engineer
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 9756f05e3887bc74578bae00138c4d1317a480f8
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 1%

---

# Skapa meddelanden för Android{#create-notificaations-android}

Använd Adobe Campaign för att skicka push-meddelanden på Android-enheter. Globala koncept för leveransskapande presenteras i [det här avsnittet](steps-about-delivery-creation-steps.md).

Börja med att skapa en ny leverans.

![](assets/nmac_delivery_1.png)

Med Firebase Cloud Messaging kan du välja mellan två typer av meddelanden:

* **[!UICONTROL Data message]**, hanteras av klientprogrammet.
  <br>Meddelanden skickas direkt till mobilprogrammet som genererar och visar android-meddelandet till enheten. Datameddelanden innehåller bara dina anpassade programvariabler.

* **[!UICONTROL Notification message]**, hanteras automatiskt av FCM SDK.
  <br> FCM visar automatiskt meddelandet på användarnas enheter för klientprogrammets räkning. Meddelanden innehåller en fördefinierad uppsättning parametrar och alternativ, men de kan fortfarande anpassas ytterligare med anpassade programvariabler.

Mer information om meddelandetyper i Firebase Cloud finns i [FCM-dokumentation](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages){target="_blank"}.


## Skapa ett datameddelande {#creating-data-message}

1. Gå till **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klicka på **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Välj **[!UICONTROL Deliver on Android (android)]** i **[!UICONTROL Delivery template]** nedrullningsbar meny. Lägg till en **[!UICONTROL Label]** till leveransen.

1. Klicka **[!UICONTROL To]** för att definiera målpopulationen. Som standard är **[!UICONTROL Subscriber application]** målmappning används. Klicka **[!UICONTROL Add]** för att välja din tjänst.

   ![](assets/nmac_android_7.png)

1. I **[!UICONTROL Target type]** fönster, markera **[!UICONTROL Subscribers of an Android mobile application]** och klicka **[!UICONTROL Next]**.

1. I **[!UICONTROL Service]** nedrullningsbar meny, välj en tjänst som du skapat tidigare och klicka sedan på **[!UICONTROL Finish]**.
The **[!UICONTROL Application variables]** läggs till automatiskt beroende på vad som lades till under konfigurationsstegen.

   ![](assets/nmac_android_6.png)

1. Välj **[!UICONTROL data message]** as **[!UICONTROL Message Type]**.

1. Redigera dina meddelanden.

   ![](assets/nmac_android_5.png)

1. Du kan lägga till information i din tidigare konfigurerade **[!UICONTROL Application variables]** vid behov. **[!UICONTROL Application variables]** måste konfigureras i Android-tjänsten och är en del av den meddelandenyttolast som skickas till den mobila enheten.

1. Klicka **[!UICONTROL Save]** och leverera.

Bilden och webbsidan ska visas i push-meddelandet när de tas emot på prenumerantens mobila Android-enheter.

![](assets/nmac_android_4.png)

## Skapa ett meddelande {#creating-notification-message}

![](assets/do-not-localize/how-to-video.png) [Lär dig hur du skapar ett push-meddelande för Android i en video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html#additional-resources){target="_blank"}.

1. Gå till **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klicka på **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Välj **[!UICONTROL Deliver on Android (android)]** i **[!UICONTROL Delivery template]** nedrullningsbar meny. Lägg till en **[!UICONTROL Label]** till leveransen.

1. Klicka **[!UICONTROL To]** för att definiera målpopulationen. Som standard är **[!UICONTROL Subscriber application]** målmappning används. Klicka **[!UICONTROL Add]** för att välja din tjänst.

   ![](assets/nmac_android_7.png)

1. I **[!UICONTROL Target type]** fönster, markera **[!UICONTROL Subscribers of an Android mobile application]** och klicka **[!UICONTROL Next]**.

1. I **[!UICONTROL Service]** nedrullningsbar meny, välj en tjänst som du skapat tidigare och klicka sedan på **[!UICONTROL Finish]**.

   ![](assets/nmac_android_6.png)

1. Välj **[!UICONTROL notification message]** as **[!UICONTROL Message Type]**.

1. Lägg till en titel och redigera meddelandet. Anpassa push-meddelanden med **[!UICONTROL Notification options]**:

   * **[!UICONTROL Channel ID]**: Ange kanal-ID för meddelandet. Appen måste skapa en kanal med det här channel-id:t innan något meddelande med det här channel-id:t tas emot.
   * **[!UICONTROL Sound]**: Ange att ljudet ska spelas upp när enheten får ditt meddelande.
   * **[!UICONTROL Color]**: Ange ikonfärgen för meddelandet.
   * **[!UICONTROL Icon]**: Ange meddelandeikonen som ska visas på dina profilers enheter.
   * **[!UICONTROL Tag]**: Ange den identifierare som ska användas för att ersätta befintliga meddelanden i meddelandelådan.
   * **[!UICONTROL Click action]**: Ange åtgärden som är kopplad till en användare genom att klicka på meddelandet.

   Mer information finns på **[!UICONTROL Notification options]** och hur du fyller i dessa fält, se [FCM-dokumentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"}.

   ![](assets/nmac_android_8.png)

1. Om ditt program har konfigurerats med HTTP v1 API-protokollet kan du anpassa ditt push-meddelande ytterligare med följande **[!UICONTROL HTTPV1 additional options]**:

   * **[!UICONTROL Ticker]**: Ange anteckningstexten för meddelandet. Endast tillgängligt för enheter med inställningen Android 5.0 Lollipop.
   * **[!UICONTROL Image]**: Ange bildens URL som ska visas i meddelandet.
   * **[!UICONTROL Notification Count]**: Ange antalet nya olästa uppgifter som ska visas direkt på programikonen.
   * **[!UICONTROL Sticky]**: Ange som true eller false. Om värdet är false ignoreras meddelandet automatiskt när användaren klickar på det. Om värdet är true visas meddelandet fortfarande även när användaren klickar på det.
   * **[!UICONTROL Notification Priority]**: Ange prioritetsnivåerna för dina meddelanden till standard, minimum, low eller high. Mer information finns i [FCM-dokumentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**: Ange synlighetsnivåerna för dina meddelanden till public, private eller secrets. Mer information finns i [FCM-dokumentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   Mer information finns på **[!UICONTROL HTTP v1 additional options]** och hur du fyller i dessa fält, se [FCM-dokumentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"}.

   ![](assets/nmac_android_9.png)

1. Du kan lägga till information i din tidigare konfigurerade **[!UICONTROL Application variables]** vid behov. **[!UICONTROL Application variables]** måste konfigureras i Android-tjänsten och är en del av den meddelandenyttolast som skickas till den mobila enheten.

1. Klicka **[!UICONTROL Save]** och leverera.

Bilden och webbsidan ska visas i push-meddelandet när de tas emot på prenumerantens mobila Android-enheter.
