---
product: campaign
title: Skapa en profillista med ett arbetsflöde
description: Lär dig hur du skapar en profillista i ett arbetsflöde
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Workflows, Profiles
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 12%

---

# Skapa en profillista med ett arbetsflöde{#creating-a-profile-list-with-a-workflow}



Skapa en **[!UICONTROL List]** typlista baserad på den nya mottagartabellen, måste du skapa ett målarbetsflöde som genererar listan.

Mer information om listor i Campaign finns i [det här avsnittet](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

Följ stegen nedan för att skapa ett målarbetsflöde och uppdatera mottagare i en anpassad mottagartabell:

1. Gå till **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** Utforskarens nod.
1. Skapa ett nytt arbetsflöde för målinriktning.
1. Placera en **Fråga** aktivitet följt av **Listuppdatering** aktivitet.

   ![](assets/mapping_create_list_workflow01.png)

1. Dubbelklicka på **Fråga** aktivitet och klicka sedan på **[!UICONTROL Edit the query]** att välja en målinriktningsdimension baserat på schemat för den nya mottagartabellen (i vårt exempel: **Enskild**). Klicka på **[!UICONTROL Finish]** för att bekräfta.

   ![](assets/mapping_create_list_workflow03.png)

1. Dubbelklicka på **Listuppdatering** väljer du **[!UICONTROL Create the list if necessary (Computed name)]** alternativknapp.

   ![](assets/mapping_create_list_workflow02.png)

1. Välj skapandemapp för den nya listan.
1. Kör arbetsflödet för att skapa listan.
1. Visa resultatet i noden för trädet som du valde under **[!UICONTROL List update]** aktivitet.

   Kontrollpanelen anger schemat som listan baseras på, vilket visas nedan:

   ![](assets/mapping_list_view.png)
