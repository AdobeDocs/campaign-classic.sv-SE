---
product: campaign
title: Dokumentation om Adobe Campaign Classic v7-uppdateringar
description: Den här sidan beskriver alla nya funktioner och uppdateringar i dokumentationen om Adobe Campaign Classic
feature: Release Notes
role: User
level: Beginner
exl-id: 07c1f4a3-cf16-4a9b-b402-e13258799f91
source-git-commit: c736ac1cda9490548f1e4b56142d61fccaca5c4a
workflow-type: tm+mt
source-wordcount: '3764'
ht-degree: 98%

---

# Dokumentationsuppdateringar{#documentation-updates}

Den här sidan visar alla nya funktioner och dokumentationsuppdateringar efter månad och version av Campaign.

Se [Versionsinformationen för Adobe Campaign Classic](../../rn/using/latest-release.md) beträffande versionsrelaterade uppdateringar.

## 2024

### April 2024 {#apr-2024}

Ett varningsmeddelande har lagts till om att användare har skapats med Adobe Identity Management System (IMS). [Läs mer](../../platform/using/access-management.md)

Alternativ saknas för arbetsflödesaktiviteten för webbhämtning har lagts till. [Läs mer](../../workflow/using/web-download.md)

Ett varningsmeddelande har lagts till i **Ändra dimension** och **Ändra datakälla** aktiviteter om hur de används i ett arbetsflöde. [Läs mer](../../workflow/using/change-data-source.md)

### Mars 2024 {#mar-2024}

