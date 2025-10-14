---
product: campaign
title: Infoga en delad resurs
description: Infoga en delad resurs
feature: Asset Sharing
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: 30a94bce-6d96-4a6d-a62f-7451c822f0e3
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 1%

---

# Infoga en delad resurs{#inserting-a-shared-asset}

Assets som delas från Adobe Experience Cloud kan användas i e-postmeddelanden och på landningssidor enligt följande:

1. Skapa ett nytt e-postmeddelande eller en ny landningssida.

   Om du använder resurser från Adobe Experience Manager resursbibliotek ska du använda en leveransmall som skapas när [integreringen ](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets) konfigureras.

   Om du inte har den här specifika mallen kontrollerar du att **Egenskaper** för leveransen är inställd på **[!UICONTROL Content editing mode]** DCE **[!UICONTROL Advanced]** på fliken **(**) och att det externa AEM-konto som du vill använda för åtkomst till ditt AEM Assets-resursbibliotek finns.

1. I redigeringsfönstret väljer du alternativet att lägga till en bild:

   * Om du använder [standardredigeringsläget](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html#adding-images){target="_blank"} väljer du **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

     ![](assets/dam_insert_image_standard.png)

   * Om du använder [avancerat redigeringsläge](../../web/using/about-campaign-html-editor.md) (DCE) går du till ett bildblock och väljer **[!UICONTROL Select a shared asset]** via snabbmenyn.

     ![](assets/dam_insert_image_dce.png)

     >[!NOTE]
     >
     >Du kan inte infoga delade bilder från Adobe Campaign i [webbåtkomsten](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) när du använder DCE.

1. Markera en bild i det urvalsfönster som öppnas och bekräfta sedan.

   De tillgängliga bilderna kommer antingen från ditt Adobe Experience Cloud-bibliotek eller ditt AEM Assets-bibliotek, beroende på hur din Adobe Campaign-instans är konfigurerad. Se avsnittet [Konfigurera åtkomst till Assets](../../integrations/using/configuring-access-to-assets.md).

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Om du använder integreringen med Adobe Target kan du använda en delad bild som standardbild. Se [den här sidan](../../integrations/using/integrating-with-adobe-target.md).
