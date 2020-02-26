---
title: Testa och skicka frågor och svar
seo-title: Validera, skicka och spåra meddelanden
description: Vanliga frågor om Campaign Classic
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8ef56aa04a3ecc94e9e3dda24562760d6a93739d

---


# Validera, skicka och spåra meddelanden {#validate-send-track}

## Testning och validering {#test-and-validate-before-sending}

Lär dig hur du utför test- och valideringssteg innan du skickar meddelanden i Adobe Campaign.

### Vad är leveransanalysen? {#what-is-the-delivery-analysis-}

Leveransanalysen är den fas under vilken målpopulationen beräknas och leveransinnehållet färdigställs. När leveransen är klar kan den skickas. Läs loggarna för att kontrollera att allt är korrekt.

[Klicka här om du vill veta mer](../../delivery/using/steps-validating-the-delivery.md).

### Varför ska jag skapa korrektur? {#why-should-i-create-proofs-}

Adobe rekommenderar starkt att du skapar korrekturmeddelanden för att testa leveransen i en godkännandegrupp innan du skickar den till huvudmålet. Sedan kan ni validera meddelandeinnehåll, personalisering och leveransparametrar.

[Klicka här om du vill veta mer](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof). Du kan också titta på [den här videon](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/managing-seed-and-proofs.html).

### Hur använder man dirigerade adresser i Adobe Campaign? {#how-to-use-seed-addresses-in-adobe-campaign-}

Seed-adresser används för målmottagare som inte matchar de definierade målvillkoren. Dessa mottagare läggs till i målet: kan importeras eller skapas direkt i leveransen eller kampanjen. För direktutskick läggs de till vid extraheringen och blandas i utdatadokumentet.

Detta har följande fördelar:

* Slumpmässig ersättning av fält med data från mottagarprofiler: gör att du bara kan ange e-postadressen, till exempel i avsnittet för startadress.
* När du använder ett arbetsflöde med datahanteringsfunktioner kan ytterligare data som bearbetas i leveranser anges på dirigeringsadressnivå för att framtvinga värden: den här sidan gör att slumpmässiga värden byts ut.

[Klicka här om du vill veta mer om dirigerade adresser](../../delivery/using/about-seed-addresses.md).

### Hur kan jag konfigurera en godkännandeprocess innan jag skickar meddelanden? {#how-can-i-set-up-an-approval-process-before-sending-messages-}

För att upptäcka eventuella fel i meddelandekonfigurationen rekommenderar Adobe att du skapar en leveransvalideringscykel. Se till att innehållet godkänns så ofta som det behövs genom att skicka korrektur till testmottagarna. Ett korrektur ska skickas varje gång en ändring görs för att godkänna innehållet.

[Klicka här om du vill veta mer](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Vad är en typologiregel? {#what-is-a-typology-rule-}

För att undvika konflikter mellan kampanjer kan Adobe Campaign testa olika kombinationer genom att tillämpa särskilda begränsningsregler. Detta garanterar att de meddelanden som skickas bäst uppfyller kundernas behov och förväntningar, i enlighet med företagets kommunikationspolicy.

[Klicka här om du vill veta mer](../../campaign/using/about-campaign-typologies.md).

## Skicka meddelanden {#send-your-messages}

Lär dig hur du skickar meddelanden i olika kanaler med Adobe Campaign.

### Hur skickar jag e-post i påfyllnader? {#how-can-i-send-emails-in-waves-}

Innan du skickar en leverans till en stor population kan du [konfigurera vågor](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) så att meddelanden delas upp i flera batchar och lasten balanseras.

### Vilka är de viktigaste stegen för att skapa ett e-postmeddelande i Campaign? {#which-are-the-key-steps-to-create-an-email-in-campaign-}

När e-postleveransen har skapats och validerats kan du skicka den. Du kan välja att skicka e-postmeddelandet till huvudmålet omedelbart eller schemalägga en leverans för ett senare datum. Innan dess kan du vid behov även beräkna målpopulationen.

[Klicka här om du vill veta mer](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Hur schemalägger man en leverans? {#how-to-schedule-a-delivery-}

Du kan skjuta upp leveransen av meddelanden för att schemalägga leveransen eller för att hantera försäljningstrycket och undvika att överbelasta en population.

[Klicka här om du vill veta mer](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

### Kan jag lägga till en bilaga i e-postmeddelanden? {#can-i-add-an-attachment-to-emails-}

Med Campaign Classic kan ni lägga till personliga bilagor i era e-postmeddelanden.

[Klicka här om du vill veta mer om e-postbilagor](../../delivery/using/attaching-files.md).

## Spåra era meddelanden och mät deras effekt {#track-your-messages-and-measure-their-impact}

Lär dig hur du spårar och mäter effekten av Adobe Campaign när dina meddelanden har skickats.

### Hur konfigurerar jag spårade länkar i en e-postleverans? {#how-can-i-configure-tracked-links-in-an-email-delivery-}

För varje leverans kan du spåra mottagningen av meddelanden och aktiveringen av länkarna som infogats i meddelandeinnehållet. På så sätt kan du spåra mottagarnas beteende efter de leveransåtgärder som de har fått som mål.

För varje URL för meddelandet kan du välja om du vill aktivera spårning, ändra länketiketten, gruppera länkar efter kategorier för exempelvis rapportsyfte.

[Klicka här om du vill veta mer](../../delivery/using/about-message-tracking.md) om hur du spårar meddelanden i Campaign Classic.

### Var kan jag komma åt leverans- och spårningsloggar? {#where-can-i-access-delivery-and-tracking-logs-}

Lär dig hur du spårar leveranser och förstår mottagarnas beteende [från den här sidan](../../delivery/using/monitoring-a-delivery.md).

### Var kan jag få leveransrapporter? {#where-can-i-get-delivery-reports-}

Adobe Campaign innehåller en uppsättning rapporter för att övervaka era leveranser och spåra era meddelanden.

[Klicka här om du vill veta mer om inbyggda rapporter](../../reporting/using/delivery-reports.md).

### Hur kvalificerar och hanterar Adobe Campaign karantänadresser? {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

Adobe Campaign hanterar en lista med adresser i karantän. Mottagare vars adress sätts i karantän exkluderas som standard vid leveransanalys och anges inte som mål. En e-postadress kan sättas i karantän, till exempel när postlådan är full eller om adressen inte finns.

[Klicka här om du vill veta mer om karantänhantering](../../delivery/using/understanding-quarantine-management.md).
