---
product: campaign
title: Installera inbyggda paket med Campaign Classic
description: Lär dig hur du installerar inbyggda Campaign-paket
feature: Installation, Application Settings
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
exl-id: 2bc077c4-ed65-4157-bfc9-df5d0442f476
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1264'
ht-degree: 1%

---

# Installera inbyggda paket med Campaign Classic{#installing-campaign-standard-packages}



## Om inbyggda paket {#campaign-standard-packages}

Inbyggda paket innehåller en uppsättning funktioner som kan installeras efter dina behov och beroende på ditt kontrakt. En fullständig lista över inbyggda Campaign-paket finns nedan.

>[!CAUTION]
>
>Du får endast installera paket som motsvarar alternativen i licensavtalet.
>
>Installationen av ett nytt paket kan påverka hela plattformen: det måste testas och valideras innan den slutgiltiga distributionen.
>
>När ett paket har installerats kan du inte avinstallera det.
>
>Kontakta Adobe för att driftsätta ett nytt inbyggt paket.

Installera ett inbyggt paket:

1. Få åtkomst till paketimportassistenten från **[!UICONTROL Tools > Advanced > Import package]** i Adobe Campaign klientkonsol.
1. Välj **[!UICONTROL Install a standard package]**.
1. Markera de paket som du vill installera i paketlistan.
   >[!NOTE]
   >
   >När ett paket är nedtonat innebär det att det redan är installerat eller att det inte är kompatibelt med din instans. Kompatibiliteten beskrivs i tabellen nedan.
1. Klicka på **[!UICONTROL Next]** och sedan på **[!UICONTROL Start]** för att starta paketinstallationen.

   När paketen har installerats visas **100%** i förloppsindikatorn och följande meddelande visas i installationsloggarna: **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** installationsfönstret.

Paketen är nu installerade.

### Lista över färdiga paket {#list-of-standard-packages}

I följande tabell visas alla inbyggda Campaign-paket.

