---
solution: Campaign Classic
product: campaign
title: Identifiera spårnings-URL:er
description: Läs mer om rekommenderat mönster för att spåra URL:er.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---


# Identifiera spårnings-URL:er

## Exempel på icke-identifiering

`<%= getURL("http://mynewsletter.com") %>` fungerar och skickar det faktiska innehållet på webbsidan via e-post till mottagarna. Men ingen av länkarna spåras. Orsaken till detta är att MTA kör `"<%=getURL(..."` för varje e-postmeddelande innan det skickas. Det kan vara olika för varje mottagare, så Adobe Campaign kan inte känna till URL:erna för att spåra och tilldela dem ett tagg-ID.

När sidan som ska hämtas är densamma för alla mottagare är det bästa sättet att göra följande:

`<%@ include url="http://mynewsletter.com" %>`

I så fall hämtas sidan under analysen, innan spårningsidentifieringen. Det gör att Adobe Campaign kan identifiera länkarna, tilldela ett tagg-ID och spåra dem.

## Rekommenderat mönster

Efter bearbetning av `<%@`-instruktioner har URL:en som ska spåras följande syntax: `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Alla andra mönster stöds inte av Adobe och bör undvikas för att förhindra potentiella säkerhetsluckor.

## Varningar för http://&lt;%=myURL%>-mönster

Syntaxen `<a href="http://<%=myURL%>">` är inte säker och rekommenderas inte eftersom:

* Tidy kan korrigera vissa av länkarna felaktigt, vilket kan hända slumpmässigt. Det typiska symtomet är HTML-kod som visas i e-postkorrekturet men inte i förhandsgranskningen.
* Det går inte att ta bort URL-adressen eftersom vissa tecken i URL-adressen kan orsaka problem.
* Du kan inte ha en parameter med namnet ID som står i konflikt med parametern i omdirigerings-URL:en.
* Spårningsintresset begränsas sedan till leveransstatistik eftersom Adobe Campaign automatiskt spårar alla möjliga värden för myURL.

Mer information finns på [den här sidan](https://helpx.adobe.com/campaign/kb/acc-security.html#privacy).

