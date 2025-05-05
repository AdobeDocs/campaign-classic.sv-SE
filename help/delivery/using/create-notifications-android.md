---
product: campaign
title: Skapa ett push-meddelande för Android-enheter
description: Lär dig skapa push-meddelanden för Android
feature: Push
role: User, Developer, Data Engineer
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Skapa meddelanden för Android{#create-notificaations-android}

Använd Adobe Campaign för att skicka push-meddelanden på Android-enheter. Globala koncept för leveransskapande presenteras i [det här avsnittet](steps-about-delivery-creation-steps.md).

Börja med att skapa en ny leverans.

![](assets/nmac_delivery_1.png)

Med Firebase Cloud Messaging kan du välja mellan två typer av meddelanden:

* **[!UICONTROL Data message]**, hanteras av klientprogrammet.
  <br>Meddelanden skickas direkt till mobilprogrammet som genererar och visar android-meddelandet till enheten. Datameddelanden innehåller bara dina anpassade programvariabler.

* **[!UICONTROL Notification message]**, hanteras automatiskt av FCM SDK.
  <br> FCM visar automatiskt meddelandet på dina användares enheter för klientprogrammets räkning. Meddelanden innehåller en fördefinierad uppsättning parametrar och alternativ, men de kan fortfarande anpassas ytterligare med anpassade programvariabler.

Mer information om meddelandetyper i Firebase Cloud finns i [FCM-dokumentationen](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages){target="_blank"}.


## Skapa ett datameddelande {#creating-data-message}

1. Gå till **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klicka på **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Välj **[!UICONTROL Deliver on Android (android)]** i listrutan **[!UICONTROL Delivery template]**. Lägg till en **[!UICONTROL Label]** i leveransen.

1. Klicka på **[!UICONTROL To]** för att definiera målpopulationen. Målmappningen **[!UICONTROL Subscriber application]** används som standard. Klicka på **[!UICONTROL Add]** för att välja tjänsten.

   ![](assets/nmac_android_7.png)

1. I fönstret **[!UICONTROL Target type]** väljer du **[!UICONTROL Subscribers of an Android mobile application]** och klickar på **[!UICONTROL Next]**.

1. I listrutan **[!UICONTROL Service]** väljer du den tjänst du skapat tidigare och sedan programmet och klickar på **[!UICONTROL Finish]**.
**[!UICONTROL Application variables]** läggs till automatiskt beroende på vad som lades till under konfigurationsstegen.

   ![](assets/nmac_android_6.png)

1. Välj **[!UICONTROL data message]** som **[!UICONTROL Message Type]**.

1. Redigera dina meddelanden.

   ![](assets/nmac_android_5.png)

1. Du kan lägga till information i din tidigare konfigurerade **[!UICONTROL Application variables]** om det behövs. **[!UICONTROL Application variables]** måste konfigureras i Android-tjänsten och är en del av den meddelandenyttolast som skickas till den mobila enheten.

1. Klicka på **[!UICONTROL Save]** och skicka leveransen.

Bilden och webbsidan ska visas i push-meddelandet när de tas emot på prenumerantens mobila Android-enheter.

![](assets/nmac_android_4.png)

## Skapa ett meddelande {#creating-notification-message}

![](assets/do-not-localize/how-to-video.png) [Lär dig hur du skapar ett push-meddelande från Android i en video](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html?lang=sv-SE#additional-resources){target="_blank"}.

1. Gå till **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klicka på **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Välj **[!UICONTROL Deliver on Android (android)]** i listrutan **[!UICONTROL Delivery template]**. Lägg till en **[!UICONTROL Label]** i leveransen.

1. Klicka på **[!UICONTROL To]** för att definiera målpopulationen. Målmappningen **[!UICONTROL Subscriber application]** används som standard. Klicka på **[!UICONTROL Add]** för att välja tjänsten.

   ![](assets/nmac_android_7.png)

1. I fönstret **[!UICONTROL Target type]** väljer du **[!UICONTROL Subscribers of an Android mobile application]** och klickar på **[!UICONTROL Next]**.

1. I listrutan **[!UICONTROL Service]** väljer du den tjänst du skapat tidigare och sedan programmet och klickar på **[!UICONTROL Finish]**.

   ![](assets/nmac_android_6.png)

1. Välj **[!UICONTROL notification message]** som **[!UICONTROL Message Type]**.

1. Lägg till en titel och redigera meddelandet. Anpassa ditt push-meddelande med **[!UICONTROL Notification options]**:

   * **[!UICONTROL Channel ID]**: Ange meddelandets kanal-ID. Appen måste skapa en kanal med det här channel-id:t innan något meddelande med det här channel-id:t tas emot.
   * **[!UICONTROL Sound]**: Ange att ljudet ska spelas upp när enheten får ditt meddelande.
   * **[!UICONTROL Color]**: Ange ikonfärgen för meddelandet.
   * **[!UICONTROL Icon]**: Ange att meddelandeikonen ska visas på dina profilers enheter.
   * **[!UICONTROL Tag]**: Ange den identifierare som ska användas för att ersätta befintliga meddelanden i meddelandelådan.
   * **[!UICONTROL Click action]**: Ange den åtgärd som är associerad med en användare genom att klicka på meddelandet.

   Mer information om **[!UICONTROL Notification options]** och hur du fyller i fälten finns i [FCM-dokumentationen](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"}.

   ![](assets/nmac_android_8.png)

1. Om ditt program har konfigurerats med HTTP v1 API-protokoll kan du anpassa ditt push-meddelande ytterligare med följande **[!UICONTROL HTTPV1 additional options]**:

   * **[!UICONTROL Ticker]**: Ange anteckningstexten för meddelandet. Endast tillgängligt för enheter med inställningen Android 5.0 Lollipop.
   * **[!UICONTROL Image]**: Ange bildens URL som ska visas i meddelandet.
   * **[!UICONTROL Notification Count]**: Ange antalet nya olästa uppgifter som ska visas direkt på programikonen.
   * **[!UICONTROL Sticky]**: Ange som sant eller falskt. Om värdet är false ignoreras meddelandet automatiskt när användaren klickar på det. Om värdet är true visas meddelandet fortfarande även när användaren klickar på det.
   * **[!UICONTROL Notification Priority]**: Ange prioritetsnivåerna för ditt meddelande till standard, minimum, low eller high. Mer information finns i [FCM-dokumentationen](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**: Ange synlighetsnivåerna för meddelandet till public, private eller secrets. Mer information finns i [FCM-dokumentationen](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   Mer information om **[!UICONTROL HTTP v1 additional options]** och hur du fyller i fälten finns i [FCM-dokumentationen](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"}.

   ![](assets/nmac_android_9.png)

1. Du kan lägga till information i din tidigare konfigurerade **[!UICONTROL Application variables]** om det behövs. **[!UICONTROL Application variables]** måste konfigureras i Android-tjänsten och är en del av den meddelandenyttolast som skickas till den mobila enheten.

1. Klicka på **[!UICONTROL Save]** och skicka leveransen.

Bilden och webbsidan ska visas i push-meddelandet när de tas emot på prenumerantens mobila Android-enheter.
