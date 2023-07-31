---
product: campaign
title: Vanliga frågor och svar om att testa och skicka
description: Vanliga frågor och svar om Campaign Classic
feature: Troubleshooting
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 7fc24ef2-b021-440b-b1f2-8c77e2425328
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 97%

---

# Validera, skicka och spåra meddelanden {#validate-send-track}



## Testa och validera {#test-and-validate-before-sending}

Läs mer om hur man utför test- och valideringssteg innan du skickar meddelanden inom Adobe Campaign.

### Vad är leveransanalysen? {#what-is-the-delivery-analysis-}

Leveransanalysen är den fas under vilken målgruppen beräknas och leveransinnehållet färdigställs. När leveransen är klar kan den skickas. Läs loggarna för att kontrollera att allt är korrekt.

[Klicka här för att läsa mer](../../delivery/using/steps-validating-the-delivery.md).

### Varför ska jag skapa korrekturer? {#why-should-i-create-proofs-}

Adobe rekommenderar starkt att du skapar korrekturmeddelanden för att testa leveransen med en godkännandegrupp innan den skickas till huvudmålet. Då kan du validera meddelandeinnehåll, personalisering och leveransparametrar.

[Klicka här för att läsa mer](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Så använder du fröadresser i Adobe Campaign.  {#how-to-use-seed-addresses-in-adobe-campaign-}

Fröadresser används för mottagare i målgruppen som inte matchar dess definierade villkor. Dessa mottagare läggs till i målgruppen. De kan importeras eller skapas direkt i leveransen eller kampanjen. För leveranser med direktutskick läggs de till vid extraheringen och blandas i dokumentet med utdata.

Detta har följande fördelar:

* Slumpmässig ersättning av fält med data från mottagarprofiler. Detta låter dig till exempel ange endast e-postadressen i avsnittet för fröadress.
* När du använder ett arbetsflöde med datahanteringsfunktioner kan ytterligare data som bearbetas i leveranser anges på fröadressnivå för att framtvinga värden. Detta kringgår att slumpmässiga värden byts ut.

[Klicka här för att läsa mer om fröadresser](../../delivery/using/about-seed-addresses.md).

### Hur kan jag ställa in en godkännandeprocess innan jag skickar meddelanden? {#how-can-i-set-up-an-approval-process-before-sending-messages-}

För att upptäcka eventuella fel i meddelandekonfigurationen rekommenderar Adobe att du skapar en leveransvalideringscykel. Se till att innehållet godkänns så ofta som det behövs genom att skicka korrekturer till testmottagare. Ett korrektur ska skickas varje gång en ändring görs för att godkänna innehållet.

[Klicka här för att läsa mer](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Vad är en typologiregel? {#what-is-a-typology-rule-}

För att undvika konflikter mellan kampanjer kan Adobe Campaign testa olika kombinationer genom att tillämpa särskilda begränsningsregler. Detta garanterar att de meddelanden som skickas bäst uppfyller kundernas behov och förväntningar i enlighet med företagets kommunikationspolicyer.

[Klicka här för att läsa mer](../../campaign-opt/using/about-campaign-typologies.md).

## Skicka meddelanden {#send-your-messages}

Läs mer om hur man skickar meddelanden över olika kanaler med Adobe Campaign.

### Hur skickar jag e-post i omgångar? {#how-can-i-send-emails-in-waves-}

Innan du skickar en leverans till en stort antal personer kan du [konfigurera omgångar](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) vilket innebär att meddelanden delas upp i flera grupper och balanserar belastningen.

### Vilka är de viktigaste stegen för att skapa ett e-postmeddelande i Campaign? {#which-are-the-key-steps-to-create-an-email-in-campaign-}

När e-postleveransen har skapats och validerats kan du skicka den. Du kan välja att skicka e-postmeddelandet till huvudmålet omedelbart eller schemalägga en leverans vid ett senare datum. Innan dess kan du vid behov även beräkna målgruppen.

[Klicka här för att läsa mer](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Så schemalägger man en leverans.  {#how-to-schedule-a-delivery-}

Du kan skjuta upp leveransen av meddelanden för att schemalägga den eller för att hantera säljtrycket och undvika att överbelasta en grupp.

[Klicka här för att läsa mer](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

### Kan jag lägga till en bilaga i e-postmeddelanden? {#can-i-add-an-attachment-to-emails-}

Med Campaign Classic kan du lägga till personliga bilagor i alla e-postmeddelanden.

[Klicka här för att läsa mer om e-postbilagor](../../delivery/using/attaching-files.md).

## Spåra dina meddelanden och mät deras inverkan {#track-your-messages-and-measure-their-impact}

Läs mer om hur man spårar och mäter inverkan av skickade meddelanden med Adobe Campaign.

### Hur konfigurerar jag spårade länkar i en e-postleverans? {#how-can-i-configure-tracked-links-in-an-email-delivery-}

För varje leverans kan du spåra mottagningen av meddelanden och aktiveringen av länkarna som har infogats i meddelandets innehåll. På så sätt kan du spåra mottagarnas beteende beroende på de leveransåtgärder de har fått som mål.

För varje URL i meddelandet kan du till exempel välja om du vill aktivera spårning, ändra länketiketten eller gruppera länkar per kategorier för rapporteringsändamål.

[Klicka här för att läsa mer](../../delivery/using/about-message-tracking.md) om hur du spårar meddelanden i Campaign Classic.

### Var kan jag komma åt leverans- och spårningsloggar? {#where-can-i-access-delivery-and-tracking-logs-}

Lär dig spåra leveranser och förstå mottagarnas beteende [från den här sidan](../../delivery/using/delivery-dashboard.md).

### Var kan jag få leveransrapporter? {#where-can-i-get-delivery-reports-}

Adobe Campaign har en uppsättning rapporter för att övervaka leveranser och spåra meddelanden.

[Klicka här för att läsa mer om inbyggda rapporter](../../reporting/using/delivery-reports.md).

### Hur kvalificerar och hanterar Adobe Campaign karantänadresser? {#how-does-adobe-campaign-qualify-and-manage-quarantine-addresses-}

Adobe Campaign hanterar en lista med adresser i karantän. Mottagare vars adress sätts i karantän exkluderas som standard vid leveransanalys och anges inte som mål. En e-postadress kan sättas i karantän när till exempel postlådan är full eller om adressen inte finns.

[Klicka här för att läsa mer om karantänhantering](../../delivery/using/understanding-quarantine-management.md).
