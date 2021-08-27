---
product: campaign
title: Bästa praxis för import och export
description: Läs mer om de bästa sätten att följa när du importerar eller exporterar data.
audience: automating
content-type: reference
topic-tags: workflow-general-operation
exl-id: 03d35202-d221-4136-aad4-00704aabb356
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 2%

---

# Bästa praxis för import och export {#import-export-best-practices}

![](../../assets/common.svg)

Genom att vara försiktig och följa de få enkla regler som beskrivs nedan kan du till stor del säkerställa att data är konsekventa i databasen och undvika vanliga fel under databasuppdatering eller dataexport.

## Använda arbetsflödesmallar {#using-import-templates}

De flesta arbetsflöden som används för att importera data bör innehålla följande aktiviteter: **[!UICONTROL Load file]**, **[!UICONTROL Reconciliation]**, **[!UICONTROL Segmentation]**, **[!UICONTROL Deduplication]**, **[!UICONTROL Update data]**.

Med hjälp av arbetsflödesmallar är det mycket bekvämt att förbereda liknande importer och säkerställa att data är konsekventa i databasen.

I många projekt skapas importer utan **[!UICONTROL Deduplication]**-aktivitet eftersom filerna som används i projektet inte har några dubbletter. Det kan ibland visas dubbletter när du importerar olika filer. Det är då svårt att deduplicera. Därför är ett borttagningssteg en bra försiktighetsåtgärd i alla importarbetsflöden.

Du kan inte utgå från att inkommande data är konsekventa och korrekta eller att IT-avdelningen eller Adobe Campaign-administratören kommer att ta hand om dem. Under projektet bör du tänka på datarensningen. Ta bort dubbletter, stämma av och bibehåll enhetligheten när du importerar data.

Ett exempel på en allmän arbetsflödesmall som utformats för import av data finns i [Exempel: Arbetsflödesmall för import av dataavsnitt](../../platform/using/creating-import-export-templates.md).

## Använd platta filformat {#using-flat-file-formats}

Det mest effektiva formatet för import är platta filer. Platta filer kan importeras i gruppläge på databasnivå.

Exempel:

* Avgränsare: tabb eller semikolon
* Första raden med rubriker
* Ingen strängavgränsare
* Datumformat: ÅÅÅ/MM/DD HH:mm:SS

Exempel på fil som ska importeras:

```
lastname;firstname;birthdate;email;crmID
Smith;Hayden;23/05/1989;hayden.smith@example.com;124365
Mars;Daniel;17/11/1987;dannymars@example.com;123545
Smith;Clara;08/02/1989;hayden.smith@example.com;124567
Durance;Allison;15/12/1978;allison.durance@example.com;120987
```

## Använd komprimering {#using-compression}

Använd zippade filer för import och export när det är möjligt. GZIP stöds som standard. Du kan lägga till förbearbetning när du importerar filer eller efterbearbetning när du extraherar data i arbetsflödesaktiviteterna **[!UICONTROL Load file]** och **[!UICONTROL Extract file]**.

**Relaterade ämnen:**

* [Aktivitet för inläsning av data (fil)](../../workflow/using/data-loading--file-.md)
* [Aktivitet för dataextrahering (fil)](../../workflow/using/extraction--file-.md)

## Importera i Delta-läge {#importing-in-delta-mode}

Vanlig import måste ske i deltaläge. Det innebär att endast ändrade eller nya data skickas till Adobe Campaign, i stället för hela tabellen varje gång.

Full import bör endast användas för inledande last.

## Bibehåll konsekvens {#maintaining-consistency}

Följ nedanstående principer för att upprätthålla datakonsekvensen i Adobe Campaign-databasen:

* Om de importerade data matchar en referenstabell i Adobe Campaign bör den stämma av med den tabellen i arbetsflödet. Poster som inte matchar bör avvisas.
* Se till att importerade data alltid är **&quot;normaliserade&quot;** (e-post, telefonnummer, e-postadress) och att normaliseringen är tillförlitlig och inte ändras under årens lopp. Om så inte är fallet kommer vissa dubbletter sannolikt att visas i databasen, och eftersom Adobe Campaign inte har verktyg för&quot;otydlig&quot; matchning är det mycket svårt att hantera och ta bort dem.
* Transaktionsdata ska ha en avstämningsnyckel och stämma av med befintliga data för att undvika att skapa dubbletter.
* **Importera relaterade filer i rätt ordning**. Om importen består av flera filer som är beroende av varandra, bör arbetsflödet se till att filerna importeras i rätt ordning. När en fil misslyckas importeras inte de andra filerna.
* **Ta bort dubbletter**, stämma av och bibehåll konsekvens när du importerar data.
