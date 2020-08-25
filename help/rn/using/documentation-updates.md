---
title: Adobe Campaign Classic – dokumentationsuppdateringar
description: Den här sidan visar alla nya funktioner och dokumentationsuppdateringar för varje version av Adobe Campaign Classic.
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
source-git-commit: 70efc8a7f1fab68d73e36b4373116c4aaaa0af5d
workflow-type: tm+mt
source-wordcount: '7164'
ht-degree: 94%

---


# Dokumentationsuppdateringar{#documentation-updates}

Den här sidan visar alla nya funktioner och dokumentationsuppdateringar per månad och version av Campaign.

Du kan även läsa [Versionsinformation om Adobe Campaign Classic](../../rn/using/latest-release.md) för mer information.

## Augusti 2020 {#aug-2020}

Lär dig de bästa metoderna för leveransdesign och att skicka med Campaign i ett särskilt avsnitt. [Läs mer](../../delivery/using/delivery-best-practices.md)

Landningssidan för bästa praxis för slutleverans har förbättrats för att underlätta tillgången till underavsnitt. [Läs mer](../../delivery/using/deliverability-key-points.md)

Instruktionsvideor finns nu tillgängliga för följande ämnen:

* [Ställa in trötthetshantering med typologiregler och fördefinierade filter](../../campaign/using/about-campaign-typologies.md)

* [Så här skapar du ett e-postmeddelande i en kampanj](../../campaign/using/marketing-campaign-deliveries.md)

* [Skapa ett flerspråkigt nyhetsbrev med villkorat innehåll](../../delivery/using/conditional-content.md)

* [Konfigurera och distribuera en leveransmall](../../delivery/using/creating-a-delivery-template.md)

* [Så här aktiverar och använder du AMP för e-post](../../delivery/using/defining-interactive-content.md)

* [Så här personaliserar du e-postmeddelanden med dynamiska innehållsblock](../../delivery/using/personalization-blocks.md)

* [Skräddarsy e-postmeddelanden med personaliseringsfält](../../delivery/using/personalization-fields.md)

* [Hantera startvärden och korrektur i ett e-postmeddelande](../../delivery/using/steps-defining-the-target-population.md)

* [Så här ställer du in en återkommande leverans](../../workflow/using/recurring-delivery.md)

* [Konfigurera kontinuerlig leverans](../../workflow/using/continuous-delivery.md)

Information har lagts till om de kontroller och åtgärder som ska utföras vid hämtning av felet&quot;Det gick inte att lösa värdnamnet&quot; efter anslutning till en FTP-server. [Läs mer](../../platform/using/sftp-server-usage.md)

Nya användningsfall har refererats i listan över [arbetsflödesanvändningsfall](../../workflow/using/about-workflow-use-cases.md):

* Automatisera framtagning, utgåva och publicering av innehåll
* Ställa in en process för mottagningsgodkännande innan en leverans skickas
* Anropa en förekomstvariabel i en fråga
* Använda en delad procentsats på en population

Aktivitetsavsnittet har berikats med ytterligare information om hur det används samt en anteckning om användningen av variabler. **[!UICONTROL AND-join]** [Läs mer](../../workflow/using/and-join.md)

## Juli 2020 {#july-2020}

Ett användningsexempel om hur du automatiskt uppdaterar en lista med en stegvis fråga har lagts till i arbetsflödets användningsfall. [Läs mer](../../workflow/using/about-workflow-use-cases.md)

Versionsinformationen [](../../rn/using/latest-release.md) har ordnats om: en [översiktssida](../../rn/using/latest-release.md) med information om byggstatus, uppgraderingsprocess, rekommendationer och viktiga länkar har lagts till. En dedikerad sida för [Gold Standard-versioner](../../rn/using/gold-standard.md) har också lagts till och [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md) har integrerats.

Ett nytt avsnitt har lagts till med riktlinjer för övervakning av Campaign Classic. [Läs mer](../../production/using/monitoring-guidelines.md)

Avsnittet Sekretess och samtycke har förbättrats med mer detaljerad information och användbara länkar. [Läs mer](../../platform/using/privacy-and-recommendations.md).

