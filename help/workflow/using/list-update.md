---
title: Listuppdatering
seo-title: Listuppdatering
description: Listuppdatering
seo-description: null
page-status-flag: never-activated
uuid: 1446f115-3f64-4b95-8e04-6426ab1b8dab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: ca2cd5bf-78a2-4e43-955d-206f4474d1e0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Listuppdatering{#list-update}

En **listuppdateringsaktivitet** lagrar populationen som anges i övergången i en lista över mottagare.

![](assets/s_user_segmentation_update_group.png)

Listan kan väljas från listan med befintliga grupper.

Den kan också skapas med alternativen **[!UICONTROL Create the list if necessary (Computed name)]** och **[!UICONTROL Create the list if necessary (Computed Folder and Name)]** . Med de här alternativen kan du välja vilken etikett du vill använda för att skapa en lista, och senare den mapp som listan ska sparas i. Etiketten kan också genereras automatiskt genom att du infogar dynamiska fält eller ett skript. De olika dynamiska fälten är tillgängliga på snabbmenyn till höger om etiketten.

![](assets/s_user_segmentation_update_list_calc.png)

Om listan redan finns läggs mottagarna till i det befintliga innehållet, såvida du inte markerar **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** alternativet. I det här fallet tas innehållet i listan bort före uppdateringen.

Om du vill att den skapade eller uppdaterade listan ska använda en annan tabell än mottagartabellen markerar du **[!UICONTROL Create or use a list with its own table]** alternativet.

Om du vill använda alternativet måste de specifika tabellerna i fråga ha konfigurerats i Adobe Campaign-instansen.

Om du sparar ett mål i en lista markeras i allmänhet slutet av ett arbetsflöde. Som standard har **[!UICONTROL List update]** aktiviteten därför ingen utgående övergång. Markera alternativet om du vill lägga till en **[!UICONTROL Generate an outbound transition]** .

## Exempel: Listuppdatering {#example--list-update}

I följande exempel följer listuppdateringsaktiviteten en fråga som riktar sig till män över 30 som bor i Frankrike. Listan skapas från resultatet av frågan. Den uppdateras sedan varje gång den startas från arbetsflödet. Det kan till exempel användas regelbundet för riktade kampanjerbjudanden.

1. Lägg till en fråga **[!UICONTROL list update activity]** direkt efter en fråga och öppna den för att redigera den.

   Mer information om hur du skapar en fråga i ett arbetsflöde finns i [Fråga](../../workflow/using/query.md).

1. Du kan välja en etikett för aktiviteten.
1. Välj alternativet **[!UICONTROL Create the list if necessary (Calculated name)]** om du vill visa att listan skapas när det första arbetsflödet har körts och sedan uppdateras med följande körningar.
1. Välj den mapp där du vill spara listan.
1. Ange en etikett för listan. Du kan infoga dynamiska fält för att automatiskt generera namnet från listan. I det här exemplet har listan samma namn som frågan för att enkelt identifiera innehållet.
1. Låt alternativet vara markerat om du vill ta bort mottagare som inte matchar målinriktningsvillkoret och infoga de nya i listan. **[!UICONTROL Purge the list if it exists (otherwise add to the list)]**
1. Låt även alternativet vara markerat **[!UICONTROL Create or use a list with its own table]** .
1. Låt alternativet vara **[!UICONTROL Generate an outbound transition]** avmarkerat.
1. Klicka **[!UICONTROL Ok]** och starta arbetsflödet.

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   Listan med matchande mottagare skapas eller uppdateras.

Mer information finns i videon [Skapa en lista över mottagare](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html) .

## Indataparametrar {#input-parameters}

* tableName
* schema

Identifierar populationen som ska sparas i gruppen.

## Utdataparametrar {#output-parameters}

* groupId

Gruppidentifierare.
