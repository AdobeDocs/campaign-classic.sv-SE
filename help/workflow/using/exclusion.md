---
title: Uteslutning
seo-title: Uteslutning
description: Uteslutning
seo-description: null
page-status-flag: never-activated
uuid: e4f54a0b-2fec-4415-986b-83c8928ed174
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: acab51f3-686b-4d2b-bb02-8fbfae36b1ba
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Uteslutning{#exclusion}

En aktivitet av typen **Uteslutning** skapar ett mål baserat på ett huvudmål som ett eller flera andra mål extraheras från.

Om du vill konfigurera den här aktiviteten anger du dess etikett och väljer huvudmottagaruppsättningen: kan du skapa resultatet med hjälp av populationen från huvuduppsättningen. Profiler som delas av huvuduppsättningen och minst en av tävlingsaktiviteterna kommer att uteslutas.

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>Mer information om hur du konfigurerar och använder exkluderingsaktiviteten finns i [Utesluta en population (Uteslutning)](../../workflow/using/targeting-data.md#excluding-a-population--exclusion-).

Markera alternativet **[!UICONTROL Generate complement]** om du vill utnyttja den återstående populationen. Komplementet kommer att innehålla den huvudsakliga inkommande populationen minus den utgående populationen. En ytterligare övergång till utdata läggs sedan till i aktiviteten enligt följande:

![](assets/s_user_segmentation_exclu_compl.png)

## Exempel på undantag {#exclusion-examples}

Följande exempel söker efter en lista över mottagare i åldrarna 18 till 30 år, med undantag för personer bosatta i Paris.

1. Infoga och öppna en **[!UICONTROL Exclusion]** -type-aktivitet efter två frågor. Den första frågan riktar sig till mottagare som bor i Paris. Den andra frågan riktar sig till 18 till 30 år.
1. Ange huvuduppsättningen. Här är den **18-30 år gamla** frågan. Element som hör till den andra uppsättningen tas inte med i slutresultatet.
1. Markera alternativet **[!UICONTROL Generate complement]** om du vill utnyttja de data som finns kvar efter uteslutningen. I detta fall består komplementet av mottagare i åldrarna 18 till 30 år som bor i Paris.
1. Godkänn undantagskonfigurationen och infoga sedan en uppdateringslistaktivitet i resultatet. Du kan också infoga ytterligare en listuppdatering till komplementet där det behövs.
1. Kör arbetsflödet. I det här exemplet består resultatet av mottagare mellan 18 och 30 år, men de som bor i Paris utesluts och skickas till komplementet.

   ![](assets/exclusion_example.png)

Exemplet med svartlistsimport använder en aktivitet av typen **Uteslutning** som finns i [Läslista](../../workflow/using/read-list.md).

## Indataparametrar {#input-parameters}

* tableName
* schema

Varje inkommande händelse måste ange ett mål som definieras av dessa parametrar.

## Utdataparametrar {#output-parameters}

* tableName
* schema
* recCount

Den här uppsättningen med tre värden identifierar det mål som är resultatet av uteslutningen. **[!UICONTROL tableName]** är namnet på tabellen som registrerar målidentifierarna, **[!UICONTROL schema]** är populationens schema (vanligtvis nms:mottagare) och **[!UICONTROL recCount]** är antalet element i tabellen.

Övergången som är associerad med komplementet har samma parametrar.
