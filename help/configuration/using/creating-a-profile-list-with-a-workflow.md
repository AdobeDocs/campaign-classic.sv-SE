---
title: Skapa en profillista med ett arbetsflöde
description: Lär dig hur du skapar en profillista i ett arbetsflöde
page-status-flag: never-activated
uuid: a30f7217-fe82-4290-b1e6-e7a126a316c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ba42c3cf-31fc-4fbc-b230-a2b3982328c5
translation-type: tm+mt
source-git-commit: c2c0609619e0cc81444d089850add6dec5de93fd
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 7%

---


# Skapa en profillista med ett arbetsflöde{#creating-a-profile-list-with-a-workflow}

Om du vill skapa en **[!UICONTROL List]** typlista baserad på den nya mottagartabellen måste du skapa ett målarbetsflöde som genererar listan.

Mer information om listor i Campaign finns i [det här avsnittet](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i video](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Följ stegen nedan för att skapa ett målarbetsflöde och uppdatera mottagare i en anpassad mottagartabell:

1. Gå till **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** noden för Utforskaren.
1. Skapa ett nytt arbetsflöde för målinriktning.
1. Placera en **Query** -aktivitet följt av en **List update** -aktivitet.

   ![](assets/mapping_create_list_workflow01.png)

1. Dubbelklicka på **Query** -aktiviteten och klicka sedan **[!UICONTROL Edit the query]** för att välja en måldimension baserat på schemat i den nya mottagartabellen (i vårt exempel: **Individuell**). Bekräfta genom **[!UICONTROL Finish]** att klicka.

   ![](assets/mapping_create_list_workflow03.png)

1. Dubbelklicka på aktiviteten **Listuppdatering** och välj sedan **[!UICONTROL Create the list if necessary (Computed name)]** alternativknappen.

   ![](assets/mapping_create_list_workflow02.png)

1. Välj skapandemapp för den nya listan.
1. Kör arbetsflödet för att skapa listan.
1. Visa resultatet i noden för trädet som du valde under **[!UICONTROL List update]** aktiviteten.

   Kontrollpanelen anger schemat som listan baseras på, vilket visas nedan:

   ![](assets/mapping_list_view.png)


