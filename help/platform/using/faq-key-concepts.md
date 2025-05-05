---
product: campaign
title: Viktiga begrepp
description: Vanliga frågor och svar om Campaign Classic
feature: Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: f0d884ae-0789-4ad9-a8fa-adeffbb560ea
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 82%

---

# Viktiga begrepp {#key-concepts}



Lär dig viktiga steg för att komma igång med Adobe Campaign.

## Kan jag ansluta till Campaign Classic med en Adobe ID? {#can-i-connect-to-campaign-classic-with-an-adobe-id-}

Tack vare integreringen med IMS (Adobe Identity Management System) kan användare ansluta till konsolen i Adobe Campaign med sitt Adobe ID. Integreringen ger följande fördelar:

* Samma ID kan användas för alla Experience Cloud-lösningar.
* Anslutningen sparas när Adobe Campaign används med olika integreringar.
* Säkrare policy för lösenordshantering.
* Använda Federated ID-konton (extern ID-leverantör).

[Klicka här för att läsa mer](../../integrations/using/about-adobe-id.md) om hur man använder Campaign Classic med ett Adobe ID.

## Vad är min version av Campaign? {#what-is-my-version-of-campaign-}

Kontrollera [versions- och build-numret](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version) i menyn **Hjälp > Om ...** på klientkonsolen i Campaign.

## Vilka är skillnaderna när du arbetar lokalt jämfört med i en hostingmiljö? {#what-are-the-differences-when-working-on-premise-vs--in-a-hosted-environment-}

Med Adobe Campaign Classic medföljer en uppsättning moduler och alternativ. Vilka moduler som är tillgängliga och vilka konfigurationer de har beror på [vilken typ av driftsättning](../../installation/using/hosting-models.md) din installation har: värdbaserad (hanterade tjänster), hybrid eller lokal.

[Klicka här för att läsa mer](../../installation/using/capability-matrix.md).

## Hur ställer jag in användarbehörigheter? {#how-can-i-set-up-user-permissions-}

Som administratör för Campaign kan du konfigurera behörigheter för användare i organisationen.

Detta är en uppsättning rättigheter och begränsningar som tillåter eller nekar:

* Åtkomst till vissa funktioner.
* Åtkomst till vissa data.
* Skapande, ändring och/eller borttagning av data.

[Klicka här för att läsa mer](../../platform/using/access-management.md) om användarbehörigheter.

## Hur säkrar jag integritetsefterlevnaden med Campaign? {#how-to-be-gdpr-compliant-with-campaign-}

Adobe Campaign har en uppsättning verktyg som hjälper dig att följa integritetsefterlevnaden i GDPR och CCPA.

