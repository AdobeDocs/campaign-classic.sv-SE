---
product: campaign
title: Live- och designmiljöer
description: Live- och designmiljöer
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: 965c4a6a-6535-454d-bd37-e9c8312b4d13
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 2%

---

# Live- och designmiljöer{#live-design-environments}



## Verksamhetsprincip {#operating-principle}

Interaktionen fungerar med två typer av erbjudandemiljöer:

* **[!UICONTROL Design]** erbjuder miljöer som innehåller erbjudanden som redigeras och kan ändras. Dessa erbjudanden har inte gått igenom godkännandecykeln och levereras inte till kontakter.
* **[!UICONTROL Live]** erbjuder miljöer som innehåller godkända erbjudanden när de presenteras för kontakter. Erbjudandena i den här miljön är skrivskyddade.

![](assets/offer_environments_overview_001.png)

Varje **[!UICONTROL Design]**-miljö är länkad till en **[!UICONTROL Live]**-miljö. När ett erbjudande är klart blir dess innehåll och behörighetskrav föremål för en godkännandecykel. När den här cykeln är slutförd distribueras det aktuella erbjudandet automatiskt till miljön **[!UICONTROL Live]**. Från och med nu finns den tillgänglig för leverans.

Som standard levereras interaktion med en **[!UICONTROL Design]**-miljö och en **[!UICONTROL Live]**-miljö länkad till den. Båda miljöerna är förkonfigurerade för den inbyggda mottagartabellen.

>[!NOTE]
>
>Om du vill skapa en annan tabell (besökstabell för anonyma erbjudanden eller en viss mottagartabell) måste du använda målmappningsassistenten för att skapa miljöerna. Mer information finns i [Skapa en erbjudandemiljö](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

Erbjudandeansvariga och leveranschefer har tillgång till olika miljövyer. Leveransansvariga kan bara visa erbjudandemiljön **[!UICONTROL Live]** och använda erbjudanden för att leverera dem. Erbjudandehanterare kan visa och ändra miljön **[!UICONTROL Design]** och visa miljön **[!UICONTROL Live]**. Mer information finns i [Operatorprofiler](../../interaction/using/operator-profiles.md).

## Skapa en erbjudandemiljö {#creating-an-offer-environment}

Som standard levereras Interaction med en förkonfigurerad miljö för att rikta sig till mottagartabellen (identifierade erbjudanden). Om du vill ha en annan tabell som mål (besökstabell för anonyma erbjudanden eller en viss mottagartabell) måste du använda följande konfigurationer:

1. Placera markören på noden **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]**. Högerklicka på den leveranskarta som du vill använda (**[!UICONTROL Visitors]** om du vill använda anonyma erbjudanden) och välj **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Klicka på **[!UICONTROL Next]** om du vill fortsätta till nästa skärm i assistenten, markera rutan **[!UICONTROL Generate a storage schema for propositions]** och klicka på **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Om rutan redan är markerad avmarkerar du den och markerar den sedan igen.

1. Adobe Campaign skapar två miljöer (**[!UICONTROL Design]** och **[!UICONTROL Live]**) med målinformation från den målmappning som tidigare aktiverats. Miljön är förkonfigurerad med målinformationen.

   Om du har aktiverat **[!UICONTROL Visitor]**-mappning kontrolleras rutan **[!UICONTROL Environment dedicated to incoming anonymous interactions]** automatiskt på miljöns **[!UICONTROL General]**-flik.

   Med det här alternativet kan du aktivera anonyma interaktionsspecifika funktioner, särskilt när du konfigurerar miljön, som innehåller blanksteg. Du kan också konfigurera alternativ som gör att du kan växla från en identifierad miljö till en anonym miljö.

   Du kan t.ex. länka en mottagarmiljö till ett tillgängligt utrymme (identifierad kontakt) med ett erbjudande som matchar en besökarmiljö (oidentifierad kontakt). På så sätt kommer olika erbjudanden att göras tillgängliga för kontakten beroende på om kontakten identifieras eller inte. Mer information finns i [Skapa erbjudandemellanslag](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>Mer information om anonyma interaktioner i en inkommande kanal finns i [Anonyma interaktioner](../../interaction/using/anonymous-interactions.md).
