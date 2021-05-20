---
solution: Campaign Classic
product: campaign
title: Sekretesshantering
description: Läs mer om sekretesshantering
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 23c873fd-9016-4d32-842c-772cfff0e23e
source-git-commit: 9781e313e03489d203e14ab0c426aa1001c7a257
workflow-type: ht
source-wordcount: '887'
ht-degree: 100%

---

# Sekretesshantering {#privacy-management}

Adobe Campaign erbjuder en uppsättning verktyg som hjälper dig att följa [integritetsregleringen](#privacy-management-regulations) (inklusive GDPR, CCPA, PDPA och LGPD).

Här följer de fem viktigaste funktionerna som Adobe Campaign erbjuder för att säkerställa beredskap för GDPR och andra integritetsregleringar:
* **Åtkomsträttigheter**
* **Rätt att radera**
* **Medgivandehantering**
* **Datalagring**
* **Hantering av rättigheter**

![](assets/privacy-gdpr-use-cases.png)

Mer information finns i [Åtkomsträttighet och rätt att glömmas](#right-access-forgotten) och [Medgivande, kvarhållning och roller](#consent-retention-roles).

<!--This section presents general information on what Privacy management is and the features provided by Adobe Campaign to manage the [Right to Access and Right to be Forgotten](#right-access-forgotten).

It also contains information on important features to manage Privacy ([Consent, Retention and Roles](#consent-retention-roles)), as well as best practices to help you with your Privacy compliance when using Adobe Campaign.-->

## Bestämmelser om integritetshantering {#privacy-management-regulations}

Funktionerna i Adobe Campaign hjälper dig att efterleva följande regler:

* **GDPR** ([allmänna dataskyddsförordningen](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en)) är EU:s integritetslagstiftning som harmoniserar och moderniserar kraven på skydd av personuppgifter.
* **CCPA** ([California Consumer Privacy Act](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;chapter=&amp;article=)) ger personer bosatta i Kalifornien nya rättigheter när det gäller deras personuppgifter och ålägger vissa enheter som bedriver verksamhet i Kalifornien skyldigheter när det gäller dataskydd.
* **PDPA** ([Personal Data Protection Act](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/)) är den nya integritetslagstiftningen som harmoniserar och moderniserar dataskyddskraven i Thailand.
* **LGPD** ([Lei Geral de Proteção de Dados](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf)) börjar gälla i början av 2021 för alla företag som samlar in eller behandlar personuppgifter i Brasilien.

Alla dessa bestämmelser gäller för kunder i Adobe Campaign som innehar data för registrerade personer i de respektive regioner eller länder som nämns ovan (EU, Kalifornien, Thailand och Brasilien).

<!--Several Privacy capabilities are available in Adobe Campaign, including consent management, data retention settings, and rights management. See [Consent, Retention and Roles](#consent-retention-roles). In addition to this, Adobe Campaign helps facilitate your readiness as Data Controller for certain Privacy requests. See [Right to Access and Right to be Forgotten](#right-access-forgotten).-->

>[!NOTE]
>
>Mer information om personuppgifter och de olika enheter som hanterar data (personuppgiftsansvarig, personuppgiftsbiträde och registrerad) finns i [Personuppgifter och personer](../../platform/using/privacy-and-recommendations.md#personal-data).

## Åtkomsträttigheter och rätt att glömmas {#right-access-forgotten}

För att underlätta beredskapen gällande din integritet kan du hantera förfrågningar om **åtkomst** och **borttagning** med Adobe Campaign.

* **Åtkomsträttigheterna** är den registrerades rätt att från personuppgiftsansvarige få bekräftelse på om personuppgifter som rör dem behandlas eller inte, var de befinner sig och för vilket syfte. Den personuppgiftsansvarige ska tillhandahålla en kostnadsfri kopia av personuppgifterna i elektroniskt format.

* **Rätten att glömmas** (förfrågan om borttagning), även känd som Radering av data, ger den registrerade rätt att låta den personuppgiftsansvarige radera sina personuppgifter, upphöra med ytterligare spridning av uppgifterna och eventuellt få tredje part att stoppa behandlingen av uppgifterna.

Se [implementeringsstegen](../../platform/using/privacy-requests.md) för att läsa om hur du kan skapa förfrågningar om **åtkomst** och **borttagning** och hur Adobe Campaign bearbetar dem.

<!--Tutorials on Privacy management in Campaign Standard are also available [here](https://docs.adobe.com/content/help/en/campaign-standard-learn/tutorials/privacy/privacy-overview.html).
https://experienceleague.adobe.com/docs/campaign-standard-learn/tutorials/privacy/privacy-overview.html?lang=en-->

## Medgivande, lagring och roller {#consent-retention-roles}

Förutom de senaste funktionerna gällande **åtkomsträttigheter** och **rätt att glömmas** erbjuder Adobe Campaign andra viktiga funktioner som är viktiga för integritet:

* [Medgivandehantering](#consent-management): prenumerationsfunktioner för hantering av preferenser
* [Datalagring](#data-retention): datalagringsperioder för alla standardiserade loggtabeller. Ytterligare datalagringsperioder kan ställas in med arbetsflöden
* [Hantering av rättigheter](#rights-management): dataåtkomst hanterad utifrån namngiven rättighet

### Medgivandehantering {#consent-management}

Medgivande innebär att den registrerade godkänner behandlingen av personuppgifter som rör sig själv. Personuppgiftsansvarige ansvarar för att erhålla nödvändigt medgivande för behandlingen. Även om Adobe Campaign kan tillhandahålla vissa funktioner som hjälper en kund att hantera medgivande som rör tjänsten, ansvarar Adobe inte för medgivandet i sig. Kunder bör arbeta med sina egna juridiska avdelningar för att fastställa egna processer och rutiner gällande att få medgivande.

Funktionerna som hjälper till att hantera vissa aspekter av medgivandet har varit centrala för Adobe Campaign sedan tidigt. Genom prenumerationshanteringen kan kunder spåra vilka mottagare som har valt att delta i vilken typ av prenumeration, oavsett om det är nyhetsbrev, dagliga eller veckovisa kampanjer eller andra typer av marknadsföringsprogram.

![](assets/privacy-consent-management.png)

Mer information om medgivandehantering finns i den [detaljerade dokumentationen](../../delivery/using/managing-subscriptions.md).

Förutom verktygen för medgivandehantering som finns i Adobe Campaign har du möjligheten att spåra om en konsument har avanmält sig till försäljning av personuppgifter. Se [det här avsnittet](../../platform/using/privacy-requests.md#sale-of-personal-information-ccpa).

### Datalagring {#data-retention}

När det gäller lagring har inbyggda loggtabeller i Campaign förinställda lagringsperioder vilket generellt begränsar datalagringen till sex månader eller mindre.

Följande är standardvärden gällande lagring för inbyggda tabeller. Var medveten om att lagringskonfigurationen ställs in av Adobes tekniska administratörer under implementeringen och att värdena kan variera för varje implementering baserat på kundens krav.

* **Konsoliderad spårning**: 1 år
* **Leveransloggar**: 6 månader
* **Spårningsloggar**: 1 år
* **Raderade leveranser**: 1 vecka
* **Importavvisanden**: 6 månader
* **Besökarprofiler**: 1 månad
* **Erbjudandeförslag**: 1 år
* **Händelser**: 1 månad
* **Statistik över händelsebearbetning**: 1 månader
* **Arkiverade händelser**: 1 år
* **Ignorerade pipeline-händelser**: 1 månad

Och på samma sätt som att ta bort kan man med standardiserad arbetsflödesfunktionalitet ställa in lagringsperioder för alla anpassade tabeller.

Kontakta Adobes konsulter eller teknikadministratörer för att veta mer om lagring eller om ni behöver ställa in lagring för anpassade tabeller.

### Hantering av rättigheter {#rights-management}

Adobe Campaign ger dig möjligheten att hantera de rättigheter som tilldelats olika operatörer i Campaign via olika färdiga eller anpassade roller.

En fördel är att du kan hantera vilka inom företaget som har åtkomst till olika typer av data. Du kan till exempel ha olika marknadsförare som täcker olika geografiska områden och varje marknadsförare kan bara komma åt data från sitt eget område.

På samma sätt kan du med den här funktionen konfigurera olika funktioner för varje användare såsom att begränsa vem som kan skicka leveranser. Mer relevant för integritetshantering är det dock att man kan begränsa vem som kan ändra eller exportera data.

![](assets/privacy-user-management.png)

Mer information om åtkomsthantering finns i den [detaljerade dokumentationen](../../platform/using/access-management.md).
