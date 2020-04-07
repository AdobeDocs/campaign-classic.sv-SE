---
title: Uppdateringar av Adobe Campaign Classic-dokumentation
description: På den här sidan visas alla nya funktioner och dokumentationsuppdateringar för varje version av Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 75f195a11170b4213f930deed886f8bf5b0817bc

---


# Dokumentationsuppdateringar{#documentation-updates}

Läs om alla de senaste uppdateringarna av dokumentationen för Adobe Campaign Classic.

På den här sidan visas alla nya funktioner och dokumentationsuppdateringar för varje version av Adobe Campaign Classic.

Du kan även läsa versionsinformationen [för](../../rn/using/latest-release.md)Adobe Campaign Classic.

## April 2020 {#april-2020}

FDA-rättighetstabellen har flyttats till Accessing an external database (FDA) documentation. [Läs mer](../../platform/using/remote-database-access-rights.md)

Vanliga frågor och svar har uppdaterats med tips på hur du rensar mjuk och hård cache. [Läs mer](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

Avsnittet om god praxis för datamodell har förbättrats med ytterligare information om index. [Läs mer](../../configuration/using/data-model-best-practices.md#indexes)

Avsnittet som beskriver den fördefinierade datamodellen för Adobe Campaign har uppdaterats med mer information om varje körklar tabell och med länkar till relevanta moduler. [Läs mer](../../configuration/using/data-model-description.md)

Användningsexempel från guiden&quot;Automatisera med arbetsflöden&quot; har omorganiserats till tematiska avsnitt. [Läs mer](../../workflow/using/using-the-local-approval-activity.md)

Avsnitten [Signera e-postkvalificering](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification) och [E-posthanteringsregler](../../delivery/using/understanding-delivery-failures.md#email-management-rules) har förbättrats med uppdaterad information.

## Mars 2020 {#march-2020}

Sidan&quot;Bästa praxis för datamodell&quot; har uppdaterats med nya avsnitt, bland annat [Sekvenser](../../configuration/using/data-model-best-practices.md#sequences), [Prestanda](../../configuration/using/data-model-best-practices.md#performance) och [Stora tabeller](../../configuration/using/data-model-best-practices.md#large-tables). [Läs mer](../../configuration/using/data-model-best-practices.md)

Nu finns ett nytt avsnitt som beskriver den fördefinierade datamodellen Adobe Campaign och interaktionen med färdiga tabeller. [Läs mer](../../configuration/using/data-model-description.md)

Ytterligare resurser har lagts till på dokumentationsstartsidan. [Läs mer](../../campaign-classic-home.md)

Ett användningsexempel har lagts till om hur du integrerar ett dynamiskt erbjudande från Adobe Target i ett e-postmeddelande i Adobe Campaign. [Läs mer](../../integrations/using/inserting-a-dynamic-image.md)

Nu finns ett nytt avsnitt som beskriver de olika språk som är tillgängliga i Adobe Campaign. [Läs mer](../../platform/using/adobe-campaign-workspace.md#languages)

Sidan Åtkomsthantering har uppdaterats med mer information om namngivna rättigheter. [Läs mer](../../platform/using/access-management.md#named-rights)

## Februari 2020 {#february-2020}

Nu finns ett nytt avsnitt med bästa praxis och viktiga rekommendationer när du utformar datamodellen för Adobe Campaign. [Läs mer](../../configuration/using/data-model-best-practices.md)

Avsnittet&quot;E-postleverans&quot; har bytt namn till&quot;Tekniska e-postkonfigurationer&quot;. [Läs mer](../../installation/using/email-deliverability.md)

Vanliga frågor om leveranser har uppdaterats med mer information om felmeddelandet&quot;kvoterna uppfyllts&quot;. [Läs mer](https://helpx.adobe.com/campaign/kb/acc-deliverability-faq.html#FAQ)

AMP för e-post stöds nu av tre e-postleverantörer (Gmail, Outlook och Mail.ru), och avsnittet som beskriver hur du definierar interaktivt innehåll med AMP har uppdaterats. [Läs mer](../../delivery/using/defining-interactive-content.md)

Avsnittet för e-postarkivering har klargjorts. [Läs mer](../../installation/using/email-archiving.md#recommendations-and-limitations)

## 20.1 - 17/02/2020{#release-20-1}

**Nya funktioner i releasen**

Snöflake FDA Connector - [Läs mer](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)

Förbättringar av Hadoop FDA Connector - [läs mer](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3)

**Andra dokumentationsuppdateringar som följer med releasen**

Guiderna för [installation](../../installation/using/before-reading.md), [produktion](../../production/using/foreword.md) och [konfiguration](../../configuration/using/additional-parameters.md) har uppdaterats med den nya systemenheten som används av servertjänstens start. Du kan fortfarande använda /etc/init.d/nlserver6, men vi rekommenderar att du nu använder kommandot systemctl för att interagera med nlserver-tjänsten.

Installationsguiden har uppdaterats och synkroniserats med den senaste versionen av kompatibilitetsmatrisen. Nya system som stöds har lagts till. Förekomster av system som inte stöds har tagits bort. [Läs mer](../../installation/using/before-reading.md)

Kompatibilitetsmatrisen har uppdaterats med Hadoop 3.0- och Snowflake FDA-anslutningarna. [Läs mer](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Ett tips om IP-tillhörighet har lagts till i installationsguiden. [Läs mer](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

Arbetsflödesavsnittet för databasrensning har uppdaterats. De angivna batchsiffrorna återspeglar nu kodimplementeringen. [Läs mer](../../production/using/database-cleanup-workflow.md)

En begränsning för FDA över HTTP har lagts till i handboken för transaktionsmeddelanden. [Läs mer](../../production/using/database-cleanup-workflow.md)

Information har lagts till om det nya alternativet som gör att du kan definiera en timeout-period för **[!UICONTROL JavaScript code]** - och **[!UICONTROL Advanced JavaScript code]** arbetsflödesaktiviteterna. [Läs mer](../../workflow/using/sql-code-and-javascript-code.md)

Information har lagts till i den nya **[!UICONTROL Start Pending]** vyn som är tillgänglig i **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]** -noden. [Läs mer](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Guiden [Skicka push-meddelanden](../../delivery/using/about-mobile-app-channel.md) har flyttats, omorganiserats och förbättrats med tydlig information.

Den nya parametern för konfigurationen av URL-adresser har dokumenterats [här](../../reporting/using/properties-of-the-report.md#defining-additional-settings).

Matrissidan för **Campaign Classic On-lokalt- och värdfunktioner** har uppdaterats med de nya FDA-anslutningarna. [Läs mer](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)

Matrissidan **Kampanjklassiska funktioner** har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Det nya **[!UICONTROL Cleanup of Nmsaddress]** arbetsflödet har dokumenterats [här](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress).

En begränsning har lagts till när en frågeaktivitet används i ett arbetsflöde. [Läs mer](../../workflow/using/query.md).

Ett nytt avsnitt har lagts till för att detaljgranska de förbättrade verifieringsreglerna för e-postadresser för att skicka en adress till karantänen om fel uppstår. [Läs mer](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

Parametern från konfigurationsfilen som anger att en instans använder Förbättrad MTA eller inte dokumenteras nu. [Läs mer](../../installation/using/the-server-configuration-file.md#mta)

## Januari 2020 {#january-2020}

Avsnittet Slutprodukt har flyttats, omorganiserats och förbättrats med uppdaterat innehåll. [Läs mer](../../delivery/using/about-deliverability.md)

Nu finns ett nytt avsnitt som beskriver grunderna i datamodellen för Adobe Campaign Classic och hur du får tillgång till beskrivningen av varje tabell. [Läs mer](../../configuration/using/about-data-model.md)

Artikeln Förbättrad MTA för Adobe Campaign har uppdaterats med mer detaljerad information om hur du installerar ett specifikt typologipaket för instanser som inte lägger till de obligatoriska Enhanced MTA-rubrikerna i varje meddelande. [Läs mer](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html#impacts)

Användningsexempel för frågedesign har omorganiserats i olika avsnitt. [Läs mer](../../workflow/using/querying-recipient-table.md)

Det finns nu ett nytt avsnitt om tips och tricks för att hantera erbjudanden och använda interaktionsmodulen i Adobe Campaign Classic. [Läs mer](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

Interaktionsdokumentationen har berikats med länkar till flera videoklipp som hjälper dig att förstå hur du bättre hanterar erbjudanden. [Läs mer](../../interaction/using/interaction-and-offer-management.md)

Artikeln om de effektivaste strategierna för att optimera frågor som körs på din instans har integrerats i dokumentationen. [Läs mer](../../workflow/using/query.md#optimizing-queries)

Rapportguiden har uppdaterats och omorganiserats. [Läs mer](../../reporting/using/about-adobe-campaign-reporting-tools.md)

Ett exempel på hur du använder en instansvariabel i ett arbetsflöde har lagts till. [Läs mer](../../workflow/using/javascript-scripts-and-templates.md)

## December 2019 {#december-2019}

Alternativet &quot;WdbcOptions_TempDbName&quot; har lagts till i listan över kampanjalternativ. [Läs mer](../../installation/using/configuring-campaign-options.md)

FDA-matrissidan har flyttats [här](/help/rn/using/assets/fda_rdbms_rights.pdf).

Sidan Behörighetsmatris för åtkomst har flyttats [här](https://docs.adobe.com/content/help/en/campaign-classic/using/getting-started/administration-basics/assets/accessrights.pdf).

Avsnittet som beskriver hur du definierar interaktivt innehåll med AMP har flyttats. [Läs mer](../../delivery/using/defining-interactive-content.md)

## 19.2 - 02/12/2019{#release-19-2}

**Nya funktioner i releasen**

California Consumer Privacy Act (CCPA) - [Läs mer](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

Interaktivt material med AMP - [läs mer](../../delivery/using/defining-interactive-content.md)

Direktövervakning av arbetsflöde - [Läs mer](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Säkra SMS-meddelanden (TLS) - [Läs mer](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

**Andra dokumentationsuppdateringar som följer med releasen**

Adobe Campaign Förbättrad MTA-dokumentation finns nu tillgänglig. [Läs mer](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html)

Ett nytt avsnitt har lagts till om hur du felsöker ett arbetsflöde som finns i läget&quot;Starta så snart som möjligt&quot; i en kampanj. [Läs mer](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

De nya alternativen NmsOperation_DeliveryPreparationWindow och WdbcKillSessionPolicy har lagts till i listan över kampanjalternativ. [Läs mer](../../installation/using/configuring-campaign-options.md)

Nu finns ett nytt dokument som beskriver grunderna i Adobe Campaign Classic-datamodellen. [Läs mer](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)

Det nya alternativet **Maximal körtidsåtgång** för personalisering i leveransegenskaperna beskrivs i det här [avsnittet](../../delivery/using/personalization-fields.md#timing-out-personalization).

Exemplen för API-anrop med en **HttpServletRequest** med logon() och query() har uppdaterats. [Läs mer](../../configuration/using/web-service-calls.md).

En rekommendation för **sqlDefault** -attributet i schemadefinitionen har lagts till. [Läs mer](../../configuration/using/elements-and-attributes.md#attribute-description).

Integrationen mellan Adobe Campaign och Adobe Real-time Customer Data Platform beskrivs nu i guiden **Integrera med Adobe Experience Cloud** . [Läs mer](../../integrations/using/about-campaign-integrations.md).

## November 2019 {#november-2019}

En varning har lagts till i [Multiplexing av servern](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) för mellanlagring och [Supporting multiple control instances](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances) sections som anger att dessa distributioner inte stöds för fullständigt värdbaserade klienter och hybridklienter.

Ett nytt avsnitt har lagts till som beskriver hur teckenkodningen som används för att skicka e-postmeddelanden ska framtvingas. [Läs mer](../../delivery/using/sending-messages.md#character-encoding)

Avsnittet Åtkomsthantering har uppdaterats med rättigheten **** Sekretessdata. [Läs mer](../../platform/using/access-management.md#named-rights)

Information har lagts till för att ange att innehåll i anpassningsfält får innehålla högst 1 024 tecken. [Läs mer](../../delivery/using/personalization-fields.md)

Kontrollpanelens dokumentation har integrerats i den nya dokumentationsuppsättningen för samarbete. [Läs mer](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)

Guiden Komma igång med bästa leveransmetoder har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/delivery-best-practices.html)

## Oktober 2019 {#october-2019}

Listan med felmeddelanden för Campaign Standard och Campaign Classic har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Guiden för att komma igång med GDPR har förbättrats och förbättrats. Det är nu en sekretessdokumentation som inkluderar GDPR och CCPA. [Läs mer](https://helpx.adobe.com/content/help/en/campaign/kb/campaign-privacy.html)

En ny felsökningssida har lagts till för spårning i Campaign Classic. [Läs mer](https://helpx.adobe.com/campaign/kb/classic-tracking-troubleshooting.html).

En ny sida med bästa praxis för Adobe Analytics Data Connector har lagts till. [Läs mer om Adobe Analytics Data Connector](../../platform/using/adobe-analytics-data-connector.md)

Guiden Komma igång med bästa leveransmetoder har flyttats och uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/delivery-best-practices.html)

En rekommendation har lagts till i SMS-kanaldokumentationen för att undvika problem när flera externa konton använder den utökade allmänna SMPP-anslutningen med samma leverantörskonto. [Läs mer](../../delivery/using/sms-channel.md#automatic-reply)

Information om hur du förhindrar att ett arbetsflöde körs samtidigt lades till i aktivitetsdokumentationen för schemaläggaren. [Läs mer](../../workflow/using/scheduler.md)

Stegen för att konfigurera Inkorgsåtergivning för lokala installationer har lagts till i dokumentationen. [Läs mer](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

## September 2019 {#september-2019}

En ny sida har lagts till med allmänna riktlinjer för att underhålla Campaign Classic. [Läs mer](https://helpx.adobe.com/campaign/kb/acc-maintenance.html)

Information om övervakning av arbetsflöden har centraliserats till ett nytt dedikerat avsnitt. [Läs mer](../../workflow/using/monitoring-workflow-execution.md).

En ny sida med allmänna riktlinjer för spårning i Adobe Campaign Classic har lagts till. [Läs mer](https://helpx.adobe.com/campaign/kb/acc-tracking.html).

De bästa metoderna för prestandaförbättringar av arbetsflöden och leveranser har uppdaterats. [Läs mer om arbetsflöden](../../workflow/using/workflow-best-practices.md) och [mer om leveranser](../../delivery/using/monitoring-a-delivery.md#best-practices-performance).

## 19.1 - 30/05/2019{#release-19-1}

**Nya funktioner i releasen**

Kontrollpanelen - [läs mer](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)

Granskningsspår - [läs mer](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Audit_trail.html)

**Andra dokumentationsuppdateringar som följer med releasen**

En ny bygguppgradering - frågor och svar har skapats. [Läs mer](https://helpx.adobe.com/campaign/kb/build-upgrade-faq.html)

Matrisen [Kompatibilitet](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) har uppdaterats. Listan över databassystem som stöds har uppdaterats, liksom Android-/iOS-versioner och relaterade SDK:er. Kompatibilitetsmatrisen [för](https://helpx.adobe.com/campaign/kb/compatibility-matrix-19-0.html) 19.0 har arkiverats.

Sidan Borttagna och borttagna funktioner i Campaign Classic har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

Beskrivningen av serverkonfigurationsfilen har lagts till i installationshandboken. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_The_server_configuration_file.html)

Ett avsnitt har lagts till som beskriver installations- och konfigurationsstegen för värdbaserade modeller och hybridmodeller. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_Introduction.html)

Ett avsnitt har lagts till som beskriver avinstallationsstegen för Campaign-servern. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Uninstalling_Campaign.html)

Guiderna för att komma igång med [säkerhet](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html), [leverans](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) och [sekretess](https://helpx.adobe.com/campaign/kb/acc-privacy.html) har uppdaterats.

Beskrivningen av förprocessarbetsflödesalternativet har uppdaterats för att återspegla produktändringar. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Data_loading__file_)

Tekniken Marketing Cloud Triggers har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Listan med felmeddelanden har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Ytterligare information om SOAP-autentiseringsmetoder för transaktionsmeddelanden har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Event_description.html)

Konfigurationsstegen för Apache har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Integration_into_a_Web_server.html#Configuring_Apache_web_server_in_RHEL)

En ny sida har lagts till med listan över slutpunkter för Campaign Standard och Classic. [Läs mer](https://helpx.adobe.com/campaign/kb/campaign-endpoints.html)

Artikeln Data package best practices har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/data-package-best-practices.html)

Dokumentationen om att hantera erbjudanden har uppdaterats med ett nytt avsnitt med bästa praxis. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/ITA_Interaction_Overview_Interaction_best_practices.html)

En ny kunskapsbasartikel om hur du använder erbjudandekatalogen i Adobe Campaign Classic har skapats. [Läs mer](https://helpx.adobe.com/campaign/kb/offer-best-practices.html)

Delarbetsflödets aktivitetsavsnittet har förbättrats med ett exempel på användning. [Läs mer](../../workflow/using/sub-workflow.md)

Kunskapsbasartikeln i [Campaign Classic On-Hosted &amp; Hosted](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html) Capabilities har uppdaterats med information om arkivering av e-post.

Transactional Messaging-dokumentationen har uppdaterats med en anteckning om mallpublicering. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/MCE_Template_publication.html)

Avsnittet Obearbetade studsmeddelanden har uppdaterats med mer information om fälten Vidarebefordringsadress och Adress för fel. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Deploying_an_instance.html#Unprocessed_bounce_mails)

Ett nytt avsnitt om arbetsflödesplanering har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Workflow_best_practices.html#Execution_and_performance)

Två nya alternativ har lagts till i listan över kampanjalternativ: XtkSecurity_Restrict_EditXML och NmsOperation_OperationMgtDebug.
[Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Lagt till information om olika externa konton som är tillgängliga i Campaign Classic och hur du konfigurerar dem.
[Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html)

Avsnittet Analytics Data Connector har uppdaterats för att återspegla gränssnittsändringar.
[Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Lagt till information i faktureringsrapporten.
[Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Billing_report)

Uppdaterad dokumentation om integrationen mellan delade målgrupper.
[Läs mer](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

Följande tekniker har uppdaterats: Protokoll och inställningar för [SMS-anslutningsprogrammet](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html) och automatisk [sekvensgenerering](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence).

Avsnittet Tekniska arbetsflöden har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

Konfigurationsproceduren för Campaign-domännamnet har förbättrats och uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html)

Migreringsproceduren för Android-appar från Google Cloud Messaging (GCM) till Firebase Cloud Messaging (FCM) har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/migrate-to-fcm.html)

Guide för att ändra storlek på kampanjmaskinvara har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)

Information har lagts till om frågesträngen för det externa Teradata-kontot. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#External_database_external_account)

## Januari 2019{#release-doc-16-01-2019}

Tekniken Marketing Cloud Triggers har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Ett meddelande lades till i avsnittet för godkännande av erbjudande för att ange att&quot;Godkänt innehåll&quot; anger att innehållsgodkännandeprocessen har uppnåtts, oavsett om alla erbjudanden har aktiverats/godkänts eller inte. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/ITA_Managing_an_offer_catalog_Approving_and_activating_an_offer.html#Approving_offer_content)

Ett nytt avsnitt lades till i installationshandboken med alternativ från noden Administration / Plattform / Alternativ. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Information har lagts till om användningen av dirigerade adresser för att skydda din sändlista. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

De viktigaste stegen när du skapar och skickar en leverans har grupperats om till ett nytt avsnitt, med referenser till de olika kanalerna vid behov. [Läs mer](../../delivery/using/steps-about-delivery-creation-steps.md)

Avsnittet [E-postarkivering](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) har flyttats, omorganiserats och förbättrats med tydlig information:

* Bästa tillvägagångssätt har lagts till för e-post per anslutning och parametrar för BCC som skickar IP-adresser. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Best_practices)

* Vi har uppdaterat stegen för att uppgradera till det nya systemet för e-postarkivering (BCC) om du redan har använt e-postarkivering med en äldre version (innan Adobe Campaign 17.2 - version 8795). [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Ett användningsexempel har lagts till i guiden Automating with Workflows: Skicka personaliserade aviseringar till operatorer. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_personalized_alerts_to_operators.html)

Avsnittet&quot;Migrera till en ny version&quot; har uppdaterats. Dokumentationen innehåller nu bara information om stegen för migrering till Adobe Campaign Classic v7 från en äldre version, eftersom det inte längre är möjligt att migrera till Adobe Campaign v6.11. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

Avsnittet&quot;Försök igen efter ett tillfälligt leveransfel&quot; har klargjorts. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Retries_after_a_delivery_temporary_failure)

Länkar till avsnittet&quot;Digital Content Editor&quot; har lagts till i avsnittet&quot;Definiera e-postinnehåll&quot;. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Message_content)

Avsnittet&quot;Transactional messaging architecture&quot; har uppdaterats med en varning som anger att det inte går att installera kontroll- och körningsinstanserna på samma dator. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Transactional_messaging_architecture.html)

Avsnittet&quot;Arbetsflödesövervakning&quot; har uppdaterats med ett meddelande för byggen mellan 8700 och 8977 (18.10), inklusive en länk till ett meddelande om hur Workflow HeatMap-paketet installeras för dessa byggen. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#About_the_Workflow_HeatMap)

Ett användningsexempel har lagts till om hur du skickar ett e-postmeddelande med anpassade datafält med hjälp av Enrichment-aktiviteten i ett arbetsflöde. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Email_enrichment_with_custom_date_fields.html)

Funktionsvideor har flyttats [hit](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/overview.html).

Två tekniklösningar har lagts till i [Teradata](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html) och [MySQL 5.7](https://helpx.adobe.com/campaign/kb/campaign_fda_mysql.html).

## 18.10 - 05/11/2018{#release-18-10}

**Nya funktioner i releasen**

Förbättringar av push-meddelanden - [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Integrating_the_SDK_into_the_mobile_application)

SQL Data Management-aktivitet - [läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#SQL_Data_Management)

Övervaka arbetsflöden - [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Workflow_monitoring)

**Andra dokumentationsuppdateringar som följer med releasen**

Campaign Classic API:er finns nu på en [dedikerad sida](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html). Om du använde filen jsapi.chm bör du nu hänvisa till den nya onlineversionen.

Kompatibilitetsmatrisen har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Sidan Borttagna och borttagna funktioner i Campaign Classic har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

I [versionsinformationen](https://docs.campaign.adobe.com/doc/AC/en/RN.html) och [äldre versionsinformation](https://docs.campaign.adobe.com/doc/AC/en/RN_legacy.html)har en varning lagts till för byggen som har återkallats. Kumulativa byggen för 17.9, 18.4 och 18.6 har också lagts till.

Guiderna för att komma igång med [säkerhet](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html), [leverans](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) och [bygguppgraderingar](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) har uppdaterats.

Guiden Komma igång med [sekretess](https://helpx.adobe.com/campaign/kb/acc-privacy.html) har uppdaterats med information om hur du anropar API externt och hur du använder queryDef för att fråga efter status och hämta GDPR-filen.

Lagt till ett användningsfall för transaktionsmeddelanden för att lägga till e-postbilagor direkt till utgående utskick. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/MCE_Use_case_Purpose.html)

Uppdaterade felsökningsavsnittet för anslutningströsklar. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Connection_thresholds.html)

Ett avsnitt har lagts till om hur du konfigurerar en proxyanslutning. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Proxy_connection_configuration)

Avsnittet om tillåten begränsning av externa kommandon har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Restricting_authorized_external_commands)

Ett felsökningsavsnitt som rör SFTP-användning har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

Översiktsavsnittet i guiden Skicka meddelanden har omstrukturerats. Information lades till om den globala processen för att skapa leveranser och de olika leveranstyperna. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_About_deliveries_and_channels_Communication_channels.html)

Listan med felmeddelanden har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Avsnittet om hur du använder dirigerade adresser flyttades till översiktskapitlet i guiden Skicka meddelanden. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

Ett nytt användningsexempel för arbetsflöde har lagts till: Hantera uppdateringar från samtidig körning av arbetsflöden. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Coordinating_data_updates.html)

Avsnittet&quot;Inkorgsåtergivning&quot; har uppdaterats med ytterligare information om Litmus och en mer detaljerad procedur. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html#Multiplexing_the_mid-sourcing_server)

Avsnittet&quot;SpamAssassin&quot; har förbättrats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_SpamAssassin.html)

Ett användningsexempel har lagts till i avsnittet&quot;Hantera reklamtrötthet med tryckregler&quot;. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/CMP_Campaign_Optimization_Pressure_rules.html#Sending_only_the_highest-weighted_messages)

Nu finns ett nytt användningsexempel som beskriver hur du skapar ett arbetsflöde för flerkanalsleverans. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Cross-channel_delivery_workflow.html)

Vissa rekommendationer har lagts till i avsnittet&quot;Arkivera e-post&quot;. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_deliverability.html#Activating_emails_BCC_archiving)

En ny rekommendation har lagts till om den lägsta skärmupplösningen för optimal användning av Adobe Campaign. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Screen_resolution)

Integreringsguiden för Experience Manager har uppdaterats med ett förtydligande som har lagts till i konfigurationen av den här integreringen. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/ITG_Adobe_Experience_Manager_About_Adobe_Experience_Manager.html)

Lagt till information om skillnaden mellan grupptypslistan och listtypslistan. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_Creating_and_managing_lists.html#About_lists_in_Adobe_Campaign)

Koden har uppdaterats för att skicka ett rapportextrakt som en bifogad fil via e-post. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_a_report_to_a_list.html#Step_3-_Creating_the_workflow)

Ett exempel har lagts till om hur du skapar en fråga för att filtrera mottagare som inte har öppnat ett e-postmeddelande de senaste 7 dagarna. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Recipients_who_did_not_open_any_delivery)

Uppdaterade integreringsguiden för Dela målgrupper med Adobe Experience Cloud. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Sharing_audiences_with_Adobe_Experience_Cloud.html)

Hjälpsidan för vanliga frågor innehåller nu information om Campaign-tillgängliga språk, webbformuläröversättning och flerspråkiga e-postmeddelanden. [Läs mer](../../platform/using/common-questions.md)

Skillnaden mellan engelska i USA och engelska finns nu i ett särskilt avsnitt. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Formats_and_units)

Hjälpsidan [Vanliga frågor](../../platform/using/common-questions.md) länkar nu till felmeddelandesidan.

Information om Open-spårningsläget har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_Personalizing_URL_tracking.html)

Lägg till information om lägsta upplösning för webbprogram och webbformulär. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_About_web_forms.html)

Integreringsguiden för Campaign och Adobe Experience Cloud-lösningar har uppdaterats och omorganiserats. [Läs mer](../../integrations/using/about-campaign-integrations.md)

Ett avsnitt om hur textvariabeln används i webbformulär har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_Static_elements_in_a_web_form.html#Using_text_variables)

Lägen för URL-spårning i meddelanden är nu detaljerade. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_How_to_configure_tracked_links.html)

Avsnittet där instansen skapades har organiserats om. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Creating_an_instance_and_logging_on.html)

Skicka e-post till japanska mobiler beskrivs nu i ett nytt avsnitt. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Sending_emails_on_Japanese_mobiles)

Avsnittet&quot;Optimera personalisering&quot; har uppdaterats med ytterligare information. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_fields.html#Optimizing_personalization)

## 18.6 - 09/07/2018{#release-18-6}

**Nya funktioner i releasen**

Kompatibilitetsmatrisen har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

JSAPI-dokumentationen har uppdaterats. [Läs mer](https://support.neolane.net/webApp/extranetLogin)

Sidan med borttagna och borttagna funktioner har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

**Andra dokumentationsuppdateringar som följer med releasen**

Namnet på användarhandböckerna för Campaign Classic har ändrats för att förenkla navigeringen, förbättra användarupplevelsen, få tillgång till information och självhjälp. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/browseAC.html)

Listan med funktioner i uttrycksredigeraren har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Creating_queries_Defining_filter_conditions.html#List_of_functions)

Guiden Komma igång för säkerhet har uppdaterats med information om hur du skyddar sidor som innehåller PI. [Läs mer](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

Listan med felmeddelanden har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Ett felsökningsavsnitt har lagts till i IMS-integreringsdokumentationen. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/ITG_Connecting_via_an_Adobe_ID_IMS_troubleshooting.html)

Guiden Skapa uppgradering - kom igång har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html)

Konfigurationsavsnittet IP-tillhörighet har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Mid-sourcing_server.html#Multiplexing_the_mid-sourcing_server)

Ett felsökningsavsnitt för prestanda och genomströmning har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Performance_and_throughput_issues.html)

Listan med inbyggda personaliseringsblock har uppdaterats med exempel. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html#Out-of-the-box_personalization_blocks)

Listan över orsaker till leveransfel har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Delivery_failure_types_and_reasons)

Ett nytt avsnitt om paketdefinitionshantering har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_Working_with_data_packages.html#Managing_package_definitions)

Campaign-integreringen med Adobe Analytics - Data connector har förbättrats och omorganiserats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Ett nytt avsnitt med självstudiekurser har lagts till, med länkar till steg-för-steg-guider och instruktionsvideor. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

En ny TechNote om SMS-anslutningsprotokoll och inställningar har skapats. [Läs mer](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

Guiden Komma igång med god leveranspraxis har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

Kontokonfigurationen för Microsoft Dynamics 365 med Web API-distribution har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

Proceduren för att installera Adobe Campaign Classic på en Windows-plattform har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Windows__Installing_the_server.html)

Tidsramen för målgruppsdelning mellan Adobe Experience Cloud och Campaign Classic har detaljerats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Importing_and_exporting_audiences.html)

Kunskapsbasartikeln som är full för Campaign Classic-listan har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/article-list.html)

En ny Technote om prestandaförbättring och bästa praxis finns tillgänglig. [Läs mer](https://helpx.adobe.com/campaign/kb/best-practices-for-performance-improvement.html)

A/B-testexemplet har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Sidan med vanliga frågor och svar om Campaign Classic har uppdaterats. [Läs mer](../../platform/using/common-questions.md)

## 18.4 - 24/04/2018{#release-18-4}

**Nya funktioner i releasen**

EU:s allmänna dataskyddsförordning (GDPR) - [Läs mer](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

Aktiva profiler - [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_About_profiles.html#Active_profiles)

Förbättrad push-koppling för Android - [läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Android_connectors)

**Andra dokumentationsuppdateringar som följer med releasen**

Versionsinformationen har förbättrats för att ge en bättre användarupplevelse och innehåller nu alla korrigeringsfiler som hör till kundförfrågningar.  [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/RN.html)

En ny sida har lagts till med de vanligaste frågorna om Campaign Classic. [Läs mer](../../platform/using/common-questions.md)

Listan med felmeddelanden har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Tekniken Marketing Cloud Triggers har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

En ny teknik har lagts till om hur du installerar och distribuerar GDPR-paketet (Privacy) på äldre versioner av Campaign Classic. [Läs mer](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html)

En ny teknik för den nya sekvensmekanismen för automatisk generering har lagts till. [Läs mer](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html)

JSAPI-dokumentationen har uppdaterats. [Läs mer](https://support.neolane.net/webApp/extranetLogin)

Kompatibilitetsmatrisen har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Nu finns en ny sida med föråldrade funktioner och versioner. [Läs mer](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

Vissa kända begränsningar och bästa metoder för RDBMS har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html)

Lär dig de bästa sätten att använda SFTP. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

Listan över tekniska arbetsflöden har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

Förteckningen över kunskapsbasartiklar (tidigare kallade&quot;tekniker&quot;) finns nu här. [Läs mer](https://helpx.adobe.com/campaign/kb/article-list.html)

Videorna [](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html) Instruktioner har uppdaterats.

Raddokumentationen har uppdaterats efter att LINE-paketet har avskrivits. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

Rapportindikatorns beräkningsdokumentation har uppdaterats. [Läs mer](../../reporting/using/indicator-calculation.md)

Lagt till information om justering av tidszonsfiler med Oracle. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/MIG_Configuration_General_configurations.html#Oracle)

En ny avdelning för övervakning av leveranser med uppdaterad information om leveransfel och hantering av karantäner har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

Avsnittet&quot;Personalisering blockeras&quot; har omorganiserats med ny information om färdiga personaliseringsblock.
[Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html)

Avsnittet Arkivera e-post har omorganiserats med ny information om ```config-<instance name>.xml``` filkonfigurationen. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Activating_email_archiving__on_premise_)

Uppdaterad information om det tekniska arbetsflödet i Message Center (Control). [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_Message_Center__Control_.html)

Lagt till information om genomströmningsbegränsningar när du konfigurerar ett SMTP-relä. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Personalizing_delivery_parameters)

## 17.12 - 14/12/2017{#release-doc-14-12-2017}

Dokumentationsuppsättningen [för](https://helpx.adobe.com/support/campaign/classic.html) Adobe Campaign Classic har organiserats om för att bli enklare att använda.

Ett nytt avsnitt med självstudiekurser har lagts till för att underlätta tillgången till de viktigaste funktionerna i Campaign för att hjälpa till med material, guider, exempel och videor. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

Ett nytt avsnitt har lagts till för att hjälpa dig att övervaka din leveransstatus men också eventuella fel och lära dig hur du åtgärdar dem. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

Listan med felmeddelanden har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Tekniken Marketing Cloud Triggers har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Migreringsguiden för Campaign Classic har lagts till i samlingen. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

Matris för kampanjkompatibilitet har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

I tillämpliga fall anges i konfigurations- och installationsanvisningarna vilken värdmodell de gäller för. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html)

Ny artikel i kunskapsbasen som belyser skillnader i konfiguration och funktion mellan lokala, hybrida och hanterade tjänster-distributioner. [Läs mer](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)

Lagt till instruktioner om hur du installerar ett standardpaket. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Installing_packages.html)

Ytterligare information om hur du konfigurerar integreringen med Audience Manager eller People core service. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

Installationsdokumentationen har uppdaterats för att ange att pgcrypto nu krävs för Campaign-installation om PostreSQL används. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Prerequisites.html#Database_access_layers)

## 17.9 - 25/09/2017{#release-17-9}

**Nya funktioner i releasen**

Förbättringar av ACS Connector

SAP HANA-kontakt - [läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#SAP_HANA)

Hadoop-anslutning via HiveSQL - [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#Hadoop)

LINE-kanal: Meddelandeförbättringar - [läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

**Andra dokumentationsuppdateringar som följer med releasen**

Nya frågeexempel har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Filtering_duplicated_recipients)

Guide för bästa leveranssätt har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

Ett A/B-prov har uppdaterats med instruktioner som saknas. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Instruktionsvideor har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

Uppdatera avsnittet för e-postarkivering. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html)

Klargör schemaläggarens användning i ett arbetsflöde. [Läs mer](../../workflow/using/scheduler.md)

Bästa praxis för att lägga till pausat arbetsflöde. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html)

Ny procedur för förbearbetning av filer vid import och efterbearbetning när data exporteras i ett arbetsflöde. Läs [här](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html).

Karantänmekanismen för dokumentationen för SMS-meddelanden har uppdaterats för att återspegla särdragen i felhanteringen för den utökade generiska SMPP-anslutningen. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines).

Dokumentationen för mobilappskanalen har förbättrats med en detaljerad procedur för att skicka avancerade meddelanden på Android. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Rich_notifications).

Återgivningsdokumentationen för Inkorgen har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html).

Dokumentationen för webbspårning har förbättrats med ett uppdaterat exempel och kommentarer. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/CFG_Setting_up_web_tracking_Additional_parameters.html#Redirection_server_configuration).

Dokumentationen för SMS-kanalen har uppdaterats med ett förtydligande i avsnittet Automatiskt svar som gäller för den utökade allmänna SMPP-anslutningen. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_SMS_channel.html#Creating_an_SMPP_external_account).

Dokumentationen för social marknadsföring har uppdaterats. [Läs mer](../../social/using/about-social-marketing.md).

En ny teknik för IP-uppvärmning har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_Deliverability_IP_Warming_overview.pdf).

Ett nytt sätt att komma igång med uppgraderingen av bygget har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html).

