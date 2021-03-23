---
solution: Campaign Classic
product: campaign
title: Leveransbarhet i Campaign
description: Lär dig god praxis vad gäller leverans
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 0420de856d1506ab92d8f0e0824bf439e0ac7dc7
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 5%

---


# Vad är leveransbarhet{#about-deliverability}?

Leveransmöjligheterna gör att ni kan mäta framgången för era kampanjer som når mottagarnas inkorgar utan att studsa, eller markeras som skräppost. [Läs varför levererbarhet är viktigt](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters).

Mer exakt är att e-postleverans är en uppsättning egenskaper som avgör hur ett meddelande kan nå sin destination, via en personlig e-postadress, inom en kort tid och med den förväntade kvaliteten i fråga om innehåll och format.

Mer information om leveransvillkor och leveranssätt finns i [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html).

## Så här förbättrar du leveransen {#deliverability-key-points}

Leveransproblem är vanligtvis kopplade till skyddsåtgärder mot skräppost som implementeras av Internetleverantörer och e-postserveradministratörer.

* Allmänna rekommendationer om hur du utformar lyckade e-postmarknadsföringskampanjer finns i [Leveransstrategi och definition](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html).

* Adobe rekommenderar att du använder de bästa metoderna som listas i det här avsnittet för mer specifika rekommendationer om hur du ska optimera leveransen av dina Adobe Campaign-e-postmeddelanden.

>[!NOTE]
>
>Eftersom internetleverantörer ständigt måste utveckla nya sofistikerade filtreringstekniker för att skydda sina kunder mot skräppost kännetecknas e-postleveransen av ständigt föränderliga kriterier och regler. Se till att du läser [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html) som uppdateras regelbundet.

### Leveransgrad

Leveransgraden är antalet meddelanden som når mottagarnas inkorgar jämfört med antalet meddelanden som levererats. Om du vill förbättra leveransmöjligheterna kan du arbeta med att öka den här hastigheten.

Med Adobe Campaign beror leveransgraden på många faktorer, bland annat:

* Korrekt konfiguration av dina instanser: kontakta din Adobe-representant för att få hjälp.
* Legitimal nätverkskonfiguration: se [det här avsnittet](../../delivery/using/optimize-delivery.md#network-config) och [Domänkonfiguration och -strategi](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy).
* Din IP-adress: se [IP-strategi](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy).
* Kvaliteten på adresserna: se [Karantänhantering](../../delivery/using/optimize-delivery.md#quarantine-management).
* Låga [antal klagomål](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) och [antal studsar](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces).
* Ditt meddelandeinnehåll: se [Kontrollera e-postinnehåll](../../delivery/using/control-message-content.md).
* Meddelandeautentisering (SPF, DKIM, DMARC): se [det här avsnittet](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).
* Avsändarens rykte: Om du vill veta mer om hur viktiga Internet-leverantörer utvärderar ett avsändarrykte kan du läsa [det här avsnittet](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html).

## Verktyg för kampanjleverans {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign har flera verktyg för att spåra och förbättra plattformens leveransförmåga. På den här sidan beskrivs också de huvudprinciper du bör tänka på för att optimera slutprodukten när du använder Campaign.

### Bygg ditt meddelande noggrant

När du konfigurerar, utformar och testar ett meddelande måste du följa de riktlinjer som beskrivs i avsnitten nedan. Genom att utnyttja alla funktioner i Adobe Campaign kan ni förbättra leveransen.

* [Bästa praxis för leverans](../../delivery/using/delivery-best-practices.md)
* [Kontrollera e-postinnehåll](../../delivery/using/control-message-content.md)
* [Inkorgsåtergivning](../../delivery/using/inbox-rendering.md)
* [Skicka en korrektur](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)

### Verifiera samtycke via dubbel anmälan {#double-opt-in}

För att undvika att skicka meddelanden till ogiltiga adresser, begränsa felaktig kommunikation och förbättra avsändarens anseende rekommenderar Adobe att du använder en mekanism för dubbel anmälan. Med den här metoden kan du säkerställa att mottagarna prenumererar avsiktligt.

Mer information finns i [Skapa ett prenumerationsformulär med dubbel anmälan](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).

Mer information om de bästa sätten att samla in data från dina kunder finns i [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene).

### Hantering av bruttokarantän

Adobe Campaign hanterar en lista som samlar in skräppostklagomål, hårda studsar och mjuka studsar som visas på ett enhetligt sätt.

För att skydda leveransen utesluts de mottagare vars adresser finns med i listan som standard från alla framtida leveranser, eftersom det kan skada ditt sändningsanseende om du skickar till dessa kontakter.

Vissa internetleverantörer betraktar automatisk e-post som skräppost om antalet ogiltiga adresser är för högt.  Med karantän kan du därför undvika att läggas till i blockeringslista av dessa leverantörer.

Mer information finns i följande avsnitt:

* [Förstå leveransfel](../../delivery/using/understanding-delivery-failures.md)
* [Förstå karantänhantering](../../delivery/using/understanding-quarantine-management.md)
* [Karantän mot blockeringslista](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)

### Använd övervaknings- och rapporteringsverktyg

Använd Adobe Campaign funktioner för att övervaka leveransen.

Med Adobe Campaign kan ni kontrollera hur era leveranser fungerar med hjälp av en uppsättning inbyggda realtidsindikatorer och rapporter för att få bättre insikt i era leveranser.

Mer information finns i följande avsnitt:

* [Övervaka levererbarhet](../../delivery/using/monitoring-deliverability.md)
* [Om leveransövervakning](../../delivery/using/about-delivery-monitoring.md)
* [Om inbyggda rapporter i Campaign](../../reporting/using/about-campaign-built-in-reports.md)

<!--TO REMOVE
## Background {#background}

Email deliverability presents a major challenge to marketers - whether they're sending a few thousand messages or several billion. One in five messages never reach the inbox, or their intended recipient.

Once relegated as a "technical issue" for the IT department, email deliverability continues to move higher on the marketing agenda. That's because savvy marketers recognize that although many of its elements are technical in nature, deliverability is ultimately a business issue with significant revenue implications.

Consider the email marketing funnel. Deliverability determines the number of messages received, which in turn impacts each subsequent stage of the funnel. Fewer emails received results in fewer opens, fewer clicks, and fewer conversions. **For companies with a large database, the difference between average and great deliverability could literally mean hundreds of thousands to millions of dollars in revenues.**

![](assets/deliverability_overview_1.png)

By settling for average (80%) deliverability, marketers are leaving significant conversions - and dollars - on the table.

What exactly is email deliverability? And how can marketers improve deliverability rates to widen the mouth of the funnel and squeeze more results from their email campaigns?

Email deliverability refers to the set of characteristics that determine a message's ability to reach its destination, via a personal e-mail address, within a short time, and with the expected quality in terms of content and format. These characteristics fall into four main categories: data quality, message and content, sending infrastructure, and reputation. Together, they form the foundation of a successful email deliverability program. This overview outlines the four fundamentals of email deliverability success and offers best practices for reaching the inbox and driving greater revenues from email marketing programs.

![](assets/deliverability_overview_2.png)-->
