---
product: campaign
title: Om innehållshantering
description: Om innehållshantering
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: 87434cc2-1636-4558-ab60-255b7f873c0c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 3%

---

# Om innehållshantering{#about-content-management}

Adobe Campaign Content Manager-modulen är ett specifikt Campaign Classic [standardpaket](../../installation/using/installing-campaign-standard-packages.md) som du kan installera för att skapa återkommande nyhetsbrev eller webbplatser. Det kan hjälpa dig att skapa, validera och publicera meddelanden.

>[!NOTE]
>
>Det här avsnittet gäller modulen Innehållshantering. Mer information om hur du utformar innehåll för e-postleveranser finns i [det här avsnittet](../../delivery/using/defining-the-email-content.md).

Modulen Innehållshantering innehåller funktioner för arbetsgrupper, arbetsflöden och innehållssamling. Detta gör att ett meddelande kan formateras automatiskt: e-post, e-post, SMS, webb osv.

Genom att använda innehållshanteraren i en leverans kan du erbjuda inmatnings- eller urvalsfält till de operatorer som ansvarar för att skapa innehåll. Layouten och visningen av det här innehållet samt eventuella ändringar som görs hanteras automatiskt med formatmallen.

![](assets/s_ncs_content_create_content_sample.png)

>[!CAUTION]
>
>Alla ändringar som görs i formatmallen implementeras på leveransnivå baserat på de innehållsmallar som används.

Innehållshantering har följande fördelar:

* Strukturerad meddelanderedigering via indatagränssnitt,
* Separation av datainnehåll och hur det presenteras (genereras i XML-format).
* Dokumentgenerering i flera format (html, txt, XML osv.) som bygger på formatmallar för att säkerställa att grafiska tecken följs,
* Återställning och automatisk sammanställning av externa innehållsflöden.
* Samarbeta med arbetsflöden för datavalidering och -kontroll.

Det här sättet att skapa innehåll har dock vissa begränsningar. bland annat följande:

* Begränsad frihet när det gäller den slutliga dokumentdesignen.
* Kravanalysen måste vara rigorös så att slutanvändarna inte drabbas av en funktion som saknas.
