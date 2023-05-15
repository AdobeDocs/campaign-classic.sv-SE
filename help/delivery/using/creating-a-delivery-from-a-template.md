---
product: campaign
title: Skapa en leverans från en mall
description: Lär dig hur du skapar en leverans från en mall
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Delivery Templates
exl-id: 7ffb649e-801f-4568-a86b-7982448e3c30
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 7%

---

# Skapa en leverans från en mall{#creating-a-delivery-from-a-template}



## Länka mallen till en leverans {#linking-the-template-to-a-delivery}

Om du vill skapa en leverans baserad på en befintlig mall väljer du mallen i listan med tillgängliga leveransmallar.

![](assets/s_ncs_user_wizard_select_template.png)

I annat fall klickar du på **[!UICONTROL Select link]** till höger om fältet för att bläddra i trädet.

![](assets/s_ncs_user_wizard_choose_link.png)

Välj önskad katalog i dialogrutan **[!UICONTROL Folder]** eller klicka på **[!UICONTROL Display sub-levels]** om du vill visa innehållet i katalogerna i underträden till den aktuella katalogen.

Välj den leveransmall som ska användas och klicka på **[!UICONTROL Ok]**.

## Kör mallen {#executing-the-template}

Du kan starta körningen av en mall direkt från malllistan utan att först skapa en leverans. Om du vill göra det väljer du den mall som ska köras och högerklickar. Välj **[!UICONTROL Actions>Execute the delivery template...]**.

Du kan också använda **[!UICONTROL File>Actions>Execute the delivery template...]**.

![](assets/s_ncs_user_template_execute_menu.png)

Ange leveransparametrarna och klicka på **[!UICONTROL Send]**.

Den här åtgärden genererar en leverans i den mapp som är kopplad till mallen. Namnet på den här leveransen är namnet på leveransmallen som den skapades från.

>[!NOTE]
>
>Mer information om hur du konfigurerar en leverans finns i [Definiera e-postinnehållet](defining-the-email-content.md).
