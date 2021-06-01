---
product: campaign
title: Designa transaktionsmeddelandemallar
description: Lär dig hur du skapar och utformar en transaktionsmeddelandemall i Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: a52bc140-072e-4f81-b6da-f1b38662bce5
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Designa transaktionsmeddelandemallar {#creating-the-message-template}

För att vara säker på att varje händelse kan ändras till ett anpassat meddelande måste du skapa en meddelandemall som matchar varje händelsetyp.

>[!IMPORTANT]
>
>Händelsetyper måste skapas i förväg. Mer information finns i [Skapa händelsetyper](../../message-center/using/creating-event-types.md).

Mallar för transaktionsmeddelanden innehåller den information som krävs för att personalisera transaktionsmeddelandet. Du kan också använda mallar för att testa förhandsvisningen av meddelanden och skicka korrektur med dirigerade adresser innan du levererar till det slutliga målet. Mer information finns i [Testa transaktionsmeddelandemallar](../../message-center/using/testing-message-templates.md).

## Skapa meddelandemallen {#creating-message-template}

1. Gå till mappen **[!UICONTROL Message Center >Transactional message templates]** i Adobe Campaign-trädet.

1. Högerklicka och välj **[!UICONTROL New]** i listrutan i listan över transaktionsmeddelandemallar eller klicka på knappen **[!UICONTROL New]** ovanför listan med transaktionsmeddelandemallar.

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

Definitionen av transaktionens meddelandeinnehåll är densamma som för vanliga leveranser i Adobe Campaign. För e-postleveranser kan du till exempel skapa innehåll i HTML- eller textformat, lägga till bilagor eller anpassa leveransobjektet. Mer information finns i kapitlet [E-postleverans](../../delivery/using/about-email-channel.md).

>[!IMPORTANT]
>
>Bilderna i meddelandet måste vara tillgängliga för alla. Adobe Campaign har ingen mekanism för överföring av bilder för transaktionsmeddelanden.\
>Till skillnad från i JSSP och webApp har `<%=` ingen standardflytning.
>
>I det här fallet måste du undvika alla data som kommer från händelsen på rätt sätt. Detta beror på hur det här fältet används. Använd till exempel encodeURIComponent i en URL. Om du vill visas i HTML-koden kan du använda escapeXMLString.

När du har definierat meddelandeinnehållet kan du integrera händelseinformation i meddelandetexten och anpassa den. Händelseinformation infogas i texten tack vare personaliseringstaggar.

![](assets/messagecenter_create_content_001.png)

* Alla anpassningsfält kommer från nyttolasten.
* Det går att referera till ett eller flera personaliseringsblock i ett transaktionsmeddelande. Blockinnehållet läggs till i leveransinnehållet under publiceringen i körningsinstansen.

Gör så här om du vill infoga personaliseringstaggar i brödtexten i ett e-postmeddelande:

1. Klicka på fliken som matchar e-postformatet (HTML eller text) i meddelandemallen.

1. Ange meddelandets brödtext.

1. Infoga taggen med hjälp av menyn **[!UICONTROL Real time events > Event XML]** i texten.

   ![](assets/messagecenter_create_custo_002.png)

1. Fyll i taggen med följande syntax: **elementnamn**.@**attributnamn** enligt nedan.

   ![](assets/messagecenter_create_custo_003.png)

1. Spara innehållet.

Meddelandet är nu klart att [testas](../../message-center/using/testing-message-templates.md).
