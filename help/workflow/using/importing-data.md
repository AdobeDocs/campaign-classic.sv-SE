---
solution: Campaign Classic
product: campaign
title: Importera data
description: Lär dig hur du importerar data i Adobe Campaign
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: e43a14a8be179dd4793176d15e2c30b3e778d3e0
workflow-type: tm+mt
source-wordcount: '2473'
ht-degree: 0%

---


# Importera data{#importing-data}

>[!CAUTION]
>
>Tänk på begränsningarna för SFTP-lagring, databaslagring och aktiv profil enligt ditt Adobe Campaign-avtal när du importerar data.

## Hur man samlar in data {#how-to-collect-data}

### Använda data från en lista: Läslista {#using-data-from-a-list--read-list}

Data som skickas i ett arbetsflöde kan komma från listor där data har förberetts och strukturerats.

Listan kan ha skapats direkt i Adobe Campaign eller importerats med **[!UICONTROL Import a list]** alternativet. For more on this option, refer to this [page](../../platform/using/generic-imports-and-exports.md).

Mer information om hur du använder läslisteaktiviteten i ett arbetsflöde finns i [Läslista](../../workflow/using/read-list.md).

### Läsa in data från en fil {#loading-data-from-a-file}

Data som bearbetas i ett arbetsflöde kan extraheras från en strukturerad fil så att de kan importeras till Adobe Campaign.

En beskrivning av inläsningen av dataaktiviteten finns i avsnittet [Datainläsning (fil)](../../workflow/using/data-loading--file-.md) .

Exempel på strukturerad fil som ska importeras:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## Bästa tillvägagångssätt vid import av data {#best-practices-when-importing-data}

Genom att vara försiktig och följa de få enkla regler som beskrivs nedan kan du till stor del säkerställa att data är konsekventa i databasen och undvika vanliga fel under databasuppdatering eller dataexport.

### Använda importmallar {#using-import-templates}

De flesta importarbetsflöden bör innehålla följande aktiviteter: **[!UICONTROL Data loading (file)]**, **[!UICONTROL Enrichment]**, **[!UICONTROL Split]**, **[!UICONTROL Deduplication]**, **[!UICONTROL Update data]**.

