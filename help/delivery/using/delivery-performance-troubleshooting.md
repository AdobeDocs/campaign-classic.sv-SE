---
product: campaign
title: Leveransprestanda och felsökning
description: Lär dig hur du optimerar leveransprestanda och felsöker problem i Campaign Classic v7
feature: Monitoring, Deliverability, Troubleshooting
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# Leveransprestanda och felsökning {#delivery-performance-troubleshooting}

>[!NOTE]
>
>Omfattande vägledning om leveransresultat och bästa praxis finns på sidan [Bästa praxis för kampanjleverans](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices). Det här innehållet gäller både Campaign Classic v7- och Campaign v8-användare.
>
>Den här sidan innehåller **Campaign Classic v7-specifika konfigurationer** för prestandaoptimering och felsökning i hybriddistributioner och anläggningsdistributioner.

Mer information om god praxis för leveransresultat, plattformsoptimering, karantänhantering, databasunderhåll och rekommendationer för schemaläggning finns i [dokumentationen om leveransmetoder för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}.

## Prestandaoptimering {#performance-optimization}

För **hybriddistributioner/lokala distributioner av Campaign Classic v7** kan följande databas- och infrastrukturoptimeringar förbättra leveransprestanda.

### Databasoptimering

**Indexadresser** för att optimera prestanda för SQL-frågor som används i programmet. Ett index kan deklareras från huvudelementet i dataschemat. Den här optimeringen kräver direkt databasåtkomst och schemaanpassning som är tillgänglig i lokala distributioner.

### Infrastrukturanpassning

**Konfiguration för stora leveranser**: För leveranser till över en miljon mottagare krävs utrymme i de sändande köerna. För lokala installationer kan underordnade MTA konfigureras för att hantera anpassade batchstorlekar. Kontakta systemadministratören för att justera inställningarna baserat på din infrastrukturkapacitet.

>[!NOTE]
>
>För användare av hanterade molntjänster i Campaign v8 hanteras infrastrukturoptimering och MTA-konfiguration av Adobe. Se [Bästa praxis för leverans av kampanjer v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} för prestandarekommendationer som gäller för din distribution.

### Databasunderhåll {#database-maintenance}

För **hybriddistributioner/lokala distributioner av Campaign Classic v7** påverkar plattforms- och databasunderhåll leveransresultaten direkt.

Vanliga underhållsåtgärder är:

**Databasrensning**: Använd arbetsflödet för databasrensning för att ta bort gamla leveransloggar, spårningsdata och tillfälliga tabeller. Dåligt databasunderhåll kan göra det långsammare att förbereda och skicka leveranser.

**Övervakning av databasprestanda**: Övervaka frågeprestanda, indexfragmentering och tabellstatistik. Detaljerad vägledning finns på [den här sidan](../../production/using/database-performances.md).

**Övervakning av tekniskt arbetsflöde**: Kontrollera att alla tekniska arbetsflöden (särskilt arbetsflöden för rensning, spårning och leveransuppdatering) körs korrekt utan fel.

>[!NOTE]
>
>För användare av hanterade molntjänster i Campaign v8 övervakas och hanteras databasunderhåll och tekniska arbetsflöden av Adobe. Fokusera på leveransspecifik övervakning enligt beskrivningen i [dokumentationen för leveranser av Campaign v8-övervakare](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}.

## Felsökning av leveransproblem {#troubleshooting}

>[!NOTE]
>
>Omfattande vägledning om felsökning av leveranser finns i dokumentationen för Campaign v8, som gäller både Campaign Classic v7- och Campaign v8-användare:
>
>* Vanliga leveransfel och lösningar: [Om leveransfel](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Långsam leveransdiagnos: [Övervaka leveranser i Campaign-gränssnittet](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* Bästa tillvägagångssätt vid leverans: [Bästa tillvägagångssätt vid leverans](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>Det här avsnittet innehåller **Campaign Classic v7-specifik felsökning** för hybriddistributioner och anläggningsdistributioner.

Följande felsökningssteg gäller för hybriddistributioner **Campaign Classic v7** och för hybriddistributioner på plats.

### MX-regelkonfiguration

Om du får problem med strypning för specifika Internet-leverantörer kan du behöva granska och justera MX-regelkonfigurationen. Mer information om MX-regler och -kvoter finns i [det här avsnittet](../../installation/using/email-deliverability.md#about-mx-rules).

### Databasunderhåll för leveransprestanda

Om du får följande fel i medelstora installationer:

```
Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
```

Orsaken är kopplad till prestandaproblem där marknadsinstansen spenderar för mycket tid på att bygga upp data innan den skickas till servern med mellanlagring.

**För lokala installationer** utför du ett vakuum och indexerar om databasen. Mer information om databasunderhåll finns i [det här avsnittet](../../production/using/recommendations.md).

Du bör också starta om alla arbetsflöden med en schemalagd aktivitet och alla arbetsflöden med statusen misslyckades. Se [det här avsnittet](../../workflow/using/scheduler.md).

### Övervakning av tekniskt arbetsflöde

För lokala installationer ska du se till att alla tekniska arbetsflöden som rör slutbarhet körs utan fel:

**Arbetsflöde för leveransuppdatering**: Uppdaterar regler för avbrutna e-postkvalificeringar och leveransindikatorer.

**Spårningsarbetsflöde**: Bearbetar spårningsdata för skickade leveranser.

**Arbetsflöde för databasrensning**: Tar regelbundet bort gamla leveransloggar och tillfälliga tabeller för att upprätthålla prestanda.

Kontrollera arbetsflödesstatus i **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

>[!NOTE]
>
>För användare av hanterade molntjänster i Campaign v8 hanteras tekniska arbetsflöden och infrastrukturövervakning av Adobe. Fokusera på leveransinnehåll och målinriktning enligt beskrivningen i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Relaterade ämnen

* [Om leveransfel](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (dokumentation för Campaign v8)
* [Bästa praxis för leverans](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (dokumentation för Campaign v8)
* [Övervaka leveranser i Campaign-gränssnittet](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (Campaign v8-dokumentation)
* [Databasunderhåll](../../production/using/recommendations.md) (v7-hybridinstallation/lokalt)
* [E-postleverans](../../installation/using/email-deliverability.md) (v7-hybrid/lokal)
* [Databasprestanda](../../production/using/database-performances.md) (v7-hybrid/lokal)

