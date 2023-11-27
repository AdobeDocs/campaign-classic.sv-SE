---
product: campaign
title: Arbetsflöde för databasrensning
description: Se hur gamla data rensas automatiskt
feature: Monitoring, Workflows
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: 624978901943b4c74f50c20298c9596f73b25b1b
workflow-type: tm+mt
source-wordcount: '2830'
ht-degree: 0%

---

# Arbetsflöde för databasrensning{#database-cleanup-workflow}



## Introduktion {#introduction}

The **[!UICONTROL Database cleanup]** arbetsflöde tillgängligt via **[!UICONTROL Administration > Production > Technical workflows]** -nod, kan du ta bort föråldrade data för att undvika exponentiell tillväxt i databasen. Arbetsflödet utlöses automatiskt utan användaråtgärder.

![cleanup](assets/ncs_cleanup_workflow.png)

## Konfiguration {#configuration}

Databasrensningen är konfigurerad på två nivåer: i arbetsflödets schemaläggare och i distributionsguiden.

### Arbetsflödesplanerare {#the-scheduler}

>[!NOTE]
>
>Mer information om schemaläggaren finns i [det här avsnittet](../../workflow/using/scheduler.md).

Som standard är **[!UICONTROL Database cleanup]** arbetsflödet är konfigurerat att starta varje dag kl. 4.00. Med schemaläggaren kan du ändra arbetsflödets utlösande frekvens. Följande frekvenser är tillgängliga:

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![schemaläggare](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>För att **[!UICONTROL Database cleanup]** arbetsflödet som ska starta vid det datum och den tidpunkt som anges i schemaläggaren, måste startas (wfserver).

### Distributionsguide {#deployment-wizard}

The **[!UICONTROL Deployment wizard]**, via **[!UICONTROL Tools > Advanced]** kan du konfigurera hur länge data sparas för. Värdena anges i dagar. Om dessa värden inte ändras används standardvärdena i arbetsflödet.

![](assets/ncs_cleanup_deployment-wizard.png)

Fälten i **[!UICONTROL Purge of data]** fönstret visas med följande alternativ. Dessa används av vissa av uppgifterna som körs av **[!UICONTROL Database cleanup]** arbetsflöde:

* Konsoliderad spårning: **NmsCleanup_TrackingStatPurgeDelay** (se [Rensa spårningsloggar](#cleanup-of-tracking-logs))
* Leveransloggar: **NmsCleanup_BroadLogPurgeDelay** (se [Rensa leveransloggar](#cleanup-of-delivery-logs))
* Spårningsloggar: **NmsCleanup_TrackingLogPurgeDelay** (se [Rensa spårningsloggar](#cleanup-of-tracking-logs))
* Borttagna leveranser: **NmsCleanup_RecycledDeliveryPurgeDelay** (se [Rensa leveranser som ska raderas eller återvinnas](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* Importavvisanden: **NmsCleanup_RejectsPurgeDelay** (se [Rensa nekanden som genererats av import](#cleanup-of-rejects-generated-by-imports-))
* Besökarprofiler: **NmsCleanup_VisitorPurgeDelay** (se [Rensa besökare](#cleanup-of-visitors))
* Erbjudandeförslag: **NmsCleanup_PropositionPurgeDelay** (se [Rensa förslag](#cleanup-of-propositions))

  >[!NOTE]
  >
  >The **[!UICONTROL Offer propositions]** fältet är bara tillgängligt när **Interaktion** -modulen är installerad.

* Händelser: **NmsCleanup_EventPurgeDelay** (se [Rensar utgångna händelser](#cleansing-expired-events))
* Arkiverade händelser: **NmsCleanup_EventHistoryPurgeDelay** (se [Rensar utgångna händelser](#cleansing-expired-events))

  >[!NOTE]
  >
  >The **[!UICONTROL Events]** och **[!UICONTROL Archived events]** fält är bara tillgängliga om **Meddelandecenter** -modulen är installerad.

* Granskningsspår: **XtkCleanup_AuditTrailPurgeDelay** (se [Rensa granskningsspår](#cleanup-of-audit-trail))

Alla uppgifter som körs av **[!UICONTROL Database cleanup]** arbetsflödet beskrivs i följande avsnitt.

## Uppgifter som utförs i arbetsflödet för databasrensning {#tasks-carried-out-by-the-database-cleanup-workflow}

Vid det datum och den tid som definieras i arbetsflödets schemaläggare (se [Schemaläggaren](#the-scheduler)) startar arbetsflödesmotorn databasrensningsprocessen. Rensningen av databasen ansluter till databasen och utför åtgärderna i den sekvens som visas nedan.

>[!IMPORTANT]
>
>Om en av dessa uppgifter misslyckas utförs inte nästa uppgift.
>
>SQL-frågor med en **BEGRÄNSNING** attribut körs upprepade gånger tills all information har bearbetats.


### Listor som ska tas bort {#lists-to-delete-cleanup}

Den första aktiviteten som körs av **[!UICONTROL Database cleanup]** arbetsflödet tar bort alla grupper med **deleteStatus != 0** attribut från **NmsGroup**. Poster som är länkade till de här grupperna och som finns i andra tabeller tas också bort.

1. Listor som ska tas bort återställs med följande SQL-fråga:

   ```sql
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. Varje lista har flera länkar till andra tabeller. Alla länkarna tas bort i grupp med följande fråga:

   ```sql
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   där `$(relatedTable)` är ett register som är relaterat till **NmsGroup** och `$(l)` är listidentifieraren.

1. När listan är en lista av typen List tas den associerade tabellen bort med följande fråga:

   ```sql
   DROP TABLE grp$(l)
   ```

1. Varje **Välj** typlistan som återställdes av åtgärden tas bort med följande fråga:

   ```sql
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   där `$(l)` är listidentifieraren

### Rensa leveranser som ska raderas eller återvinnas {#cleanup-of-deliveries-to-be-deleted-or-recycled}

Den här aktiviteten rensar alla leveranser som ska tas bort eller återvinnas.

1. The **[!UICONTROL Database cleanup]** arbetsflödet väljer alla leveranser för vilka **deleteStatus** fältet har värdet **[!UICONTROL Yes]** eller **[!UICONTROL Recycled]** och vars raderingsdatum är tidigare än den period som definierats i **[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecycledDeliveryPurgeDelay**) i distributionsguiden. Mer information finns i [Distributionsguide](#deployment-wizard). Perioden beräknas i relation till aktuellt serverdatum.
1. För varje server med mellanleverantörer väljer aktiviteten listan över leveranser som ska tas bort.
1. The **[!UICONTROL Database cleanup]** arbetsflödet tar bort leveransloggar, bilagor, information om spegelsidor och alla andra relaterade data.
1. Innan leveransen tas bort rensas länkad information från följande tabeller bort:

   * I tabellen för uteslutning av leverans (**NmsDlvExclusion**) används följande fråga:

     ```sql
     DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
     ```

     där **$(l)** är leveransens identifierare.

   * I kupongtabellen (**NmsCouponValue**) används följande fråga (med massborttagningar):

     ```sql
     DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
     ```

     där `$(l)` är leveransens identifierare.

   * I leveransloggtabellerna (**NmsBroadlogXx**) utförs massraderingar i grupper om 20 000 poster.
   * I offerttabellen (**NmsPropositionXx**) utförs massraderingar i grupper om 20 000 poster.
   * I spårningsloggtabellerna (**NmsTrackinglogXx**) utförs massraderingar i grupper om 20 000 poster.
   * I leveransfragmenttabellen (**NmsDeliveryPart**) utförs massraderingar i grupper om 500 000 poster. Det här registret innehåller information om personalisering för de meddelanden som återstår att leverera.
   * I spegelsidans datagragmenttabell (**NmsMirrorPageInfo**) utförs massraderingar i grupper om 20 000 poster för utgångna leveransdelar och för avslutade eller annullerade delar. Den här tabellen innehåller personaliseringsinformation om alla meddelanden som används för att generera spegelsidor.
   * I söktabellen med spegelsidor (**NmsMirrorPageSearch**) utförs massraderingar i grupper om 20 000 poster. Det här registret är ett sökindex som ger åtkomst till personaliseringsinformation som lagras i **NmsMirrorPageInfo** tabell.
   * I batchprocessloggtabellen (**XtkJobLog**) utförs massraderingar i grupper om 20 000 poster. Det här registret innehåller loggen över leveranser som ska tas bort.
   * I URL-spårningstabellen för leverans (**NmsTrackingUrl**) används följande fråga:

     ```sql
     DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
     ```

     där `$(l)` är leveransens identifierare.

     Den här tabellen innehåller de URL:er som finns i leveranserna som ska tas bort för att aktivera spårning av dem.

1. Leveransen tas bort från leveransregistret (**NmsDelivery**):

   ```sql
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   där `$(l)` är leveransens identifierare.

#### Leveranser med medelhög källkod {#deliveries-using-mid-sourcing}

The **[!UICONTROL Database cleanup]** arbetsflödet tar också bort leveranser från servern/servrarna med mellankällor.

1. För att göra detta kontrollerar arbetsflödet att varje leverans är inaktiv (baserat på dess status). Om en leverans är aktiv stoppas den innan den tas bort. Kontrollen utförs genom att följande fråga körs:

   ```sql
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   där **$(l)** är leveransens identifierare.

1. Om statusvärdet är **[!UICONTROL Start pending]** , **[!UICONTROL In progress]** , **[!UICONTROL Recovery pending]** , **[!UICONTROL Recovery in progress]** , **[!UICONTROL Pause requested]** , **[!UICONTROL Pause in progress]** , eller **[!UICONTROL Paused]** (värden 51, 55, 61, 62, 71, 72, 75) stoppas leveransen och aktiviteten tömmer den länkade informationen.

### Rensa utgångna leveranser {#cleanup-of-expired-deliveries}

Den här aktiviteten stoppar leveranser vars giltighetsperiod har gått ut.

1. The **[!UICONTROL Database cleanup]** arbetsflödet skapar en lista över leveranser som har upphört att gälla. Den här listan innehåller alla utgångna leveranser med en annan status än **[!UICONTROL Finished]** , samt nyligen stoppade leveranser med över 10 000 obearbetade meddelanden. Följande fråga används:

   ```sql
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   där `delivery mode 1` matchar **[!UICONTROL Mass delivery]** läge, `state 51` matchar **[!UICONTROL Start pending]** tillstånd, `state 85` matchar **[!UICONTROL Stopped]** och det högsta antalet leveransloggar som uppdateras på leveransservern är 10 000.

1. Arbetsflödet innehåller sedan en lista över nyligen utgångna leveranser som använder mellanleverantörer. Leveranser för vilka inga leveransloggar har återställts via servern med mellanlagring är undantagna.

   Följande fråga används:

   ```sql
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. Följande fråga används för att identifiera om det externa kontot fortfarande är aktivt eller inte, för att filtrera leveranser efter datum:

   ```sql
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. I listan över utgångna leveranser, leveransloggar vars status är **[!UICONTROL Pending]** , växla till **[!UICONTROL Delivery cancelled]** och alla leveranser i den här listan växlar till **[!UICONTROL Finished]** .

   Följande frågor används:

   ```sql
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   där `$(curdate)`är databasserverns aktuella datum, `$(bl)` är identifieraren för leveransloggmeddelandet, `$(dl)` är leveransidentifierare, `delivery status 6` matchar **[!UICONTROL Pending]** status och `delivery status 7` matchar **[!UICONTROL Delivery cancelled]** status.

   ```sql
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   där `delivery state 95` matchar **[!UICONTROL Finished]** status, och `$(dl)` är leveransens identifierare.

1. Alla fragment (**deliveryParts**) av föråldrade leveranser tas bort och alla föråldrade fragment av pågående meddelandeleveranser tas bort. Massborttagning används för båda dessa uppgifter.

   Följande frågor används:

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   där `delivery state 95` matchar **[!UICONTROL Finished]** status, `delivery state 85` matchar **[!UICONTROL Stopped]** status, och `$(curDate)` är aktuellt serverdatum.

### Rensa spegelsidor {#cleanup-of-mirror-pages}

Den här uppgiften tar bort de webbresurser (spegelsidor) som används av leveranser.

1. Först och främst återställs listan över leveranser som ska rensas med följande fråga:

   ```sql
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)
   ```

   där `$(curDate)` är aktuellt serverdatum.

1. The **NmsMirrorPageInfo** tabellen rensas, om det behövs med hjälp av identifieraren för den tidigare återskapade leveransen. Massborttagning används för att generera följande frågor:

   ```sql
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   ```sql
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   där `$(dl)` är leveransens identifierare.

1. En post läggs sedan till i leveransloggen.
1. Rensade leveranser identifieras sedan så att de inte behöver bearbetas igen senare. Följande fråga körs:

   ```sql
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   där `$(strIn)` är listan med leveransidentifierare.

### Rensa arbetsregister {#cleanup-of-work-tables}

Den här uppgiften tar bort alla arbetsregister som matchar leveranser vars status är **[!UICONTROL Being edited]** , **[!UICONTROL Stopped]** eller **[!UICONTROL Deleted]** .

1. Listan med tabeller med namn som börjar med **wkDlv_** återställs först med följande fråga (postgresq):

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Tabellerna som används av pågående arbetsflöden exkluderas sedan. För att göra detta återställs listan över pågående leveranser med följande fråga:

   ```sql
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   där `0` är värdet som matchar **[!UICONTROL Being edited]** leveransstatus, `85` matchar **[!UICONTROL Stopped]** status och `100` matchar **[!UICONTROL Deleted]** status.

1. Tabeller som inte längre används tas bort med följande fråga:

   ```sql
   DROP TABLE wkDlv_15487_1;
   ```

### Rensa nekanden som genererats av import {#cleanup-of-rejects-generated-by-imports-}

I det här steget kan du ta bort poster som inte bearbetades av alla data under importen.

1. Massradering utförs på **XtkReject** tabell med följande fråga:

   ```sql
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l)
   ```

   där `$(curDate)` är det aktuella serverdatumet från vilket vi subtraherar den period som definierats för **NmsCleanup_RejectsPurgeDelay** alternativ (se [Distributionsguide](#deployment-wizard)) och `$(l)` är det högsta antalet poster som får tas bort.

1. Alla ignorerade objekt tas sedan bort med följande fråga:

   ```sql
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### Rensa arbetsflödesinstanser {#cleanup-of-workflow-instances}

Den här aktiviteten rensar varje arbetsflödesinstans med hjälp av dess identifierare (**lWorkflowId**) och historik (**Historik**). Den tar bort inaktiva tabeller genom att köra arbetstabellrensningsåtgärden igen. Rensningen tar också bort alla överblivna arbetstabeller (wkf% och wkfhisto%) i borttagna arbetsflöden.

>[!NOTE]
>
>Historikens tömningsfrekvens anges för varje arbetsflöde i **Historik på dagar** fält (standardvärde 30 dagar). Det här fältet finns i **Körning** -fliken i arbetsflödesegenskaperna. Mer information om detta finns i [det här avsnittet](../../workflow/using/workflow-properties.md#execution).

1. Följande fråga används för att återställa listan med arbetsflöden som ska tas bort:

   ```sql
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. Den här frågan genererar en lista över arbetsflöden som kommer att användas för att ta bort alla länkade loggar, slutförda uppgifter och slutförda händelser med hjälp av följande frågor:

   ```sql
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```sql
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```sql
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   där `$(lworkflow)` är identifieraren för arbetsflödet och `$(lhistory)` är historikens identifierare.

1. Alla oanvända tabeller tas bort. För detta ändamål samlas alla tabeller in tack vare en **wkf%** skriv masken med följande fråga (efter):

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. Därefter exkluderas alla tabeller som används av en väntande arbetsflödesinstans. Listan över aktiva arbetsflöden återställs med följande fråga:

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. Varje arbetsflödes-ID återställs sedan för att hitta namnet på tabellerna som används i pågående arbetsflöden. Dessa namn tas inte med i listan över tidigare återställda tabeller.
1. Aktivitetshistoriktabeller av typen &quot;inkrementell fråga&quot; exkluderas med hjälp av följande frågor:

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   där `$(strcondition)` är listan med tabeller som matchar **wkfhisto%** mask.

1. De återstående tabellerna tas bort med följande fråga:

   ```sql
   DROP TABLE wkf15487_12;
   ```

### Rensa arbetsflödesinloggningar {#cleanup-of-workflow-logins}

Den här uppgiften tar bort arbetsflödesinloggningar med följande fråga:

```sql
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### Rensa tabeller över överblivna arbeten {#cleanup-of-orphan-work-tables}

Den här aktiviteten tar bort överblivna arbetsregister som är länkade till grupper. The **NmsGroup** I tabellen lagras de grupper som ska rensas (med en annan typ än 0). Prefixet för tabellnamnen är **grå**. Följande fråga används för att identifiera de grupper som ska rensas:

```sql
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### Rensa besökare {#cleanup-of-visitors}

Den här uppgiften tar bort inaktuella poster från besökstabellen med massborttagning. Föråldrade poster är de för vilka den senaste ändringen är tidigare än den bevarandeperiod som definierats i distributionsguiden (se [Distributionsguide](#deployment-wizard)). Följande fråga används:

```sql
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

där `$(tsDate)` är det aktuella serverdatumet, från vilket vi subtraherar den period som definierats för **NmsCleanup_VisitorPurgeDelay** alternativ.

### Rensa NPAI {#cleanup-of-npai}

Med den här åtgärden kan du ta bort poster som matchar giltiga adresser i **NmsAddress** tabell. Följande fråga används för att utföra massborttagning:

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

där `status 2` matchar **[!UICONTROL Valid]** status, `$(tsDate1)` är aktuellt serverdatum, och `$(tsDate2)` matchar **NmsCleanup_LastCleanup** alternativ.

### Rensa prenumerationer {#cleanup-of-subscriptions-}

Den här aktiviteten tar bort alla prenumerationer som tagits bort av användaren från **NmsSubscription** tabell, använda massborttagning. Följande fråga används:

```sql
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### Rensa spårningsloggar {#cleanup-of-tracking-logs}

Den här uppgiften tar bort inaktuella poster från loggtabellerna för spårning och webbspårning. Föråldrade poster är poster som är tidigare än den bevarandeperiod som definieras i distributionsguiden (se [Distributionsguide](#deployment-wizard)).

1. Först återställs listan med spårningsloggtabeller med följande fråga:

   ```sql
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. Massborttagning används för att rensa alla tabeller i listan med tidigare återskapade tabeller. Följande fråga används:

   ```sql
   DELETE FROM NmsTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM NmsTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   där `$(tsDate)` är det aktuella serverdatumet från vilket vi subtraherar den period som definierats för **NmsCleanup_TrackingLogPurgeDelay** alternativ.

1. Registret för spårningsstatistik rensas med massborttagning. Följande fråga används:

   ```sql
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   där `$(tsDate)` är det aktuella serverdatumet från vilket vi subtraherar den period som definierats för **NmsCleanup_TrackingStatPurgeDelay** alternativ.

### Rensa leveransloggar {#cleanup-of-delivery-logs}

Med den här uppgiften kan du rensa leveransloggarna som lagras i olika tabeller.

1. För detta ändamål återställs listan med leveransloggscheman med följande fråga:

   ```sql
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. När du använder mellanleverantörer är **NmsBroadLogMid** Det finns ingen referens till tabellen i leveransmappningar. The **nms:broadLogMid** schemat läggs till i listan som återställdes av föregående fråga.
1. The **Databasrensning** arbetsflödet tar sedan bort föråldrade data från tidigare återställda tabeller. Följande fråga används:

   ```sql
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   där `$(tableName)` är namnet på varje tabell i listan över scheman, och `$(option)` är det datum som är definierat för **NmsCleanup_BroadLogPurgeDelay** alternativ (se [Distributionsguide](#deployment-wizard)).

1. Slutligen kontrollerar arbetsflödet om **NmsProviderMsgId** tabellen finns. Om så är fallet tas alla föråldrade data bort med följande fråga:

   ```sql
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   där `$(option)` matchar datumet som definierats för **NmsCleanup_BroadLogPurgeDelay** alternativ (se [Distributionsguide](#deployment-wizard)).

### Rensa tabellen NmsEmailErrorStat {#cleanup-of-the-nmsemailerrorstat-table-}

Den här aktiviteten rensar **NmsEmailErrorStat** tabell. Huvudprogrammet (**coalesceErrors**) definierar två datum:

* **Startdatum**: datum för nästa process som matchar **NmsLastErrorStatCoalesce** eller det senaste datumet i tabellen.
* **Slutdatum**: aktuellt serverdatum.

Om startdatumet är senare än eller lika med slutdatumet utförs ingen process. I det här fallet **coalesceUpToDate** visas.

Om startdatumet är tidigare än slutdatumet visas **NmsEmailErrorStat** tabellen är rensad.

Det totala antalet fel i **NmsEmailErrorStat** tabellen, mellan start- och slutdatum, återställs med följande fråga:

```sql
SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)
```

där `$end` och `$start` är start- och slutdatum som definierats tidigare.

Om summan är större än 0:

1. Följande fråga utförs för att bara hålla fel utanför ett visst tröskelvärde (vilket är lika med 20):

   ```sql
   SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20
   ```

1. The **coalescingErrors** meddelandet visas.
1. En ny anslutning skapas för att ta bort alla fel som inträffade mellan start- och slutdatumet. Följande fråga används:

   ```sql
   DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)
   ```

1. Varje fel sparas i **NmsEmailErrorStat** tabell med följande fråga:

   ```sql
   INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))
   ```

   där varje variabel matchar ett värde som återställdes av föregående fråga.

1. The **start** variabeln uppdateras med värdena från föregående process för att slutföra slingan.

Slingan och aktivitetsstoppet.

Rensningar utförs på **NmsEmailError** och **cleanupNmsMxDomain** tabeller.

### Rensning av tabellen NmsEmailError {#cleanup-of-the-nmsemailerror-table-}

Följande fråga används:

```sql
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Frågan tar bort alla rader utan länkade poster i **NmsEmailErrorStat** från **NmsEmailError** tabell.

### Rensa NmsMxDomain-tabellen {#cleanup-of-the-nmsmxdomain-table-}

Följande fråga används:

```sql
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

Den här frågan tar bort alla rader utan en länkad post i **NmsEmailErrorStat** tabell från **NmsMxDomain** tabell.

### Rensa förslag {#cleanup-of-propositions}

Om **Interaktion** modulen är installerad, den här aktiviteten körs för att rensa **NmsPropositionXx** tabeller.

Listan med förslagstabeller återställs och massborttagning utförs för var och en av dem med hjälp av följande fråga:

```sql
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

där `$(option)` är det datum som är definierat för **NmsCleanup_PropositionPurgeDelay** alternativ (se [Distributionsguide](#deployment-wizard)).

### Rensa simuleringstabeller {#cleanup-of-simulation-tables}

Den här aktiviteten rensar överblivna simuleringstabeller (som inte längre är länkade till en erbjudandesimulering eller en leveranssimulering).

1. Följande fråga används för att återställa listan med simuleringar som behöver rensas:

   ```sql
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. Namnet på de tabeller som ska tas bort består av **wkSimu_** -prefix följt av simuleringens identifierare (till exempel: **wkSimu_456831_aggr**):

   ```sql
   DROP TABLE wkSimu_456831_aggr
   ```

### Rensa granskningsspår {#cleanup-of-audit-trail}

Följande fråga används:

```sql
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

där **$(tsDate)** är det aktuella serverdatumet från vilket perioden som definierats för **XtkCleanup_AuditTrailPurgeDelay** alternativet subtraheras.

### Rensa Nmsaddress {#cleanup-of-nmsaddress}

Följande fråga används:

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

Den här frågan tar bort alla poster som är relaterade till iOS och Android.

### Statistikuppdatering och lagringsoptimering {#statistics-update}

The **XtkCleanup_NoStats** kan du styra hur lagringsoptimeringssteget i rensningsarbetsflödet fungerar.

Om **XtkCleanup_NoStats** finns inte eller om värdet är 0 körs lagringsoptimeringen i utförligt läge (VACUUM VERBOSE ANALYZE) på PostgreSQL och uppdateringsstatistik för alla andra databaser. Kontrollera PostgreSQL-loggarna för att se till att kommandot körs. VACUUM kommer att visa rader i formatet: `INFO: vacuuming "public.nmsactivecontact"` och ANALYZE kommer att visa rader i formatet: `INFO: analyzing "public.nmsactivecontact"`.

Om värdet för alternativet är 1 utförs ingen statistikuppdatering i någon databas. Följande loggrad visas i arbetsflödesloggarna: `Option 'XtkCleanup_NoStats' is set to '1'`.

Om värdet för alternativet är 2 körs lagringsanalysen i detaljerat läge (ANALYZE VERBOSE) på PostgreSQL och statistik uppdateras för alla andra databaser. Kontrollera PostgreSQL-loggarna för att se till att kommandot körs. ANALYZE kommer att visa rader i formatet: `INFO: analyzing "public.nmsactivecontact"`.

### Rensning av prenumeration (NMAC) {#subscription-cleanup--nmac-}

Den här uppgiften tar bort alla prenumerationer som rör borttagna tjänster eller mobilprogram.

Följande fråga används för att återställa listan med sändningsscheman:

```sql
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

Uppgiften återställer sedan namnen på de tabeller som är länkade till **appSubscription** länkar och tar bort dessa tabeller.

Det här rensningsarbetsflödet tar också bort alla poster där det är inaktiverat = 1 som inte har uppdaterats sedan den tid som angetts i **NmsCleanup_AppSubscriptionRcpPurgeDelay** alternativ.

### Rensar sessionsinformation {#cleansing-session-information}

Den här aktiviteten tar bort information från **sessionInfo** tabellen används följande fråga:

```sql
DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### Rensar utgångna händelser {#cleansing-expired-events}

Den här aktiviteten rensar de händelser som tas emot och lagras på körningsinstanserna och de händelser som arkiveras på en kontrollinstans.

### Rensningsreaktioner {#cleansing-reactions}

Den här aktiviteten rensar reaktionerna (tabell) **NmsRemaMatchRcp**) där hypoteserna i sig har tagits bort.
