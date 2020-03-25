---
title: Leverans
seo-title: Leverans
description: Leverans
seo-description: null
page-status-flag: never-activated
uuid: 3a74fd0b-8598-46a0-bf13-cf35db0987d7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 9fd7122e-22c7-4f9a-a2a4-5de3daaa3c2e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 366d2149933fa68dfec2a732d1014e1875709cff

---


# Leverans{#delivery}

Med en aktivitet av typen **Leverans** kan du skapa en leveransåtgärd. Den kan konstrueras med indataelement.

Om du vill konfigurera den redigerar du aktiviteten och anger leveransalternativen.

![](assets/edit_diffusion.png)

1. **Leverans**

   Du kan:

   * Agera på leveransen som anges i den inkommande övergången. Det gör du genom att markera det första alternativet i fönsteravsnittet **[!UICONTROL Delivery]** .

      Det här alternativet kan användas när en tidigare arbetsflödesaktivitet redan har skapats eller specificerat leveransen. Detta kan ha gjorts, som i exemplet nedan, av en aktivitet av samma typ som har genererat en utgående övergång.

      I följande exempel skapas leveransen för första gången. Populationen och innehållet definieras senare. Därefter anges informationen för dessa tre element på nytt i en ny leveransaktivitet med hjälp av övergången för inkommande trafik så att den kan skickas.

      ![](assets/specified_transition_option_exemple.png)

   * Välj den aktuella leveransen direkt. Det gör du genom att välja **[!UICONTROL Explicit]** alternativet och välja leverans i listrutan i **[!UICONTROL Delivery]** fältet.

      I listan visas oavslutade leveranser i mappen **Leveranser** som standard. Klicka på **[!UICONTROL Select link]** ikonen om du vill komma åt andra kampanjer.

      ![](assets/diffusion_edit_1.png)

      Välj kampanjen i listrutan i **[!UICONTROL Folder]** fältet eller klicka på **[!UICONTROL Display sub-levels]** för att visa alla leveranser som finns i undermapparna:

      ![](assets/diffusion_edit_2.png)

      När du har valt leveransåtgärden kan du visa innehållet genom att klicka på **[!UICONTROL Edit link]** -ikonen.

   * Skapa ett skript för att beräkna leveransen. Om du vill göra det markerar du **[!UICONTROL Computed by a script]** alternativet och anger skriptet. Du kan öppna ett inmatningsfönster genom att klicka på **[!UICONTROL Edit...]** alternativet. I följande exempel återskapas leveransens identifierare:

      ![](assets/diffusion_edit_3.png)

   * Skapa en ny leverans. För att göra detta väljer du **[!UICONTROL New, created from a template]** alternativet och väljer den leveransmall som leveransen ska baseras på.

      ![](assets/diffusion_edit_4.png)

      Klicka på **[!UICONTROL Select link]** ikonen för att bläddra bland mapparna och klicka på **[!UICONTROL Edit link]** ikonen om du vill visa innehållet i den valda mallen.

1. **Mottagare**

   Mottagarna kan anges av de inkommande händelserna, till exempel efter en filimport, eller anges i leveransåtgärden. De kan också lagras i en eller flera filer.

   ![](assets/diffusion_edit_5.png)

1. **Innehåll**

   Innehållet i meddelandet kan definieras i leverans- eller inkommande-händelsen.

   ![](assets/diffusion_edit_6.png)

