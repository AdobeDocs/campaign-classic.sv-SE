---
product: campaign
title: Om integreringar i Campaign
description: Använd andra Adobe-lösningar och kombinera deras olika funktioner med Campaign
feature: Overview
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 597d24fa780a324507c56c55a5309b6ee1cf46eb
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 4%

---

# Kom igång med Adobe Campaign-integreringar {#about-campaign-integrations}

Adobe Experience Cloud är en omfattande uppsättning förstklassiga, integrerade lösningar som bygger på en gemensam dataplattform med en gemensam uppsättning kraftfulla lösningar och appar.

Läs mer om funktionsintegreringar mellan Adobe Campaign- och Adobe Experience Cloud-lösningar på [den här sidan](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/integrations){_blank}.

En fullständig lista över Adobe-lösningar och apptjänster som kan integreras med Adobe Campaign, samt tillhörande dokumentation, finns i [det här avsnittet](#experience-cloud-integrations).

>[!CAUTION]
>
>Dessa integreringar kräver att Adobe Identity Management System (IMS) implementeras för att logga in via Adobe ID. [Läs mer på den här sidan](../../integrations/using/about-adobe-id.md).
>

## Länka era lösningar {#working-with-experience-cloud-solutions}

Flera lösningar kan länkas till Adobe Experience Cloud. **organisationen** är den kundentitet som gör det möjligt för en administratör att konfigurera grupper och användare samt att styra enkel inloggning (SSO) i Adobe Experience Cloud. Organisationen fungerar som ett inloggningsföretag som omfattar alla produkter och lösningar från Experience Cloud. Oftast är en organisation ditt företagsnamn. Ett företag kan dock ha många organisationer.

Organisationshantering och länkning av Adobe Experience Cloud-konton finns i [Adobe Experience Cloud hjälpportal](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations){_blank}.

## Hantering av identitet och cookies {#id-and-cookies}

När du installerar Adobe Campaign eller integrerar en befintlig installation med Adobe Experience Cloud är [Adobe Experience Cloud identitetstjänst](https://experienceleague.adobe.com/en/docs/id-service/using/home){_blank} aktiverad. Den här tjänsten ersätter den permanenta cookie som framför allt används av Adobe Campaign för spårningsfunktionerna.

Adobe Experience Cloud ID-tjänst (Identity Service) är ett universellt, beständigt ID som identifierar besökarna i alla lösningar i Experience Cloud.

Ett unikt besökar-ID tilldelas mottagare som genererar spårningsloggar. Detta ID sparas i fältet **[!UICONTROL Requester UUID (@sourceID)]** i tabellen **[!UICONTROL nms:trackingLogRcp]**. **Spårningsdata för mottagare som fanns innan besökar-ID-tjänsten implementerades kommer därför inte längre att kunna användas**.

ID:t känns sedan igen av de andra Adobe Experience Cloud-lösningarna med samma CNAME. [Läs mer](https://experienceleague.adobe.com/en/docs/id-service/using/reference/analytics-reference/cname){_blank}.

## Experience Cloud-integreringar {#experience-cloud-integrations}

Följande tabell visar tillgänglig integreringsdokumentation för Experience Cloud.

<table> 
 <thead> 
  <tr> 
   <th> Lösningar och appar <br /> </th> 
   <th> Användningsfall<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Real-time Customer Data Platform (RTCDP)</strong><br /> </td> 
   <td> Konfigurera integreringen mellan Adobe Campaign och Adobe Real-time Customer Data Platform (RTCDP) för att dela segmentdata och importera målgrupper till Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">Läs mer</a> om Campaign - Adobe Real-time Customer Data Platform-integrering.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS) - Adobe ID</strong><br /> </td> 
   <td> Konfigurera Adobe IMS för att ansluta till Adobe Campaign med samma Adobe ID som för andra Adobe Experience Cloud-lösningar.<br /> En Adobe ID måste användas för att logga in för att kunna använda vissa funktioner som är kopplade till Adobe Experience Cloud-integreringar.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Läs mer</a> om hur du implementerar Adobe ID med Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Konfigurera den här integreringen för att skapa e-postinnehåll eller formulär som mappas till Adobe Campaign-databasen direkt i <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Läs mer</a> om integrering mellan Adobe Campaign och Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Konfigurera den här integreringen för att infoga bilder som beräknas dynamiskt av <strong>Adobe Target</strong> när e-postmeddelandet som skapas och skickas av Adobe Campaign öppnas.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Läs mer</a> om integrering mellan Adobe Campaign och Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Konfigurera den här integreringen för att dela målgrupper mellan Adobe Experience Cloud-lösningar och appar som du använder.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Läs mer</a> om Adobe Campaign - Adobe Audience Manager-integreringar.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Assets</strong><br /> </td> 
   <td> Konfigurera den här integreringen för att infoga resurser från ditt Adobe Experience Cloud-bibliotek i e-postmeddelanden och landningssidor som skapats i Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Läs mer</a> om integrering med Adobe Campaign - Assets</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Konfigurera den här integreringen för att infoga resurser från ditt <strong>AEM Assets</strong> -bibliotek i e-postmeddelanden och landningssidor som skapats i Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Läs mer</a> om integrering mellan Adobe Campaign och AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Utlösare för Experience Cloud</strong><br /> </td> 
   <td> Konfigurera integreringen mellan <strong>Adobe Experience Cloud Triggers</strong> och Adobe Campaign för att skicka personaliserade e-postmeddelanden till dina kunder som en reaktion på specifika beteenden som spåras på din webbplats av Adobe Analytics.<br /> <p><a href="about-triggers.md">Läs mer</a> om integrering mellan Adobe Campaign och Experience Cloud-utlösare.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics Connector</strong><br /> </td> 
   <td> Konfigurera den här integreringen så att Adobe Campaign och Adobe Analytics kan interagera genom segment som rör användarbeteende efter en e-postkampanj. Omvänt skickas indikatorer och attribut för e-postkampanjer från Adobe Campaign till Adobe Analytics.<br /> <p><a href="../../integrations/using/gs-aa.md">Läs mer</a> om Campaign - Integrering med Analytics Connectors.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
