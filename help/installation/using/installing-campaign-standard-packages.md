---
title: Installera standardpaket för Campaign Classic
seo-title: Installera standardpaket för Campaign Classic
description: Installera standardpaket för Campaign Classic
seo-description: null
page-status-flag: never-activated
uuid: 1cba9487-52fc-442f-ae99-f8a2c157f25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: dd8f9adf-208c-42d9-b1a7-bfc8a690687e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: efef031d9c662daac6634ff7cc0d05d9d512443b

---


# Installera standardpaket för Campaign Classic{#installing-campaign-standard-packages}

## Om standardpaket {#campaign-standard-packages}

Paket är en uppsättning funktioner som kan installeras efter behov. De gör att du kan lägga till fler alternativ till instansen.

>[!CAUTION]
>
>Du får endast installera paket som motsvarar alternativen i licensavtalet.
>
>När ett paket har installerats kan du inte avinstallera det. Installationen av ett nytt paket kan påverka hela plattformen: den måste testas och valideras innan den slutliga driftsättningen.

Så här installerar du ett standardpaket:

1. Öppna guiden för paketimport från **[!UICONTROL Tools > Advanced > Package import...]** Adobe Campaign-klientkonsolen.
1. Välj **[!UICONTROL Install a standard package]**.
1. Kontrollera de paket som du vill installera i listan som visas.
   >[!NOTE]
   >
   >Om ett paket är nedtonat kan du inte installera det. Det betyder att det redan är installerat eller att det inte är kompatibelt med din instans. Du kan t.ex. inte installera **paketet med plattformar** för mellanleverantörer på en marknadsinstans. Den här informationen finns i tabellen nedan.
1. Klicka **[!UICONTROL Next]** och sedan **[!UICONTROL Start]** för att starta paketinstallationen.

   När paketen har installerats visar förloppsindikatorn **100 %** och följande meddelande visas i installationsloggarna: **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** installationsfönstret.

Paketen är nu installerade.

### Lista över färdiga paket {#list-of-standard-packages}

I följande tabell visas alla standardpaket med deras beskrivning, instanstypen som de kan installeras på (Marknadsföring, Mid, osv.) och ytterligare information.

