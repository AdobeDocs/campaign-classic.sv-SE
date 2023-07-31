---
product: campaign
title: Anonym spårning
description: Lär dig hur du ställer in anonym spårning
feature: Configuration, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 5%

---

# Anonym spårning{#anonymous-tracking}

Med Adobe Campaign kan du länka insamlade webbspårningsdata till en mottagare när de bläddrar anonymt på din webbplats. När en användare bläddrar på de taggade sidorna på din webbplats registreras den här surfinformationen så att när användaren klickar i ett e-postmeddelande som skickas av Adobe Campaign identifieras de och informationen länkas automatiskt till dem.

>[!IMPORTANT]
>
>Om du konfigurerar anonym spårning på en webbplats kan en stor mängd spårningsloggar samlas in, vilket påverkar databasåtgärden. Var försiktig.\
>Spårningsloggar sparas i databasen tills spårningsdata rensas. Använd distributionsguiden för att konfigurera tömningsfrekvensen. Mer information om detta finns i [det här avsnittet](../../installation/using/deploying-an-instance.md#purging-data).

Om du vill aktivera anonym webbspårning för din instans måste följande element konfigureras:

* The **trackWebVisitors** parametern för **omdirigering** -elementet i **serverConf.xml** spårningsserverns fil måste anges till **true**&#39;, placera en permanent cookie (**uuid230**) i webbläsarna för okända internetanvändare som besöker webbplatsen.
* The **Anonym webbspårning** Du måste välja läge på spårningskonfigurationsskärmen i distributionsguiden.

  ![](assets/webtracking_anonymous_set.png)

* Webbformulär måste publiceras och köras på spårningsservern. Matchningsalternativet måste väljas i distributionsguiden.

  ![](assets/webtracking_publication_set_for_webapps.png)
