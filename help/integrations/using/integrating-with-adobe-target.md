---
title: Integrera med Adobe Target
seo-title: Integrera med Adobe Target
description: Integrera med Adobe Target
seo-description: null
page-status-flag: never-activated
uuid: de482b31-0b7b-4669-8a00-28da48c6c5a9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: 44c7acdd-6b7a-4e88-b2a7-3e9bf8a6eab5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c3737b22c7bf4e614c5a2fbe8e8fd954d3ece8a
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---


# Integrera med Adobe Target{#integrating-with-adobe-target}

Integrationen mellan Adobe Campaign och Adobe Target (Classic och Standard) i Adobe Experience Cloud gör att du kan inkludera ett erbjudande från Adobe Target i en e-postleverans från Adobe Campaign.

Följande princip gäller: När en mottagare öppnar ett e-postmeddelande som skickas via Adobe Campaign kan du med ett anrop till Adobe Target visa en dynamisk version av innehållet. Den här dynamiska versionen beräknas utifrån de regler som anges i förväg när e-postmeddelandet skapas.

Läs mer om integrationen mellan Adobe Campaign och Adobe Target och [dessa fyra tips och trick](https://www.adobe.com/content/dam/www/us/en/marketing/campaign/pdfs/Adobe_Campaign_for_Target_Tips_and_Tricks.pdf).
>[!NOTE]
>
>Integreringen stöder bara statiska bilder. Resten av innehållet kan inte personaliseras.

Flera typer av data kan användas av Adobe Target:

* Data från datamart i Adobe Campaign
* Segment länkade till besökar-ID i Adobe Target, om de data som används inte omfattas av juridiska begränsningar
* Adobe Target data: användaragent, IP-adress, geolokaliseringsdata

>[!NOTE]
>
>Du hittar även information om integrationen mellan Adobe Campaign och Adobe Target på hjälpsidorna [för](https://docs.adobe.com/content/help/en/target/using/integrate/campaign-and-target.html)Adobe Target.
