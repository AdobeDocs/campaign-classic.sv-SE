---
product: campaign
title: Skapa en leveransmall
description: Skapa en leveransmall
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
exl-id: 40a03e04-56c7-48c0-95b8-aa7bf1121048
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 7%

---

# Skapa en leveransmall{#creating-a-delivery-template}

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#delivery-template-video)

## Konvertera en befintlig leverans till en mall {#converting-an-existing-delivery-to-a-template}

En leverans kan konverteras till en mall för nya upprepade leveransåtgärder. Om du vill konvertera en leverans till en mall väljer du den i leveranslistan, som du kommer åt via noden **[!UICONTROL Campaign management]** i trädet.

Högerklicka och välj **[!UICONTROL Actions > Save as template...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

Den här åtgärden skapar en leveransmall av den valda leveransen. Du måste ange den mapp där den sparas (i fältet **[!UICONTROL Folder]**) samt den mapp där leveranser som skapats baserat på den här mallen skapas (i fältet **[!UICONTROL Execution folder]**).

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

Mer information om konfigurationsläget finns i [Länka mallen till en leverans](../../delivery/using/creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery).

## Skapa en ny mall {#creating-a-new-template}

Så här konfigurerar du en leveransmall:

1. Öppna Campaign Explorer.
1. I mappen **Resources** väljer du **Mallar** och sedan **Leveransmallar**.

   ![](assets/delivery_template_1.png)

1. Klicka på **Nytt** i verktygsfältet för att skapa en ny leveransmall.

   ![](assets/delivery_template_2.png)

1. Ändra **etiketten** och **det interna namnet** för mappen.
1. Spara mallen och öppna den igen.
1. Klicka på knappen **Egenskaper** och ändra sedan värdena enligt dina önskemål.

   ![](assets/delivery_template_3.png)

1. På fliken **Allmänt** bekräftar eller ändrar du de platser som har valts i mappen **Körning**, **Mapp** och **Routning**.

   ![](assets/delivery_template_4.png)

1. Fyll i kategorin **E-postparametrar** med ditt e-postämne och din målgrupp.
1. Lägg till ditt **HTML-innehåll** för att anpassa mallen, så kan du visa en länk för spegelsida och en länk för att avbryta prenumeration.
1. Välj fliken **Förhandsgranska**. I listrutan **Testa anpassning** väljer du **Mottagare** om du vill förhandsgranska mallen som den valda profilen.

   ![](assets/delivery_template_5.png)

1. Klicka på **Spara**. Mallen kan nu användas i en leverans.

>[!NOTE]
>
>För att undvika konfigurationsfel rekommenderar vi att du duplicerar en intern mall och ändrar dess egenskaper i stället för att skapa en ny mall.

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

Ytterligare Campaign Classic-instruktionsvideor finns [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
