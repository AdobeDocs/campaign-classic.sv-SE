---
title: Tabeller att underhålla
seo-title: Tabeller att underhålla
description: Tabeller att underhålla
seo-description: null
page-status-flag: never-activated
uuid: 1085e929-65cc-48fa-9c31-0508a14b4704
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 6ec4e566-7116-4d7f-835d-cb0f3c3a6a7a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Tabeller att underhålla{#tables-to-maintain}

Listan med tabeller som ska behållas beror på vilken version av Adobe Campaign du har, hur du använder den och på datamodellens konfiguration.

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
   <th> <strong>Kommentarer</strong><br /> </th> 
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
   <td> Det här är systemets största tabell. Det finns en post per skickat meddelande och dessa poster infogas, uppdateras för att spåra leveransstatus och tas bort när historiken rensas. <br /> </td> 
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
   <td> Det här är systemets största tabell. Det finns en post per skickat meddelande och dessa poster infogas, uppdateras för att spåra leveransstatus och tas bort när historiken rensas. Observera att i 5.10 är den här tabellen mindre än motsvarigheten i 4.05 (NmsBroadLog) eftersom SMTP-meddelandetexten är faktoriserad i tabellen NmsBroadLogMsg i version 5.10. Det är dock fortfarande viktigt att indexera om den här tabellen regelbundet (varannan vecka att börja med) och helt återskapa den då och då (en gång i månaden eller när prestanda påverkas). <br /> </td> 
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

Förutom listan ovan kan tabeller som skapas av kunder (som inte finns i datamodellen för Adobe Campaign) under plattformskonfigurationen också fragmenteras, särskilt om de uppdateras ofta under datainläsning eller synkronisering. Dessa tabeller kan ingå i Adobe Campaigns standarddatamodell (till exempel **NmsRecipient**). I det här fallet är det administratören av Adobe Campaign-plattformen som måste göra en revision av sin specifika databasmodell för att kunna hitta dessa anpassade tabeller. Dessa tabeller nämns inte nödvändigtvis uttryckligen i våra underhållsprocedurer.
