---
product: campaign
title: Skapa ett Experience Manager-nyhetsbrev
description: Skapa ett Experience Manager-nyhetsbrev
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
exl-id: 9fa3ce08-3007-4c65-9841-bad339428b7c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 1%

---

# Skapa ett Experience Manager-nyhetsbrev{#creating-an-experience-manager-newsletter}



Den här integreringen kan till exempel användas för att skapa ett nyhetsbrev i Adobe Experience Manager som sedan används i Adobe Campaign som en del av en e-postkampanj.

**Från Adobe Experience Manager:**

1. Klicka på AEM **Adobe Experience** logotypen längst upp till vänster på sidan och välj **[!UICONTROL Sites]**.

   ![](assets/aem_uc_1.png)

1. Välj **[!UICONTROL Campaigns > Name of your brand (here We.Retail) > Main Area > Email campaigns]**.
1. Klicka på **[!UICONTROL Create]** knappen längst upp till höger på sidan och välj **[!UICONTROL Page]**.

   ![](assets/aem_uc_2.png)

1. Välj **[!UICONTROL Adobe Campaign Email (AC 6.1)]** mall och ge nyhetsbrevet ett namn.
1. När sidan har skapats går du till **[!UICONTROL Page information]** meny och klicka **[!UICONTROL Open Properties]**.

   ![](assets/aem_uc_3.png)

1. I **[!UICONTROL Cloud Services]** flik, välja **[!UICONTROL Adobe Campaign]** as **[!UICONTROL Cloud service configuration]** och din Adobe Campaign-instans i den andra listrutan.

   ![](assets/aem_uc_4.png)

1. Redigera ditt e-postinnehåll genom att lägga till komponenter, t.ex. anpassningsfält från Adobe Campaign.
1. När din e-postadress är klar kan du gå till **[!UICONTROL Page information]** meny och klicka **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_5.png)

1. I den första listrutan väljer du **[!UICONTROL Publish to Adobe Campaign]** som arbetsflödesmodell och klicka **[!UICONTROL Start workflow]**.

   ![](assets/aem_uc_6.png)

1. Som föregående steg startar du sedan **[!UICONTROL Approve for Campaign]** arbetsflöde.
1. En ansvarsfriskrivning visas ovanpå sidan. Klicka **[!UICONTROL Complete]** för att bekräfta granskningen och klicka på **[!UICONTROL Ok]**.

   ![](assets/aem_uc_7.png)

1. Klicka igen **[!UICONTROL Complete]** och markera **[!UICONTROL Newsletter approval]** i **[!UICONTROL Next Step]** nedrullningsbar meny.

   ![](assets/aem_uc_8.png)

Nyhetsbrevet är nu klart och synkroniserat i Adobe Campaign.

**Från Adobe Campaign:**

1. Från **[!UICONTROL Campaigns]** flik, klicka **[!UICONTROL Deliveries]** sedan **[!UICONTROL Create]**.

   ![](assets/aem_uc_9.png)

1. I **[!UICONTROL Delivery template]** väljer du **[!UICONTROL Email delivery with AEM content (mailAEMContent)]** mall.

   ![](assets/aem_uc_10.png)

1. Lägg till en **[!UICONTROL Label]** till leveransen och klicka **[!UICONTROL Continue]**.
1. Klicka på knappen **[!UICONTROL Synchronize]**.

   Om knappen inte visas i gränssnittet klickar du på **[!UICONTROL Properties]** och väljer **[!UICONTROL Advanced]** -fliken. The **[!UICONTROL Content editing mode]** ska anges till **[!UICONTROL AEM]** med AEM i **[!UICONTROL AEM account]** fält.

   ![](assets/aem_uc_11.png)

1. Markera leveransen som skapats i Adobe Experience Manager och klicka på **[!UICONTROL Ok]**.
1. Klicka på **[!UICONTROL Refresh content]** så snart du har ändrat AEM.

   ![](assets/aem_uc_12.png)

Din e-post kan nu skickas till din målgrupp.
