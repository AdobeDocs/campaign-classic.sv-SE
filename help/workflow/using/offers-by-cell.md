---
title: Erbjudanden per cell
seo-title: Erbjudanden per cell
description: Erbjudanden per cell
seo-description: null
page-status-flag: never-activated
uuid: 731bfdde-abd2-400e-9e22-3dbaad37c5b9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: d90594bb-e3ba-4fb1-9e11-83d519c1ca7d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Erbjudanden per cell{#offers-by-cell}

Med den här **[!UICONTROL Offers by cell]** aktiviteten kan du distribuera den inkommande populationen (till exempel från en fråga) till flera segment och ange ett erbjudande som ska visas för vart och ett av dessa segment.

Den här aktiviteten kan bara användas med **Interaktion**. Mer information finns i det här [avsnittet](../../interaction/using/about-outbound-channels.md).

Så här gör du:

1. Lägg till **[!UICONTROL Offers by cell]** aktiviteten när du har angett målpopulationen och öppna den.
1. Välj det erbjudandeutrymme som du vill visa erbjudandena på på fliken **[!UICONTROL General]** .
1. På **[!UICONTROL Cells]** fliken anger du de olika deluppsättningarna med **[!UICONTROL Add]** knappen:

   * Ange delmängdsfyllningen med de tillgängliga filtrerings- och begränsningsreglerna.
   * Välj sedan det erbjudande som du vill presentera för undergruppen. De erbjudanden som är tillgängliga är sådana som är berättigade till det erbjudandeutrymme som valdes i föregående steg.

      ![](assets/int_offer_per_cell1.png)

1. Konfigurera sedan en leveransaktivitet som motsvarar den valda kanalen. Se [Flerkanalsleveranser](../../workflow/using/cross-channel-deliveries.md).

