---
product: campaign
title: Adapt your configuration
description: Lär dig hur du anpassar konfigurationen före och efter en migrering till Campaign v7
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 327f220d6700242308ef3738a38cc95b970e3f46
workflow-type: tm+mt
source-wordcount: '1980'
ht-degree: 3%

---

# Anpassa konfigurationen{#configuring-your-platform}

![](../../assets/v7-only.svg)

Vissa större förändringar i Adobe Campaign v7 kräver specifik konfiguration. Dessa konfigurationer kan vara nödvändiga före eller efter migrering.

Detaljerad konfiguration som ska utföras i Adobe Campaign v7 vid migrering från Campaign v5 eller v6 finns i [den här sidan](general-configurations.md).


During the migration, the **NmsRecipient** table is rebuilt from the schemas definition. Alla ändringar som görs i SQL-strukturen för den här tabellen utanför Adobe Campaign går förlorade.

Exempel på element som ska kontrolleras:

* If you have added a column (or an index) into the **NmsRecipient** table but you have not detailed it in the schema, this will not be saved.
* The **tabellutrymme** som standard återfår attributets värden, dvs. de som definieras i distributionsguiden.
* Om du har lagt till en referensvy i **NmsRecipient** måste du ta bort den innan du migrerar den.


## Före migreringen {#before-the-migration}

När du migrerar till Adobe Campaign v7 måste följande element konfigureras. Dessa element måste åtgärdas innan du startar **postuppgradering**.

