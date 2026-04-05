---
product: campaign
title: Sekretesshantering
description: Läs mer om sekretesshantering
feature: Privacy, Privacy Tools
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 23c873fd-9016-4d32-842c-772cfff0e23e
source-git-commit: 647709dd4b0c70c342be03d3012bc02f10ff2c00
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 0%

---

# Sekretesshantering {#privacy-management}

Adobe Campaign erbjuder en uppsättning verktyg som hjälper dig att följa [sekretesslagstiftningen](#privacy-management-regulations) (inklusive GDPR, CCPA, PDPA, LGPD).

Här är de fem viktigaste funktionerna från Adobe Campaign för att säkerställa sekretessregler:

* **Rätt till åtkomst**
* **Höger att ta bort**
* **Hantering av samtycke**
* **Datalagring**
* **Rättighetshantering**

![](assets/privacy-gdpr-use-cases.png)

Mer information finns i [Åtkomst och rättighet att bli glömd](#right-access-forgotten) och [Medgivande, Bevarande och Roller](#consent-retention-roles).

<!--
This section presents general information on what Privacy management is and the features provided by Adobe Campaign to manage the [Right to Access and Right to be Forgotten](#right-access-forgotten).

It also contains information on important features to manage Privacy ([Consent, Retention and Roles](#consent-retention-roles)), as well as best practices to help you with your Privacy compliance when using Adobe Campaign.
-->

## Bestämmelser om integritetshantering {#privacy-management-regulations}

Adobe Campaign funktioner hjälper dig att följa följande regler:

* **GDPR** (den allmänna dataskyddsförordningen) är Europeiska unionens (EU) integritetslagstiftning som harmoniserar och moderniserar dataskyddskraven för EU:s länder.
* **CCPA** (California Consumer Privacy Act) ger personer bosatta i Kalifornien nya rättigheter när det gäller deras personuppgifter och ålägger dataskyddsansvar för vissa enheter som bedriver verksamhet i Kalifornien.
* **PDPA** (Personal Data Protection Act) är den integritetslagstiftning som harmoniserar och moderniserar dataskyddskraven för Thailand.
* **LGPD** (Lei Geral de Proteção de Dados) gäller alla företag som samlar in eller behandlar personuppgifter i Brasilien.
* **CASL** (Canadian Anti Spam Law) omfattar alla meddelanden som skickas till eller från Kanada, men inte meddelanden som skickas via Kanada.
* **VCDPA** (Virginia Consumer Data Protection Act) och **CPA** (Colorado Privacy Act) gäller för alla företag som bedriver verksamhet eller målbor i dessa delstater.

Alla dessa bestämmelser gäller för Adobe Campaign-kunder som har data för registrerade i de respektive regioner eller länder som nämns ovan.

<!--Several Privacy capabilities are available in Adobe Campaign, including consent management, data retention settings, and rights management. See [Consent, Retention and Roles](#consent-retention-roles). In addition to this, Adobe Campaign helps facilitate your readiness as Data Controller for certain Privacy requests. See [Right to Access and Right to be Forgotten](#right-access-forgotten).-->

>[!NOTE]
>
>Mer information om personuppgifter och om olika enheter som hanterar data (Data Controller, Data Processor och Data Subject) finns i [Personliga data och personuppgifter](../../platform/using/privacy-and-recommendations.md#personal-data).

## Rätt till åtkomst och rätt att glömma {#right-access-forgotten}

För att underlätta sekretessberedskapen kan du med Adobe Campaign hantera förfrågningar om **åtkomst** och **Ta bort**.

* **Åtkomsträttigheten** ger den registrerade rätt att få bekräftelse från den personuppgiftsansvarige på om personuppgifter som rör dem behandlas, var och i vilket syfte. Den personuppgiftsansvarige ska tillhandahålla en kostnadsfri kopia av personuppgifterna i elektroniskt format.

* **Rättigheten att bli glömd** (begäran om radering) kallas även dataradering och ger den registrerade rätt att få personuppgiftsbiträdet att radera sina personuppgifter, upphöra med vidare spridning av data och eventuellt få tredje parter att avbryta behandlingen av data.

Mer information om hur du kan skapa **Access** - och **Delete**-begäranden och hur Adobe Campaign behandlar dem finns i [implementeringsstegen](../../platform/using/privacy-requests.md).

<!--
Tutorials on Privacy management in Campaign Standard are also available [here](https://experienceleague.adobe.com/docs/campaign-standard-learn/tutorials/privacy/privacy-overview.html).

https://experienceleague.adobe.com/docs/campaign-standard-learn/tutorials/privacy/privacy-overview.html
-->

## Samtycke, bevarande och roller {#consent-retention-roles}

Förutom de senaste funktionerna för **Åtkomst** och **Rätt att bli glömd** har Adobe Campaign andra viktiga funktioner som är viktiga för sekretessen:

* [Hantering av samtycke](#consent-management): prenumerationsfunktioner för inställningshantering
* [Datalagring](#data-retention): datalagringsperioder i alla standardloggtabeller, ytterligare kvarhållningsperioder kan ställas in med arbetsflöden
* [Rättighetshantering](#rights-management): dataåtkomst hanteras av namngiven rättighet

### Hantering av samtycke {#consent-management}

Samtycke innebär att den registrerade godkänner behandlingen av personuppgifter som rör en registrerad. Datakontrollanten ansvarar för att inhämta nödvändigt samtycke för den bearbetningen. Även om Adobe Campaign kan tillhandahålla vissa funktioner som hjälper en kund att hantera samtycke som rör tjänsten, ansvarar Adobe inte för samtycke. Kunderna bör arbeta med sina egna juridiska avdelningar för att fastställa sina egna processer och rutiner för att få tillstånd.

Funktionerna för att hantera vissa aspekter av samtycke har varit centrala för Adobe Campaign sedan början. Genom prenumerationshanteringen kan kunderna spåra vilka mottagare som har valt att delta i vilken typ av prenumerationer, oavsett om det är nyhetsbrev, dagliga eller veckovisa kampanjer eller andra typer av marknadsföringsprogram.

![](assets/privacy-consent-management.png)

Mer information om hantering av samtycke finns i den [detaljerade dokumentationen](../../delivery/using/managing-subscriptions.md).

Förutom de verktyg för hantering av samtycke som Adobe Campaign tillhandahåller har ni möjlighet att spåra om en konsument har valt ut för försäljning av personuppgifter. Se [det här avsnittet](../../platform/using/privacy-requests.md#sale-of-personal-information-ccpa).

### Datalagring {#data-retention}

När det gäller lagring har inbyggda loggtabeller i Campaign förinställda lagringsperioder, vilket generellt begränsar datalagringen till sex månader eller mindre.

Följande är standardvärden för kvarhållning för inbyggda tabeller. Tänk på att lagringskonfigurationen ställs in av Adobe tekniska administratörer under implementeringen, och värdena kan variera för varje implementering baserat på kundens krav.

* **Konsoliderad spårning**: 1 år
* **Leveransloggar**: 6 månader
* **Spårningsloggar**: 1 år
* **Borttagna leveranser**: 1 vecka
* **Importavslag**: 6 månader
* **Besökarprofiler**: 1 månad
* **Erbjudandeerbjudanden**: 1 år
* **Händelser**: 1 månad
* **Statistik för händelsebearbetning**: 1 år
* **Arkiverade händelser**: 1 år
* **Pipeline-händelser ignorerades**: 1 månad
* **Dynamisk rapportering**: 13 månader

Och på liknande sätt som med standardfunktioner för arbetsflöde kan du ta bort kvarhållningsperioder för anpassade tabeller.

Kontakta Adobe konsulter eller teknikadministratörer för att få veta mer om lojalitet eller om ni behöver ange lojalitet för anpassade tabeller.

### Rights Management {#rights-management}

Adobe Campaign ger er möjlighet att hantera de rättigheter som tilldelats olika Campaign-operatorer via olika färdiga eller anpassade roller.

En fördel är att du kan hantera vilka inom företaget som har åtkomst till olika typer av data. Du kan till exempel ha olika marknadsförare som täcker olika geografiska områden och varje marknadsförare kan bara komma åt data från sin geo.

På samma sätt kan du med den här funktionen konfigurera olika funktioner för varje användare, till exempel begränsa vem som kan skicka leveranser eller mer relevant för sekretesshantering, som kan ändra eller exportera data.

![](assets/privacy-user-management.png)

Mer information om åtkomsthantering finns i [detaljerad dokumentation](../../platform/using/access-management.md).
