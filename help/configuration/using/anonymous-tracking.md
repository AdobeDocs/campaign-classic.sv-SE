---
product: campaign
title: Anonym spårning
description: Lär dig hur du ställer in anonym spårning
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 5%

---

# Anonym spårning{#anonymous-tracking}

Med Adobe Campaign kan du länka insamlade webbspårningsdata till en mottagare när de bläddrar anonymt på din webbplats. När en användare bläddrar på de taggade sidorna på din webbplats registreras den här surfinformationen så att när användaren klickar i ett e-postmeddelande som skickas av Adobe Campaign identifieras de och informationen länkas automatiskt till dem.

>[!IMPORTANT]
>
>Om du konfigurerar anonym spårning på en webbplats kan en stor mängd spårningsloggar samlas in, vilket påverkar databasåtgärden. Var försiktig.\
>Spårningsloggar sparas i databasen tills spårningsdata rensas. Använd distributionsguiden för att konfigurera tömningsfrekvensen. Mer information om detta finns i [det här avsnittet](../../installation/using/deploying-an-instance.md#purging-data).

Om du vill aktivera anonym webbspårning för din instans måste följande element konfigureras:

* Parametern **trackWebVisitors** för elementet **redirection** i filen **serverConf.xml** för spårningsservern måste anges till **true** för att en permanent cookie (**uid230**) ska kunna placeras i webbläsare för okända Internetanvändare som besöker webbplatsen.
* Läget **Anonym webbspårning** måste väljas på spårningskonfigurationsskärmen i distributionsguiden.

  ![](assets/webtracking_anonymous_set.png)

* Webbformulär måste publiceras och köras på spårningsservern. Matchningsalternativet måste väljas i distributionsguiden.

  ![](assets/webtracking_publication_set_for_webapps.png)
