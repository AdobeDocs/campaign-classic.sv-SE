---
product: campaign
title: Läsa in (SOAP)
description: Läsa in (SOAP)
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 20414e73-2ba9-44f9-8e16-cb6604933ee0
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---

# Läsa in (SOAP){#loading-soap}

>[!CAUTION]
>
>Aktiviteten **Inläsning (SOAP)** är bara tillgänglig om du har **FDA-modulen (Federated Data Access)** installerad. Kontrollera licensavtalet.

Aktiviteten **Loading (SOAP)** används utöver aktiviteten **datainläsning (RDBMS)** när det inte går att samla in data direkt via FDA i en extern databas.

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

   Du kan också anpassa formatet för kolumndata via länken **[!UICONTROL Advanced parameters]**. Mer information om hur du formaterar importerade data finns i [avsnittet](../../platform/using/executing-import-jobs.md).

1. Du kan använda radnumret som en identifierare och/eller ange att SOAP-anropet returnerar flera element.
1. Ange följande tabbskript efter funktion:

   * **[!UICONTROL Initialization]**: skapar en SOAP-anslutning.
   * **[!UICONTROL Iteration]**: utför anropet till SOAP-tjänsten. Returvärdet för den här funktionen måste vara ett XML-objekt som är kompatibelt med beskrivningen av exemplet eller WSDL.

      Koden för den här fliken anropas i en slinga av Adobe Campaign tills ett XML-objekt som är null returneras.

   * **[!UICONTROL Finalization]**: stänger anslutningen och/eller frigör andra resurser som skapas under bearbetningen.
