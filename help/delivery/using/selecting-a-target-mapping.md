---
product: campaign
title: Välj en målmappning
description: Lär dig målinrikta mappning
feature: Delivery Templates
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 10%

---

# Välj en målmappning{#selecting-a-target-mapping}

![](../../assets/common.svg)

Som standard är målet för leveransmallar **[!UICONTROL Recipients]**. Målmappningen använder därför fälten i **nms:mottagare** tabell. Adobe Campaign erbjuder andra målmappningar för leveranser som kan användas utifrån dina behov.

![](assets/delivery_select_mapping.png)

Mappningarna är följande:

| Namn | Använd | Standardschema |
|---|---|---|
| Mottagare | Leverera till mottagare av Adobe Campaign-databasen | nms:mottagare |
| Besökare | Leverera till besökare vars profiler har samlats in via hänskjutning (viral marknadsföring) eller via sociala nätverk (Facebook, Twitter), till exempel. | mns:besökare |
| Prenumerationer | Leverera till mottagare som prenumererar på en informationstjänst som ett nyhetsbrev | nms:prenumeration |
| Prenumerationer på besökare | Skicka till besökare som prenumererar på en informationstjänst | nms:visitorSub |
| Tjänst | Publicera till ett Twitter-konto eller en Facebook-sida | nms:service |
| Operatorer | Leverera till Adobe Campaign | nms:operator |
| Extern fil | Leverera via en fil som innehåller all information som behövs för leveransen | Inget länkat schema, inget mål har angetts |

>[!NOTE]
>
>Du kan också skapa nya målmappningar. Den här åtgärden är reserverad för expertanvändare. Mer information hittar du i [det här avsnittet](../../configuration/using/target-mapping.md).