<table> 
 <thead> 
  <tr> 
   <th> Paket </th> 
   <th> Beskrivning </th> 
   <th> Instanstyp </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Leverans<br /> </td> 
   <td> Övervakar leveranser och eventuella problem som uppstår när meddelanden skickas. <a href="../../delivery/using/about-delivery-monitoring.md">Läs mer</a><br /> </td> 
   <td> Alla</td> 
  </tr> 
  <tr> 
   <td> Marknadsföringskampanjer (kampanj)<br /> </td> 
   <td> Definierar, optimerar, kör och analyserar kommunikation och marknadsföringskampanjer. <a href="../../campaign/using/designing-marketing-campaigns.md">Läs mer</a><br /> </td> 
   <td> Marknadsföring</td>
  </tr> 
  <tr> 
   <td> Marknadsföringsresurser (MRM)<br /> </td> 
   <td> Kontrollerar marknadsföringsåtgärder i ett samverkansbaserat läge genom att tillhandahålla hantering och spårning av uppgifter, budget och marknadsföringsresurser. <a href="../../mrm/using/about-marketing-resource-management.md">Läs mer</a> <br /> </td> 
   <td> Marknadsföring</td> 
  </tr> 
  <tr> 
   <td> Erbjudandemotor (interaktion)<br /> </td> 
   <td> Svarar i realtid under en interaktion med en viss kontakt (en kund eller ett visst mål) genom att göra dem till ett eller flera anpassade erbjudanden.  Valfritt. <a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">Läs mer</a> <br /> </td> 
   <td> Alla<br /> </td> 
  </tr> 
  <tr> 
   <td> Kontroll över erbjudandemotorn med körningsinstansen. Valfritt.<br /> </td> 
   <td> Paket som ska installeras på kontrollinstansen för erbjudandemotorn (interaktion). <a href="../../interaction/using/distributed-architectures.md#packages-configuration">Läs mer</a> </td> 
   <td> Marknadsföring<br /> </td>  
  </tr> 
  <tr> 
   <td> Erbjud motor för körningsinstanser. Valfritt.<br /> </td> 
   <td> Paket som ska installeras på körningsinstanser för erbjudandemotorn (interaktion). <a href="../../interaction/using/distributed-architectures.md">Läs mer</a> </td> 
   <td> Mid, körning <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Sociala nätverk (social marknadsföring) <br /> </td> 
   <td> Synkroniserar Adobe Campaign med X (tidigare Twitter) och Facebook. <a href="../../social/using/about-social-marketing.md">Läs mer</a> <br /> </td> 
   <td> Alla</td> 
  </tr> 
  <tr> 
   <td> Kontroll av transaktionsmeddelande (Message Center - Control)<br /> </td> 
   <td> Hanterar utlösarmeddelanden som genereras från händelser som utlöses från informationssystem. Valfritt. <a href="../../message-center/using/about-transactional-messaging.md">Läs mer</a> <br /> </td> 
   <td> Marknadsföring<br /> </td> 
  </tr> 
  <tr> 
   <td> Körning av transaktionsmeddelande (Message Center - Execution) <br /> </td> 
   <td> Säkerställer högre tillgänglighet och bättre lasthantering. Valfritt. <a href="../../message-center/using/about-transactional-messaging.md">Läs mer</a><br /> </td> 
   <td> Körning<br /> </td>
  </tr> 
  <tr> 
   <td> LINE-kanal <br /> </td> 
   <td> Skickar leveranser via LINE-kanalen med Adobe Campaign. Valfritt. Transaktionsmeddelanden (Message Center-paket) är obligatoriskt. <a href="../../delivery/using/line-channel.md">Läs mer</a> <br /> </td> 
   <td> Alla<br /> </td> 
  </tr> 
  <tr> 
   <td> Direktreklam, kanal<br /> </td> 
   <td> Skickar leveranser via direktreklamkanalen med Adobe Campaign. Valfritt. <a href="../../delivery/using/about-direct-mail-channel.md">Läs mer</a><br /> </td> 
   <td> Alla<br /> </td>
  </tr> 
  <tr> 
   <td> Mobilkanal (SMS) <br /> </td> 
   <td> Skickar leveranser via Mobile/SMS-kanalen med Adobe Campaign. Valfritt. <a href="../../delivery/using/sms-channel.md">Läs mer</a> <br /> </td> 
   <td> Alla<br /> </td> 
  </tr> 
   <tr> 
   <td> Telefonkanal <br /> </td> 
   <td> Skickar leveranser via telefonkanalen med Adobe Campaign. Används för callcenter. Valfritt. <a href="../../delivery/using/communication-channels.md">Läs mer</a> <br /> </td> 
   <td> Alla<br /> </td> 
  </tr> 
  <tr> 
   <td> Mobilappskanal<br /> </td> 
   <td> Använder Adobe Campaign-plattformen för att skicka personaliserade meddelanden till iOS- och Android-terminaler via appar. Valfritt. <a href="../../delivery/using/about-mobile-app-channel.md">Läs mer</a> <br /> </td> 
   <td> Alla<br /> </td> 
  </tr> 
  <tr> 
   <td> Innehållshanteraren <br /> </td> 
   <td> Skapar återkommande nyhetsbrev eller webbplatser och validerar och publicerar sedan dina meddelanden. <a href="../../delivery/using/about-content-management.md">Läs mer</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> Onlineundersökningar (Survey Manager)<br /> </td> 
   <td> Skapar och hanterar onlineformulär för att lägga till eller ändra profilinformation, för att prenumerera, för att avbeställa eller för att fylla i ett tävlingsformulär. Valfritt. <a href="../../surveys/using/about-surveys.md">Läs mer</a> <br /> </td> 
   <td> Marknadsföring<br /> </td> 
  </tr> 
  <tr> 
   <td> Marknadsföringsanalys<br /> </td> 
   <td> Gör att du kan analysera och mäta data, beräkna statistik, förenkla och optimera framtagning och beräkning av rapporter. Du kan också skapa rapporter och skapa målpopulationer. Valfritt. <a href="../../reporting/using/ac-cubes.md">Läs mer</a><br /> </td> 
   <td> Marknadsföring<br /> </td> 
  </tr> 
  <tr> 
   <td> Svarshanteraren <br /> </td> 
   <td> Mäter framgången och lönsamheten för marknadsföringskampanjer eller erbjuder förslag för alla kommunikationskanaler.  Valfritt. <a href="../../response/using/about-response-manager.md">Läs mer</a> <br /> </td> 
   <td> Marknadsföring<br /> </td> 
  </tr> 
  <tr> 
   <td> Åtkomst till externa data (federerad dataåtkomst)<br /> </td> 
   <td> Tillhandahåller alternativet FDA (Federated Data Access) för att bearbeta information som lagras i en eller flera externa databaser så att du kan komma åt externa data utan att ändra datastrukturen i Adobe Campaign.  Valfritt. <a href="../../workflow/using/accessing-an-external-database-fda.md">Läs mer</a> <br /> </td> 
   <td> Alla<br /> </td> 
  </tr> 
  <tr> 
   <td> Kampanjoptimering <br /> </td> 
   <td> Kontrollerar, filtrerar och övervakar sändningen av leveranser så att de skickade meddelandena bäst uppfyller kundernas behov och förväntningar, i enlighet med företagets kommunikationspolicy. Valfritt. <a href="../../campaign-opt/using/about-campaign-typologies.md">Läs mer</a> <br /> </td> 
   <td> Marknadsföring<br /> </td> 
  </tr> 
  <tr> 
   <td> Leveransövervakning (e-postleverans)<br /> </td> 
   <td> Mäter framgången för era kampanjer och når mottagarnas inkorg utan studsar eller markeras som skräppost. Valfritt. <a href="../../delivery/using/about-deliverability.md">Läs mer</a> <br /> </td> 
   <td> Alla </td> 
  </tr> 
  <tr> 
   <td> Kuponghantering<br /> </td> 
   <td> Skapar en uppsättning kuponger att lägga till i kommande marknadsföringserbjudanden. Valfritt. <a href="../../delivery/using/personalized-coupons.md">Läs mer</a> <br /> </td> 
   <td> Marknadsföring<br /> </td> 
  </tr> 
  <tr> 
   <td> Inkorgsåtergivning (IR)<br /> </td> 
   <td> Gör att du kan förhandsgranska meddelandet som skickas i olika sammanhang där det kan tas emot och kontrollera kompatibiliteten i de flesta datorer och program. Valfritt. <a href="../../delivery/using/inbox-rendering.md">Läs mer</a><br /> </td> 
   <td> Marknadsföring<br /> </td> 
  </tr> 
  <tr> 
   <td> Central/lokal marknadsföring (distribuerad marknadsföring)<br /> </td> 
   <td> Implementerar samverkanskampanjer mellan centrala enheter (huvudkontor, marknadsföringsavdelningar osv.) och lokala enheter (försäljningsställen, regionala myndigheter osv.). Valfritt. <a href="../../distributed/using/about-distributed-marketing.md">Läs mer</a><br /> </td> 
   <td> Marknadsföring </td> 
  </tr> 
  <tr> 
   <td> CRM-kopplingar<br /> </td> 
   <td> Tillhandahåller olika CRM-anslutningar för att länka din Adobe Campaign-plattform till dina tredjepartssystem.  <a href="../../platform/using/crm-connectors.md">Läs mer</a> <br /> </td> 
   <td> Marknadsföring</td> 
  </tr> 
  <tr> 
   <td> Web Analytics-anslutningar<br /> </td> 
   <td> Gör att Adobe Campaign och Adobe Analytics kan interagera via Web Analytics-anslutningspaketet. Inte kompatibelt med Transactional Messaging (Message Center-paket). <a href="../../integrations/using/gs-aa.md">Läs mer</a><br /> </td> 
   <td> Marknadsföring </td> 
  </tr> 
  <tr> 
   <td> AEM-integrering <br /> </td> 
   <td> Gör att du kan hantera innehållet i e-postutskick och formulär direkt i Adobe Experience Manager för att dra nytta av AEM funktioner för innehållsredigering och Adobe Campaign leveranskapacitet. <a href="../../integrations/using/about-adobe-experience-manager.md">Läs mer</a> <br /> </td> 
   <td> Marknadsföring</td> 
  </tr> 
  <tr> 
   <td> Integrering av delade målgrupper i Adobe Experience Cloud<br /> </td> 
   <td> Gör att ni kan utbyta och dela målgrupper/segment med Adobe Experience Cloud lösningar och appar. Kräver IMS. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Läs mer</a> <br /> </td> 
   <td> Marknadsföring<br /> </td> 
  </tr> 
  <tr> 
   <td> Integrering med Adobe Experience Cloud<br /> </td> 
   <td> Används för att importera och exportera målgrupper/segment från olika Adobe Experience Cloud-lösningar till Adobe Campaign. Valfritt. <a href="../../integrations/using/configuring-ims.md#installing-the-package">Läs mer</a> </td> 
   <td> Marknadsföring</td> 
  </tr> 
  <tr> 
   <td> Skyddsförordningen för personuppgifter<br /> </td> 
   <td> Innehåller ytterligare funktionalitet som hjälper dig att följa sekretesskraven i Campaign Classic. <a href="https://helpx.adobe.com/se/campaign/kb/acc-privacy.html">Läs mer</a> <br /> </td> 
   <td> Alla</td> 
  </tr> 
  <tr> 
   <td> Överför till medelkälla <br /> </td> 
   <td> Detaljerar installation och konfiguration av en server med mellanlagring samt distributionen av en instans som gör det möjligt för tredje part att skicka meddelanden i mellankälläge. Valfritt. <a href="../../installation/using/mid-sourcing-server.md">Läs mer</a> <br /> </td> 
   <td> Marknadsföring </td> 
  </tr> 
  <tr> 
   <td> Plattformen <br /> för mellanleverantörer </td> 
   <td> Denna konfiguration är en optimal mellanlösning mellan en värdkonfiguration (ASP) och internalisering. Utomvända körningskomponenter utförs på en"server med mellanleverantörer" på Adobe Campaign. Valfritt. <a href="../../installation/using/mid-sourcing-server.md">Läs mer</a> <br /> </td> 
   <td> Mid-sourcing </td> 
  </tr> 
  <tr> 
   <td> Stöd för AMP<br /> </td> 
   <td> Gör att du kan använda den nya interaktiva AMP för e-postformat och skicka dynamiska e-postmeddelanden. Valfritt. <a href="../../delivery/using/defining-interactive-content.md">Läs mer</a> <br /> </td> 
   <td> Alla </td> 
  </tr> 
  <tr> 
   <td> ACS-anslutning (borttagen)<br /> </td> 
   <td> Bridges Adobe Campaign v7 and Adobe Campaign Standard. Det är en integrerad funktion i Campaign v7 som automatiskt återger data till Campaign Standarden och kombinerar det bästa av båda programmen. Valfritt.<br /> </td> 
   <td> Marknadsföring </td> 
  </tr> 
 </tbody> 
