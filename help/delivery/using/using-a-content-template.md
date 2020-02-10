---
title: Använda en innehållsmall
seo-title: Använda en innehållsmall
description: Använda en innehållsmall
seo-description: null
page-status-flag: never-activated
uuid: 893b9711-593f-4865-b61a-ef0fede9a2b0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: 48f491b7-bf7b-457f-9cf2-db2bbf4eceea
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Använda en innehållsmall{#using-a-content-template}

## Om innehållsmallar {#about-content-templates}

Innehållsmallar kan refereras och användas direkt i leveranser. Se [Skapa en leverans via innehållshantering](#creating-a-delivery-via-content-management)

De kan också användas för att skapa innehållsinstanser. När de har skapats är de här instanserna klara att levereras (se [Leverera en innehållsinstans](#delivering-a-content-instance)) eller exporteras (se [Skapa en innehållsinstans](#creating-a-content-instance)).

## Skapa en leverans via innehållshantering {#creating-a-delivery-via-content-management}

Du kan referera till en innehållsmall i en leverans när du använder inmatningsfält för att ange innehåll. Ytterligare en flik läggs till i leveransguiden för att definiera leveransinnehåll.

![](assets/s_ncs_content_deliver_a_content.png)

Layouten används automatiskt baserat på de valda inställningarna. Om du vill visa den klickar du på **[!UICONTROL HTML preview]** (eller **[!UICONTROL Text preview]** ) och väljer en mottagare som ska testa personaliseringselementen.

![](assets/s_ncs_content_deliver_a_content_html.png)

Mer information finns i det fullständiga implementeringsexemplet: Skapa [innehåll i leveransguiden](../../delivery/using/use-case--creating-content-management.md#creating-content-in-the-delivery-wizard).

## Skapa en innehållsinstans {#creating-a-content-instance}

Du kan skapa innehåll direkt i Adobe Campaign-trädet som ska användas i arbetsflöden, exporteras eller injiceras direkt i nya leveranser.

Använd följande steg:

1. Markera **[!UICONTROL Resources > Contents]** trädets nod, högerklicka och välj **[!UICONTROL Properties]**.

   ![](assets/s_ncs_content_folder_properties.png)

1. Välj de publiceringsmallar som ska vara aktiva för den här mappen.

   ![](assets/s_ncs_content_folder_templates.png)

1. Nu kan du skapa nytt innehåll med knappen **[!UICONTROL New]** ovanför innehållslistan.

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. Ange fälten i formuläret.

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. Klicka sedan på **[!UICONTROL HTML preview]** fliken för att visa återgivningen. Här anges inte de anpassningsfält som hämtats från databasen.

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. När innehållet har skapats läggs det till i listan med tillgängligt innehåll. Klicka på **[!UICONTROL Properties]** länken om du vill ändra dess etikett, status eller visa dess historik.

   ![](assets/s_ncs_content_folder_template_properties.png)

1. När innehållet har godkänts kan det vid behov skapas med lämplig knapp i verktygsfältet.

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >Du kan auktorisera generering av icke godkänt innehåll. Om du vill göra det ändrar du det relevanta alternativet i publiceringsmallen. Mer information finns i [Skapa och konfigurera mallen](../../delivery/using/publication-templates.md#creating-and-configuring-the-template).

   HTML- och textinnehållet genereras som standard i **publiceringsmappen** för Adobe Campaign-instansen. Du kan ändra publikationsmappen tack vare alternativet **NcmPublishingDir** .

## Leverera en innehållsinstans {#delivering-a-content-instance}

Om du vill skapa en innehållsinstans och leverera den måste en leveransmall länkas till den publiceringsmall som används för att generera innehållet. Mer information finns i [Leverans](../../delivery/using/publication-templates.md#delivery).

Dessutom måste innehållslagringsmappen dedikeras till innehåll som hämtas från den här publiceringsmallen (när en innehållsmapp gör att du kan generera flera typer av innehåll kan leveranser inte skapas automatiskt).

Om du vill skapa leveransen automatiskt baserat på det valda innehållet klickar du på **[!UICONTROL Delivery]** ikonen och väljer mallen.

![](assets/s_ncs_content_folder_create_the_delivery.png)

Text- och HTML-innehåll anges automatiskt.
