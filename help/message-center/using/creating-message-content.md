---
solution: Campaign Classic
product: campaign
title: Skapa meddelandeinnehåll
description: Skapa meddelandeinnehåll
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 3%

---


# Skapa meddelandeinnehåll{#creating-message-content}

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
1. Infoga taggen med hjälp av menyerna **[!UICONTROL Real time events>Event XML]** i texten.

   ![](assets/messagecenter_create_custo_002.png)

1. Fyll i taggen med följande syntax: **elementnamn**.@**attributnamn** enligt nedan.

   ![](assets/messagecenter_create_custo_003.png)

