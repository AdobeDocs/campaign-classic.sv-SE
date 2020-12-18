---
solution: Campaign Classic
product: campaign
title: Definiera rätt publik
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 3%

---


# Definiera rätt publik {#define-the-right-audience}

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

Läs mer [i det här fallet](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery).

## Indexera e-postadresser {#index-addresses}

För att optimera prestanda för SQL-frågor som används i programmet kan ett index deklareras från huvudelementet i dataschemat.

Stegen för att lägga till ett index till e-postadressen visas [i det här avsnittet](../../configuration/using/database-mapping.md#indexed-fields).
