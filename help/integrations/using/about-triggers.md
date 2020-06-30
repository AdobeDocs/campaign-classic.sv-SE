---
title: Om Adobe Experience Manager
seo-title: Om Adobe Experience Manager
description: Om Adobe Experience Manager
seo-description: null
page-status-flag: never-activated
uuid: c523822f-8178-4989-bd88-ab402470e540
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 0d617f1c-0d0b-489f-9027-a92b1f1eee37
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 39d6da007d69f81da959660b24b56ba2558a97ba
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---


# Om Adobe Experience Cloud-utlösare{#about-adobe-experience-triggers}

[!DNL Triggers] är en integrering mellan Adobe Campaign och Adobe Analytics via pipeline. Pipelinen hämtar användarens åtgärder eller utlösare från din webbplats. En kundvagnsöverläggning är ett exempel på utlösare. Utlösare bearbetas i Adobe Campaign för att skicka e-post i nära realtid.

[!DNL Triggers] köra marknadsföringsåtgärder inom ett kort tidsintervall efter en användares åtgärd. Den typiska svarstiden är mindre än en timme.

Det ger smidigare integrering eftersom konfigurationen är minimal och en tredje part inte berörs.
Det stöder också stora trafikvolymer utan att påverka marknadsföringsaktiviteternas resultat. Integrationen kan till exempel behandla en miljon utlösare per timme.

## [!DNL Triggers] arkitektur {#triggers-architecture}

### Vad är Pipeline? {#pipeline-explanation}

>[!CAUTION]
>
>Endast Adobe Cloud-lösningar kan producera och förbruka evenemang från Adobes Pipeline-tjänster. System som är externa än Adobe kan inte göra det.

Pipeline är ett meddelandesystem på Experience Cloud som använder [Apache Kafka](http://kafka.apache.org/). Det är ett sätt att enkelt skicka data mellan olika lösningar. Dessutom är Pipeline en meddelandekö i stället för en databas. Producenterna pushar på händelser i pipeline och konsumenterna lyssnar på flödet och gör vad de vill med händelsen. Händelser sparas i några dagar, men inte längre. Syftet är att avlyssna händelser dygnet runt och bearbeta dem direkt.

![](assets/triggers_1.png)

### Hur fungerar Pipeline? {#how-pipeline-work}

Processen&quot;rörlig&quot; körs alltid på marknadsföringsservern i Adobe Campaign. Den ansluter till pipeline, hämtar händelserna och bearbetar dem direkt.

![](assets/triggers_2.png)

Processen som skickas till Experience Cloud loggas in med en autentiseringstjänst och en privat nyckel skickas. Autentiseringstjänsten returnerar en token. Token används för att autentisera vid hämtning av händelser. [!DNL Triggers] hämtas från en REST-webbtjänst med hjälp av en enkel GET-begäran. Svaret är JSON-format. Parametrar för begäran innehåller namnet på utlösaren och en pekare som anger det senaste meddelandet som har hämtats. Den rörliga processen hanterar den automatiskt.

## Integrering med Adobe Experience Cloud Triggers med Adobe Campaign Classic

Här följer några [!DNL Triggers] tips:

* Data måste lagras [!DNL Trigger] som de kommer i Campaign. Den ska inte behandlas direkt eftersom den skulle skapa latens.
* Tidsstämpeln ska kontrolleras från meddelandet och inte från databasen.
* Använd TriggerTimestamp och trigger ID för att ta bort dubbletter.

>[!CAUTION]
>
>Exemplet nedan är inte tillgängligt. Detta är ett specifikt exempel från olika möjliga implementeringar.

Pipeline-händelserna laddas ned automatiskt. Dessa händelser kan övervakas med hjälp av ett formulär.

![](assets/triggers_3.png)

Pipeline Event-noden är inte inbyggd och måste läggas till, liksom det relaterade formuläret måste skapas i Campaign. De här åtgärderna är begränsade till expertanvändare. Mer information finns i följande avsnitt: [Navigeringshierarki](../../configuration/using/about-navigation-hierarchy.md) och [formulärredigering](../../configuration/using/editing-forms.md).

Ett återkommande kampanjarbetsflöde frågar efter utlösare och om de matchar marknadsföringskriterierna startar det en leverans.

![](assets/triggers_4.png)
