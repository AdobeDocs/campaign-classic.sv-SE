---
product: campaign
title: Designa transaktionsmeddelandemallar
description: Lär dig hur du skapar och utformar en transaktionsmeddelandemall i Adobe Campaign Classic.
feature: Transactional Messaging
exl-id: a52bc140-072e-4f81-b6da-f1b38662bce5
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Designa transaktionsmeddelandemallar {#creating-the-message-template}

![](../../assets/v7-only.svg)

För att vara säker på att varje händelse kan ändras till ett anpassat meddelande måste du skapa en meddelandemall som matchar varje händelsetyp.

>[!IMPORTANT]
>
>Händelsetyper måste skapas i förväg. Mer information finns i [Skapa händelsetyper](../../message-center/using/creating-event-types.md).

Mallar för transaktionsmeddelanden innehåller den information som krävs för att personalisera transaktionsmeddelandet. Du kan också använda mallar för att testa förhandsvisningen av meddelanden och skicka korrektur med dirigerade adresser innan du levererar till det slutliga målet. Mer information finns i [Testa mallar för transaktionsmeddelanden](../../message-center/using/testing-message-templates.md).

## Skapa meddelandemallen {#creating-message-template}

1. Gå till **[!UICONTROL Message Center >Transactional message templates]** i Adobe Campaign-trädet.

1. Högerklicka och välj i listan över transaktionsmeddelandemallar **[!UICONTROL New]** i listrutan eller klicka på **[!UICONTROL New]** ovanför listan med transaktionsmeddelandemallar.

   ![](assets/messagecenter_create_model_001.png)

1. I leveransfönstret väljer du den leveransmall som passar den kanal du vill använda.

   ![](assets/messagecenter_create_model_002.png)

1. Ändra vid behov etiketten.

1. Välj den typ av händelse som matchar meddelandet som du vill skicka.

   ![](assets/messagecenter_create_model_003.png)

   Händelsetyper måste skapas i förväg i konsolen. Mer information finns i [Skapa händelsetyper](../../message-center/using/creating-event-types.md).

   >[!IMPORTANT]
   >
   >En händelsetyp kan inte länkas till mer än en mall.

1. Ange en natur och en beskrivning och klicka sedan på **[!UICONTROL Continue]** för att skapa meddelandetexten (se [Skapa meddelandeinnehållet](#creating-message-content)).

   ![](assets/messagecenter_create_model_004.png)

## Skapa meddelandeinnehållet {#creating-message-content}

Definitionen av transaktionens meddelandeinnehåll är densamma som för vanliga leveranser i Adobe Campaign. För e-postleveranser kan du till exempel skapa innehåll i HTML eller textformat, lägga till bilagor eller anpassa leveransobjektet. Mer information finns i [E-postleverans](../../delivery/using/about-email-channel.md) kapitel.

>[!IMPORTANT]
>
>Bilderna i meddelandet måste vara tillgängliga för alla. Adobe Campaign har ingen mekanism för överföring av bilder för transaktionsmeddelanden.\
>Till skillnad från i JSSP eller webApp, `<%=` har ingen standardescape-konvertering.
>
>I det här fallet måste du undvika alla data som kommer från händelsen på rätt sätt. Detta beror på hur det här fältet används. Använd till exempel encodeURIComponent i en URL. Om du vill visas i HTML kan du använda escapeXMLString.

När du har definierat meddelandeinnehållet kan du integrera händelseinformation i meddelandetexten och anpassa den. Händelseinformation infogas i texten tack vare personaliseringstaggar.

![](assets/messagecenter_create_content_001.png)

* Alla anpassningsfält kommer från nyttolasten.
* Det går att referera till ett eller flera personaliseringsblock i ett transaktionsmeddelande. Blockinnehållet läggs till i leveransinnehållet under publiceringen i körningsinstansen.

Gör så här om du vill infoga personaliseringstaggar i brödtexten i ett e-postmeddelande:

1. Klicka på fliken som matchar e-postformatet (HTML eller text) i meddelandemallen.

1. Ange meddelandets brödtext.

1. Infoga taggen med hjälp av **[!UICONTROL Real time events > Event XML]** -menyn.

   ![](assets/messagecenter_create_custo_002.png)

1. Fyll i taggen med följande syntax: **elementnamn**.@**attributnamn** enligt nedan.

   ![](assets/messagecenter_create_custo_003.png)

1. Spara innehållet.

Meddelandet är nu klart att skickas [testad](../../message-center/using/testing-message-templates.md).
