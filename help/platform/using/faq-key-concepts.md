---
title: Viktiga begrepp
seo-title: Vanliga frågor om kampanjfunktioner
description: Vanliga frågor om Campaign Classic
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8ef56aa04a3ecc94e9e3dda24562760d6a93739d

---


# Viktiga begrepp {#key-concepts}

Lär dig viktiga steg att börja med Adobe Campaign.

## Kan jag ansluta till Campaign Classic med ett Adobe-ID? {#can-i-connect-to-campaign-classic-with-an-adobe-id-}

Tack vare integreringen med IMS (Adobe Identity Management System) kan användare ansluta till Adobe Campaign-konsolen med sitt Adobe ID. Integreringen ger följande fördelar:

* Samma ID kan användas för alla Experience Cloud-lösningar.
* Anslutningen sparas när Adobe Campaign används med olika integreringar.
* Lösenordshanteringsprincip för säkerhetslösenord.
* Användning av Federated ID-konton (extern ID-leverantör).

[Klicka här om du vill veta mer](../../integrations/using/about-adobe-id.md) om hur du använder Campaign Classic med ett Adobe-ID.

## Vad är min version av Campaign? {#what-is-my-version-of-campaign-}

[ Kontrollera ](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)version och build-nummer **i** Hjälp > Om... meny för Campaign-klientkonsolen.

## Vilka är skillnaderna när du arbetar lokalt jämfört med i en hostingmiljö? {#what-are-the-differences-when-working-on-premise-vs--in-a-hosted-environment-}

Adobe Campaign Classic innehåller en uppsättning moduler och alternativ. Vilka moduler som är tillgängliga och vilka konfigurationer de har beror på [vilken typ av distribution](../../installation/using/hosting-models.md) du har: värdbaserade (hanterade tjänster) eller på plats.

