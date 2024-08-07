---
product: campaign
title: Importera och exportera data med arbetsflöden
description: Lär dig hur du importerar och exporterar data med arbetsflöden i Campaign
feature: Data Management, Workflows
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 266ecd49-7101-4ff1-941f-1f9b39b44955
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 2%

---

# Importera och exportera data med arbetsflöden {#import-export-workflows}



## Samla in data {#collecting-data-workflows}

Arbetsflöden kan vara ett användbart sätt att automatisera vissa importprocesser. Oavsett om du importerar data från en lokal fil eller från en SFTP kan du använda arbetsflöden för att standardisera datahanteringsprocesserna.

### Använd data från en lista: Läslista {#using-data-from-a-list--read-list}

Data som skickas i ett arbetsflöde kan komma från listor där data har förberetts och strukturerats.

Den här listan kan ha skapats direkt i Adobe Campaign eller importerats med alternativet **[!UICONTROL Import a list]**. Mer information om det här alternativet finns på [sidan](../../platform/using/about-generic-imports-exports.md).

Mer information om hur du använder läslisteaktiviteten i ett arbetsflöde finns på [den här sidan](../../workflow/using/read-list.md).

### Läsa in data från en fil {#loading-data-from-a-file}

De data som bearbetas i ett arbetsflöde kan extraheras från en strukturerad fil så att de kan importeras till Adobe Campaign.

En beskrivning av dataaktiviteten som läses in finns i avsnittet [Datainläsning (fil)](../../workflow/using/data-loading-file.md).

Exempel på strukturerad fil som ska importeras:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

När data har samlats in kan du använda dem i dina arbetsflöden, till exempel för att förbättra en leverans eller uppdatera databasen. Mer information finns på [den här sidan](../../workflow/using/how-to-use-workflow-data.md).

## Exportera data {#exporting-data-via-a-workflow}

Arbetsflöden kan vara ett användbart sätt att automatisera vissa av dina exportprocesser eller exportera exakta datauppsättningar efter att ha använt några av de tillgängliga datahanteringsaktiviteterna för att omvandla dina data.

Exportåtgärder utförs med en **[!UICONTROL Data extraction (file) activity]**. Mer information om hur du konfigurerar och använder aktiviteten finns på [den här sidan](../../workflow/using/extraction-file.md).
