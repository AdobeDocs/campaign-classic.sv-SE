---
title: Infoga en delad resurs
seo-title: Infoga en delad resurs
description: Infoga en delad resurs
seo-description: null
page-status-flag: never-activated
uuid: ab661bfd-d0a3-4b5c-ba52-4c76c834d584
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: asset-sharing
discoiquuid: 3d01cc7e-5685-4101-bf4b-ef5f6e52b3c9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Infoga en delad resurs{#inserting-a-shared-asset}

Resurser som delas från Adobe Experience Cloud kan användas i e-postmeddelanden och på landningssidor på följande sätt:

1. Skapa ett nytt e-postmeddelande eller en ny landningssida.

   Om du använder resurser från resursbiblioteket i Adobe Experience Manager ska du använda en leveransmall som skapas när du [konfigurerar integreringen](../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets).

   Om du inte har den här specifika mallen kontrollerar du att **fliken**( **[!UICONTROL Content editing mode]** fliken) är inställd på&#x200B;**[!UICONTROL Advanced]** DCE **i leveransegenskaperna** och att det externa AEM-konto som du vill använda för att komma åt ditt AEM Resursbibliotek finns.

1. I redigeringsfönstret väljer du alternativet att lägga till en bild:

   * Om du använder [standardredigeringsläget](../../delivery/using/defining-the-email-content.md#adding-images)väljer du **[!UICONTROL Image]** > **[!UICONTROL Select a shared asset]**.

      ![](assets/dam_insert_image_standard.png)

   * Om du använder det [avancerade redigeringsläget](../../web/using/about-campaign-html-editor.md) (DCE) går du till ett bildblock och väljer sedan **[!UICONTROL Select a shared asset]** via snabbmenyn.

      ![](assets/dam_insert_image_dce.png)

      >[!NOTE]
      >
      >Du kan inte infoga delade bilder från Adobe Campaign i [webbåtkomsten](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) när du använder DCE.

1. Markera en bild i det urvalsfönster som öppnas och bekräfta sedan.

   De tillgängliga bilderna kommer antingen från ditt Adobe Experience Cloud-bibliotek eller från ditt AEM Assets-bibliotek, beroende på hur din Adobe Campaign-instans är konfigurerad. Se avsnittet [Konfigurera åtkomst till resurser](../../integrations/using/configuring-access-to-assets.md) .

   ![](assets/dam_shared_image_selection.png)

>[!NOTE]
>
>Om du använder integreringen med Adobe Target kan du använda en delad bild som standardbild. Se [den här sidan](../../integrations/using/integrating-with-adobe-target.md).

