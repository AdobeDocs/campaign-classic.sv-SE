---
product: campaign
title: Om Adobe Experience Cloud-utlösare
description: Kom igång med Adobe Experience Cloud Triggers implementering
feature: Triggers
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 271e0f9fde0cbfb016e201c8390b26673d8fc696
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 7%

---

# Arbeta med utlösare för Campaign och Experience Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] är en integrering mellan Adobe Campaign och Adobe Analytics. Pipelinen hämtar användarens åtgärder eller utlösare från din webbplats. En kundvagnsöverläggning är ett exempel på utlösare. Utlösare bearbetas i Adobe Campaign för att skicka e-post i nära realtid.

>[!CAUTION]
>
>Den här funktionen är inte tillgänglig som en del av produkten. För den här implementeringen kan du samarbeta med din Adobe-representant/kundtjänst. Du kan sedan följa de steg som beskrivs här [page](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] köra marknadsföringsåtgärder inom ett kort tidsintervall efter en användares åtgärd. Den typiska svarstiden är mindre än en timme.

Det ger smidigare integrering eftersom konfigurationen är minimal och en tredje part inte berörs.
Det stöder också stora trafikvolymer utan att påverka marknadsföringsaktiviteternas resultat. Integrationen kan till exempel behandla en miljon utlösare per timme.

![](assets/do-not-localize/book.png) Upptäck hur man [skapa en Experience Cloud-utlösare](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html) och identifiera, definiera och övervaka viktiga konsumentbeteenden.

## [!DNL Triggers] arkitektur {#triggers-architecture}

The [!DNL pipelined] körs alltid på Adobe Campaign marknadsföringsserver. Den ansluter till pipeline, hämtar händelserna och bearbetar dem direkt.

![](assets/triggers_2.png)

The [!DNL pipelined] loggar in på Experience Cloud med en autentiseringstjänst och skickar en privat nyckel. Autentiseringstjänsten returnerar en token. Token används för att autentisera vid hämtning av händelser.

Mer information om autentisering finns i [page](../../integrations/using/configuring-adobe-io.md).
