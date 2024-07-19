---
product: campaign
title: Exempel på tillägg
description: Exempel på tillägg
feature: Interaction, Offers
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---

# Exempel på tillägg{#extension-example}



Vid inkommande kontakt (kundtjänst eller webbplats) föreslås de mest relevanta erbjudandena till en viss kontakt med hjälp av en uppsättning regler för behörighet. Utöka schemat **nms:interaction** om du vill förbättra kriterierna för dina erbjudanden.

* Om du vill lägga till en ny interaktionskontext utökar du schemat **nms:interaction** och skapar så många **attribute** -element som behövs i schemat.

  I följande exempel är de villkor som lagts till landskoden och den senast besökta sidan.

  ![](assets/s_ncs_configuration_offer_schemas.png)

* Du kan sedan använda de attribut som tidigare skapats när du definierar definitionen av kvalificeringskriterier.

  I följande exempel kan vi skapa behörighetskriterier för att visa ett erbjudande baserat på användarens land eller den senaste webbsidan som de visade.

  ![](assets/s_ncs_configuration_offer_context.png)

* När du konfigurerar SOAP anrop infogar du XML-elementet **context** i den referenskontextinformation som lagts till i interaktionsschemat. Mer information finns i [Integrering via SOAP (serversidan)](../../interaction/using/integration-via-soap-server-side.md).
