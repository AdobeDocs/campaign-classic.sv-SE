---
title: Om Campaign-integreringar
description: Lär dig mer om funktionella integreringar mellan den aktuella versionen av Adobe Campaign och [Adobe Experience Cloud-lösningar]
page-status-flag: never-activated
uuid: 087abdf0-b4b2-45e6-be21-b03bf85ddf83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: campaign-integrations
discoiquuid: 0af1fd96-48ef-43c9-a03b-0f9a6e0e02fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c3737b22c7bf4e614c5a2fbe8e8fd954d3ece8a
workflow-type: tm+mt
source-wordcount: '778'
ht-degree: 0%

---


# Om Campaign-integreringar {#about-campaign-integrations}

Adobe Experience Cloud är en omfattande uppsättning förstklassiga, integrerade lösningar som bygger på en gemensam dataplattform med en gemensam uppsättning kraftfulla bastjänster.

Lär dig mer om funktionella integreringar mellan Adobe Campaign och [Adobe Experience Cloud-lösningar](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) och [bastjänster](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html). Sedan kan ni modernisera era lösningar och implementera Experience Cloud så att ni kan använda funktioner som kundattribut och målgrupper.

En fullständig lista över Adobes lösningar och bastjänster som kan integreras med Adobe Campaign samt tillhörande dokumentation finns i [det här avsnittet](#experience-cloud-integrations).

![](assets/ExCloud-solutions.png)


>[!CAUTION]
>
>De flesta av dessa integreringar kräver att du loggar in via ett Adobe ID (IMS). Mer information om den här implementeringen finns på [den här sidan](../../integrations/using/about-adobe-id.md).
>
>Observera att IMS-implementering är en komplex process som kan vara lång. Det är förbehållet Adobes tekniska administratörer.

## Länka lösningar {#working-with-experience-cloud-solutions}

Beroende på din miljö kan flera lösningar länkas till Adobe Experience Cloud. De är länkade som organisationer. En **organisation** är den enhet som gör det möjligt för en administratör att konfigurera grupper och användare samt att styra enkel inloggning i Experience Cloud. Organisationen fungerar som ett inloggningsföretag som omfattar alla produkter och lösningar från Experience Cloud. Oftast är en organisation ditt företagsnamn. Ett företag kan dock ha många organisationer.

Organisationshantering och länkning av Adobe Experience Cloud-konton beskrivs i hjälpportalen [för](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html)Adobe Experience Cloud.

>[!CAUTION]
>
>När du nyinstallerar Adobe Campaign eller integrerar en befintlig installation med Adobe Experience Cloud aktiveras [Experience Cloud ID-tjänsten](https://docs.adobe.com/content/help/en/id-service/using/home.html) . Den här tjänsten ersätter den permanenta cookie som framför allt används av Adobe Campaign för spårningsfunktionerna.
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
   <th> Användningsexempel<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Real-time Customer Data Platform</strong><br /> </td> 
   <td> Integrationen mellan Adobe Campaign och Adobe Real-time Customer Data Platform gör att ni kan dela segmentdata och importera målgrupper till Adobe Campaign.<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">Läs mer</a> om Campaign - Platform-integrering med kunddata i realtid från Adobe.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS - Adobe ID</strong><br /> </td> 
   <td> Gör att ni kan ansluta till Adobe Campaign med samma Adobe ID som för andra Adobe Experience Cloud-lösningar.<br /> Ett Adobe ID måste användas för att logga in för att kunna använda vissa funktioner som är kopplade till Adobe Experience Cloud-integreringar, särskilt bastjänsterna.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Läs mer</a> om hur du implementerar Adobe ID med Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Gör att du kan skapa e-postinnehåll eller formulär som mappas till Adobe Campaign-databasen direkt i <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Läs mer</a> om integrationen mellan Adobe Campaign och Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Gör att du kan infoga bilder som beräknas dynamiskt av <strong>Adobe Target</strong> när e-postmeddelandet som skapas och skickas av Adobe Campaign öppnas.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Läs mer</a> om integrationen mellan Adobe Campaign och Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Bastjänst</strong><br /> för människor <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Gör att ni kan dela målgrupper mellan Adobe Experience Cloud-lösningarna och kärnan som ni använder.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Läs mer</a> om Adobe Campaign - Bastjänsten för människor och integreringar med Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Bastjänst för tillgångar</strong><br /> </td> 
   <td> Gör att du kan infoga resurser från ditt Adobe Experience Cloud-bibliotek i e-postmeddelanden och landningssidor som skapats i Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Läs mer</a> om Adobe Campaign - Integrering med bastjänsterna för Assets</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Gör att du kan infoga resurser från ditt <strong>AEM Assets</strong> -bibliotek i e-postmeddelanden och landningssidor som skapats i Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Läs mer</a> om integrationen mellan Adobe Campaign och AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud-utlösare</strong><br /> </td> 
   <td> Integrationen mellan <strong>Triggers bastjänst</strong> och Adobe Campaign gör att ni kan skicka personaliserade e-postmeddelanden till era kunder som en reaktion på specifika beteenden som Adobe Analytics spårar på er webbplats.<br /> <p><a href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html">Läs mer</a> om integrering mellan Adobe Campaign och Experience Cloud.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics - Dataanslutningar</strong><br /> </td> 
   <td> <strong>Med datakopplingar</strong> (som tidigare kallades Adobe Genesis) kan Adobe Campaign och Adobe Analytics interagera genom segment som rör användarbeteende efter en e-postkampanj. Omvänt skickas indikatorer och attribut för e-postkampanjer som levereras av Adobe Campaign till Adobe Analytics - Datakoppling.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">Läs mer</a> om Campaign - Integrering med Data Connectors.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