Konfigurationsavsnittet för mobilappar har uppdaterats för tokenbaserad anslutning till APN:er i iOS. [Läs mer](../../delivery/using/configuring-the-mobile-application.md#creating-ios-app)

### Januari 2024 {#jan-2024}

Information har lagts till om hur standardfältet postalAddress för direktreklam definieras och varför det är viktigt att se till att adresserna är fullständiga. [Läs mer](../../delivery/using/about-direct-mail-channel.md)

Lade till en ny sida om hur du konfigurerar SMS-kanalen i Campaign i en mid-sourcingsinfrastruktur. [Läs mer](../../delivery/using/sms-set-up-mid.md)

## 2023

### December 2023 {#dec-2023}

JWT (JSON Web Tokens) håller på att tas ur bruk och ersätts med OAuth. Övergången genomförs stegvis i de kommande versionerna av Campaign och dokumentationen kommer att uppdateras för att återspegla dessa uppdateringar.

Tillagd konfiguration av externt FDA-konto för Amazon Redshift. [Läs mer](../../installation/using/configure-fda-redshift.md)

### Augusti 2023 {#aug-2023}

En begränsning har lagts till för att ange att du inte kan använda Adobe Campaign för att dekomprimera zippade filer som är större än 4 GB. [Läs mer](../../platform/using/unzip-decrypt.md)

### April 2023 {#apr-2023}

Lade till ett tekniskt dokument om hur du aktiverar Microsoft Edge Chromium på lokala/hybridmiljöer. [Läs mer](../../technotes/using/edge-chromium.md)

### Mars 2023 {#mar-2023}

Uppdaterat avsnitt med versionsinformation med förbättringar och korrigeringar för 7.3.3. [Läs mer](latest-release.md)


+++ 2022


## November 2022 {#nov-2022}

Uppdaterat avsnitt med versionsinformation med 7.3.2-förbättringar och korrigeringar. [Läs mer](latest-release.md)

Uppdaterad kompatibilitetsmatris med stöd för Teradata 17. [Läs mer](compatibility-matrix.md)

Fil- och resurshanteringsavsnittet har uppdaterats med ytterligare information om attributet **uploadWhiteList**. [Läs mer](../../installation/using/file-res-management.md)

Dokumentationen om säkerhetszoner har uppdaterats med ytterligare information om attributet **allowDebug**. [Läs mer](../../installation/using/security-zones.md#recommendations)

Migreringshandboken har uppdaterats. Referenser till Adobe Campaign-versioner som inte stöds har tagits bort. [Läs mer](../../migration/using/about-migration.md)


## Juli 2022 {#july-2022}

Övergången till den nya levererbarhetsservern beskrivs i ett nytt tekniskt dokument. [Läs mer](../../technotes/using/deliverability-server.md)

**Dokumentationsuppdateringar för version 7.3.1**

Uppdaterad kompatibilitetsmatris. [Läs mer](compatibility-matrix.md)

Uppdaterat avsnitt med versionsinformation. [Läs mer](rn-overview.md)

Tidskänsliga meddelanden med iOS 15. [Läs mer](../../delivery/using/create-notifications-ios.md)


## Mars 2022 {#mar-2022}

Lade till en detaljerad beskrivning av alternativet **[!UICONTROL Test SMTP delivery]**. [Läs mer](../../delivery/using/steps-sending-the-delivery.md#delivery-additiona-parameters)

Sidan Kom igång med uppgraderingar har uppdaterats för att klargöra riktlinjerna för uppgradering av Campaign Console. [Läs mer](../../rn/using/rn-overview.md)

Den nya builden (v7.2.2) för Campaign är nu tillgänglig. [Läs mer](../../rn/using/latest-release.md)

<!--Added troubleshooting information related to the ACS connector. [Read more](../../integrations/using/troubleshooting-the-acs-connector.md)-->

Äldre PostgreSQL-versioner som har nått slutet av livscykeln har lagts till på sidan [Inaktuella och borttagna funktioner](../../rn/using/deprecated-features.md#dbe-eol).

## Februari 2022 {#february-2022}

Uppdaterade aktivitetsavsnittet **Filöverföring** med en påminnelse om att manuellt övervaka storleken på det arkiverade innehållet i SFTP-katalogen om alternativet **Radera källfilerna efter överföringen** inte är markerat. [Läs mer](../../workflow/using/file-transfer.md#properties)

Avsnittet Karantän jämfört med Blockeringslista har förtydligats. [Läs mer](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)

Avsnitten om hur du skickar en adress till karantän och hur du tar bort adresser från karantänlistan har uppdaterats. [Läs mer](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

En bästa praxis för arbetsflöde har lagts till för att rekommendera att inte utföra flera stoppförfrågningar på samma arbetsflöde. [Läs mer](../../workflow/using/workflow-best-practices.md)

Information tillagd om hur du stoppar återkommande leveranser från att köras i en kampanj. [Läs mer](../../workflow/using/recurring-delivery.md)

## Januari 2022 {#january-2022}

**Dokumentationsuppdateringar kommer med versionen 7.2.1**

Uppdaterad kompatibilitetsmatris. [Läs mer](compatibility-matrix.md)

Uppdaterat avsnitt med versionsinformation. [Läs mer](rn-overview.md)

Uppdaterad konfiguration av externt FDA-konto för Snowflake. [Läs mer](../../installation/using/configure-fda-snowflake.md)

Uppdaterad konfiguration av externt FDA-konto för Azure Synapse Analytics. [Läs mer](../../installation/using/configure-fda-synapse.md#azure-external)

Google BigQuery FDA Connector har uppdaterats. [Läs mer](../../installation/using/configure-fda-google-big-query.md)

Åtgärdsaktiviteterna Microsoft CRM, Salesforce och Oracle CRM On Demand har tagits bort från dokumentationen efter deras utfasning.

Det nya alternativet **Avbryt vid fel** har lagts till i avsnittet Felhantering i arbetsflöde. [Läs mer](../../workflow/using/advanced-parameters.md#in-case-of-errors)

Lade till ett gruppuppdateringsalternativ i CRM-anslutningsaktiviteten. [Läs mer](../../workflow/using/crm-connector.md)

+++

+++ 2021

## December 2021{#dec-2021}

Versionsinformation om Campaign Classic v7 har omorganiserats för att förenkla navigeringen. [Läs mer](rn-overview.md)

Dokumentationen om formulärversionen i Campaign har uppdaterats och förbättrats. [Läs mer](../../configuration/using/editing-forms.md)

CentOs 8 har nått slutet av sin livscykel och är nu inaktuell i Adobe Campaign Classic. [Läs mer](deprecated-features.md)

## November 2021{#nov-2021}

Lade till en begränsning för inkommande SMS (MO). [Läs mer](../../delivery/using/sms-protocol.md#multipart)

Uppdaterade logguppgifterna om migreringsprocessen för CRM-anslutningsdistribution. [Läs mer](../../migration/using/testing-the-migration.md#verification-process)

Lade till krav om IMS-behörigheter för att implementera integrering mellan Adobe Campaign och Adobe Analytics. [Läs mer](../../platform/using/adobe-analytics-provisioning.md)

Uppdaterade datumet för slutet på livscykeln för Adobe Analytics Data Connector från den 1 mars 2022 till den 17 augusti 2022. [Läs mer](deprecated-features.md)

Lade till en länk till den mobila SDK-dokumentationen för Adobe Experience Platform för att förklara hur du konfigurerar Campaign-tillägget i Adobe Launch. [Läs mer](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)

Lade till ett avsnitt om hur du använder JavaScript för att beräkna värden, utbyta data och utföra specifika åtgärder med SOAP-anrop.[Läs mer](../../workflow/using/javascript-scripts-and-templates.md)

Lade till exempel på implementering av JavaScript-koder i arbetsflöden. [Läs mer](../../workflow/using/javascript-in-workflows.md)


## Oktober 2021{#oct-2021}

Befintliga tekniska anmärkningar har grupperats i det nya avsnittet **Technote**.

Sidan **Rekommendationer för storleksändring av maskinvara** har uppdaterats och lagts till i avsnittet **Technotes**. [Läs mer](../../technotes/using/hardware-sizing.md)

## September 2021{#sept-2021}

**Dokumentationsuppdateringar kommer med utgåvan 21.1.4**

Diagramtypen **Mätare** har tagits bort.

Skärmbilder och parametrar för rapporter och webbprogram har uppdaterats efter att Adobe Flash har tagits bort.

Beskrivningen av de [tekniska arbetsflödet för fakturering](../../production/using/monitoring-processes.md#billing-report) har uppdaterats med ett nytt skyddsförslag.

## Augusti 2021{#aug-2021}

Ny arbetsflödesaktivitet har lagts till: Ändra datakälla – [Läs mer](../../workflow/using/change-data-source.md)

Tillämplighetsemblem har lagts till på dokumentationssidorna: **Gäller endast v7** för Campaign Classic v7-funktioner och **gäller för v7 och v8** för gemensamma funktioner.

Ett meddelande har lagts till om integrationen mellan Campaign och AEM Assets, som har tagits bort från och med Adobe Experience Manager 6.4. [Läs mer](../../integrations/using/configuring-access-to-assets.md)


## Juli 2021 {#july-2021}

[Campaign version 21.1.3](../../rn/using/latest-release.md#release-21-1-3-build-9330) har flyttats till Allmän tillgänglighet (GA).


## Juni 2021 {#june-2021}

Avsnittet **Transaktionsmeddelanden** har organiserats om och förtydligats med ett nytt Kom igång-avsnitt, inklusive ett [förbättrat schema](../../message-center/using/about-transactional-messaging.md#transactional-messaging-operating-principle) för att ge en bättre förståelse av processen. [Läs mer](../../message-center/using/about-transactional-messaging.md)

**Dokumentationsuppdateringar kommer med utgåvan 21.1.3**

Integrering med Adobe Journey Orchestration – [Läs mer](https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=sv). Ett steg-för-steg-exempel visas på [den här sidan](https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=sv)

Förbättringar av LINE-kanaler – [Läs mer](../../delivery/using/line-channel.md)

Ny Vertica Analytics FDA-anslutning – [Läs mer](../../installation/using/configure-fda-vertica.md)

Ny Google BigQuery FDA connector – [Läs mer](../../installation/using/configure-fda-google-big-query.md)

Den tekniska arbetsflödesbeskrivningen Fakturering (fakturering) omfattar nu de uppgifter som ursprungligen utfördes av Antal aktiva faktureringsprofiler (billingActiveContactCount). [Läs mer](../../workflow/using/about-technical-workflows.md)

## Maj 2021 {#may-2021}

Rapportdokumentationen för värmekartor för arbetsflöden har uppdaterats och förbättrats. [Läs mer](../../workflow/using/heatmap.md)

Kraven för Campaign Client Console har uppdaterats i kompatibilitetsmatrisen. [Läs mer](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

Steg för steg-installationen av Campaign Client Console har förbättrats och klargjorts. [Läs mer](../../installation/using/installing-the-client-console.md)

Ett nytt tekniskt meddelande har skapats om signeringsproblemet för spårade URL:er. [Läs mer](../../technotes/using/tracked-urls.md)

## April 2021 {#april-2021}

Ett nytt avsnitt har lagts till som handlar om hur man arbetar med källor och destinationer i Adobe Experience Platform för att dela data mellan Campaign Classic och Adobes kunddataplattform i realtid (RTCDP). [Läs mer](../../integrations/using/get-started-sources-destinations.md)

Ett nytt tekniskt meddelande har skapats för att beskriva hur man uppdaterar studskompetens efter ett avbrott i en internetleverantör. [Läs mer](../../delivery/using/update-bounce-qualification.md)

## Mars 2021 {#march-2021}

[Avsnittet Kom igång med SMS](../../delivery/using/sms-channel.md) har organiserats om och förbättrats. Nu kan läsa om hur du [konfigurerar SMS-kanalen](../../delivery/using/sms-set-up.md), [skapar ett SMS](../../delivery/using/sms-create.md) samt [skickar och spårar SMS](../../delivery/using/sms-send.md) i dedikerade avsnitt.

Sidan Hjälp- och supportalternativ för Campaign Classic har integrerats i huvuddokumentationen. [Läs mer](../../support.md)

Ett nytt avsnitt har lagts till med god praxis och kontroller gällande säkerhet och sekretess. [Läs mer](../../installation/using/get-started-security-privacy.md)

[Kapitlet om behörighetshantering](../../platform/using/access-management.md) har förbättrats och delats upp i avsnitt, inklusive information om [operatörer](../../platform/using/access-management-operators.md), [operatörsgrupper](../../platform/using/access-management-groups.md), [namngivna rättigheter](../../platform/using/access-management-named-rights.md) och [mapphantering](../../platform/using/access-management-folders.md).

Läs om hur du skapar och hanterar dina kampanjer via de här nya sidorna:
* [Skapa och konfigurera kampanjmallar](../../campaign/using/marketing-campaign-templates.md)
* [Leveranser av marknadsföringskampanjer](../../campaign/using/marketing-campaign-deliveries.md)
* [Välj målgruppen för dina kampanjer](../../campaign/using/marketing-campaign-target.md)
* [Hantera associerade dokument](../../campaign/using/marketing-campaign-assets.md)
* [Konfigurera och hantera godkännandeprocessen](../../campaign/using/marketing-campaign-approval.md)

Information har lagts till i avsnittet om **[!UICONTROL Advanced JavaScript]**-aktivitet om hur du använder metoden task.setCompleted() för att avsluta uppgiften och förhindra framtida återkallningar. [Läs mer](../../workflow/using/sql-code-and-javascript-code.md#adv-js-code-desc)

Avsnittet [Levererbarhet](../../delivery/using/about-deliverability.md) har uppdaterats och innehåller nu länkar till den nya [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv). All generisk information om levererbarhet som kan tillämpas på olika Adobe-lösningar har flyttats till [bilagan för Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/general-resources.html?lang=sv#additional-resources).

## Februari 2021 {#release-21.1}

**Dokumentationsuppdateringar kommer med utgåvan 21.1**

Den nya funktionen **Feedback via e-post** (privat beta) finns dokumenterad [här](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service).

Avsnittet **Serverkonfigurationsfilen** har uppdaterats med de konfigurationsparametrar som behövs för att Campaign ska kunna ansluta till en annan tjänst med IMS. [Läs mer](../../installation/using/the-server-configuration-file.md#ims)

I listan över leveransstatus har beskrivningen av **Har tagits med i beräkningen av tjänsteleverantören** uppdaterats: den här statusen används nu även för e-postleveranser som skickas med tjänsten [Feedback via e-post](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service). [Läs mer](../../delivery/using/delivery-statuses.md#list-delivery-statuses)

De kortkommandon som finns på den nya inloggningsskärmen för att ansluta till Adobe Campaign är nu dokumenterade. [Läs mer](../../platform/using/launching-adobe-campaign.md#connecting-to-adobe-campaign)

**Andra uppdateringar**

Ett nytt avsnitt har lagts till med detaljerad information om hur A/B-tester kan utföras med arbetsflöden. [Läs mer](../../delivery/using/get-started-a-b-testing.md)

Avsnittet Avancerad MTA i Adobe Campaign har flyttats [hit](../../delivery/using/sending-with-enhanced-mta.md).

En ny sida har lagts till för att ge en översikt över spårningsfunktionerna i [!DNL Campaign Classic]. [Läs mer](../../delivery/using/about-message-tracking.md)

Ett felsökningsavsnitt har lagts till för att hjälpa dig att lösa vanliga problem med spårning. [Läs mer](../../delivery/using/tracking-troubleshooting.md)

Avsnittet **Skicka ett e-postmeddelande** har ordnats om och förtydligats med nya underavsnitt. [Läs mer](../../delivery/using/sending-messages.md)

Information har lagts till om hur du lägger till länkar i e-postmeddelanden som kan personaliseras och som har stöd för spårning. [Läs mer](../../delivery/using/tracking-personalized-links.md).

## Januari 2021 {#jan-2021}

Aktivitetsavsnittet **[!UICONTROL Fork]** har berikats med bästa praxis. [Läs mer](../../workflow/using/fork.md)

Avsnittet **CRM-kopplingar** har uppdaterats, förbättrats och omorganiserats. [Läs mer](../../platform/using/crm-connectors.md).

Steg för att ansluta **Adobe Campaign och Microsoft Dynamics** beskrivs nu på en egen sida. [Läs mer](../../platform/using/crm-ms-dynamics.md).

Oracle On Demand-API:et är nu föråldrat som en CRM-koppling till Campaign. [Läs mer](../../rn/using/deprecated-features.md).

Läs [här](../../production/using/locate-tomcat-version.md) om hur du tar reda på den aktuella versionen av den inbäddade Tomcat-webbservleten som används i en instans i Adobe Campaign.

Listan över tekniska arbetsflöden med tillhörande paket har förbättrats och centraliserats till en enda sida. [Läs mer](../../workflow/using/about-technical-workflows.md)

Avsnittet Felsökning i användarhandboken **Övervakning** har omorganiserats och förbättrats med en landningssida. [Läs mer](../../production/using/troubleshooting.md).

Det finns ett nytt avsnitt gällande att **importera och exportera data** med nya sidor som rör bästa praxis för arbetsflöden, datakomprimering, kryptering och import. [Läs mer](../../platform/using/get-started-data-import-export.md)

+++


+++ 2020


## December 2020 {#dec-2020}

Avsnittet **Leveransövervakning** har omorganiserats med tematiska ämnen. [Läs mer](../../delivery/using/about-delivery-monitoring.md)

Ett användningsfall har lagts till om hur du lägger till avsändarnas IP-adresser i leveransloggarna. [Läs mer](../../delivery/using/delivery-dashboard.md#use-case)

Frågor och svar om sekretess har flyttats till [det här avsnittet](../../platform/using/privacy-faq.md).

Ett användningsfall har lagts till om hur du använder **[!UICONTROL Deduplication]**-aktivitetens funktioner för sammanslagning. [Läs mer](../../workflow/using/deduplication-merge.md)

Protokoll- och inställningssidan med en fullständig beskrivning beträffande SMS-kopplingen finns nu tillgänglig [här](../../delivery/using/sms-protocol.md).

Information har lagts till i avsnittet **Transaktionsmeddelanden** som varnar för att händelsemapparna inte får anges som vyer över körningsinstanserna för att undvika problem med åtkomsträttigheter. [Läs mer](../../message-center/using/about-event-processing.md#event-collection)

## November 2020 {#nov-2020}

Översikten över kampanjdatamodellen har förbättrats och omorganiserats. [Läs mer](../../configuration/using/about-data-model.md).

Konfiguration av externa konton har flyttats till [det här avsnittet](../../installation/using/external-accounts.md).

Dokumentationen om federerad dataåtkomst (FDA) i Campaign har förbättrats med information för varje extern databaskonfiguration och flyttats till [det här avsnittet](../../installation/using/about-fda.md).

Campaign version 20.2.3 har flyttats till Allmän tillgänglighet (GA).

Sektionen om sekretess har flyttats och berikats med två nya sidor: [Sekretesshantering](../../platform/using/privacy-management.md) och [Hantering av förfrågningar om användarens information](../../platform/using/privacy-requests.md).

En anteckning har lagts till på sidan med serverkonfiguration gällande mid-sourcing för att specificera att det externa kontots interna namn inte bör uppdateras när servern väl har konfigurerats. [Läs mer](../../installation/using/mid-sourcing-server.md)

Information har lagts till om syntaxen som ska användas när en sökväg till en extern SFTP-server anges. [Läs mer](../../platform/using/sftp-server-usage.md#external-SFTP-server)

Avsnittet Personuppgifter och personer har uppdaterats med ett användningsfall för att illustrera hur de olika personerna interagerar när det gäller sekretess. [Läs mer](../../platform/using/privacy-and-recommendations.md#use-case-scenario)

Ett nytt avsnitt som listar vanliga frågor och svar gällande integritet har lagts till. [Läs mer](../../platform/using/privacy-faq.md)

## Oktober 2020 {#oct-2020}

**Nya funktioner i version 20.3**

Förbättrade push-meddelanden för iOS – [läs mer](../../delivery/using/configuring-the-mobile-application.md)

Förbättrade push-meddelanden för Android – [läs mer](../../delivery/using/configuring-the-mobile-application-android.md)

**Andra dokumentationsuppdateringar som följer med denna version**

Kompatibilitetsmatrisen har uppdaterats. [Läs mer](../../rn/using/compatibility-matrix.md)

Sidan Inaktuella och borttagna funktioner har uppdaterats. [Läs mer](../../rn/using/deprecated-features.md)

Versionsinformation och kompatibilitetsmatris för [!DNL Gold Standard]-versionen finns nu tillgängliga på en dedikerad sida.
[Läs mer](../../rn/using/gold-standard.md).

Integrering av utlösare som ursprungligen baserades på oAUTH-autentiseringsinställningar för åtkomst till pipelines har nu ändrats och flyttats till Adobe I/O. [Läs mer](../../integrations/using/configuring-adobe-io.md)

**Andra uppdateringar**

Dokumentationssidorna har uppdaterats för att återspegla uppdateringen Tomcat 8.

Mer information har lagts till i beskrivningen i rutan ”Om” i avsnittet ”Ladda ned din version av Adobe Campaign”. [Läs mer](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)

Riktlinjer för att utföra en versionsuppgradering har lagts till i avsnittet Uppdatera Adobe Campaign Classic. [Läs mer](../../production/using/build-upgrade.md)

Vanliga frågor och svar om builduppgraderingen av Campaign har lagts till i vanliga frågor om Campaign. Läs mer [Läs mer](../../platform/using/faq-build-upgrade.md)

Campaign lokalt samt värdbaserade och hybridvärd-modeller beskrivs nu i ett särskilt avsnitt. [Läs mer](../../installation/using/hosting-models.md)

Matrisen med funktionerna i Campaign per värdmodell har uppdaterats och flyttats i installationshandboken. [Läs mer](../../installation/using/capability-matrix.md)

Avsnittet med avancerade funktioner i Campaign Reporting har förbättrats så att det beskriver hur URL-parametrar och -variabler används i anpassade rapporter. [Läs mer](../../reporting/using/advanced-functionalities.md)

Sidan med rapportegenskaper har omorganiserats och förbättrats för att underlätta konfigurationen. [Läs mer](../../reporting/using/properties-of-the-report.md)

## September 2020 {#september-2020}

En anteckning har lagts till för att specificera att antalet aktiva profiler endast är tillgängligt för marknadsföringsinstanser. [Läs mer](../../platform/using/about-profiles.md#active-profiles)

Ett nytt exempel om schemaversionen har lagts till för att länka ett fält till en befintlig referenstabell. [Läs mer](../../configuration/using/examples-of-schemas-edition.md#uc-link)

En anteckning har lagts till om användningen av ytterligare data med fröadresser vid leveranser. [Läs mer](../../delivery/using/creating-seed-addresses.md#defining-addresses)

## Augusti 2020 {#aug-2020}

Läs om de bästa metoderna för leveransdesign och att skicka med Campaign i ett särskilt avsnitt. [Läs mer](../../delivery/using/delivery-best-practices.md)

Landningssidan gällande bästa praxis för levererbarhet har förbättrats för att underlätta åtkomsten till underavsnitt. [Läs mer](../../delivery/using/about-deliverability.md)

Instruktionsvideor finns nu tillgängliga för följande ämnen:

* [Så ställer du in trötthetshantering med typologiregler och fördefinierade filter](../../campaign-opt/using/about-campaign-typologies.md)

* [Så skapar du ett e-postmeddelande i en kampanj](../../campaign/using/marketing-campaign-deliveries.md)

* [Så skapar du ett flerspråkigt nyhetsbrev med villkorligt innehåll](../../delivery/using/conditional-content.md)

* [Så konfigurerar och driftsätter du en leveransmall](../../delivery/using/creating-a-delivery-template.md)

* [Så aktiverar och använder du AMP för e-postmeddelanden](../../delivery/using/defining-interactive-content.md)

* [Så personaliserar du e-postmeddelanden med dynamiska innehållsblock](../../delivery/using/personalization-blocks.md)

* [Så personaliserar du e-postmeddelanden med personaliseringsfält](../../delivery/using/personalization-fields.md)

* [Så hanterar du frön och korrektur i ett e-postmeddelande](../../delivery/using/steps-defining-the-target-population.md)

* [Så ställer du in en återkommande leverans](../../workflow/using/recurring-delivery.md)

* [Så ställer du in en kontinuerlig leverans](../../workflow/using/continuous-delivery.md)

Information har lagts till om de kontroller och åtgärder som ska utföras när man får felet ”Det gick inte att lösa värdnamnet” efter anslutning till en FTP-server. [Läs mer](../../platform/using/sftp-server-usage.md)

Nya användningsfall har refererats i listan [Användningsfall med arbetsflöde](../../workflow/using/about-workflow-use-cases.md):

* Automatisera skapande, redigering och publicering av innehåll
* Ställa in en process för mottagningsgodkännande innan en leverans skickas
* Anropa en instansvariabel i en fråga
* Tillämpa en delad procentsats på en grupp

Aktivitetsavsnittet **[!UICONTROL AND-join]** har berikats med ytterligare information om hur det används, samt en anteckning om användningen av variabler. [Läs mer](../../workflow/using/and-join.md)

## Juli 2020 {#july-2020}

Ett användningsfall om hur man automatiskt uppdaterar en lista med en inkrementell fråga har lagts till i användningsfallen om arbetsflöde. [Läs mer](../../workflow/using/about-workflow-use-cases.md)

[Versionsinformationen](../../rn/using/latest-release.md) har omorganiseras: en [översiktssida](../../rn/using/latest-release.md) med information om buildstatus, uppgraderingsprocess, rekommendationer och viktiga länkar har lagts till. En dedikerad sida för [[!DNL Gold Standard] -versioner](../../rn/using/gold-standard.md) har också lagts till och [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md) har integrerats.

Ett nytt avsnitt har lagts till med riktlinjer gällande att övervaka Campaign Classic. [Läs mer](../../production/using/monitoring-guidelines.md)

Avsnittet Sekretess och samtycke har förbättrats med mer detaljerad information och användbara länkar. [Läs mer](../../platform/using/privacy-and-recommendations.md)

Sekretesshanteringen på sidan Campaign Classic har uppdaterats med information om fältet ”reglering” som nu är tillgängligt när du använder API:et, så att det går att konfigurera en automatisk process för förfrågan om användarens information. [Läs mer](https://helpx.adobe.com/ie/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

Sidan Översikt över integritetshantering har uppdaterats med information om Thailands lag för persondataskydd (PDPA) och Brasiliens Lei Geral de Proteção de Dados (LGPD). [Läs mer](../../platform/using/privacy-and-recommendations.md)

Information har lagts till om loggar om delarbetsflöden och beteende vid fel. [Läs mer](../../workflow/using/sub-workflow.md)

Bästa praxis har lagts till i aktivitetsavsnittet **[!UICONTROL Scheduler]**. [Läs mer](../../workflow/using/scheduler.md)

## Juni 2020 {#june-2020}

Avsnittet Ta bort en adress i karantän har uppdaterats. Detta inkluderar förtydligande av de fall där adresser automatiskt tas bort från karantänlistan. [Läs mer](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

Användningsfall har lagts till om hur data [krypteras](../../platform/using/zip-encrypt.md) och [dekrypteras](../../platform/using/unzip-decrypt.md) med Kontrollpanelen och arbetsflödena i Campaign.

Sidan för integration av utlösare i Experience Cloud och Adobe Campaign Classic har flyttats [hit](../../integrations/using/about-triggers.md).

## Juli 2020 {#release-20-2}

**Nya funktioner i version 20.2**

Stöd för uttryckssymboler – [läs mer](../../delivery/using/customizing-emoticon-list.md)

Azure Synapse FDA-koppling – [läs mer](../../installation/using/configure-fda-synapse.md)

Integritetslagar för Thailand och Brasilien – [läs mer](https://helpx.adobe.com/se/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

**Andra dokumentationsuppdateringar som följer med denna version**

Det nya alternativet för att avpublicera en mall för transaktionsmeddelanden beskrivs i [det här avsnittet](../../message-center/using/publishing-message-templates.md#template-unpublication).

De nya alternativen som gör det möjligt att ange begränsningar när du skickar e-postmeddelanden som innehåller bilder som hämtas från en personlig webbadress och bilagor har lagts till i listan med alternativ i Campaign Classic. [Läs mer](../../installation/using/configuring-campaign-options.md#delivery)

Det nya alternativet **Förbered leveransdelarna i databasen** beskrivs i [det här avsnittet](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis).

Avsnittet Validera leveransen har förtydligats och uppdaterats. [Läs mer](../../delivery/using/steps-validating-the-delivery.md)

Parametrarna för den nya mekanismen för att spåra länkad underskrift har lagts till i avsnittet [Serverns konfigurationsfil](../../installation/using/the-server-configuration-file.md).

Kompatibilitetsmatrisen har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html)

Avsnittet Arbetsflödet för rensning har uppdaterats. [Läs mer](../../production/using/database-cleanup-workflow.md)

Nätverkets slutpunkter i Campaign har flyttats till det här [avsnittet](../../installation/using/campaign-network-endpoints.md).

Avsnittet Installation av Spam Assassin har uppdaterats med det nya namnet på installationsfilen. [Läs mer](../../installation/using/configuring-spamassassin.md#installing-spamassassin)

Avsnittet om att duplicera miljöer har uppdaterats. [Läs mer](../../production/using/duplicating-environments.md#step-2---export-the-target-environment-configuration--dev-)

## Maj 2020 {#may-2020}

Avsnittet Övervaka levererbarhet har flyttats och förbättrats. [Läs mer](../../delivery/using/monitoring-deliverability.md)

Avsnittet Felsöka levererbarhet har flyttats och förbättrats. [Läs mer](../../delivery/using/deliverability-faq.md)

Riktlinjer för levererbarhet när du startar en ny plattform har förbättrats. [Läs mer](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv#transition-process)

Avsnittet Skicka transaktionsmeddelanden med bilagor har flyttats och uppdaterats. [Läs mer](../../message-center/using/transactional-email-with-attachments.md)

Avsnittet Bästa praxis för datapaket har flyttats och uppdaterats. [Läs mer](../../platform/using/working-with-data-packages.md#data-package-best-practices)

## April 2020 {#april-2020}

FDA-rättighetstabellen har flyttats till dokumentationen Åtkomst till en extern databas (FDA). [Läs mer](../../installation/using/remote-database-access-rights.md)

Vanliga frågor och svar har uppdaterats med tips på hur du rensar mjukt och hårt cacheminne. [Läs mer](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

Bästa praxis för datamodeller har förbättrats med ytterligare information om index. [Läs mer](../../configuration/using/data-model-best-practices.md#indexes)

Avsnittet som beskriver den inbyggda datamodellen i Adobe Campaign har uppdaterats med mer information om varje tabell. [Läs mer](../../configuration/using/data-model-description.md)

Användningsfall med arbetsflöden har uppdaterats och omorganiserats i tematiska avsnitt. [Läs mer](../../workflow/using/about-workflow-use-cases.md)

Avsnitten [Kvalificering av ej levererad e-post](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) och [hanteringsregler för e-post](../../delivery/using/understanding-delivery-failures.md#email-management-rules) har förbättrats med uppdaterad information.

Artikeln Adobe Campaign Enhanced MTA har uppdaterats. Den gäller nu endast Campaign Classic. [Läs mer](https://helpx.adobe.com/se/campaign/kb/acc-campaign-enhanced-mta.html)

## Mars 2020 {#march-2020}

Bästa praxis för datamodeller har uppdaterats med nya avsnitt som inkluderar bland annat [Sekvenser](../../configuration/using/data-model-best-practices.md#sequences), [Prestanda](../../configuration/using/data-model-best-practices.md#performance) och [Stora tabeller](../../configuration/using/data-model-best-practices.md#large-tables). [Läs mer](../../configuration/using/data-model-best-practices.md)

Ett nytt avsnitt finns nu tillgängligt som beskriver den inbyggda datamodellen i Adobe Campaign och interaktionen mellan tabeller. [Läs mer](../../configuration/using/data-model-description.md)

Ytterligare nyckellänkar har lagts till på dokumentationens startsida. [Läs mer](../../campaign-classic-home.md)

Ett användningsfall har lagts till om hur du kan integrera ett dynamiskt erbjudande från Adobe Target i ett e-postmeddelande i Adobe Campaign. [Läs mer](../../integrations/using/inserting-a-dynamic-image.md)

Ett nytt avsnitt finns nu tillgängligt som beskriver de olika språk som finns i Adobe Campaign. [Läs mer](../../platform/using/adobe-campaign-workspace.md#languages)

Riktlinjerna för åtkomsthantering har uppdaterats med mer information om namngivna rättigheter. [Läs mer](../../platform/using/access-management-named-rights.md)

## Februari 2020 {#february-2020}

Ett nytt avsnitt finns nu tillgängligt som beskriver bästa praxis och viktiga rekommendationer när datamodellen i Adobe Campaign utformas. [Läs mer](../../configuration/using/data-model-best-practices.md)

Ett nytt avsnitt finns nu tillgängligt om Konfigurationer av teknisk e-post. [Läs mer](../../installation/using/email-deliverability.md)

Vanliga frågor och svar om levererbarheten har uppdaterats med mer information om felmeddelandet om att &quot;kvoterna har uppfyllts&quot;. [Läs mer](https://helpx.adobe.com/se/campaign/kb/acc-deliverability-faq.html#FAQ)

AMP för e-post stöds nu av nya e-postleverantörer: den relaterade dokumentationen har uppdaterats. [Läs mer](../../delivery/using/defining-interactive-content.md)

Avsnittet E-postarkivering har förbättrats. [Läs mer](../../installation/using/email-archiving.md#recommendations-and-limitations)

## Januari 2020 {#release-20-1}

**Nya funktioner i version 20.1**

Snowflake FDA-koppling – [läs mer](../../installation/using/configure-fda-snowflake.md)

Förbättringar på Hadoop FDA-koppling – [läs mer](../../installation/using/configure-fda-hadoop.md)

**Andra dokumentationsuppdateringar som följer med denna version**

Handböckerna för [installation](../../installation/using/general-architecture.md), [produktion](../../production/using/foreword.md) och [konfiguration](../../configuration/using/additional-parameters.md) har uppdaterats med den nya systemenheten som används vid uppstart av tjänsten nlserver. /Etc/init.d/nlserver6 kan fortfarande användas men Adobe rekommenderar att du nu använder kommandot systemctl för att interagera med tjänsten nlserver.

Installationshandboken har uppdaterats och synkroniserats med den senaste versionen av kompatibilitetsmatrisen. Nya system som stöds har lagts till. Förekomster av system som är inaktuella och inte stöds har tagits bort. [Läs mer](../../installation/using/general-architecture.md)

Kompatibilitetsmatrisen har uppdaterats med kopplingar till Hadoop 3.0 och Snowflake FDA. [Läs mer](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html)

Ett tips om IP-tillhörighet har lagts till i installationshandboken. [Läs mer](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

Avsnittet Arbetsflödet för databasrensning har uppdaterats. De angivna gruppsiffrorna återspeglar nu implementeringen av kod. [Läs mer](../../production/using/database-cleanup-workflow.md)

En begränsning på FDA över HTTP har lagts till i handboken för transaktionsmeddelanden. [Läs mer](../../production/using/database-cleanup-workflow.md)

Information har lagts till om det nya alternativet som låter dig definiera en timeout-period för arbetsflödesaktiviteterna **[!UICONTROL JavaScript code]** och **[!UICONTROL Advanced JavaScript code]**. [Läs mer](../../workflow/using/sql-code-and-javascript-code.md)

Information har lagts till i den nya **[!UICONTROL Start Pending]**-vyn som är tillgänglig i noden **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]**. [Läs mer](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Handboken [Skicka push-meddelanden](../../delivery/using/about-mobile-app-channel.md) har flyttats, omorganiserats och förbättrats med tydlig information.

Den nya parametern för rapportkonfigurationen av webbadresser har dokumenterats [här](../../reporting/using/properties-of-the-report.md#defining-additional-settings).

Sidan för den **Lokala och värdbaserade funktionsmatrisen i Campaign Classic** har uppdaterats med de nya FDA-kopplingarna. [Läs mer](../../installation/using/capability-matrix.md).

Sidan **Funktionsmatrisen för Campaign Classic** har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html)

Det nya **[!UICONTROL Cleanup of Nmsaddress]**-arbetsflödet har dokumenterats [här](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress).

En begränsning har lagts till när en frågeaktivitet används i ett arbetsflöde. [Läs mer](../../workflow/using/query.md).

Ett nytt avsnitt har lagts till för att i detalj dokumentera de förbättrade verifieringsreglerna gällande e-postadresser för att skicka en adress till karantän om ett mjukt fel uppstår. [Läs mer](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

Parametern i konfigurationsfilen som anger om en instans använder Enhanced MTA eller inte är nu dokumenterad. [Läs mer](../../installation/using/the-server-configuration-file.md#mta)

Avsnittet Levererbarhet har flyttats, omorganiserats och förbättrats med uppdaterat innehåll. [Läs mer](../../delivery/using/about-deliverability.md)

Ett nytt avsnitt finns nu tillgängligt som beskriver grunderna för datamodellen i Adobe Campaign Classic och hur du får åtkomst till beskrivningen av varje tabell. [Läs mer](../../configuration/using/about-data-model.md)

Artikeln Adobe Campaign Enhanced MTA har uppdaterats med mer detaljerad information om hur du installerar ett specifikt typologipaket för instanser som inte lägger till de obligatoriska Enhanced MTA-rubrikerna i varje meddelande. [Läs mer](https://helpx.adobe.com/se/campaign/kb/acc-campaign-enhanced-mta.html#impacts)

Användningsfallen relaterade till att utforma frågor har omorganiserats i olika avsnitt. [Läs mer](../../workflow/using/querying-recipient-table.md)

Ett nytt avsnitt finns nu tillgängligt om tips och trick för att hantera erbjudanden och använda interaktionsmodulen i Adobe Campaign Classic. [Läs mer](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

Dokumentationen om interaktion har berikats med länkar till flera videoklipp som hjälper dig att förstå hur du bättre hanterar erbjudanden. [Läs mer](../../interaction/using/interaction-and-offer-management.md)

Artikeln med bästa praxis för att optimera frågor som körs på din instans har integrerats i dokumentationen. [Läs mer](../../workflow/using/query.md#optimizing-queries)

Rapporthandboken har uppdaterats och omorganiserats. [Läs mer](../../reporting/using/about-adobe-campaign-reporting-tools.md)

Ett exempel på hur du använder en instansvariabel i ett arbetsflöde har lagts till. [Läs mer](../../workflow/using/javascript-scripts-and-templates.md)

+++
