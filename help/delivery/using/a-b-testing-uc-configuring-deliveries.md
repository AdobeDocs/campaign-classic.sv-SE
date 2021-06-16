---
product: campaign
title: Konfigurera leveranser
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: 809de30b-7d08-40de-bf3e-dc80d62eae80
source-git-commit: 895aa2fd4fa9c7c71c0073e9be33c12d4e92c9fa
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Konfigurera leveranser i arbetsflödet {#step-4--configuring-the-deliveries-in-the-workflow}

När [populationer har skapats](a-b-testing-uc-population-samples.md) kan du konfigurera leveranserna. I det här fallet gör de två första leveranserna att du kan skicka olika innehåll till populationen A och B. Den tredje leveransen är reservleveransen: det skickas till mottagare som inte tillhör A eller B. Innehållet beräknas med ett skript och är identiskt med antingen A eller B, beroende på vilken som har den högsta öppna frekvensen. Vi måste konfigurera en vänteperiod för den tredje leveransen för att ta reda på resultatet av leveranserna A och B. Det är därför den tredje leveransen innehåller en **[!UICONTROL Wait]**-aktivitet.

1. Gå till aktiviteten **[!UICONTROL Split]** och länka övergången som är avsedd för population A till en av de e-postleveranser som redan finns i arbetsflödet.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Dubbelklicka på leveransen för att öppna den.
1. Välj mall för leverans A i listrutan.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Klicka på **[!UICONTROL Continue]** för att visa leveransen och spara den.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Länka övergången för aktiviteten **[!UICONTROL Split]** som är avsedd för population B till den andra e-postleveransen.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Öppna leveransen, välj mallen i leverans B och spara sedan leveransen.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Länka övergången som är avsedd för den återstående populationen till aktiviteten **[!UICONTROL Wait]**.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Öppna aktiviteten **[!UICONTROL Wait]** och konfigurera en vänteperiod på 5 dagar.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Länka aktiviteten **[!UICONTROL Wait]** till aktiviteten **[!UICONTROL JavaScript code]**.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

Nu kan du skapa skriptet. [Läs mer](a-b-testing-uc-script.md).