Läs [det här dokumentet](privacy-and-recommendations.md) för att få en förståelse av de verktyg och funktioner som Adobe Campaign erbjuder, samt bästa praxis, för att hjälpa dig att uppfylla GDPR-kraven när du använder vår tjänst. Implementeringsstegen för Campaign Classic beskrivs i [den här artikeln](https://helpx.adobe.com/se/campaign/kb/acc-privacy.html).

## Vad är Campaign-användargränssnittskoncept jag bör känna till? {#what-are-campaign-user-interface-concepts-i-should-know-}

Läs [det här avsnittet](../../platform/using/adobe-campaign-workspace.md) för att veta mer om grunderna för arbetsytan i Adobe Campaign.

![](assets/do-not-localize/how-to-video.png) [Upptäck arbetsytan i Campaign via en video](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/getting-started/exploring-the-adobe-campaign-classic-user-interface.html?lang=sv-SE)

## Hur väljer jag målgrupp för mina meddelanden? {#how-can-i-select-the-target-population-of-my-messages-}

Med Adobe Campaign kan du använda olika strategier för att skapa publiker och välja målmottagare.

[Klicka här för att läsa mer](../../delivery/using/steps-defining-the-target-population.md).

## Vad är ett arbetsflöde? {#what-is-a-workflow-}

Med Adobe Campaign följer arbetsflöden för att orkestrera alla processer och uppgifter i olika moduler på programservern. I den omfattande grafiska miljön kan du utforma processer såsom segmentering, kampanjkörning, filhantering och mänskligt deltagande osv. Arbetsflödesmotorn kör och spårar dessa processer.

Du kan till exempel använda ett arbetsflöde för att ladda ned en fil från en server, expandera den och sedan importera poster som finns i databasen i Adobe Campaign.

Ett arbetsflöde kan även innefatta en eller flera operatörer som ska meddelas eller som kan göra val och godkänna processer. På så sätt kan du skapa en leveransinstruktion, tilldela en eller flera operatörer uppgiften att arbeta med innehåll, ange mål och godkänna korrekturer innan leveransen påbörjas.

[Klicka här för att läsa mer](../../workflow/using/about-workflows.md) om arbetsflöden. Du kan även läsa om [bästa praxis för arbetsflödet](../../workflow/using/building-a-workflow.md).

## Hur skapar och skickar jag ett första e-postmeddelande? {#how-to-create-and-send-a-first-email-}

[Klicka här för att får reda på mer](../../delivery/using/about-email-channel.md).

![](assets/do-not-localize/how-to-video.png) [Upptäck detta i en video](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/getting-started/creating-a-campaign-and-an-email.html?lang=sv-SE)

## Hur skickar jag SMS-meddelanden? {#how-to-send-sms-messages-}

Läs mer [i det här avsnittet](../../delivery/using/sms-channel.md) om hur man konfigurerar plattformen och skickar SMS-meddelanden.

## Hur skickar jag push-meddelanden? {#how-to-send-push-notifications-}

Läs mer om hur man använder Adobe Campaign för att [skicka personaliserade push-meddelanden](../../delivery/using/create-notifications-ios.md) till iOS- och Android-enheter via appar.

## Hur designar och delar man en enkät online? {#how-to-design-and-share-an-online-survey-}

Läs mer om de viktigaste stegen för hur man [skapar en undersökning online](../../surveys/using/getting-started-with-surveys.md) för att utforma och publicera den med Campaign Classic.

## Hur skapar man landningssidor? {#how-to-create-landing-page-}

Du kan använda redigeraren för digitalt innehåll i Adobe Campaign för att utforma en landningssida och definiera kartläggning med databasfält.

[Klicka här för att läsa mer](../../web/using/creating-a-landing-page.md).

## Hur kan jag spåra leveranser? {#how-can-i-track-deliveries-}

Du kan spåra leveranser som skickas med Campaign Classic via dedikerade [leveransrapporter](../../reporting/using/delivery-reports.md) och sedan övervaka dem.

Läs mer om spårningshantering i Campaign på [den här sidan](https://helpx.adobe.com/se/campaign/kb/acc-tracking.html).

## Vilka är de bästa säkerhetsrutinerna (lokalt)? {#what-are-security-best-practices--on-premise--}

Läs [checklistan för säkerhetskonfiguration](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/security-privacy/get-started-security-privacy.html?lang=sv) för att hitta de viktigaste elementen att kolla för säkerhetskonfigurationen och åtkomsten till lokala driftsättningar.

## Hur översätter jag ett felmeddelande? {#how-to-translate-an-error-message-}

Visas ett felmeddelande på ett främmande språk? Alla felmeddelanden och deras översättning listas på [den här sidan](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html?lang=sv).

## Kan jag skapa ett webbformulär och samla in svar i Campaign? {#can-i-create-a-webform-and-collect-answers-in-campaign-}

Läs mer om hur man [skapar ett webbformulär](../../web/using/about-web-forms.md). Utforma, testa och publicera ett webbformulär samt samla in svar.

## Finns det en lista över borttagna funktioner och versioner? {#is-there-a-list-of-deprecated-features-and-versions-}

Adobe utvärderar ständigt funktionerna i produkten. Adobe gör detta för att med tiden planera att ersätta funktioner med kraftfullare versioner eller bestämma sig för att implementera utvalda delar på nytt för att bli bättre förberedda på framtida förväntningar eller tillägg. Eftersom Campaign fungerar med verktyg från tredje part uppdateras kompatibiliteten regelbundet, vilket innebär att endast de versioner som stöds kan implementeras.

[Klicka här för att läsa mer](../../rn/using/deprecated-features.md).

## Finns det nya dokumentationsuppdateringar och hjälpmaterial? {#are-there-new-documentation-updates-and-help-materials-released-}

De senaste dokumentationsuppdateringarna för Campaign Classic listas [på den här sidan](https://experienceleague.adobe.com/docs/campaign-classic/using/documentation-updates.html?lang=sv-SE).

Du kan även se de senaste tekniska dokumenten som finns [på den här sidan](https://helpx.adobe.com/se/campaign/kb/article-list.html).
