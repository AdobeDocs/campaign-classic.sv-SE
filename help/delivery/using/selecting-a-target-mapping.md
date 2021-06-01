---
product: campaign
title: Välja en målgrupp att kartlägga
description: Välja en målgrupp att kartlägga
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
exl-id: b5514fa3-1e65-45dc-8e40-d1ba3b673e7a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 8%

---

# Välja en målgrupp att kartlägga{#selecting-a-target-mapping}

Som standard har leveransmallar som mål **[!UICONTROL Recipients]**. Målmappningen använder därför fälten i tabellen **nms:receive**. Adobe Campaign erbjuder andra målmappningar för leveranser som kan användas utifrån dina behov.

![](assets/delivery_select_mapping.png)

Mappningarna är följande:

| Namn | Använd | Standardschema |
|---|---|---|
| Mottagare | Leverera till mottagare av Adobe Campaign-databasen | nms:mottagare |
| Besökare | Leverera till besökare vars profiler har samlats in via hänskjutning (viral marknadsföring) eller via sociala nätverk (Facebook, Twitter), till exempel. | mns:besökare |
| Prenumerationer | Leverera till mottagare som prenumererar på en informationstjänst som ett nyhetsbrev | nms:prenumeration |
| Prenumerationer på besökare | Ge besökare som prenumererar på en informationstjänst | nms:visitorSub |
| Tjänst | Publicera till ett Twitter-konto eller en Facebook-sida | nms:service |
| Operatorer | Leverera till Adobe Campaign | nms:operator |
| Extern fil | Leverera via en fil som innehåller all information som behövs för leveransen | Inget länkat schema, inget mål har angetts |

>[!NOTE]
>
>Du kan också skapa nya målmappningar. Den här åtgärden är reserverad för expertanvändare. Mer information finns i [Konfigurationshandboken](../../configuration/using/target-mapping.md).
