---
product: campaign
title: Välja en målgrupp att kartlägga
description: Välja en målgrupp att kartlägga
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 8%

---

# Välja en målgrupp att kartlägga{#selecting-a-target-mapping}

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
>Du kan också skapa nya målmappningar. Den här åtgärden är reserverad för expertanvändare. Mer information finns i [Konfigurationsguide](../../configuration/using/target-mapping.md).