* Tidszoner

   Under en migrering från en v5.11-plattform måste du ange vilken tidszon som ska användas under efteruppgraderingen.

   Om du vill använda läget &quot;multi-timezone&quot;, se [det här avsnittet](../../migration/using/general-configurations.md#time-zones).

   Om du använder Oracle som databas kontrollerar du att Oraclets tidszonsfiler har synkroniserats korrekt mellan programservern och databasservern. [Läs mer](../../migration/using/general-configurations.md#oracle)

* Säkerhetszoner

   Av säkerhetsskäl är Adobe Campaign-plattformen inte längre tillgänglig som standard: du måste konfigurera säkerhetszonerna, vilket kräver att du samlar in användarens IP-adresser innan migreringen. [Läs mer](../../migration/using/general-configurations.md#security)

* Syntax

   Viss Javascript-kod kanske inte längre accepteras i version 7 på grund av att en ny tolk används. [Läs mer](../../migration/using/general-configurations.md#javascript).

   På samma sätt introduceras en ny syntax i Adobe Campaign v7 som ersätter den SQLData-baserade syntaxen. Om du använder kodelement med den här syntaxen måste du anpassa dem. [Läs mer](../../migration/using/general-configurations.md#sqldata)

* Lösenord

   Du måste konfigurera **Administratör** och **Intern** lösenord. [Läs mer](../../migration/using/before-starting-migration.md#user-passwords)

* Trädstruktur

   Om du migrerar från en v5.11-plattform måste du ordna om trädstrukturmapparna enligt Adobe Campaign v6-standarderna. [Läs mer](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).

* Interaktion

   If you are migrating from Campaign v6.02 and using the  **Interaction** module, you must delete all 6.02 schema references that no longer exist in v7. [Läs mer](../../migration/using/general-configurations.md#interaction)

## Efter migreringen {#after-the-migration}

After running **postupgrade**, check and configure the following elements:

* Spegla sidor

   Mirror page personalization block has changed with v6.x. This new version improves security when accessing these pages.

   Om du använde v5-anpassningsblocket i dina meddelanden kommer speglingssidan inte att visas. Adobe rekommenderar starkt att du använder det nya anpassningsblocket när du infogar en spegelsida i dina meddelanden.

   Som en tillfällig lösning (och eftersom spegelsidorna fortfarande är aktiva) kan du återgå till det gamla personaliseringsblocket för att undvika det här problemet genom att ändra alternativet **[!UICONTROL XtkAcceptOldPasswords]** och ange **[!UICONTROL 1]**. Detta påverkar inte användningen av det nya v6.x-anpassningsblocket.

* Syntax

   Om du får problem med syntaxen under efteruppgraderingen måste du tillfälligt aktivera **allowSQLInjection** i **serverConf.xml** eftersom det ger dig tid att skriva om koden. Se till att återaktivera skyddet när koden har anpassats. [Läs mer](../../migration/using/general-configurations.md#sqldata)

* Konflikter

   Migreringen utförs efter uppgraderingen och konflikter kan uppstå i rapporter, formulär eller webbprogram. Konflikterna kan lösas från konsolen. [Läs mer](../../migration/using/general-configurations.md#conflicts)

* Tomcat

   Om du har anpassat installationsmappen kontrollerar du att den har uppdaterats korrekt efter migreringen. [Läs mer](../../migration/using/general-configurations.md#tomcat)

* Rapporter

   Alla färdiga rapporter använder för närvarande v6.x-renderingsmotorn. Om du har lagt till JavaScript-kod i rapporterna kan vissa element påverkas. [Läs mer](../../migration/using/general-configurations.md#reports)

* Webbprogram

   Om du har problem med anslutningen till dina identifierade webbprogram efter uppgraderingen måste du aktivera **allowUserPassword** och **sessionTokenOnly** i **serverConf.xml** -fil. För att undvika säkerhetsproblem måste dessa två alternativ återaktiveras när problemet har lösts. [Läs mer](../../migration/using/general-configurations.md#identified-web-applications)

   Beroende på vilken typ av webbprogram det är och hur de är konfigurerade måste du utföra ytterligare ändringar för att vara säker på att de fungerar som de ska. [Läs mer](../../migration/using/general-configurations.md#web-applications)

   Om du migrerar från en v5.11-plattform måste ytterligare konfigurationer utföras. [Läs mer](../../migration/using/general-configurations.md#specific-configurations-in-v5-11.md)

* Säkerhetszoner

   Innan du startar servern måste du konfigurera säkerhetszonerna. [Learn more](../../installation/using/security-zones.md) and [see here](../../migration/using/general-configurations.md#security)

* Arbetsflöden

   If migrating from a v5.11 platform, you must check the workflows folder. [Läs mer](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* Spåra

   Om du migrerar från en v5.11-plattform måste du konfigurera spårningsläget. [Läs mer](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* Interaktion

   Om du använder **Interaktion** måste du justera alla parametrar efter migreringen. [Läs mer](../../migration/using/general-configurations.md#interaction)

* Kontrollpaneler

   Om ett klientfel uppstår måste du antingen uppdatera dina instrumentpaneler med den nya Adobe Campaign v7-koden eller manuellt kopiera följande filer från v6.02-instansen till v7-instansen:

   ```
   v6.02 files and spaces:
   /usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
   /usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
   v6.1 files and spaces:
   /usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
   /usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
   ```


## Specifika konfigurationer från v5.11 till v7{#specific-configurations-in-v5-11}

![](../../assets/v7-only.svg)

I det här avsnittet beskrivs den ytterligare konfiguration som krävs vid migrering från v5.11. Du bör även konfigurera inställningarna som anges i [Allmänna konfigurationer](../../migration/using/general-configurations.md) -avsnitt.

### Webbapplikationer {#web-applications-v5}

Följande varning visas automatiskt under migreringen:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side JavaScript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Vissa komponenter i webbprogram, till exempel de olika formelfälten, har @id-attribut. De används i XML-koden för webbprogram och genereras inte längre på samma sätt. De är inte synliga i gränssnittet och du får normalt inte använda dem. I vissa fall kan @id-attribut ha använts för att anpassa återgivningen av webbprogram, till exempel via en formatmall eller JavaScript-kod.

Under migreringen kan du **måste** Kontrollera loggfilens sökväg som anges i varningen:

* **Filen är inte tom**: Den innehåller varningar som rör inkonsekvenser som registrerats före migreringen och som fortfarande finns. Detta kan vara JavaScript-kod i ett webbprogram som refererar till ett ID som inte finns. Varje fel måste kontrolleras och korrigeras.
* **Filen är tom**: detta innebär att Adobe Campaign inte har upptäckt några problem.

Oavsett om filen är tom eller inte måste du kontrollera att dessa ID:n inte används för konfiguration någon annanstans (och anpassa konfigurationen om så är fallet).

### Arbetsflöden {#workflows}

Eftersom namnet på Adobe Campaign installationskatalog har ändrats kanske vissa arbetsflöden inte fungerar efter migreringen. Om ett arbetsflöde refererar till katalogen nl5 i någon av dess aktiviteter genereras ett fel. Replace this reference with **build**. Du kan köra en SQL-fråga för att identifiera dessa arbetsflöden (PostgreSQL-exempel):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

### MySQL {#mysql}

>[!CAUTION]
>
>MySQL stöds bara i v7 som huvuddatabasmotor när du migrerar från version 6.02 eller 5.11 med den här motorn.

MySQL hanterar inte tidszoner som standard. To enable timezone management, run the following command:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>Mer information finns i [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) sida.

Om databasstrukturen har ändrats, t.ex. under konfiguration (skapa specifika index, skapa SQL-vyer osv.), bör vissa försiktighetsåtgärder vidtas vid migrering. Vissa ändringar kan ha sin grund i inkompatibilitet med migreringsförfarandet. Skapa t.ex. SQL-vyer som innehåller **Tidsstämpel** fälten är inte kompatibla med **usetimestamptz** alternativ. Vi rekommenderar därför att du följer rekommendationerna nedan:

1. Before starting the migration, back up the database.
1. Ta bort SQL-ändringar.
1. Perform the postupgrade
   >[!NOTE]
   >
   >Du måste följa stegen för migrering i [det här avsnittet](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md).
1. Reintegrate SQL changes.

In this example, a **NmcTrackingLogMessages** view had been created and this has a **Timestamp** field named **tslog**. I det här fallet misslyckas migreringsproceduren och följande felmeddelande visas:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

För att vara säker på att efteruppgraderingen fungerar måste du ta bort vyn före migreringen och återskapa den efter migreringen samtidigt som du anpassar den till TIMESTAMP MED TIMEZONE-läget.

### Spåra {#tracking}

Spårningsformeln har ändrats. När du migrerar ersätts den gamla formeln (v5) med den nya (v7). Om du använder en anpassad formel i Adobe Campaign v5 måste den här konfigurationen anpassas i Adobe Campaign v7 (**NmsTracking_ClickFormula** och **NmsTracking_OpenFormula** alternativ).

Hanteringen av webbspårning har också ändrats. När migreringen till v7 har slutförts måste du starta distributionsguiden för att slutföra konfigurationen av webbspårningen.

![](assets/migration_web_tracking.png)

Tre olika lägen finns tillgängliga:

* **Sessionswebbspårning**: Om **[!UICONTROL Leads]** paketet har inte installerats. Det här alternativet är markerat som standard. Det här alternativet är det mest idealiska när det gäller prestanda och du kan begränsa spårningsloggarnas storlek.
* **Permanent webbspårning**
* **Anonym webbspårning**: Om **[!UICONTROL Leads]** paketet är installerat. Det här alternativet är markerat som standard. Det är det mest resurskrävande alternativet. Som ovan **sSourceId** -kolumnen måste vara indexerad (i spårningstabellen och **CrmIncomingLead** tabell).

>[!NOTE]
>
>Mer information om dessa tre lägen finns i [det här avsnittet](../../configuration/using/about-web-tracking.md).

### Trädstruktur för Adobe Campaign v7 {#campaign-vseven-tree-structure}

Under migreringen ordnas trädstrukturen automatiskt om baserat på v7-standarderna. De nya mapparna läggs till, de föråldrade mapparna tas bort och deras innehåll placeras i mappen &quot;Att flytta&quot;. Alla objekt i den här mappen måste kontrolleras efter migreringen, och konsulten måste välja att antingen behålla eller ta bort varje objekt. Objekt som ska behållas måste flyttas till rätt plats.

Ett alternativ har lagts till för att inaktivera automatisk migrering av navigeringsträdet. Den här åtgärden är nu manuell. Föråldrade mappar tas inte bort och nya mappar läggs inte till. Det här alternativet bör endast användas om det färdiga v5-navigeringsträdet har genomgått för många ändringar. Lägg till alternativet i konsolen, innan du migrerar, i **[!UICONTROL Administration > Options]** nod:

* Internt namn: NlMigration_KeepFolderStructure
* Datatyp: Heltal
* Värde (text): 1

Om du använder det här alternativet måste du efter migreringen ta bort gamla mappar, lägga till nya mappar och köra alla nödvändiga kontroller.

**List of new folders**:

The following folders need to be added after the migration:

| Internt namn | Etikett | Villkor |
|---|---|---|
| nmsAutoObjects | Objekt som skapas automatiskt | - |
| nmsCampaignAdmin | Kampanjhantering | - |
| nmsCampaignMgt | Kampanjhantering | - |
| nmsCampaignRes | Kampanjhantering | - |
| nmsModels | Mallar | - |
| nmsOnlineRes | Online | - |
| nmsProduction | Produktion | - |
| nmsProfilProcess | Processer | - |
| xtkDashboard | Kontrollpaneler | - |
| xtkPlatformAdmin | Plattform | - |
| nmsLocalOrgUnit | Organisationsenheter | - |
| nmsMRM | MRM | MRM är installerat |
| nmsOperations | Kampanjer | Campaign har installerats |

**Lista över föråldrade mappar**:

De föråldrade mappar som ska tas bort efter migreringen är följande:

>[!NOTE]
>
>Hela innehållet i de föråldrade mapparna måste kontrolleras och för varje objekt avgör konsulten om de ska behålla eller ta bort det. De artiklar som ska behållas måste flyttas till lämplig plats.

| Internt namn | Etikett | Villkor |
|---|---|---|
| nmsAdministration | Administration | - |
| nmsDeliveryMgt | Kampanjkörning | - |
| ncmContent | Innehållshantering | Content Manager är installerat |
| ncmForm | Inmatningsformulär | Content Manager är installerat |
| ncmImage | Bilder | Content Manager är installerat |
| ncmJavascript | JavaScript-koder | Content Manager är installerat |
| ncmJst | JavaScript-mallar | Content Manager är installerat |
| ncmParameters | Konfiguration | Content Manager är installerat |
| ncmSrcSchema | Datascheman | Content Manager är installerat |
| ncmStylesheet | XSL-formatfiler | Content Manager är installerat |
| nmsAdminPlan | Administration | Campaign har installerats |
| nmsResourcePlan | Resurser | Campaign har installerats |
| nmsResourcesModels | Mallar | Campaign har installerats |
| nmsRootPlan | Kampanjhantering | Campaign har installerats |
| nmsOperator | Marknadsförare | MRM är installerat |


## Specifika konfigurationer från v6.02 till v7{#specific-configurations-in-v6-02}

![](../../assets/v7-only.svg)

I följande avsnitt beskrivs den ytterligare konfiguration som krävs vid migrering från v6.02. Du bör även konfigurera inställningarna i [den här sidan](../../migration/using/general-configurations.md).

### Webbapplikationer {#web-applications-v6}

Om du migrerar från v6.02 kan felloggar för webbprogram av översiktstyp visas. Exempel på felmeddelanden:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

Dessa webbprogram använde SQLData och är inte kompatibla med v7 på grund av högre säkerhet. Dessa fel leder till ett migreringsfel.

Om du inte använde dessa webbprogram kör du följande rensningsskript och kör efteruppgraderingen igen:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

Om du har ändrat dessa webbprogram och vill fortsätta använda dem i v7 måste du aktivera **allowSQLInjection** i dina olika säkerhetszoner och starta om efteruppgraderingen. Se [SQLData](../../migration/using/general-configurations.md#sqldata) om du vill ha mer information om detta.

### Meddelandecenter {#message-center}

Efter migrering av en kontrollinstans i Message Center måste du publicera om transaktionsmeddelandemallarna för att de ska fungera.

I v7 har namnen på transaktionsmeddelandemallar för körningsinstanser ändrats. De är för närvarande prefixerade av det operatörsnamn som motsvarar kontrollinstansen som de skapas i, till exempel **control1_template1_rt** (där **control1** är namnet på operatorn). Om du har ett stort antal mallar rekommenderar vi att du tar bort gamla mallar på kontrollinstanser.