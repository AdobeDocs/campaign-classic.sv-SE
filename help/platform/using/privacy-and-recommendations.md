---
product: campaign
title: Sekretess och medgivande
description: Läs mer om sekretess och medgivande
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: d2451b62-bddf-4dee-8789-35aaae8348e1
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '2033'
ht-degree: 100%

---

# Integritet och medgivande{#privacy-and-recommendations}

![](../../assets/common.svg)

## Allmänna rekommendationer {#general-recommendations}

Adobe Campaign är ett kraftfullt verktyg för att samla in och behandla mycket stora mängder data, bland annat personuppgifter och känsliga data. Det är därför som integritet måste hanteras försiktigt.

* Använd alltid personlig information på ett ansvarsfullt och etiskt sätt.

* Undvik att skicka oönskade e-postmeddelanden, push-meddelanden och SMS-meddelanden (”spam”). Adobe tror starkt på principerna om auktoriserad marknadsföring när det gäller att främja kundens livstidsvärde och -lojalitet och vi förbjuder därför strikt att Adobe Campaign används för att skicka oönskade meddelanden.

Ta dig tid att gå igenom [Checklistan för säkerhet och sekretess](../../installation/using/get-started-security-privacy.md) för att lära dig grunderna i att kontrollera säkerhet och sekretess.

### Integritetsbestämmelser {#privacy-regulations}

