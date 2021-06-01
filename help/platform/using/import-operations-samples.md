---
product: campaign
title: Generiska importexempel
description: Läs mer om generiska importer som du kan utföra med importjobb.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4582b524-2b6d-484c-bace-29d2e69f60e9
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 1%

---

# Generiska importexempel {#import-operations-samples}

## Importera från en lista med mottagare {#example--import-from-a-list-of-recipients}

Om du vill skapa och ange en lista med mottagare från översikten över listor gör du så här:

1. Skapa listan

   * Klicka på länken **[!UICONTROL Lists]** på menyn **[!UICONTROL Profiles and targets]** på Adobe Campaign hemsida.
   * Klicka på **[!UICONTROL Create]** och sedan på **[!UICONTROL Import a list]**.

1. Markera filen som ska importeras

   Klicka på mappen till höger om fältet **[!UICONTROL Local file]** och markera filen som innehåller listan som ska importeras.

   ![](assets/s_ncs_user_import_example00_01.png)

1. Listnamn och lagring

   Ange namnet på listan och välj den katalog där den ska sparas.

   ![](assets/s_ncs_user_import_example00_02.png)

1. Starta importen

   Klicka på **[!UICONTROL Next]** och sedan på **[!UICONTROL Start]** för att börja importera listan.

   ![](assets/s_ncs_user_import_example00_03.png)

## Importera nya poster från en textfil {#example--import-new-records-from-a-text-file-}

Så här importerar du nya mottagarprofiler som lagras i en textfil till Adobe Campaign-databasen:

1. Välja en mall

   * På Adobe Campaign hemsida klickar du på länken **[!UICONTROL Profiles and targets]** och sedan på **[!UICONTROL Jobs]**. Ovanför listan med jobb klickar du på **[!UICONTROL New import]**.
   * Låt mallen **[!UICONTROL New text import]** vara markerad som standard.
   * Ändra etiketten och beskrivningen.
   * Välj **[!UICONTROL Simple import]**.
   * Behåll standardjobbmappen.
   * Klicka på **[!UICONTROL Advanced parameters]** och välj alternativet **[!UICONTROL Tracking mode]** om du vill visa information om importen under körningen.

1. Markera filen som ska importeras

   Klicka på mappen till höger om fältet **[!UICONTROL Local file]** och välj den fil du vill importera.

   ![](assets/s_ncs_user_import_example01_01.png)

1. Associerar fält

   Klicka på ikonen **[!UICONTROL Guess the destination fields]** för att mappa käll- och målscheman automatiskt. Kontrollera informationen i det här fönstret innan du klickar på **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_import_example03_01.png)

1. Avstämning

   * Gå till tabellen **Mottagare (nms:mottagare)**.
   * Välj åtgärden **[!UICONTROL Insertion]** och lämna standardvärdena i de andra fälten.

      ![](assets/s_ncs_user_import_example04_01.png)

1. Importerar mottagare

   * Om det behövs anger du en mapp där posterna ska importeras till.

      ![](assets/s_ncs_user_import_example05_01.png)

1. Starta importen

   * Klicka på **[!UICONTROL Start]**.

      I mitten av redigeraren kan du kontrollera att importen har slutförts och se hur många poster som har bearbetats.

      ![](assets/s_ncs_user_import_example06_01.png)

      I **[!UICONTROL Tracking]**-läget kan du spåra information om importen för varje post i källfilen. Det gör du genom att klicka på **[!UICONTROL Profiles and Targets]** och sedan på **[!UICONTROL Processes]**, markera relevant import och leta upp flikarna **[!UICONTROL General]**, **[!UICONTROL Journal]** och **[!UICONTROL Rejects]**.

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

   * Låt **[!UICONTROL Update or insert]** vara markerat som standard.
   * Låt alternativet **[!UICONTROL Management of duplicates]** vara i **[!UICONTROL Update]**-läge så att befintliga poster i databasen ändras med data från textfilen.
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

   * Gå till tabellen och välj åtgärden **[!UICONTROL Update]**.
   * Välj alternativet **[!UICONTROL Reject entity]** för fältet **[!UICONTROL Management of doubles]**.
   * Låt alternativet **[!UICONTROL Management of duplicates]** vara i **[!UICONTROL Update]**-läge så att befintliga poster i databasen ändras med data från textfilen.
   * Placera markören på **[!UICONTROL Last name (@lastName)]**-noden och välj alternativet **[!UICONTROL Update only if destination is empty]**.
   * Upprepa den här åtgärden för noden **[!UICONTROL Company (@company)]**.
   * Tilldela en avstämningsnyckel till fälten **[!UICONTROL Birth date]**, **[!UICONTROL E-mail]** och **[!UICONTROL First name]**.

      ![](assets/s_ncs_user_import_example04_03.png)

1. Starta importen

   Klicka på **[!UICONTROL Start]**.

   Kontrollera i mottagartabellen att posterna har ändrats av importen.

   ![](assets/s_ncs_user_import_example06_05.png)

   Endast värden som var tomma har ersatts med värden från textfilen, men det befintliga värdet i databasen har inte ersatts med värdet från importfilen.

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

   * Gå till tabellen och välj **[!UICONTROL Update]**.
   * Välj alternativet **[!UICONTROL Reject entity]** för fältet **[!UICONTROL Management of doubles]**.
   * Låt alternativet **[!UICONTROL Management of duplicates]** vara i **[!UICONTROL Update]**-läge för befintliga poster i databasen som ska ändras med data från textfilen.
   * Placera markören på noden **[!UICONTROL Account number (@account)]** och välj alternativet **[!UICONTROL Take empty values into account]**.
   * Markera fälten **[!UICONTROL Birth date]**, **[!UICONTROL E-mail]** och **[!UICONTROL First name]** och tilldela dem en avstämningsnyckel.

      ![](assets/s_ncs_user_import_example04_04.png)

1. Starta importen

   * Klicka på **[!UICONTROL Start]**.
   * Kontrollera i mottagartabellen att posterna har ändrats av åtgärden.

      ![](assets/s_ncs_user_import_example06_06.png)

      Värdena för textfilen som var tom har skrivit över värdena i databasen. De befintliga värdena i databasen uppdaterades med värdena i importfilen i enlighet med det **[!UICONTROL Update]**-alternativ som valts för dubbletter i steg 4.
