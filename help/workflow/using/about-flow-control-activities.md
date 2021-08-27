---
product: campaign
title: Om flödeskontrollaktiviteter
description: Om flödeskontrollaktiviteter
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 3810cbd0-159c-4161-b568-1f61dcea0300
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 7%

---

# Om flödeskontrollaktiviteter{#about-flow-control-activities}

![](../../assets/common.svg)

Följande aktiviteter är databasaktiviteter: Deras huvuduppgift är att samordna de andra aktiviteterna.

* **Start och slut**: gör att du kan visa start- och slutpunkterna för ett arbetsflöde. Se [Start och slut](start-and-end.md).
* **Gaffel**: gör att du kan aktivera alla utgående övergångar. Se avsnittet [Förgrening](fork.md).
* **Avtalad tid**: gör att du kan vänta på att flera åtgärder som har startats samtidigt ska slutföras innan du fortsätter. Se avsnittet [Förgrening](fork.md).
* **Schemaläggare**: I kan du definiera ett arbetsflödeskörningsschema. Se [Schemaläggaren](scheduler.md).
* **Test**: möjliggör en övergång baserat på ett testresultat. Se [Test](test.md).
* **Vänta**: aktiverar utgående övergång efter en viss tidsgräns. Se [Vänta](wait.md).
* **Tidsbegränsning**: gör att du kan pausa en uppgift under en angiven period. Se [Tidsbegränsning](time-constraint.md).
* **Delarbetsflöde**: gör att du kan köra ett annat arbetsflöde. Se [Delarbetsflöde](sub-workflow.md).
* **Hoppar**: I kan du implementera övergångar utan länkar. Se [Hoppa (startpunkt och slutpunkt)](jump--start-point-and-end-point-.md).
* **Extern signal**: gör att du kan aktivera den utgående övergången när du har tagit emot en extern signal. Se [Extern signal](external-signal.md)-avsnittet.
* **Godkännande**: Med kan du skicka ett e-postmeddelande till en operator eller en grupp operatorer och vänta på godkännande för att fortsätta med körningen. Se avsnittet [Godkännande](approval.md).
* **Varning**: gör att du kan skicka en varning till en operator eller grupp med operatorer. Se avsnittet [Varning](alert.md).
* **Aktivitet**: I kan du konfigurera körning av uppgifter. Se avsnittet [Aktivitet](task.md).
