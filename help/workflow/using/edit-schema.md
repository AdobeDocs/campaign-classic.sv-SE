---
product: campaign
title: Redigera schema
description: Läs mer om arbetsflödesaktiviteten Redigera schema
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Workflows, Targeting Activity
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 9%

---

# Redigera schema{#edit-schema}



Data kan omformas, normaliseras och vid behov berikas i arbetsflödet med **[!UICONTROL Edit schema]** aktivitet. Det används vanligtvis för att normalisera datastrukturen: du kan ändra namn på utdatakolumnerna eller deras innehåll genom att beräkna medelvärden för ett fält eller en mängd, till exempel.

Den här aktiviteten ändrar inte data i arbetstabellen, utan ändrar bara dess schema, dvs. den logiska vyn av data.

![](assets/wf_manipulation_box.png)

Du kan också skapa kopplingar med andra arbetstabeller via **[!UICONTROL Links]** -fliken.

![](assets/wf_manipulation_box_link_tab.png)

I det nedre avsnittet kan du konfigurera listan med föreningsvillkor, dvs. villkoren som används för att stämma av data från de två tabellerna.
