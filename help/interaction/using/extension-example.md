---
product: campaign
title: Exempel på tillägg
description: Exempel på tillägg
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: 07a5742c6f142c786ad8ba2f8774e7e90e8cd191
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---

# Exempel på tillägg{#extension-example}

![](../../assets/common.svg)

Vid inkommande kontakt (kundtjänst eller webbplats) föreslås de mest relevanta erbjudandena till en viss kontakt med hjälp av en uppsättning regler för behörighet. Om du vill utöka kriterierna för dina erbjudanden kan du utöka **nms:interaktion** schema.

* Om du vill lägga till en ny interaktionskontext utökar du **nms:interaktion** schema och skapa så många **attribute** element efter behov i schemat.

   I följande exempel är de villkor som lagts till landskoden och den senast besökta sidan.

   ![](assets/s_ncs_configuration_offer_schemas.png)

* Du kan sedan använda de attribut som tidigare skapats när du definierar definitionen av kriterierna.

   I följande exempel kan vi skapa behörighetskriterier för att visa ett erbjudande baserat på användarens land eller den senaste webbsidan som de visade.

   ![](assets/s_ncs_configuration_offer_context.png)

* När SOAP-anrop konfigureras infogar du **kontext** XML-element för att referera till kontextinformation som lagts till i interaktionsschemat. Mer information finns i [Integrering via SOAP (serversida)](../../interaction/using/integration-via-soap--server-side-.md).
