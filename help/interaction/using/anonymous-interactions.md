---
title: Anonyma interaktioner
seo-title: Anonyma interaktioner
description: Anonyma interaktioner
seo-description: null
page-status-flag: never-activated
uuid: 6e28e8a4-8d2f-4747-8dd0-680fbf02b25d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: unitary-interactions
discoiquuid: 3fd7a1ef-b0e2-4a7e-9e36-044d997db785
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8e37be4f764feadb49c70a9d598f8f3b8f864380

---


# Anonyma interaktioner{#anonymous-interactions}

I den här [videon](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&ref=helpx.adobe.com) får du en översikt över hur erbjudanden levereras till identifierade och anonyma mål.

## Målgruppsanpassning och lagring av en miljö för anonym interaktion {#targeting-and-storing-an-environment-for-anonymous-interactions}

Som standard levereras Interaction med en förkonfigurerad miljö för att rikta sig till mottagartabellen (identifierade erbjudanden). Om du vill skapa en annan tabell (besökstabell för anonyma erbjudanden eller en viss mottagartabell) måste du använda guiden för målmappning för att skapa miljön. Mer information finns i [Skapa en erbjudandemiljö](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

När du skapar en anonym miljö via guiden för att skapa mappningar, markeras **[!UICONTROL Environment dedicated to incoming anonymous interactions]** rutan automatiskt på miljöns **[!UICONTROL General]** flik.

Funktionen **[!UICONTROL Targeting dimension]** slutförs automatiskt. Som standard länkas den till besökstabellen.

Fältet **[!UICONTROL Visitor folder]** visas. Den slutförs automatiskt för att länka till **[!UICONTROL Visitors]** mappen. I det här fältet kan du välja var besökarprofiler ska sparas.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>Om du vill filtrera flera typer av besökare, till exempel om anonyma erbjudanden presenteras för ett eller flera varumärken, måste du skapa en miljö för varje varumärke och en **[!UICONTROL Visitors]** typmapp för varje miljö.

## Erbjud katalog för anonyma interaktioner {#offer-catalog-for-anonymous-interactions}

På samma sätt som utgående interaktioner ordnas inkommande interaktioner i en erbjudandekatalog som består av kategorier och erbjudanden.

Om du vill skapa kategorier och platser använder du samma process som för identifierade besökare (se [Skapa erbjudandekategorier](../../interaction/using/creating-offer-categories.md) och [Skapa en erbjudandemiljö](../../interaction/using/live-design-environments.md#creating-an-offer-environment)).

## Anonyma besökare {#anonymous-visitors}

Anonyma besökare kan bli föremål för en process för identifiering av cookies när de ansluter. Den här implicita igenkänningen baseras på besökarens webbläsarhistorik.

Under det här steget görs en jämförelse mellan de data som har återställts av cookies och de i din databas. I vissa fall är besökaren erkänd (han identifieras sedan implicit), i andra fall är han inte erkänd (och förblir därför anonym).

Om du vill köra den här analysen markerar du **[!UICONTROL Implicitly identify the individual based on their browser history]** alternativet.

![](assets/identification_anonymous_visitors.png)

## Bearbetar oidentifierade anonyma besökare {#processing-unidentified-anonymous-visitors}

Om ingen anonym besökare identifieras efter analysen kan du lagra deras data i ett givet utrymme. På så sätt kan du föreslå erbjudanden som är särskilt avsedda för den här typen av besökare, och som matchar de angivna typologireglerna.

Om det inte finns något element som gör att du kan identifiera en kontakt, eller om du inte vill föreslå ett identifierat erbjudande till en kontakt som kan identifieras implicit, kan du välja att göra en reservlösning i en anonym miljö.

Om du vill göra det kontrollerar du **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]** och anger sedan den miljö som är dedikerad till de oidentifierade besökarna i **[!UICONTROL Linked anonymous space]** när du anger ett erbjudandeutrymme.

![](assets/anonymous_to_anonymous_environment.png)

