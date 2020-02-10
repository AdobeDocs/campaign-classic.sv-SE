---
title: Skapa en profillista med ett arbetsflöde
seo-title: Skapa en profillista med ett arbetsflöde
description: Skapa en profillista med ett arbetsflöde
seo-description: null
page-status-flag: never-activated
uuid: a30f7217-fe82-4290-b1e6-e7a126a316c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ba42c3cf-31fc-4fbc-b230-a2b3982328c5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 681e6ec5fc9ed8c7e46af04f0ed62927b30e1b2e

---


# Skapa en profillista med ett arbetsflöde{#creating-a-profile-list-with-a-workflow}

Om du vill skapa en **[!UICONTROL List]** typlista baserad på den nya mottagartabellen måste du skapa ett målarbetsflöde som genererar listan. Mer information om listor i Campaign finns i [det här avsnittet](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

1. Gå till **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** noden för Utforskaren.
1. Skapa ett nytt arbetsflöde för målinriktning.
1. Placera en **Query** -aktivitet följt av en **List update** -aktivitet.

   ![](assets/mapping_create_list_workflow01.png)

1. Dubbelklicka på **Query** -aktiviteten och klicka sedan **[!UICONTROL Edit the query]** för att välja en måldimension baserat på schemat i den nya mottagartabellen (i vårt exempel: **Individual**). Bekräfta genom **[!UICONTROL Finish]** att klicka.

   ![](assets/mapping_create_list_workflow03.png)

1. Dubbelklicka på aktiviteten **Listuppdatering** och välj sedan **[!UICONTROL Create the list if necessary (Computed name)]** alternativknappen.

   ![](assets/mapping_create_list_workflow02.png)

1. Välj skapandemapp för den nya listan.
1. Kör arbetsflödet för att skapa listan.
1. Visa resultatet i noden för trädet som du valde under **[!UICONTROL List update]** aktiviteten.

   Kontrollpanelen anger schemat som listan baseras på, vilket visas nedan:

   ![](assets/mapping_list_view.png)

>[!NOTE]
>
>Du kan även se videon [Skapa en lista över mottagare](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/creating-a-list-of-recipients.html) .

