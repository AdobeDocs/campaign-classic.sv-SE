---
product: campaign
title: Övervaka leveransen i Adobe Campaign Classic
description: Läs om verktyg och riktlinjer för leveransövervakning i Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 2%

---

# Övervaka levererbarhet{#monitoring-deliverability}

![](../../assets/common.svg)

Nedan hittar du information om de olika övervakningsverktygen i Adobe Campaign samt ytterligare riktlinjer för hur du utnyttjar de funktioner som Adobe Campaign erbjuder för att övervaka din plattforms leveransbarhet.

## Övervaka levererbarhet {#configuration}

Den här funktionen är tillgänglig via ett dedikerat paket i Adobe Campaign. Paketet måste vara installerat för att du ska kunna använda det. När du är klar startar du om servern så att paketet kan användas.
* För värdbaserade klienter och hybridklienter konfigureras **Leveransövervakning** av Adobe tekniska support och konsulter. Kontakta din kontoansvarige på Adobe om du vill ha mer information.

* För lokala installationer måste du installera **[!UICONTROL Deliverability monitoring (Email Deliverability)]**-paketet via **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**-menyn. Mer information finns i [Installera Campaign Classic-standardpaket](../../installation/using/installing-campaign-standard-packages.md).

I Adobe Campaign Classic hanteras **Leveransövervakning** av arbetsflödet **[!UICONTROL Refresh for deliverability]**. Det installeras som standard på alla instanser och gör att du kan initiera listan över regler för studsmeddelanden, domänlistan och listan över MX:er. När **[!UICONTROL Deliverability monitoring (Email Deliverability)]**-paketet har installerats körs det här arbetsflödet varje natt för att regelbundet uppdatera listan över regler och göra det möjligt att aktivt hantera plattformsleveransen.

Leveranspaketet ger dig tillgång till:

* Återgivningsrapporten [Inkorgen](inbox-rendering.md) som gör att du kan förhandsgranska meddelanden på större e-postklienter för att skanna innehåll och anseende.
* Översikt över meddelandekvalitet (inkorg, skräppost).

## Övervakningsverktyg {#monitoring-tools}

Du kan även använda följande verktyg:

* Rapporten **[!UICONTROL Delivery throughput]** ger dig en översikt över hela plattformens genomströmning under en viss period. Mer information finns i [det här avsnittet](../../reporting/using/global-reports.md#delivery-throughput).
* Varje leverans genererar en utsändningsstatistikrapport för olika internetleverantörer. Den visar vissa data- och anseendemått som kan påverka leveransförmågan, inklusive följande tal:
   * **[!UICONTROL Hard bounces]** ange datakvalitet. Talet ska vara mindre än 2%.
   * **[!UICONTROL Soft bounces]** ange anseende. Talet får inte vara högre än 10 % för någon ISP.

   Mer information finns i avsnittet [Leveransstatistik](../../reporting/using/global-reports.md#delivery-statistics).
* Mer generellt ger [kontrollpanelen](about-delivery-monitoring.md) åtkomst till:
   * [leveranssammanfattning](delivery-dashboard.md#delivery-summary), som visar hur detaljerad sändningen är och hur många meddelanden som ska skickas, bearbetas och skickas.
   * Leveransloggarna och historiken [som visar vilket mål som har uteslutits och varför.](delivery-dashboard.md#delivery-logs-and-history)
   * [spårningsloggar](delivery-dashboard.md#tracking-logs) som visar spårningsinformation som öppningar och klick.

## Riktlinjer för övervakning {#monitoring-guidelines}

Här följer ytterligare riktlinjer för leveransövervakning:

* Kontrollera regelbundet [leveransflödet](../../reporting/using/global-reports.md#delivery-throughput) för hela plattformen för att kontrollera om den stämmer överens med den ursprungliga konfigurationen.
* Kontrollera att [återförsök](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) är rätt inställda (30 minuter för återförsöksperiod och mer än 20 återförsök) i leveransmallar.
* Kontrollera regelbundet att postlådan [bounce](understanding-delivery-failures.md#bounce-mail-management) är tillgänglig och att kontot inte håller på att förfalla.
* Kontrollera varje leveransflöde som du når från [kontrollpanelen](delivery-dashboard.md) för att se till att det stämmer överens med leveransinnehållets giltighet (t.ex. &quot;flash sales&quot; ska levereras på några minuter, inte dagar).
* När du använder [vågor](steps-sending-the-delivery.md#sending-using-multiple-waves) måste du kontrollera att varje våg har tillräckligt med tid för att slutföra innan nästa våg aktiveras.
* Kontrollera att antalet fel och nya [karantäner](understanding-quarantine-management.md) stämmer överens med andra leveranser.
* Läs noga igenom [leveransloggarna](delivery-dashboard.md#delivery-logs-and-history) för att kontrollera vilken typ av fel som markeras (blockeringslista, DNS-problem, antispam-regler osv.).

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
