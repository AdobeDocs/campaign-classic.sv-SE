---
solution: Campaign Classic
product: campaign
title: Dela målgrupper med Adobe Experience Cloud
description: Dela målgrupper med Adobe Experience Cloud
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '239'
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
