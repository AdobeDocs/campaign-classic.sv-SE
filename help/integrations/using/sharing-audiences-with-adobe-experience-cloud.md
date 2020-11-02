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
source-git-commit: 4b98c23f4120cbea6dd54cd68b61202e74bee3e1
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# Sharing audiences with Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>För att kunna dela målgrupper med Adobe Experience Cloud lösningar måste ni implementera Adobe Identity Management System. [Läs mer om IMS](../../integrations/using/about-adobe-id.md).

Med Adobe Campaign kan ni dela målgrupper och segment med Adobe Experience Cloud lösningar och bastjänster. Det finns två alternativ:

1. Skicka Adobe Experience Platform segmentdata till Adobe Campaign. För att implementera den här integreringen måste ni koppla kunddataplattformen i realtid till Campaign (RTCDP). [Läs mer i det här avsnittet](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html).


1. Integrera **Adobe Campaign** med **People core service** (kallas även **Profiles &amp; Audiences core service**) eller Adobe Audience Manager. Då kan du:

   * Importera delade målgrupper/segment från olika Adobe Experience Cloud-lösningar till Adobe Campaign. Publiker kan importeras via listor i Adobe Campaign.

   * Exportera listor i form av Adobe Experience Cloud delade målgrupper. Dessa målgrupper kan användas i de olika Adobe Experience Cloud-lösningar ni använder. Målgrupper kan exporteras efter målgruppsanpassning i ett arbetsflöde med hjälp av en dedikerad **[!UICONTROL Update shared audience]** aktivitet.

Den här integreringen stöder två typer av Adobe Experience Cloud ID:

* **Besökar-ID**: den här typen av identifierare används för att anpassa Adobe Experience Cloud-besökare till Adobe Campaign-mottagare.
* **Deklarerat ID**: den här typen av identifierare kan stämma av alla typer av data med element från Adobe Campaign-databasen. Den representeras i Adobe Campaign som en fördefinierad avstämningsnyckel.
