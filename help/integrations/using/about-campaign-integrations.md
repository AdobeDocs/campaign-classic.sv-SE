---
product: campaign
title: Om integreringar i Campaign
description: Använd andra Adobe-lösningar och kombinera deras olika funktioner med Campaign
feature: Overview
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 59156851156338c9462781d31ce81a651362f2da
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 7%

---

# Kom igång med Adobe Campaign-integreringar {#about-campaign-integrations}



Adobe Experience Cloud är en omfattande uppsättning förstklassiga, integrerade lösningar som bygger på en gemensam dataplattform med en gemensam uppsättning kraftfulla bastjänster.

Läs om funktionella integreringar mellan Adobe Campaign och [Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/marketing-cloud-integrations.html) och [bastjänster](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html). Sedan kan ni modernisera era lösningar och implementera Experience Cloud så att ni kan använda funktioner som kundattribut och målgrupper.

![](assets/ExCloud-solutions.png)

En fullständig lista över Adobe-lösningar och bastjänster som kan integreras med Adobe Campaign, samt tillhörande dokumentation, finns på [det här avsnittet](#experience-cloud-integrations).

>[!CAUTION]
>
>De flesta av dessa integreringar kräver att Adobe Identity Management System (IMS) implementeras för att logga in via Adobe ID. [Läs mer på den här sidan](../../integrations/using/about-adobe-id.md).
>

## Länka era lösningar {#working-with-experience-cloud-solutions}

Flera lösningar kan länkas till Adobe Experience Cloud. The **organisation** är den kundenhet som gör det möjligt för en administratör att konfigurera grupper och användare samt att styra enkel inloggning (SSO) i Adobe Experience Cloud. Organisationen fungerar som ett inloggningsföretag som omfattar alla produkter och lösningar från Experience Cloud. Oftast är en organisation ditt företagsnamn. Ett företag kan dock ha många organisationer.

Organisationshantering och länkning av Adobe Experience Cloud-konton finns i [Adobe Experience Cloud hjälpportal](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html).

## Hantering av identitet och cookies {#id-and-cookies}

När du installerar Adobe Campaign eller integrerar en befintlig installation med Adobe Experience Cloud [Adobe Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/id-service/using/home.html) är aktiverat. Den här tjänsten ersätter den permanenta cookie som framför allt används av Adobe Campaign för spårningsfunktionerna.

Adobe Experience Cloud ID-tjänst (Identity Service) är ett universellt, beständigt ID som identifierar besökarna i alla lösningar i Experience Cloud.

Ett unikt besökar-ID tilldelas mottagare som genererar spårningsloggar. Detta ID sparas i **[!UICONTROL Requester UUID (@sourceID)]** fält för **[!UICONTROL nms:trackingLogRcp]** tabell. **Spårningsdata för mottagare som fanns innan besökar-ID-tjänsten implementerades kommer därför inte längre att vara användbara**.

ID:t känns sedan igen av de andra Adobe Experience Cloud-lösningarna med samma CNAME. [Läs mer](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/cname.html)

## Experience Cloud-integreringar {#experience-cloud-integrations}

Följande tabell visar tillgänglig integreringsdokumentation för Experience Cloud.

<table> 
 <thead> 
  <tr> 
   <th> Lösningar och bastjänster<br /> </th> 
   <th> Användningsfall<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Real-time Customer Data Platform (RTC)</strong><br /> </td> 
   <td> Tack vare integreringen mellan Adobe Campaign och Adobe Real-time Customer Data Platform (RTCDP) kan ni dela segmentdata och importera målgrupper till Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">Läs mer</a> om Campaign - integrering med Adobe Real-time Customer Data Platform.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS) - Adobe ID</strong><br /> </td> 
   <td> Gör att du kan ansluta till Adobe Campaign med samma Adobe ID som för andra Adobe Experience Cloud-lösningar.<br /> En Adobe ID måste användas för att logga in för att kunna använda vissa funktioner som är kopplade till Adobe Experience Cloud integreringar, särskilt bastjänster.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Läs mer</a> om att implementera Adobe ID med Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Skapa e-postinnehåll eller formulär som mappas till Adobe Campaign-databasen direkt i <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Läs mer</a> om Adobe Campaign - integrering med Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Gör att du kan infoga bilder som beräknas dynamiskt av <strong>Adobe Target</strong> när e-postmeddelandet som skapats och skickats av Adobe Campaign öppnas.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Läs mer</a> om Adobe Campaign - integrering med Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Bastjänst för människor</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Gör att ni kan dela målgrupper mellan Adobe Experience Cloud lösningar och kärnan som ni använder.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Läs mer</a> om Adobe Campaign - Bastjänsten för människor och Adobe Audience Manager-integreringar.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Bastjänst för tillgångar</strong><br /> </td> 
   <td> Du kan infoga resurser från ditt bibliotek i Adobe Experience Cloud i e-postmeddelanden och landningssidor som har skapats i Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Läs mer</a> om Adobe Campaign - Integrering med bastjänsterna Assets</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Gör att du kan infoga resurser från dina <strong>AEM Assets</strong> bibliotek till e-postmeddelanden och landningssidor som skapats i Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Läs mer</a> om Adobe Campaign - integrering med AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud-utlösare</strong><br /> </td> 
   <td> Integration mellan <strong>Startar bastjänst</strong> och Adobe Campaign gör att ni kan skicka personaliserade e-postmeddelanden till era kunder som en reaktion på specifika beteenden som spåras på er webbplats av Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/se/campaign/kb/triggers-and-campaign.html">Läs mer</a> om Adobe Campaign - integrering av utlösare för Experience Cloud.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics Connector</strong><br /> </td> 
   <td> <strong>Adobe Analytics Connector</strong> gör att Adobe Campaign och Adobe Analytics kan interagera genom segment som rör användarbeteende efter en e-postkampanj. Omvänt skickas indikatorer och attribut för e-postkampanjer från Adobe Campaign till Adobe Analytics.<br /> <p><a href="../../platform/using/gs-aa.md">Läs mer</a> om Campaign - Integrering med Analytics Connectors.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
