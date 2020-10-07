---
title: Dela målgrupper med Adobe Experience Cloud
seo-title: Dela målgrupper med Adobe Experience Cloud
description: Dela målgrupper med Adobe Experience Cloud
seo-description: null
page-status-flag: never-activated
uuid: 24ac3463-69ab-48b4-85e0-4fe1948bf5ed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 8f295058-5a78-4512-9bdf-d5f022457e10
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---


# Sharing audiences with Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!NOTE]
>
>IMS måste vara implementerat för att den här integreringen ska kunna användas. Läs avsnittet om [IMS](../../integrations/using/about-adobe-id.md).

Med Adobe Campaign kan ni utbyta och dela målgrupper/segment med Adobe Experience Cloud lösningar och bastjänster. För att göra detta måste du integrera **Adobe Campaign** med **People core service** (kallas även **Profiles &amp; Audiences core service**) eller Adobe Audience Manager. Då kan du:

* Importera delade målgrupper/segment från olika Adobe Experience Cloud-lösningar till Adobe Campaign. Publiker kan importeras via listor i Adobe Campaign.
* Exportera listor i form av Adobe Experience Cloud delade målgrupper. Dessa målgrupper kan användas i de olika Adobe Experience Cloud-lösningar ni använder. Målgrupper kan exporteras efter målgruppsanpassning i ett arbetsflöde med hjälp av en dedikerad **[!UICONTROL Update shared audience]** aktivitet.

>[!CAUTION]
>
>Beroende på vilken typ av data det rör sig om kan det vara tillåtet att importera målgrupper i Adobe Campaign.

Integreringen stöder två typer av Adobe Experience Cloud ID:

* **Besökar-ID**: den här typen av identifierare används för att anpassa Adobe Experience Cloud-besökare till Adobe Campaign-mottagare.
* **Deklarerat ID**: den här typen av identifierare kan stämma av alla typer av data med element från Adobe Campaign-databasen. Den representeras i Adobe Campaign som en fördefinierad avstämningsnyckel.