För att kunna hantera personuppgifter på ett korrekt sätt bör du arbeta i enlighet med lagstiftningen i den eller de regioner där du bedriver verksamhet. Dessa regler omfattar:
* [GDPR](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en) (Europeiska allmänna dataskyddsförordningen)
* [DPA](https://www.gov.uk/data-protection) (Storbritanniens genomförande av GDPR)
* [Europas direktiv om integritet och elektronisk kommunikation](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219)
* [CAN-SPAM Act](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business) (amerikansk lagstiftning gällande regler och krav på kommersiell e-post)
* [CCPA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;chapter=&amp;article=) (California Consumer Privacy Act)
* [PDPA](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/) (Thailand Personal Data Protection Act)
* [LGPD](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf) (den brasilianska allmänna dataskyddslagen) – träder i kraft från och med den 16 augusti 2020

>[!NOTE]
>
>Mer information om hur GDPR, CCPA, PDPA och LGPD påverkar Adobe Campaign finns på [den här sidan](../../platform/using/privacy-management.md#privacy-management-regulations).

### Integritet i Adobe Experience Cloud {#experience-cloud-privacy}

Adobe Campaign ingår som en del av Adobe Experience Cloud. Sättet på vilket sekretess hanteras i Campaign följer Experience Clouds allmänna principer som till exempel följande:

* **Vilken information samlas in när Adobe Experience Cloud används**

   Som ett företag som använder Adobe Experience Cloud-lösningar väljer du vilken information som ska samlas in och skickas till ditt Adobe Experience Cloud-konto. Exempel på information som kan samlas in är webbläsaraktivitet, IP-adresser, platsinformation från mobila enheter, kampanjers framgång, artiklar som har köpts eller placerats i en kundvagn osv.

   >[!NOTE]
   >
   >I likhet med alla andra Adobe-produkter samlar Campaign in information om program- och webbplatsanvändare. Se [Adobes integritetspolicy](https://www.adobe.com/se/privacy/policy.html) för mer information.

* **Så används Adobe Experience Cloud för att samla in information**

   * Adobe Experience Cloud-lösningar använder cookies och liknande tekniker såsom webb-beacons (kallas även för taggar eller pixlar) för att göra det möjligt att samla in information. Se [det här avsnittet](#tracking-capabilities) för mer information om cookies och spårningsfunktioner med Adobe Campaign.
   * Du kan också använda Adobe Experience Cloud-tekniker i dina mobilappar. Mer information om hur du skickar mobilleveranser med Campaign finns i [SMS-kanal](../../delivery/using/sms-channel.md) och [Mobilappskanal](../../delivery/using/about-mobile-app-channel.md).

* **Dina användares integritetsinställningar gällande hur du använder Adobe Experience Cloud**

   Adobe ber att du erbjuder dina kunder en integritetspolicy som beskriver:

   * Din bästa praxis gällande integritet i samband med Adobe Experience Cloud
   * Hur användare kan ställa in sina preferenser gällande insamling eller användning av sin information i samband med Adobe Experience Cloud

   >[!NOTE]
   >
   >Liksom för alla Adobe-produkter kan användare i Campaign avanmäla sig från att dela information som samlas in om dem via appar och webbplatser. Mer information finns i [Vanliga frågor och svar om att använda Adobe Experience Cloud](https://www.adobe.com/se/privacy/experience-cloud-usage-info-faq.html).

Se [den här sidan](https://www.adobe.com/se/privacy/marketing-cloud.html) för mer information om integriteten i Adobe Experience Cloud.

## Personuppgifter och personer {#personal-data}

När integritet hanteras är det viktigt att definiera vilka data som ska hanteras med försiktighet och av vem.
* **Personuppgifter** är information som direkt eller indirekt kan identifiera en levande individ.
* **Känsliga personuppgifter** är information som är relaterad till en individs ras, politiska åsikter, religiösa övertygelser, kriminella bakgrund, genetiska uppgifter, hälsodata, sexuella preferenser, biometrisk information samt medlemskap i fackföreningar.

När du integrerar Campaign med andra Experience Cloud-lösningar där målgrupper kan överföras från ett system till ett annat, som till exempel [Adobe Analytics](../../platform/using/adobe-analytics-connector.md), [Audience Manager eller den grundläggande tjänsten People](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md), [Campaign Standard](../../integrations/using/synchronizing-audiences.md) eller med andra lösningar med [CRM-kopplingar](../../platform/using/crm-connectors.md) måste du vara extra noga med att skydda personuppgifter.

De [viktigaste föreskrifterna](#privacy-regulations) avser de olika enheter som hanterar data enligt följande:
* Ett **personuppgiftsansvarig** är den myndighet som bestämmer syftet med att samla in, använda och dela personuppgifter och hur det ska göras.
* Ett **personuppgiftsbiträde** är en individ eller part som samlar in, använder eller delar personuppgifter enligt den personuppgiftsansvariges anvisningar.
* En **registrerad** är en levande individ vars personuppgifter samlas in, används eller delas och som direkt eller indirekt kan identifieras genom hänvisning till dessa personuppgifter.

Som företag som samlar in och delar personuppgifter är du den personuppgiftsansvarige, dina kunder är de registrerade och Adobe Campaign fungerar som personuppgiftsbiträde när vi hanterar deras personuppgifter enligt dina anvisningar. Observera att det är ditt ansvar som personuppgiftsansvarige att hantera relationen med de registrerade såsom vid hantering av [förfrågningar om användarens information](#privacy-requests).

### Scenario med användningsfall {#use-case-scenario}

För att illustrera hur personerna i de olika rollerna interagerar följer ett exempel, på hög nivå, av en GDPR-kundupplevelse.

I det här exemplet är kunden i Adobe Campaign ett flygbolag. Det här företaget är **personuppgiftsansvarig** och alla klienter i flygbolaget är **registrerade**. Laura är i det här fallet en kund hos flygbolaget.

Dessa är de olika personerna som används i det här exemplet:

* **Laura** är den **registrerade**. Hon är mottagaren som får meddelanden från flygbolaget. Laura är kanske en person som flyger ofta men kan vid något tillfälle besluta att hon inte vill ha någon personlig reklam eller marknadsföringsmeddelanden från flygbolaget. Hon ber flygbolaget (baserat på deras process) att ta bort sitt nummer som frekvent flygresenär.

* **Anne** är **personuppgiftsansvarig** hos flygbolaget. Hon tar emot Lauras begäran, erhåller de ID-nummer som efterfrågas för att identifiera den registrerade och lämnar in begäran i Adobe Campaign.

* **Adobe Campaign** är **personuppgiftsbiträdet**.

![](assets/privacy-gdpr-flow.png)

Här följer det allmänna flödet för det här användningsfallet:

1. Den **registrerade** (Laura) skickar en GDPR-begäran till **personuppgiftsansvarige** via e-post, kundtjänsten eller en webbportal.

1. **Personuppgiftsansvarige** (Anne) skickar GDPR-begäran till Campaign via gränssnittet eller ett API.

1. När **personuppgiftsbiträdet** (Adobe Campaign) tar emot informationen utförs åtgärden i GDPR-begäran och ett svar eller bekräftelse skickas till **personuppgiftsansvarige** (Anne).

1. **Personuppgiftsansvarige** (Anne) granskar sedan informationen och skickar tillbaka den till den **registrerade** (Laura).

## Datainsamling {#data-acquisition}

Med Adobe Campaign kan ni samla in data, inklusive personuppgifter och känslig information. Det är därför viktigt att du erhåller och övervakar medgivande från dina mottagare.

* Låt alltid mottagarna godkänna att ta emot meddelanden. För att göra detta ska du fortsätt respektera förfrågningar om borttagning så snabbt som möjligt och verifiera medgivande genom en dubbel anmälningsprocess. Mer information om det här finns i [Skapa ett prenumerationsformulär med dubbel anmälan](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).
* Importera inte bedrägliga listor och använd dirigerade adresser för att kontrollera att din klientfil inte används bedrägligt. Mer information om det här finns i [Om dirigerade adresser](../../delivery/using/about-seed-addresses.md).
* Genom medgivande och behörighetshantering kan du spåra mottagarnas preferenser och hantera vem inom organisationen som har tillgång till vilka data. Mer information finns i [det här avsnittet](#consent).
* Underlätta och hantera förfrågningar om användarens information från era mottagare. Mer information finns i [det här avsnittet](#privacy-requests).

## Integritetshantering {#privacy-management}

Integritetshantering avser alla processer och verktyg som kan hjälpa dig att följa integritetsbestämmelser (GDPR, CCPA, osv.). Få en översikt över vad integritetshantering är på [denna sida](privacy-and-recommendations.md).

Adobe Campaign tillhandahåller olika funktioner för integritetshantering:
* Medgivandehantering, datalagring och användarroller. Se [det här avsnittet](#consent).
* Förfrågningar om användarens information (åtkomsträttigheter och rätt att glömmas). Se [det här avsnittet](#privacy-requests).
* Avanmäl dig gällande försäljning av personuppgifter (CCPA-specifik) Se [det här avsnittet](../../platform/using/privacy-requests.md#sale-of-personal-information-ccpa).

De viktigaste integritetsfunktionerna i Campaign och ett exempel på vilka personer som berörs, presenteras i [det här avsnittet](https://helpx.adobe.com/se/campaign/kb/campaign-privacy-more.html#gdprpersonasandflow).

### Medgivande, lagring och roller {#consent}

Adobe Campaign erbjuder viktiga funktioner som är grundläggande för integriteten:

* **Medgivandehantering**: genom prenumerationshantering kan du hantera mottagarnas preferenser och spåra vilka mottagare som har valt att anmäla sig till vilka typer av prenumerationer. Mer information om det här finns i [Om prenumerationer](../../delivery/using/about-services-and-subscriptions.md).
* **Datalagring**: alla inbyggda standardiserade loggtabeller har förinställda lagringsperioder vilket i allmänhet begränsar datalagringen till 6 månader eller mindre. Ytterligare lagringsperioder kan ställas in med arbetsflöden. Kontakta Adobes konsulter eller teknikadministratörer för mer information om detta.
* **Hantering av rättigheter**: Adobe Campaign ger dig möjligheten att hantera de rättigheter som tilldelats olika operatörer i Campaign via olika färdiga eller anpassade roller. Det här låter dig hantera vilka inom företaget som kan få åtkomst till, ändra eller exportera olika typer av data. Se [Om åtkomsthantering](../../platform/using/access-management.md) för mer information.

Se [det här avsnittet](../../platform/using/privacy-management.md#consent-retention-roles) för mer information om dessa funktioner och hur du hanterar dem i Adobe Campaign.

### Förfrågningar om användarens information {#privacy-requests}

Adobe Campaign erbjuder ytterligare funktioner som underlättar din beredskap som personuppgiftsansvarig för vissa förfrågningar om användarens information:

* **Åtkomsträttigheterna** är den registrerades rätt att från personuppgiftsansvarige få bekräftelse på om personuppgifter som rör dem behandlas eller inte, var de befinner dig och varför.

* **Rätten att glömmas** (förfrågan om borttagning) ger den registrerade rätten att låta personuppgiftsansvarig radera sina personuppgifter.

Förfrågningar om **åtkomst** och **radering** visas i [det här avsnittet](../../platform/using/privacy-management.md#right-access-forgotten).

Implementeringsstegen för att skapa de här förfrågningarna finns i [det här avsnittet](../../platform/using/privacy-requests.md).

## Spårningsfunktioner {#tracking-capabilities}

### Cookies {#cookies}

Tack vare spårningsfunktionerna i Adobe Campaign kan du spåra vad leveransmottagarna surfar om med hjälp av tre typer av cookies: en sessionscookie och två permanenta cookies.

* En **sessionscookie**: Cookien **nlid** innehåller identifieraren för e-postmeddelandet som skickas till kontakten (**broadlogId**) och identifieraren för meddelandemallen (**deliveryId**). Den läggs till när kontakten klickar på en URL som ingår i ett e-postmeddelande som skickas av Adobe Campaign och låter dig spåra deras beteende på webben. Denna sessionscookie raderas automatiskt när webbläsaren stängs. Kontakten kan konfigurera sin webbläsare så att den inte tillåter cookies.

* Två **permanenta** cookies:
   * Cookien **UUID** (Universal Unique IDentifier) delas mellan Adobe Experience Cloud-lösningar. Den ställs in en gång tills den försvinner från klientwebbläsaren när ett nytt värde skapas. Med den här cookien kan du identifiera de användare som interagerar med Experience Cloud-lösningarna när de besöker en webbplats. Den kan ställas in av en landningssida (för att koppla okända kundaktiviteter till en mottagare) eller av en leverans. Beskrivningen av den här cookien finns på [den här sidan](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-mc.html?lang=sv#ec-cookies).
   * Cookien **nllastdelid** (som introducerades i Campaign Classic 20.3) är en permanent cookie som innehåller **deliveryId** för den senaste leveransen där användaren klickade på länken. Den här cookien används för att identifiera spårningstabellen som ska användas när sessionscookien saknas.

Föreskrifter som den allmänna dataskyddsförordningen (GDPR) kräver att företag erhåller medgivande från webbplatsanvändare innan de installerar några cookies.

* Du måste informera användare om att dina webbplatser är utrustade med verktyg för webbspårning via en auktoriseringsbegäran (som till exempel visas ovanpå webbplatsen) med en kryssruta för att godkänna installationen av cookies. Du kan eventuellt lägga till en banderoll högst upp på den första sidan som de besöker osv.
* Popup-fönster bör undvikas eftersom de ofta blockeras av webbläsare.

### Meddelandespårning {#message-tracking}

Med Adobe Campaign kan du spåra skickade e-postmeddelanden och leveransmottagarnas beteende: öppna, klicka på länkar, avsluta prenumerationer osv. Mer information om det här finns i [Om meddelandespårning](../../delivery/using/about-message-tracking.md).

Du gör det genom att lägga till [spårade länkar](../../delivery/using/how-to-configure-tracked-links.md) i dina meddelanden för att mäta effekten av leverans och mottagarens beteende på fliken [Spårning](../../delivery/using/delivery-dashboard.md#tracking-logs) på instrumentpanelen för leverans. Spårningsdata tolkas i rapporten [Tracking indicators](../../reporting/using/delivery-reports.md#tracking-indicators).

### Webbspårning {#web-tracking}

Med Adobe Campaign kan du också övervaka hur mottagarna surfar på webbplatsen: Infoga spårningstaggar för att samla in information och mäta besök på sidor med webbapplikationer. Mer information om det här finns i [Spåra en webbapplikation](../../web/using/tracking-a-web-application.md).

Konfigurationen av webbspårning visas i [det här avsnittet](../../configuration/using/about-web-tracking.md).

För att ytterligare hantera spårning kan du använda Adobe Campaign för visa en avanmälningsbanderoll med ett val att stoppa spårning av webbeteende, för slutanvändare som vill avanmäla sig från beteendespårning. Mer information om det här finns i [Avanmälan av spårning av webbapplikationer](../../web/using/web-application-tracking-opt-out.md).
