---
product: campaign
title: Om innehållshantering
description: Kom igång med modulen Innehållshanteraren för Campaign
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Landing Pages, Email Design
role: User
exl-id: 87434cc2-1636-4558-ab60-255b7f873c0c
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 2%

---

# Om innehållshantering{#about-content-management}

Adobe Campaign Content Manager-modulen är ett specifikt [inbyggt Campaign Classic-paket](../../installation/using/installing-campaign-standard-packages.md) som du kan installera för att skapa återkommande nyhetsbrev eller webbplatser. Det kan hjälpa dig att skapa, validera och publicera meddelanden.

>[!NOTE]
>
>Det här avsnittet gäller modulen Innehållshantering. Mer information om hur du utformar innehåll för e-postleveranser finns i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=sv-SE){target="_blank"}.

Modulen Innehållshantering innehåller funktioner för arbetsgrupper, arbetsflöden och innehållssamling. Detta gör att ett meddelande kan formateras automatiskt: e-post, e-post, SMS, webb osv.

Genom att använda innehållshanteraren i en leverans kan du erbjuda inmatnings- eller urvalsfält till de operatorer som ansvarar för att skapa innehåll. Layouten och visningen av det här innehållet samt eventuella ändringar som görs hanteras automatiskt med formatmallen.

![](assets/s_ncs_content_create_content_sample.png)

>[!CAUTION]
>
>Alla ändringar som görs i formatmallen implementeras på leveransnivå baserat på de innehållsmallar som används.

Innehållshantering har följande fördelar:

* Strukturerad meddelanderedigering via indatagränssnitt,
* Separation av datainnehåll och hur det presenteras (genereras i XML-format).
* Dokumentgenerering i olika format (html, txt, XML osv.) som bygger på formatmallar för att säkerställa överensstämmelse med grafiska tecken,
* Återställning och automatisk sammanställning av externa innehållsflöden.
* Collaboration med arbetsflöde för datavalidering och -kontroll.

Det här sättet att skapa innehåll har dock vissa begränsningar, bland annat:

* Begränsad frihet när det gäller den slutliga dokumentdesignen.
* Kravanalysen måste vara rigorös så att slutanvändarna inte drabbas av en funktion som saknas.
