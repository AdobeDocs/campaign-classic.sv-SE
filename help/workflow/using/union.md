---
title: Union
seo-title: Union
description: Union
seo-description: null
page-status-flag: never-activated
uuid: 987e106e-c414-4db4-a93e-96e43dc04370
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 573021ad-1efb-4156-af6d-417737ce745a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Union{#union}

En union grupperar resultatet av flera inkommande aktiviteter i ett enda mål. Målet skapas med alla mottagna resultat: Alla tidigare aktiviteter måste därför avslutas för att unionen ska kunna genomföras.

![](assets/s_user_segmentation_union.png)

>[!NOTE]
>
>Mer information om hur du konfigurerar och använder unionsaktiviteten finns i [Kombinera flera mål (unionen)](../../workflow/using/targeting-data.md#combining-several-targets--union-).

## Unionsexempel {#union-example}

I följande exempel har resultaten från två frågor kombinerats för att uppdatera listan. De två frågorna har mottagarna som mål. Resultaten är därför baserade på samma tabell.

1. Infoga en aktivitet av typen **[!UICONTROL Union]** -type direkt efter de två frågorna och före en aktivitet av typen update i listan, och öppna den sedan.
1. Du kan ange en etikett.
1. Välj **[!UICONTROL Keys only]** avstämningsmetoden eftersom populationen som är resultatet av frågor i det här exemplet innehåller konsekventa data.
1. Om du har lagt till ytterligare data för frågorna kan du bestämma dig för att bara behålla de data som delas.
1. Om du vill begränsa storleken på den slutliga populationen markerar du **[!UICONTROL Limit size of generated population]** rutan.

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

Den här uppsättningen med tre värden identifierar målet som uppstår från unionen. **[!UICONTROL tableName]** är namnet på tabellen som registrerar målidentifierarna, **[!UICONTROL schema]** är populationens schema (vanligtvis nms:mottagare) och **[!UICONTROL recCount]** är antalet element i tabellen.
