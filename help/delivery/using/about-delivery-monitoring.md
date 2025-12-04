---
product: campaign
title: Kom igång med leveransövervakning
description: Läs mer om Campaign Classic funktioner för leveransövervakning
feature: Monitoring, Deliverability
role: User
exl-id: 9ce11da0-e37b-459e-8ec7-d2bddf59bdf7
source-git-commit: e60a8391416bc9899548971bddb61705467a80e5
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 1%

---

# Kom igång med leveransövervakning {#about-delivery-monitoring}

>[!IMPORTANT]
>
>Den här sidan innehåller **Campaign Classic v7-specifika övervakningsfunktioner** för hybriddistributioner och lokala distributioner.

## Övervakningsfunktioner

### Leveransövervakning {#monitoring-deliveries}

**För hybriddistributioner/lokala distributioner av Campaign Classic v7** krävs ytterligare övervakning för serverresurser och MTA-konfiguration (Mail Transfer Agent).

#### Felsöka väntande leveranser {#pending-deliveries}

Vad händer om leveranserna inte skickas och deras status förblir **Väntande**?

* Körningsprocessen väntar på att vissa resurser ska vara tillgängliga. MTA har kanske inte startats.
Kontrollera att mta@instance startas på dina MTA-servrar och starta MTA-modulen om det behövs. [Läs mer](../../production/using/administration.md).

* Leveransen kan ha en tillhörighet som inte har konfigurerats på den sändande instansen.
Tips: Kontrollera konfigurationen för trafikhantering (IP-tillhörighet). Mer information finns i Kontrollera utgående SMTP-trafik.

>[!NOTE]
>
>Dessa steg kan bara utföras av en expertanvändare på lokala installationer.

### Leveransövervakning {#deliverability-monitoring}

#### Installation av leveranspaket {#deliverability-package}

Den här funktionen är tillgänglig via ett dedikerat paket i Adobe Campaign. Paketet måste vara installerat för att du ska kunna använda det. När du är klar startar du om servern så att paketet kan användas.

* För värdbaserade klienter och hybridklienter konfigureras **Leveransövervakning** på din instans av Adobe tekniska support och konsulter. Kontakta er kontoansvarige på Adobe om du vill ha mer information.

* För lokala installationer måste du installera paketet **[!UICONTROL Deliverability monitoring (Email Deliverability)]** via menyn **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**. Mer information finns i [Installera Campaign Classic standardpaket](../../installation/using/installing-campaign-standard-packages.md).

#### Arbetsflöde för slutprodukter {#deliverability-workflow}

I Adobe Campaign Classic hanteras **Leveransövervakning** av arbetsflödet **[!UICONTROL Refresh for deliverability]**. Det installeras som standard på alla instanser och gör att du kan initiera listan över regler för studsmeddelanden, domänlistan och listan över MX:er. När paketet **[!UICONTROL Deliverability monitoring (Email Deliverability)]** har installerats körs det här arbetsflödet natt för att regelbundet uppdatera listan över regler och göra det möjligt att aktivt hantera plattformsleveransen.

**Leveranspaketet ger dig åtkomst till:**

* Återgivningsrapporten [Inkorgen](inbox-rendering.md) som gör att du kan förhandsgranska meddelanden på större e-postklienter för att kunna skanna innehåll och anseende.
* Översikt över meddelandekvalitet (inkorg, skräppost).

#### Övervakningsverktyg {#monitoring-tools}

**För lokala installationer** kan du använda följande övervakningsverktyg:

