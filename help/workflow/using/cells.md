---
product: campaign
title: Celler
description: Celler
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: 7b562dba-7e4b-40a7-91db-7b9379de44ca
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 8%

---

# Celler{#cells}



The **[!UICONTROL Cells]** -aktiviteten ger en vy över de olika deluppsättningarna i form av datakolumner. Den underlättar delmängdsmanipulation och är även utformad för att uppmuntra personaliseringsmöjligheter.

![](assets/wf_split_cells.png)

Den här aktiviteten kan konfigureras för att ange specifika parametrar baserat på användarnas behov. Som standard visas detaljerna för varje delmängd i ett dedikerat fönster via **[!UICONTROL Selection]** och **[!UICONTROL Advanced]** -tabbar. I exemplet nedan har formuläret ändrats: a **[!UICONTROL Data]** -fliken har lagts till för att aktivera associationen för ett erbjudande och en prioritetsnivå för varje delmängd.

![](assets/wf_split_cells_with_customization.png)

Följande information har lagts till i arbetsflödesformuläret (i **[!UICONTROL Administration > Configurations > Input forms]** nod i Adobe Campaign-trädet):

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

Anpassa anmälningsformulär i Adobe Campaign är reserverat för expertanvändare. Mer information om detta hittar du i det här [avsnittet](../../configuration/using/identifying-a-form.md).
