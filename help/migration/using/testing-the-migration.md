---
product: campaign
title: Testa migreringen
description: Testa migreringen
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Migreringstester{#testing-the-migration}



## Allmänt förfarande {#general-procedure}

Beroende på konfigurationen finns det flera sätt att utföra migreringstester.

Du bör ha en test-/utvecklingsmiljö för att utföra migreringstester. Användningen av Adobe Campaign-miljöer regleras av licensavtal: kontrollera licensavtalet eller kontakta Adobe.

1. Stoppa all pågående utveckling och föra över den till produktionsmiljön.
1. Säkerhetskopiera utvecklingsmiljödatabasen.
1. Stoppa alla Adobe Campaign-processer i utvecklingsinstansen.
1. Säkerhetskopiera produktionsmiljödatabasen och återställ den som en utvecklingsmiljö.
1. Innan du startar Adobe Campaign-tjänsterna kör du **frysinstansskriptet.js** som gör att du kan rensa databasen för alla objekt som kördes när säkerhetskopieringen startades.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >Kommandot startar som standard i läget **dry** och visar alla begäranden som kördes av det kommandot, utan att starta dem. Använd **run** i kommandot för att köra autentiseringsbegäranden.

1. Kontrollera att säkerhetskopiorna är korrekta genom att försöka återställa dem. Se till att du har tillgång till din databas, dina tabeller, dina data osv.
1. Testa migreringsproceduren i utvecklingsmiljön.
1. Om migreringen av utvecklingsmiljön lyckas kan du migrera produktionsmiljön.

>[!CAUTION]
>
>På grund av ändringar i datastrukturen går det inte att importera och exportera datapaket mellan en v5-plattform och en v7-plattform.


## Migreringsverktyg {#migration-tools}

Med olika alternativ kan du mäta effekten av en migrering och identifiera potentiella problem. Dessa alternativ ska utföras:

* i kommandot **config**:

  ```
  nlserver.exe config <option> -instance:<instance-name>
  ```

* eller vid uppgraderingen:

  ```
  nlserver.exe config -postupgrade <option> -instance:<instance-name>
  ```

>[!NOTE]
>
>* Du måste använda alternativet **-instance:`<instanceame>`**. Vi rekommenderar inte att du använder alternativet **-allinstances**.
>* Med Adobe Campaign-uppdateringskommandot (**postupgrade**) kan du synkronisera resurser och uppdateringsscheman samt databasen. Den här åtgärden kan bara utföras en gång på programservern. När resurserna har synkroniserats kan du med kommandot **postupgrade** identifiera om synkroniseringen genererar fel eller varningar.

### Objekt som inte är standard eller saknas

* Alternativet **-showCustomEntities** visar listan över alla objekt som inte är standard:

  ```
  nlserver.exe config -showCustomEntities -instance:<instance-name>
  ```

  Exempel på ett skickat meddelande:

  ```
  xtk_migration:opsecurity2 xtk:entity
  ```

* Alternativet **-showDeletedEntities** visar en lista över alla standardobjekt som saknas i databasen eller filsystemet. För varje objekt som saknas anges sökvägen.

  ```
  nlserver.exe config -showDeletedEntities -instance:<instance-name>
  ```

  Exempel på ett skickat meddelande:

  ```
  Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
  ```

### Verifieringsprocess {#verification-process}

Den här processen är integrerad som standard i postuppgraderingskommandot och gör att du kan visa varningar och fel som kan få migreringen att misslyckas. **Om fel visas har migreringen inte körts.** Om detta händer korrigerar du alla fel och startar sedan om efteruppgraderingen.

Du kan starta verifieringsprocessen fristående (utan migrering) med kommandot:

```
nlserver.exe config -postupgrade -check -instance:<instance-name>
```

>[!NOTE]
>
>Du kan ignorera alla varningar och fel med JST-310040-koden.

Följande uttryck söks efter (skiftlägeskänsliga):

<table> 
 <thead> 
  <tr> 
   <th> Uttryck <br /> </th> 
   <th> Felkod <br /> </th> 
   <th> Loggtyp <br /> </th> 
   <th> Kommentarer<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> Varning<br /> </td> 
   <td> Den här typen av syntax stöds inte längre i leveranspersonalisering. <br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> Varning<br /> </td> 
   <td> Det här biblioteket får inte användas.<br /> </td> 
  </tr> 
  <tr> 
   <td> logon(<br />) </td> 
   <td> PU-0003<br /> </td> 
   <td> Varning<br /> </td> 
   <td> Den här anslutningsmetoden får inte längre användas.<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br />) </td> 
   <td> PU-0004<br /> </td> 
   <td> Varning<br /> </td> 
   <td> Den här funktionen stöds bara när den används i JavaScript-kod som körs från en säkerhetszon i läget <strong>sessionTokenOnly</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> Fel <br /> </td> 
   <td> Den här typen av fel leder till ett migreringsfel.<br /> </td> 
  </tr> 
  <tr> 
   <td> crmDeploymentType="lokal"<br /> </td> 
   <td> PU-0007<br /> </td> 
   <td> Fel <br /> </td> 
   <td> Den här typen av distribution stöds inte längre. Distributionstypen för Office 365- och On-Local Microsoft CRM Connector har nu tagits bort. 
   </br>Om du använder någon av de här inaktuella distributionstyperna i ett externt konto bör det externa kontot tas bort och du bör sedan köra kommandot <b> postupgrade</b> . 
   </br>Om du vill ändra till Web API-distribution läser du <a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">Webbprogram</a>.<br /> </td>
  </tr> 
  <tr> 
   <td> CRM v1(mscrmArbetsflöde/sfdcWorkflow)<br /> </td> 
   <td> PU-0008<br /> </td> 
   <td> Fel <br /> </td> 
   <td> Åtgärder i Microsoft CRM, Salesforce och Oracle CRM On Demand är inte längre tillgängliga. Om du vill konfigurera datasynkroniseringen mellan Adobe Campaign och ett CRM-system måste du använda målinriktningsaktiviteten för <a href="../../workflow/using/crm-connector.md" target="_blank">CRM-anslutningen</a>.<br /> </td>
  </tr> 
 </tbody> 
</table>

En konsekvenskontroll av databaser och scheman utförs också.

### Återställningsalternativ {#restoration-option}

Med det här alternativet kan du återställa färdiga objekt om de har ändrats. För varje återställt objekt sparas en säkerhetskopia av ändringarna i den valda mappen:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instance-name>
```

>[!NOTE]
>
>Vi rekommenderar att du använder absoluta mappsökvägar och behåller mappträdsstrukturen. Till exempel: backupFolder\nms\srcSchema\billing.xml.

### Återuppta migreringen {#resuming-migration}

Om du startar om efteruppgraderingen efter ett migreringsfel återupptas den från samma plats som den stoppades.
