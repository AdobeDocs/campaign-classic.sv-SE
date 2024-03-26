---
product: campaign
title: Vanliga frågor och svar om arbetsflöden
description: Vanliga frågor och svar om Campaign Classic
feature: Troubleshooting, Workflows
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 7d1bb3c6-d056-4212-9500-75459a0046fa
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 78%

---

# Vanliga frågor och svar om arbetsflöden {#workflows-faq}



Lär dig att orkestrera processer och uppgifter med arbetsflöden i Adobe Campaign.

## Vilka är de viktigaste stegen för att skapa ett arbetsflöde? {#what-are-the-key-steps-to-create-a-workflow-}

[Klicka här för att lära dig hur du skapar ditt första arbetsflöde](../../workflow/using/building-a-workflow.md). Lär dig mer om koncept och bästa praxis för att skapa arbetsflöden i Campaign.

## Hur importerar jag data i Campaign? {#how-can-i-import-data-in-campaign-}

Lär dig de bästa sätten att importera data i [det här avsnittet](../../platform/using/import-export-best-practices.md).

## Kan jag övervaka arbetsflödeskörningen? {#can-i-monitor-workflow-execution-}

Läs om hur man övervakar körningen av arbetsflödet i Campaign [på den här sidan](../../workflow/using/starting-a-workflow.md).

## Hur uppdaterar jag Campaign-data med ett arbetsflöde? {#how-can-i-update-campaign-data-with-a-workflow-}

Du kan utföra omfattande uppdateringar samt sammanfoga och infoga data i databasen.

[Klicka här för att läsa mer](../../workflow/using/update-data.md).

## Hur kan jag utnyttja datahanteringsfunktionerna? {#how-can-i-leverage-data-management-capabilities-}

I Adobe Campaign kan du dra nytta av en uppsättning aktiviteter för att lösa komplexa problem med målgrupper genom att erbjuda mer effektiva och flexibla verktyg. Datahanteringsaktiviteter låter dig implementera konsekvent hantering av all kommunikation med en kontakt med hjälp av information som är länkad till dennes kontrakt, prenumerationer och reaktivitet på leveranser osv. Datahantering låter dig följa datas livscykeln under segmenteringsåtgärder och då särskilt:

* Förenkla och optimera målinriktningsprocesser genom att inkludera data som inte är modellerad i datakartläggningen (skapa nya tabeller: lokalt tillägg till varje arbetsflöde per målgrupp beroende på konfiguration).
* Behålla och överföra buffertberäkningar. Särskilt under faserna då målgrupper konstrueras eller för databasadministration.
* Åtkomst till externa baser (tillval): heterogena databaser som beaktas under målinriktningsprocessen.

[Klicka här för att läsa mer](../../workflow/using/targeting-data.md#data-management) och lära dig om att utforma komplexa mål och arbeta med data som kombinerar arbetsflödesaktiviteter för datahantering.

## Kan jag automatisera utskick av personaliserade meddelanden? {#can-i-automate-personalized-messages-sending-}

Läs om [det här användningsfallet](../../workflow/using/enriching-data.md) för att skicka personaliserade meddelanden till personer beroende på deras högsta poäng i en tävling.

## Hur kan jag dela en målgrupp i delmängder med ett arbetsflöde? {#how-can-i-split-an-audience-in-subsets-with-a-workflow-}

Läs mer om hur man delar upp ett mål i flera undergrupper [i det här avsnittet](../../workflow/using/split.md).

## Hur uppdaterar jag mottagardata från en extern fil? {#how-can-i-update-recipient-data-from-an-external-file-}

Du kan ändra vissa fält i en tabell i Campaign med värden från en extern textfil.

[Klicka här för att läsa mer](../../platform/using/import-operations-samples.md#example--enrich-the-values-with-those-of-an-external-file).

## Hur kan jag identifiera och inrikta mig på nya mottagare? {#how-can-i-identify-and-target-new-recipients-}

[I det här användningsfallet](../../workflow/using/using-aggregates.md) lär du dig hur du använder aggregat för att automatiskt identifiera de senast tillagda mottagarna i databasen och skicka ett välkomstmeddelande till dem.
