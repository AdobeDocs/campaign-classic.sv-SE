---
product: campaign
title: Generiska importexempel
description: Läs mer om generiska importer som du kan utföra med importjobb
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4582b524-2b6d-484c-bace-29d2e69f60e9
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 1%

---

# Generiska importexempel {#import-operations-samples}



## Importera från en lista med mottagare {#example--import-from-a-list-of-recipients}

Om du vill skapa och ange en lista med mottagare från översikten över listor gör du så här:

1. Skapa listan

   * Klicka på **[!UICONTROL Lists]** i **[!UICONTROL Profiles and targets]** på Adobe Campaign hemsida.
   * Klicka på **[!UICONTROL Create]** och sedan **[!UICONTROL Import a list]** -knappen.

1. Markera filen som ska importeras

   Klicka på mappen till höger om **[!UICONTROL Local file]** och markera filen som innehåller listan som ska importeras.

   ![](assets/s_ncs_user_import_example00_01.png)

1. Listnamn och lagring

   Ange namnet på listan och välj den katalog där den ska sparas.

   ![](assets/s_ncs_user_import_example00_02.png)

1. Starta importen

   Klicka **[!UICONTROL Next]** och sedan **[!UICONTROL Start]** för att börja importera listan.

   ![](assets/s_ncs_user_import_example00_03.png)

## Importera nya poster från en textfil {#example--import-new-records-from-a-text-file-}

Så här importerar du nya mottagarprofiler som lagras i en textfil till Adobe Campaign-databasen:

1. Välja en mall

   * På Adobe Campaign hemsida klickar du på **[!UICONTROL Profiles and targets]** länk, sedan **[!UICONTROL Jobs]**. Ovanför listan med jobb klickar du på **[!UICONTROL New import]**.
   * Behåll **[!UICONTROL New text import]** -mall vald som standard.
   * Ändra etiketten och beskrivningen.
   * Välj **[!UICONTROL Simple import]**.
   * Behåll standardjobbmappen.
   * Klicka **[!UICONTROL Advanced parameters]** och väljer **[!UICONTROL Tracking mode]** om du vill visa information om importen under körningen.

1. Markera filen som ska importeras

   Klicka på mappen till höger om **[!UICONTROL Local file]** och välj den fil som du vill importera.

   ![](assets/s_ncs_user_import_example01_01.png)

1. Associerar fält

   Klicka på **[!UICONTROL Guess the destination fields]** om du vill mappa käll- och målscheman automatiskt. Kontrollera informationen i det här fönstret innan du klickar **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_import_example03_01.png)

1. Avstämning

   * Gå till **Mottagare (nms:mottagare)** tabell.
   * Välj **[!UICONTROL Insertion]** och lämna standardvärdena i de andra fälten.

      ![](assets/s_ncs_user_import_example04_01.png)

1. Importerar mottagare

   * Om det behövs anger du en mapp där posterna ska importeras till.

      ![](assets/s_ncs_user_import_example05_01.png)

1. Starta importen

   * Klicka på **[!UICONTROL Start]**.

      I mitten av redigeraren kan du kontrollera att importen har slutförts och se hur många poster som har bearbetats.

      ![](assets/s_ncs_user_import_example06_01.png)

      The **[!UICONTROL Tracking]** I kan du spåra importinformationen för varje post i källfilen. Det gör du genom att klicka på **[!UICONTROL Profiles and Targets]** sedan **[!UICONTROL Processes]** väljer du relevant import och letar upp **[!UICONTROL General]**, **[!UICONTROL Journal]** och **[!UICONTROL Rejects]** -tabbar.

      * Kontrollerar importförloppet

         ![](assets/s_ncs_user_import_example07_01.png)

      * Processvisning för varje post

         ![](assets/s_ncs_user_import_example07_02.png)

## Uppdatera och infoga mottagare {#example--update-and-insert-recipients}

Vi vill uppdatera befintliga poster i databasen och skapa nya från en textfil. Här följer ett exempel på proceduren:

1. Välja en mall

   Upprepa stegen som beskrivs i exempel 2 ovan.

1. Fil som ska importeras

   Markera filen som du vill importera.

   I vårt exempel visar översikten över de första raderna i filen att filen innehåller uppdateringar för tre poster och att en post skapas.

   ![](assets/s_ncs_user_import_example02_02.png)

1. Associerar fält

   Använd proceduren i exempel 2 ovan.

1. Avstämning

   * Behåll **[!UICONTROL Update or insert]** som standard.
   * Behåll alternativet **[!UICONTROL Management of duplicates]** in **[!UICONTROL Update]** så att befintliga poster i databasen ändras med data från textfilen.
   * Markera fälten **[!UICONTROL Birth date]**, **[!UICONTROL Name]** och **[!UICONTROL Company]** och tilldela dem en avstämningsnyckel.

      ![](assets/s_ncs_user_import_example04_02.png)

