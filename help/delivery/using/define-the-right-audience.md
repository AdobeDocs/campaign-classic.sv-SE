---
product: campaign
title: Definiera rätt målgrupp
description: Lär dig de bästa sätten att välja målgrupp
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Audiences
role: User
hide: true
hidefromtoc: true
exl-id: c0533148-b027-4158-9b95-8d2df769e963
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 3%

---

# Definiera rätt målgrupp {#define-the-right-audience}

Målgruppspopulationen är avgörande: skapa listor noggrant, testa e-postmeddelanden på populära e-postklienter och mobila enheter och se till att e-postlistorna är aktuella (utan okända eller föråldrade adresser). Du kan också skicka korrektur som hjälper dig att konfigurera en komplett valideringscykel.

Läs mer om målpopulationer [i det här avsnittet](steps-defining-the-target-population.md)

## Rikta er till rätt målgrupp {#target-the-right-audience}

När innehållet är klart måste du noga definiera vem som ska få meddelandet.

För att leveransen ska bli framgångsrik vill ni skicka det mest relevanta personaliserade innehållet till rätt mottagare. Med Adobe Campaign kan du skapa det mest korrekta målet: du kan välja mottagare utifrån deras ålder, lokalisering, vad de köpt, om de klickat på en länk i en tidigare leverans osv. Med Adobe Campaign kan du även definiera testprofiler, kontrollgrupper och startadresser för att vara säker på att målet är korrekt.

## Målmappningar {#target-mappings}

I Campaign Classic är leveransmallarna som standard avsedda för **mottagare**. Adobe Campaign erbjuder andra målmappningar för leveranser som du kan ändra efter behov.

Du kan till exempel leverera till besökare vars profiler har samlats in via sociala nätverk eller till besökare som prenumererar på en informationstjänst.

Dessa mappningar presenteras [ i det här avsnittet](steps-defining-the-target-population.md#select-a-target-mapping).

Du kan också skapa och använda en anpassad målmappning. Mer information om detta finns i [det här avsnittet](../../configuration/using/target-mapping.md).

## Externa mottagare {#external-recipients}

Du kan leverera till mottagare som lagras i en extern fil i stället för att sparas i databasen. Läs mer [i det här avsnittet](steps-defining-the-target-population.md#selecting-external-recipients).

## Skicka till prenumeranterna {#send-to-subscribers}

Om du vill skicka meddelanden till prenumeranterna på ett nyhetsbrev kan du rikta dem direkt till motsvarande informationstjänst. Läs mer [i det här avsnittet](managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


## Testa mottagare och startadresser {#test-recipients-seed-addresses}

Om du vill testa leveransen använder du korrektur innan du skickar till huvudmålet.

Se till att du väljer rätt korrekturmottagare eftersom de validerar formuläret och meddelandets innehåll. Stegen för att definiera korrekturmottagare visas [i det här avsnittet](steps-defining-the-target-population.md#selecting-the-proof-target).

Seed-adresser används för målmottagare som inte matchar de definierade målvillkoren för att testa en leverans innan den skickas till huvudmålet. De visas [ i det här avsnittet](about-seed-addresses.md).

## Deduplicera adresser {#deduplicate-addresses}

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
