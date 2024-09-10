---
product: campaign
title: Leveranser över flera kanaler
description: Läs mer om flerkanalsleveranser
feature: Workflows, Channels Activity
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 6%

---

# Leveranser över flera kanaler{#cross-channel-deliveries}



Flerkanalsleveranser är tillgängliga på fliken **[!UICONTROL Deliveries]** för kampanjarbetsflödesaktiviteter.

De olika tillgängliga kanalerna är:

* [E-post](../../delivery/using/about-email-channel.md)
* [Direktutskick](../../delivery/using/about-direct-mail-channel.md)
* [Mobil](../../delivery/using/sms-channel.md)
* [X (tidigare Twitter)](../../social/using/about-social-marketing.md)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

Välj den mall som du vill basera leveransen på och definiera dess innehåll.

Du kan ange ett mål för leveransen uppströms arbetsflödet med hjälp av olika målinriktningsaktiviteter.

I exemplet nedan skapar vi ett arbetsflöde för att skicka ett e-postmeddelande eller ett SMS för prenumeranter på push-meddelanden och sedan ett push-meddelande en vecka senare. Så här gör du:

1. Skapa en kampanj.
1. Lägg till en **[!UICONTROL Query]** i arbetsflödet på fliken **[!UICONTROL Targeting and workflows]** i kampanjen.
1. Konfigurera frågan. Här väljer vi till exempel de mottagare som prenumererar på push-meddelanden som måldimension.

   >[!NOTE]
   >
   >Använd måldimensionen för **prenumerantprogram** för push-meddelanden.

   ![](assets/cross_channel_delivery_1.png)

1. Lägg till filtervillkoren i frågan. I det här fallet väljer vi mottagare som har ett mobilnummer eller en e-postadress.

   ![](assets/cross_channel_delivery_2.png)

1. Lägg till en **[!UICONTROL Split]**-aktivitet i arbetsflödet för att dela upp mottagare som har ett mobilnummer och de som har en e-postadress.
1. Välj en leverans för varje mål på fliken **[!UICONTROL Delivery]**.

   Skapa leveransen på samma sätt som med en klassisk leveransassistent genom att dubbelklicka på leveransaktiviteten i arbetsflödet. Se denna [sida](../../delivery/using/about-email-channel.md) för mer information om detta.

   ![](assets/cross_channel_delivery_3.png)

1. Lägg till och konfigurera en **[!UICONTROL Wait]**-aktivitet för att mottagarna inte ska få för många leveranser samtidigt.
1. Lägg till en **[!UICONTROL Split]**-aktivitet för att dela upp prenumeranter på ett iOS- eller Android-mobilprogram.

   Välj en tjänst för vart och ett av operativsystemen. Mer information om hur du skapar tjänster finns på [sidan](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. Välj och konfigurera en leverans av mobilapplikationer för vart och ett av operativsystemen.

   ![](assets/cross_channel_delivery_5.png)
