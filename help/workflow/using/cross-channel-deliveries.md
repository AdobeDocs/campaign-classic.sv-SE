---
title: Leveranser över flera kanaler
seo-title: Leveranser över flera kanaler
description: Leveranser över flera kanaler
seo-description: null
page-status-flag: never-activated
uuid: 191ff39e-f739-48b3-8865-ad1b641b7499
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 8dda45b4-4b5d-4b4e-a8b4-45d9bc49aaf3
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 8%

---


# Leveranser över flera kanaler{#cross-channel-deliveries}

Flerkanalsleveranser är tillgängliga på fliken **[!UICONTROL Deliveries]** för kampanjarbetsflödesaktiviteter.

Med dem kan du skapa en leverans som är specifik för en viss kanal. Du kan ange den mall som du vill basera leveransen på samt innehållet i den, på samma sätt som med en klassisk leveransguide.

De olika kanalerna är:

* [E-post](../../delivery/using/about-email-channel.md)
* [Direktreklam](../../delivery/using/about-direct-mail-channel.md)
* [Mobil](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/publishing-on-twitter.md)
* [Facebook](../../social/using/publishing-on-facebook.md)
* [iOS](../../delivery/using/creating-notifications.md#sending-notifications-on-ios)
* [Android](../../delivery/using/creating-notifications.md#sending-notifications-on-android)

Du kan ange ett mål för leveransen uppströms arbetsflödet med hjälp av olika målinriktningsaktiviteter.

Här skapar vi t.ex. ett arbetsflöde för att skicka ett e-postmeddelande eller ett SMS för prenumeranter på push-meddelanden, och sedan ett push-meddelande en vecka senare. Så här gör du:

1. Skapa en kampanj.
1. Lägg till en **[!UICONTROL Targeting and workflows]** funktion i arbetsflödet på fliken **[!UICONTROL Query]** i kampanjen.
1. Konfigurera frågan. Här väljer vi till exempel de mottagare som prenumererar på push-meddelanden som måldimension.

   >[!NOTE]
   >
   >Kom ihåg att använda måldimensionen för **prenumerationsprogram** för push-meddelanden.

   ![](assets/cross_channel_delivery_1.png)

1. Lägg till filtervillkoren i frågan. I det här fallet väljer vi mottagare som har ett mobilnummer eller en e-postadress.

   ![](assets/cross_channel_delivery_2.png)

1. Lägg till en **[!UICONTROL Split]** aktivitet i arbetsflödet för att dela upp mottagare som har ett mobilnummer och de som har en e-postadress.
1. Välj en leverans för varje mål på **[!UICONTROL Delivery]** fliken.

   Skapa leveransen på samma sätt som med en klassisk leveransguide genom att dubbelklicka på leveransaktiviteten i arbetsflödet. Se denna [sida](../../delivery/using/about-email-channel.md) för mer information om detta.

   ![](assets/cross_channel_delivery_3.png)

1. Lägg till och konfigurera en **[!UICONTROL Wait]** aktivitet för att mottagarna inte ska få för många leveranser samtidigt.
1. Lägg till en **[!UICONTROL Split]** aktivitet för att dela upp prenumeranter på ett iOS- eller Android-mobilprogram.

   Välj en tjänst för vart och ett av operativsystemen. For more on service creation, refer to this [page](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Välj och konfigurera en leverans av mobilapplikationer för vart och ett av operativsystemen.

   ![](assets/cross_channel_delivery_5.png)