<table> 
 <thead> 
  <tr> 
   <th> Paket </th> 
   <th> Beskrivning </th> 
   <th> Instanstyp </th> 
   <th> Mer info </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Leverans<br /> </td> 
   <td> Övervakar leveranser och eventuella problem som uppstår när meddelanden skickas.<br /> </td> 
   <td> Alla</td> 
   <td> <a href="../../delivery/using/monitoring-a-delivery.md">Läs mer</a></td> 
  </tr> 
  <tr> 
   <td> Marknadsföringskampanjer (Campaign)<br /> </td> 
   <td> Definierar, optimerar, kör och analyserar kommunikation och marknadsföringskampanjer.<br /> </td> 
   <td> Marknadsföring</td> 
   <td> <a href="../../campaign/using/designing-marketing-campaigns.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Marknadsföringsresurser<br /> </td> 
   <td> Kontrollerar marknadsföringsåtgärder i ett samverkansbaserat läge genom att tillhandahålla hantering och spårning av uppgifter, budget och marknadsföringsresurser.<br /> </td> 
   <td> Marknadsföring</td> 
   <td> <a href="../../campaign/using/about-marketing-resource-management.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Erbjudandemotor (interaktion)<br /> </td> 
   <td> Svarar i realtid under en interaktion med en viss kontakt (en kund eller ett visst mål) genom att göra dem till ett eller flera anpassade erbjudanden. <br /> </td> 
   <td> Alla<br /> </td> 
   <td> Valfritt, <a href="../../interaction/using/interaction-and-offer-management.md">Läs mer</a></td> 
  </tr> 
  <tr> 
   <td> Kontroll över erbjudandemotorn med körningsinstans<br /> </td> 
   <td> </td> 
   <td> Marknadsföring<br /> </td> 
   <td> Valfritt</td> 
  </tr> 
  <tr> 
   <td> Erbjud motor för körningsinstanser<br /> </td> 
   <td> </td> 
   <td> Mid, körning <br /> </td> 
   <td> Valfritt</td> 
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Sociala nätverk (social marknadsföring) <br /> </td> 
   <td> Synkroniserar Adobe Campaign med Twitter och Facebook.<br /> </td> 
   <td> Alla</td> 
   <td> <a href="../../social/using/about-social-marketing.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Kontroll av transaktionsmeddelanden (Message Center - Control)<br /> </td> 
   <td> Hanterar utlösarmeddelanden som genereras från händelser som utlöses från informationssystem.<br /> </td> 
   <td> Marknadsföring<br /> </td> 
   <td> Valfritt, <a href="../../message-center/using/about-transactional-messaging.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Körning av transaktionsmeddelande (Message Center - Execution) <br /> </td> 
   <td> Säkerställer högre tillgänglighet och bättre lasthantering.<br /> </td> 
   <td> Körning<br /> </td> 
   <td> Valfritt, <a href="../../message-center/using/about-transactional-messaging.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> LINE-kanal<br /> </td> 
   <td> Skickar leveranser via LINE-kanalen med Adobe Campaign,<br /> </td> 
   <td> Alla<br /> </td> 
   <td> Valfritt, meddelandecenter obligatoriskt</td> 
  </tr> 
  <tr> 
   <td> Direktreklam, kanal<br /> </td> 
   <td> Skickar leveranser via direktreklamkanalen med Adobe Campaign.<br /> </td> 
   <td> Alla<br /> </td> 
   <td> Valfritt, <a href="../../delivery/using/about-direct-mail-channel.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Mobilkanal (SMS) <br /> </td> 
   <td> Skickar leveranser via mobil-/SMS-kanalen med Adobe Campaign.<br /> </td> 
   <td> Alla<br /> </td> 
   <td> Valfritt, <a href="../../delivery/using/sms-channel.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Telefonkanal<br /> </td> 
   <td> Skickar leveranser via telefonkanalen med Adobe Campaign.<br /> </td> 
   <td> Alla<br /> </td> 
   <td> Valfritt</td> 
  </tr> 
  <tr> 
   <td> Faxkanal<br /> </td> 
   <td> Skickar leveranser via faxkanalen med Adobe Campaign.<br /> </td> 
   <td> Alla<br /> </td> 
   <td> Valfritt</td> 
  </tr> 
  <tr> 
   <td> Mobilappskanal<br /> </td> 
   <td> Använder Adobe Campaign-plattformen för att skicka personaliserade meddelanden till iOS- och Android-terminaler via appar. <br /> </td> 
   <td> Alla<br /> </td> 
   <td> Valfritt, <a href="../../delivery/using/about-mobile-app-channel.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Content Manager<br /> </td> 
   <td> Skapar återkommande nyhetsbrev eller webbplatser och validerar och publicerar sedan dina meddelanden.<br /> </td> 
   <td> </td> 
   <td> <a href="../../delivery/using/about-content-management.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Onlineundersökningar (Survey Manager)<br /> </td> 
   <td> Skapar och hanterar onlineformulär för att lägga till eller ändra profilinformation, för att prenumerera, för att avbeställa eller för att fylla i ett tävlingsformulär.<br /> </td> 
   <td> Marknadsföring<br /> </td> 
   <td> Valfritt, <a href="../../web/using/about-surveys.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Marknadsföringsanalys<br /> </td> 
   <td> Gör att du kan analysera och mäta data, beräkna statistik, förenkla och optimera framtagning och beräkning av rapporter. Du kan också skapa rapporter och skapa målpopulationer. <br /> </td> 
   <td> Marknadsföring<br /> </td> 
   <td> Valfritt, <a href="../../reporting/using/about-cubes.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Svarshanteraren<br /> </td> 
   <td> Mäter framgången och lönsamheten för marknadsföringskampanjer eller erbjuder förslag för alla kommunikationskanaler.<br /> </td> 
   <td> Marknadsföring<br /> </td> 
   <td> Valfritt, <a href="../../campaign/using/about-response-manager.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Åtkomst till externa data (federerad dataåtkomst)<br /> </td> 
   <td> Tillhandahåller alternativet FDA (Federated Data Access) för att bearbeta information som lagras i en eller flera externa databaser så att du kan komma åt externa data utan att ändra strukturen för Adobe Campaign-data.<br /> </td> 
   <td> Alla<br /> </td> 
   <td> Valfritt, <a href="../../workflow/using/accessing-an-external-database--fda-.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Kampanjoptimering<br /> </td> 
   <td> Kontrollerar, filtrerar och övervakar sändningen av leveranser så att de skickade meddelandena bäst uppfyller kundernas behov och förväntningar, i enlighet med företagets kommunikationspolicy. <br /> </td> 
   <td> Marknadsföring<br /> </td> 
   <td> Valfritt, <a href="../../campaign/using/about-campaign-typologies.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Leveransövervakning (e-postleverans)<br /> </td> 
   <td> Mäter framgången för era kampanjer och når mottagarnas inkorg utan studsar eller markeras som skräppost.<br /> </td> 
   <td> Alla </td> 
   <td> Valfritt, <a href="https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Kuponghantering<br /> </td> 
   <td> Skapar en uppsättning kuponger att lägga till i kommande marknadsföringserbjudanden.<br /> </td> 
   <td> Marknadsföring<br /> </td> 
   <td> Valfritt, <a href="../../delivery/using/personalized-coupons.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Inkorgsåtergivning (IR)<br /> </td> 
   <td> Gör att du kan förhandsgranska meddelandet som skickas i olika sammanhang där det kan tas emot och kontrollera kompatibiliteten i de flesta datorer och program. Du behöver ett Litmus-konto.<br /> </td> 
   <td> Marknadsföring<br /> </td> 
   <td> Valfritt, <a href="../../delivery/using/inbox-rendering.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Central/lokal marknadsföring (distribuerad marknadsföring)<br /> </td> 
   <td> Implementerar samverkanskampanjer mellan centrala enheter (huvudkontor, marknadsavdelningar osv.) och lokala enheter (säljställen, regionala organ osv.).<br /> </td> 
   <td> Marknadsföring </td> 
   <td> Valfritt, <a href="../../campaign/using/about-distributed-marketing.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> CRM-anslutningar<br /> </td> 
   <td> Tillhandahåller olika CRM-anslutningar för att länka din Adobe Campaign-plattform till dina tredjepartssystem.<br /> </td> 
   <td> Marknadsföring</td> 
   <td> <a href="../../platform/using/crm-connectors.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Web Analytics-anslutningar<br /> </td> 
   <td> Tillåter Adobe Campaign och Adobe Analytics att interagera via Web Analytics-anslutningspaketet.<br /> </td> 
   <td> Marknadsföring </td> 
   <td> Inte kompatibelt med transaktionsmeddelanden, <a href="../../platform/using/adobe-analytics-data-connector.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> AEM-integration<br /> </td> 
   <td> Gör att ni kan hantera innehållet i era e-postleveranser och era formulär direkt i Adobe Experience Manager för att dra nytta av både AEM:s funktioner för innehållsredigering och Adobe Campaigns leveranskapacitet.<br /> </td> 
   <td> Marknadsföring</td> 
   <td> <a href="../../integrations/using/about-adobe-experience-manager.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Integrering av delade målgrupper i Adobe Marketing Cloud<br /> </td> 
   <td> Gör att ni kan utbyta och dela målgrupper/segment med Adobe Experience Cloud-lösningar och bastjänster.<br /> </td> 
   <td> Marknadsföring<br /> </td> 
   <td> Kräver IMS, <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Integrering med Adobe Marketing Cloud<br /> </td> 
   <td> Gör att ni kan importera och exportera målgrupper/segment från olika Adobe Marketing Cloud-lösningar till Adobe Campaign. </td> 
   <td> Marknadsföring</td> 
   <td> Valfritt, <a href="../../integrations/using/configuring-ims.md#installing-the-package">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Skyddsförordningen för personuppgifter<br /> </td> 
   <td> Innehåller ytterligare funktionalitet som kan hjälpa dig att uppfylla kraven för sekretess i Campaign Classic.<br /> </td> 
   <td> Alla</td> 
   <td> <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Överföring till medelkälla <br /> </td> 
   <td> Detaljerar installation och konfiguration av en server med mellanlagring samt distributionen av en instans som gör det möjligt för tredje part att skicka meddelanden i mellankälläge.<br /> </td> 
   <td> Marknadsföring </td> 
   <td> Valfritt, <a href="../../installation/using/mid-sourcing-server.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> Plattform för mellanleverantörer<br /> </td> 
   <td> Denna konfiguration är en optimal mellanlösning mellan en värdkonfiguration (ASP) och internalisering. De utåtriktade komponenterna utförs på en"server med mellanleverantörer" på Adobe Campaign.<br /> </td> 
   <td> Mid-sourcing </td> 
   <td> Valfritt, <a href="../../installation/using/mid-sourcing-server.md">Läs mer</a> </td> 
  </tr> 
  <tr> 
   <td> ACS Connector<br /> </td> 
   <td> Bridge Adobe Campaign v7 och Adobe Campaign Standard. Det är en integrerad funktion i Campaign v7 som automatiskt återger data till Campaign Standard och kombinerar det bästa av båda programmen. <br /> </td> 
   <td> Marknadsföring </td> 
   <td> Valfritt, <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Läs mer</a> </td> 
  </tr> 
 </tbody> 
