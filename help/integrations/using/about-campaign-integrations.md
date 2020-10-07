---
title: Om integreringar i Campaign
description: Använd andra Adobe-lösningar och kombinera deras olika funktioner med Campaign.
page-status-flag: never-activated
uuid: 087abdf0-b4b2-45e6-be21-b03bf85ddf83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: campaign-integrations
discoiquuid: 0af1fd96-48ef-43c9-a03b-0f9a6e0e02fe
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 10%

---


# Om integreringar i Campaign {#about-campaign-integrations}

Adobe Experience Cloud är en omfattande uppsättning förstklassiga, integrerade lösningar som bygger på en gemensam dataplattform med en gemensam uppsättning kraftfulla bastjänster.

Läs om funktionella integreringar mellan Adobe Campaign och [Adobe Experience Cloud lösningar](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) och [bastjänster](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html). Sedan kan ni modernisera era lösningar och implementera Experience Cloud så att ni kan använda funktioner som kundattribut och målgrupper.

En fullständig lista över Adobe-lösningar och bastjänster som kan integreras med Adobe Campaign, samt tillhörande dokumentation, finns i [detta avsnitt](#experience-cloud-integrations).

![](assets/ExCloud-solutions.png)


>[!CAUTION]
>
>De flesta av dessa integreringar kräver att du loggar in via en Adobe ID (IMS). For more on this implementation, refer to [this page](../../integrations/using/about-adobe-id.md).
>
>Observera att IMS-implementering är en komplex process som kan vara lång. Det är förbehållet de tekniska administratörerna i Adobe.

## Länka lösningar {#working-with-experience-cloud-solutions}

Beroende på din miljö kan flera lösningar länkas till Adobe Experience Cloud. De är länkade som organisationer. An **organization** is the entity that enables an administrator to configure groups and users, and to control single sign-on in the Experience Cloud. Organisationen fungerar som ett inloggningsföretag som omfattar alla produkter och lösningar i Experience Cloud. Oftast är en organisation ditt företagsnamn. Ett företag kan dock ha många organisationer.

Organisationshantering och länkning av Adobe Experience Cloud-konton finns i [Adobe Experience Cloud hjälpportal](https://docs.adobe.com/content/help/sv-SE/core-services/interface/manage-users-and-products/organizations.html).

>[!CAUTION]
>
>När du installerar om Adobe Campaign eller integrerar en befintlig installation med Adobe Experience Cloud aktiveras [Experience Cloud ID-tjänsten](https://docs.adobe.com/content/help/en/id-service/using/home.html) . Den här tjänsten ersätter den permanenta cookie som framför allt används av Adobe Campaign för spårningsfunktionerna.
>
>Ett unikt besökar-ID tilldelas sedan mottagare som genererar spårningsloggar. Detta ID sparas i **[!UICONTROL Requester UUID (@sourceID)]** fältet i **[!UICONTROL nms:trackingLogRcp]** tabellen. Spårningsdata för mottagare som fanns innan besökar-ID-tjänsten implementerades kommer därför inte längre att vara användbara.
>
>ID:t känns sedan igen av de andra Adobe Experience Cloud-lösningarna med samma [CNAME](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/cname.html).

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
   <td> <strong>Adobe kunddataplattform i realtid</strong><br /> </td> 
   <td> Integrationen mellan Adobe Campaign och Adobe kunddataplattform i realtid gör att ni kan dela segmentdata och importera målgrupper till Adobe Campaign.<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">Läs mer</a> om Campaign - Integrering av kunddataplattformen i realtid med Adobe.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS - Adobe ID</strong><br /> </td> 
   <td> Gör att du kan ansluta till Adobe Campaign med samma Adobe ID som för andra Adobe Experience Cloud-lösningar.<br /> En Adobe ID måste användas för att logga in för att kunna använda vissa funktioner som är kopplade till Adobe Experience Cloud integreringar, särskilt bastjänster.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Läs mer</a> om hur du implementerar Adobe ID med Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Allows you to create email contents or forms mapped to the Adobe Campaign database directly in <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Läs mer</a> om Adobe Campaign-Adobe Experience Manager-integrering.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Allows you to insert images that are dynamically computed by <strong>Adobe Target</strong> when the email created and sent by Adobe Campaign is opened.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Läs mer</a> om Adobe Campaign-Adobe Target-integrering.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Bastjänst</strong><br /> för människor <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Gör att ni kan dela målgrupper mellan Adobe Experience Cloud lösningar och kärnan som ni använder.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Läs mer</a> om Adobe Campaign - Bastjänst för människor och Adobe Audience Manager-integreringar.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Bastjänst för tillgångar</strong><br /> </td> 
   <td> Du kan infoga resurser från ditt bibliotek i Adobe Experience Cloud i e-postmeddelanden och landningssidor som har skapats i Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Läs mer</a> om Adobe Campaign - integreringen av bastjänsterna för Assets</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Allows you to insert assets from your <strong>AEM Assets</strong> library into emails and landing pages created in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Läs mer</a> om Adobe Campaign-AEM Assets-integrering.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Utlösare i Experience Cloud</strong><br /> </td> 
   <td> Integration between <strong>Triggers core service</strong> and Adobe Campaign allows you to send personalized emails to your customers as a reaction to specific behaviors that are tracked on your website by Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/se/campaign/kb/triggers-and-campaign.html">Läs mer</a> om integrering mellan Adobe Campaign och Experience Cloud.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics - Dataanslutningar</strong><br /> </td> 
   <td> <strong>Med datakopplingar</strong> (som tidigare kallades Adobe Genesis) kan Adobe Campaign och Adobe Analytics interagera genom segment som rör användarbeteende efter en e-postkampanj. Omvänt skickas indikatorer och attribut för e-postkampanjer som levereras av Adobe Campaign till Adobe Analytics - Datakoppling.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">Läs mer</a> om Campaign - Integrering med Data Connectors.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

