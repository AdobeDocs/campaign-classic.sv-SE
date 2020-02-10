---
title: Leveranser
seo-title: Leveranser
description: Leveranser
seo-description: null
page-status-flag: never-activated
uuid: d323eb4d-937b-4b37-8400-942336f0a1b4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 37612f62-68c0-4f73-a9a1-6d017aab862f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# Leveranser{#deliveries}

Arbetsflödena som anges nedan installeras som standard.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Rapportera aggregat</span><br /> </td> 
   <td> <span class="uicontrol">reportingAggregates</span><br /> </td> 
   <td> Det här arbetsflödet uppdaterar aggregat som används i rapporter. Den aktiveras varje dag klockan 2 som standard.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Fakturering</span><br /> </td> 
   <td> <span class="uicontrol">fakturering</span><br /> </td> 
   <td> Det här arbetsflödet skickar systemaktivitetsrapporten till faktureringsoperatorn via e-post. Den utlöses som standard den 25:e varje månad.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Antal aktiva faktureringsprofiler</span><br /> </td> 
   <td> <span class="uicontrol">fakturingActiveContactCount</span><br /> </td> 
   <td> <p>Det här arbetsflödet räknar antalet aktiva profiler. Den utlöses varje natt klockan 1:00 som standard.</p> <p>"<strong>profil</strong>" innebär ett register över information (t.ex.: en post i nmsRecipient-tabellen eller en extern tabell som innehåller ett cookie-ID, Kund-ID, mobilidentifierare eller annan information som är relevant för en viss kanal) som representerar en slutkund, potentiell kund eller lead. Fakturering gäller endast profiler som är "aktiva". En profil betraktas som"aktiv" om profilen har delats eller kommunicerats via någon kanal under de senaste tolv månaderna.</p> <p>Facebook- och Twitter-kanaler beaktas inte.</p> <p>Du kan få en översikt över <span class="uicontrol">Antal aktiva profiler</span> via menyn <span class="uicontrol">Administration</span> &gt; <span class="uicontrol">Kampanjhantering</span> &gt; <span class="uicontrol">Kundstatistik</span> .</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Rensa</span> alias <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span><br /> </td> 
   <td> Det här arbetsflödet standardiserar uppräkningsvärden. Den aktiveras varje dag klockan tre som standard.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Uppdatering för leveransbarhet</span><br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span><br /> </td> 
   <td> Med det här arbetsflödet kan du skapa en lista över regler för studsmeddelanden samt en lista över domäner och MX:er på plattformen. Det här arbetsflödet fungerar bara om HTTPS-porten är öppen. De här listorna uppdateras inte om inte leveransmodulen är installerad.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Databasrensning</span><br /> </td> 
   <td> <span class="uicontrol">rensa</span><br /> </td> 
   <td> <p>Det här arbetsflödet är arbetsflödet för databasunderhåll: utför olika beräkningar från statistiken och processerna och tar bort föråldrade data från databasen enligt den definierade konfigurationen i distributionsassistenten. Den aktiveras varje dag klockan fyra som standard.</p> <p>Mer information finns på den här <a href="../../production/using/database-cleanup-workflow.md">sidan</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Rensa pausade arbetsflöden</span><br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span><br /> </td> 
   <td> <p>Det här arbetsflödet analyserar pausade arbetsflöden som har allvarlighetsgraden inställd på normal och utlöser varningar och meddelanden när de har pausats för länge. Efter en månad stoppas de pausade tekniska arbetsflödena ovillkorligt. Som standard utlöses den varje måndag kl. 5.</p> <p>Mer information finns i <a href="../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">Hantera pausade arbetsflöden</a>.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Meddelande</span> om erbjudande <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span><br /> </td> 
   <td> Det här arbetsflödet distribuerar godkända erbjudanden i onlinemiljön samt i alla kategorier i erbjudandekatalogen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Förhandsgranska</span><br /> </td> 
   <td> <span class="uicontrol">prognos</span><br /> </td> 
   <td> Det här arbetsflödet analyserar leveranser som sparats i den preliminära kalendern (skapar preliminära loggar). Den utlöses som standard varje dag klockan 1:00.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Spårning</span><br /> </td> 
   <td> <span class="uicontrol">spåra</span><br /> </td> 
   <td> Det här arbetsflödet utför återställning och konsolidering av spårningsinformation. Dessutom säkerställs omberäkningen av spårnings- och leveransstatistik, särskilt sådan som används i arbetsflöden för meddelandecentrets arkivering. Som standard aktiveras den en gång per timme. <br /> </td> 
  </tr> 
 </tbody> 
</table>

