---
product: campaign
title: Om flödeskontrollaktiviteter
description: Om flödeskontrollaktiviteter
feature: Workflows
exl-id: 3810cbd0-159c-4161-b568-1f61dcea0300
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 5%

---

# Flödeskontrollaktiviteter i arbetsflöden{#about-flow-control-activities}



Följande aktiviteter är databasaktiviteter: deras huvuduppgift är att samordna de andra aktiviteterna.

* **Start och slut**: gör att du kan visa start- och slutpunkterna för ett arbetsflöde. Se [Start och slut](start-and-end.md).
* **Gaffel**: du kan aktivera alla utgående övergångar. Se [Gaffel](fork.md) -avsnitt.
* **Avtalad tid**: gör att du kan vänta på att flera åtgärder som har startats samtidigt ska slutföras innan du fortsätter. Se [Gaffel](fork.md) -avsnitt.
* **Schemaläggare**: låter dig definiera ett arbetsflödeskörningsschema. Se [Schemaläggare](scheduler.md).
* **Testa**: aktiverar en övergång baserat på ett testresultat. Se [Testa](test.md).
* **Vänta**: aktiverar den utgående övergången efter en viss tidsgräns. Se [Vänta](wait.md).
* **Tidsbegränsning**: låter dig pausa en uppgift under en angiven period. Se [Tidsbegränsning](time-constraint.md).
* **Delarbetsflöde**: gör att du kan köra ett annat arbetsflöde. Se [Delarbetsflöde](sub-workflow.md).
* **Påssjuka**: låter dig implementera övergångar utan länkar. Se [Hoppa (startpunkt och slutpunkt)](jump-start-point-and-end-point.md).
* **Extern signal**: gör att du kan aktivera den utgående övergången när du har tagit emot en extern signal. Se [Extern signal](external-signal.md)-avsnittet.
* **Godkännande**: gör att du kan skicka ett e-postmeddelande till en operator eller en grupp med operatorer och vänta på godkännande för att fortsätta med körningen. Se [Godkännande](approval.md) -avsnitt.
* **Varning**: gör att du kan skicka en varning till en operator eller en grupp med operatorer. Se [Varning](alert.md) -avsnitt.
* **Uppgift**: låter dig konfigurera körning av uppgifter. Se [Uppgift](task.md) -avsnitt.
