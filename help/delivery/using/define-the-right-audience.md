---
product: campaign
title: Definiera rätt målgrupp
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: c0533148-b027-4158-9b95-8d2df769e963
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 3%

---

# Definiera rätt målgrupp {#define-the-right-audience}

Målgruppen är följande: skapa listor noggrant, testa e-postmeddelanden på populära e-postklienter och mobila enheter och se till att e-postlistorna är aktuella (utan okända eller föråldrade adresser). Du kan också skicka korrektur som hjälper dig att konfigurera en komplett valideringscykel.

Läs mer om målpopulationer [i detta avsnitt](../../delivery/using/steps-defining-the-target-population.md)

## Rikta er till rätt målgrupp {#target-the-right-audience}

När innehållet är klart måste du noga definiera vem som ska få meddelandet.

För att leveransen ska bli framgångsrik vill ni skicka det mest relevanta personaliserade innehållet till rätt mottagare. Med Adobe Campaign kan ni skapa det mest korrekta målet: kan du välja mottagare utifrån deras ålder, lokalisering, vad de har köpt, om de har klickat på en länk i en tidigare leverans osv. Med Adobe Campaign kan du även definiera testprofiler, kontrollgrupper och startadresser för att vara säker på att målet är korrekt.

## Målmappningar {#target-mappings}

I Campaign Classic är leveransmallarna som standard **mottagare** som mål. Adobe Campaign erbjuder andra målmappningar för leveranser som du kan ändra efter behov.

Du kan till exempel leverera till besökare vars profiler har samlats in via sociala nätverk eller till besökare som prenumererar på en informationstjänst.

Dessa mappningar visas [i det här avsnittet](../../delivery/using/selecting-a-target-mapping.md).

Du kan också skapa och använda en anpassad målmappning. Mer information om detta finns i [det här avsnittet](../../configuration/using/target-mapping.md).

## Externa mottagare {#external-recipients}

Du kan leverera till mottagare som lagras i en extern fil i stället för att sparas i databasen. Läs mer [i det här avsnittet](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

## Skicka till dina prenumeranter {#send-to-subscribers}

Om du vill skicka meddelanden till prenumeranterna på ett nyhetsbrev kan du rikta dem direkt till motsvarande informationstjänst. Läs mer [i det här avsnittet](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## Testmottagare och startadresser {#test-recipients-seed-addresses}

Om du vill testa leveransen använder du korrektur innan du skickar till huvudmålet.

Se till att du väljer rätt korrekturmottagare eftersom de validerar formuläret och meddelandets innehåll. Stegen för att definiera korrekturmottagare visas [i det här avsnittet](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target).

Seed-adresser används för målmottagare som inte matchar de definierade målvillkoren för att testa en leverans innan den skickas till huvudmålet. De visas [i det här avsnittet](../../delivery/using/about-seed-addresses.md).

## Ta bort dubblettadresser {#deduplicate-addresses}

Det är viktigt att undvika att ha dubbla e-postadresser, eftersom detta kan påverka ditt mål:

* Samma meddelande kan skickas mer än en gång när ett mål delas.

* Om en mottagare säger upp prenumerationen efter att ha fått ett meddelande kommer deras duplicerade profil fortfarande att få framtida meddelanden.

Borttagning av dubbletter skyddar det avsändande anseendet och garanterar en god karantänhantering.

**Relaterade ämnen:**

* [Dedupliceringsaktivitet](../../workflow/using/deduplication.md).
* [Användningsfall: Använda sammanfogningsfunktionen för aktiviteten Deduplicering](../../workflow/using/deduplication-merge.md)

## Indexera e-postadresser {#index-addresses}

För att optimera prestanda för SQL-frågor som används i programmet kan ett index deklareras från huvudelementet i dataschemat.

Stegen för att lägga till ett index till e-postadressen visas [i det här avsnittet](../../configuration/using/database-mapping.md#indexed-fields).
