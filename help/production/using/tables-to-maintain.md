---
product: campaign
title: Tabeller att underhålla
description: Tabeller att underhålla
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 1%

---

# Tabeller att underhålla{#tables-to-maintain}



Listan med tabeller som ska behållas beror på vilken version av Adobe Campaign du har, hur du använder den och på datamodellkonfigurationen.

Följande lista innehåller endast de tabeller som är mest fragmenterade. Effekterna är följande:

* överförbrukning av diskutrymme, vilket påverkar databasåtkomsten,
* index som inte har uppdaterats regelbundet, vilket försämrar frågeprestanda.

## Adobe Campaign-tabeller {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Tabellnamn </strong><br /> </th> 
   <th> <strong>Storlek</strong><br /> </th> 
   <th> <strong>Huvudtyp av verksamhet</strong><br /> </th> 
   <th> <strong>Kommentar</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> Liten<br /> </td> 
   <td> Uppdateringar<br /> </td> 
   <td> Det finns en post per leveransåtgärd. En enskild post kan uppdateras flera gånger för att återspegla leveransförloppet, så index i den här tabellen brukar fragmenteras snabbt. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> Medel<br /> </td> 
   <td> Infogningar, uppdateringar, borttagningar<br /> </td> 
   <td> Arbetsregister som poster infogas i under leveransförberedelsen. De uppdateras sedan under leveransen och tas slutligen bort när leveransen är klar.<br /> Tabellen brukar fragmenteras snabbt även om dess genomsnittliga storlek är ganska begränsad.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> Stor<br /> </td> 
   <td> Infogningar, borttagningar<br /> </td> 
   <td> Tabellen innehåller den information som behövs för att skapa anpassade spegelsidor. Den innehåller ett PM-fält (CLOB) som därför är mycket stort. Volymen står i direkt proportion till historiken för de spegelsidor som behålls. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> Medel<br /> </td> 
   <td> Infogningar, uppdateringar, borttagningar<br /> </td> 
   <td> Det här registret innehåller statistik om leveransprocessen. Dess register uppdateras regelbundet. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Medel<br /> </td> 
   <td> Uppdateringar, infogningar<br /> </td> 
   <td> Tabellen innehåller information om e-postadresser. Den uppdateras ofta som en del av karantänprocessen (poster skapas vid det första leveransfelet, uppdateras när räknarna ändras och tas bort när leveransen har slutförts). <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> Liten<br /> </td> 
   <td> Uppdateringar<br /> </td> 
   <td> Det finns en post per arbetsflödesinstans, så få poster. Tabellen uppdateras dock regelbundet för att återspegla status och framsteg.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> Liten<br /> </td> 
   <td> Infogningar, uppdateringar, borttagningar<br /> </td> 
   <td> Varje körning av en arbetsflödesaktivitet leder till att en post skapas i den här tabellen. Tömningsmekanismen tar bort dem när de har gått ut.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> Liten<br /> </td> 
   <td> Infogningar, uppdateringar, borttagningar<br /> </td> 
   <td> Varje övergång som aktiveras mellan uppgifter i ett arbetsflöde leder till att en post skapas i den här tabellen. Tömningsmekanismen tar bort dem när de har gått ut. <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> Mycket liten <br /> </td> 
   <td> Infogningar, uppdateringar, borttagningar<br /> </td> 
   <td> Det här registret är specifikt för arbetsflödesmotorn. Det gör det möjligt att skicka kommandon till arbetsflöden (till exempel Start, Stop, Pause). Även om den är liten beaktas den här tabellen när du tömmer transaktionsregister som är länkade till arbetsflöden.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> Störst<br /> </td> 
   <td> Infogningar, uppdateringar, borttagningar<br /> </td> 
   <td> Det här är den största tabellen i systemet. Det finns en post per skickat meddelande och dessa poster infogas, uppdateras för att spåra leveransstatus och tas bort när historiken rensas. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> Stor<br /> </td> 
   <td> Infogningar, borttagningar<br /> </td> 
   <td> Spårningsloggar infogas och tas bort när historiken rensas, men de uppdateras inte. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> Liten<br /> </td> 
   <td> Uppdateringar<br /> </td> 
   <td> Tabellen innehåller information som används för kvalificerande SMTP-fel. Den är ganska liten, men kommer att uppdateras enormt, så indexen i den här tabellen brukar fragmenteras snabbt. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> Medel<br /> </td> 
   <td> Infogningar, uppdateringar, borttagningar<br /> </td> 
   <td> Den här tabellen innehåller aggregaten för SMTP-fel sorterade efter domän. Den innehåller inledningsvis detaljerad information som sammanställs av rensningsaktiviteten när den blir inaktuell. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid (på en instans med mellanleverantörer)<br /> </td> 
   <td> Stor<br /> </td> 
   <td> Infogningar, uppdateringar, borttagningar<br /> </td> 
   <td> Endast när 5.10-instansen (eller senare) används som en mellankällsinstans. Detta är en av de största tabellerna i databasen. Det finns en post per skickat meddelande och dessa poster infogas, uppdateras för att spåra leveransstatus och tas bort när historiken rensas. När du använder mellanleverantörer rekommenderar vi att du begränsar historiken (vanligtvis mindre än två månader), så tabellen är rimlig i fråga om storlek (mindre än 30 Go för 60 miljoner rader, data+index), men det är mycket viktigt att bygga om den då och då. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp (när NmsRecipient-tabellen används) <br /> </td> 
   <td> Stor<br /> </td> 
   <td> Infogningar, uppdateringar, borttagningar<br /> </td> 
   <td> Det här är den största tabellen i systemet. Det finns en post per skickat meddelande och dessa poster infogas, uppdateras för att spåra leveransstatus och tas bort när historiken rensas. Observera att i 5.10 är den här tabellen mindre än motsvarigheten i 4.05 (NmsBroadLog) eftersom SMTP-meddelandetexten är faktoriserad i tabellen NmsBroadLogMsg i version 5.10. Det är dock fortfarande viktigt att indexera om den här tabellen regelbundet (varannan vecka att börja med) och helt återskapa den då och då (en gång i månaden eller när prestanda påverkas). <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXx (när en extern mottagartabell används)<br /> </td> 
   <td> Stor<br /> </td> 
   <td> Infogningar, uppdateringar, borttagningar<br /> </td> 
   <td> Samma som NmsBroadLogRcp men med en extern mottagartabell. Anpassa Yyy och Xxx med värdena i din leveranskarta. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp (när NmsRecipient-tabellen används) <br /> </td> 
   <td> Stor<br /> </td> 
   <td> Infogningar, borttagningar<br /> </td> 
   <td> Spårningsloggar infogas och tas bort när historiken rensas, men de uppdateras inte. Volymen beror på hur lång datalagringen är. <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXx (när den externa mottagartabellen används)<br /> </td> 
   <td> Stor<br /> </td> 
   <td> Infogningar, borttagningar<br /> </td> 
   <td> Samma som NmsTrackingLogRcp men med en extern mottagartabell. Anpassa Yyy och Xxx med de värden som används i din leveranskarta. <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent (körningsinstans i meddelandecenter)<br /> </td> 
   <td> Stor<br /> </td> 
   <td> Infogningar, uppdateringar, borttagningar<br /> </td> 
   <td> Liknar de andra sändningstabellerna, men med NmsRtEvent i stället för NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent( körningsinstans i meddelandecenter)<br /> </td> 
   <td> Stor<br /> </td> 
   <td> Infogningar, borttagningar<br /> </td> 
   <td> Liknar de andra trackingLog-tabellerna, men med NmsRtEvent-tabellen i stället för NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent (körningsinstans för Message Center)<br /> </td> 
   <td> Stor<br /> </td> 
   <td> Infogningar, uppdateringar, borttagningar<br /> </td> 
   <td> Tabell som innehåller händelsekön för meddelandecentret. Statusen för dessa händelser uppdateras av Message Center när de bearbetas. Borttagningar utförs under tömningen. Vi rekommenderar att du regelbundet återskapar indexet för den här tabellen och återskapar det.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHistory (kontrollinstansen Message Center)<br /> </td> 
   <td> Stor<br /> </td> 
   <td> Infogningar, uppdateringar, borttagningar<br /> </td> 
   <td> Liknar NmsRtEvent. Den här tabellen arkiverar alla händelser från alla körningsinstanser. Den används inte av någon realtidsprocess, utan endast av rapporter.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> Mycket liten<br /> </td> 
   <td> Infogningar, uppdateringar, borttagningar<br /> </td> 
   <td> Tabeller som innehåller mobilprogram och deras konfiguration.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> Stor<br /> </td> 
   <td> Infogningar, uppdateringar<br /> </td> 
   <td> Tabell som innehåller identifierare för mobila enheter (adresser) som används för att skicka meddelandet (liknar en mottagartabell).<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> Stor<br /> </td> 
   <td> Infogningar, uppdateringar, borttagningar<br /> </td> 
   <td> Liknar de andra sändningstabellerna, men med NmsappSubscriptionRcp i stället för NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> Stor<br /> </td> 
   <td> Infogningar, borttagningar<br /> </td> 
   <td> Liknar de andra trackingLog-tabellerna, men med tabellen NmsappSubscriptionRcp i stället för NmsRecipient.<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> Liten<br /> </td> 
   <td> Infogningar, borttagningar<br /> </td> 
   <td> Register som innehåller användarsessioner. Antalet infogningar och borttagningar är mycket viktigt.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Kundregister {#customer-tables}

Förutom listan ovan kan tabeller som skapas av kunder (som inte finns i Adobe Campaign datamodell) under plattformskonfiguration också fragmenteras, särskilt om de uppdateras ofta under datainläsning eller synkronisering. Dessa tabeller kan ingå i Adobe Campaign standarddatamodell (till exempel **NmsRecipient**). I det här fallet är det upp till administratören för Adobe Campaign-plattformen att utföra en revision av sin specifika databasmodell för att hitta dessa anpassade tabeller. Dessa tabeller nämns inte nödvändigtvis uttryckligen i våra underhållsprocedurer.
