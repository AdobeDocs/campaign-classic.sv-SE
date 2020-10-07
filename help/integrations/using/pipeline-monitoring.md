---
title: Konfigurera integreringen
seo-title: Konfigurera integreringen
description: Konfigurera integreringen
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 2%

---


# Övervaka pipelines {#pipeline-monitoring}

Statuswebbtjänsten ger [!DNL pipelined] information om [!DNL pipelined] processens status.

Den kan nås manuellt via en webbläsare eller automatiskt med ett övervakningsprogram.

Det är i REST-format, vilket beskrivs nedan.

![](assets/triggers_8.png)

## Indikatorer {#indicators}

I det här avsnittet visas indikatorerna i statuswebbtjänsten.

Rekommenderade indikatorer för övervakning markeras.

* Konsument: namnet på klienten som drar i utlösarna. Konfigureras i pipeline-alternativet.
* http-request
   * last-alive-ms-ago: tiden i ms sedan en anslutningskontroll gjordes.
   * last-failed-cnx-ms-ago: tiden i ms sedan senaste gången som anslutningskontrollen misslyckades.
   * pipeline-host: namnet på den värd från vilken pipelinedata hämtas.
* pekare
   * aktuell-förskjutning: pekarens värde i pipeline, per underordnad tråd.
   * last-flush-ms-ago: tid i ms sedan en grupp utlösare hämtades.
   * next-offsets-flush: tid att vänta till nästa batch, när den är klar.
   * bearbetad-sedan-senaste-flush: antal utlösare som bearbetats i den senaste batchen.
* routning
   * utlösare: lista över utlösare som hämtats. Konfigureras i [!DNL pipelined] alternativet.
* status
   * Average-pointer-flush-time-ms: genomsnittlig bearbetningstid för en grupp utlösare.
   * Average-trigger-processing-time-ms: Genomsnittlig tid för tolkning av utlösardata.
   * bytes-read: antal byte som har lästs från kön sedan processen startades.
   * aktuella meddelanden: aktuellt antal väntande meddelanden som har hämtats från kön och väntar på bearbetning. **Den här indikatorn ska vara nära noll**.
   * aktuella försök: aktuellt antal meddelanden som inte har kunnat bearbetas och som väntar på nytt försök.
   * toppmeddelanden: maximalt antal väntande meddelanden som processen har hanterat sedan den startades.
   * pekartömningar: Antal meddelandebatchar som har bearbetats sedan starten.
   * routing-JS-custom: antal meddelanden som har bearbetats av den anpassade JS-servern.
   * utlösare ignorerad: antal meddelanden som har ignorerats efter för många återförsök på grund av bearbetningsfel.
   * triggerbearbetad: antal meddelanden som har bearbetats utan fel.
   * trigger-receive: antal meddelanden som tagits emot från kön.

Dessa statusvärden visas per processtråd.

* Average-trigger-processing-time-ms: Genomsnittlig tid för tolkning av utlösardata.
* is-JS-processor: värdet &quot;1&quot; om den här tråden använder den anpassade JS:en.
* utlösare ignorerad: antal meddelanden som har ignorerats efter för många återförsök på grund av bearbetningsfel. **Den här indikatorn ska vara noll**.
* utlösare-fel: antal bearbetningsfel i JS. **Den här indikatorn ska vara noll**.
* trigger-receive: antal meddelanden som tagits emot från kön.

* Inställningar: de anges i konfigurationsfilerna.
   * flush-pointer-msg-count: antal meddelanden i en batch.
   * flush-pointer-period-ms: tiden mellan två batchar, i millisekunder.
   * processing-threads-JS: antal bearbetningstrådar som kör den anpassade JS-servern.
   * retry-period-ms: tiden mellan två försök när ett bearbetningsfel inträffar.
   * retry-validity-duration-ms: längden från den tidpunkt då bearbetningen görs om tills meddelandet ignoreras.
   * Rapport över försäljningsförloppsmeddelanden

## Rapport över försäljningsförloppsmeddelanden {#pipeline-report}

Den här rapporten visar antalet meddelanden per timme under de senaste fem dagarna.

![](assets/triggers_9.png)
