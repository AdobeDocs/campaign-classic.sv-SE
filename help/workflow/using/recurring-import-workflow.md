---
product: campaign
title: Konfigurera en återkommande import
description: Lär dig hur du konfigurerar en arbetsflödesmall för återkommande importer.
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: e6e140cb-8de0-4ab9-bddc-95abe04124c6
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 0%

---

# Konfigurera ett arbetsflöde för återkommande import {#setting-up-a-recurring-import}

Det är bäst att använda en arbetsflödesmall om du behöver importera filer med samma struktur regelbundet.

I det här exemplet visas hur du anger ett förinställt arbetsflöde som kan återanvändas för import av profiler från en CRM i Adobe Campaign-databasen. Mer information om alla möjliga inställningar för varje aktivitet finns i det här [avsnittet](../../workflow/using/about-activities.md).

1. Skapa en ny arbetsflödesmall från **[!UICONTROL Resources > Templates > Workflow templates]**.
1. Lägg till följande aktiviteter:

   * **[!UICONTROL Data loading (file)]**: Definiera den förväntade strukturen för filen som innehåller de data som ska importeras.
   * **[!UICONTROL Enrichment]**: Stäm av importerade data med databasdata.
   * **[!UICONTROL Split]**: Skapa filter för att bearbeta poster på olika sätt beroende på om de kan förenas eller inte.
   * **[!UICONTROL Deduplication]**: Deduplicera data från den inkommande filen innan den infogas i databasen.
   * **[!UICONTROL Update data]**: Uppdatera databasen med de importerade profilerna.

   ![](assets/import_template_example0.png)