[Klicka här om du vill veta mer](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Hur ställer jag in användarbehörigheter? {#how-can-i-set-up-user-permissions-}

Som kampanjadministratör kan du konfigurera behörigheter för användare i organisationen.

Detta är en uppsättning rättigheter och begränsningar som tillåter eller nekar till:

* Tillgång till vissa funktioner.
* Tillgång till vissa uppgifter.
* Skapa, ändra och/eller ta bort data.

[Klicka här om du vill veta mer](../../platform/using/access-management.md) om användarbehörigheter.

## Hur säkrar jag integritetsefterlevnaden med Campaign? {#how-to-be-gdpr-compliant-with-campaign-}

Adobe Campaign erbjuder en uppsättning verktyg som hjälper dig att uppfylla sekretesskraven för GDPR och CCPA.

Läs [det här dokumentet](https://helpx.adobe.com/campaign/kb/campaign-privacy-overview.html) för att få en förståelse för de verktyg och funktioner som Adobe Campaign tillhandahåller, samt för bästa praxis, för att hjälpa er med er GDPR-efterlevnad när ni använder vår tjänst. Implementeringsstegen för Campaign Classic beskrivs i [den här artikeln](https://helpx.adobe.com/campaign/kb/acc-privacy.html).

## Vad är Campaign-användargränssnittskoncept som jag bör känna till? {#what-are-campaign-user-interface-concepts-i-should-know-}

Läs [det här avsnittet](../../platform/using/adobe-campaign-workspace.md) om du vill veta mer om grunderna för arbetsytan i Adobe Campaign. Du kan också titta på [den här videon](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/interface-overview.html).

## Hur väljer jag målgrupp för mina meddelanden? {#how-can-i-select-the-target-population-of-my-messages-}

Med Adobe Campaign kan ni använda olika strategier för att skapa målgrupper och välja målmottagare.

[Klicka här om du vill veta mer](../../delivery/using/steps-defining-the-target-population.md).

## Vad är ett arbetsflöde? {#what-is-a-workflow-}

Adobe Campaign innehåller arbetsflöden för att samordna alla processer och uppgifter i olika moduler på programservern. I den omfattande grafiska miljön kan ni utforma processer som segmentering, kampanjhantering, filhantering, medarbetare osv. Arbetsflödesmotorn kör och spårar dessa processer.

Du kan till exempel använda ett arbetsflöde för att hämta en fil från en server, expandera den och sedan importera poster i Adobe Campaign-databasen.

Ett arbetsflöde kan även omfatta en eller flera operatorer som ska meddelas eller som kan göra val och godkänna processer. På så sätt kan du skapa en leveransåtgärd, tilldela en eller flera operatorer en uppgift att arbeta med innehåll, ange mål och godkänna korrektur innan leveransen påbörjas.

[Klicka här om du vill veta mer](../../workflow/using/about-workflows.md) om arbetsflöden. Du kan även läsa upp [arbetsflödets bästa praxis](../../workflow/using/building-a-workflow.md).

## Hur skapar och skickar jag ett första e-postmeddelande? {#how-to-create-and-send-a-first-email-}

[Klicka här om du vill veta mer](../../delivery/using/about-email-channel.md) eller [se videon](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/creating-a-campaign-and-an-email.html) för att skapa ett e-postmeddelande i en kampanj.

## Hur skickar jag SMS-meddelanden? {#how-to-send-sms-messages-}

Lär dig hur du konfigurerar plattformen och skickar SMS-meddelanden [i det här avsnittet](../../delivery/using/sms-channel.md).

## Hur skickar jag push-meddelanden? {#how-to-send-push-notifications-}

Lär dig hur du använder Adobe Campaign för att [skicka personaliserade push-meddelanden](../../delivery/using/creating-notifications.md) till iOS- och Android-enheter via appar.

## Hur designar och delar man en undersökning online? {#how-to-design-and-share-an-online-survey-}

Lär dig hur du [skapar en onlineenkät](../../web/using/getting-started-with-surveys.md)med viktiga steg för att designa och publicera den med Campaign Classic.

## Hur skapar man landningssidor? {#how-to-create-landing-page-}

Du kan använda redigeraren för digitalt innehåll i Adobe Campaign för att utforma en landningssida och definiera mappning med databasfält.

[Klicka här om du vill veta mer](../../web/using/creating-a-landing-page.md).

## Hur kan jag spåra leveranser? {#how-can-i-track-deliveries-}

Du kan spåra leveranser som skickats med Campaign Classic via dedikerade [leveransrapporter](../../reporting/using/delivery-reports.md) och sedan övervaka leveranserna.

Läs mer om spårningshantering i Campaign på [den här sidan](https://helpx.adobe.com/campaign/kb/acc-tracking.html).

## Vilka är de bästa säkerhetsrutinerna (lokalt)? {#what-are-security-best-practices--on-premise--}

Läs checklistan [för](https://helpx.adobe.com/campaign/kb/acc-security.html) säkerhetskonfiguration för att hitta nyckelelement som kontrollerar säkerhetskonfigurationen och åtkomsten till driftsättningar på plats.

## Hur översätter jag ett felmeddelande? {#how-to-translate-an-error-message-}

Visas ett felmeddelande på ett främmande språk? Alla felmeddelanden och deras översättning visas på [den här sidan](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html).

## Kan jag skapa ett webbformulär och samla in svar i Campaign? {#can-i-create-a-webform-and-collect-answers-in-campaign-}

Lär dig hur du [skapar ett webbformulär](../../web/using/about-web-forms.md): utforma, testa, publicera ett webbformulär och samla in svar.

## Finns det en lista över borttagna funktioner och versioner? {#is-there-a-list-of-deprecated-features-and-versions-}

Adobe utvärderar ständigt funktionerna i produkten och planerar att ersätta funktioner med kraftfullare versioner, eller bestämmer sig för att återimplementera utvalda delar för att bli bättre förberedda för framtida förväntningar eller tillägg. Eftersom Campaign fungerar med verktyg från tredje part uppdateras kompatibiliteten regelbundet, så att endast de versioner som stöds kan implementeras.

[Klicka här om du vill veta mer](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html).

## Finns det nya dokumentationsuppdateringar och hjälpmaterial? {#are-there-new-documentation-updates-and-help-materials-released-}

De senaste uppdateringarna för Campaign Classic-dokumentation visas [på den här sidan](https://docs.adobe.com/content/help/en/campaign-classic/using/documentation-updates.html).

Du kan även läsa de senaste tekniska anteckningarna som finns [på den här sidan](https://helpx.adobe.com/campaign/kb/article-list.html).
