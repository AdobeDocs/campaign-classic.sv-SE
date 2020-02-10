---
title: Läser in (SOAP)
seo-title: Läser in (SOAP)
description: Läser in (SOAP)
seo-description: null
page-status-flag: never-activated
uuid: 80597892-e363-48f6-8633-faad161064a4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 94178104-f8ba-4c17-8ff9-928c5d2df1b7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Läser in (SOAP){#loading-soap}

>[!CAUTION]
>
>SOAP-aktiviteten ( **Loading)** är bara tillgänglig om du har **FDA-modulen (Federated Data Access)** installerad. Kontrollera licensavtalet.

Aktiviteten **Loading (SOAP)** används utöver aktiviteten för **datainläsning (RDBMS)** när det inte är möjligt att samla in data direkt via FDA i en extern databas.

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

   Du kan också anpassa kolumndataformatet via **[!UICONTROL Advanced parameters]** länken. Mer information om hur du formaterar importerade data finns i det här [avsnittet](../../platform/using/importing-data.md#import-wizard).

1. Du kan använda radnumret som en identifierare och/eller ange att SOAP-anropet returnerar flera element.
1. Ange följande tabbskript efter funktion:

   * **[!UICONTROL Initialization]**: skapar en SOAP-anslutning.
   * **[!UICONTROL Iteration]**: utför anropet till SOAP-tjänsten. Returvärdet för den här funktionen måste vara ett XML-objekt som är kompatibelt med beskrivningen av exemplet eller WSDL.

      Koden på den här fliken anropas i en slinga av Adobe Campaign tills ett XML-objekt som är null returneras.

   * **[!UICONTROL Finalization]**: stänger anslutningen och/eller frigör andra resurser som skapas under bearbetningen.

