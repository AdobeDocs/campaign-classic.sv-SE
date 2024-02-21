---
product: campaign
title: Läsa in (SOAP)
description: Läsa in (SOAP)
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Workflows
exl-id: 20414e73-2ba9-44f9-8e16-cb6604933ee0
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 6%

---

# Läsa in (SOAP){#loading-soap}



>[!CAUTION]
>
>The **Läser in (SOAP)** aktiviteten är bara tillgänglig om du har **FDA (Federated Data Access)** modulen är installerad. Kontrollera licensavtalet.

The **Läser in (SOAP)** -aktiviteten används utöver **datainläsning (RDBMS)** verksamhet när det inte är möjligt att samla in data direkt via FDA i en extern databas.

Åtgärden är följande:

1. Välj mellan att använda ett XML-exempel eller en WSDL.

   Följande exempel kommer från ett tekniskt arbetsflöde i Message Center-modulen.

   ![](assets/load_soap_002.png)

1. Välj en exempelfil för ett XML-exempel. Filen analyseras för att skapa ett resultatexempel.

   För en WSDL anger du den matchande URL:en och genererar sedan skelettkoden. Den valda tjänsten och det valda samtalet uppdateras och visas automatiskt.

   ![](assets/soap_load_003.png)

1. Välj **[!UICONTROL Click here to view and edit analysis results]** för att ange varje identifierad kolumn.

   ![](assets/soap_load_001.png)

   Om du vill uppdatera exemplet väljer du **[!UICONTROL Re-analyze the example]**.

   Du kan också anpassa kolumndataformatet via **[!UICONTROL Advanced parameters]** länk. Mer information om hur du formaterar importerade data finns i [section](../../platform/using/executing-import-jobs.md).

1. Du kan använda radnumret som en identifierare och/eller ange att SOAP-anropet returnerar flera element.
1. Ange följande tabbskript beroende på deras funktion:

   * **[!UICONTROL Initialization]**: upprättar en SOAP-anslutning.
   * **[!UICONTROL Iteration]**: utför anropet till SOAP-tjänsten. Returvärdet för den här funktionen måste vara ett XML-objekt som är kompatibelt med beskrivningen av exemplet eller WSDL.

     Koden för den här fliken anropas i en slinga av Adobe Campaign tills ett XML-objekt som är null returneras.

   * **[!UICONTROL Finalization]**: stänger anslutningen och/eller frigör andra resurser som skapas under bearbetningen.
