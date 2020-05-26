---
title: Arbetsflödets livscykel
description: Läs mer om arbetsflödets livscykel.
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# Arbetsflödets livscykel {#workflow-life-cycle}

Arbetsflödescykeln består av tre huvudsteg.

* **Redigeras**

   Detta är den inledande designfasen: När ett nytt arbetsflöde skapas är dess status&quot;Redigeras&quot;. Arbetsflödet hanteras ännu inte av servern och kan ändras utan risk.

* **Startat**

   När den inledande designfasen är klar kan arbetsflödet startas. I den här fasen hanteras instansen av servern och de enskilda åtgärderna körs. Arbetsflödet kan fortfarande ändras med vissa försiktighetsåtgärder.

* **Slutförd**

   Ett arbetsflöde är&quot;Slutfört&quot; när det inte längre finns några pågående uppgifter eller när en operator uttryckligen har stoppat instansen.

Aktiviteterna **Start** och **Leverans** beskrivs till exempel medan aktiviteten **Godkännande** blinkar i arbetsflödet nedan.

![](assets/new-workflow-6.png)

Detta innebär att de två första aktiviteterna har slutförts och att godkännande pågår, dvs. det har skapats men ännu inte slutförts.

Tecknen **574 -OK** som visas ovanför övergången efter **leveransaktiviteten** innebär att leveransförberedelsen har 574 mottagare som mål och att åtgärden har slutförts. Den här informationen, som läggs till i övergångarna när de körs, beräknas av aktiviteterna som bearbetar data.

Arbetsflödet startas och väntar på att en operator som tillhör gruppen som anges i **godkännandeaktiviteten** ska fatta ett beslut. Operatörer som tillhör gruppen och som har en e-postadress eller ett mobiltelefonnummer meddelas.

Operatorhantering beskrivs i det här [avsnittet](../../platform/using/access-management.md).

Mer information om hur du övervakar arbetsflöden finns i [det här avsnittet](../../workflow/using/monitoring-workflow-execution.md).