</table>

### Paket för meddelandecenter {#message-center-package}

Om du vill lägga till en leveranskanal (mobilkanal, mobilappskanal osv.) måste detta utföras innan du installerar paketet Message Center. Om du har startat ett Message Center-projekt i e-postkanalen måste du, mitt i projektet, lägga till en ny kanal enligt följande:

1. Installera den kanal du vill använda, till exempel **mobilkanalen**, med hjälp av guiden för paketimport ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Importera filen ( **[!UICONTROL Tools > Advanced > Import package > File]**) och välj:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. I **[!UICONTROL XML data content to import]** behålls endast leveransmallen för Message Center som motsvarar den bifogade kanalen. Om du till exempel har lagt till **mobilkanalen** ska du bara behålla det **enhetselement** som motsvarar **[!UICONTROL Mobile transactional message]** (smsTriggerMessage)-mallen. Om du har lagt till **mobilappskanalen** ska du bara behålla **transaktionsmeddelandemallarna** (iosTriggerMessage) och **transaktionsmeddelandena** för Android (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

### LINE-paket {#line-package}

För att kunna skicka leveranser via LINE-kanalen med Adobe Campaign måste du installera LINE-paketet.

Installation av LINE-paketet är en standardinstallation som beskrivs i avsnittet [Importera paket](../../platform/using/working-with-data-packages.md#importing-packages) .

![](assets/line_config_1.png)

>[!CAUTION]
>
>Leveransmallarna för LINE i Message Center är inte tillgängliga om Message Center-paketen har installerats före LINE.