## Maj 2017{#release-doc-30-05-2017}

Det finns en ny guide för att komma igång: Den innehåller några av de bästa metoderna som kan användas för att leverera med Adobe Campaign, från att skapa och målinrikta till att skicka och övervaka. [Läs mer](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

Guiden för att komma igång med säkerhet har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

Dokumentationen [&quot;Arkivera e-post&quot;&quot;](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) har uppdaterats med [&quot;E-post-BCC&quot;](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Configuring_the_BCC_email_address__on_premise_) och de [detaljerade stegen för att aktivera funktionen](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Archiving_emails).

Vissa videoklipp har lagts till och uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

Lär dig hur du skickar en leverans till mottagare som har lästs in från en extern fil utan att uppdatera databasen. [Läs mer](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)

Exemplet med dubbel anmälan har uppdaterats. [Läs mer](../../web/using/use-cases--web-forms.md)

## Mars 2017{#release-doc-31-03-2017}

Leverans: guiden [Komma](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) igång har uppdaterats. Leveransdokumentationen innehåller nu en mer detaljerad [översikt](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_About_deliverability.html) och en beskrivning av [implementeringsprocessen och de viktigaste stegen](../../delivery/using/deliverability-key-points.md).

Avsnittet&quot;Skicka med vågformer&quot; har flyttats och förbättrats med detaljerade exempel, rekommendationer och användningsexempel.    [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Sending_using_multiple_waves)

En tabell som beskriver felen som är specifika för SMS-meddelanden har lagts till i avsnittet Karantänhantering. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines)