</table>

### Paket för meddelandecenter {#message-center-package}

Du måste installera leveranskanaler (e-post, mobilkanal, mobilappskanal, LINE osv.) innan du installerar Transactional Messaging (Message Center-paket). Om du har startat ett meddelandecenterprojekt som bara är till för e-post och behöver lägga till en ny kanal i efterhand måste du följa dessa steg:

1. Installera den nya kanalen, till exempel **Mobile-kanalen**, med hjälp av paketimportassistenten ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Importera filen ( **[!UICONTROL Tools > Advanced > Import package > File]**) och välj:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. I **[!UICONTROL XML data content to import]** sparar du bara den leveransmall för meddelandecentret som motsvarar den relaterade kanalen. Om du till exempel har lagt till **mobilkanalen** ska du bara behålla elementet **entities** som motsvarar mallen **[!UICONTROL Mobile transactional message]** (smsTriggerMessage). Om du har lagt till **Mobile App Channel** ska du bara behålla **iOS-transaktionsmeddelandemallar** (iosTriggerMessage) och **Android-transaktionsmeddelanden** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)


### Kanalinställningar för [!DNL LINE]{#line-package}

Om du vill konfigurera [!DNL LINE]-kanalen måste du först installera paketet [!DNL LINE].

När det gäller en mellankällskonfiguration måste du:

* Installera paketet [!DNL LINE] på både Marketing och MID-instansen

* Konfigurera det [!DNL LINE] externa kontot på mkt-instansen så att det pekar på mittinstansen genom att ändra leveransläget. [Läs mer](../../delivery/using/line-channel.md#configure-line-external)

* Konfigurera autentiseringsuppgifterna [!DNL LINE] i det externa kontot på MID-instansen.

>[!CAUTION]
>
>Leveransmallarna för Message Center för [!DNL LINE]-kanalen är inte tillgängliga om Message Center-paketen har installerats före [!DNL LINE].