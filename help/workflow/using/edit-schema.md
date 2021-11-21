---
product: campaign
title: Redigera schema
description: Läs mer om arbetsflödesaktiviteten Redigera schema
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 3%

---

# Redigera schema{#edit-schema}

![](../../assets/common.svg)

Data kan omformas, normaliseras och vid behov berikas i arbetsflödet med **[!UICONTROL Edit schema]** aktivitet. Det används vanligtvis för att normalisera datastrukturen: Du kan byta namn på utdatakolumnerna eller ändra deras innehåll genom att till exempel beräkna medelvärdena för ett fält eller en mängd.

Den här aktiviteten ändrar inte data i arbetstabellen, utan ändrar bara dess schema, dvs. den logiska vyn av data.

![](assets/wf_manipulation_box.png)

Du kan också skapa kopplingar med andra arbetstabeller via **[!UICONTROL Links]** -fliken.

![](assets/wf_manipulation_box_link_tab.png)

I det nedre avsnittet kan du konfigurera listan med föreningsvillkor, dvs. villkoren som används för att stämma av data från de två tabellerna.
