---
title: Skapa ett Experience Manager-nyhetsbrev
seo-title: Skapa ett Experience Manager-nyhetsbrev
description: Skapa ett Experience Manager-nyhetsbrev
seo-description: null
page-status-flag: never-activated
uuid: 75cf4891-06a6-42d2-9b22-b4d93e0dc64a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 627ade78-96b3-4a6e-9ace-74610a3c8d1a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 56212b320d5077f9b66952e7c11eb8bdcea9e3b4
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Skapa ett Experience Manager-nyhetsbrev{#creating-an-experience-manager-newsletter}

Den här integreringen kan till exempel användas för att skapa ett nyhetsbrev i Adobe Experience Manager som sedan används i Adobe Campaign som en del av en e-postkampanj.

Ett mer detaljerat exempel på hur du använder den här integreringen finns i den här [steg-för-steg-guiden](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/aem.html).

**Från Adobe Experience Manager:**

1. Klicka på **Adobe Experience** -logotypen i den övre vänstra delen av sidan i din AEM-författarinstans och välj **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Välj **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**.
1. Klicka på **[!UICONTROL Create]** knappen i det övre högra hörnet på sidan och markera sedan **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. Välj **[!UICONTROL Adobe Campaign Email (AC 6.1)]** mall och ge nyhetsbrevet ett namn.
1. När sidan har skapats öppnar du **[!UICONTROL Page information]** menyn och klickar på **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. På **[!UICONTROL Cloud Services]** fliken väljer du **[!UICONTROL Adobe Campaign]** som **[!UICONTROL Cloud service configuration]** och din Adobe Campaign-instans i den andra listrutan.

   ![](assets/aem_uc_4.png)

1. Redigera ditt e-postinnehåll genom att lägga till komponenter, t.ex. anpassningsfält från Adobe Campaign.
1. När e-postmeddelandet är klart går du till **[!UICONTROL Page information]** menyn och klickar **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. I den första listrutan väljer du **[!UICONTROL Publish to Adobe Campaign]** som arbetsflödesmodell och klickar på **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. Starta sedan arbetsflödet som föregående steg **[!UICONTROL Approve for Campaign]** .
1. En ansvarsfriskrivning visas ovanpå sidan. Klicka **[!UICONTROL Complete]** för att bekräfta granskningen och klicka på **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. Klicka igen **[!UICONTROL Complete]** och välj **[!UICONTROL Newsletter approval]** i **[!UICONTROL Next Step]** listrutan.

   ![](assets/aem_uc_8.png)

Nyhetsbrevet är nu klart och synkroniserat i Adobe Campaign.

**Från Adobe Campaign:**

1. From the **[!UICONTROL Campaigns]** tab, click **[!UICONTROL Deliveries]** then **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. Välj **[!UICONTROL Delivery template]** mallen i **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** listrutan.

   ![](assets/aem_uc_10.png)

1. Lägg till en **[!UICONTROL Label]** till leveransen och klicka på **[!UICONTROL Continue]**.
1. Klicka på **[!UICONTROL Synchronize]** knappen.

   Om den här knappen inte visas i gränssnittet klickar du på **[!UICONTROL Properties]** -knappen och väljer **[!UICONTROL Advanced]** -fliken. Fältet **[!UICONTROL Content editing mode]** ska ställas in på **[!UICONTROL AEM]** med din AEM-instans i **[!UICONTROL AEM account]** fältet.

   ![](assets/aem_uc_11.png)

1. Markera den leverans du skapat tidigare i Adobe Experience Manager och klicka på **[!UICONTROL Ok]**.
1. Klicka på **[!UICONTROL Refresh content]** knappen så snart några ändringar har gjorts i din AEM-leverans.

   ![](assets/aem_uc_12.png)

Din e-post kan nu skickas till din målgrupp.
