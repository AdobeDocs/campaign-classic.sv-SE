---
product: campaign
title: Arbeta med Adobe Campaign och Adobe Target
description: Lär dig integrera Adobe Campaign med Adobe Target
feature: Target Integration
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Arbeta med Campaign och Target{#integrating-with-adobe-target}



Använd Adobe Campaign med Adobe Target för att optimera e-postinnehåll.

Om du vill optimera ditt e-postinnehåll kan du skapa ett omdirigeringserbjudande i Adobe Target och sedan använda Adobe Campaign för att hantera e-posterbjudandena. Du kan t.ex. visa olika erbjudanden för män och kvinnor.

Integrationen äger rum när e-postmeddelandet öppnas. När kunden öppnar e-postmeddelandet anropas Target och en dynamisk version av innehållet visas. Innehållet består av en statisk bild som stöds av alla webbläsare. Target spårar reaktionen på erbjudandet på målgrupps- eller sessionsnivå och att data finns tillgängliga i Target-rapporter. [Läs mer i Adobe Target-dokumentationen](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html?lang=sv-SE).


>[!NOTE]
>
>Integreringen stöder bara statiska bilder. Resten av innehållet kan inte anpassas.

Adobe Target kan använda flera typer av data:

* Data från Adobe Campaign datamart
* Segment som är länkade till besökar-ID i Adobe Target, om de data som används inte omfattas av juridiska begränsningar
* Adobe Target data: användaragent, IP-adress, geopositioneringsdata
