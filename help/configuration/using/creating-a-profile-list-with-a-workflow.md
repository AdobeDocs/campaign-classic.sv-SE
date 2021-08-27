---
product: campaign
title: Skapa en profillista med ett arbetsflöde
description: Lär dig hur du skapar en profillista i ett arbetsflöde
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 10%

---

# Skapa en profillista med ett arbetsflöde{#creating-a-profile-list-with-a-workflow}

![](../../assets/v7-only.svg)

Om du vill skapa en **[!UICONTROL List]**-typlista baserad på den nya mottagartabellen måste du skapa ett målarbetsflöde som genererar listan.

Mer information om listor i Campaign finns i [det här avsnittet](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Följ stegen nedan för att skapa ett målarbetsflöde och uppdatera mottagare i en anpassad mottagartabell:

1. Gå till noden **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** i Utforskaren.
1. Skapa ett nytt arbetsflöde för målinriktning.
1. Placera en **Query**-aktivitet följt av en **List update**-aktivitet.

   ![](assets/mapping_create_list_workflow01.png)

1. Dubbelklicka på aktiviteten **Fråga** och klicka sedan på **[!UICONTROL Edit the query]** för att välja en måldimension baserat på schemat för den nya mottagartabellen (i vårt exempel: **Individuell**). Bekräfta genom att klicka på **[!UICONTROL Finish]**.

   ![](assets/mapping_create_list_workflow03.png)

1. Dubbelklicka på aktiviteten **Listuppdatering** och välj sedan alternativknappen **[!UICONTROL Create the list if necessary (Computed name)]**.

   ![](assets/mapping_create_list_workflow02.png)

1. Välj skapandemapp för den nya listan.
1. Kör arbetsflödet för att skapa listan.
1. Visa resultatet i noden för trädet som du valde under aktiviteten **[!UICONTROL List update]**.

   Kontrollpanelen anger schemat som listan baseras på, vilket visas nedan:

   ![](assets/mapping_list_view.png)
