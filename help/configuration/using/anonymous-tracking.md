---
solution: Campaign Classic
product: campaign
title: Anonym spårning
description: Anonym spårning
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 6%

---


# Anonym spårning{#anonymous-tracking}

Med Adobe Campaign kan du länka insamlade webbspårningsdata till en mottagare när de bläddrar anonymt på din webbplats. När en användare bläddrar på de taggade sidorna på din webbplats registreras den här surfinformationen så att när användaren klickar i ett e-postmeddelande som skickas av Adobe Campaign identifieras de och informationen länkas automatiskt till dem.

>[!IMPORTANT]
>
>Om du konfigurerar anonym spårning på en webbplats kan en stor mängd spårningsloggar samlas in, vilket påverkar databasåtgärden. Var försiktig.\
>Spårningsloggar sparas i databasen tills spårningsdata rensas. Använd distributionsguiden för att konfigurera tömningsfrekvensen. Mer information om detta finns i [det här avsnittet](../../installation/using/deploying-an-instance.md#purging-data).

Om du vill aktivera anonym webbspårning för din instans måste följande element konfigureras:

* Parametern **trackWebVisitors** för **omdirigeringselementet** i spårningsserverns **serverConf.xml** -fil måste anges till **true** för att en permanent cookie (**uid230**) ska kunna placeras i webbläsare för okända Internetanvändare som besöker webbplatsen.
* Läget för **anonym webbspårning** måste väljas på konfigurationsskärmen för spårning i distributionsguiden.

   ![](assets/webtracking_anonymous_set.png)

* Webbformulär och enkäter måste publiceras och köras på spårningsservern. Matchningsalternativet måste väljas i distributionsguiden.

   ![](assets/webtracking_publication_set_for_webapps.png)

