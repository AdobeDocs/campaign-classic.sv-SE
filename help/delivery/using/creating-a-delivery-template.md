---
title: Skapa en leveransmall
seo-title: Skapa en leveransmall
description: Skapa en leveransmall
seo-description: null
page-status-flag: never-activated
uuid: 8ceae1ec-9e02-4809-aa8b-1e6bd7790950
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: 0e67d9dd-3ee8-4c06-98a4-3a2c644b6c0a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# Skapa en leveransmall{#creating-a-delivery-template}

## Konvertera en befintlig leverans till en mall {#converting-an-existing-delivery-to-a-template}

En leverans kan konverteras till en mall för nya upprepade leveransåtgärder. Om du vill konvertera en leverans till en mall väljer du den i leveranslistan, som du når via trädets **[!UICONTROL Campaign management]** nod.

Högerklicka och välj **[!UICONTROL Actions > Save as template...]**.

![](assets/s_ncs_user_campaign_save_as_scenario.png)

Den här åtgärden skapar en leveransmall av den valda leveransen. Du måste ange den mapp där den sparas (i **[!UICONTROL Folder]** fältet) samt den mapp där leveranser som skapats baserat på den här mallen skapas (i **[!UICONTROL Execution folder]** fältet).

![](assets/s_ncs_user_campaign_save_as_scenario_a.png)

Mer information om konfigurationsläget finns i [Länka mallen till en leverans](../../delivery/using/creating-a-delivery-from-a-template.md#linking-the-template-to-a-delivery).

## Skapa en ny mall {#creating-a-new-template}

Så här konfigurerar du en leveransmall:

1. Öppna Campaign Explorer.
1. I mappen **Resources** väljer du **Templates** och sedan **Delivery templates**.

   ![](assets/delivery_template_1.png)

1. Klicka på **Nytt** i verktygsfältet för att skapa en ny leveransmall.

   ![](assets/delivery_template_2.png)

1. Ändra mappens **etikett** och **interna namn** .
1. Spara mallen och öppna den igen.
1. Klicka på knappen **Egenskaper** och ändra sedan värdena enligt dina önskemål.

   ![](assets/delivery_template_3.png)

1. På fliken **Allmänt** bekräftar eller ändrar du de platser som är markerade i listrutorna **Körningsmapp**, **Mapp** och **Routning** .

   ![](assets/delivery_template_4.png)

1. Fyll i kategorin **E-postparametrar** med ditt e-postämne och din målgrupp.
1. Om du lägger till ditt **HTML-innehåll** för att anpassa mallen kan du visa en länk för spegelsida och en länk för att avbryta prenumerationen.
1. Välj fliken **Förhandsgranska** . I listrutan **Testa personalisering** väljer du **Mottagare** för att förhandsgranska mallen som vald profil.

   ![](assets/delivery_template_5.png)

1. Klicka på **Spara**. Mallen kan nu användas i en leverans.

>[!NOTE]
>
>För att undvika konfigurationsfel rekommenderar vi att du duplicerar en intern mall och ändrar dess egenskaper i stället för att skapa en ny mall.
