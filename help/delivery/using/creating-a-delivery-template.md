---
product: campaign
title: Skapa en leveransmall
description: Skapa en leveransmall
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Delivery Templates
exl-id: 40a03e04-56c7-48c0-95b8-aa7bf1121048
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 11%

---

# Skapa en leveransmall{#creating-a-delivery-template}



![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#delivery-template-video)

## Konvertera en befintlig leverans till en mall {#converting-an-existing-delivery-to-a-template}

En leverans kan konverteras till en mall för nya upprepade leveransåtgärder. Om du vill konvertera en leverans till en mall väljer du den i leveranslistan som du når via **[!UICONTROL Campaign management]** trädnod.

Högerklicka och välj **[!UICONTROL Actions > Save as template...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

Den här åtgärden skapar en leveransmall av den valda leveransen. Du måste ange mappen där den sparas (i **[!UICONTROL Folder]** fält) samt den mapp där leveranser som skapats baserat på den här mallen skapas (i **[!UICONTROL Execution folder]** fält).

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

Mer information om konfigurationsläget finns i [Länka mallen till en leverans](creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery).

## Skapa en ny mall {#creating-a-new-template}

>[!NOTE]
>
>För att undvika konfigurationsfel rekommenderar Adobe att du duplicerar en ursprunglig mall och anpassar inställningarna i stället för att skapa en ny mall.

Så här konfigurerar du en leveransmall:

1. Öppna Campaign Explorer.
1. I **Resurser** mapp, markera **Mallar** sedan **Leveransmallar**.

   ![](assets/delivery_template_1.png)

1. Klicka **Nytt** i verktygsfältet för att skapa en ny leveransmall, eller **Duplicera** en befintlig mall.

   ![](assets/delivery_template_2.png)

1. Ändra **Etikett** och **Internt namn** i mappen.
1. Spara mallen och öppna den igen.
1. Klicka på **Egenskaper** och sedan ändra värdena enligt dina önskemål.

   ![](assets/delivery_template_3.png)

1. I **Allmänt** kan du bekräfta eller ändra de platser som du har valt på fliken **Körningsmapp**, **Mapp** och **Routning** nedrullningsbara menyer.

   ![](assets/delivery_template_4.png)

1. Slutför **E-postparametrar** -kategori med ditt e-postämne och din målgrupp.
1. Lägg till **HTML content** om du vill anpassa mallen kan du visa en länk för spegelsida och en länk för att avbryta prenumerationen.
1. Välj **Förhandsgranska** -fliken. I **Testa personalisering** nedrullningsbar meny, välja **Mottagare** om du vill förhandsgranska mallen som den valda profilen.

   ![](assets/delivery_template_5.png)

1. Klicka **Spara**. Mallen kan nu användas i en leverans.


## Självstudievideor {#delivery-template-video}

### Konfigurera en leveransmall

I följande video visas hur du konfigurerar en mall för en ad hoc-leverans.

>[!VIDEO](https://video.tv.adobe.com/v/24066?quality=12)

### Så här ställer du in egenskaper för leveransmallar

I följande video visas hur du ställer in leveransmallsegenskaperna och förklarar varje egenskap i detalj.

>[!VIDEO](https://video.tv.adobe.com/v/24067?quality=12)

### Distribuera en ad hoc-leveransmall

I den här videon förklaras hur du distribuerar en mall för ad hoc-e-postleverans och den förklarar skillnaden mellan en e-postleverans och ett leveransarbetsflöde.

>[!VIDEO](https://video.tv.adobe.com/v/24065?quality=12)

Det finns fler instruktionsvideor för Campaign Classic [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
