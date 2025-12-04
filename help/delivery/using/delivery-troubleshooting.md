---
product: campaign
title: Felsökning av leverans
description: Lär dig mer om leveransresultat och hur du felsöker problem med leveransövervakning
feature: Monitoring, Deliverability, Troubleshooting
role: User
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 1%

---

# Felsökning av leverans {#delivery-troubleshooting}

>[!NOTE]
>
>Omfattande vägledning om felsökning av leveranser finns i dokumentationen för Campaign v8, som gäller både Campaign Classic v7- och Campaign v8-användare:
>
>* Vanliga leveransfel och lösningar: [Om leveransfel](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* Långsam leveransdiagnos: [Övervaka leveranser i Campaign-gränssnittet](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* Bästa tillvägagångssätt vid leverans: [Bästa tillvägagångssätt vid leverans](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>Den här sidan innehåller **Campaign Classic v7-specifik felsökning** för hybriddistributioner och anläggningsdistributioner.

## Felsökning {#v7-specific}

Följande felsökningssteg gäller för hybriddistributioner **Campaign Classic v7/lokala distributioner** för den infrastruktur du hanterar:

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
>För användare av hanterade molntjänster i Campaign v8 hanteras tekniska arbetsflöden och infrastrukturövervakning av Adobe. Fokusera på leveransinnehåll och målinriktning enligt beskrivningen i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Relaterade ämnen

* [Om leveransfel](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (dokumentation för Campaign v8)
* [Bästa praxis för leverans](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (dokumentation för Campaign v8)
* [Övervaka leveranser i Campaign-gränssnittet](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (Campaign v8-dokumentation)
* [Databasunderhåll](../../production/using/recommendations.md) (v7-hybridinstallation/lokalt)
* [E-postleverans](../../installation/using/email-deliverability.md) (v7-hybrid/lokal)
