---
product: campaign
title: Redigera schema
description: Läs mer om arbetsflödesaktiviteten Redigera schema
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 3%

---

# Redigera schema{#edit-schema}

Data kan omformas, normaliseras och, om det behövs, berikas i arbetsflödet med hjälp av aktiviteten **[!UICONTROL Edit schema]**. Det används vanligtvis för att normalisera datastrukturen: Du kan byta namn på utdatakolumnerna eller ändra deras innehåll genom att till exempel beräkna medelvärdena för ett fält eller en mängd.

Den här aktiviteten ändrar inte data i arbetstabellen, utan ändrar bara dess schema, dvs. den logiska vyn av data.

![](assets/wf_manipulation_box.png)

Du kan också skapa kopplingar med andra arbetstabeller via fliken **[!UICONTROL Links]**.

![](assets/wf_manipulation_box_link_tab.png)

I det nedre avsnittet kan du konfigurera listan med föreningsvillkor, dvs. villkoren som används för att stämma av data från de två tabellerna.
