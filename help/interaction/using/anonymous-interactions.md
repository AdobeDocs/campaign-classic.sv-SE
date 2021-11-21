---
product: campaign
title: Anonyma interaktioner
description: Anonyma interaktioner
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: a8face46-a933-4f2c-8299-ccb66f05967d
source-git-commit: 8b970705f0da6a9e09de9fadb3e1a8c5f4814f9f
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 1%

---

# Anonyma interaktioner{#anonymous-interactions}

![](../../assets/v7-only.svg)

![](assets/do-not-localize/how-to-video.png) Titta på detta [video](https://helpx.adobe.com/campaign/classic/how-to/indetified-and-anonymous-interaction-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/digital-marketers/explevel/intermediate/applaunch/get-started/collection.ccx.js&amp;ref=helpx.adobe.com) för att få en översikt över hur erbjudanden levereras till identifierade och anonyma mål.

## Målgruppsanpassning och lagring av en miljö för anonym interaktion {#targeting-and-storing-an-environment-for-anonymous-interactions}

Som standard levereras Interaction med en förkonfigurerad miljö för att rikta sig till mottagartabellen (identifierade erbjudanden). Om du vill skapa en annan tabell (besökstabell för anonyma erbjudanden eller en viss mottagartabell) måste du använda guiden för målmappning för att skapa miljön. Mer information finns i [Skapa en erbjudandemiljö](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

När du skapar en anonym miljö via guiden för att skapa mappningar **[!UICONTROL Environment dedicated to incoming anonymous interactions]** -rutan markeras automatiskt i miljöns **[!UICONTROL General]** -fliken.

The **[!UICONTROL Targeting dimension]** slutförs automatiskt. Som standard länkas den till besökstabellen.

The **[!UICONTROL Visitor folder]** visas. Det fylls automatiskt i för att länka till **[!UICONTROL Visitors]** mapp. I det här fältet kan du välja var besökarprofiler ska sparas.

![](assets/anonymous_environment_option.png)

>[!NOTE]
>
>Om du vill filtrera flera typer av besökare, till exempel om anonyma erbjudanden presenteras för ett eller flera varumärken, måste du skapa en miljö för varje varumärke och en **[!UICONTROL Visitors]** typmapp för varje miljö.

## Erbjud katalog för anonyma interaktioner {#offer-catalog-for-anonymous-interactions}

På samma sätt som utgående interaktioner ordnas inkommande interaktioner i en erbjudandekatalog som består av kategorier och erbjudanden.

Om du vill skapa kategorier och mellanslag använder du samma process som för identifierade besökare (se [Skapa erbjudandekategorier](../../interaction/using/creating-offer-categories.md) och [Skapa en erbjudandemiljö](../../interaction/using/live-design-environments.md#creating-an-offer-environment)).

## Anonyma besökare {#anonymous-visitors}

Anonyma besökare kan bli föremål för en process för identifiering av cookies när de ansluter. Den här implicita igenkänningen baseras på besökarens webbläsarhistorik.

Under det här steget görs en jämförelse mellan de data som har återställts av cookies och de i din databas. I vissa fall identifieras besökare (de identifieras sedan implicit), i andra fall identifieras de inte (och förblir därför anonyma).

Om du vill köra den här analysen kontrollerar du **[!UICONTROL Implicitly identify the individual based on their browser history]** alternativ.

![](assets/identification_anonymous_visitors.png)

## Bearbetar oidentifierade anonyma besökare {#processing-unidentified-anonymous-visitors}

Om ingen anonym besökare identifieras efter analysen kan du lagra deras data i ett givet utrymme. På så sätt kan du föreslå erbjudanden som är särskilt avsedda för den här typen av besökare, och som matchar de angivna typologireglerna.

Om det inte finns något element som gör att du kan identifiera en kontakt, eller om du inte vill föreslå ett identifierat erbjudande till en kontakt som kan identifieras implicit, kan du välja att göra en reservlösning i en anonym miljö.

Om du vill göra det går du till **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]** anger du sedan den miljö som är dedikerad till de oidentifierade besökarna i **[!UICONTROL Linked anonymous space]** när du anger ett erbjudandeutrymme.

![](assets/anonymous_to_anonymous_environment.png)
