---
product: campaign
title: Sammanslutning
description: Läs mer om unionens arbetsflödesaktivitet
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 1cda3146-c333-4743-a871-c44583b6e5b2
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 1%

---

# Sammanslutning{#union}

En union grupperar resultatet av flera inkommande aktiviteter i ett enda mål. Målet skapas med alla mottagna resultat: Alla tidigare aktiviteter måste därför avslutas för att unionen ska kunna genomföras.

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>Mer information om hur du konfigurerar och använder unionsaktiviteten finns i [Kombinera flera mål (Union)](../../workflow/using/targeting-data.md#combining-several-targets--union-).

## Unionsexempel {#union-example}

I följande exempel har resultaten från två frågor kombinerats för att uppdatera listan. De två frågorna har mottagarna som mål. Resultaten är därför baserade på samma tabell.

1. Infoga en **[!UICONTROL Union]** -type-aktivitet direkt efter de två frågorna och före en update-type-aktivitet i listan och öppna den.
1. Du kan ange en etikett.
1. Välj avstämningsmetoden **[!UICONTROL Keys only]** eftersom populationen som är resultatet av frågor i det här exemplet innehåller konsekventa data.
1. Om du har lagt till ytterligare data för frågorna kan du bestämma dig för att behålla endast de data som delas.
1. Om du vill begränsa storleken på den slutliga populationen markerar du rutan **[!UICONTROL Limit size of generated population]**.

   Ange det slutliga talet genom att ange det maximala antalet mottagare och genom att välja frågan vars population ska prioriteras.

1. Godkänn unionsaktiviteten och konfigurera sedan listuppdateringsaktiviteten (se [Listuppdatering](../../workflow/using/list-update.md)).
1. Starta arbetsflödet. Antalet resultat visas och listan som definieras i listuppdateringsaktiviteten skapas eller uppdateras. Den här listan innehåller en uppsättning mottagare för båda frågorna eller, i tillämpliga fall, numret som definierades i föregående steg.

   ![](assets/union_example.png)

## Indataparametrar {#input-parameters}

* tableName
* schema

Varje inkommande händelse måste ange ett mål som definieras av dessa parametrar.

## Utdataparametrar {#output-parameters}

* tableName
* schema
* recCount

Den här uppsättningen med tre värden identifierar målet som uppstår från unionen. **[!UICONTROL tableName]** är namnet på tabellen som registrerar målidentifierarna,  **[!UICONTROL schema]** är populationens schema (vanligtvis nms:mottagare) och  **[!UICONTROL recCount]** är antalet element i tabellen.
