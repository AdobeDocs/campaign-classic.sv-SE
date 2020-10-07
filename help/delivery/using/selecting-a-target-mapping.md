---
title: Välja en målgrupp att kartlägga
seo-title: Välja en målgrupp att kartlägga
description: Välja en målgrupp att kartlägga
seo-description: null
page-status-flag: never-activated
uuid: 29a666a3-2ecc-4732-b068-c93935929771
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-delivery-templates
discoiquuid: e2c6e273-1640-4f46-a80e-0cecb06e2769
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 10%

---


# Välja en målgrupp att kartlägga{#selecting-a-target-mapping}

Som standard har leveransmallar som mål **[!UICONTROL Recipients]**. Målmappningen använder därför fälten i tabellen **nms:receive** . Adobe Campaign erbjuder andra målmappningar för leveranser som kan användas utifrån dina behov.

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
>Du kan också skapa nya målmappningar. Den här åtgärden är reserverad för expertanvändare. For more information, refer to the [Configuration guide](../../configuration/using/target-mapping.md).
