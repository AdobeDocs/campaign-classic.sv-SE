---
title: Resurser och principer för Content Manager
seo-title: Resurser och principer för Content Manager
description: Resurser och principer för Content Manager
seo-description: null
page-status-flag: never-activated
uuid: 3560e392-129a-471d-a211-05481cdda224
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: b22b3abb-6fe5-4f4d-93fc-0d00d426edb6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Resurser och principer för Content Manager{#content-manager-resources-and-principles}

Du måste definiera en publikationsmall som innehåller omformningsmallar för varje innehåll.

Ett innehållsblock är strukturerat i ett XML-dokument för datalagring. Ett redigeringsgränssnitt används för att mata in innehållet från Adobe Campaign-klientkonsolen eller via en webbläsare. Innehållet kan också matas in automatiskt genom att XML-flöde eller data samlas in i en databas.

Genom att kombinera XML-dokumentet med XSL- eller JavaScript-mallarna genereras automatiskt en projektion av publikationsmallen i de olika formaten (HTML, text).

![](assets/d_ncs_content_process.png)

Följande resurser krävs för innehållskonfigurationen:

* Datascheman: beskrivning av XML-innehållsstrukturen. Mer information finns i [Datascheman](../../delivery/using/data-schemas.md).
* Formulär för datainmatning: konstruktion av datainmatningsskärmar. Mer information finns i [Inmatningsformulär](../../delivery/using/input-forms.md).
* Bilder: bilder som används i inmatningsformulär. Mer information finns i [Bildhantering](../../delivery/using/formatting.md#image-management).
* Formatmallar: formatering av utdatadokument med XSLT-språk. Mer information finns i [Formatering](../../delivery/using/formatting.md).
* JavaScript-mallar: formatering av utdatadokument med JavaScript. Mer information finns i [Publikationsmallar](../../delivery/using/publication-templates.md).
* JavaScript-koder: JavaScript-koder för dataaggregering. Mer information finns i [Aggregator](../../delivery/using/publication-templates.md#aggregator).
* Publikationsmallar: definition av publiceringsmallar. Mer information finns i [Publikationsmallar](../../delivery/using/publication-templates.md).
* Innehåll: innehållsinstanser som ska skapas och publiceras. Mer information finns i [Använda en innehållsmall](../../delivery/using/using-a-content-template.md).
