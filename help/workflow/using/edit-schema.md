---
title: Redigera schema
seo-title: Redigera schema
description: Redigera schema
seo-description: null
page-status-flag: never-activated
uuid: abd77902-98b7-4ab7-a240-dd6b3bb247bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 733576d2-505f-4598-89eb-a10e7331bf7e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 7%

---


# Redigera schema{#edit-schema}

Data kan omformas, normaliseras och, om det behövs, berikas i arbetsflödet med hjälp av **[!UICONTROL Edit schema]** aktiviteten. Det används vanligtvis för att normalisera datastrukturen: Du kan byta namn på utdatakolumnerna eller ändra deras innehåll genom att till exempel beräkna medelvärdena för ett fält eller en mängd.

Den här aktiviteten ändrar inte data i arbetstabellen, utan ändrar bara dess schema, dvs. den logiska vyn av data.

![](assets/wf_manipulation_box.png)

Du kan också skapa kopplingar med andra arbetstabeller via **[!UICONTROL Links]** fliken.

![](assets/wf_manipulation_box_link_tab.png)

I det nedre avsnittet kan du konfigurera listan med föreningsvillkor, dvs. villkoren som används för att stämma av data från de två tabellerna.
