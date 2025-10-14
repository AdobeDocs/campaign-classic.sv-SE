---
product: campaign
title: Vanliga frågor och svar om arbetsflöden
description: Vanliga frågor och svar om Campaign Classic
feature: Troubleshooting, Workflows
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 7d1bb3c6-d056-4212-9500-75459a0046fa
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 43%

---

# Vanliga frågor och svar om arbetsflöden {#workflows-faq}



Lär dig att orkestrera processer och uppgifter med arbetsflöden i Adobe Campaign.

## Vilka är de viktigaste stegen för att skapa ett arbetsflöde? {#what-are-the-key-steps-to-create-a-workflow-}

Lär dig hur du skapar ditt första arbetsflöde i [Campaign v8-dokumentationen](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html){target="_blank"}: lär dig koncept och bästa tillvägagångssätt för att skapa arbetsflöden i Campaign.

## Hur importerar jag data i Campaign? {#how-can-i-import-data-in-campaign-}

Lär dig de bästa sätten att importera data i [det här avsnittet](../../platform/using/import-export-best-practices.md).

## Kan jag övervaka arbetsflödeskörningen? {#can-i-monitor-workflow-execution-}

Förstå hur du övervakar körningen av Campaign-arbetsflödet i [Campaign v8-dokumentationen]&#x200B;(https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution)
.html){target="_blank"}.

## Hur uppdaterar jag Campaign-data med ett arbetsflöde? {#how-can-i-update-campaign-data-with-a-workflow-}

Du kan utföra omfattande uppdateringar samt sammanfoga och infoga data i databasen.

Läs mer i [Campaign v8-dokumentationen](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/update-data.html){target="_blank"}.

## Hur kan jag utnyttja datahanteringsfunktionerna? {#how-can-i-leverage-data-management-capabilities-}

I Adobe Campaign kan du dra nytta av en uppsättning aktiviteter för att lösa komplexa problem med målgrupper genom att erbjuda mer effektiva och flexibla verktyg. Datahanteringsaktiviteter låter dig implementera konsekvent hantering av all kommunikation med en kontakt med hjälp av information som är länkad till dennes kontrakt, prenumerationer och reaktivitet på leveranser osv. Datahantering låter dig följa datas livscykeln under segmenteringsåtgärder och då särskilt:

* Förenkla och optimera målinriktningsprocesser genom att inkludera data som inte är modellerad i datakartläggningen (skapa nya tabeller: lokalt tillägg till varje arbetsflöde per målgrupp beroende på konfiguration).
* Behålla och överföra buffertberäkningar. Särskilt under faserna då målgrupper konstrueras eller för databasadministration.
* Åtkomst till externa baser (tillval): heterogena databaser som beaktas under målinriktningsprocessen.

Lär dig hur du utformar komplexa mål och arbetar med data som kombinerar arbetsflödesaktiviteter för datahantering i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html){target="_blank"}.

## Kan jag automatisera utskick av personaliserade meddelanden? {#can-i-automate-personalized-messages-sending-}

Läs [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/enrich-data.html){target="_blank"} om du vill veta hur du skickar personaliserade meddelanden till personer beroende på deras högsta poäng i en tävling.

## Hur kan jag dela en målgrupp i delmängder med ett arbetsflöde? {#how-can-i-split-an-audience-in-subsets-with-a-workflow-}

Lär dig hur du delar upp ett mål i flera deluppsättningar i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html){target="_blank"}.

## Hur uppdaterar jag mottagardata från en extern fil? {#how-can-i-update-recipient-data-from-an-external-file-}

Du kan ändra vissa fält i en tabell i Campaign med värden från en extern textfil.

[Klicka här för att läsa mer](../../platform/using/import-operations-samples.md#example--enrich-the-values-with-those-of-an-external-file).

## Hur kan jag identifiera och inrikta mig på nya mottagare? {#how-can-i-identify-and-target-new-recipients-}

Läs [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/data-management/using-aggregates.html){target="_blank"} om du vill veta hur du använder aggregat för att automatiskt identifiera de senast tillagda mottagarna i databasen och skicka ett välkomstmeddelande till dem.
