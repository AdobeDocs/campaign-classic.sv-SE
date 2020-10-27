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
translation-type: tm+mt
source-git-commit: d15e953740b0a4dd8073b36fd59b4c4e44906340
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 1%

---


# Om Adobe Experience Cloud-utlösare{#about-adobe-experience-triggers}

[!DNL Triggers] är en integrering mellan Adobe Campaign och Adobe Analytics. Pipelinen hämtar användarens åtgärder eller utlösare från din webbplats. En kundvagnsöverläggning är ett exempel på utlösare. Utlösare bearbetas i Adobe Campaign för att skicka e-post i nära realtid.

[!DNL Triggers] köra marknadsföringsåtgärder inom ett kort tidsintervall efter en användares åtgärd. Den typiska svarstiden är mindre än en timme.

Det ger smidigare integrering eftersom konfigurationen är minimal och en tredje part inte berörs.
Det stöder också stora trafikvolymer utan att påverka marknadsföringsaktiviteternas resultat. Integrationen kan till exempel behandla en miljon utlösare per timme.

## [!DNL Triggers] arkitektur {#triggers-architecture}

Processen [!DNL pipelined] körs alltid på Adobe Campaign marknadsföringsserver. Den ansluter till pipeline, hämtar händelserna och bearbetar dem direkt.

![](assets/triggers_2.png)

Processen loggar in på Experience Cloud med hjälp av en autentiseringstjänst och skickar en privat nyckel. [!DNL pipelined] Autentiseringstjänsten returnerar en token. Token används för att autentisera vid hämtning av händelser.

For more information on authentication, refer to this [page](../../integrations/using/configuring-adobe-io.md).

>[!NOTE]
>
>Ytterligare bearbetning av händelser görs som en del av ACX-paketet som tillhandahålls utanför standardimplementeringen. Mottagna händelser bearbetas omedelbart med JavaScript-kod. Den sparas i en databastabell utan vidare bearbetning i realtid. Utlösarna används för målgruppsanpassning av ett kampanjarbetsflöde som skickar e-postmeddelanden. Kampanjen har konfigurerats så att den kund som har utlöst händelsen får ett e-postmeddelande.
