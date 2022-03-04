---
product: campaign
title: Leveranser över flera kanaler
description: Läs mer om flerkanalsleveranser
feature: Workflows, Channels Activity
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: e454cc29038b4eab9fad1dcb46813fc8e1a83db1
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 8%

---

# Leveranser över flera kanaler{#cross-channel-deliveries}

![](../../assets/common.svg)

Flerkanalsleveranser är tillgängliga i **[!UICONTROL Deliveries]** flik för kampanjarbetsflödesaktiviteter.

De olika kanalerna är:

* [E-post](../../delivery/using/about-email-channel.md)
* [Direktutskick](../../delivery/using/about-direct-mail-channel.md)
* [Mobil](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/publishing-on-twitter.md) (endast Campaign Classic v7)
* [Facebook](../../social/using/publishing-on-facebook.md) (endast Campaign Classic v7)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

Välj den mall som du vill basera leveransen på och definiera innehållet i mallen.

Du kan ange ett mål för leveransen uppströms arbetsflödet med hjälp av olika målinriktningsaktiviteter.

I exemplet nedan skapar vi ett arbetsflöde för att skicka ett e-postmeddelande eller ett SMS för prenumeranter på push-meddelanden och sedan ett push-meddelande en vecka senare. Så här gör du:

1. Skapa en kampanj.
1. I **[!UICONTROL Targeting and workflows]** fliken med kampanjen, lägg till en **[!UICONTROL Query]** till arbetsflödet.
1. Konfigurera frågan. Här väljer vi till exempel de mottagare som prenumererar på push-meddelanden som måldimension.

   >[!NOTE]
   >
   >För push-meddelanden använder du **prenumerationsprogram** måldimension.

   ![](assets/cross_channel_delivery_1.png)

1. Lägg till filtervillkoren i frågan. I det här fallet väljer vi mottagare som har ett mobilnummer eller en e-postadress.

   ![](assets/cross_channel_delivery_2.png)

1. Lägg till en **[!UICONTROL Split]** aktiviteter i ditt arbetsflöde för att dela upp mottagare som har ett mobilnummer och de som har en e-postadress.
1. I **[!UICONTROL Delivery]** väljer du en leverans för varje mål.

   Skapa leveransen på samma sätt som med en klassisk leveransguide genom att dubbelklicka på leveransaktiviteten i arbetsflödet. Se denna [sida](../../delivery/using/about-email-channel.md) för mer information om detta.

   ![](assets/cross_channel_delivery_3.png)

1. Lägg till och konfigurera en **[!UICONTROL Wait]** aktivitet för att mottagarna inte ska få för många leveranser samtidigt.
1. Lägg till en **[!UICONTROL Split]** aktiviteter för att dela upp prenumeranter av iOS- eller Android-mobilprogram.

   Välj en tjänst för vart och ett av operativsystemen. Mer information om hur du skapar tjänster finns i [page](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Välj och konfigurera en leverans av mobilapplikationer för vart och ett av operativsystemen.

   ![](assets/cross_channel_delivery_5.png)
