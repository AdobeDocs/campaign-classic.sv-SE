---
title: Flerkanalsleveranser
seo-title: Flerkanalsleveranser
description: Flerkanalsleveranser
seo-description: null
page-status-flag: never-activated
uuid: 191ff39e-f739-48b3-8865-ad1b641b7499
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 8dda45b4-4b5d-4b4e-a8b4-45d9bc49aaf3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Flerkanalsleveranser{#cross-channel-deliveries}

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

   Skapa leveransen på samma sätt som med en klassisk leveransguide genom att dubbelklicka på leveransaktiviteten i arbetsflödet. Mer information finns på den här [sidan](../../delivery/using/about-email-channel.md).

   ![](assets/cross_channel_delivery_3.png)

1. Lägg till och konfigurera en **[!UICONTROL Wait]** aktivitet för att mottagarna inte ska få för många leveranser samtidigt.
1. Lägg till en **[!UICONTROL Split]** aktivitet för att dela upp prenumeranter av iOS- eller Android-mobilprogram.

   Välj en tjänst för vart och ett av operativsystemen. Mer information om hur du skapar tjänster finns på den här [sidan](../../delivery/using/setting-up-mobile-app-channel.md#creating-the-service-and-collecting-subscriptions).

   ![](assets/cross_channel_delivery_4.png)

1. Välj och konfigurera en leverans av mobilapplikationer för vart och ett av operativsystemen.

   ![](assets/cross_channel_delivery_5.png)

