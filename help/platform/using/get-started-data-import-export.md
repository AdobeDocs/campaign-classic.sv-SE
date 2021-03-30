---
solution: Campaign Classic
product: campaign
title: Kom igång med import och export av data
description: Läs mer om import och export av data i Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 12%

---


# Kom igång med import och export av data {#get-started-data-import-export}

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

Flera [metodtips](../../platform/using/import-export-best-practices.md) bör följas vid import- och exportåtgärder för att säkerställa att data är konsekventa i databasen och undvika vanliga fel under uppdatering och export.

Dessutom finns rekommendationer och vanliga problem med användningen av SFTP-servrar i [det här avsnittet](../../platform/using/sftp-server-usage.md).
