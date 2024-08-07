---
product: campaign
title: Identifierar spårnings-URL:er
description: Läs mer om rekommenderat mönster för att spåra URL:er
feature: Monitoring
role: User, Developer, Data Engineer
exl-id: 7611d6a1-6c55-4ba3-b905-58426c944991
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 2%

---

# Identifiera spårnings-URL:er

## Exempel på icke-identifiering

`<%= getURL("http://mynewsletter.com") %>` fungerar och skickar det faktiska innehållet på webbsidan via e-post till mottagarna. Men ingen länk spåras. Orsaken till detta är att MTA kör `"<%=getURL(..."` för varje e-postmeddelande innan det skickas. Det kan vara olika för varje mottagare, så Adobe Campaign kan inte känna till URL:erna för att spåra och tilldela dem ett tagg-ID.

När sidan som ska hämtas är densamma för alla mottagare är det bästa sättet att göra följande:

`<%@ include url="http://mynewsletter.com" %>`

I så fall hämtas sidan under analysen, innan spårningsidentifieringen. Det gör att Adobe Campaign kan identifiera länkarna, tilldela ett tagg-ID och spåra dem.

## Rekommenderat mönster

Efter bearbetning av `<%@`-instruktioner har URL:en som ska spåras följande syntax: `<a href="http://myurl.com/a.php?param1=aaa&param2=<%=escapeUrl(recipient.xxx)%>&param3=<%=escapeUrl(recipient.xxx)%>">`

>[!IMPORTANT]
>
>Alla andra mönster stöds inte av Adobe och bör undvikas för att förhindra potentiella säkerhetsluckor.

## Oskyddat mönster

När du lägger till anpassade länkar till ditt innehåll bör du alltid undvika att ha en personalisering i värdnamnsdelen av webbadressen för att undvika eventuella säkerhetsbrister. Läs mer på [den här sidan](../../installation/using/privacy.md#url-personalization).

Syntaxen `<a href="http://<%=myURL%>">` är till exempel **inte säker** och måste undvikas.

* Om du använder den här syntaxen kan det leda till säkerhetsproblem om länken som genereras av Adobe Campaign innehåller en eller flera parametrar.
* Tidy kan korrigera vissa av länkarna felaktigt, vilket kan hända slumpmässigt. Det typiska symtomet är HTML som visas i e-postkorrekturet men inte i förhandsgranskningen.
* Det går inte att ta bort URL-adressen eftersom vissa tecken i URL-adressen kan orsaka problem.
* Du kan inte ha en parameter med namnet ID som står i konflikt med parametern i omdirigerings-URL:en.
* Spårningsintresset begränsas sedan till leveransstatistik eftersom Adobe Campaign automatiskt spårar alla möjliga värden för myURL.
