---
title: Celler
seo-title: Celler
description: Celler
seo-description: null
page-status-flag: never-activated
uuid: 1b18928f-04e1-4268-ab8e-ff74d78599de
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: f7187d42-56e9-4681-b172-22abd43ecd29
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Celler{#cells}

Aktiviteten ger **[!UICONTROL Cells]** en vy över de olika deluppsättningarna i form av datakolumner. Den underlättar delmängdsmanipulation och är även utformad för att uppmuntra personaliseringsmöjligheter.

![](assets/wf_split_cells.png)

Den här aktiviteten kan konfigureras för att ange specifika parametrar baserat på användarnas behov. Som standard visas detaljerna för varje delmängd i ett dedikerat fönster via flikarna **[!UICONTROL Selection]** och **[!UICONTROL Advanced]** . I exemplet nedan har formuläret ändrats: en **[!UICONTROL Data]** flik har lagts till för att aktivera associationen för ett erbjudande och en prioritetsnivå för varje delmängd.

![](assets/wf_split_cells_with_customization.png)

För den här konfigurationen har följande information lagts till i arbetsflödesformuläret (i noden **[!UICONTROL Administration > Configurations > Input forms]** i Adobe Campaign-trädet):

```
<container img="nms:miniatures/mini-enrich.png" label="Data">
                <input xpath="@code"/>
                <container xpath="select/node[@alias='@numTest']">
                  <input alwaysActive="true" expr="'long'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Priority'" type="expr" xpath="@label"/>
                  <input label="Priority" maxValue="12" minValue="0" type="number"
                         xpath="@value" xpathEditFromType="@type"/>
                </container>
                <container xpath="select/node[@alias='@test']">
                  <input alwaysActive="true" expr="'string'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Identifier'" type="expr" xpath="@label"/>
                  <input label="Cell identifier" xpath="@value"/>
                </container>
                <container xpath="select/node[@alias='linkTest']">
                  <input alwaysActive="true" expr="'link'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'nms:offer'" type="expr" xpath="@dataType"/>
                  <input alwaysActive="true" expr="'Offre'" type="expr" xpath="@label"/>
                  <input computeStringAlias="@valueLabel" label="Offers" notifyPathList="@_cs|@valueLabel"
                         schema="nms:offer" type="linkEdit" xpath="@value"/>
                </container>
```

Anpassa anmälningsformulär i Adobe Campaign är reserverat för expertanvändare. Mer information finns i det här [avsnittet](../../configuration/using/identifying-a-form.md).