Sekretesshantering på Campaign Classic-sidan har uppdaterats med information om fältet&quot;Reglering&quot; som nu är tillgängligt när du använder API:t för att konfigurera automatisk process för förfrågningar om sekretess. [Läs mer](https://helpx.adobe.com/ie/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

Sidan Sekretesshanteringsöversikt har uppdaterats med information om Thailands lag för skydd av personuppgifter (PDPA) och Brasiliens Lei Geral de Proteção de Dados (LGPD). [Läs mer](https://helpx.adobe.com/campaign/kb/campaign-privacy-overview.html#whatisgdpr)

Information har lagts till i delarbetsflödets loggar och beteende vid fel. [Läs mer](../../workflow/using/sub-workflow.md)

Bästa tillvägagångssätt har lagts till i **[!UICONTROL Scheduler]** aktivitetsavsnittet. [Läs mer](../../workflow/using/scheduler.md)

## Juni 2020 {#june-2020}

Avsnittet Ta bort en adress i karantän har uppdaterats. Detta inkluderar förtydligande av de fall där adresser automatiskt tas bort från karantänlistan. [Läs mer](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

Användningsfall har lagts till om hur data [krypteras](../../workflow/using/how-to-use-workflow-data.md#use-case-gpg-encrypt) och [dekrypteras](../../workflow/using/importing-data.md#use-case-gpg-decrypt) med Kontrollpanelen och arbetsflödena i Campaign.

De båda termerna &quot;vitlistad&quot; och &quot;svartlistad&quot; har tagits bort från dokumentationen för Adobe Campaign. Vissa förekomster av dessa termer kan fortfarande förekomma i produktgränssnittet, alternativnamn och intern kod men ersätts i kommande versioner av Campaign med &quot;blockeringslista&quot; och &quot;tillåtelselista&quot;.

The Experience Cloud Triggers and Adobe Campaign Classic integration page has been moved [here](../../integrations/using/about-triggers.md).

## 20.2 – 08/06/2020{#release-20-2}

**Nya funktioner i denna version**

Stöd för uttryckssymboler – [läs mer](../../delivery/using/customizing-emoticon-list.md)

Azure Synapse FDA-koppling – [läs mer](../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse)

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

FDA-rättighetstabellen har flyttats till dokumentationen Åtkomst till en extern databas (FDA). [Läs mer](../../platform/using/remote-database-access-rights.md)

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

Riktlinjerna för åtkomsthantering har uppdaterats med mer information om namngivna rättigheter. [Läs mer](../../platform/using/access-management.md#named-rights)

## Februari 2020 {#february-2020}

Ett nytt avsnitt finns nu tillgängligt som beskriver bästa praxis och viktiga rekommendationer när datamodellen i Adobe Campaign utformas. [Läs mer](../../configuration/using/data-model-best-practices.md)

Ett nytt avsnitt finns nu tillgängligt om Konfigurationer av teknisk e-post. [Läs mer](../../installation/using/email-deliverability.md)

Vanliga frågor och svar om levererbarheten har uppdaterats med mer information om felmeddelandet om att &quot;kvoterna har uppfyllts&quot;. [Läs mer](https://helpx.adobe.com/se/campaign/kb/acc-deliverability-faq.html#FAQ)

AMP för e-post stöds nu av nya e-postleverantörer: den relaterade dokumentationen har uppdaterats. [Läs mer](../../delivery/using/defining-interactive-content.md)

Avsnittet E-postarkivering har förbättrats. [Läs mer](../../installation/using/email-archiving.md#recommendations-and-limitations)

## 20.1 - 17/02/2020{#release-20-1}

**Nya funktioner i denna version**

Snowflake FDA-koppling – [läs mer](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)

Förbättringar på Hadoop FDA-koppling – [läs mer](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3)

**Andra dokumentationsuppdateringar som följer med denna version**

Handböckerna för [installation](../../installation/using/before-reading.md), [produktion](../../production/using/foreword.md) och [konfiguration](../../configuration/using/additional-parameters.md) har uppdaterats med den nya systemenheten som används vid uppstart av tjänsten nlserver. /Etc/init.d/nlserver6 kan fortfarande användas men Adobe rekommenderar att du nu använder kommandot systemctl för att interagera med tjänsten nlserver.

Installationshandboken har uppdaterats och synkroniserats med den senaste versionen av kompatibilitetsmatrisen. Stöd för nya system har lagts till. Förekomster av system som inte stöds har tagits bort. [Läs mer](../../installation/using/before-reading.md)

Kompatibilitetsmatrisen har uppdaterats med kopplingar till Hadoop 3.0 och Snowflake FDA. [Läs mer](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html)

Ett tips om IP-tillhörighet har lagts till i installationshandboken. [Läs mer](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

Avsnittet Arbetsflödet för databasrensning har uppdaterats. De angivna gruppsiffrorna återspeglar nu implementeringen av kod. [Läs mer](../../production/using/database-cleanup-workflow.md)

En begränsning på FDA över HTTP har lagts till i handboken för transaktionsmeddelanden. [Läs mer](../../production/using/database-cleanup-workflow.md)

Information har lagts till om det nya alternativet som låter dig definiera en timeout-period för arbetsflödesaktiviteterna **[!UICONTROL JavaScript code]** och **[!UICONTROL Advanced JavaScript code]**. [Läs mer](../../workflow/using/sql-code-and-javascript-code.md)

Information har lagts till i den nya **[!UICONTROL Start Pending]**-vyn som är tillgänglig i noden **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]**. [Läs mer](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Handboken [Skicka push-meddelanden](../../delivery/using/about-mobile-app-channel.md) har flyttats, omorganiserats och förbättrats med tydlig information.

Den nya parametern för rapportkonfigurationen av webbadresser har dokumenterats [här](../../reporting/using/properties-of-the-report.md#defining-additional-settings).

Sidan för den **Lokala och värdbaserade funktionsmatrisen i Campaign Classic** har uppdaterats med de nya FDA-kopplingarna. [Läs mer](https://helpx.adobe.com/se/campaign/kb/acc-on-prem-vs-hosted.html)

Sidan **Funktionsmatrisen för Campaign Classic** har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html)

Det nya **[!UICONTROL Cleanup of Nmsaddress]**-arbetsflödet har dokumenterats [här](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress).

En begränsning har lagts till när en frågeaktivitet används i ett arbetsflöde. [Läs mer](../../workflow/using/query.md).

Ett nytt avsnitt har lagts till för att i detalj dokumentera de förbättrade verifieringsreglerna gällande e-postadresser för att skicka en adress till karantän om ett mjukt fel uppstår. [Läs mer](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

Parametern i konfigurationsfilen som anger om en instans använder Enhanced MTA eller inte är nu dokumenterad. [Läs mer](../../installation/using/the-server-configuration-file.md#mta)

## Januari 2020 {#january-2020}

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

Sidan FDA-matriser har flyttats [hit](../../platform/using/remote-database-access-rights.md).

Sidan Matris för åtkomsträttigheter har flyttats [hit](https://docs.adobe.com/content/help/sv-SE/campaign-classic/using/getting-started/administration-basics/assets/accessrights.pdf).

Avsnittet som beskriver hur man definierar interaktivt innehåll med AMP har flyttats. [Läs mer](../../delivery/using/defining-interactive-content.md)

## 19.2 - 02/12/2019{#release-19-2}

**Nya funktioner i denna version**

California Consumer Privacy Act (CCPA) – [läs mer](https://helpx.adobe.com/se/campaign/kb/acc-privacy.html)

Interaktivt material med AMP – [läs mer](../../delivery/using/defining-interactive-content.md)

Övervakning av arbetsflöde i realtid – [läs mer](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

Säkra SMS-meddelanden (TLS) – [läs mer](https://helpx.adobe.com/se/campaign/kb/sms-connector-protocol-and-settings.html)

**Andra dokumentationsuppdateringar som följer med denna version**

Dokumentationen för Adobe Campaign Enhanced MTA finns nu tillgänglig. [Läs mer](https://helpx.adobe.com/se/campaign/kb/acc-campaign-enhanced-mta.html)

Ett nytt avsnitt har lagts till om hur man felsöker ett arbetsflöde som finns i läget &quot;Starta så snart som möjligt&quot; i en kampanj. [Läs mer](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

De nya alternativen &quot;NmsOperation_DeliveryPreparationWindow&quot; och &quot;WdbcKillSessionPolicy&quot; har lagts till i listan över alternativ i Campaign. [Läs mer](../../installation/using/configuring-campaign-options.md)

Ett nytt dokument finns nu tillgänglig som beskriver grunderna för datamodellen i Adobe Campaign Classic. [Läs mer](https://helpx.adobe.com/se/campaign/kb/acc-datamodel.html)

Det nya alternativet **Maximal körtid för personalisering** i leveransegenskaperna beskrivs i det här [avsnittet](../../delivery/using/personalization-fields.md#timing-out-personalization).

Exemplen för API-anrop med en **HttpServletRequest** med logon() och query() har uppdaterats. [Läs mer](../../configuration/using/web-service-calls.md).

En rekommendation för attributet **sqlDefault** i schemadefinitionen har lagts till. [Läs mer](../../configuration/using/elements-and-attributes.md#attribute-description).

Integrationen mellan Adobe Campaign och Adobe Real-time Customer Data Platform finns nu med i handboken **Integrera med Adobe Experience Cloud**. [Läs mer](../../integrations/using/about-campaign-integrations.md).

## November 2019 {#november-2019}

En varning har lagts till i avsnitten [Multiplexering av mid-sourcing-servern](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) och [Stöd för flera kontrollinstanser](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances) som beskriver att dessa driftsättningar inte har stöd för fullständigt värdbaserade klienter och hybridklienter.

Ett nytt avsnitt har lagts till som beskriver hur man forcerar teckenkodningen som används för att skicka e-postmeddelanden. [Läs mer](../../delivery/using/sending-messages.md#character-encoding)

Avsnittet Åtkomsthantering har uppdaterats med **Rättigheten till personuppgifter**. [Läs mer](../../platform/using/access-management.md#named-rights)

Information har lagts till för att specificera att innehåll i personaliseringsfält högst får innehålla 1 024 tecken. [Läs mer](../../delivery/using/personalization-fields.md)

Kontrollpanelens dokumentation har integrerats i den nya dokumentationsuppsättningen för samarbete. [Läs mer](https://docs.adobe.com/content/help/sv-SE/control-panel/using/control-panel-home.html)

Starthandboken Bästa praxis för leverans har uppdaterats. [Läs mer](../../delivery/using/delivery-best-practices.md)

## Oktober 2019 {#october-2019}

Listan med felmeddelanden i Campaign Standard och Campaign Classic har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

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

Bästa praxis för prestandaförbättringar i arbetsflöden och leveranser har uppdaterats. [Läs mer om arbetsflöden](../../workflow/using/workflow-best-practices.md) och [leveranser](../../delivery/using/monitoring-a-delivery.md#best-practices-performance).

## 19.1 - 30/05/2019{#release-19-1}

**Nya funktioner i denna version**

Kontrollpanel – [läs mer](https://docs.adobe.com/content/help/sv-SE/control-panel/using/control-panel-home.html)

Verifieringskedja – [läs mer](../../production/using/audit-trail.md)

**Andra dokumentationsuppdateringar som följer med denna version**

Nya frågor och svar har skapats för uppgradering av versioner. [Läs mer](https://helpx.adobe.com/se/campaign/kb/build-upgrade-faq.html)

[Kompatibilitetsmatrisen](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html) har uppdaterats. Listan över databassystem som det finns stöd för har uppdaterats såväl som Android-/iOS-versioner och relaterade SDK:er. [Kompatibilitetsmatrisen 19.0](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix-19-0.html) har arkiverats.

Sidan &quot;Inaktuella och borttagna funktioner i Campaign Classic&quot; har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/deprecated-and-removed-features.html)

Beskrivningen om serverkonfigurationsfilen har lagts till i installationshandboken. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_The_server_configuration_file.html)

Ett avsnitt har lagts till som beskriver installations- och konfigurationsstegen för värdbaserade modeller och hybridmodeller. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_Introduction.html)

Ett avsnitt har lagts till som beskriver avinstallation av Campaign-servern. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Uninstalling_Campaign.html)

Starthandböckerna [Säkerhet](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html), [Leverans](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) och [Sekretess](https://helpx.adobe.com/se/campaign/kb/acc-privacy.html) har uppdaterats.

Beskrivningen av alternativet arbetsflöde före bearbetning har uppdaterats för att återspegla produktändringar. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Data_loading__file_)

Den tekniska dokumentationen för utlösare i Marketing Cloud har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/triggers-and-campaign.html)

Listan med felmeddelanden har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Ytterligare information om SOAP-autentiseringsmetoder för transaktionsmeddelanden har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Event_description.html)

Konfigurationsstegen för Apache har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Integration_into_a_Web_server.html#Configuring_Apache_web_server_in_RHEL)

En ny sida har lagts till med en lista över slutpunkter för Campaign Standard och Campaign Classic. [Läs mer](https://helpx.adobe.com/se/campaign/kb/campaign-endpoints.html)

Artikeln Bästa praxis för datapaket har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/data-package-best-practices.html)

Dokumentationen Hantera erbjudanden har uppdaterats med ett nytt avsnitt som listar bästa praxis. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/ITA_Interaction_Overview_Interaction_best_practices.html)

En ny kunskapsbasartikel om hur man använder erbjudandekatalogen i Adobe Campaign Classic har skapats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/offer-best-practices.html)

Avsnittet Underliggande arbetsflödesaktivitet har förbättrats med ett exempel på användning. [Läs mer](../../workflow/using/sub-workflow.md)

Kunskapsbasartikeln om [funktionsmatrisen för lokal och värdbaserad Campaign Classic](https://helpx.adobe.com/se/campaign/kb/acc-on-prem-vs-hosted.html) har uppdaterats med information om arkivering av e-post.

Dokumentationen om transaktionsmeddelanden har uppdaterats med ett kort avsnitt om mallpublicering. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/MCE_Template_publication.html)

Avsnittet Obearbetade och ej levererade e-postmeddelanden har uppdaterats med mer information om fälten Vidarebefordringsadress och Adress för fel. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Deploying_an_instance.html#Unprocessed_bounce_mails)

Ett nytt avsnitt om bästa praxis för arbetsflödesplanering har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Workflow_best_practices.html#Execution_and_performance)

Två nya alternativ har lagts till i listan över alternativ i Campaign: XtkSecurity_Restrict_EditXML och NmsOperation_OperationMgtDebug.
[Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Information har lagts till om de olika externa konton som är tillgängliga i Campaign Classic och hur de konfigureras.
[Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html)

Avsnittet Analysverktyg för datakoppling har uppdaterats för att återspegla ändringar i gränssnittet.
[Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Information har lagts till om faktureringsrapporten.
[Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Billing_report)

Dokumentation om integrationen mellan delade publiker har uppdaterats.
[Läs mer](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

Följande tekniska dokumentation har uppdaterats: [SMS-kopplingsprotokoll och -inställningar](https://helpx.adobe.com/se/campaign/kb/sms-connector-protocol-and-settings.html) och [Automatisk sekvensgenerering](https://helpx.adobe.com/se/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence).

Avsnittet Tekniskt arbetsflöde har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

Inställningsproceduren för domännamnet i Campaign har förbättrats och uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/domain-name-delegation.html)

Migreringsproceduren för Android-appar från Google Cloud Messaging (GCM) till Firebase Cloud Messaging (FCM) har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/migrate-to-fcm.html)

Handboken Ändra storlek på maskinvara i Campaign har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/hardware-sizing-guide.html)

Information har lagts till om query banding för det externa Teradata-kontot. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#External_database_external_account)

## Januari 2019{#release-doc-16-01-2019}

Den tekniska dokumentationen för utlösare i Marketing Cloud har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/triggers-and-campaign.html)

Ett meddelande har lagts till i avsnittet Godkännande av erbjudande för att specificera att &quot;Godkänt innehåll&quot; indikerar att godkännandeprocessen för innehåll har uppnåtts. Detta gäller oavsett om alla erbjudanden har aktiverats/godkänts eller inte. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/ITA_Managing_an_offer_catalog_Approving_and_activating_an_offer.html#Approving_offer_content)

Ett nytt avsnitt har lagts till i installationshandboken med alternativ från noderna administration/plattform/alternativ. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

Information har lagts till om användningen av fröadresser för att skydda din e-postlista. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

De viktigaste stegen när du skapar och skickar en leverans har grupperats om till ett nytt avsnitt med referenser till de olika kanalerna vid behov. [Läs mer](../../delivery/using/steps-about-delivery-creation-steps.md)

Avsnittet [E-postarkivering](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) har flyttats, omorganiserats och förbättrats med tydlig information:

* Bästa praxis har lagts till för e-postmeddelanden per anslutning och IP-adressers parametrar när man skickar med BCC. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Best_practices)

* Vi har uppdaterat stegen gällande att uppgradera till det nya systemet för e-postarkivering (osynlig för leveransmottagarna). Detta gäller om du redan använde e-postarkivering med en äldre version (före Adobe Campaign 17.2 – build 8795). [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Ett användningsfall l har lagts till i handboken Automatisera med arbetsflöden: skicka personaliserade aviseringar till operatörer. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_personalized_alerts_to_operators.html)

Avsnittet &quot;Migrera till en ny version&quot; har uppdaterats. Dokumentationen innehåller nu bara information om stegen för att migrera till Adobe Campaign Classic version 7 från en äldre version. Detta eftersom det inte längre är möjligt att migrera till Adobe Campaign version 6.11. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

Avsnittet &quot;Återförsök efter ett tillfälligt leveransfel&quot; har klargjorts. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Retries_after_a_delivery_temporary_failure)

Länkar till avsnittet &quot;Redigerare för digitalt innehåll&quot; har lagts till i avsnittet &quot;Definiera e-postinnehållet&quot;. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Message_content)

Avsnittet &quot;Transaktionsmeddelandets arkitektur&quot; har uppdaterats med en varning som specificerar att man inte kan installera kontroll- och körningsinstanserna på samma maskin. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Transactional_messaging_architecture.html)

Avsnittet &quot;Arbetsflödesövervakning&quot; har uppdaterats med ett meddelande för versioner mellan 8700 och 8977 (18.10) inklusive en länk till den tekniska dokumentationen om hur Workflow HeatMap-paketet installeras för dessa versioner. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#About_the_Workflow_HeatMap)

Ett användningsfall har lagts till om hur du skickar ett e-postmeddelande med anpassade datafält med hjälp av berikandeaktiviteten i ett arbetsflöde. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Email_enrichment_with_custom_date_fields.html)

Videor med funktioner har flyttats [hit](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/overview.html).

Två tekniska dokument har lagts till om [Teradata](https://helpx.adobe.com/se/campaign/kb/campaign_fda_teradata.html) och [MySQL 5.7](https://helpx.adobe.com/se/campaign/kb/campaign_fda_mysql.html).

## 18.10 - 05/11/2018{#release-18-10}

**Nya funktioner i denna version**

Förbättringar av push-meddelanden – [läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Integrating_the_SDK_into_the_mobile_application)

Datahanteringsaktivitet i SQL – [läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#SQL_Data_Management)

Övervaka arbetsflöden – [läs mer](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Workflow_monitoring)

**Andra dokumentationsuppdateringar som följer med denna version**

API:er i Campaign Classic finns nu på en [dedikerad sida](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html). Om du använder filen jsapi.chm bör du nu använda den nya versionen online.

Kompatibilitetsmatrisen har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html)

Sidan &quot;Inaktuella och borttagna funktioner i Campaign Classic&quot; har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/deprecated-and-removed-features.html)

I [versionsinformationen](https://docs.adobe.com/content/help/sv-SE/campaign-classic/using/release-notes/latest-release.html) och [äldre versionsinformation](https://docs.campaign.adobe.com/doc/AC/en/RN_legacy.html) har en varning lagts till för versioner som har återkallats. Kumulativa versioner för 17.9, 18.4 och 18.6 har också lagts till.

Starthandböckerna [Säkerhet](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html), [Leverans](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) och [Versionsuppgradering](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) har uppdaterats.

Starthandboken [Sekretess](https://helpx.adobe.com/se/campaign/kb/acc-privacy.html) har uppdaterats med information om hur man anropar API:et externt och hur man använder queryDef för att fråga efter status och ladda ned GDPR-filen.

Ett användningsfall har lagts till för transaktionsmeddelanden för att lägga till e-postbilagor direkt till utgående utskick. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/MCE_Use_case_Purpose.html)

Avsnittet om felsökning för anslutningsgränsvärden har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Connection_thresholds.html)

Ett avsnitt har lagts till om hur man konfigurerar en proxyanslutning. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Proxy_connection_configuration)

Avsnittet om begränsningar av auktoriserade externa kommandon har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Restricting_authorized_external_commands)

Ett avsnitt om felsökning som rör SFTP-användning har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

Översiktsavsnittet i handboken Skicka meddelanden har omstrukturerats. Information har lagts till om den globala processen för att skapa leveranser och de olika leveranstyperna. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_About_deliveries_and_channels_Communication_channels.html)

Listan med felmeddelanden har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Avsnittet om hur man använder fröadresser flyttades till översiktskapitlet för handboken Skicka meddelanden. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

Ett nytt användningsfall för arbetsflöde har lagts till: hantera uppdateringar från associerade exekveringar av arbetsflöden. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Coordinating_data_updates.html)

Avsnittet &quot;Inkorgsåtergivning&quot; har uppdaterats med ytterligare information om Litmus och en mer detaljerad procedur. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html#Multiplexing_the_mid-sourcing_server)

Avsnittet &quot;SpamAssassin&quot; har förbättrats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_SpamAssassin.html)

Ett användningsfall har lagts till i avsnittet &quot;Hantera reklamtrötthet med tryckregler&quot;. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/CMP_Campaign_Optimization_Pressure_rules.html#Sending_only_the_highest-weighted_messages)

Ett nytt användningsfall finns nu tillgängligt som beskriver hur man skapar ett arbetsflöde för leverans över flera kanaler. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Cross-channel_delivery_workflow.html)

Vissa rekommendationer har lagts till i avsnittet &quot;Arkivera e-post&quot;. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_deliverability.html#Activating_emails_BCC_archiving)

En ny rekommendation har lagts till gällande den lägsta skärmupplösningen för optimal användning i Adobe Campaign. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Screen_resolution)

Integreringsguiden för Experience Manager har uppdaterats med vissa förtydliganden som har lagts till i konfigurationen av den här integreringen. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/ITG_Adobe_Experience_Manager_About_Adobe_Experience_Manager.html)

Information har lagts till gällande skillnaden mellan listan med grupptyper och listan med listtyper. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_Creating_and_managing_lists.html#About_lists_in_Adobe_Campaign)

Koden för att skicka ett rapportutdrag som en bifogad fil via e-post har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_a_report_to_a_list.html#Step_3-_Creating_the_workflow)

Ett exempel har lagts till om hur man skapar en fråga för att filtrera mottagare som inte har öppnat ett e-postmeddelande de senaste sju dagarna. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Recipients_who_did_not_open_any_delivery)

Integreringshandboken för delning av publiker med Adobe Experience Cloud har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Sharing_audiences_with_Adobe_Experience_Cloud.html)

Hjälpsidan för vanliga frågor innehåller nu information om tillgängliga språk, översättning av webbformulär och flerspråkiga e-postmeddelanden i Campaign. [Läs mer](../../platform/using/common-questions.md)

Skillnaden mellan engelska i USA och engelska i Storbritannien finns nu i ett särskilt avsnitt. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Formats_and_units)

Hjälpsidan [vanliga frågor](../../platform/using/common-questions.md) länkar nu till sidan med felmeddelanden.

Information om öppet spårningsläge har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_Personalizing_URL_tracking.html)

Information om lägsta upplösning för webbprogram och webbformulär har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_About_web_forms.html)

