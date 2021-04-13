---
solution: Campaign Classic
product: campaign
title: Om integreringar i Campaign
description: Använd andra Adobe-lösningar och kombinera deras olika funktioner med Campaign.
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
translation-type: tm+mt
source-git-commit: 326ccbad77f3bd03a8eba22d7714084d52d2f02b
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 8%

---

# Kom igång med Adobe Campaign-integreringar {#about-campaign-integrations}

Adobe Experience Cloud är en omfattande uppsättning förstklassiga, integrerade lösningar som bygger på en gemensam dataplattform med en gemensam uppsättning kraftfulla bastjänster.

Läs om funktionsintegreringar som finns mellan Adobe Campaign och [Adobe Experience Cloud lösningar](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) och [bastjänster](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html). Sedan kan ni modernisera era lösningar och implementera Experience Cloud så att ni kan använda funktioner som kundattribut och målgrupper.

![](assets/ExCloud-solutions.png)

En fullständig lista över Adobe-lösningar och bastjänster som kan integreras med Adobe Campaign, samt tillhörande dokumentation, finns i [det här avsnittet](#experience-cloud-integrations).

>[!CAUTION]
>
>De flesta av dessa integreringar kräver att Adobe Identity Management System (IMS) implementeras för att logga in via Adobe ID. [Läs mer på den här sidan](../../integrations/using/about-adobe-id.md).


## Länka dina lösningar {#working-with-experience-cloud-solutions}

Flera lösningar kan kopplas till Adobe Experience Cloud. **organisationen** är den kundenhet som gör det möjligt för en administratör att konfigurera grupper och användare samt att styra enkel inloggning (SSO) i Adobe Experience Cloud. Organisationen fungerar som ett inloggningsföretag som omfattar alla produkter och lösningar från Experience Cloud. Oftast är en organisation ditt företagsnamn. Ett företag kan dock ha många organisationer.

Organisationshantering och länkning av Adobe Experience Cloud-konton beskrivs i [Adobe Experience Cloud hjälpportal](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html).

## Hantering av identitet och cookies {#id-and-cookies}

När du installerar Adobe Campaign eller integrerar en befintlig installation med Adobe Experience Cloud är [Adobe Experience Cloud identitetstjänst](https://docs.adobe.com/content/help/en/id-service/using/home.html) aktiverad. Den här tjänsten ersätter den permanenta cookie som framför allt används av Adobe Campaign för spårningsfunktionerna.

Adobe Experience Cloud ID-tjänst (Identity Service) är ett universellt, beständigt ID som identifierar besökarna i alla lösningar i Experience Cloud.

Ett unikt besökar-ID tilldelas mottagare som genererar spårningsloggar. Detta ID sparas i fältet **[!UICONTROL Requester UUID (@sourceID)]** i tabellen **[!UICONTROL nms:trackingLogRcp]**. **Spårningsdata för mottagare som fanns innan besökar-ID-tjänsten implementerades kommer därför inte längre att vara användbara**.

ID:t känns sedan igen av de andra Adobe Experience Cloud-lösningarna med samma [CNAME](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/cname.html).

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
   <td> <strong>Adobe Real-time Customer Data Platform (RTCDP)</strong><br /> </td> 
   <td> Integrationen mellan Adobe Campaign och Adobe Real-time Customer Data Platform (RTCDP) gör att du kan dela segmentdata och importera målgrupper till Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">Läs </a> mer om Campaign - Integrering av kunddataplattformen i realtid med Adobe.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS) - Adobe ID</strong><br /> </td> 
   <td> Gör att du kan ansluta till Adobe Campaign med samma Adobe ID som för andra Adobe Experience Cloud-lösningar.<br /> En Adobe ID måste användas för att logga in för att kunna använda vissa funktioner som är kopplade till Adobe Experience Cloud integreringar, särskilt bastjänster.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Läs </a> mer om hur du implementerar Adobe ID med Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Gör att du kan skapa e-postinnehåll eller formulär som mappas till Adobe Campaign-databasen direkt i <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Läs </a> mer om integrationen mellan Adobe Campaign och Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Gör att du kan infoga bilder som beräknas dynamiskt av <strong>Adobe Target</strong> när e-postmeddelandet som skapas och skickas av Adobe Campaign öppnas.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Läs </a> mer om integrationen mellan Adobe Campaign och Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Bastjänst </strong><br /> <strong>för människorAdobe Audience Manager</strong><br /> </td> 
   <td> Gör att du kan dela målgrupper mellan Adobe Experience Cloud lösningar och kärnan som du använder.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Läs </a> mer om Adobe Campaign - Bastjänst för människor och Adobe Audience Manager-integreringar.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Bastjänst för tillgångar</strong><br /> </td> 
   <td> Du kan infoga resurser från ditt bibliotek i Adobe Experience Cloud i e-postmeddelanden och landningssidor som har skapats i Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Läs </a> mer om Adobe Campaign - Integrering av bastjänsterna för Assets</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Gör att du kan infoga resurser från ditt <strong>AEM Assets</strong>-bibliotek i e-postmeddelanden och landningssidor som skapats i Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Läs </a> mer om integrationen mellan Adobe Campaign och AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Utlösare i Experience Cloud</strong><br /> </td> 
   <td> Integrationen mellan <strong>Triggers core service</strong> och Adobe Campaign gör att du kan skicka personaliserade e-postmeddelanden till dina kunder som en reaktion på specifika beteenden som spåras på din webbplats av Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/se/campaign/kb/triggers-and-campaign.html">Läs </a> mer om integrationen mellan Adobe Campaign och Experience Cloud.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics - Dataanslutningar</strong><br /> </td> 
   <td> <strong>Med datakopplingar</strong>  (som tidigare kallades Adobe Genesis) kan Adobe Campaign och Adobe Analytics interagera genom segment som rör användarbeteende efter en e-postkampanj. Omvänt skickas indikatorer och attribut för e-postkampanjer som levereras av Adobe Campaign till Adobe Analytics - Dataanslutning.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">Läs </a> mer om Campaign - Integrering med Data Connectors.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
