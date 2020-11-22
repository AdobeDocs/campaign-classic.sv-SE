---
solution: Campaign Classic
product: campaign
title: Infoga en delad resurs
description: Infoga en delad resurs
audience: integrations
content-type: reference
topic-tags: asset-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---


# Infoga en delad resurs{#inserting-a-shared-asset}

Resurser som delas från Adobe Experience Cloud kan användas i e-postmeddelanden och på landningssidor enligt följande:

1. Skapa ett nytt e-postmeddelande eller en ny landningssida.

   Om du använder resurser från Adobe Experience Manager resursbibliotek ska du använda en leveransmall som skapas när du [konfigurerar integreringen](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   Om du inte har den här specifika mallen kontrollerar du att **fliken**( **[!UICONTROL Content editing mode]** fliken) är inställd på&#x200B;**[!UICONTROL Advanced]** DCE **i leveransegenskaperna** och att det AEM externa kontot som du vill använda för åtkomst till ditt AEM Assets-resursbibliotek finns.

1. I redigeringsfönstret väljer du alternativet att lägga till en bild:

   * Om du använder [standardredigeringsläget](../../delivery/using/defining-the-email-content.md#adding-images)väljer du **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_standard.png)

   * Om du använder det [avancerade redigeringsläget](../../web/using/about-campaign-html-editor.md) (DCE) går du till ett bildblock och väljer sedan **[!UICONTROL Select a shared asset]** via snabbmenyn.

      ![](assets/dam_insert_image_dce.png)

      >[!NOTE]
      >
      >Du kan inte infoga delade bilder från Adobe Campaign i [webbåtkomst](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) när du använder DCE.

1. Markera en bild i det urvalsfönster som öppnas och bekräfta sedan.

   De tillgängliga bilderna kommer antingen från ditt Adobe Experience Cloud-bibliotek eller ditt AEM Assets-bibliotek, beroende på hur din Adobe Campaign-instans är konfigurerad. Se avsnittet [Konfigurera åtkomst till resurser](../../integrations/using/configuring-access-to-assets.md) .

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Om du använder integreringen med Adobe Target kan du använda en delad bild som standardbild. Se [den här sidan](../../integrations/using/integrating-with-adobe-target.md).

