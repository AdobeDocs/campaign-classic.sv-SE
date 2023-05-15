---
product: campaign
title: Skärmleverans i Adobe Campaign
description: Läs om verktyg och riktlinjer för övervakning av slutprodukter i Adobe Campaign
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: e4caa316-242f-46cd-a20b-a5eee5a0c456
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 1%

---

# Övervaka leveransen{#monitoring-deliverability}



Nedan hittar du information om de olika övervakningsverktygen i Adobe Campaign samt ytterligare riktlinjer för hur du utnyttjar de funktioner som Adobe Campaign erbjuder för att övervaka din plattforms leveransbarhet.

## Kontroll av levererbarhet {#about-deliverability-monitoring}

Den här funktionen är tillgänglig via ett dedikerat paket i Adobe Campaign. Paketet måste vara installerat för att du ska kunna använda det. När du är klar startar du om servern så att paketet kan användas.
* För värdkunder och hybridkunder **Leveransövervakning** konfigureras av Adobe teknisk support och konsulter. Kontakta din kontoansvarige på Adobe om du vill ha mer information.

* För lokala installationer måste du installera **[!UICONTROL Deliverability monitoring (Email Deliverability)]** via **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** -menyn. Mer information finns i [Installera Campaign Classic-standardpaket](../../installation/using/installing-campaign-standard-packages.md).

I Adobe Campaign Classic **Leveransövervakning** hanteras av **[!UICONTROL Refresh for deliverability]** arbetsflöde. Det installeras som standard på alla instanser och gör att du kan initiera listan över regler för studsmeddelanden, domänlistan och listan över MX:er. När **[!UICONTROL Deliverability monitoring (Email Deliverability)]** paketet är installerat. Det här arbetsflödet körs regelbundet för att uppdatera listan över regler och gör att du kan hantera plattformsleverans aktivt.

Leveranspaketet ger dig tillgång till:

* The [Återgivningsrapport för inkorgen](inbox-rendering.md) som gör att du kan förhandsgranska meddelanden på större e-postklienter för att skanna innehåll och anseende.
* Översikt över meddelandekvalitet (inkorg, skräppost).

## Övervakningsverktyg {#monitoring-tools}

Du kan även använda följande verktyg:

* The **[!UICONTROL Delivery throughput]** rapporten ger en översikt över hela plattformens dataflöde under en viss period. Mer information finns i [det här avsnittet](../../reporting/using/global-reports.md#delivery-throughput).
* Varje leverans genererar en utsändningsstatistikrapport för olika internetleverantörer. Den visar vissa data- och anseendemått som kan påverka leveransförmågan, inklusive följande tal:
   * **[!UICONTROL Hard bounces]** ange datakvalitet. Talet ska vara mindre än 2%.
   * **[!UICONTROL Soft bounces]** ange anseende. Talet får inte vara högre än 10 % för någon ISP.

   Mer information finns i [Leveransstatistik](../../reporting/using/global-reports.md#delivery-statistics) -avsnitt.
* Mer generellt är [kontrollpanel för leverans](about-delivery-monitoring.md) ger dig tillgång till
   * den [leveranssammanfattning](delivery-dashboard.md#delivery-summary), som visar hur detaljerad sändningen är och hur många meddelanden som ska skickas, bearbetas och skickas.
   * den [leveransloggar och historik](delivery-dashboard.md#delivery-logs-and-history), som visar vilket mål som har uteslutits och varför.
   * den [spårningsloggar](delivery-dashboard.md#tracking-logs), som visar spårningsinformation som öppningar och klickningar.

## Riktlinjer för övervakning {#monitoring-guidelines}

Här följer ytterligare riktlinjer för leveransövervakning:

* Kontrollera regelbundet [leveransflöde](../../reporting/using/global-reports.md#delivery-throughput) för hela plattformen för att kontrollera om den är förenlig med den ursprungliga installationen.
* Kontrollera att [återförsök](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) är korrekt konfigurerade (30 minuter för återförsöksperiod och mer än 20 försök) i leveransmallar.
* Kontrollera regelbundet att [studsa](understanding-delivery-failures.md#bounce-mail-management) postlådan är tillgänglig och kontot håller inte på att förfalla.
* Kontrollera varje leveransflöde, som du kommer åt via [kontrollpanel för leverans](delivery-dashboard.md), för att säkerställa att det stämmer överens med leveransinnehållets giltighet (t.ex. &quot;flash sales&quot; ska levereras på några minuter, inte dagar).
* När du använder [vågor](steps-sending-the-delivery.md#sending-using-multiple-waves)kontrollerar du att varje våg har tillräckligt med tid att slutföra innan nästa utlöses.
* Kontrollera att antalet fel och nya [karantän](understanding-quarantine-management.md) överensstämmer med andra leveranser.
* Använd [leveransloggar](delivery-dashboard.md#delivery-logs-and-history) i detalj kontrollera vilken typ av fel som markeras (blockeringslista, DNS-problem, regler mot skräppost osv.).
