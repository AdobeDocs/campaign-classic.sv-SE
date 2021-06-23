---
product: campaign
title: Resurser och principer för innehållshanteraren
description: Resurser och principer för innehållshanteraren
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 6%

---

# Resurser och principer för innehållshanteraren{#content-manager-resources-and-principles}

Du måste definiera en publikationsmall som innehåller omformningsmallar för varje innehåll.

Ett innehållsblock är strukturerat i ett XML-dokument för datalagring. Ett redigeringsgränssnitt används för att mata in innehåll från Adobe Campaign klientkonsol eller via en webbläsare. Innehållet kan också matas in automatiskt genom att XML-flöde eller data samlas in i en databas.

Genom att kombinera XML-dokumentet med XSL- eller JavaScript-mallarna genereras automatiskt en projektion av publikationsmallen i de olika formaten (HTML, text).

![](assets/d_ncs_content_process.png)

Följande resurser krävs för innehållskonfigurationen:

* Datascheman: beskrivning av XML-innehållsstrukturen. Mer information finns i [Datamodeller](data-schemas.md).
* Formulär för datainmatning: konstruktion av datainmatningsskärmar. Mer information finns i [Inmatningsformulär](input-forms.md).
* Bilder: bilder som används i inmatningsformulär. Mer information finns i [Bildhantering](formatting.md#image-management).
* Formatmallar: formatering av utdatadokument med XSLT-språk. Mer information finns i [Formatering](formatting.md).
* JavaScript-mallar: formatering av utdatadokument med JavaScript. Mer information finns i [Publikationsmallar](publication-templates.md).
* JavaScript-koder: JavaScript-koder för dataaggregering. Mer information finns i [Aggregator](publication-templates.md#aggregator).
* Publikationsmallar: definition av publiceringsmallar. Mer information finns i [Publikationsmallar](publication-templates.md).
* Innehåll: innehållsinstanser som ska skapas och publiceras. Mer information finns i [Använda en innehållsmall](using-a-content-template.md).
