---
solution: Campaign Classic
product: campaign
title: Sekretess och samtycke
description: Läs mer om sekretess och samtycke
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 9e31f69fde38dcdc7f4e6d3ba3fb17911f96ded8
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---


# Frågor och svar om sekretess {#privacy-faq}

Här är några av de vanliga frågorna om sekretess och samtycke när du använder Adobe Campaign.

## Viktiga termer {#key-terms}

**Vilka är nyckelvillkoren för sekretess?**

Nedan finns en länk till de viktigaste villkoren och begreppen för sekretess och samtycke i Adobe Campaign:

* [Bestämmelser om sekretesshantering](../../platform/using/privacy-management.md#privacy-management-regulations)
* [Personuppgifter och personuppgifter](../../platform/using/privacy-and-recommendations.md#personal-data)
* [Rätt till åtkomst och rätt att glömma](../../platform/using/privacy-management.md#right-access-forgotten)
* [Samtycke, bevarande och roller](../../platform/using/privacy-management.md#consent-retention-roles)

## Beredskap för sekretesslagstiftning {#privacy-regulations-readiness}

**Vad föreslår Adobe Campaign för att följa de senaste sekretessbestämmelserna?**

Adobe lämnar ingen juridisk rådgivning. Ni bör samarbeta med era egna jurister för att säkerställa att de vidtar alla nödvändiga åtgärder för att nå fram till GDPR, CCPA, PDPA, LGPD eller någon annan tillämplig beredskap för reglering.

**Förbered för dataåtkomst och -borttagning**

* Identifiera en process för att ta emot/besvara förfrågningar från registrerade, inklusive att utse en kontaktpunkt för integritetsskydd.

* Granska de olika kunddata som lagras i Adobe Campaign och identifiera unika identifierare (det kommer troligen att finnas fler än en).

* Bestäm en policy och process för validering/autentisering för att bekräfta identiteten på registrerade personer.

* Se till att den registrerades svar är lätt att förstå.

**Överväg samtycke**

* Ange och uppdatera vid behov alla kontaktpunkter för datainhämtning för GDPR (dvs. överväg språk, mekanism för samtycke och godkännandeloggar).

* Se till att alla marknadsföringsmejl innehåller länkarna för att avbryta prenumerationen.

* Utvärdera den globala strategin för e-postmarknadsföring för att fastställa geografiska implementeringar.

**Förstå era data**

* Granska alla import- och hämtningskällor där data flödar in i Adobe Campaign och dokumentera vilka fält som används i marknadsföringsarbetet.

* Ta bort oanvända dataattribut från Adobe Campaign-databasen.

* Använd data som finns i Adobe Campaign för den avsikt de fångats in och ge era mottagare bättre personaliserade upplevelser.

* Granska och uppdatera behörigheter för dataåtkomst för att säkerställa att Adobe Campaign-användare kan utnyttja endast de data som behövs för att köra sina kampanjer, men inte komma åt data utöver det här.

* Se till att alla användare av Adobe Campaign har rätt åtkomstbehörighet för att utföra de uppgifter de behöver, men att de inte har några andra rättigheter att utföra ytterligare uppgifter.

## Bevara användarengagemang {#preserve-user-engagement}

**Hur kan Data Controllers få sitt samtycke med minimal inverkan på användarinteraktionen?**

I de fall där samtycke kommer att behövas för vissa marknadsföringsaktiviteter måste konsumentens samtycke vara aktivt (dvs. ingen tystnad som samtycke eller förkryssade kryssrutor), fristående, och det får inte vara villkorat av att tjänsterna erbjuds.

Det kan till och med finnas tillfällen då vissa samtycke behöver uppdateras för att kunna fortsätta använda data som går framåt.

I stället för att tänka på dessa krav på ökat medgivande som en risk för det marknadsföringsbara universum, skulle marknadsförarna kunna använda dem som en sann indikator på varumärkesengagemang och varumärkeslojalitet, liksom kundnöjdhet och förtroende.

## Hantera samtycke {#manage-consent}

**Hur kan Data Controllers hantera samtycke i Adobe Campaign?**

Adobe Campaign har redan funktioner för att hantera samtycke på fler nivåer än de flesta marknadsförare använder via anpassade datafält eller via en eller flera tjänster.

Marknadsförarna bör höra med sin juristrådgivare om hur de ska gå vidare och sedan utnyttja de funktioner som redan finns i Adobe Campaign.

Du kan t.ex. utöka datamodellen i Adobe Campaign så att den inte bara spåras om någon har anmält sig, utan även tidsstämpeln för anmälan och en typ av indikator som anger det exakta tillämpningsområdet för samtycke.

## Radering av data {#data-deletion}

**Vilka data kan personuppgiftsansvariga radera i Adobe Campaign som svar på en kundförfrågan från en registrerad?**

Alla data som är kopplade till den registrerade tas bort, inklusive färdiga och anpassade tabeller.

Tekniskt sett raderas alla data som är länkade till den registrerade med `integrity="own"` data.

Som Data Controller har du möjlighet att anpassa detta genom att ändra integriteten för länkar som definieras i dataschemat (t.ex. om du har en affärsjustering för att inte ta bort vissa data).

**Hur påverkas rapporter när leverans- och spårningsloggar tas bort?**

Rapporterna i Adobe Campaign baseras på indikatorer som beräknas på aggregerade data från leverans- och spårningsloggar. Om du tar bort de enskilda loggarna påverkas därför inte de mätvärden som visas i rapporterna.

## Importera data igen {#re-import-data}

**I Adobe Campaign överförs ofta poster från en extern datakälla. Måste jag tänka på att eventuellt importera om data vid ett senare datum?**

Som personuppgiftsansvarig måste du se till att du tar bort alla nödvändiga data om den registrerade från alla dina system när du tar emot en raderingsbegäran.

## Anmäl dig igen {#opt-in-again}

**Kan en registrerade, vars uppgifter har raderats från Adobe Campaign, anmäla sig senare?**

En registrerade kan anmäla sig igen eller läggas till som ny mottagare efter att hans/hennes uppgifter har raderats från Adobe Campaign.

Du kan använda granskningsspåret som anger när den tidigare borttagningen utfördes och när den nya mottagaren skapades.