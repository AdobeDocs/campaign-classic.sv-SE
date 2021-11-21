---
product: campaign
title: Specifika konfigurationer i version 5.11
description: Specifika konfigurationer i version 5.11
audience: migration
content-type: reference
topic-tags: configuration
exl-id: 978e1249-f79b-4f5f-9a94-3bb2510785de
source-git-commit: e719c8c94f1c08c6601b3386ccd99d250c9e606b
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 3%

---

# Specifika konfigurationer i version 5.11{#specific-configurations-in-v5-11}

![](../../assets/v7-only.svg)

I det här avsnittet beskrivs den ytterligare konfiguration som krävs vid migrering från v5.11. Du bör även konfigurera inställningarna som anges i [Allmänna konfigurationer](../../migration/using/general-configurations.md) -avsnitt.

## Webbapplikationer {#web-applications}

Följande varning visas automatiskt under migreringen:

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side JavaScript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Vissa komponenter i webbprogram, till exempel de olika formelfälten, har @id-attribut. De används i XML-koden för webbprogram och genereras inte längre på samma sätt. De är inte synliga i gränssnittet och du får normalt inte använda dem. I vissa fall kan @id-attribut ha använts för att anpassa återgivningen av webbprogram, till exempel via en formatmall eller JavaScript-kod.

Under migreringen kan du **måste** Kontrollera loggfilens sökväg som anges i varningen:

* **Filen är inte tom**: Den innehåller varningar som rör inkonsekvenser som registrerats före migreringen och som fortfarande finns. Detta kan vara JavaScript-kod i ett webbprogram som refererar till ett ID som inte finns. Varje fel måste kontrolleras och korrigeras.
* **Filen är tom**: detta innebär att Adobe Campaign inte har upptäckt några problem.

Oavsett om filen är tom eller inte måste du kontrollera att dessa ID:n inte används för konfiguration någon annanstans (och anpassa konfigurationen om så är fallet).

## Arbetsflöden {#workflows}

Eftersom namnet på Adobe Campaign installationskatalog har ändrats kanske vissa arbetsflöden inte fungerar efter migreringen. Om ett arbetsflöde refererar till katalogen nl5 i någon av dess aktiviteter genereras ett fel. Ersätt den här referensen med **bygga**. Du kan köra en SQL-fråga för att identifiera dessa arbetsflöden (PostgreSQL-exempel):

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

## Användarvänlighet {#user-friendliness}

Hemsidan för Adobe Campaign v5.11 är inte längre tillgänglig.

Även om det inte rekommenderas finns det vissa lösningar om du vill behålla specifika gränssnitt från Adobe Campaign v5.11. Kontakta oss om du vill ha mer information.

## MySQL {#mysql}

>[!IMPORTANT]
>
>MySQL stöds bara i v7 som huvuddatabasmotor när du migrerar från version 6.02 eller 5.11 med den här motorn.

MySQL hanterar inte tidszoner som standard. Om du vill aktivera hantering av tidszoner kör du följande kommando:

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>Mer information finns i [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) sida.

Om databasstrukturen har ändrats, t.ex. under konfiguration (skapa specifika index, skapa SQL-vyer osv.), bör vissa försiktighetsåtgärder vidtas vid migrering. Vissa ändringar kan ha sin grund i inkompatibilitet med migreringsförfarandet. Skapa t.ex. SQL-vyer som innehåller **Tidsstämpel** fälten är inte kompatibla med **usetimestamptz** alternativ. Vi rekommenderar därför att du följer rekommendationerna nedan:

1. Innan du startar migreringen bör du säkerhetskopiera databasen.
1. Ta bort SQL-ändringar.
1. Utför efteruppgraderingen enligt proceduren som beskrivs i  [Krav för migrering till Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) -avsnitt.
   >[!NOTE]
   >
   >Du måste följa migreringsstegen i [Krav för migrering till Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) -avsnitt.
1. Återintegrera SQL-ändringar.

I det här exemplet **NmcTrackingLogMessages** vyn har skapats och har en **Tidsstämpel** fält namngivet **tslog**. I det här fallet misslyckas migreringsproceduren och följande felmeddelande visas:

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

För att vara säker på att efteruppgraderingen fungerar måste du ta bort vyn före migreringen och återskapa den efter migreringen samtidigt som du anpassar den till TIMESTAMP MED TIMEZONE-läget.

## Spåra {#tracking}

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

## Trädstruktur för Adobe Campaign v7 {#campaign-vseven-tree-structure}

Under migreringen ordnas trädstrukturen automatiskt om baserat på v7-standarderna. De nya mapparna läggs till, de föråldrade mapparna tas bort och deras innehåll placeras i mappen &quot;Att flytta&quot;. Alla objekt i den här mappen måste kontrolleras efter migreringen, och konsulten måste välja att antingen behålla eller ta bort varje objekt. Objekt som ska behållas måste flyttas till rätt plats.

Ett alternativ har lagts till för att inaktivera automatisk migrering av navigeringsträdet. Den här åtgärden är nu manuell. Föråldrade mappar tas inte bort och nya mappar läggs inte till. Det här alternativet bör endast användas om det färdiga v5-navigeringsträdet har genomgått för många ändringar. Lägg till alternativet i konsolen, innan du migrerar, i **[!UICONTROL Administration > Options]** nod:

* Internt namn: NlMigration_KeepFolderStructure
* Datatyp: Heltal
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
| ncmSrcSchema | Datascheman | Content Manager är installerat |
| ncmStylesheet | XSL-formatfiler | Content Manager är installerat |
| nmsAdminPlan | Administration | Campaign har installerats |
| nmsResourcePlan | Resurser | Campaign har installerats |
| nmsResourcesModels | Mallar | Campaign har installerats |
| nmsRootPlan | Kampanjhantering | Campaign har installerats |
| nmsOperator | Marknadsförare | MRM är installerat |