* Rapporten **[!UICONTROL Delivery throughput]** ger dig en översikt över hela plattformens dataflöde under en viss period. Mer information finns i [det här avsnittet](../../reporting/using/global-reports.md#delivery-throughput).
* Varje leverans genererar en utsändningsstatistikrapport för olika internetleverantörer. Den visar vissa data- och anseendemått som kan påverka leveransförmågan, inklusive följande tal:
   * **[!UICONTROL Hard bounces]** anger datakvalitet. Talet ska vara mindre än 2%.
   * **[!UICONTROL Soft bounces]** anger rykte. Talet får inte vara högre än 10 % för någon ISP.

  Mer information finns i avsnittet [Leveransstatistik](../../reporting/using/global-reports.md#delivery-statistics).

#### Riktlinjer för övervakning {#monitoring-guidelines}

**För lokala installationer** finns det ytterligare riktlinjer för leveransövervakning:

* Kontrollera regelbundet [leveransdataflödet](../../reporting/using/global-reports.md#delivery-throughput) för hela plattformen för att kontrollera om den stämmer överens med den ursprungliga konfigurationen.
* Kontrollera att [återförsök](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) har konfigurerats korrekt (30 minuter för återförsöksperiod och mer än 20 återförsök) i leveransmallar.
* Kontrollera regelbundet att postlådan [bounce](understanding-delivery-failures.md#bounce-mail-management) är tillgänglig och att kontot inte håller på att förfalla.
* Kontrollera varje leveransflöde, som du kommer åt från [leveransinstrumentpanelen](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}, för att se till att det stämmer överens med leveransinnehållets giltighet (t.ex. ska &#39;flash sales&#39; levereras på några minuter, inte dagar).
* När du använder vågor måste du kontrollera att varje våg har tillräckligt med tid för att slutföra innan nästa våg aktiveras.
* Kontrollera att antalet fel och nya [karantäner](understanding-quarantine-management.md) stämmer överens med andra leveranser.
* Läs noggrant igenom [leveransloggarna](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/send/monitor/delivery-dashboard#delivery-logs-and-history){target="_blank"} för att kontrollera vilken typ av fel som markeras (blockeringslista, DNS-problem, skräppostregler osv.).

### Felsökning {#delivery-troubleshooting}

Specifika åtgärder kan utföras när problem påträffas med leveranser i **hybriddistributioner/lokala distributioner**:

* [Leveransproblem](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Bildvisningsproblem](../../production/using/image-display-issues.md)
* [Problem med leveransresultat](delivery-performance-troubleshooting.md)
* [Tillfälliga filer ger ut](../../production/using/temporary-files.md) - *endast lokala kunder*

## Övervaka leveranser

Följande resurser hjälper dig att övervaka och spåra leveransresultatet i Campaign Classic v7:

### Åtkomst till kontrollpanelen för leverans

Lär dig hur du får åtkomst till leveranslistor och använder kontrollpanelen för leverans för att övervaka din sändningsaktivitet:

* [Skärmleveranser i Campaign-gränssnittet](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (dokumentationen för Campaign v8 gäller både v7 och v8)
* [Leveransstatus](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (dokumentation för kampanj v8)
* [Avancerat: Anpassa leveransloggar](customize-delivery-logs.md) (endast hybrid v7/lokal - schemautökning)

### Spåra meddelandeinteraktioner

Spåra öppningar, klick och mottagarnas interaktioner med dina leveranser:

* [Dokumentation för meddelandespårning](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"} (Campaign v8-dokumentation - gäller både v7 och v8)
* [Konfigurera spårade länkar](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"} (Campaign v8-dokumentation)
* [Åtkomstspårningsloggar](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"} (dokumentation för Campaign v8)

### Optimera leveransresultatet

Bästa praxis och felsökning för leveransproblem:

* [Bästa tillvägagångssätt vid leverans](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (dokumentation för Campaign v8 - gäller både v7 och v8)
* [Leveransprestanda och felsökning](delivery-performance-troubleshooting.md) (v7-hybrid/lokal specifik konfiguration)

### Förstå misslyckanden och karantän

Hantera leveransfel, studentmejl och adresser i karantän:

* [Om leveransfel](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (dokumentation för Campaign v8 - utförlig guide för både v7 och v8)
* [Karantänhantering](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (Campaign v8-dokumentation - omfattande guide för både v7 och v8)
* [Leveransfel och karantänkonfiguration](delivery-failures-quarantine.md) (v7-hybridkonfigurationer/lokala specifika konfigurationer)
