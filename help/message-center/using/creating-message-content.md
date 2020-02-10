---
title: Skapa meddelandeinnehåll
seo-title: Skapa meddelandeinnehåll
description: Skapa meddelandeinnehåll
seo-description: null
page-status-flag: never-activated
uuid: 4ee013fc-fba2-4120-b796-dd4008000ea9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 1f420652-c9af-4a49-8d5c-a640e960aced
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2c0d4054fbc15a88ea0370269b62c7d647aea033

---


# Skapa meddelandeinnehåll{#creating-message-content}

Definitionen av transaktionens meddelandeinnehåll är densamma som för vanliga leveranser i Adobe Campaign. För e-postleveranser kan du till exempel skapa innehåll i HTML- eller textformat, lägga till bilagor eller anpassa leveransobjektet. Mer information finns i kapitlet om [e-postleverans](../../delivery/using/about-email-channel.md).

>[!CAUTION]
>
>Bilderna i meddelandet måste vara tillgängliga för alla. Adobe Campaign innehåller ingen mekanism för överföring av bilder för transaktionsmeddelanden.\
>Till skillnad från i JSSP och webApp `<%=` finns ingen standardflytning.
>
>I det här fallet måste du undvika alla data som kommer från händelsen på rätt sätt. Den här inställningen beror på hur fältet används. Använd till exempel encodeURIComponent i en URL. Om du vill visas i HTML-koden kan du använda escapeXMLString.

När du har definierat meddelandeinnehållet kan du integrera händelseinformation i meddelandetexten och anpassa den. Händelseinformation infogas i texten tack vare personaliseringstaggar.

![](assets/messagecenter_create_content_001.png)

* Alla anpassningsfält kommer från nyttolasten.
* Det går att referera till ett eller flera personaliseringsblock i ett transaktionsmeddelande. Blockinnehållet läggs till i leveransinnehållet under publiceringen i körningsinstansen.

Gör så här om du vill infoga personaliseringstaggar i brödtexten i ett e-postmeddelande:

1. Klicka på fliken som matchar e-postformatet (HTML eller text) i meddelandemallen.
1. Ange meddelandets brödtext.
1. Infoga taggen med hjälp av **[!UICONTROL Real time events>Event XML]** menyerna i texten.

   ![](assets/messagecenter_create_custo_002.png)

1. Fyll i taggen med följande syntax: **elementnamn**.@**attributnamn** enligt nedan.

   ![](assets/messagecenter_create_custo_003.png)

