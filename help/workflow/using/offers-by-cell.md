---
product: campaign
title: Erbjudanden per cell
description: Erbjudanden per cell
feature: Workflows, Targeting Activity, Interaction
exl-id: 72b17b48-093a-4eb9-a848-3c1570e49b61
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 8%

---

# Erbjudanden per cell{#offers-by-cell}



Med aktiviteten **[!UICONTROL Offers by cell]** kan du distribuera den inkommande populationen (från en fråga till exempel) till flera segment och ange ett erbjudande som ska visas för vart och ett av dessa segment.

Den här aktiviteten kan bara användas med **Interaktion**. Mer information finns i det här [avsnittet](../../interaction/using/about-outbound-channels.md).

Så här gör du:

1. Lägg till aktiviteten **[!UICONTROL Offers by cell]** när du har angett målpopulationen och öppna den sedan.
1. På fliken **[!UICONTROL General]** väljer du det erbjudandeutrymme som du vill visa erbjudandena på.
1. På fliken **[!UICONTROL Cells]** anger du de olika delmängderna med knappen **[!UICONTROL Add]**:

   * Ange delmängdsfyllningen med de tillgängliga filtrerings- och begränsningsreglerna.
   * Välj sedan det erbjudande som du vill presentera för undergruppen. De erbjudanden som är tillgängliga är sådana som är berättigade till det erbjudandeutrymme som valdes i föregående steg.

     ![](assets/int_offer_per_cell1.png)

1. Konfigurera sedan en leveransaktivitet som motsvarar den valda kanalen. Se [Flerkanalsleveranser](cross-channel-deliveries.md).
