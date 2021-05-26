---
solution: Campaign Classic
product: campaign
title: Dela målgrupper med Adobe Experience Cloud
description: Dela målgrupper med Adobe Experience Cloud
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: bce114f36d1ec4582fc79e750d48155ba0d7cd1f
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 4%

---

# Dela målgrupper med Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>För att kunna dela målgrupper med Adobe Experience Cloud lösningar måste ni implementera Adobe Identity Management System. [Läs mer om IMS](../../integrations/using/about-adobe-id.md).

Med Adobe Campaign kan ni dela målgrupper och segment med Adobe Experience Cloud lösningar och bastjänster. Det finns två alternativ:

1. Skicka Adobe Experience Platform segmentdata till Adobe Campaign. För att implementera den här integreringen måste ni koppla kunddataplattformen i realtid till Campaign (RTCDP). [Läs mer i det här avsnittet](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).


1. Integrera **Adobe Campaign** med **People core service** (kallas även **kärntjänsten Profiles &amp; Audiences**) eller Adobe Audience Manager. Då kan du:

   * Importera delade målgrupper/segment från olika Adobe Experience Cloud-lösningar till Adobe Campaign. Publiker kan importeras via listor i Adobe Campaign.

   * Exportera listor i form av Adobe Experience Cloud delade målgrupper. Dessa målgrupper kan användas i de olika Adobe Experience Cloud-lösningar ni använder. Målgrupper kan exporteras efter målgruppsanpassning i ett arbetsflöde med en dedikerad **[!UICONTROL Update shared audience]**-aktivitet.

Den här integreringen stöder två typer av Adobe Experience Cloud ID:

* **Besökar-ID**: den här typen av identifierare används för att anpassa Adobe Experience Cloud-besökare till Adobe Campaign-mottagare.
* **Deklarerat ID**: den här typen av identifierare kan stämma av alla typer av data med element från Adobe Campaign-databasen. Den representeras i Adobe Campaign som en fördefinierad avstämningsnyckel.

   >[!NOTE]
   >
   > Deklarerad  ID-datakälla kan nu även användas med integreringen av den grundläggande tjänsten People.
   >
   >Om du använder integreringen med huvudtjänsten Kontakter och vill lägga till integreringen med Audience Manager måste du få hjälp av en Adobe Audience Manager-konsults för att undvika att förlora alla ID-synkroniseringar som samlas in när du går över till att använda den här deklarerade ID-datakällan i ett Adobe Audience Manager-sammanhang.
