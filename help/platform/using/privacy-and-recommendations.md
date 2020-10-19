---
title: Sekretess och rekommendationer
seo-title: Sekretess och rekommendationer
description: Sekretess och rekommendationer
seo-description: null
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '1848'
ht-degree: 8%

---


# Privacy and Consent{#privacy-and-recommendations}

## Allmänna rekommendationer {#general-recommendations}

Adobe Campaign är ett kraftfullt verktyg för att samla in och behandla mycket stora mängder data, inklusive personuppgifter och känsliga data. Det är därför sekretess måste hanteras noggrant.

* Gör alltid ansvarsfull och etisk användning av personuppgifter.

* Undvik att skicka oönskade e-postmeddelanden, push-meddelanden och SMS-meddelanden (&quot;spam&quot;). Adobe tror starkt på principerna om tillståndsmarknadsföring när det gäller att främja kundens livstidsvärde och lojalitet, och förbjuder därför strikt användning av Adobe Campaign för att skicka oönskade meddelanden.

Ta dig tid att gå igenom [checklistan för säkerhet och integritet](https://helpx.adobe.com/se/campaign/kb/acc-security.html) för att lära dig grunderna i att kontrollera säkerhet och integritet.

### Sekretessregler {#privacy-regulations}

För att kunna hantera personuppgifter på ett korrekt sätt bör du arbeta i enlighet med lagstiftningen i den eller de regioner där du arbetar. Dessa regler omfattar:
* [GDPR](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en) (Europeiska allmänna dataskyddsförordningen)
* [DPA](https://www.gov.uk/data-protection) (Förenade kungarikets genomförande av GDPR)
* [Europeiskt direktiv om integritet och elektronisk kommunikation](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219)
* [CAN-SPAM Act](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business) (amerikansk lag om regler och krav för kommersiell e-post)
* [CCPA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;kapitel=&amp;artikel=) (California Consumer Privacy Act)
* [PDPA](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/) (Thailand Personal Data Protection Act)
* [LGPD](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf) (Brasilien General Data Protection Law) - börjar gälla den 16 augusti 2020

>[!NOTE]
>
>Mer information om hur GDPR, CCPA, PDPA och LGPD gäller för Adobe Campaign finns på [den här sidan](https://helpx.adobe.com/se/campaign/kb/campaign-privacy-overview.html#whatisgdpr).

### Adobe Experience Cloud privacy {#experience-cloud-privacy}

Adobe Campaign ingår i Adobe Experience Cloud lösningar. Det sätt på vilket sekretessen hanteras i Campaign följer de allmänna principerna för Experience Cloud, som följande:

* **Vilken information samlas in när Adobe Experience Cloud används**

   Som företag som använder Adobe Experience Cloud lösningar väljer du vilken information som ska registreras och skickas till ditt Adobe Experience Cloud-konto. Exempel på information som kan samlas in är webbläsaraktivitet, IP-adresser, platsinformation från mobila enheter, kampanjfrekvens, artiklar som köpts eller placerats i kundvagn osv.

   >[!NOTE]
   >
   >För alla Adobe-produkter samlar Campaign in information om program- och webbplatsanvändare. Mer information finns i [Adobe integritetspolicy](https://www.adobe.com/privacy/policy.html).

* **Hur Adobe Experience Cloud används för att samla in information**

   * Adobe Experience Cloud lösningar använder cookies och liknande tekniker, som webbfyrar (kallas även taggar eller pixlar), för att göra det möjligt att samla in information. Mer information om cookies och spårningsfunktioner med Adobe Campaign finns i [det här avsnittet](#tracking-capabilities).
   * Du kan också använda Adobe Experience Cloud-tekniker i dina mobilappar. Mer information om hur du skickar mobilleveranser med Campaign finns i [SMS-kanal](../../delivery/using/sms-channel.md) och [Mobilappskanal](../../delivery/using/about-mobile-app-channel.md).

* **Dina användares sekretessinställningar för din användning av Adobe Experience Cloud**

   Adobe ber dig att ge dina kunder en egen sekretesspolicy som beskriver:

   * Din sekretesspraxis i samband med Adobe Experience Cloud
   * Hur användare kan ange sina inställningar för insamling eller användning av information i samband med Adobe Experience Cloud

   >[!NOTE]
   >
   >Liksom för alla Adobe-produkter kan Campaign-användare avanmäla sig från att dela information som samlats in om dem via appar och webbplatser. Mer information finns i Vanliga frågor om [Adobe Experience Cloud-användning](https://www.adobe.com/privacy/experience-cloud-usage-info-faq.html).

Mer information om Adobe Experience Cloud sekretess finns på [den här sidan](https://www.adobe.com/privacy/marketing-cloud.html).

## Personuppgifter och personuppgifter {#personal-data}

När sekretessen hanteras är det viktigt att definiera vilka data som ska hanteras med omsorg och av vem.
* **Personuppgifter** är information som direkt eller indirekt kan identifiera en levande individ.
* **Känsliga personuppgifter** är information som rör en individs ras, politiska åsikter, religiösa övertygelser, kriminell bakgrund, genetiska uppgifter, hälsodata, sexuella preferenser, biometrisk information samt medlemskap i fackföreningar.

De [viktigaste lagstiftningarna](#privacy-regulations) avser de olika enheter som hanterar uppgifter enligt följande:
* En **personuppgiftsansvarig** är den myndighet som bestämmer hur och syftet med att samla in, använda och dela personuppgifter.
* En **dataprocessor** är en person eller part som samlar in, använder eller delar personuppgifter enligt den personuppgiftsansvariges anvisningar.
* En **registrerad** är en levande person vars personuppgifter samlas in, används eller delas och som direkt eller indirekt kan identifieras genom hänvisning till dessa personuppgifter.

Som företag som samlar in och delar personuppgifter är du den registeransvarige och dina kunder är de registrerade och Adobe Campaign fungerar som databehandlare när de hanterar sina personuppgifter enligt dina anvisningar. Observera att det är ditt ansvar som personuppgiftsansvariga att hantera relationen till de registrerade, t.ex. vid hantering av [sekretessförfrågningar](#privacy-requests).

När ni integrerar Campaign med andra Experience Cloud-lösningar där målgrupper kan överföras från ett system till ett annat, som [Adobe Analytics](../../platform/using/adobe-analytics-data-connector.md), [Audience Manager eller People core service](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md), [Campaign Standard](../../integrations/using/synchronizing-audiences.md)eller andra lösningar via [CRM Connectors](../../platform/using/crm-connectors.md), måste ni vara extra noga med att skydda personuppgifter.

## Datainsamling {#data-acquisition}

Med Adobe Campaign kan ni samla in data, inklusive personuppgifter och känslig information. Det är därför viktigt att du får och övervakar samtycke från dina mottagare.

* Låt alltid mottagarna godkänna att ta emot meddelanden. Om du vill göra det måste du fortsätta att efterleva avanmälningsbegäranden så snabbt som möjligt och verifiera samtycke genom en dubbel avanmälningsprocess. Mer information finns i [Skapa ett prenumerationsformulär med dubbel anmälan](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).
* Importera inte falska listor och använd dirigerade adresser för att kontrollera att din klientfil inte används bedrägligt. Mer information finns i [Om dirigerade adresser](../../delivery/using/about-seed-addresses.md).
* Genom samtycke och behörighetshantering kan ni spåra mottagarnas preferenser och hantera vem inom organisationen som har tillgång till vilka data. Mer information finns i [det här avsnittet](#consent).
* Underlätta och hantera förfrågningar om sekretess från era mottagare. Mer information finns i [det här avsnittet](#privacy-requests).

## Integritetshantering {#privacy-management}

Integritetshantering avser alla processer och verktyg som kan hjälpa er att följa sekretessbestämmelser (GDPR, CCPA, etc.). Få en översikt över vilken sekretesshantering som finns på [den här sidan](https://helpx.adobe.com/se/campaign/kb/campaign-privacy-overview.html).

Adobe Campaign tillhandahåller olika funktioner för sekretesshantering:
* Hantering av samtycke, datalagring och användarroller. Se [det här avsnittet](#consent).
* Sekretessförfrågningar (rätt till åtkomst och rätt att bli glömd). Se [det här avsnittet](#privacy-requests).
* Avanmäl dig från försäljning av personuppgifter (CCPA-specifik). Se [det här avsnittet](https://helpx.adobe.com/se/campaign/kb/acc-privacy.html#ccpa).

De viktigaste sekretessfunktionerna i Campaign och ett exempel på vilka personer som berörs presenteras i [det här avsnittet](https://helpx.adobe.com/campaign/kb/campaign-privacy-more.html#gdprpersonasandflow).


### Samtycke, bevarande och roller {#consent}

Ursprungligen har Adobe Campaign viktiga funktioner som är viktiga för sekretessen:

* **Hantering** av samtycke: Genom prenumerationshanteringsprocessen kan du hantera mottagarnas inställningar och spåra vilka mottagare som har valt vilken typ av prenumerationer du vill ha. Mer information finns i [Om prenumerationer](../../delivery/using/about-services-and-subscriptions.md).
* **Datalagring**: Alla inbyggda standardloggtabeller har förinställda lagringsperioder, vilket i allmänhet begränsar datalagringen till 6 månader eller mindre. Ytterligare kvarhållningsperioder kan ställas in med arbetsflöden. Mer information får du om du kontaktar konsulterna eller teknikadministratörerna på Adobe.
* **Rättighetshantering**: Adobe Campaign ger er möjlighet att hantera de rättigheter som tilldelats olika Campaign-operatorer via olika färdiga eller anpassade roller. På så sätt kan du hantera vilka inom företaget som kan få åtkomst till, ändra eller exportera olika typer av data. Mer information finns i [Om åtkomsthantering](../../platform/using/access-management.md).

Mer information om dessa funktioner och hur du hanterar dem i Adobe Campaign finns på [den här sidan](https://helpx.adobe.com/campaign/kb/campaign-privacy-overview.html#consent).

### Sekretessförfrågningar {#privacy-requests}

Adobe Campaign erbjuder ytterligare funktioner som hjälper dig att underlätta din beredskap som Data Controller för vissa sekretessförfrågningar:

* Den **** registrerade har rätt att få en bekräftelse från den registeransvarige på om personuppgifter som rör dem behandlas eller inte, var och varför.

* Den **rättigheten att bli glömd** (begäran om radering) ger den registrerade rätt att få registereditorn att radera sina personuppgifter.

>[!NOTE]
>
>Den här uppsättningen verktyg är till för att hjälpa dig att uppfylla dina krav på sekretess för GDPR, CCPA, PDPA och LGPD. Mer information om de olika reglerna finns på [den här sidan](https://helpx.adobe.com/se/campaign/kb/campaign-privacy-overview.html#whatisgdpr).

<!--* **GDPR** (General Data Protection Regulation) is the European Union’s (EU) privacy law that harmonizes and modernizes data protection requirements. GDPR applies to Adobe Campaign customers who hold data for Data Subjects residing in the EU.

* **CCPA** (California Consumer Privacy Act) provides California residents new rights in regards to their personal information and imposes data protection responsibilities on certain entities whom conduct business in California.

* **Thailand's PDPA** (Personal Data Protection Act) is the new privacy law that harmonizes and modernizes data protection requirements for Thailand. This regulation applies to Adobe Campaign customers who hold data for Data Subjects residing in this country.

Brazil's Lei Geral de Proteção de Dados (LGPD) will be effective starting Aug, 16 for all companies collecting or processing personal data in Brazil. This regulation also applies to Adobe Campaign customers who hold data for Data Subjects residing in this country.-->

Begäran om **åtkomst** och **borttagning** visas på [den här sidan](https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess). Implementeringsstegen för att skapa dessa begäranden beskrivs i [det här avsnittet](https://helpx.adobe.com/se/campaign/kb/acc-privacy.html#ManagingPrivacyRequests). <!--Tutorials are also available [here](https://docs.adobe.com/content/help/en/campaign-standard-learn/tutorials/privacy/privacy-overview.html).-->

## Spårningsfunktioner {#tracking-capabilities}

### Cookies {#cookies}

Tack vare spårningsfunktionerna i Adobe Campaign kan du spåra hur mottagarna ser ut med hjälp av tre typer av cookies: en sessionscookie och två permanenta cookies.

* A **session cookie**: the **nlid** cookie contains the identifier of the email sent to the contact (**broadlogId**) and the identifier of the message template (**deliveryId**). Den läggs till när kontakten klickar på en URL som ingår i ett e-postmeddelande som skickas av Adobe Campaign och låter dig spåra deras beteende på webben. Denna sessionscookie raderas automatiskt när webbläsaren stängs. Kontakten kan konfigurera sin webbläsare så att den inte tillåter cookies.
* Två **permanenta cookies**:
   * Cookien **UID** (Universal Unique IDentifier) delas mellan Adobe Experience Cloud-lösningar. Den ställs in en gång tills den försvinner från klientwebbläsaren när ett nytt värde skapas. Med denna cookie kan du identifiera de användare som interagerar med Experience Cloud-lösningarna när de besöker en webbplats. Den kan deponeras av en landningssida (för att koppla okända kundaktiviteter till en mottagare) eller av en leverans. Beskrivningen av denna cookie finns [här](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-mc.html).
   * Den **olevererade** cookien (som introducerades i Campaign Classic 20.3) är en permanent cookie som innehåller **deliveryId** för den senaste leveransen som användaren klickade på länken från. Den här cookien används för att identifiera spårningstabellen som ska användas, när sessionscookien saknas.

I sådana förordningar som den allmänna dataskyddsförordningen (GDPR) anges att företag kräver att webbplatsanvändarna godkänner avtalet innan de installerar cookies.

* Du måste informera användare om att dina webbplatser är utrustade med verktyg för webbspårning via en auktoriseringsbegäran (som visas på sidan till exempel) med en kryssruta för att godkänna användningen av cookies, eller lägga till en banderoll högst upp på den första sidan som de landar på, osv.
* Popup-fönster bör undvikas eftersom de ofta blockeras av webbläsare.

### Meddelandespårning {#message-tracking}

Med Adobe Campaign kan du spåra skickade e-postmeddelanden och hur leveransmottagarna fungerar: öppna, klicka på länkar, avsluta abonnemang osv. Mer information finns i [Om meddelandespårning](../../delivery/using/about-message-tracking.md).

Det gör du genom att lägga till [spårade länkar](../../delivery/using/how-to-configure-tracked-links.md) i meddelandena för att mäta effekten av leverans och mottagarnas beteende på fliken [Spårning](../../delivery/using/monitoring-a-delivery.md#tracking-logs) på kontrollpanelen för leverans. Spårningsdata tolkas i rapporten [Spårningsindikatorer](../../reporting/using/delivery-reports.md#tracking-indicators) .

### Webbspårning {#web-tracking}

Med Adobe Campaign kan du också övervaka hur mottagarna surfar på webbplatsen: infoga spårningstaggar för att samla in information och mäta besök på webbprogramsidor. Mer information finns i [Spåra ett webbprogram](../../web/using/tracking-a-web-application.md).

Konfigurationen av webbspårning visas i [det här avsnittet](../../configuration/using/about-web-tracking.md).

För att ytterligare hantera spårning kan du med Adobe Campaign visa en avanmälningsbanderoll så att du inte längre kan spåra webbbeteenden för slutanvändare som avanmäler sig från beteendespårning. Mer information finns i [Avanmäl dig](../../web/using/web-application-tracking-opt-out.md)till webbprogramspårning.