Arbetsflöden: ett nytt exempel på flerkanalsarbetsflöde har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Cross-channel_deliveries)

Marketing Cloud-utlösare: En ny teknik om hur du konfigurerar och använder den med Adobe Campaign har lagts till. [Läs mer](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Handboken för arbetsflöde har organiserats om och utökats. Hitta enkelt hur du [bygger](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Building_a_workflow.html) och [kör](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html) ett arbetsflöde, hur du [målar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html) och [hanterar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html#Data_Management) data, hur du [importerar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html) [](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Updating_the_database) [](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow)data och hur du använder arbetsflödesdata för attuppdatera databasen¥ eller för attskicka leveranser¥.

Ett exempel på [importarbetsflöde](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow) som skapats efter [importrutiner](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html#Import_best_practices) är nu tillgängligt.
Installationsguiden har uppdaterats för den här nya versionen. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Architecture_and_hosting_models_General_architecture.html)

Kompatibilitetsmatrisen har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Mottagarna får ett mervärde när du inkluderar kuponger i e-postleveranserna. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalized_coupons.html)

## Adobe Campaign v7 - 16/03/2017{#release-17-2}

**Nya funktioner i releasen**

ACS Connector

Webb-API för Microsoft Dynamics - [läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

BCC-metoden för e-postarkivering - [läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Koppling till Amazon Simple Storage Service (S3) - [läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Event_activities.html#File_transfer)

