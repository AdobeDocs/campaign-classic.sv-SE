---
solution: Campaign Classic
product: campaign
title: Kom igång med spårning av personaliserade länkar
description: Lär dig hur du skriver länkar i e-postmeddelanden som kan personaliseras och supportspårning i Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 768fe62db4efd1217c22973c7e5dc31097d67bae
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 6%

---


# Kom igång med spårning av personaliserade länkar {#tracking-personalized-links}

Länkarna i e-postinnehåll som innehåller personalisering måste spåras med specifik syntax.

Med JavaScript i e-postinnehåll (HTML eller Text) kan du generera och skicka dynamiskt innehåll till mottagarna, med två begränsningar:

* Skriptet kan inte komma åt databasen direkt (SQL-funktionen och API-funktionerna är inte tillgängliga),
* Adobe Campaign måste kunna identifiera URL:er så att länkar kan spåras. [Läs mer](detecting-tracking-urls.md)

Du kan lägga till [specifika förbearbetningsinstruktioner](pre-processing-instructions.md) i dessa URL:er

förbearbetningsinstruktioner.

För spårningsidentifiering bäddar Adobe Campaign in [Tidy](http://www.html-tidy.org/) för att tolka HTML-källan och identifiera mönstret. Här listas alla URL:er för innehållet så att de kan spåras individuellt. Adobe Campaign använder Tidy igen för att ersätta URL:en (`http://myurl.com`) med en URL som pekar på Adobe Campaign omdirigeringsserver.

I det ursprungliga innehållet: `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` ersätts för en viss mottagare med: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Var:

* &quot;h&quot; betyder HTML-innehåll (eller &quot;t&quot; för textinnehåll).
* 617791 är meddelande-ID:t / brustlogg-ID (hexadecimalt).
* 71ffa3 är NmsDelivery-ID (hexadecimalt).
* 71ffa8 är NmsTrackingUrl-ID:t (hexadecimalt).
* p1, p2 och så vidare, är alla parametrar som ska ersättas i URL:en.