1. **Åtgärd som ska köras**

   Du kan skapa leveransen, förbereda den, starta den, beräkna målet eller skicka ett korrektur.

   ![](assets/diffusion_edit_7.png)

   Välj vilken typ av åtgärd som ska utföras:

   * **[!UICONTROL Save]**: Med det här alternativet kan du skapa leveransen och spara den. Den kommer inte att analysera eller leverera den.
   * **[!UICONTROL Estimate the target]**: Med det här alternativet kan du beräkna leveransmålet för att bedöma dess potential (första analysfasen). Den här åtgärden motsvarar att välja **[!UICONTROL Estimate the population to be targeted]** alternativet och klicka **[!UICONTROL Analyze]** när du skickar en leverans till huvudmålet via **Leverans**.
   * **[!UICONTROL Prepare]**: Med det här alternativet kan du köra hela analysprocessen (målberäkning och innehållsförberedelse). Leveransen har inte skickats. Den här åtgärden motsvarar att välja **[!UICONTROL Deliver as soon as possible]** alternativet och klicka **[!UICONTROL Analyze]** när du skickar en leverans till huvudmålet med **Leverans**.
   * **[!UICONTROL Send a proof]**: Med det här alternativet kan du skicka ett bevis på leveransen. Den här åtgärden motsvarar att klicka på **[!UICONTROL Send a proof]** knappen i verktygsfältet för en leverans med **leverans**
   * **[!UICONTROL Prepare and start]**: Med det här alternativet startas hela analysprocessen (målberäkning och förberedelse av innehåll) och leveransen skickas. Den här åtgärden motsvarar klickning **[!UICONTROL Deliver as soon as possible]**, **[!UICONTROL Analyze]** och **[!UICONTROL Confirm delivery]** alternativ när du skickar en leverans till huvudmålet med **Leverans**.
   Med den **[!UICONTROL Act on a delivery]** aktivitet som används ytterligare i arbetsflödet kan du starta alla återstående steg som krävs för att starta leveransen (målberäkning, förberedelse av innehåll, leverans). Mer information finns i [Leveranskontroll](../../workflow/using/delivery-control.md).

   Följande alternativ är också tillgängliga:

   * **[!UICONTROL Generate an outbound transition]**

      Skapar en utgående övergång som ska aktiveras i slutet av körningen. Du kan välja om du vill hämta målet för den utgående leveransen eller inte.

   * **[!UICONTROL Do not recover target]**

      Återställer inte målet för åtgärden för utgående leverans.

   * **[!UICONTROL Processing errors]**

      Se [Leveranskontroll](../../workflow/using/delivery-control.md).
   På fliken **Skript** kan du ändra leveransparametrarna.

   ![](assets/edit_diffusion_fil_script.png)

## Exempel: arbetsflöde för leverans {#example--delivery-workflow}

Skapa ett nytt arbetsflöde och lägg till aktiviteter enligt bilden nedan:

![](assets/new-workflow-5.png)

Öppna aktiviteten **Leverans** och definiera egenskaperna enligt följande:

* Välj **[!UICONTROL Delivery]** och välj en leveransmall i **[!UICONTROL New, created from a template]** avsnittet.
* Markera i **[!UICONTROL Recipients]** avsnittet **[!UICONTROL Specified in the delivery]**.
* Behåll **[!UICONTROL Action to execute]** alternativet i **[!UICONTROL Prepare]** avsnittet.

![](assets/new-workflow-param-delivery.png)

Klicka **[!UICONTROL OK]** för att stänga egenskapsfönstret. Du har just konfigurerat en aktivitet som består av att skapa och förbereda en ny leverans baserat på en leveransmall vars mål ska anges i den.

Öppna aktiviteten **Godkännande** och definiera egenskaperna enligt följande:

1. I **[!UICONTROL Assignment type]** fältet väljer du en grupp som du är registrerad i. Om du är ansluten med administratörskontot väljer du gruppen Administration.
1. Ange sedan en titel och infoga följande text i meddelandetexten:

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   Detta är ett meddelande som innehåller ett uttryck skrivet i JavaScript: **[!UICONTROL vars.recCount]** representerar antalet mottagare som den föregående uppgiften levereras till. Mer information om JavaScript-uttryck finns i [JavaScript-skript och -mallar](../../workflow/using/javascript-scripts-and-templates.md).

   ![](assets/new-workflow-param-validation.png)

   Godkännandeaktiviteten beskrivs i [Godkännande](../../workflow/using/approval.md).

## Indataparametrar {#input-parameters}

Leverans-ID, om alternativet **[!UICONTROL Specified in the transition]** är markerat i **[!UICONTROL Delivery]** avsnittet.

* deliveryId
* tableName
* schema

Varje inkommande händelse måste ange ett mål som definieras av dessa parametrar.

>[!NOTE]
>
>Den här parametern visas bara om **[!UICONTROL Specified by inbound event(s)]** alternativet är markerat i **[!UICONTROL Recipients]** avsnittet.

* filnamn

   Det fullständiga namnet på filen som genereras om **[!UICONTROL File(s) specified by inbound event(s)]** alternativet är markerat i **[!UICONTROL Recipients]** avsnittet.

* contentId

   Innehållsidentifierare om **[!UICONTROL Specified by inbound events]** alternativet är markerat i **[!UICONTROL Content]** avsnittet.

## Utdataparametrar {#output-parameters}

* tableName
* schema
* recCount

Den här uppsättningen med tre värden identifierar det mål som är resultatet av leveransen. **[!UICONTROL tableName]** är namnet på den tabell som memorerar målets identifierare, **[!UICONTROL schema]** är populationens schema (vanligtvis nms:mottagare) och **[!UICONTROL recCount]** är antalet element i tabellen.

Övergången som är associerad med komplementet har samma parametrar.

>[!NOTE]
>
>Det finns inga utdataparametrar när **[!UICONTROL Do not recover target]** alternativet är markerat.

