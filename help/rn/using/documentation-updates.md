---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic – dokumentationsuppdateringar
description: Den här sidan visar alla nya funktioner och dokumentationsuppdateringar för varje version av Adobe Campaign Classic
audience: rns
content-type: reference
topic-tags: latest-documentation-updates
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '4092'
ht-degree: 95%

---


# Dokumentationsuppdateringar{#documentation-updates}

Den här sidan visar alla nya funktioner och dokumentationsuppdateringar per månad och version av Campaign.

Se [Versionsinformationen för Adobe Campaign Classic](../../rn/using/latest-release.md) beträffande versionsrelaterade uppdateringar.

## Mars 2021 {#march-2021}

Information har lagts till i **[!UICONTROL Advanced JavaScript]**-aktivitetsavsnittet om hur du använder metoden task.setCompleted() för att avsluta aktiviteten och förhindra framtida återkallningar. [Läs mer](../../workflow/using/sql-code-and-javascript-code.md#adv-js-code-desc)

## Februari 2021 {#release-21.1}

**Dokumentationsuppdateringar i version 21.1**

Den nya funktionen **E-postfeedbacktjänst** (privat beta) finns [här](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service).

Avsnittet **Serverkonfigurationsfilen** har uppdaterats med de konfigurationsparametrar som behövs för att Campaign ska kunna ansluta till en annan tjänst med IMS. [Läs mer](../../installation/using/the-server-configuration-file.md#ims)

I listan över leveransstatus har beskrivningen för **som tagits med i beräkningen av tjänsteleverantören** uppdaterats: den här statusen används nu även för e-postleveranser som skickas med [tjänsten för e-postfeedback](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service). [Läs mer](../../delivery/using/delivery-statuses.md#list-delivery-statuses)

De kortkommandon som finns på den nya inloggningsskärmen för att ansluta till Adobe Campaign är nu dokumenterade. [Läs mer](../../platform/using/launching-adobe-campaign.md#connecting-to-adobe-campaign)

**Andra uppdateringar**

Ett nytt avsnitt har lagts till med detaljerad information om hur A/B-tester kan utföras med arbetsflöden. [Läs mer](../../delivery/using/get-started-a-b-testing.md)

Avsnittet Adobe Campaign Enhanced MTA har flyttats [här](../../delivery/using/sending-with-enhanced-mta.md).

En ny sida har lagts till för att ge en översikt över spårningsfunktionerna i [!DNL Campaign Classic]. [Läs mer](../../delivery/using/about-message-tracking.md)

Ett felsökningsavsnitt har lagts till för att hjälpa dig att lösa vanliga problem med spårning. [Läs mer](../../delivery/using/tracking-troubleshooting.md)

Avsnittet **Skicka ett e-postmeddelande** har ordnats om och förtydligats med nya underavsnitt. [Läs mer](../../delivery/using/sending-messages.md)

Information har lagts till om hur du lägger till länkar i e-postmeddelanden som kan personaliseras och som stöder spårning. [Läs mer](../../delivery/using/tracking-personalized-links.md).

## Januari 2021 {#jan-2021}

Aktivitetsavsnittet **[!UICONTROL Fork]** har berikats med bästa praxis. [Läs mer](../../workflow/using/fork.md)

Avsnittet **CRM-kopplingar** har uppdaterats, förbättrats och omorganiserats. [Läs mer](../../platform/using/crm-connectors.md).

Steg för att ansluta **Adobe Campaign och Microsoft Dynamics** beskrivs nu på en egen sida. [Läs mer](../../platform/using/crm-ms-dynamics.md).

Oracle On Demand-API:et är nu föråldrat som en CRM-koppling till Campaign. [Läs mer](../../rn/using/deprecated-features.md).

Läs [här](../../production/using/locate-tomcat-version.md) om hur du tar reda på den aktuella versionen av den inbäddade Tomcat-webbservleten som används i en instans i Adobe Campaign.

Listan över tekniska arbetsflöden med tillhörande paket har förbättrats och centraliserats till en enda sida. [Läs mer](../../workflow/using/about-technical-workflows.md)

Avsnittet Felsökning i användarhandboken **Övervakning** har omorganiserats och förbättrats med en landningssida. [Läs mer](../../production/using/troubleshooting.md).

Det finns ett nytt avsnitt gällande att **importera och exportera data** med nya sidor som rör bästa praxis för arbetsflöden, datakomprimering, kryptering och import. [Läs mer](../../platform/using/get-started-data-import-export.md)

## December 2020 {#dec-2020}

Avsnittet **Leveransövervakning** har omorganiserats med tematiska ämnen. [Läs mer](../../delivery/using/about-delivery-monitoring.md)

Ett användningsfall har lagts till om hur du lägger till avsändarnas IP-adresser i leveransloggarna. [Läs mer](../../delivery/using/delivery-dashboard.md#use-case)

Frågor och svar om sekretess har flyttats till [det här avsnittet](../../platform/using/privacy-faq.md).

Ett användningsfall har lagts till om hur du använder **[!UICONTROL Deduplication]**-aktivitetens funktioner för sammanslagning. [Läs mer](../../workflow/using/deduplication-merge.md)

Protokoll- och inställningssidan med en fullständig beskrivning beträffande SMS-kopplingen finns nu tillgänglig [här](../../delivery/using/sms-protocol.md).

Information har lagts till i avsnittet **Transaktionsmeddelanden** som varnar för att händelsemapparna inte får anges som vyer över körningsinstanserna för att undvika problem med åtkomsträttigheter. [Läs mer](../../message-center/using/event-collection.md)

## November 2020 {#nov-2020}

Översikten över kampanjdatamodellen har förbättrats och omorganiserats. [Läs mer](../../configuration/using/about-data-model.md).

Konfiguration av externa konton har flyttats till [det här avsnittet](../../installation/using/external-accounts.md).

Dokumentationen om federerad dataåtkomst (FDA) i Campaign har förbättrats med information för varje extern databaskonfiguration och flyttats till [det här avsnittet](../../installation/using/about-fda.md).

[Campaign version 20.2.3](../../rn/using/release--20-2.md#release-20-2-3-build-9182) har flyttats till Allmän tillgänglighet (GA).

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

Versionsinformation och kompatibilitetsmatris för utgåvan Gold Standard finns nu i ett särskilt avsnitt.
[Läs mer](../../rn/using/gold-standard.md#gs-11).

Integrering av utlösare som ursprungligen baserades på oAUTH-autentiseringsinställningar för åtkomst till pipelines har nu ändrats och flyttats till Adobe I/O. [Läs mer](../../integrations/using/configuring-adobe-io.md)

**Andra uppdateringar**

Dokumentationssidorna har uppdaterats för att återspegla uppdateringen Tomcat 8.

Mer information har lagts till i beskrivningen i rutan ”Om” i avsnittet ”Ladda ned din version av Adobe Campaign”. [Läs mer](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)

Riktlinjer för att utföra en versionsuppgradering har lagts till i avsnittet Uppdatera Adobe Campaign Classic. Läs mer [Läs mer](../../production/using/build-upgrade.md)

Vanliga frågor och svar om builduppgraderingen av Campaign har lagts till i vanliga frågor om Campaign. Läs mer [Läs mer](../../platform/using/faq-build-upgrade.md)

Campaign lokalt samt värdbaserade och hybridvärd-modeller beskrivs nu i ett särskilt avsnitt. [Läs mer](../../installation/using/hosting-models.md)

Matrisen med funktionerna i Campaign per värdmodell har uppdaterats och flyttats i installationshandboken. [Läs mer](../../installation/using/capability-matrix.md)

Avsnittet med avancerade funktioner i Campaign Reporting har förbättrats så att det beskriver hur URL-parametrar och -variabler används i anpassade rapporter. [Läs mer](../../reporting/using/advanced-functionalities.md)

Sidan med rapportegenskaper har omorganiserats och förbättrats för att underlätta konfigurationen. [Läs mer](../../reporting/using/properties-of-the-report.md)

Ett nytt tekniskt dokument har skapats med information om hur du migrerar från det gamla binära protokollet till HTTP/2-baserade API:er från APN-leverantören. [Läs mer](https://helpx.adobe.com/se/campaign/kb/migrate-to-apns-http2.html)

## September 2020 {#september-2020}

En anteckning har lagts till för att specificera att antalet aktiva profiler endast är tillgängligt för marknadsföringsinstanser. [Läs mer](../../platform/using/about-profiles.md#active-profiles)

Ett nytt exempel om schemaversionen har lagts till för att länka ett fält till en befintlig referenstabell. [Läs mer](../../configuration/using/examples-of-schemas-edition.md#uc-link)

En anteckning har lagts till om användningen av ytterligare data med fröadresser vid leveranser. [Läs mer](../../delivery/using/creating-seed-addresses.md#defining-addresses)

## Augusti 2020 {#aug-2020}

Läs om de bästa metoderna för leveransdesign och att skicka med Campaign i ett särskilt avsnitt. [Läs mer](../../delivery/using/delivery-best-practices.md)

Landningssidan gällande bästa praxis för levererbarhet har förbättrats för att underlätta åtkomsten till underavsnitt. [Läs mer](../../delivery/using/deliverability-key-points.md)

Instruktionsvideor finns nu tillgängliga för följande ämnen:

* [Så ställer man in trötthetshantering med typologiregler och fördefinierade filter](../../campaign/using/about-campaign-typologies.md)

* [Så skapar man ett e-postmeddelande i en kampanj](../../campaign/using/marketing-campaign-deliveries.md)

* [Så skapar man ett flerspråkigt nyhetsbrev med villkorligt innehåll](../../delivery/using/conditional-content.md)

* [Så konfigurerar och distribuera man en leveransmall](../../delivery/using/creating-a-delivery-template.md)

* [Så aktiverar och använder man AMP för e-postmeddelanden](../../delivery/using/defining-interactive-content.md)

* [Så personaliserar man e-postmeddelanden med dynamiska innehållsblock](../../delivery/using/personalization-blocks.md)

* [Så personaliserar man e-postmeddelanden med personaliseringsfält](../../delivery/using/personalization-fields.md)

* [Så hanterar man frön och korrektur i ett e-postmeddelande](../../delivery/using/steps-defining-the-target-population.md)

* [Så ställer man in en återkommande leverans](../../workflow/using/recurring-delivery.md)

* [Så ställer man in en kontinuerlig leverans](../../workflow/using/continuous-delivery.md)

Information har lagts till om de kontroller och åtgärder som ska utföras när man får felet ”Det gick inte att lösa värdnamnet” efter anslutning till en FTP-server. [Läs mer](../../platform/using/sftp-server-usage.md)

Nya användningsfall har refererats i listan [Användningsfall med arbetsflöde](../../workflow/using/about-workflow-use-cases.md):

* Automatisera skapande, redigering och publicering av innehåll
* Ställa in en process för mottagningsgodkännande innan en leverans skickas
* Anropa en instansvariabel i en fråga
* Tillämpa en delad procentsats på en grupp

Aktivitetsavsnittet **[!UICONTROL AND-join]** har berikats med ytterligare information om hur det används samt en anteckning om användningen av variabler. [Läs mer](../../workflow/using/and-join.md)

## Juli 2020 {#july-2020}

Ett användningsfall om hur man automatiskt uppdaterar en lista med en inkrementell fråga har lagts till i användningsfallen om arbetsflöde. [Läs mer](../../workflow/using/about-workflow-use-cases.md)

[Versionsinformationen](../../rn/using/latest-release.md) har omorganiseras: en [översiktssida](../../rn/using/latest-release.md) med information om buildstatus, uppgraderingsprocess, rekommendationer och viktiga länkar har lagts till. En dedikerad sida för [Gold Standard-versioner](../../rn/using/gold-standard.md) har också lagts till och [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md) har integrerats.

Ett nytt avsnitt har lagts till med riktlinjer gällande att övervaka Campaign Classic. [Läs mer](../../production/using/monitoring-guidelines.md)

Avsnittet Sekretess och samtycke har förbättrats med mer detaljerad information och användbara länkar. [Läs mer](../../platform/using/privacy-and-recommendations.md)

Sekretesshanteringen på sidan Campaign Classic har uppdaterats med information om fältet ”reglering” som nu är tillgängligt när du använder API:et, så att det går att konfigurera en automatisk process för förfrågan om användarens information. [Läs mer](https://helpx.adobe.com/ie/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

Sidan Översikt över integritetshantering har uppdaterats med information om Thailands lag för persondataskydd (PDPA) och Brasiliens Lei Geral de Proteção de Dados (LGPD). [Läs mer](https://helpx.adobe.com/se/campaign/kb/campaign-privacy-overview.html#whatisgdpr)

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

Det nya alternativet för att avpublicera en mall för transaktionsmeddelanden beskrivs i [det här avsnittet](../../message-center/using/template-unpublication.md).

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

Avsnittet Riktlinjer för levererbarhet när du startar en ny plattform har förbättrats. [Läs mer](../../delivery/using/starting-new-platform.md)

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

Installationshandboken har uppdaterats och synkroniserats med den senaste versionen av kompatibilitetsmatrisen. Stöd för nya system har lagts till. Förekomster av system som inte stöds har tagits bort. [Läs mer](../../installation/using/general-architecture.md)

Kompatibilitetsmatrisen har uppdaterats med kopplingar till Hadoop 3.0 och Snowflake FDA. [Läs mer](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

Ett tips om IP-tillhörighet har lagts till i installationshandboken. [Läs mer](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

Avsnittet Arbetsflödet för databasrensning har uppdaterats. De angivna gruppsiffrorna återspeglar nu implementeringen av kod. [Läs mer](../../production/using/database-cleanup-workflow.md)

En begränsning på FDA över HTTP har lagts till i handboken för transaktionsmeddelanden. [Läs mer](../../production/using/database-cleanup-workflow.md)

Information har lagts till om det nya alternativet som låter dig definiera en timeout-period för arbetsflödesaktiviteterna **[!UICONTROL JavaScript code]** och **[!UICONTROL Advanced JavaScript code]**. [Läs mer](../../workflow/using/sql-code-and-javascript-code.md)

Information har lagts till i den nya **[!UICONTROL Start Pending]**-vyn som är tillgänglig i noden **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]**. [Läs mer](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Handboken [Skicka push-meddelanden](../../delivery/using/about-mobile-app-channel.md) har flyttats, omorganiserats och förbättrats med tydlig information.

Den nya parametern för rapportkonfigurationen av webbadresser har dokumenterats [här](../../reporting/using/properties-of-the-report.md#defining-additional-settings).

Sidan för den **Lokala och värdbaserade funktionsmatrisen i Campaign Classic** har uppdaterats med de nya FDA-kopplingarna. [Läs mer](../../installation/using/capability-matrix.md).

Sidan **Funktionsmatrisen för Campaign Classic** har uppdaterats. [Läs mer](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

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

## December 2019 {#december-2019}

Alternativet &quot;WdbcOptions_TempDbName&quot; har lagts till i listan över alternativ i Campaign. [Läs mer](../../installation/using/configuring-campaign-options.md)

Sidan FDA-matriser har flyttats [hit](../../installation/using/remote-database-access-rights.md).

Sidan Matris för åtkomsträttigheter har flyttats [hit](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en).

Avsnittet som beskriver hur man definierar interaktivt innehåll med AMP har flyttats. [Läs mer](../../delivery/using/defining-interactive-content.md)

**Nya funktioner i version 19.2**

California Consumer Privacy Act (CCPA) – [läs mer](https://helpx.adobe.com/se/campaign/kb/acc-privacy.html)

Interaktivt material med AMP – [läs mer](../../delivery/using/defining-interactive-content.md)

Övervakning av arbetsflöde i realtid – [läs mer](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Säkra SMS-meddelanden (TLS) – [läs mer](https://helpx.adobe.com/se/campaign/kb/sms-connector-protocol-and-settings.html)

**Andra dokumentationsuppdateringar som följer med denna version**

Dokumentationen för Adobe Campaign Enhanced MTA finns nu tillgänglig. [Läs mer](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html)

Ett nytt avsnitt har lagts till om hur man felsöker ett arbetsflöde som finns i läget &quot;Starta så snart som möjligt&quot; i en kampanj. [Läs mer](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

De nya alternativen &quot;NmsOperation_DeliveryPreparationWindow&quot; och &quot;WdbcKillSessionPolicy&quot; har lagts till i listan över alternativ i Campaign. [Läs mer](../../installation/using/configuring-campaign-options.md)

Ett nytt dokument finns nu tillgänglig som beskriver grunderna för datamodellen i Adobe Campaign Classic. [Läs mer](https://helpx.adobe.com/se/campaign/kb/acc-datamodel.html)

Det nya alternativet **Maximal körtid för personalisering** i leveransegenskaperna beskrivs i det här [avsnittet](../../delivery/using/personalization-fields.md#timing-out-personalization).

Exemplen för API-anrop med en **HttpServletRequest** med logon() och query() har uppdaterats. [Läs mer](../../configuration/using/web-service-calls.md).

En rekommendation för attributet **sqlDefault** i schemadefinitionen har lagts till. [Läs mer](../../configuration/using/schema/attribute.md)).

Integrationen mellan Adobe Campaign och Adobe Real-time Customer Data Platform finns nu med i handboken **Integrera med Adobe Experience Cloud**. [Läs mer](../../integrations/using/about-campaign-integrations.md).

## November 2019 {#november-2019}

En varning har lagts till i avsnitten [Multiplexering av mid-sourcing-servern](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) och [Stöd för flera kontrollinstanser](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances) som beskriver att dessa driftsättningar inte har stöd för fullständigt värdbaserade klienter och hybridklienter.

Ett nytt avsnitt har lagts till som beskriver hur man forcerar teckenkodningen som används för att skicka e-postmeddelanden. [Läs mer](../../delivery/using/sending-messages.md#character-encoding)

Avsnittet Åtkomsthantering har uppdaterats med **Rättigheten till personuppgifter**. [Läs mer](../../platform/using/access-management-named-rights.md)

Information har lagts till för att specificera att innehåll i personaliseringsfält högst får innehålla 1 024 tecken. [Läs mer](../../delivery/using/personalization-fields.md)

Kontrollpanelens dokumentation har integrerats i den nya dokumentationsuppsättningen för samarbete. [Läs mer](https://docs.adobe.com/content/help/sv-SE/control-panel/using/control-panel-home.html)

Starthandboken Bästa praxis för leverans har uppdaterats. [Läs mer](../../delivery/using/delivery-best-practices.md)

## Oktober 2019 {#october-2019}

Listan med felmeddelanden i Campaign Standard och Campaign Classic har uppdaterats. [Läs mer](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/error_messages/error_codes.html)

Starthandboken GDPR har förbättrats och berikats. Det finns nu en dokumentation om sekretesshantering som inkluderar GDPR och CCPA. [Läs mer](https://helpx.adobe.com/se/campaign/kb/campaign-privacy.html)

En ny sida med felsökning har lagts till för spårning i Campaign Classic. [Läs mer](https://helpx.adobe.com/se/campaign/kb/classic-tracking-troubleshooting.html).

En ny sida med bästa praxis för datakopplingen i Adobe Analytics har lagts till. [Läs mer om datakopplingen i Adobe Analytics](../../platform/using/adobe-analytics-data-connector.md)

Starthandboken Bästa praxis för leverans har flyttats och uppdaterats. [Läs mer](../../delivery/using/delivery-best-practices.md)

En rekommendation har lagts till i dokumentationen om SMS-kanaler för att undvika problem när flera externa konton använder kopplingen till Extended generic SMPP med samma leverantörskonto. [Läs mer](../../delivery/using/sms-channel.md#automatic-reply)

Information om hur man förhindrar simultana exekveringar av arbetsflöden har lagts till i aktivitetsdokumentationen för Scheduler. [Läs mer](../../workflow/using/scheduler.md)

Stegen för att konfigurera inkorgsåtergivning på lokala installationer har lagts till i dokumentationen. [Läs mer](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

## September 2019 {#september-2019}

En ny sida med allmänna riktlinjer om hur man underhåller Campaign Classic har lagts till. [Läs mer](../../production/using/monitoring-guidelines.md)

Information om övervakning av arbetsflöden har centraliserats till ett nytt dedikerat avsnitt. [Läs mer](../../workflow/using/monitoring-workflow-execution.md).

En ny sida med allmänna riktlinjer gällande spårning i Adobe Campaign Classic har lagts till. [Läs mer](https://helpx.adobe.com/se/campaign/kb/acc-tracking.html).

Bästa praxis för prestandaförbättringar i arbetsflöden och leveranser har uppdaterats. [Läs mer om arbetsflöden](../../workflow/using/workflow-best-practices.md) och [leveranser](../../delivery/using/delivery-performances.md#best-practices-performance).

## Maj 2019 {#release-19-1}

**Nya funktioner i version 19.1**

Kontrollpanel – [läs mer](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)

Verifieringskedja – [läs mer](../../production/using/audit-trail.md)

**Andra dokumentationsuppdateringar som följer med denna version**

Nya frågor och svar har skapats för uppgradering av versioner. [Läs mer](https://helpx.adobe.com/se/campaign/kb/build-upgrade-faq.html)

[Kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) har uppdaterats. Listan över databassystem som det finns stöd för har uppdaterats såväl som Android-/iOS-versioner och relaterade SDK:er. [Kompatibilitetsmatrisen 19.0](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix-19-0.html) har arkiverats.

Sidan &quot;Inaktuella och borttagna funktioner i Campaign Classic&quot; har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/deprecated-and-removed-features.html)

Beskrivningen om serverkonfigurationsfilen har lagts till i installationshandboken. [Läs mer](../../installation/using/the-server-configuration-file.md)

Ett avsnitt har lagts till som beskriver installations- och konfigurationsstegen för värdbaserade modeller och hybridmodeller. [Läs mer](../../installation/using/hosting-models.md)

Ett avsnitt har lagts till som beskriver avinstallation av Campaign-servern. [Läs mer](../../installation/using/uninstalling-campaign.md)

Starthandböckerna [Säkerhet](https://helpx.adobe.com/se/campaign/kb/acc-security.html), [Leverans](../../delivery/using/deliverability-key-points.md) och [Sekretess](../../platform/using/privacy-management.md) har uppdaterats.

Beskrivningen av alternativet arbetsflöde före bearbetning har uppdaterats för att återspegla produktändringar. [Läs mer](../../workflow/using/data-loading--file-.md)

Den tekniska dokumentationen för utlösare i Marketing Cloud har uppdaterats. [Läs mer](../../integrations/using/about-triggers.md)

Listan med felmeddelanden har uppdaterats. [Läs mer](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/error_messages/error_codes.html)

Ytterligare information om SOAP-autentiseringsmetoder för transaktionsmeddelanden har lagts till. [Läs mer](../../message-center/using/event-description.md)

Konfigurationsstegen för Apache har uppdaterats. [Läs mer](../../installation/using/integration-into-a-web-server-for-linux.md)

En ny sida har lagts till med en lista över slutpunkter för Campaign Standard och Campaign Classic. [Läs mer](../../installation/using/campaign-network-endpoints.md)

Artikeln Bästa praxis för datapaket har uppdaterats. [Läs mer](../../configuration/using/data-model-best-practices.md)

Dokumentationen Hantera erbjudanden har uppdaterats med ett nytt avsnitt som listar bästa praxis. [Läs mer](../../interaction/using/interaction-best-practices.md)

En ny kunskapsbasartikel om hur man använder erbjudandekatalogen i Adobe Campaign Classic har skapats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/offer-best-practices.html)

Avsnittet Underliggande arbetsflödesaktivitet har förbättrats med ett exempel på användning. [Läs mer](../../workflow/using/sub-workflow.md)

Sidan med en [matris för lokala och värdbaserade funktioner i Campaign Classic](../../installation/using/capability-matrix.md) har uppdaterats med information om e-postmeddelanden som är osynliga för leveransmottagarna.

Dokumentationen om transaktionsmeddelanden har uppdaterats med ett kort avsnitt om mallpublicering. [Läs mer](../../message-center/using/template-publication.md)

Avsnittet Obearbetade och ej levererade e-postmeddelanden har uppdaterats med mer information om fälten Vidarebefordringsadress och Adress för fel. [Läs mer](../../installation/using/deploying-an-instance.md)

Ett nytt avsnitt om bästa praxis för arbetsflödesplanering har lagts till. [Läs mer](../../workflow/using/workflow-best-practices.md)

Två nya alternativ har lagts till i listan över alternativ i Campaign: XtkSecurity_Restrict_EditXML och NmsOperation_OperationMgtDebug.
[Läs mer](../../installation/using/configuring-campaign-options.md)

Information har lagts till om de olika externa konton som är tillgängliga i Campaign Classic och hur de konfigureras.
[Läs mer](../../installation/using/external-accounts.md)

Avsnittet Analysverktyg för datakoppling har uppdaterats för att återspegla ändringar i gränssnittet.
[Läs mer](../../platform/using/adobe-analytics-data-connector.md)

Information har lagts till om faktureringsrapporten.
[Läs mer](../../production/using/monitoring-processes.md)

Dokumentation om integrationen mellan delade publiker har uppdaterats.
[Läs mer](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)

Följande tekniska dokumentation har uppdaterats: [SMS-kopplingsprotokoll och -inställningar](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html) och [Automatisk sekvensgenerering](https://helpx.adobe.com/se/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence).

Avsnittet Tekniskt arbetsflöde har uppdaterats. [Läs mer](../../workflow/using/about-technical-workflows.md)

Inställningsproceduren för domännamnet i Campaign har förbättrats och uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/domain-name-delegation.html)

Migreringsproceduren för Android-appar från Google Cloud Messaging (GCM) till Firebase Cloud Messaging (FCM) har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/migrate-to-fcm.html)

Handboken Ändra storlek på maskinvara i Campaign har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/hardware-sizing-guide.html)

Information har lagts till om query banding för det externa Teradata-kontot. [Läs mer](../../installation/using/external-accounts.md)

## Januari 2019{#release-doc-16-01-2019}

Den tekniska dokumentationen för utlösare i Marketing Cloud har uppdaterats. [Läs mer](../../integrations/using/about-triggers.md)

Ett meddelande har lagts till i avsnittet Godkännande av erbjudande för att specificera att &quot;Godkänt innehåll&quot; indikerar att godkännandeprocessen för innehåll har uppnåtts. Detta gäller oavsett om alla erbjudanden har aktiverats/godkänts eller inte. [Läs mer](../../interaction/using/offer-catalog-overview.md)

Ett nytt avsnitt har lagts till i installationshandboken med alternativ från noderna administration/plattform/alternativ. [Läs mer](../../installation/using/configuring-campaign-options.md)

Information har lagts till om användningen av fröadresser för att skydda din e-postlista. [Läs mer](../../delivery/using/creating-seed-addresses.md)

De viktigaste stegen när du skapar och skickar en leverans har grupperats om till ett nytt avsnitt med referenser till de olika kanalerna vid behov. [Läs mer](../../delivery/using/steps-about-delivery-creation-steps.md)

Avsnittet [E-postarkivering](../../installation/using/email-archiving.md) har flyttats, omorganiserats och förbättrats med tydlig information:

* Bästa praxis har lagts till för e-postmeddelanden per anslutning och IP-adressers parametrar när man skickar med BCC.

* Vi har uppdaterat stegen gällande att uppgradera till det nya systemet för e-postarkivering (osynlig för leveransmottagarna). Detta gäller om du redan använde e-postarkivering med en äldre version (före Adobe Campaign 17.2 – build 8795).

Ett användningsfall l har lagts till i handboken Automatisera med arbetsflöden: skicka personaliserade aviseringar till operatörer. [Läs mer](../../workflow/using/sending-personalized-alerts-to-operators.md)

Avsnittet &quot;Migrera till en ny version&quot; har uppdaterats. Dokumentationen innehåller nu bara information om stegen för att migrera till Adobe Campaign Classic version 7 från en äldre version. Detta eftersom det inte längre är möjligt att migrera till Adobe Campaign version 6.11. [Läs mer](../../migration/using/about-migration.md)

Avsnittet &quot;Återförsök efter ett tillfälligt leveransfel&quot; har klargjorts. [Läs mer](../../delivery/using/understanding-delivery-failures.md)

Länkar till avsnittet &quot;Redigerare för digitalt innehåll&quot; har lagts till i avsnittet &quot;Definiera e-postinnehållet&quot;. [Läs mer](../../delivery/using/defining-the-email-content.md)

Avsnittet &quot;Transaktionsmeddelandets arkitektur&quot; har uppdaterats med en varning som specificerar att man inte kan installera kontroll- och körningsinstanserna på samma maskin. [Läs mer](../../message-center/using/transactional-messaging-architecture.md)

Avsnittet &quot;Arbetsflödesövervakning&quot; har uppdaterats med ett meddelande för versioner mellan 8700 och 8977 (18.10) inklusive en länk till den tekniska dokumentationen om hur Workflow HeatMap-paketet installeras för dessa versioner. [Läs mer](../../workflow/using/heatmap.md)

Ett användningsfall har lagts till om hur du skickar ett e-postmeddelande med anpassade datafält med hjälp av berikandeaktiviteten i ett arbetsflöde. [Läs mer](../../workflow/using/email-enrichment-with-custom-date-fields.md)

Videor med funktioner har flyttats [hit](https://docs.adobe.com/content/help/sv-SE/campaign-classic-learn/tutorials/overview.html).
