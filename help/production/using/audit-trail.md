---
product: campaign
title: Granskningskedja
description: Lär dig övervaka instansen med granskningsspår för Campaign
feature: Audit Trail, Monitoring, Workflows
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: 3d1ed85dcafc5afc4088db98c09d78fb7e9c0a39
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 2%

---

# Granskningskedja{#audit-trail}

>[!INFO]
>
>Läs mer om funktionen Granskningsspår i [Adobe Campaign v8-dokumentationen](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/analytics/audit-trail).

I Adobe Campaign ger **[!UICONTROL Audit trail]** dig tillgång till den fullständiga historiken över ändringar som gjorts i din instans.

**[!UICONTROL Audit trail]** samlar i realtid in en omfattande lista över åtgärder och händelser som inträffar i din Adobe Campaign-instans. Det innehåller ett självbetjäningssätt för att få tillgång till en historik med data som kan hjälpa dig att besvara frågor som: vad som hände med dina arbetsflöden och vem som senast uppdaterade dem eller vad som gjorde användarna i instansen.

>[!NOTE]
>
>Adobe Campaign granskar inte ändringar som gjorts i användarrättigheter, mallar, personalisering eller kampanjer.\
>Granskningsspårning kan bara hanteras av administratörer för instansen.

![](assets/audit_trail_2.png)

+++ Läs mer om tillgängliga enheter för granskningsspår

* **Schemagranskningsspår**: Du kan utforska de ändringar som gjorts i dina scheman samt identifiera vem som gjort ändringarna och när de gjordes.

  Mer information om scheman finns på [sidan](../../configuration/using/data-schemas.md).

* **Arbetsflödets granskningsspår** spårar alla åtgärder som är relaterade till dina arbetsflöden, inklusive:

   * Starta
   * Pausa
   * Stoppa
   * Starta om
   * Rensning som motsvarar åtgärden Rensa historik
   * Simulera vilket motsvarar åtgärden Starta i simuleringsläge
   * Aktivering som är lika med åtgärden Kör väntande uppgifter nu
   * Ovillkorligt stopp

  Mer information om arbetsflöden finns på [sidan](../../workflow/using/about-workflows.md).

  Mer information om hur du övervakar arbetsflöden finns i det [dedikerade avsnittet](../../workflow/using/monitoring-workflow-execution.md).

* Med **Alternativ granskningsspår** kan du kontrollera aktiviteter och senaste ändringar som du har gjort i alternativen.

  Mer information om alternativ finns på [sidan](../../installation/using/configuring-campaign-options.md).

* **Leveransverifieringskedja** gör att du kan kontrollera aktiviteter och senaste ändringar som du har gjort i leveranserna.

  Mer information om leveranser finns på [sidan](../../delivery/using/communication-channels.md).

* Med **externt konto** kan du kontrollera ändringar som gjorts i externa konton, som används av tekniska processer som tekniska arbetsflöden eller kampanjarbetsflöden.

  Mer information om externt konto finns på [sidan](../../installation/using/external-accounts.md).

* Med **Leveransmappning** kan du övervaka aktiviteter och nyligen gjorda ändringar i dina leveransmappningar.

  Mer information om leveransmappning finns på [sidan](../../configuration/using/target-mapping.md).

* Med **Webbprogram** kan du kontrollera ändringar som gjorts i webbformulär i Campaign V8 som används för att skapa sidor med indata- och urvalsfält, och som kan innehålla data från databasen.

  Mer information om webbprogram finns på [sidan](../../web/using/about-web-applications.md).

* Med **Erbjudandet** kan du kontrollera aktiviteter och senaste ändringar av dina erbjudanden.

  Mer information om erbjudandet finns på [sidan](../../interaction/using/interaction-and-offer-management.md).

* Med **Operator** kan du övervaka aktiviteter och nyligen gjorda ändringar i operatorerna.

  Mer information om operatorer finns på [sidan](../../platform/using/access-management-operators.md).

+++
