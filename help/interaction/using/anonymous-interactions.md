---
solution: Campaign Classic
product: campaign
title: Anonyma interaktioner
description: Anonyma interaktioner
audience: interaction
content-type: reference
topic-tags: unitary-interactions
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 1%

---


# Anonyma interaktioner{#anonymous-interactions}

![](assets/do-not-localize/how-to-video.png) Titta på den här  [](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com) videon för att få en översikt över hur erbjudanden levereras till identifierade och anonyma mål.

## Målgruppsanpassning och lagring av en miljö för anonyma interaktioner {#targeting-and-storing-an-environment-for-anonymous-interactions}

Som standard levereras Interaction med en förkonfigurerad miljö för att rikta sig till mottagartabellen (identifierade erbjudanden). Om du vill skapa en annan tabell (besökstabell för anonyma erbjudanden eller en viss mottagartabell) måste du använda guiden för målmappning för att skapa miljön. Mer information finns i [Skapa en erbjudandemiljö](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

När du skapar en anonym miljö via guiden för att skapa mappningen markeras rutan **[!UICONTROL Environment dedicated to incoming anonymous interactions]** automatiskt på miljöns **[!UICONTROL General]**-flik.

**[!UICONTROL Targeting dimension]** slutförs automatiskt. Som standard länkas den till besökstabellen.

Fältet **[!UICONTROL Visitor folder]** visas. Det slutförs automatiskt för att länka till mappen **[!UICONTROL Visitors]**. I det här fältet kan du välja var besökarprofiler ska sparas.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>Om du vill filtrera flera typer av besökare, till exempel om anonyma erbjudanden presenteras för ett eller flera varumärken, måste du skapa en miljö för varje varumärke och en **[!UICONTROL Visitors]**-typmapp för varje miljö.

## Erbjud katalog för anonyma interaktioner {#offer-catalog-for-anonymous-interactions}

På samma sätt som utgående interaktioner ordnas inkommande interaktioner i en erbjudandekatalog som består av kategorier och erbjudanden.

Om du vill skapa kategorier och mellanslag använder du samma process som för identifierade besökare (se [Skapa erbjudandekategorier](../../interaction/using/creating-offer-categories.md) och [Skapa en erbjudandemiljö](../../interaction/using/live-design-environments.md#creating-an-offer-environment)).

## Anonyma besökare {#anonymous-visitors}

Anonyma besökare kan bli föremål för en process för identifiering av cookies när de ansluter. Den här implicita igenkänningen baseras på besökarens webbläsarhistorik.

Under det här steget görs en jämförelse mellan de data som har återställts av cookies och de i din databas. I vissa fall är besökaren erkänd (han identifieras sedan implicit), i andra fall är han inte erkänd (och förblir därför anonym).

Om du vill köra den här analysen kontrollerar du alternativet **[!UICONTROL Implicitly identify the individual based on their browser history]** för erbjudandeutrymme.

![](assets/identification_anonymous_visitors.png)

## Bearbetar oidentifierade anonyma besökare {#processing-unidentified-anonymous-visitors}

Om ingen anonym besökare identifieras efter analysen kan du lagra deras data i ett givet utrymme. På så sätt kan du föreslå erbjudanden som är särskilt avsedda för den här typen av besökare, och som matchar de angivna typologireglerna.

Om det inte finns något element som gör att du kan identifiera en kontakt, eller om du inte vill föreslå ett identifierat erbjudande till en kontakt som kan identifieras implicit, kan du välja att göra en reservlösning i en anonym miljö.

Om du vill göra det kontrollerar du **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]** och anger sedan den miljö som är dedikerad till de oidentifierade besökarna i **[!UICONTROL Linked anonymous space]** när du anger ett erbjudandeutrymme.

![](assets/anonymous_to_anonymous_environment.png)

