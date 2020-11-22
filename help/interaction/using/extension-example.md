---
solution: Campaign Classic
product: campaign
title: Exempel på tillägg
description: Exempel på tillägg
audience: interaction
content-type: reference
topic-tags: advanced-parameters
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

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

