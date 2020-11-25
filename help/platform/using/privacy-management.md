---
solution: Campaign Classic
product: campaign
title: Integritetshantering
description: Läs mer om sekretesshantering
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 97e039e48068e3862bc6640711efe54f21fc0f15
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 1%

---


# Integritetshantering {#privacy-management}

Adobe Campaign offers a set of tools to help you comply with [Privacy regulations](#privacy-management-regulations) (including GDPR, CCPA, PDPA, LGPD).

Här är de fem viktigaste funktionerna som Adobe Campaign erbjuder för att säkerställa beredskap för GDPR och andra sekretessbestämmelser:

![](assets/privacy-gdpr-use-cases.png)

* **Rätt till åtkomst**

* **Höger att ta bort**

Mer information finns i [Rätt till åtkomst och Rätt att bli glömd](#right-access-forgotten).

* **Hantering av samtycke**

* **Datalagring**

* **Rättighetshantering**

Mer information finns i [Godkännande, kvarhållning och roller](#consent-retention-roles).

<!--This section presents general information on what Privacy management is and the features provided by Adobe Campaign to manage the [Right to Access and Right to be Forgotten](#right-access-forgotten).

It also contains information on important features to manage Privacy ([Consent, Retention and Roles](#consent-retention-roles)), as well as best practices to help you with your Privacy compliance when using Adobe Campaign.-->

## Bestämmelser om integritetshantering {#privacy-management-regulations}

Adobe Campaign funktioner hjälper dig att följa följande regler:

* **GDPR** (den[allmänna dataskyddsförordningen](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en)) är Europeiska unionens (EU) integritetslagstiftning som harmoniserar och moderniserar dataskyddskraven för EU:s länder.
* **CCPA** ([California Consumer Privacy Act](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;kapitel=&amp;artikel=)) ger personer bosatta i Kalifornien nya rättigheter när det gäller deras personuppgifter och ålägger vissa företag som bedriver verksamhet i Kalifornien dataskydd ansvar.
* **PDPA** ([Personal Data Protection Act](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/)) är den nya integritetslagen som harmoniserar och moderniserar dataskyddskraven för Thailand.
* **LGPD** ([Lei Geral de Proteção de Dados](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf)) träder i kraft i början av 2021 för alla företag som samlar in eller behandlar personuppgifter i Brasilien.

Alla dessa bestämmelser gäller för Adobe Campaign-kunder som innehar uppgifter för registrerade personer i de respektive regioner eller länder som nämns ovan (EU, Kalifornien, Thailand, Brasilien).

<!--Several Privacy capabilities are available in Adobe Campaign, including consent management, data retention settings, and rights management. See [Consent, Retention and Roles](#consent-retention-roles). In addition to this, Adobe Campaign helps facilitate your readiness as Data Controller for certain Privacy requests. See [Right to Access and Right to be Forgotten](#right-access-forgotten).-->

>[!NOTE]
>
>Mer information om personuppgifter och om de olika enheter som hanterar data (personuppgiftsansvariga, databehandlare och registrerade) finns i [Personuppgifter och personuppgifter](../../platform/using/privacy-and-recommendations.md#personal-data).

## Rätt till åtkomst och rätt att glömma {#right-access-forgotten}

För att underlätta beredskapen för din integritet kan du med Adobe Campaign hantera förfrågningar om **åtkomst** och **borttagning** .

* Den **registrerade har rätt att få en bekräftelse från den registeransvarige på huruvida personuppgifter som rör dem behandlas, var och i vilket syfte, från den registrerade har rätt att få tillgång till** uppgifterna. Den personuppgiftsansvarige ska tillhandahålla en kostnadsfri kopia av personuppgifterna i elektroniskt format.

* Den **rättighet som ska tas bort** ger den registrerade rätt att låta den registrerade radera sina personuppgifter, upphöra med vidarespridning av uppgifterna och eventuellt låta tredje part stoppa behandlingen av uppgifterna.

Om du vill veta hur du kan skapa **Access** - och **Delete** -begäranden och hur Adobe Campaign behandlar dem läser du [implementeringsstegen](../../platform/using/privacy-requests.md).

<!--Tutorials on Privacy management in Campaign Standard are also available [here](https://docs.adobe.com/content/help/en/campaign-standard-learn/tutorials/privacy/privacy-overview.html).
https://experienceleague.corp.adobe.com/docs/campaign-standard-learn/tutorials/privacy/privacy-overview.html?lang=en-->

## Samtycke, bevarande och roller {#consent-retention-roles}

Förutom de senaste funktionerna för **höger till åtkomst** och **rätt att bli glömd** har Adobe Campaign andra viktiga funktioner som är viktiga för integriteten:

* [Hantering](#consent-management)av samtycke: prenumerationsfunktioner för hantering av preferenser
* [Datalagring](#data-retention): kvarhållningsperioder för alla standardloggtabeller, ytterligare kvarhållningsperioder kan ställas in med arbetsflöden
* [Rättighetshantering](#rights-management): dataåtkomst hanterad av namngiven rättighet

### Hantering av samtycke {#consent-management}

Samtycke innebär att den registrerade godkänner behandlingen av personuppgifter som rör en registrerade. Datakontrollanten ansvarar för att inhämta nödvändigt samtycke för den bearbetningen. Även om Adobe Campaign kan tillhandahålla vissa funktioner som hjälper en kund att hantera samtycke som rör tjänsten, ansvarar Adobe inte för samtycke. Kunderna bör arbeta med sina egna juridiska avdelningar för att fastställa sina egna processer och rutiner för att få tillstånd.

Funktionerna för att hantera vissa aspekter av samtycke har varit centrala för Adobe Campaign sedan början. Genom prenumerationshanteringen kan kunderna spåra vilka mottagare som har valt att delta i vilken typ av prenumerationer, oavsett om det är nyhetsbrev, dagliga eller veckovisa kampanjer eller andra typer av marknadsföringsprogram.

![](assets/privacy-consent-management.png)

Mer information om hantering av samtycke finns i den [detaljerade dokumentationen](../../delivery/using/managing-subscriptions.md).

Förutom de verktyg för hantering av samtycke som Adobe Campaign tillhandahåller har ni möjlighet att spåra om en konsument har valt ut för försäljning av personuppgifter. Se [det här avsnittet](../../platform/using/privacy-requests.md##sale-of-personal-information-ccpa).

### Datalagring {#data-retention}

När det gäller lagring har inbyggda loggtabeller i Campaign förinställda lagringsperioder, vilket generellt begränsar datalagringen till sex månader eller mindre.

Följande är standardvärden för kvarhållning för inbyggda tabeller. Tänk på att de tekniska administratörerna för Adobe ställer in kvarhållningskonfigurationen under implementeringen, och värdena kan variera för varje implementering baserat på kundens krav.

* **Konsoliderad spårning**: 1 år
* **Leveransloggar**: 6 månader
* **Spårningsloggar**: 1 år
* **Borttagna leveranser**: 1 vecka
* **Importavvisanden**: 6 månader
* **Besökarprofiler**: 1 månad
* **Erbjudandeförslag**: 1 år
* **Händelser**: 1 månad
* **Statistik för händelsebearbetning**: 1 år
* **Arkiverade händelser**: 1 år
* **Pipeline-händelser ignorerades**: 1 månad

Och på liknande sätt som med standardfunktioner för arbetsflöde kan du ta bort kvarhållningsperioder för anpassade tabeller.

Kontakta Adobe konsulter eller teknikadministratörer för att få veta mer om lojalitet eller om ni behöver ange lojalitet för anpassade tabeller.

### Rättighetshantering {#rights-management}

Adobe Campaign ger er möjlighet att hantera de rättigheter som tilldelats olika Campaign-operatorer via olika färdiga eller anpassade roller.

En fördel är att du kan hantera vilka inom företaget som har åtkomst till olika typer av data. Du kan till exempel ha olika marknadsförare som täcker olika geografiska områden och varje marknadsförare kan bara komma åt data från sin geo.

På samma sätt kan du med den här funktionen konfigurera olika funktioner för varje användare, till exempel begränsa vem som kan skicka leveranser eller mer relevant för sekretesshantering, som kan ändra eller exportera data.

![](assets/privacy-user-management.png)

Mer information om åtkomsthantering finns i den [detaljerade dokumentationen](../../platform/using/access-management.md).