1. Starta importen

   * Klicka på **[!UICONTROL Start]**.

      I spårningsfönstret kan du kontrollera att importen har slutförts och se hur många poster som har bearbetats.

      ![](assets/s_ncs_user_import_example06_02.png)

   * Kontrollera i mottagartabellen att posterna har ändrats av den här åtgärden.

      ![](assets/s_ncs_user_import_example06_03.png)

## Förbättra värdena med värdena i en extern fil {#example--enrich-the-values-with-those-of-an-external-file}

Vi vill ändra vissa fält i en databastabell från en textfil och prioritera värdena i databasen.

I det här exemplet ser du att vissa fält i textfilen har ett värde, medan motsvarande fält i databasen är tomma. Andra fält innehåller ett annat värde än det som finns i databasen.

* Innehållet i den textfil som ska importeras.

   ![](assets/s_ncs_user_import_example02_03.png)

* Databasstatus före import

   ![](assets/s_ncs_user_import_example06_04.png)

Använd följande steg:

1. Välja en mall

   Använd proceduren i exempel 2 ovan.

1. Fil som ska importeras

   Markera filen som du vill importera.

1. Associerar fält

   Använd proceduren i exempel 2 ovan.

   I förhandsgranskningen av de första raderna i filen ser du att filen innehåller uppdateringar för vissa poster.

1. Avstämning

   * Gå till tabellen och välj **[!UICONTROL Update]** operation.
   * Välj alternativet **[!UICONTROL Reject entity]** för **[!UICONTROL Management of doubles]** fält.
   * Behåll alternativet **[!UICONTROL Management of duplicates]** in **[!UICONTROL Update]** så att befintliga poster i databasen ändras med data från textfilen.
   * Placera markören på **[!UICONTROL Last name (@lastName)]** och väljer **[!UICONTROL Update only if destination is empty]** alternativ.
   * Upprepa den här åtgärden för **[!UICONTROL Company (@company)]** nod.
   * Tilldela en avstämningsnyckel till fälten **[!UICONTROL Birth date]**, **[!UICONTROL Email]** och **[!UICONTROL First name]**.

      ![](assets/s_ncs_user_import_example04_03.png)

1. Starta importen

   Klicka på **[!UICONTROL Start]**.

   Kontrollera i mottagartabellen att posterna har ändrats av importen.

   ![](assets/s_ncs_user_import_example06_05.png)

   Endast värden som var tomma har ersatts av värden från textfilen, men det befintliga värdet i databasen har inte ersatts av värdet från importfilen.

## Uppdatera och förbättra värden från dem i en extern fil {#example--update-and-enrich-the-values-from-those-in-an-external-file}

Vi vill ändra vissa fält i en databastabell från en textfil och prioritera värdena i textfilen.

I det här exemplet ser du att vissa fält i textfilen har ett tomt värde, medan motsvarande fält i databasen inte är tomma. Andra fält innehåller ett annat värde än det i databasen.

* Innehållet i den textfil som ska importeras.

   ![](assets/s_ncs_user_import_example02_04.png)

* Databasstatus före import

   ![](assets/s_ncs_user_import_example06_07.png)

1. Välja en mall

   Använd proceduren i exempel 2 ovan.

1. Fil som ska importeras

   Markera filen som du vill importera.

   I förhandsgranskningen av de första raderna i filen ser du att filen innehåller tomma fält och uppdateringar för vissa poster.

1. Associerar fält

   Använd proceduren i exempel 2 ovan.

1. Avstämning

   * Gå till tabellen och markera **[!UICONTROL Update]**.
   * Välj alternativet **[!UICONTROL Reject entity]** för **[!UICONTROL Management of doubles]** fält.
   * Lämna alternativet **[!UICONTROL Management of duplicates]** in **[!UICONTROL Update]** läge för befintliga poster i databasen som ska ändras med data från textfilen.
   * Placera markören på **[!UICONTROL Account number (@account)]** nod och välj alternativet **[!UICONTROL Take empty values into account]**.
   * Markera fälten **[!UICONTROL Birth date]**, **[!UICONTROL Email]** och **[!UICONTROL First name]** och tilldela dem en avstämningsnyckel.

      ![](assets/s_ncs_user_import_example04_04.png)

1. Starta importen

   * Klicka på **[!UICONTROL Start]**.
   * Kontrollera i mottagartabellen att posterna har ändrats av åtgärden.

      ![](assets/s_ncs_user_import_example06_06.png)

      Värdena för textfilen som var tom har skrivit över värdena i databasen. De befintliga värdena i databasen uppdaterades med värdena i importfilen i enlighet med **[!UICONTROL Update]** för dubbletter i steg 4.
