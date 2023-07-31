---
product: campaign
title: Dela målgrupper med Adobe Experience Cloud
description: Dela målgrupper med Adobe Experience Cloud
feature: Audiences, People Core Service Integration
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 6%

---

# Dela målgrupper med Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}



>[!CAUTION]
>
>För att kunna dela målgrupper med Adobe Experience Cloud lösningar måste ni implementera Adobe Identity Management System. [Läs mer om IMS](../../integrations/using/about-adobe-id.md).

Med Adobe Campaign kan ni dela målgrupper och segment med Adobe Experience Cloud lösningar och bastjänster. Det finns två alternativ:

1. Skicka Adobe Experience Platform segmentdata till Adobe Campaign. För att implementera integreringen måste ni koppla Real-time Customer Data Platform till Campaign (RTCDP). [Läs mer i det här avsnittet](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

1. Integrera **Adobe Campaign** med **Bastjänst för människor** (kallas även **Bastjänst för profiler och målgrupper**) eller Adobe Audience Manager. Då kan du:

   * Importera delade målgrupper/segment från olika Adobe Experience Cloud-lösningar till Adobe Campaign. Publiker kan importeras via listor i Adobe Campaign.

   * Exportera listor i form av delade Adobe Experience Cloud-målgrupper. Dessa målgrupper kan användas i de olika Adobe Experience Cloud-lösningar ni använder. Målgrupper kan exporteras efter målgruppsanpassning i ett arbetsflöde med hjälp av en dedikerad **[!UICONTROL Update shared audience]** aktivitet.

Den här integreringen stöder två typer av Adobe Experience Cloud ID:

* **Besökar-ID**: den här typen av identifierare förenar Adobe Experience Cloud-besökare med Adobe Campaign-mottagare.
* **Deklarerat ID**: den här typen av identifierare förenar alla typer av data med element från Adobe Campaign-databasen. Den representeras i Adobe Campaign som en fördefinierad avstämningsnyckel.

  >[!NOTE]
  >
  > Deklarerad  ID-datakälla kan nu även användas med integreringen av den grundläggande tjänsten People.
  >
  >Om du använder integreringen med huvudtjänsten Kontakter och vill lägga till integreringen med Audience Manager måste du få hjälp av en Adobe Audience Manager-konsults för att undvika att förlora alla ID-synkroniseringar som samlas in när du går över till att använda den här deklarerade ID-datakällan i ett Adobe Audience Manager-sammanhang.
