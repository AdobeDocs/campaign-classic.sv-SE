---
product: campaign
title: Resurser och principer för innehållshanteraren
description: Resurser och principer för Content Manager
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Templates
role: User, Developer, Data Engineer
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 4%

---

# Resurser och principer för innehållshanteraren{#content-manager-resources-and-principles}


Du måste definiera en publikationsmall som innehåller omformningsmallar för varje innehåll.

Ett innehållsblock är strukturerat i ett XML-dokument för datalagring. Ett redigeringsgränssnitt används för att mata in innehåll från Adobe Campaign klientkonsol eller via en webbläsare. Innehållet kan också matas in automatiskt genom att XML-flöde eller data samlas in i en databas.

Genom att kombinera XML-dokumentet med XSL- eller JavaScript-mallarna genereras automatiskt en projektion av publikationsmallen i de olika formaten (HTML, text).

![](assets/d_ncs_content_process.png)

Följande resurser krävs för innehållskonfigurationen:

* Datamodeller: beskrivning av XML-innehållsstrukturen. Mer information finns i [Datamodeller](data-schemas.md).
* Datainmatningsformulär: konstruktion av datainmatningsskärmar. Mer information finns i [Indataformulär](input-forms.md).
* Bilder: bilder som används i inmatningsformulär. Mer information finns i [Bildhantering](formatting.md#image-management).
* Formatmallar: formatera utdatadokument med XSLT-språk. Mer information finns i [Formatering](formatting.md).
* JavaScript-mallar: formatera utdatadokument med JavaScript. Mer information finns i [Publikationsmallar](publication-templates.md).
* JavaScript-koder: JavaScript-koder för datainsamling. Mer information finns i [Aggregator](publication-templates.md#aggregator).
* Publikationsmallar: definition av publiceringsmallar. Mer information finns i [Publikationsmallar](publication-templates.md).
* Innehåll: innehållsinstanser som ska skapas och publiceras. Mer information finns i [Använda en innehållsmall](using-a-content-template.md).
