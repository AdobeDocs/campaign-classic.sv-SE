---
product: campaign
title: Kom igång med spårning av personaliserade länkar
description: Lär dig hur du skriver länkar i e-postmeddelanden som kan personaliseras och supportspårning i Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---

# Kom igång med spårning av personaliserade länkar {#tracking-personalized-links}

![](../../assets/common.svg)

Länkarna i e-postinnehåll som innehåller personalisering måste spåras med specifik syntax.

Med JavaScript i e-postinnehåll (HTML eller Text) kan du generera och skicka dynamiskt innehåll till mottagarna, med två begränsningar:

* Skriptet kan inte komma åt databasen direkt (SQL-funktionen och API-funktionerna är inte tillgängliga),
* Adobe Campaign måste kunna identifiera URL:er så att länkar kan spåras. [Läs mer](detecting-tracking-urls.md)

Du kan lägga till specifika förbearbetningsinstruktioner för att skripta URL:en och spåra den. [Läs mer](pre-processing-instructions.md)

För spårningsidentifiering bäddar Adobe Campaign in [Tidy](https://www.html-tidy.org/) för att tolka HTML-källan och identifiera mönstret. Här listas alla URL:er för innehållet så att de kan spåras individuellt. Adobe Campaign använder Tidy igen för att ersätta URL:en (`http://myurl.com`) med en URL som pekar på Adobe Campaign omdirigeringsserver.

I det ursprungliga innehållet: `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` ersätts för en viss mottagare med: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Var:

* &quot;h&quot; betyder HTML-innehåll (eller &quot;t&quot; för textinnehåll).
* 617791 är meddelande-ID:t / brustlogg-ID (hexadecimalt).
* 71ffa3 är NmsDelivery-ID (hexadecimalt).
* 71ffa8 är NmsTrackingUrl-ID:t (hexadecimalt).
* p1, p2 och så vidare, är alla parametrar som ska ersättas i URL:en.
