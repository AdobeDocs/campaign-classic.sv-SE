---
solution: Campaign Classic
product: campaign
title: Övervaka leveransen i Adobe Campaign Classic
description: Läs om verktyg och riktlinjer för leveransövervakning i Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 2%

---


# Övervaka levererbarhet{#monitoring-deliverability}

Nedan finns information om de olika övervakningsverktygen i Adobe Campaign samt ytterligare riktlinjer för leveransövervakning.

## Övervakningsverktyg {#monitoring-tools}

Använd de funktioner som Adobe Campaign erbjuder för att övervaka plattformens leveransbarhet.

Leveranspaketet ger dig tillgång till:

* Teknisk spårningsrapport för den dagliga leveransen (teknisk övervakning). Med den här rapporten, som är tillgänglig på begäran, kan du få en daglig rapport via e-post till en angiven adress. Mer information får du om du kontaktar Adobe kundtjänst.
* Återgivningsrapporten [för](../../delivery/using/inbox-rendering.md) Inkorgen som gör att du kan förhandsgranska meddelanden på större e-postklienter för att skanna innehåll och anseende.
* Översikt över meddelandekvalitet (inkorg, skräppost).

Du kan även använda följande verktyg:

* Rapporten innehåller en översikt över hela plattformens dataflöde under en viss period. **[!UICONTROL Delivery throughput]** Mer information finns i [det här avsnittet](../../reporting/using/global-reports.md#delivery-throughput).
* Rapporten **[!UICONTROL Technical deliverability monitoring]** innehåller ett antal kvalitetsindikatorer för er plattform. Mer information finns i [det här avsnittet](#technical-deliverability-monitoring).
* Varje leverans genererar en utsändningsstatistikrapport för olika internetleverantörer. Den visar vissa data- och anseendemått som kan påverka leveransförmågan, inklusive följande tal:
   * **[!UICONTROL Hard bounces]** ange datakvalitet. Talet ska vara mindre än 2%.
   * **[!UICONTROL Soft bounces]** ange anseende. Talet får inte vara högre än 10 % för någon ISP.

   For more on this, see the [Delivery statistics](../../reporting/using/global-reports.md#delivery-statistics) section.
* Mer generellt ger [kontrollpanelen](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard) dig tillgång till:
   * En sammanfattning [av](../../delivery/using/monitoring-a-delivery.md#delivery-summary)leveransen, som visar hur detaljerad sändningen är och [hur många meddelanden](../../delivery/using/monitoring-a-delivery.md#number-of-messages-sent) som ska skickas, behandlas och skickas utan fel.
   * Leveransloggar och [leveranshistorik](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history), som visar vilket mål som har uteslutits och varför.
   * loggarna [för](../../delivery/using/monitoring-a-delivery.md#tracking-logs)spårning, som visar spårningsinformation som öppningar och klick.

## Riktlinjer för övervakning {#monitoring-guidelines}

Här följer ytterligare riktlinjer för leveransövervakning:

* Kontrollera regelbundet [leveransflödet](../../reporting/using/global-reports.md#delivery-throughput) för hela plattformen för att kontrollera om den överensstämmer med den ursprungliga konfigurationen.
* Kontrollera att [återförsök](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) är korrekt inställda (30 minuter för återförsöksperiod och mer än 20 återförsök) i leveransmallar.
* Kontrollera regelbundet att [studspostlådan](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management) är tillgänglig och att kontot inte håller på att förfalla.
* Kontrollera varje leveransflöde för att säkerställa att det stämmer överens med leveransinnehållets giltighet (t.ex. &quot;flash sales&quot; ska levereras på några minuter, inte dagar).
* När du använder [vågor](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)bör du kontrollera att varje våg har tillräckligt med tid för att slutföra innan nästa våg aktiveras.
* Kontrollera att antalet fel och nya [karantän](../../delivery/using/understanding-quarantine-management.md) stämmer överens med andra leveranser.
* Läs noggrant igenom [leveransloggarna](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history) för att kontrollera vilka typer av fel som markeras (blockeringslista, DNS-problem, antispam-regler osv.).

## Signalspam {#signal-spam}

Signal Spam är en fransk tjänst som erbjuder anonymiserad rapportering av feedback-slingor för franska internetleverantörer (Orange, SFR).

* Med den här tjänsten kan ni följa de franska internetleverantörernas rykte och följa kundens aktivitetsutveckling.

* Signal Spam ger också direkta klagomål som slutanvändarna loggar via ett dedikerat gränssnitt. Dessa klagomål sätts sedan i karantän från e-postadressdatabasen.

## 250ok {#deliverability-250ok}

[250ok](https://250ok.com/) är en kompletterande övervakningslösning för de interna verktygen för Adobe-leverans som tillhandahåller IP- och domänbaserade blockeringslista samt anseendeindikatorer.

Den information som tillhandahålls är i realtid, vilket möjliggör en proaktiv hjälp.

## Övervakningsrapport för teknisk leverans {#technical-deliverability-monitoring}

Den tekniska leveransövervakningsrapporten uppdateras dagligen och är tillgänglig genom att gå till **[!UICONTROL Monitoring]** > **[!UICONTROL Overview]** och klicka på **[!UICONTROL Technical monitoring]** länken på fliken Adobe Campaign **[!UICONTROL Home]** . Det innehåller ett antal kvalitetsindikatorer för er plattform.

Dessa indikatorer uppdateras dagligen kl. 9.00.

>[!NOTE]
>
>Dessutom kan du få en daglig rapport via e-post till en angiven adress. Informera oss om den begärda e-postadressen via e-post eller via Adobe Campaign Extranet.

![](assets/s_tn_del_monitoring.png)

Följande indikatorer används i rapporten:

* **[!UICONTROL Reverse DNS]** : Adobe Campaign kontrollerar om en omvänd DNS anges för en IP-adress och att detta korrekt pekar tillbaka till IP-adressen.

* **[!UICONTROL SPF]** (Sender Policy Framework): En autentiseringsmekanism som gör det möjligt för Internet-leverantörer och postlådeleverantörer att kontrollera om e-postavsändaren är auktoriserad på den sändande domänen.

* **[!UICONTROL DomainKeys]** : En tjänst som utvecklats av Yahoo och som är avsedd att certifiera identiteten för en e-postavsändare.

* **[!UICONTROL IP and RBL domain]** (Blackutjämlista i realtid): En lista över IP-adresser och domäner som flaggats av organisationer i blockeringslista för dåligt sändande rykte. Listorna hanteras av särskilda organisationer som Spamhaus, Spampolis, SURBL/URIBL osv. Adobe Campaign bearbetar för närvarande kontroller mot RBL:er som har en betydande påverkan på leveransen. Dessa URL:er återspeglar avsändarens anseende och kan refereras av Internet-leverantörer innan de godkänner att få dina e-postmeddelanden.

* **[!UICONTROL SNDS]** (Data Services för smarta nätverk): En [Windows Live Hotmail-tjänst mot skräppost](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx). Hotmail är den enda Internet-leverantör som tillhandahåller den här typen av information. Benchmark-poängen är ett grönt filterresultat, en klagofrekvens på mindre än 0,1 % och noll skräppostsvällningar.

<!--### Delivery Reports - Broadcast Statistics {#broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability.-->
