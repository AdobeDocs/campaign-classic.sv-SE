---
title: Kontinuerlig leverans
seo-title: Kontinuerlig leverans
description: Kontinuerlig leverans
seo-description: null
page-status-flag: never-activated
uuid: af8b4582-299e-47f9-9819-987b35db94ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 9d80be19-8dde-4278-ab5f-23f364fe422e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Kontinuerlig leverans{#continuous-delivery}

Med en åtgärd av typen **kontinuerlig** leverans kan du lägga till nya mottagare till en befintlig leverans. Med den här leveranstypen slipper du skapa en ny leverans varje gång: Det här läget är ofta mer effektivt, särskilt när det gäller meddelanden om låga volymer eller meddelanden som skickas ut vid behov. På en leveransmallnivå kan du ange ett skript för att beräkna etiketten (och kampanjmappen) för den associerade leveransen. Om skriptet beräknar en leverans som inte finns än, skapas den direkt.

![](assets/edit_diffusion_fil.png)

Alternativet visar **[!UICONTROL Process errors]** en viss övergång som aktiveras om ett fel genereras. I det här fallet försätts arbetsflödet inte i felläge och fortsätter med körningen.

Fel som beaktas är filsystemfel (filen kunde inte flyttas, katalogen kunde inte nås osv.).

Det här alternativet bearbetar inte fel relaterade till aktivitetskonfigurationen, dvs. ogiltiga värden.

## Indataparametrar {#input-parameters}

* tableName
* schema

Varje inkommande händelse måste ange ett mål som definieras av dessa parametrar.

Endast när **[!UICONTROL Specified by the inbound event]** alternativet är markerat.

## Utdataparametrar {#output-parameters}

* tableName
* schema
* recCount

Den här uppsättningen med tre värden identifierar det mål som uppstår vid leverans. **[!UICONTROL tableName]** är namnet på den tabell som memorerar målets identifierare, **[!UICONTROL schema]** är populationens schema (vanligtvis nms:mottagare) och **[!UICONTROL recCount]** är antalet element i tabellen.

Övergången som är associerad med komplementet har samma parametrar.