Med importmallar är det mycket bekvämt att förbereda liknande importer och säkerställa att data är konsekventa i databasen. Lär dig hur du skapar arbetsflödesmallar i [avsnittet Arbetsflödesmallar](../../workflow/using/building-a-workflow.md#workflow-templates) .

I många projekt byggs importen utan **[!UICONTROL Deduplication]** aktivitet eftersom filerna som används i projektet inte har några dubbletter. Det kan ibland visas dubbletter när du importerar olika filer. Det är då svårt att deduplicera. Därför är ett borttagningssteg en bra försiktighetsåtgärd i alla importarbetsflöden.

Du kan inte utgå från att inkommande data är konsekventa och korrekta, eller att IT-avdelningen eller Adobe Campaign-administratören kommer att ta hand om dem. Under projektet bör du tänka på datarensningen. Ta bort dubbletter, stämma av och bibehåll enhetligheten när du importerar data.

Ett exempel på en importmall finns i avsnittet [Konfigurera en återkommande import](#setting-up-a-recurring-import) .

### Använda platta filformat {#using-flat-file-formats}

Det mest effektiva formatet för import är platta filer. Platta filer kan importeras i gruppläge på databasnivå.

Exempel:

* Avgränsare: tabb eller semikolon
* Första raden med rubriker
* Ingen strängavgränsare
* Datumformat: YYYY/MM/DD HH:mm:SS

Adobe Campaign kan inte importera XML-filer med vanliga filimportaktiviteter. Det går att importera XML-filer med JavaScript, men bara med små volymer: mindre än 10 000 poster per fil.

### Använda komprimering och kryptering {#using-compression-and-encryption}

Använd zippade filer för import och export när det är möjligt.

I Linux går det att packa upp en fil och importera samtidigt med hjälp av en kommandorad. Exempel:

```
zcat nl6/var/vp/import/filename.gz
```

Det är också bra att kryptera filer som skickas över nätverket om de inte är säkra. GPG kan användas för detta.

### Läsa in data i grupp från filer {#loading-data-in-batch-from-files}

Att läsa in data batchvis från en fil är effektivare än att läsa in en rad i taget och i realtid (till exempel via en webbtjänst).

Import med webbtjänster är inte effektivt. Det är bäst att använda filer när det är möjligt.

Att anropa externa webbtjänster för att berika profiler i realtid är också känt för att orsaka prestandaproblem och minnesläckor, eftersom det fungerar på radnivå.

Om du behöver importera data är det bättre att göra det gruppvis, med ett arbetsflöde än i realtid, med ett webbprogram eller en webbtjänst.

### Använda datahantering {#using-data-management}

Inläsning i iterativt läge (rad för rad) med JavaScript bör begränsas till små volymer.

Använd alltid aktiviteten i arbetsflöden för datahantering för bättre effektivitet. **[!UICONTROL Data Loading (File)]**

### Importera i Delta-läge {#importing-in-delta-mode}

Vanlig import måste göras i deltaläge. Det innebär att endast ändrade eller nya data skickas till Adobe Campaign, i stället för hela tabellen varje gång.

Full import bör endast användas för inledande last.

Importera data med hjälp av datahantering i stället för JavaScript.

### Bevara konsekvensen {#maintaining-consistency}

Följ nedanstående principer för att upprätthålla datakonsekvensen i Adobe Campaign-databasen:

* Om de importerade data matchar en referenstabell i Adobe Campaign bör den stämma av med den tabellen i arbetsflödet. Poster som inte matchar bör avvisas.
* Se till att importerade data alltid är **&quot;normaliserade&quot;** (e-post, telefonnummer, e-postadress) och att normaliseringen är tillförlitlig och inte förändras under årens lopp. Om så inte är fallet kommer vissa dubbletter sannolikt att visas i databasen, och eftersom Adobe Campaign inte har verktyg för&quot;otydlig&quot; matchning är det mycket svårt att hantera och ta bort dem.
* Transaktionsdata ska ha en avstämningsnyckel och stämma av med befintliga data för att undvika att skapa dubbletter.
* **Importera relaterade filer i rätt ordning**.

   Om importen består av flera filer som är beroende av varandra, bör arbetsflödet se till att filerna importeras i rätt ordning. När en fil misslyckas importeras inte de andra filerna.

* **Ta bort dubbletter**, stämma av och bibehåll konsekvens när du importerar data.

## Användningsfall: konfigurera en återkommande import {#setting-up-a-recurring-import}

Det är bäst att använda en importmall om du behöver importera filer med samma struktur regelbundet.

I det här exemplet visas hur du anger ett förinställt arbetsflöde som kan återanvändas för import av profiler från en CRM i Adobe Campaign-databasen. Mer information om alla möjliga inställningar för varje aktivitet finns i det här [avsnittet](../../workflow/using/about-activities.md).

1. Skapa en ny arbetsflödesmall från **[!UICONTROL Resources > Templates > Workflow templates]**.
1. Lägg till följande aktiviteter:

   * **[!UICONTROL Data loading (file)]**: Definiera den förväntade strukturen för filen som innehåller de data som ska importeras.
   * **[!UICONTROL Enrichment]**: Stäm av importerade data med databasdata.
   * **[!UICONTROL Split]**: Skapa filter för att bearbeta poster på olika sätt beroende på om de kan förenas eller inte.
   * **[!UICONTROL Deduplication]**: Deduplicera data från den inkommande filen innan den infogas i databasen.
   * **[!UICONTROL Update data]**: Uppdatera databasen med de importerade profilerna.

   ![](assets/import_template_example0.png)

1. Konfigurera **[!UICONTROL Data Loading (file)]** aktiviteten:

   * Definiera den förväntade strukturen genom att överföra en exempelfil. Exempelfilen bör bara innehålla några få rader, men alla kolumner som behövs för importen. Kontrollera och redigera filformatet för att säkerställa att typen av varje kolumn är korrekt: text, datum, heltal osv. Exempel:

      ```
      lastname;firstname;birthdate;email;crmID
      Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
      ```

   * I **[!UICONTROL Name of the file to load]** avsnittet markerar du **[!UICONTROL Upload a file from the local machine]** och lämnar fältet tomt. Varje gång ett nytt arbetsflöde skapas från den här mallen kan du här ange vilken fil du vill ha, så länge den motsvarar den definierade strukturen.

      Du kan använda något av alternativen, men du måste ändra mallen därefter. Om du till exempel väljer **[!UICONTROL Specified in the transition]** kan du lägga till en **[!UICONTROL File Transfer]** aktivitet innan du hämtar filen som ska importeras från en FTP-/SFTP-server. Med S3- eller SFTP-anslutning kan du även importera segmentdata till Adobe Campaign med Adobe kunddataplattform i realtid. For more on this, refer to this [documentation](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).

      ![](assets/import_template_example1.png)

1. Konfigurera **[!UICONTROL Enrichment]** aktiviteten. Syftet med den här aktiviteten i det här sammanhanget är att identifiera inkommande data.

   * På **[!UICONTROL Enrichment]** fliken markerar du **[!UICONTROL Add data]** och definierar en länk mellan importerade data och måldimensionen för mottagarna. I det här exemplet används det anpassade fältet **CRM ID** för att skapa kopplingsvillkoret. Använd fältet eller kombinationen av fält som du behöver så länge det går att identifiera unika poster.
   * Låt alternativet vara omarkerat på **[!UICONTROL Reconciliation]** fliken **[!UICONTROL Identify the document from the working data]** .

   ![](assets/import_template_example2.png)

1. Konfigurera aktiviteten för att hämta avstämda mottagare i en övergång och mottagare som inte kunde avstämas men som har tillräckligt med data i en andra övergång. **[!UICONTROL Split]**

   Övergången med avstämda mottagare kan sedan användas för att uppdatera databasen. Övergången med okända mottagare kan sedan användas för att skapa nya mottagarposter i databasen om det finns en minimiuppsättning information i filen.

   Mottagare som inte kan förenas och som inte har tillräckligt med data markeras i en komplementövergång och kan exporteras i en separat fil eller helt enkelt ignoreras.

   * Välj filterinställning på aktivitetens **[!UICONTROL General]** flik **[!UICONTROL Use the additional data only]** och kontrollera att **[!UICONTROL Targeting dimension]** inställningen automatiskt är **[!UICONTROL Enrichment]**.

      Markera det här alternativet om du vill se om det inte går att infoga någon post i databasen. **[!UICONTROL Generate complement]** Om du behöver kan du använda ytterligare bearbetning för kompletterande data: export av filer, uppdatering av listor osv.

   * I den första delmängden av **[!UICONTROL Subsets]** fliken lägger du till ett filtervillkor i den inkommande fyllningen för att endast markera poster där den mottagande primärnyckeln inte är lika med 0. På så sätt markeras data från filen som är avstämda med mottagare från databasen i den delmängden.

      ![](assets/import_template_example3.png)

   * Lägg till en andra delmängd som markerar ej avstämda poster som har tillräckligt med data för att infogas i databasen. Till exempel: e-postadress, förnamn och efternamn.

      Deluppsättningar bearbetas i den ordning de skapas, vilket innebär att alla poster som redan finns i databasen redan är markerade i den första deluppsättningen när den andra deluppsättningen bearbetas.

      ![](assets/import_template_example3_2.png)

   * Alla poster som inte är markerade i de två första delmängderna markeras i **[!UICONTROL Complement]**.

1. Konfigurera den **[!UICONTROL Update data]** aktivitet som finns efter den första utgående övergången för den **[!UICONTROL Split]** aktivitet som konfigurerats tidigare.

   * Välj **[!UICONTROL Update]** som **[!UICONTROL Operation type]** eftersom den inkommande övergången bara innehåller mottagare som redan finns i databasen.
   * I **[!UICONTROL Record identification]** avsnittet väljer du **[!UICONTROL Using reconciliation keys]** och definierar en nyckel mellan måldimensionen och länken som skapas i **[!UICONTROL Enrichment]**. I det här exemplet används det anpassade fältet **CRM ID** .
   * I **[!UICONTROL Fields to update]** avsnittet anger du fälten från mottagardimensionen som ska uppdateras med värdet för motsvarande kolumn från filen. Om namnen på filkolumnerna är identiska eller nästan identiska med namnen på mottagarnas dimensionsfält kan du använda trollstavsknappen för att automatiskt matcha de olika fälten.

      ![](assets/import_template_example6.png)

1. Konfigurera den **[!UICONTROL Deduplication]** aktivitet som finns efter övergången och som innehåller ej avstämda mottagare:

   * Välj **[!UICONTROL Edit configuration]** och ange måldimensionen till det temporära schema som genereras från arbetsflödets **[!UICONTROL Enrichment]** aktivitet.

      ![](assets/import_template_example4.png)

   * I det här exemplet används e-postfältet för att hitta unika profiler. Du kan använda vilket fält som helst som du är säker på är ifyllt och ingår i en unik kombination.
   * På **[!UICONTROL Deduplication method]** skärmen markerar du **[!UICONTROL Advanced parameters]** och markerar **[!UICONTROL Disable automatic filtering of 0 ID records]** alternativet för att se till att poster som har en primärnyckel som är lika med 0 (som ska vara alla poster i den här övergången) inte utesluts.

   ![](assets/import_template_example7.png)

1. Konfigurera den **[!UICONTROL Update data]** aktivitet som finns efter den **[!UICONTROL Deduplication]** aktivitet som konfigurerats tidigare.

   * Välj **[!UICONTROL Insert]** som **[!UICONTROL Operation type]** eftersom den inkommande övergången bara innehåller mottagare som inte finns i databasen.
   * Markera **[!UICONTROL Record identification]** och välj **[!UICONTROL Directly using the targeting dimension]** **[!UICONTROL Recipients]** dimensionen i avsnittet.
   * I **[!UICONTROL Fields to update]** avsnittet anger du fälten från mottagardimensionen som ska uppdateras med värdet för motsvarande kolumn från filen. Om namnen på filkolumnerna är identiska eller nästan identiska med namnen på mottagarnas dimensionsfält kan du använda trollstavsknappen för att automatiskt matcha de olika fälten.

      ![](assets/import_template_example8.png)

1. Efter den tredje övergången av **[!UICONTROL Split]** aktiviteten lägger du till en **[!UICONTROL Data extraction (file)]** aktivitet och en **[!UICONTROL File transfer]** aktivitet om du vill hålla reda på data som inte har infogats i databasen. Konfigurera de aktiviteterna för att exportera den kolumn du behöver och för att överföra filen till en FTP- eller SFTP-server där du kan hämta den.
1. Lägg till en **[!UICONTROL End]** aktivitet och spara arbetsflödesmallen.

Mallen kan nu användas och är tillgänglig för alla nya arbetsflöden. Allt som behövs är då att ange filen som innehåller de data som ska importeras i **[!UICONTROL Data loading (file)]** aktiviteten.

![](assets/import_template_example9.png)

## Zippa upp eller dekryptera en fil före bearbetning {#unzipping-or-decrypting-a-file-before-processing}

### Om förbearbetningsfaser {#about-pre-processing-stages}

Med Adobe Campaign kan du importera komprimerade eller krypterade filer. Innan de kan läsas in i en [datainläsningsaktivitet (fil)](../../workflow/using/data-loading--file-.md) kan du definiera en förbearbetning för att packa upp eller dekryptera filen.

Så här kan du göra:

1. Använd [kontrollpanelen](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data) för att generera ett nyckelpar för offentlig/privat nyckel.

   >[!NOTE]
   >
   >Kontrollpanelen är tillgänglig för alla kunder som har AWS som värd (med undantag för kunder som har sina marknadsföringsinstanser på plats).

1. Om din installation av Adobe Campaign ligger hos Adobe kontaktar du Adobe kundtjänst för att få de verktyg som behövs installerade på servern.
1. Om du har en installation av Adobe Campaign installerad installerar du verktyget som du vill använda (till exempel: GPG, GZIP) och nödvändiga nycklar (krypteringsnyckel) på programservern.

Du kan sedan använda de förbehandlingskommandon du vill i dina arbetsflöden:

1. Lägg till och konfigurera en **[!UICONTROL File transfer]** aktivitet i arbetsflödet.
1. Lägg till en **[!UICONTROL Data loading (file)]** aktivitet och definiera filformatet.
1. Markera alternativet **[!UICONTROL Pre-process the file]**.
1. Ange det förbehandlingskommando som du vill använda.
1. Lägg till andra aktiviteter för att hantera data som kommer från filen.
1. Spara och kör arbetsflödet.

Ett exempel visas i användningsexemplet nedan.

**Relaterade ämnen:**

* [Aktivitet](../../workflow/using/data-loading--file-.md)för datainläsning (fil).
* [Zippa eller kryptera en fil](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

### Användningsfall: Importera data krypterade med en nyckel som genererats av Kontrollpanelen {#use-case-gpg-decrypt}

I det här fallet skapar vi ett arbetsflöde för att importera data som har krypterats i ett externt system med hjälp av en nyckel som genererats på Kontrollpanelen.

En självstudievideo som visar hur du använder en GPG-nyckel för att dekryptera data finns också i [det här avsnittet](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/instance-settings/gpg-key-management/decrypting-data.html?lang=en#instance-settings).

Så här utför du det här användningsfallet:

1. Använd Kontrollpanelen för att generera ett nyckelpar (public/private). Detaljerade steg finns i dokumentationen för [Kontrollpanelen](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data).

   * Den offentliga nyckeln delas med det externa systemet, som kommer att använda den för att kryptera data som ska skickas till Campaign.
   * Den privata nyckeln används av Campaign Classic för att dekryptera inkommande krypterade data.

   ![](assets/gpg_generate.png)

1. I det externa systemet använder du den offentliga nyckel som hämtats från Kontrollpanelen för att kryptera de data som ska importeras till Campaign Classic.

1. Bygg ett arbetsflöde i Campaign Classic för att importera krypterade data och dekryptera dem med den privata nyckel som har installerats via Kontrollpanelen. För att göra detta ska vi skapa ett arbetsflöde enligt följande:

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** aktivitet: Överför filen från en extern källa till Campaign Classic. I det här exemplet vill vi överföra filen från en SFTP-server.
   * **[!UICONTROL Data loading (file)]** aktivitet: Läser in data från filen i databasen och dekrypterar den med den privata nyckel som genereras på Kontrollpanelen.

1. Öppna **[!UICONTROL File transfer]** aktiviteten och ange sedan det externa konto som du vill importera den krypterade GPG-filen från.

   ![](assets/gpg_key_transfer.png)

   Globala koncept för hur du konfigurerar aktiviteten finns i [det här avsnittet](../../workflow/using/file-transfer.md).

1. Öppna **[!UICONTROL Data loading (file)]** aktiviteten och konfigurera den efter dina behov. Globala koncept för hur du konfigurerar aktiviteten finns i [det här avsnittet](../../workflow/using/data-loading--file-.md).

   Lägg till en förbearbetningsfas i aktiviteten för att dekryptera inkommande data. Det gör du genom att markera **[!UICONTROL Pre-process the file]** alternativet och sedan kopiera och klistra in dekrypteringskommandot i **[!UICONTROL Command]** fältet:

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >I det här exemplet använder vi den lösenfras som används som standard av Kontrollpanelen, som är&quot;lösenfras&quot;.
   >
   >Om du redan har installerat GPG-nycklar på din instans via en kundtjänstförfrågan tidigare kan lösenfrasen ha ändrats och vara en annan som standard.

1. Klicka **[!UICONTROL OK]** för att bekräfta aktivitetskonfigurationen.

1. Du kan nu köra arbetsflödet. När dekrypteringen är klar kan du kontrollera i arbetsflödets loggar att den har körts och att data från filen har importerats.

   ![](assets/gpg_run.png)
