---
title: Anonym spårning
seo-title: Anonym spårning
description: Anonym spårning
seo-description: null
page-status-flag: never-activated
uuid: 21ba3657-eabf-4228-9fc0-e72712bf8fe7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 2d2c6ae9-4dba-4b82-a25e-eda65a49572d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Anonym spårning{#anonymous-tracking}

Med Adobe Campaign kan ni länka insamlade webbspårningsdata till en mottagare när de surfar anonymt på er webbplats. När en användare bläddrar på de taggade sidorna på din webbplats samlas den här surfinformationen in, så att när användaren klickar i ett e-postmeddelande som skickas av Adobe Campaign identifieras de och informationen länkas automatiskt till dem.

>[!IMPORTANT]
>
>Om du konfigurerar anonym spårning på en webbplats kan en stor mängd spårningsloggar samlas in, vilket påverkar databasåtgärden. Var försiktig.\
>Spårningsloggar sparas i databasen tills spårningsdata rensas. Använd distributionsguiden för att konfigurera tömningsfrekvensen. Mer information finns i [det här avsnittet](../../installation/using/deploying-an-instance.md#purging-data).

Om du vill aktivera anonym webbspårning för din instans måste följande element konfigureras:

* Parametern **trackWebVisitors** för **omdirigeringselementet** i spårningsserverns **serverConf.xml** -fil måste anges till **true** för att en permanent cookie (**uid230**) ska kunna placeras i webbläsare för okända Internetanvändare som besöker webbplatsen.
* Läget för **anonym webbspårning** måste väljas på konfigurationsskärmen för spårning i distributionsguiden.

   ![](assets/webtracking_anonymous_set.png)

* Webbformulär och enkäter måste publiceras och köras på spårningsservern. Matchningsalternativet måste väljas i distributionsguiden.

   ![](assets/webtracking_publication_set_for_webapps.png)

