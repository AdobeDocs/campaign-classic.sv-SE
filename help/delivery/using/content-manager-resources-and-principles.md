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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 8%

---


# Resurser och principer för Content Manager{#content-manager-resources-and-principles}

Du måste definiera en publikationsmall som innehåller omformningsmallar för varje innehåll.

Ett innehållsblock är strukturerat i ett XML-dokument för datalagring. Ett redigeringsgränssnitt används för att mata in innehåll från Adobe Campaign klientkonsol eller via en webbläsare. Innehållet kan också matas in automatiskt genom att XML-flöde eller data samlas in i en databas.

Genom att kombinera XML-dokumentet med XSL- eller JavaScript-mallarna genereras automatiskt en projektion av publikationsmallen i de olika formaten (HTML, text).

![](assets/d_ncs_content_process.png)

Följande resurser krävs för innehållskonfigurationen:

* Datascheman: beskrivning av XML-innehållsstrukturen. For more on this, refer to [Data schemas](../../delivery/using/data-schemas.md).
* Formulär för datainmatning: konstruktion av datainmatningsskärmar. For more on this, refer to [Input forms](../../delivery/using/input-forms.md).
* Bilder: bilder som används i inmatningsformulär. For more on this, refer to [Image management](../../delivery/using/formatting.md#image-management).
* Formatmallar: formatering av utdatadokument med XSLT-språk. For more on this, refer to [Formatting](../../delivery/using/formatting.md).
* JavaScript-mallar: formatering av utdatadokument med JavaScript. For more on this, refer to [Publication templates](../../delivery/using/publication-templates.md).
* JavaScript-koder: JavaScript-koder för dataaggregering. For more on this, refer to [Aggregator](../../delivery/using/publication-templates.md#aggregator).
* Publikationsmallar: definition av publiceringsmallar. For more on this, refer to [Publication templates](../../delivery/using/publication-templates.md).
* Innehåll: innehållsinstanser som ska skapas och publiceras. Mer information finns i [Använda en innehållsmall](../../delivery/using/using-a-content-template.md).
