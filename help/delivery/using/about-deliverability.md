---
product: campaign
title: Kom igång med leverans i Campaign
description: Lär dig god praxis vad gäller leverans
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Deliverability
role: User
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 7%

---

# Vad är levererbarhet?{#about-deliverability}

Leveransmöjligheterna gör att ni kan mäta framgången för era kampanjer som når mottagarnas inkorgar utan att studsa, eller markeras som skräppost. [Läs varför leveranssäkerhet är viktigt](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters).

Mer exakt är att e-postleverans avser den uppsättning egenskaper som avgör hur ett meddelande kan nå sin destination, via en personlig e-postadress, inom en kort tid och med den förväntade kvaliteten i fråga om innehåll och format.

En djupdykning i vad som är möjligt och mer information om termer, begrepp och metoder för leverans finns i [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv).

## Hur man förbättrar leveransen {#deliverability-key-points}

Leveransproblem är vanligtvis kopplade till skyddsåtgärder mot skräppost som implementeras av Internetleverantörer och e-postserveradministratörer.

* Allmänna rekommendationer om hur du utformar framgångsrika e-postmarknadsföringskampanjer finns i [Leveransstrategi och definition](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html).

* Adobe rekommenderar att du använder de bästa metoderna som listas i det här avsnittet för mer specifika rekommendationer om hur du ska optimera leveransen av dina Adobe Campaign-e-postmeddelanden.

>[!NOTE]
>
>Eftersom internetleverantörer ständigt måste utveckla nya sofistikerade filtreringstekniker för att skydda sina kunder mot skräppost kännetecknas e-postleveransen av ständigt föränderliga kriterier och regler. Se till att du refererar till [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv) som uppdateras regelbundet.

### Leveransgrad

Leveransgraden är antalet meddelanden som når mottagarnas inkorgar jämfört med antalet meddelanden som levererats. Om du vill förbättra leveransmöjligheterna kan du arbeta med att öka den här hastigheten.

Med Adobe Campaign beror leveransgraden på många faktorer, bland annat:

* Korrekt konfiguration av dina instanser: kontakta din Adobe-representant för att få hjälp.
* Legitimerad nätverkskonfiguration: se [det här avsnittet](optimize-delivery.md#network-config) och [Domäninställningar och -strategi](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy).
* Din IP-adress är känd: se [IP-strategi](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy).
* Kvaliteten på adresserna: se [Karantänhantering](optimize-delivery.md#quarantine-management).
* Låg [klagomål](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) och [hård studsa](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces) räntenivåer.
* Ditt meddelandeinnehåll: se [Styr e-postinnehållet](control-message-content.md).
* Meddelandeautentisering (SPF, DKIM, DMARC): se [det här avsnittet](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).
* Avsändarens rykte: om du vill veta hur de viktigaste internetleverantörerna utvärderar ett avsändarens rykte kan du läsa [det här avsnittet](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html).

## Verktyg för kampanjleverans {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign har flera verktyg för att spåra och förbättra plattformens leveransförmåga. På den här sidan beskrivs också de huvudprinciper du bör tänka på för att optimera slutprodukten när du använder Campaign.

### Bygg ditt meddelande noggrant

När du konfigurerar, utformar och testar ett meddelande måste du följa de riktlinjer som beskrivs i avsnitten nedan. Genom att utnyttja alla funktioner i Adobe Campaign kan ni förbättra leveransen.

* [God praxis för leverans](delivery-best-practices.md)
* [Styr e-postinnehållet](control-message-content.md)
* [Inkorgsåtergivning](inbox-rendering.md)
* [Skicka ett bevis](steps-validating-the-delivery.md#sending-a-proof)

### Verifiera samtycke genom dubbel anmälan {#double-opt-in}

För att undvika att skicka meddelanden till ogiltiga adresser, begränsa felaktig kommunikation och förbättra avsändarens anseende rekommenderar Adobe att du använder en mekanism för dubbel anmälan. Med den här metoden kan du säkerställa att mottagarna prenumererar avsiktligt.

Mer information om det här finns i [Skapa ett prenumerationsformulär med dubbel anmälan](../../web/using/use-cases-web-forms.md#create-a-subscription--form-with-double-opt-in).

Mer information om de bästa metoderna för att samla in data från kunderna finns i [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene).

### Hantering av bruttokarantän

Adobe Campaign hanterar en lista som samlar in skräppostklagomål, hårda studsar och mjuka studsar som visas på ett enhetligt sätt.

För att skydda leveransen utesluts de mottagare vars adresser finns med i listan som standard från alla framtida leveranser, eftersom det kan skada ditt sändningsanseende om du skickar till dessa kontakter.

Vissa internetleverantörer betraktar automatisk e-post som skräppost om antalet ogiltiga adresser är för högt.  Med karantän kan du därför undvika att läggas till i blockeringslista av dessa leverantörer.

Mer information finns i följande avsnitt:

* [Förstå leveransfel](understanding-delivery-failures.md)
* [Förstå karantänhantering](understanding-quarantine-management.md)
* [Karantän mot blockeringslista](understanding-quarantine-management.md#quarantine-vs-denylist)

### Använd övervaknings- och rapporteringsverktyg

Använd de funktioner som Adobe Campaign erbjuder för att övervaka leveransen.

Med Adobe Campaign kan ni kontrollera hur era leveranser fungerar med hjälp av en uppsättning inbyggda realtidsindikatorer och rapporter för att få bättre insikt i era leveranser.

Mer information finns i följande avsnitt:

* [Skärmleverans](monitoring-deliverability.md)
* [Kom igång med leveransövervakning](about-delivery-monitoring.md)
* [Kom igång med inbyggda rapporter för Campaign](../../reporting/using/about-campaign-built-in-reports.md)
