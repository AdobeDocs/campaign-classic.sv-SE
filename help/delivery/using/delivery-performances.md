---
product: campaign
title: Bästa praxis för leveransprestanda
description: Läs mer om leveransresultat och bästa praxis
feature: Deliverability
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 3%

---

# Bästa praxis för leveransprestanda {#delivery-performances}

>[!NOTE]
>
>Omfattande vägledning om leveransresultat och bästa praxis finns på sidan [Bästa praxis för kampanjleverans](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices). Det här innehållet gäller både Campaign Classic v7- och Campaign v8-användare.
>
>Den här sidan innehåller **Campaign Classic v7-specifika prestandakonfigurationer** för hybriddistributioner och lokala distributioner.

Mer information om god praxis för leveransresultat, plattformsoptimering, karantänhantering, databasunderhåll och rekommendationer för schemaläggning finns i [dokumentationen om leveransmetoder för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Prestandajustering {#best-practices-performance}

För **Campaign Classic v7-hybriddistributioner/lokala distributioner** kan följande databas- och infrastrukturoptimeringar förbättra leveransprestanda:

### Databasoptimering

**Indexadresser** för att optimera prestanda för SQL-frågor som används i programmet. Ett index kan deklareras från huvudelementet i dataschemat. Den här optimeringen kräver direkt databasåtkomst och schemaanpassning som är tillgänglig i lokala distributioner.

### Infrastrukturanpassning

**Konfiguration för stora leveranser**: För leveranser till över en miljon mottagare krävs utrymme i de sändande köerna. För lokala installationer kan underordnade MTA konfigureras för att hantera anpassade batchstorlekar. Kontakta systemadministratören för att justera inställningarna baserat på din infrastrukturkapacitet.

>[!NOTE]
>
>För användare av hanterade molntjänster i Campaign v8 hanteras infrastrukturoptimering och MTA-konfiguration av Adobe. Se [Bästa praxis för leverans av kampanjer v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} för prestandarekommendationer som gäller för din distribution.

## Databasunderhåll {#performance-issues}

För **hybriddistributioner/lokala distributioner av Campaign Classic v7** påverkar plattforms- och databasunderhåll leveransresultaten direkt.

Vanliga underhållsåtgärder är:

**Databasrensning**: Använd arbetsflödet för databasrensning för att ta bort gamla leveransloggar, spårningsdata och tillfälliga tabeller. Dåligt databasunderhåll kan göra det långsammare att förbereda och skicka leveranser.

**Övervakning av databasprestanda**: Övervaka frågeprestanda, indexfragmentering och tabellstatistik. Detaljerad vägledning finns på [den här sidan](../../production/using/database-performances.md).

**Övervakning av tekniskt arbetsflöde**: Kontrollera att alla tekniska arbetsflöden (särskilt arbetsflöden för rensning, spårning och leveransuppdatering) körs korrekt utan fel.

>[!NOTE]
>
>För användare av hanterade molntjänster i Campaign v8 övervakas och hanteras databasunderhåll och tekniska arbetsflöden av Adobe. Fokusera på leveransspecifik övervakning enligt beskrivningen i [dokumentationen för leveranser av Campaign v8-övervakare](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}.

## Relaterade ämnen

* [Bästa praxis för leverans](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (dokumentation för Campaign v8)
* [Övervaka leveransen](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"} (dokumentation för Campaign v8)
* [Leveransfelsökning](delivery-troubleshooting.md)
* [Databasprestanda](../../production/using/database-performances.md) (v7-hybrid/lokal)
