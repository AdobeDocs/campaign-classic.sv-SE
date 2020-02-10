---
title: Använda kuber för att utforska data
seo-title: Använda kuber för att utforska data
description: Använda kuber för att utforska data
seo-description: null
page-status-flag: never-activated
uuid: ba15e7dc-0a3b-48cf-971a-7a89b8b9c9f7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: e1ab1e82-8194-40a8-8df3-e7cfbaa3e777
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Använda kuber för att utforska data{#using-cubes-to-explore-data}

Marknadsföringsanalys gör det enklare att skapa rapporter och att identifiera och välja data från databasen via kuber. Detta gör att du kan:

* Skapa rapporter baserade på kuber. Processen beskrivs här: Utforska [data i en rapport](#exploring-the-data-in-a-report).
* Samla in data i databasen och gruppera dem i listor, t.ex. för att identifiera och bygga mål och leveranser. Mer information finns i [Skapa en målpopulation](#building-a-target-population).
* Infoga en pivottabell i en rapport och referera till en befintlig kub i den. Mer information finns i [Infoga en pivottabell i en rapport](#inserting-a-pivot-table-into-a-report).

>[!NOTE]
>
>Marknadsföringsanalys krävs för att skapa eller ändra kuber. Mer information finns i [Om kuber](../../reporting/using/about-cubes.md).

## Utforska data i en rapport {#exploring-the-data-in-a-report}

### Steg 1 - Skapa en rapport baserad på en kub {#step-1---creating-a-report-based-on-a-cube}

Om du vill skapa en rapport baserad på en kub klickar du på **[!UICONTROL Create]** -knappen i **[!UICONTROL Reports]** universum och väljer den kub som du vill använda.

Processen beskrivs här: [Skapa en rapport baserad på en kub](../../reporting/using/creating-indicators.md#creating-a-report-based-on-a-cube).

### Steg 2 - Markera rader och kolumner {#step-2---selecting-lines-and-columns}

Standardvisningen visar de två första måtten för kuben (ålder och stad, i det här fallet).

Med **[!UICONTROL Add]** knapparna på varje axel kan du lägga till dimensioner.

![](assets/s_advuser_cube_in_report_03.png)

1. Markera de dimensioner som du vill visa i tabellens rader och kolumner. Det gör du genom att dra och släppa de tillgängliga måtten enligt nedan:
1. Välj de dimensioner som du vill lägga till i tabellen i listan:

   ![](assets/s_advuser_cube_in_report_04.png)

1. Välj sedan parametrarna för dimensionen.

   ![](assets/s_advuser_cube_in_report_04b.png)

   Parametrarna beror på datatypen för den valda dimensionen.

   För datum kan till exempel flera nivåer vara tillgängliga. Mer information finns i [Visa mått](../../reporting/using/concepts-and-methodology.md#displaying-measures).

   Följande alternativ erbjuds i det här fallet:

   ![](assets/s_advuser_cube_in_report_config2.png)

   Du kan antingen:

   * Expandera data vid inläsning: värdena visas som standard varje gång rapporten uppdateras (standardvärde: nej).
   * Visa summan i slutet av raden: När data visas i kolumner kan du med ett extra alternativ visa summan i slutet av raden: en kolumn läggs till i tabellen (standardvärde: ja).
   * Använd en sortering: värdena i kolumnen kan sorteras efter värde, etikett eller baserat på ett mått (standardvärde: efter värde).
   * Visa värdena i stigande (a-z, 0-9) eller fallande (z-a, 9-0) ordning.
   * Ändra antalet kolumner som ska visas vid inläsning (som standard: 200).

1. Bekräfta genom **[!UICONTROL Ok]** att klicka: dimensionen läggs till i de befintliga dimensionerna.

   Den gula banderollen ovanför tabellen visar att du har gjort ändringar: Klicka på knappen för att spara dem **[!UICONTROL Save]** .

   ![](assets/s_advuser_cube_in_report_04c.png)

### Steg 3 - Konfigurera de mått som ska visas {#step-3---configuring-the-measures-to-display}

När raderna och kolumnerna är på plats anger du de mått som du vill visa samt deras visningsläge.

Som standard visas bara ett mått. Så här lägger du till eller konfigurerar mått:

1. Klicka på **[!UICONTROL Measures]** knappen.

   ![](assets/s_advuser_cube_in_report_05.png)

1. Med den här **[!UICONTROL Use a measure]** kommandoknappen kan du välja ett av de befintliga måtten.

   ![](assets/s_advuser_cube_in_report_08.png)

   Markera den information som du vill visa och typen av formatering. Listan med alternativ beror på vilken typ av mått som har konfigurerats.

   ![](assets/s_advuser_cube_in_report_09.png)

   Den övergripande mätkonfigurationen är också tillgänglig via **[!UICONTROL Edit the configuration of the pivot table]** ikonen i sidhuvudet.

   ![](assets/s_advuser_cube_in_report_config_02.png)

   Du kan sedan välja om måttetiketter ska visas eller inte. Mer information finns i [Konfigurera visningen](../../reporting/using/concepts-and-methodology.md#configuring-the-display).

1. Det går att bygga nya mått med hjälp av befintliga. Om du vill göra det klickar du på **[!UICONTROL Create a measure]** och konfigurerar den.

   ![](assets/s_advuser_cube_in_report_config_02a.png)

   Följande typer av åtgärder är tillgängliga:

   * En kombination av åtgärder: den här typen av åtgärd gör det möjligt att bygga den nya åtgärden med hjälp av befintliga åtgärder:

      De tillgängliga operatorerna är: summa, differens, multiplikation och ränta.

   * Andel: Med den här typen av mått kan du beräkna antalet poster som mäts för en given dimension. Du kan beräkna proportionaliteten baserat på en dimension eller en underdimension.
   * Variation: Med det här måttet kan du beräkna variationen i värden för en nivå.
   * Standardavvikelse: Med den här typen av mått kan du beräkna avvikelser inom varje cellgrupp jämfört med medelvärdet för värdena. Du kan till exempel jämföra inköpsvolymen för alla befintliga segment.
   Det skapade måttet läggs till i rapporten.

   ![](assets/s_advuser_cube_in_report_config_02b.png)

   När du har skapat ett mått kan du redigera det och vid behov ändra dess konfiguration. Det gör du genom att klicka på **[!UICONTROL Measures]** knappen och sedan gå till fliken för det mått som du vill redigera.

   Klicka sedan **[!UICONTROL Edit the dynamic measure]** för att öppna inställningsmenyn.

## Bygga en målpopulation {#building-a-target-population}

Rapporter som byggs med kuber gör att du kan samla in data från tabellen och spara dem i en lista.

Lägg dem i en kundvagn och bearbeta innehållet.

Gör så här om du vill gruppera en population i en lista:

1. Klicka på cellerna som innehåller de ifyllningar som ska samlas för att markera dem och klicka sedan på **[!UICONTROL Add to cart]** ikonen .

   ![](assets/s_advuser_cube_in_report_config_02c.png)

   Så många gånger som krävs för att samla in olika profiler

1. Klicka på **[!UICONTROL Show cart]** knappen om du vill visa innehållet innan du kör exporten.

   ![](assets/s_advuser_cube_in_report_config_02d.png)

1. Med **[!UICONTROL Export]** knappen kan du gruppera objekten i kundvagnen i en lista.

   Du måste ange namnet på listan och vilken typ av export som ska utföras.

   ![](assets/s-advuser_cube_in_report_config_02e.png)

   Klicka **[!UICONTROL Start]** för att köra exporten.

1. När exporten är klar bekräftar ett meddelande att den har körts och hur många poster som har bearbetats.

   ![](assets/s_advuser_cube_in_report_config_02f.png)

   Du kan antingen spara innehållet i kundvagnen eller tömma den.

   Den relevanta listan nås via **[!UICONTROL Profiles and targets]** universum.

   ![](assets/s_advuser_cube_in_report_config_02g.png)

## Infoga en pivottabell i en rapport {#inserting-a-pivot-table-into-a-report}

Så här skapar du en tabell och utforskar data i en kub:

1. Skapa en ny rapport med en enda sida och infoga en pivottabell i den. Mer information finns på [den här sidan](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table).

   ![](assets/s_advuser_cube_in_report_01.png)

1. Välj en kub på sidans flik för att bearbeta dimensionerna som den innehåller och visa beräknade mått. **[!UICONTROL Data]**

   ![](assets/s_advuser_cube_in_report_02.png)

   Detta gör att du kan skapa rapporten som ska visas. Mer information finns i [steg 2 - Markera rader och kolumner](#step-2---selecting-lines-and-columns).

