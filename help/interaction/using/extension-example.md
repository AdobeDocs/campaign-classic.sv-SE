---
title: Exempel på tillägg
seo-title: Exempel på tillägg
description: Exempel på tillägg
seo-description: null
page-status-flag: never-activated
uuid: 6703b6e8-4eac-4a94-a80a-a7cd71b25cdf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 990b6cbc-9b7b-4278-a635-653d5abafe87
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Exempel på tillägg{#extension-example}

Vid inkommande kontakt (kundtjänst eller webbplats) föreslås de mest relevanta erbjudandena till en viss kontakt med hjälp av en uppsättning regler för behörighet. Utöka **nms:interaction** -schemat om du vill förbättra kriterierna för dina erbjudanden.

* Om du vill lägga till en ny interaktionskontext utökar du schemat **nms:interaction** och skapar så många **attributelement** som behövs i schemat.

   I följande exempel är de villkor som lagts till landskoden och den senast besökta sidan.

   ![](assets/s_ncs_configuration_offer_schemas.png)

* Du kan sedan använda de attribut som tidigare skapats när du definierar definitionen av kriterierna.

   I följande exempel kan vi skapa behörighetskriterier för att visa ett erbjudande baserat på användarens land eller den senaste webbsidan som de visade.

   ![](assets/s_ncs_configuration_offer_context.png)

* När du konfigurerar SOAP-anrop infogar du XML-elementet **context** i den kontextinformation som läggs till i interaktionsschemat. Mer information finns i [Integrering via SOAP (serversidan)](../../interaction/using/integration-via-soap--server-side-.md).

