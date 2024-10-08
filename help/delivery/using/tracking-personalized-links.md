---
product: campaign
title: Kom igång med spårning av personaliserade länkar
description: Lär dig skriva länkar i e-postmeddelanden som kan personaliseras och supportspårning i Campaign
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Personalization
role: User
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 7%

---

# Kom igång med spårning av personaliserade länkar {#tracking-personalized-links}

Länkarna i e-postinnehåll som innehåller personalisering måste spåras med specifik syntax.

Med JavaScript i e-postinnehåll (HTML eller Text) kan du generera och skicka dynamiskt innehåll till mottagarna, med två begränsningar:

* Skriptet kan inte komma åt databasen direkt (SQL-funktionen och API-funktionerna är inte tillgängliga),
* Adobe Campaign måste kunna identifiera URL:er så att länkar kan spåras. [Läs mer](detecting-tracking-urls.md)

Du kan lägga till specifika förbearbetningsinstruktioner för att skripta URL:en och spåra den. [Läs mer](pre-processing-instructions.md)

För spårningsidentifiering bäddar Adobe Campaign in [Tidy](https://www.html-tidy.org/) för att tolka HTML-källan och identifiera mönstret. Här listas alla URL:er för innehållet så att de kan spåras individuellt. Adobe Campaign använder Tidy igen för att ersätta URL:en (`http://myurl.com`) med en URL som pekar på Adobe Campaign omdirigeringsserver.

I det ursprungliga innehållet ersätts till exempel `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` för en viss mottagare med: `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

Var:

* &quot;h&quot; betyder HTML (eller &quot;t&quot; för textinnehåll).
* 617791 är meddelande-ID:t / brustlogg-ID (hexadecimalt).
* 71ffa3 är NmsDelivery-ID (hexadecimalt).
* 71ffa8 är NmsTrackingUrl-ID (hexadecimalt).
* p1, p2 och så vidare, är alla parametrar som ska ersättas i URL:en.
