---
title: Testa migreringen
seo-title: Testa migreringen
description: Testa migreringen
seo-description: null
page-status-flag: never-activated
uuid: 3ee6a10b-dea2-41c6-9aef-ee3ac922b459
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: 30e3082f-a367-4c3b-bff2-208ccf97acd4
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# Testa migreringen{#testing-the-migration}

## Allmänt förfarande {#general-procedure}

Beroende på konfigurationen finns det flera sätt att utföra migreringstester.

Du bör ha en test-/utvecklingsmiljö för att utföra migreringstester. För utvecklingsmiljöer krävs licens: kontrollera licensavtalet eller kontakta Adobe Campaigns säljavdelning.

1. Stoppa all pågående utveckling och föra över den till produktionsmiljön.
1. Säkerhetskopiera utvecklingsmiljödatabasen.
1. Stoppa alla Adobe Campaign-processer i utvecklingsinstansen.
1. Säkerhetskopiera produktionsmiljödatabasen och återställ den som en utvecklingsmiljö.
1. Innan du startar Adobe Campaign-tjänsterna kör du skriptet **frysinstans.js** som gör att du kan rensa databasen för alla objekt som kördes när säkerhetskopieringen startades.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >Kommandot startar som standard i **torrt** läge och visar alla begäranden som har utförts av det kommandot, utan att starta dem. Om du vill utföra en begäran om autentisering använder du **run** i kommandot.

1. Kontrollera att säkerhetskopiorna är korrekta genom att försöka återställa dem. Se till att du har tillgång till din databas, dina tabeller, dina data osv.
1. Testa migreringsproceduren i utvecklingsmiljön.

   De fullständiga procedurerna beskrivs i avsnittet [Krav för migrering till Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .

1. Om migreringen av utvecklingsmiljön lyckas kan du migrera produktionsmiljön.

>[!IMPORTANT]
>
>På grund av ändringar i datastrukturen går det inte att importera och exportera datapaket mellan en v5-plattform och en v7-plattform.

>[!NOTE]
>
>Med uppdateringskommandot i Adobe Campaign (**postuppgradering**) kan du synkronisera resurser och uppdateringsscheman samt databasen. Den här åtgärden kan bara utföras en gång på programservern. När resurserna har synkroniserats kan du med kommandot **postupgrade** identifiera om synkroniseringen genererar fel eller varningar.

## Migreringsverktyg {#migration-tools}

Med olika alternativ kan du mäta effekten av en migrering och identifiera potentiella problem. Dessa alternativ ska utföras:

* i **config** -kommandot:

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* eller vid uppgraderingen:

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>**Du måste använda`<instanceame>`**-instansen: alternativ. Vi rekommenderar inte att du använder alternativet**-allinstances **.

### -showCustomEntities och -showDeletedEntities, alternativ {#showcustomentities-and--showdeletedentities-options}

* Alternativet **-showCustomEntities** visar listan över alla objekt som inte är standard:

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   Exempel på ett skickat meddelande:

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* Alternativet **-showDeletedEntities** visar listan med alla standardobjekt som saknas i databasen eller filsystemet. För varje objekt som saknas anges sökvägen.

   ```
   nlserver.exe config -showDeletedEntities -instance:<instanceName>
   ```

   Exempel på ett skickat meddelande:

   ```
   Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
   ```

### Verifieringsprocess {#verification-process}

Den här processen är integrerad som standard i postuppgraderingskommandot och gör att du kan visa varningar och fel som kan få migreringen att misslyckas. **Om fel visas har migreringen inte körts.** Om detta händer korrigerar du alla fel och startar sedan om efteruppgraderingen.

Du kan starta verifieringsprocessen fristående (utan migrering) med kommandot:

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>Ignorera alla varningar och fel som har JST-310040-koden.

Följande uttryck söks efter (skiftlägeskänsliga):

<table> 
 <thead> 
  <tr> 
   <th> Uttryck<br /> </th> 
   <th> Felkod<br /> </th> 
   <th> Loggtyp<br /> </th> 
   <th> Kommentarer<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> Varning<br /> </td> 
   <td> Den här typen av syntax stöds inte längre i leveranspersonalisering. Se <a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>. Annars kontrollerar du att värdetypen är korrekt.<br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> Varning<br /> </td> 
   <td> Det här biblioteket får inte användas.<br /> </td> 
  </tr> 
  <tr> 
   <td> logon(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> Varning<br /> </td> 
   <td> Den här anslutningsmetoden får inte längre användas. Se <a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">Identifierade webbprogram</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall()<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> Varning<br /> </td> 
   <td> Den här funktionen stöds bara när den används i JavaScript-kod som körs från en säkerhetszon i <strong>sessionTokenOnly</strong> -läge.<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Den här typen av fel leder till ett migreringsfel. Se <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> SQLDATA<br /> </td> 
   <td> PU-0006<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Den här typen av fel leder till ett migreringsfel. Se <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>. Om du får felloggar av översiktstyp för webbprogram (migrering från v6.02), se <a href="../../migration/using/specific-configurations-in-v6-02.md#web-applications" target="_blank">Webbprogram</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

En konsekvenskontroll av databaser och scheman utförs också.

### Återställningsalternativ {#restoration-option}

Med det här alternativet kan du återställa färdiga objekt om de har ändrats. För varje återställt objekt sparas en säkerhetskopia av ändringarna i den valda mappen:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>Vi rekommenderar att du använder absoluta mappsökvägar och behåller mappträdsstrukturen. Till exempel: backupFolder\nms\srcSchema\billing.xml.

### Återupptar migrering {#resuming-migration}

Om du startar om efteruppgraderingen efter ett migreringsfel återupptas den från samma plats som den stoppades.