Integreringshandboken för lösningar med Campaign och Adobe Experience Cloud har uppdaterats och omorganiserats. [Läs mer](../../integrations/using/about-campaign-integrations.md)

Ett avsnitt om att använda textvariabler i webbformulär har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_Static_elements_in_a_web_form.html#Using_text_variables)

Lägen för URL-spårning i meddelanden är nu detaljerade. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_How_to_configure_tracked_links.html)

Avsnittet Skapa instanser har omorganiserats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Creating_an_instance_and_logging_on.html)

Att skicka e-post på japanska mobiltelefoner beskrivs nu i ett nytt avsnitt. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Sending_emails_on_Japanese_mobiles)

Avsnittet &quot;Optimera personalisering&quot; har uppdaterats med ytterligare information. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_fields.html#Optimizing_personalization)

## 18.6 - 09/07/2018{#release-18-6}

**Nya funktioner i denna version**

Kompatibilitetsmatrisen har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html)

JSAPI-dokumentationen har uppdaterats. [Läs mer](https://support.neolane.net/webApp/extranetLogin)

Sidan Inaktuella och borttagna funktioner har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/deprecated-and-removed-features.html)

**Andra dokumentationsuppdateringar som följer med denna version**

Användarhandböckerna för Campaign Classic har bytt namn för att förenkla navigering, förbättra användarupplevelsen samt ge tillgång till information och självhjälp. [Läs mer](https://docs.adobe.com/content/help/sv-SE/campaign-classic/using/campaign-classic-home.html)

Listan med funktioner som är tillgängliga i uttrycksredigeraren har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Creating_queries_Defining_filter_conditions.html#List_of_functions)

Starthandboken Säkerhet har uppdaterats med information om hur man skyddar sidor som innehåller PI. [Läs mer](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

Listan med felmeddelanden har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Ett avsnitt med felsökning har lagts till i integreringsdokumentationen för IMS. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/ITG_Connecting_via_an_Adobe_ID_IMS_troubleshooting.html)

Starthandboken Versionsuppgradering har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html)

