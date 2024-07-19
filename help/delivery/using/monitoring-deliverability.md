---
product: campaign
title: Skärmleverans i Adobe Campaign
description: Läs om verktyg och riktlinjer för övervakning av slutprodukter i Adobe Campaign
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Deliverability
role: User, Admin
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 1%

---

# Övervaka leveransen{#monitoring-deliverability}

Nedan hittar du information om de olika övervakningsverktygen i Adobe Campaign samt ytterligare riktlinjer för hur du utnyttjar de funktioner som Adobe Campaign erbjuder för att övervaka din plattforms leveransbarhet.

## Kontroll av levererbarhet {#about-deliverability-monitoring}

Den här funktionen är tillgänglig via ett dedikerat paket i Adobe Campaign. Paketet måste vara installerat för att du ska kunna använda det. När du är klar startar du om servern så att paketet kan användas.
* För värdbaserade klienter och hybridklienter konfigureras **Leveransövervakning** på din instans av Adobe tekniska support och konsulter. Kontakta din kontoansvarige på Adobe om du vill ha mer information.

* För lokala installationer måste du installera paketet **[!UICONTROL Deliverability monitoring (Email Deliverability)]** via menyn **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**. Mer information finns i [Installera Campaign Classicens standardpaket](../../installation/using/installing-campaign-standard-packages.md).

I Adobe Campaign Classic hanteras **Leveransövervakning** av arbetsflödet **[!UICONTROL Refresh for deliverability]**. Det installeras som standard på alla instanser och gör att du kan initiera listan över regler för studsmeddelanden, domänlistan och listan över MX:er. När paketet **[!UICONTROL Deliverability monitoring (Email Deliverability)]** har installerats körs det här arbetsflödet natt för att regelbundet uppdatera listan över regler och göra det möjligt att aktivt hantera plattformsleveransen.

Leveranspaketet ger dig tillgång till:

* Återgivningsrapporten [Inkorgen](inbox-rendering.md) som gör att du kan förhandsgranska meddelanden på större e-postklienter för att kunna skanna innehåll och anseende.
* Översikt över meddelandekvalitet (inkorg, skräppost).

## Övervakningsverktyg {#monitoring-tools}

Du kan även använda följande verktyg:

* Rapporten **[!UICONTROL Delivery throughput]** ger dig en översikt över hela plattformens dataflöde under en viss period. Mer information finns i [det här avsnittet](../../reporting/using/global-reports.md#delivery-throughput).
* Varje leverans genererar en utsändningsstatistikrapport för olika internetleverantörer. Den visar vissa data- och anseendemått som kan påverka leveransförmågan, inklusive följande tal:
   * **[!UICONTROL Hard bounces]** anger datakvalitet. Talet ska vara mindre än 2%.
   * **[!UICONTROL Soft bounces]** anger rykte. Talet får inte vara högre än 10 % för någon ISP.

  Mer information finns i avsnittet [Leveransstatistik](../../reporting/using/global-reports.md#delivery-statistics).
* Mer generellt ger [kontrollpanelen för leverans](about-delivery-monitoring.md) dig tillgång till:
   * [leveranssammanfattningen](delivery-dashboard.md#delivery-summary), som visar detaljerna för avsändande och antalet meddelanden som ska skickas, bearbetas och skickas.
   * [leveransloggar och historik](delivery-dashboard.md#delivery-logs-and-history), som visar vilket mål som har uteslutits och varför,
   * [spårningsloggar](delivery-dashboard.md#tracking-logs) som visar spårningsinformation som öppningar och klick.

## Riktlinjer för övervakning {#monitoring-guidelines}

Här följer ytterligare riktlinjer för leveransövervakning:

* Kontrollera regelbundet [leveransdataflödet](../../reporting/using/global-reports.md#delivery-throughput) för hela plattformen för att kontrollera om den stämmer överens med den ursprungliga konfigurationen.
* Kontrollera att [återförsök](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) har konfigurerats korrekt (30 minuter för återförsöksperiod och mer än 20 återförsök) i leveransmallar.
* Kontrollera regelbundet att postlådan [bounce](understanding-delivery-failures.md#bounce-mail-management) är tillgänglig och att kontot inte håller på att förfalla.
* Kontrollera varje leveransflöde, som du kommer åt från [leveransinstrumentpanelen](delivery-dashboard.md), för att se till att det stämmer överens med leveransinnehållets giltighet (t.ex. ska &#39;flash sales&#39; levereras på några minuter, inte dagar).
* När du använder [vågor](steps-sending-the-delivery.md#sending-using-multiple-waves) bör du kontrollera att varje våg har tillräckligt med tid för att slutföra innan nästa utlöses.
* Kontrollera att antalet fel och nya [karantäner](understanding-quarantine-management.md) stämmer överens med andra leveranser.
* Läs noggrant igenom [leveransloggarna](delivery-dashboard.md#delivery-logs-and-history) för att kontrollera vilken typ av fel som markeras (blockeringslista, DNS-problem, skräppostregler osv.).
