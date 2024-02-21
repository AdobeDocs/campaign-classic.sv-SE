---
product: campaign
title: Exempel på tillägg
description: Exempel på tillägg
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 4%

---

# Exempel på tillägg{#extension-example}



Vid inkommande kontakt (kundtjänst eller webbplats) föreslås de mest relevanta erbjudandena till en viss kontakt med hjälp av en uppsättning regler för behörighet. Om du vill utöka kriterierna för dina erbjudanden kan du utöka **nms:interaktion** schema.

* Utöka **nms:interaktion** schema och skapa så många **attribute** element efter behov i schemat.

  I följande exempel är de villkor som lagts till landskoden och den senast besökta sidan.

  ![](assets/s_ncs_configuration_offer_schemas.png)

* Du kan sedan använda de attribut som tidigare skapats när du definierar definitionen av kvalificeringskriterier.

  I följande exempel kan vi skapa behörighetskriterier för att visa ett erbjudande baserat på användarens land eller den senaste webbsidan som de visade.

  ![](assets/s_ncs_configuration_offer_context.png)

* När SOAP-anrop konfigureras infogar du **kontext** XML-element för att referera till kontextinformation som lagts till i interaktionsschemat. Mer information finns i [Integrering via SOAP (serversida)](../../interaction/using/integration-via-soap-server-side.md).