Avsnittet Konfiguration av IP-tillhörighet har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Mid-sourcing_server.html#Multiplexing_the_mid-sourcing_server)

Ett avsnitt med felsökning för prestanda och genomströmning har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Performance_and_throughput_issues.html)

Listan över inbyggda personaliseringsblock har uppdaterats med exempel. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html#Out-of-the-box_personalization_blocks)

Listan över orsaker till leveransfel har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Delivery_failure_types_and_reasons)

Ett nytt avsnitt om hantering av paketdefinition har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_Working_with_data_packages.html#Managing_package_definitions)

Avsnittet Integrera Campaign med Adobe Analytics – datakoppling har förbättrats och omorganiserats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

Ett nytt avsnitt med självstudiekurser har lagts till med länkar till steg-för-steg-handböcker och instruktionsvideor. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

En ny teknisk dokumentation om SMS-anslutningsprotokoll och -inställningar har skapats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/sms-connector-protocol-and-settings.html)

Starthandboken Bästa praxis för leverans har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

Kontokonfigurationen för Microsoft Dynamics 365 med Web API-driftsättningar har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

Proceduren för att installera Adobe Campaign Classic på en Windows-plattform har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Windows__Installing_the_server.html)

Tidsramen för publikdelning mellan Adobe Experience Cloud och Campaign Classic har givits ytterligare detaljer. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Importing_and_exporting_audiences.html)

