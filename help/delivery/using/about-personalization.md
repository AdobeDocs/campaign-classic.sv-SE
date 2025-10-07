---
product: campaign
title: Kom igång med personalisering
description: Lär dig hur du personaliserar meddelanden och använder villkorat innehåll i Campaign
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Personalization
role: User
exl-id: 555082a2-1b62-4aa4-b80c-77b1a1ef9491
source-git-commit: a1e9fec0e9c85bf25b79e24a7432dfb45bd1a0cb
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 12%

---

# Kom igång med personalisering{#about-personalization}

Meddelanden som skickas av Adobe Campaign kan personaliseras på flera olika sätt både när det gäller innehåll och utseende. Dessa sätt kan kombineras enligt kriterier som har tagits specifikt från mottagarprofilerna. För e-postleveranser kan du definiera elementen och anpassningsvillkoren för en leverans direkt i JavaScript på fliken **[!UICONTROL Source]** i meddelandet. I allmänhet kan du med Adobe Campaign:

* Anpassa meddelandeformatet. Se [Meddelandeinnehåll](defining-the-email-content.md#message-content).
* Infoga dynamiska personaliseringsfält. Se [Anpassningsfält](personalization-fields.md).
* Infoga fördefinierade personaliseringsblock. Se [Personaliseringsblock](personalization-blocks.md).
* Skapa villkorsstyrt innehåll. Se avsnittet [Villkorligt innehåll](conditional-content.md).

>[!CAUTION]
>
>Följande variabler är interna variabler som kan användas för personalisering, men som inte får ändras: **delivery**, **message**, **dataSource**, **targetData**, **provider**, **coupon**, **couponValue**, **position**.


Med Adobe Campaign kan ni skräddarsy era leveranser för att skicka meddelanden som matchar mottagarnas profiler och intressen.

Personalization hjälper er att göra budskapen mer relevanta och engagerande. Du kan använda mottagardata för att anpassa innehåll, lägga till dynamiska fält eller visa annan information baserat på villkor. Läs om hur du konfigurerar och använder personaliseringsfunktioner i dina leveranser i [Adobe Campaign v8-dokumentationen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=sv-SE){target=_blank}.

Som en del av kampanjsatsningen v8 har Campaign Classic-dokumentationen omstrukturerats. Gemensamma funktioner är nu bara tillgängliga i Campaign v8-dokumentationsuppsättningen.

>[!BEGINTABS]

>[!TAB Dokumentation för innehållspersonalisering]

Mer information om innehållspersonalisering finns i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=sv-SE){target=_blank}.


[![bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=sv-SE){target=_blank}


>[!TAB Skapa e-postleverans]

Läs om hur du skapar e-postleveranser i dokumentationen för Campaign v8:

* [Skapa en e-postleverans](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email.html?lang=sv-SE){target="_blank"}: Lär dig mer om de olika stegen som krävs för att skapa en e-postleverans.
* [Definiera e-postinnehållet](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=sv-SE){target="_blank"}: Definiera vad e-postmeddelandet ska innehålla: avsändare, ämne, innehåll, bilder.
* [Definiera interaktivt innehåll](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-interactive-content.html?lang=sv-SE){target="_blank"}: Använd den interaktiva AMP för e-post-format för att skicka dynamiska e-postmeddelanden.
* [Skicka e-post på japanska mobiler](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/sending-emails-on-japanese-mobiles.html?lang=sv-SE){target="_blank"}: Använd ett av de tre specifika japanska formaten för e-post på mobiler.
* [Bifoga filer i ett e-postmeddelande](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html?lang=sv-SE){target="_blank"}: Lär dig olika sätt att bifoga en eller flera filer i ett e-postmeddelande.


>[!TAB E-postparametrar]

Läs dessa sidor för att lära dig mer om e-postparametrar i dokumentationen för Campaign v8:

* [Länk till spegelsidan](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/mirror-page.html?lang=sv-SE){target="_blank"}: Konfigurera spegelsidan så att dina klienter alltid får bästa återgivningsresultat.
* [Lägg till en BCC-adress](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-bcc.html?lang=sv-SE){target="_blank"}: Konfigurera Adobe Campaign för att behålla en kopia av e-postmeddelanden som skickas från din plattform.
* [Definiera ytterligare e-postparametrar](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-parameters.html?lang=sv-SE){target="_blank"}: Lär dig mer om de alternativ och parametrar som är tillgängliga från leveransegenskaperna.

Se även den här [sidan](sending-with-enhanced-mta.md) om du vill veta mer om den förbättrade MTA-filen.

>[!ENDTABS]





<!--
Adobe Campaign lets you mass deliver personalized electronic messages to a target population.

Before starting sending emails:

* Make sure recipient profiles contain at least an email address.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).
* Read out these sections to learn more about Deliverability: [Deliverability management in Campaign](about-deliverability.md) and [Deliverability best practices guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv-SE).

The key steps to send an email are as follows:

* [Create an email delivery](creating-an-email-delivery.md)
* [Define the target population](steps-defining-the-target-population.md)
* [Define the email content](defining-the-email-content.md)
* [Send the email](sending-messages.md)
* [Monitor the delivery](about-delivery-monitoring.md)

The sections below provide information that is specific to the email channel. For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).
-->