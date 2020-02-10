---
title: Live-/designmiljöer
seo-title: Live-/designmiljöer
description: Live-/designmiljöer
seo-description: null
page-status-flag: never-activated
uuid: 38ee2f6a-e446-4ac6-b962-40b648eeaf66
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 3cea2be4-4da4-4ebd-a241-1bbaa5abb16e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Live-/designmiljöer{#live-design-environments}

## Verksamhetsprincip {#operating-principle}

Interaktionen fungerar i två typer av miljöer:

* **[!UICONTROL Design]** erbjuder miljöer som innehåller erbjudanden som redigeras och kan ändras. Dessa erbjudanden har inte gått igenom godkännandecykeln och levereras inte till kontakter.
* **[!UICONTROL Live]** erbjuder miljöer som innehåller godkända erbjudanden när de presenteras för kontakter. Erbjudandena i den här miljön är skrivskyddade.

![](assets/offer_environments_overview_001.png)

Varje **[!UICONTROL Design]** miljö är länkad till en **[!UICONTROL Live]** miljö. När ett erbjudande är klart blir dess innehåll och behörighetskrav föremål för en godkännandecykel. När den här cykeln är slutförd distribueras det aktuella erbjudandet automatiskt till **[!UICONTROL Live]** miljön. Från och med nu finns den tillgänglig för leverans.

Som standard innehåller Interaction en **[!UICONTROL Design]** miljö och en **[!UICONTROL Live]** miljö som är länkad till den. Båda miljöerna är förkonfigurerade för mottagartabellen som är klar att användas.

>[!NOTE]
>
>Om du vill skapa en annan tabell (besökstabell för anonyma erbjudanden eller en viss mottagartabell) måste du använda guiden för målmappning för att skapa miljöerna. Mer information finns i [Skapa en erbjudandemiljö](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

Erbjudandeansvariga och leveranschefer har tillgång till olika miljövyer. Leveransansvariga kan bara visa **[!UICONTROL Live]** erbjudandemiljön och använda erbjudanden för att leverera dem. Erbjudandeansvariga kan visa och ändra **[!UICONTROL Design]** miljön och visa **[!UICONTROL Live]** miljön. Mer information finns i [Operator profiles](../../interaction/using/operator-profiles.md).

## Skapa en erbjudandemiljö {#creating-an-offer-environment}

Som standard levereras Interaction med en förkonfigurerad miljö för att rikta sig till mottagartabellen (identifierade erbjudanden). Om du vill ha en annan tabell som mål (besökstabell för anonyma erbjudanden eller en viss mottagartabell) måste du använda följande konfigurationer:

1. Placera markören på **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]** -noden. Högerklicka på den leveranskarta som du vill använda (**[!UICONTROL Visitors]** om du vill använda anonyma erbjudanden) och välj **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Klicka **[!UICONTROL Next]** för att gå till nästa skärm i guiden, markera **[!UICONTROL Generate a storage schema for propositions]** rutan och klicka på **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Om rutan redan är markerad avmarkerar du den och markerar den sedan igen.

1. Adobe Campaign skapar två miljöer (**[!UICONTROL Design]** och **[!UICONTROL Live]** ) med målinformation från den tidigare aktiverade målmappningen. Miljön är förkonfigurerad med målinformationen.

   Om du har aktiverat **[!UICONTROL Visitor]** mappning markeras **[!UICONTROL Environment dedicated to incoming anonymous interactions]** rutan automatiskt på miljöns **[!UICONTROL General]** flik.

   Med det här alternativet kan du aktivera anonyma interaktionsspecifika funktioner, särskilt när du konfigurerar miljön, som innehåller blanksteg. Du kan också konfigurera alternativ som gör att du kan växla från en identifierad miljö till en anonym miljö.

   Du kan t.ex. länka en mottagarmiljö till ett tillgängligt utrymme (identifierad kontakt) med ett erbjudandeutrymme som matchar en besökarmiljö (oidentifierad kontakt). På så sätt kommer olika erbjudanden att göras tillgängliga för kontakten beroende på om han/hon är identifierad eller inte. Mer information finns i [Skapa erbjudandemellanslag](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>Mer information om anonyma interaktioner i en inkommande kanal finns i [Anonyma interaktioner](../../interaction/using/anonymous-interactions.md).