Listan över kunskapsbasartiklar för Campaign Classic har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/article-list.html)

Ett nytt tekniskt dokument om prestandaförbättring och bästa praxis finns nu tillgängligt. [Läs mer](https://helpx.adobe.com/se/campaign/kb/best-practices-for-performance-improvement.html)

A/B-testexempel har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Sidan med vanliga frågor och svar för Campaign Classic har uppdaterats. [Läs mer](../../platform/using/common-questions.md)

## 18.4 - 24/04/2018{#release-18-4}

**Nya funktioner i denna version**

EU:s allmänna dataskyddsförordning (GDPR) – [läs mer](https://helpx.adobe.com/se/campaign/kb/acc-privacy.html)

Aktiva profiler – [läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_About_profiles.html#Active_profiles)

Förbättrade push-kopplingar för Android – [läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Android_connectors)

**Andra dokumentationsuppdateringar som följer med denna version**

Versionsinformationen har förbättrats för att ge en bättre användarupplevelse och innehåller nu alla korrigeringsfiler relaterade till kundförfrågningar.  [Läs mer](https://docs.adobe.com/content/help/sv-SE/campaign-classic/using/release-notes/latest-release.html)

En ny sida med de vanligaste frågorna om Campaign Classic har lagts till. [Läs mer](../../platform/using/common-questions.md)

Listan med felmeddelanden har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Den tekniska dokumentationen för utlösare i Marketing Cloud har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/triggers-and-campaign.html)

Ett nytt tekniskt dokument har lagts till om hur man installerar och driftsätter integritetspaketet (GDPR) på äldre versioner av Campaign Classic. [Läs mer](https://helpx.adobe.com/se/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html)

Ett tekniskt dokument gällande den nya automatiska genereringsmekanismen för sekvenser har lagts till. [Läs mer](https://helpx.adobe.com/se/campaign/kb/sequence_auto_generation.html)

JSAPI-dokumentationen har uppdaterats. [Läs mer](https://support.neolane.net/webApp/extranetLogin)

Kompatibilitetsmatrisen har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html)

En ny sida med inaktuella funktioner och versioner finns nu tillgänglig. [Läs mer](https://helpx.adobe.com/se/campaign/kb/deprecated-and-removed-features.html)

Vissa kända begränsningar och bästa praxis för RDBMS har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html)

Lär dig bästa praxis för att använda SFTP. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

Listan över tekniska arbetsflöden har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

Förteckningen över kunskapsbasartiklar (tidigare kallade &quot;tekniska dokument&quot;) finns nu här. [Läs mer](https://helpx.adobe.com/se/campaign/kb/article-list.html)

[Instruktionsvideorna](https://docs.adobe.com/content/help/sv-SE/campaign-classic-learn/tutorials/overview.html) har uppdaterats.

LINE-dokumentationen har uppdaterats efter att LINE-paketet har avskrivits. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

Dokumentationen för att beräkna rapportindikatorer har uppdaterats. [Läs mer](../../reporting/using/indicator-calculation.md)

Information om att justera filer per tidszon med Oracle har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/MIG_Configuration_General_configurations.html#Oracle)

Ett nytt avsnitt som heter &quot;Övervaka leveranser&quot; har lagts till med uppdaterad information om leveransfel och hantering av karantäner. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

Avsnittet &quot;Personaliseringsblock&quot; har omorganiserats med ny information om färdiga personaliseringsblock.
[Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html)

Avsnittet Arkivera e-post har omorganiserats med ny information om konfigurationen av ```config-<instance name>.xml```-filer. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Activating_email_archiving__on_premise_)

Information om det tekniska arbetsflödet i Message Center (Control) har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_Message_Center__Control_.html)

Information om genomströmningsbegränsningar när man konfigurerar ett SMTP-relä har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Personalizing_delivery_parameters)

## 17.12 - 14/12/2017{#release-doc-14-12-2017}

Uppsättningen med [dokumentation om Adobe Campaign Classic](https://helpx.adobe.com/support/campaign/classic.html) har omorganiserats för att bli enklare att använda.

Ett nytt avsnitt med självstudiekurser har lagts till för att underlätta tillgången till hjälpmaterial om de viktigaste funktionerna i Campaign, handböcker, exempel och videor. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

Ett nytt avsnitt har lagts till för att hjälpa dig att övervaka leveransstatusen men även eventuella fel samt lära dig hur du åtgärdar dem. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

Listan med felmeddelanden har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Den tekniska dokumentationen för utlösare i Marketing Cloud har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/triggers-and-campaign.html)

Migreringsguiden för Campaign Classic har lagts till i samlingen. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

Kompatibilitetsmatrisen för Campaign har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html)

I tillämpliga fall anger nu konfigurations- och installationsanvisningarna vilken värdmodell de gäller för. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html)

En ny kunskapsbasartikel som belyser skillnader i konfiguration och funktion mellan lokala, hybrida och Managed Services-driftsättningar. [Läs mer](https://helpx.adobe.com/se/campaign/kb/acc-on-prem-vs-hosted.html)

Instruktioner om hur man installerar ett standardpaket har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Installing_packages.html)

Ytterligare information om hur man konfigurerar integreringen med den grundläggande tjänsten Audience Manager eller People. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

Installationsdokumentationen har uppdaterats för att ange att pgcrypto nu krävs för installation av Campaign om PostreSQL används. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Prerequisites.html#Database_access_layers)

## 17.9 - 25/09/2017{#release-17-9}

**Nya funktioner i denna version**

Förbättringar av ACS-koppling

SAP HANA-koppling – [läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#SAP_HANA)

Hadoop-koppling via HiveSQL – [läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#Hadoop)

LINE-kanal: meddelandeförbättringar – [läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

**Andra dokumentationsuppdateringar som följer med denna version**

Nya frågeexempel har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Filtering_duplicated_recipients)

Handboken med bästa praxis för leverans har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

A/B-testexempel har uppdaterats med de instruktioner som saknades. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Instruktionsvideorna har uppdaterats. [Läs mer](https://docs.adobe.com/content/help/sv-SE/campaign-classic-learn/tutorials/overview.html)

Avsnittet med e-postarkivering har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html)

Att använda Scheduler i ett arbetsflöde har förtydligats. [Läs mer](../../workflow/using/scheduler.md)

Bästa praxis för pausat arbetsflöde har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html)

Ny procedur om att förbearbeta filer vid import och efterbearbeta dem när data exporteras i ett arbetsflöde. Läs [här](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html).

Karantänmekanismen för dokumentationen om SMS-meddelanden har uppdaterats för att återspegla särdragen i felhanteringen för kopplingen till Extended generic SMPP. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines).

Dokumentationen för mobilappskanalen har förbättrats med en detaljerad procedur för att skicka avancerade meddelanden på Android. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Rich_notifications).

Dokumentationen om inkorgsåtergivning har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html).

