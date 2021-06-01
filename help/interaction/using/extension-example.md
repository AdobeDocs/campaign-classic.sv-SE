---
product: campaign
title: Exempel på tillägg
description: Exempel på tillägg
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: d4acf99b-cef4-48f7-b4cd-c032ec12592f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---

# Exempel på tillägg{#extension-example}

Vid inkommande kontakt (kundtjänst eller webbplats) föreslås de mest relevanta erbjudandena till en viss kontakt med hjälp av en uppsättning regler för behörighet. Om du vill utöka behörighetskriterierna för dina erbjudanden ska du utöka schemat **nms:interaction**.

* Om du vill lägga till en ny interaktionskontext utökar du schemat **nms:interaction** och skapar så många **attribute**-element som behövs i schemat.

   I följande exempel är de villkor som lagts till landskoden och den senast besökta sidan.

   ![](assets/s_ncs_configuration_offer_schemas.png)

* Du kan sedan använda de attribut som tidigare skapats när du definierar definitionen av kriterierna.

   I följande exempel kan vi skapa behörighetskriterier för att visa ett erbjudande baserat på användarens land eller den senaste webbsidan som de visade.

   ![](assets/s_ncs_configuration_offer_context.png)

* När du konfigurerar SOAP-anrop infogar du XML-elementet **context** för att referera till kontextinformation som lagts till i interaktionsschemat. Mer information finns i [Integrering via SOAP (serversidan)](../../interaction/using/integration-via-soap--server-side-.md).
