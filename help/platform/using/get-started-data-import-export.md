---
product: campaign
title: Kom igång med dataimport och export
description: Läs mer om import och export av data i Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d6055d97-75fc-4ed7-89bd-8336157454eb
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 11%

---

# Kom igång med dataimport och export {#get-started-data-import-export}

![](../../assets/common.svg)

Adobe Campaign Classic har funktioner för datahantering som gör att du kan importera och exportera data. Dessa åtgärder kan utföras med antingen arbetsflöden eller generiska import- och exporteringar.

>[!IMPORTANT]
>
>Tänk på att SFTP-lagring, databaslagring och aktiva profiler begränsas enligt ditt Adobe Campaign-avtal när du använder den här funktionen.

## Arbetsflöden {#workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**** Arbetsflöden är ett användbart sätt att automatisera importprocesserna. Oavsett om du importerar data från en lokal fil eller från en SFTP kan du använda dem för att standardisera datahanteringsrutinerna.

I arbetsflöden kan import- och exportåtgärder upprepas automatiskt enligt ett schema, t.ex. för att automatisera datautbyte mellan flera informationssystem.

Mer information om detta finns i [det här avsnittet](../../platform/using/import-export-workflows.md).

## Allmän import och export {#generic-import-export}

<img src="assets/do-not-localize/icon_templates.svg" width="60px">

Dessutom innehåller Campaign Classic **generiska importer och exporter** som gör att du kan skapa tillfälliga import- eller exportjobb.

Import och export konfigureras i dedikerade mallar som du kan konfigurera och använda för att starta och övervaka import- och exportjobb.

Mer information om generisk import och export finns i [det här avsnittet](../../platform/using/about-generic-imports-exports.md).

>[!IMPORTANT]
>Allmän import och export bör endast användas vid enstaka tillfällen. För att säkerställa att alla data är enhetliga och effektiviserar rekommenderar vi att du utför import- och exportåtgärder via arbetsflöden.

## Datakryptering och komprimering {#data-encryption-compression}

<img src="assets/do-not-localize/icon_encrypt.svg" width="60px">

I Campaign Classic kan du importera komprimerade eller krypterade filer och exportera komprimerade eller krypterade filer.

Dessa åtgärder utförs i arbetsflöden genom att förbearbetningssteg tillämpas på de data som du vill utnyttja.

Mer information om detta hittar du i dessa avsnitt.

* [Zippa upp eller dekryptera en fil](../../platform/using/unzip-decrypt.md)
* [Zippa eller kryptera en fil](../../platform/using/zip-encrypt.md)

## Bästa praxis och felsökning {#best-practices-troubleshooting}

<img src="assets/do-not-localize/icon_bestpractices.svg" width="60px">

Du bör följa flera [metodtips](../../platform/using/import-export-best-practices.md) när du utför import- och exportåtgärder för att säkerställa att data är konsekventa i databasen och undvika vanliga fel vid uppdatering och export.

Dessutom finns rekommendationer och vanliga problem med användningen av SFTP-servrar i [det här avsnittet](../../platform/using/sftp-server-usage.md).