Dokumentationen för inställning av webbspårning har förbättrats med ett uppdaterat exempel och kommentarer. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/CFG_Setting_up_web_tracking_Additional_parameters.html#Redirection_server_configuration).

Dokumentationen för SMS-kanalen har uppdaterats med ett förtydligande i avsnittet Automatiskt svar som gäller för kopplingen till Extended generic SMPP. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_SMS_channel.html#Creating_an_SMPP_external_account).

Dokumentationen för Social marknadsföring har uppdaterats. [Läs mer](../../social/using/about-social-marketing.md).

Ett nytt tekniskt dokument för IP-uppvärmning har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_Deliverability_IP_Warming_overview.pdf).

En ny starthandbok för versionsuppgradering har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html).

## Maj 2017{#release-doc-30-05-2017}

En ny starthandbok finns tillgänglig: den innehåller några av de bästa praxis som kan användas för att leverera med Adobe Campaign – från att skapa och målinrikta till att skicka och övervaka. [Läs mer](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

Starthandboken Säkerhet har uppdaterats. [Läs mer](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

[Dokumentationen &quot;Arkivera e-post&quot;](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) har uppdaterats med avsnittet [&quot;E-post som är osynlig för leveransmottagarna&quot;](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Configuring_the_BCC_email_address__on_premise_) och de [detaljerade stegen för att aktivera funktionen](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Archiving_emails).

Vissa videoklipp har lagts till och uppdaterats. [Läs mer](https://docs.adobe.com/content/help/sv-SE/campaign-classic-learn/tutorials/overview.html)

Läs om hur man skickar en leverans till mottagare som har lästs in från en extern fil utan att uppdatera databasen. [Läs mer](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)

Exemplet med dubbel anmälan har uppdaterats. [Läs mer](../../web/using/use-cases--web-forms.md)

## Mars 2017{#release-doc-31-03-2017}

Levererbarhet: [starthandboken](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) har uppdaterats. Dokumentationen om levererbarhet innehåller nu en mer detaljerad [översikt](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_About_deliverability.html) och en beskrivning av [implementeringsprocessen och de viktigaste stegen](../../delivery/using/deliverability-key-points.md).

Avsnittet &quot;Skicka i omgångar&quot; har flyttats och förbättrats med detaljerade exempel, rekommendationer och användningsfall.    [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Sending_using_multiple_waves)

En tabell som beskriver de fel som är specifika för SMS-meddelanden har lagts till i avsnittet &quot;Karantänhantering&quot;. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines)

Arbetsflöden: ett nytt exempel på arbetsflöde över flera kanaler har lagts till. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Cross-channel_deliveries)

Utlösare i Marketing Cloud: ett nytt tekniskt dokument om hur man konfigurerar och använder den med Adobe Campaign har lagts till. [Läs mer](https://helpx.adobe.com/se/campaign/kb/triggers-and-campaign.html)

Handboken för arbetsflöde har omorganiserats och utökats. Hitta enkelt hur man [bygger](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Building_a_workflow.html) och [kör](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html) ett arbetsflöde, hur man [målinriktar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html) och [hanterar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html#Data_Management) data, hur man [importerar](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html) data och hur man använder arbetsflödesdata för att [uppdatera databasen](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Updating_the_database) eller [skicka leveranser](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow).

Ett exempel på [arbetsflödesimport](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow) som har skapats efter [bästa praxis för import](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html#Import_best_practices) finns nu tillgängligt.
Installationshandboken har uppdaterats för den här nya versionen. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Architecture_and_hosting_models_General_architecture.html)

Kompatibilitetsmatrisen har uppdaterats. [Läs mer](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html)

Mottagare får ett mervärde när du inkluderar kuponger i e-postleveranserna. [Läs mer](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalized_coupons.html)

## Adobe Campaign version 7 – 16/03/2017{#release-17-2}

**Nya funktioner i denna version**

ACS-koppling

Webb-API för Microsoft Dynamics – [läs mer](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

Metoden e-postarkivering som är osynlig för leveransmottagarna – [läs mer](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Koppling till Amazon Simple Storage Service (S3) – [läs mer](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Event_activities.html#File_transfer)

