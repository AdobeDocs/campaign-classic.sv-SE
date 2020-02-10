---
title: Specifika konfigurationer i v5.11
seo-title: Specifika konfigurationer i v5.11
description: Specifika konfigurationer i v5.11
seo-description: null
page-status-flag: never-activated
uuid: d6920beb-a766-4aec-8a8e-d32e47b545a4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: fc280640-528d-44de-87d8-52f443772abd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 703fa6e5d5e6f1c8c512bd65ebadad724f02ded3

---


# Specifika konfigurationer i v5.11{#specific-configurations-in-v5-11}

I det här avsnittet beskrivs den ytterligare konfiguration som krävs vid migrering från v5.11. Du bör även konfigurera inställningarna som anges i avsnittet [Allmänna konfigurationer](../../migration/using/general-configurations.md) .

## Webbprogram {#web-applications}

Följande varning visas automatiskt under migreringen:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side javascript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Vissa komponenter i webbprogram, till exempel de olika formelfälten, har @id-attribut. De används i XML-koden för webbprogram och genereras inte längre på samma sätt. De är inte synliga i gränssnittet och du får normalt inte använda dem. I vissa fall kan @id-attribut ha använts för att anpassa återgivningen av webbprogram, till exempel via en formatmall eller JavaScript-kod.

Under migreringen **måste** du kontrollera loggfilens sökväg som anges i varningen:

* **Filen är inte tom**: Den innehåller varningar som rör inkonsekvenser som registrerats före migreringen och som fortfarande finns. Detta kan vara JavaScript-kod i ett webbprogram som refererar till ett ID som inte finns. Varje fel måste kontrolleras och korrigeras.
* **Filen är tom**: detta innebär att Adobe Campaign inte har upptäckt några problem.

Oavsett om filen är tom eller inte måste du kontrollera att dessa ID:n inte används för konfiguration någon annanstans (och anpassa konfigurationen om så är fallet).

## Arbetsflöden {#workflows}

Eftersom namnet på installationskatalogen för Adobe Campaign har ändrats kanske vissa arbetsflöden inte fungerar efter migreringen. Om ett arbetsflöde refererar till katalogen nl5 i någon av dess aktiviteter genereras ett fel. Ersätt den här referensen med **bygge**. Du kan köra en SQL-fråga för att identifiera dessa arbetsflöden (PostgreSQL-exempel):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

## Användarvänlighet {#user-friendliness}

Startsidan för Adobe Campaign v5.11 är inte längre tillgänglig.

Även om det inte rekommenderas finns det vissa lösningar om du vill behålla specifika gränssnitt från Adobe Campaign v5.11. Kontakta oss om du vill ha mer information.

## MySQL {#mysql}

>[!CAUTION]
>
>MySQL stöds bara i v7 som huvuddatabasmotor när du migrerar från version 6.02 eller 5.11 med den här motorn.

MySQL hanterar inte tidszoner som standard. Om du vill aktivera hantering av tidszoner kör du följande kommando:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>Mer information finns på [http://dev.mysql.com/doc/refman/5.5/en/time-zone-support.html](http://dev.mysql.com/doc/refman/5.5/en/time-zone-support.html) .

Om databasstrukturen har ändrats, t.ex. under konfiguration (skapa specifika index, skapa SQL-vyer osv.), bör vissa försiktighetsåtgärder vidtas vid migrering. Vissa ändringar kan ha sin grund i inkompatibilitet med migreringsförfarandet. Att skapa SQL-vyer som innehåller **tidsstämpelfält** är till exempel inte kompatibelt med alternativet **usetimestamptz** . Vi rekommenderar därför att du följer rekommendationerna nedan:

1. Innan du startar migreringen bör du säkerhetskopiera databasen.
1. Ta bort SQL-ändringar.
1. Utför efteruppgraderingen enligt den procedur som beskrivs i [Krav för migrering till Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .
   >[!NOTE]
   >
   >Du måste följa de migreringssteg som beskrivs i [Krav för migrering till Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .
1. Återintegrera SQL-ändringar.

I det här exemplet har en **vy av typen NmcTrackingLogMessages** skapats och den har ett **tidsstämpelfält** med namnet **tslog**. I det här fallet misslyckas migreringsproceduren och följande felmeddelande visas:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

För att vara säker på att efteruppgraderingen fungerar måste du ta bort vyn före migreringen och återskapa den efter migreringen samtidigt som du anpassar den till TIMESTAMP MED TIMEZONE-läget.

## Spårning {#tracking}

Spårningsformeln har ändrats. När du migrerar ersätts den gamla formeln (v5) med den nya (v7). Om du använder en anpassad formel i Adobe Campaign v5 måste den här konfigurationen anpassas i Adobe Campaign v7 (**alternativen NmsTracking_ClickFormula** och **NmsTracking_OpenFormula** ).

Hanteringen av webbspårning har också ändrats. När migreringen till v7 har slutförts måste du starta distributionsguiden för att slutföra konfigurationen av webbspårningen.

![](assets/migration_web_tracking.png)

Tre lägen är tillgängliga:

* **Sessionswebbspårning**: Om paketet inte har installerats är det här alternativet valt som standard. **[!UICONTROL Leads]** Det här alternativet är det mest idealiska när det gäller prestanda och du kan begränsa spårningsloggarnas storlek.
* **Permanent webbspårning**
* **Anonym webbspårning**: Om paketet är installerat är det här alternativet valt som standard. **[!UICONTROL Leads]** Det är det mest resurskrävande alternativet. Som ovan måste **sSourceId** -kolumnen indexeras (i spårningstabellen och **CrmIncomingLead** -tabellen).

>[!NOTE]
>
>Mer information om dessa tre lägen finns i [det här avsnittet](../../configuration/using/about-web-tracking.md).

## Trädstruktur för Adobe Campaign v7 {#campaign-vseven-tree-structure}

Under migreringen ordnas trädstrukturen automatiskt om baserat på v7-standarderna. De nya mapparna läggs till, de föråldrade mapparna tas bort och deras innehåll placeras i mappen &quot;Att flytta&quot;. Alla objekt i den här mappen måste kontrolleras efter migreringen och konsulten måste välja att antingen behålla eller ta bort varje objekt. Objekt som ska behållas måste flyttas till rätt plats.

Ett alternativ har lagts till för att inaktivera automatisk migrering av navigeringsträdet. Den här åtgärden är nu manuell. Föråldrade mappar tas inte bort och nya mappar läggs inte till. Det här alternativet bör endast användas om det färdiga v5-navigeringsträdet har genomgått för många ändringar. Lägg till alternativet i konsolen, innan du migrerar, i **[!UICONTROL Administration > Options]** noden:

* Internt namn: NlMigration_KeepFolderStructure
* Datatyp:Heltal
* Värde (text): 1

Om du använder det här alternativet måste du efter migreringen ta bort gamla mappar, lägga till nya mappar och köra alla nödvändiga kontroller.

**Lista över nya mappar**:

Följande mappar måste läggas till efter migreringen:

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
| ncmSrcSchema | Datamodeller | Content Manager är installerat |
| ncmStylesheet | XSL-formatfiler | Content Manager är installerat |
| nmsAdminPlan | Administration | Campaign har installerats |
| nmsResourcePlan | Resurser | Campaign har installerats |
| nmsResourcesModels | Mallar | Campaign har installerats |
| nmsRootPlan | Kampanjhantering | Campaign har installerats |
| nmsOperator | Marknadsförare | MRM är installerat |