1. Konfigurera aktiviteten **[!UICONTROL Data Loading (file)]**:

   * Definiera den förväntade strukturen genom att överföra en exempelfil. Exempelfilen bör bara innehålla några få rader, men alla kolumner som behövs för importen. Kontrollera och redigera filformatet för att säkerställa att typen av varje kolumn är korrekt: text, datum, heltal osv. Exempel:

      ```
      lastname;firstname;birthdate;email;crmID
      Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
      ```

   * I avsnittet **[!UICONTROL Name of the file to load]** väljer du **[!UICONTROL Upload a file from the local machine]** och lämnar fältet tomt. Varje gång ett nytt arbetsflöde skapas från den här mallen kan du här ange vilken fil du vill ha, så länge den motsvarar den definierade strukturen.

      Du kan använda något av alternativen, men du måste ändra mallen därefter. Om du till exempel väljer **[!UICONTROL Specified in the transition]** kan du lägga till en **[!UICONTROL File Transfer]**-aktivitet innan du hämtar filen som ska importeras från en FTP-/SFTP-server. Med S3- eller SFTP-anslutning kan du även importera segmentdata till Adobe Campaign med Adobe kunddataplattform i realtid. Mer information finns i [dokumentationen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

      ![](assets/import_template_example1.png)

1. Konfigurera aktiviteten **[!UICONTROL Enrichment]**. Syftet med den här aktiviteten i det här sammanhanget är att identifiera inkommande data.

   * På fliken **[!UICONTROL Enrichment]** väljer du **[!UICONTROL Add data]** och definierar en länk mellan importerade data och måldimensionen för mottagarna. I det här exemplet används det anpassade fältet **CRM ID** för att skapa kopplingsvillkoret. Använd fältet eller kombinationen av fält som du behöver så länge det går att identifiera unika poster.
   * Lämna alternativet **[!UICONTROL Identify the document from the working data]** omarkerat på fliken **[!UICONTROL Reconciliation]**.

   ![](assets/import_template_example2.png)

1. Konfigurera aktiviteten **[!UICONTROL Split]** för att hämta avstämda mottagare i en övergång och mottagare som inte kunde avstämas men som har tillräckligt med data i en andra övergång.

   Övergången med avstämda mottagare kan sedan användas för att uppdatera databasen. Övergången med okända mottagare kan sedan användas för att skapa nya mottagarposter i databasen om det finns en minimiuppsättning information i filen.

   Mottagare som inte kan förenas och som inte har tillräckligt med data markeras i en komplementövergång och kan exporteras i en separat fil eller helt enkelt ignoreras.

   * På fliken **[!UICONTROL General]** i aktiviteten väljer du **[!UICONTROL Use the additional data only]** som filtreringsinställning och kontrollerar att **[!UICONTROL Targeting dimension]** automatiskt är inställt på **[!UICONTROL Enrichment]**.

      Markera alternativet **[!UICONTROL Generate complement]** för att se om det inte går att infoga någon post i databasen. Om du behöver kan du använda ytterligare bearbetning för kompletterande data: export av filer, uppdatering av listor osv.

   * I den första delmängden av fliken **[!UICONTROL Subsets]** lägger du till ett filtreringsvillkor i den inkommande populationen för att endast markera poster där den mottagande primärnyckeln inte är lika med 0. På så sätt markeras data från filen som är avstämda med mottagare från databasen i den delmängden.

      ![](assets/import_template_example3.png)

   * Lägg till en andra delmängd som markerar ej avstämda poster som har tillräckligt med data för att infogas i databasen. Till exempel: e-postadress, förnamn och efternamn.

      Deluppsättningar bearbetas i den ordning de skapas, vilket innebär att alla poster som redan finns i databasen redan är markerade i den första deluppsättningen när den andra deluppsättningen bearbetas.

      ![](assets/import_template_example3_2.png)

   * Alla poster som inte är markerade i de två första delmängderna markeras i **[!UICONTROL Complement]**.

1. Konfigurera aktiviteten **[!UICONTROL Update data]** som finns efter den första utgående övergången för aktiviteten **[!UICONTROL Split]** som konfigurerats tidigare.

   * Välj **[!UICONTROL Update]** som **[!UICONTROL Operation type]** eftersom den inkommande övergången bara innehåller mottagare som redan finns i databasen.
   * I avsnittet **[!UICONTROL Record identification]** väljer du **[!UICONTROL Using reconciliation keys]** och definierar en nyckel mellan måldimensionen och länken som skapas i **[!UICONTROL Enrichment]**. I det här exemplet används det anpassade fältet **CRM ID**.
   * I avsnittet **[!UICONTROL Fields to update]** anger du fälten från mottagardimensionen som ska uppdateras med värdet för motsvarande kolumn från filen. Om namnen på filkolumnerna är identiska eller nästan identiska med namnen på mottagarnas dimensionsfält kan du använda trollstavsknappen för att automatiskt matcha de olika fälten.

      ![](assets/import_template_example6.png)

1. Konfigurera aktiviteten **[!UICONTROL Deduplication]** som finns efter övergången som innehåller ej avstämda mottagare:

   * Välj **[!UICONTROL Edit configuration]** och ange måldimensionen till det temporära schema som genereras från **[!UICONTROL Enrichment]**-aktiviteten i arbetsflödet.

      ![](assets/import_template_example4.png)

   * I det här exemplet används e-postfältet för att hitta unika profiler. Du kan använda vilket fält som helst som du är säker på är ifyllt och ingår i en unik kombination.
   * På skärmen **[!UICONTROL Deduplication method]** väljer du **[!UICONTROL Advanced parameters]** och markerar alternativet **[!UICONTROL Disable automatic filtering of 0 ID records]** för att se till att poster som har en primärnyckel som är lika med 0 (som ska vara alla poster i den här övergången) inte utesluts.

   ![](assets/import_template_example7.png)

1. Konfigurera aktiviteten **[!UICONTROL Update data]** som finns efter aktiviteten **[!UICONTROL Deduplication]** som konfigurerats tidigare.

   * Välj **[!UICONTROL Insert]** som **[!UICONTROL Operation type]** eftersom den inkommande övergången bara innehåller mottagare som inte finns i databasen.
   * I avsnittet **[!UICONTROL Record identification]** väljer du **[!UICONTROL Directly using the targeting dimension]** och väljer dimensionen **[!UICONTROL Recipients]**.
   * I avsnittet **[!UICONTROL Fields to update]** anger du fälten från mottagardimensionen som ska uppdateras med värdet för motsvarande kolumn från filen. Om namnen på filkolumnerna är identiska eller nästan identiska med namnen på mottagarnas dimensionsfält kan du använda trollstavsknappen för att automatiskt matcha de olika fälten.

      ![](assets/import_template_example8.png)

1. Efter den tredje övergången av aktiviteten **[!UICONTROL Split]** lägger du till en **[!UICONTROL Data extraction (file)]**-aktivitet och en **[!UICONTROL File transfer]**-aktivitet om du vill hålla reda på data som inte har infogats i databasen. Konfigurera de aktiviteterna för att exportera den kolumn du behöver och för att överföra filen till en FTP- eller SFTP-server där du kan hämta den.
1. Lägg till en **[!UICONTROL End]**-aktivitet och spara arbetsflödesmallen.

Mallen kan nu användas och är tillgänglig för alla nya arbetsflöden. Allt behövs sedan för att ange filen som innehåller de data som ska importeras i **[!UICONTROL Data loading (file)]**-aktiviteten.

![](assets/import_template_example9.png)
