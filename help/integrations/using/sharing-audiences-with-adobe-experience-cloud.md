---
product: campaign
title: Dela målgrupper med Adobe Experience Cloud
description: Dela målgrupper med Adobe Experience Cloud
feature: Audiences
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Dela målgrupper med Adobe Experience Cloud {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>För att kunna dela målgrupper med Adobe Experience Cloud lösningar måste ni implementera Adobe Identity Management System. [Läs mer om IMS](../../integrations/using/about-adobe-id.md).

Med Adobe Campaign kan ni dela målgrupper och segment med Adobe Experience Cloud tjänster. Det finns två alternativ:

1. Skicka Adobe Experience Platform segmentdata till Adobe Campaign. För att implementera integreringen måste ni koppla Real-time Customer Data Platform till Campaign (RTCDP). [Läs mer i det här avsnittet](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=sv-SE){target="_blank"}.

1. Integrera **Adobe Campaign** med **Experience Cloud-målgrupper** eller **Adobe Audience Manager**. Då kan du:

   * Importera delade målgrupper/segment från olika Adobe Experience Cloud-lösningar till Adobe Campaign. Publiker kan importeras via listor i Adobe Campaign.

   * Exportera listor i form av delade Adobe Experience Cloud-målgrupper. Dessa målgrupper kan användas i de olika Adobe Experience Cloud-lösningar ni använder. Publiker kan exporteras efter målgruppsanpassning i ett arbetsflöde med en dedikerad **[!UICONTROL Update shared audience]**-aktivitet.

Den här integreringen stöder två typer av Adobe Experience Cloud ID:

* **Besökar-ID**: den här typen av identifierare förenar Adobe Experience Cloud-besökare med Adobe Campaign-mottagare.
* **Deklarerat ID**: Den här typen av identifierare förenar alla typer av data med element från Adobe Campaign-databasen. Den representeras i Adobe Campaign som en fördefinierad avstämningsnyckel.

  >[!NOTE]
  >
  > Deklarerad ID-datakälla kan nu även användas med Experience Cloud Assets-integrering.
  >
