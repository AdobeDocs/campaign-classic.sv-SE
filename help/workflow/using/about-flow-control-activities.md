---
product: campaign
title: Om flödeskontrollaktiviteter
description: Om flödeskontrollaktiviteter
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 3810cbd0-159c-4161-b568-1f61dcea0300
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 5%

---

# Flödeskontrollaktiviteter i arbetsflöden{#about-flow-control-activities}



Följande aktiviteter är databasaktiviteter: deras huvuduppgift är att samordna de andra aktiviteterna.

* **Start och slut**: gör att du kan visa start- och slutpunkterna för ett arbetsflöde. Se [Start och slut](start-and-end.md).
* **Förgrening**: gör att du kan aktivera alla utgående övergångar. Se avsnittet [Förgrening](fork.md).
* **Avtalad tid**: gör att du kan vänta på att flera aktiviteter som har startats samtidigt ska slutföras innan du fortsätter. Se avsnittet [Förgrening](fork.md).
* **Schemaläggaren**: gör att du kan definiera ett arbetsflödeskörningsschema. Se [Schemaläggaren](scheduler.md).
* **Test**: aktiverar en övergång baserat på ett testresultat. Se [Test](test.md).
* **Vänta**: aktiverar den utgående övergången efter en given tidsgräns. Se [Vänta](wait.md).
* **Tidsbegränsning**: gör att du kan pausa en aktivitet under en angiven period. Se [Tidsbegränsning](time-constraint.md).
* **Delarbetsflöde**: gör att du kan köra ett annat arbetsflöde. Se [Delarbetsflöde](sub-workflow.md).
* **Hoppar**: gör att du kan implementera övergångar utan länkar. Se [Hoppa (startpunkt och slutpunkt)](jump-start-point-and-end-point.md).
* **Extern signal**: gör att du kan aktivera den utgående övergången efter att du har tagit emot en extern signal. Se [Extern signal](external-signal.md)-avsnittet.
* **Godkännande**: gör att du kan skicka ett e-postmeddelande till en operator eller en grupp med operatorer och vänta på godkännande för att fortsätta med körningen. Se avsnittet [Godkännande](approval.md).
* **Varning**: gör att du kan skicka en varning till en operator eller en grupp med operatorer. Se avsnittet [Varning](alert.md).
* **Aktivitet**: gör att du kan konfigurera körning av aktiviteter. Se avsnittet [Aktivitet](task.md).
