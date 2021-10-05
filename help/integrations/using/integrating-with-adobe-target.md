---
product: campaign
title: Integrera med Adobe Target
description: Integrera med Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: 2e29d090-b87b-4cff-a703-58e1da082f04
source-git-commit: 0996cc313be93300bce2f094c97e45a794cd459e
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Integrera med Adobe Target{#integrating-with-adobe-target}

![](../../assets/v7-only.svg)

Genom integrationen mellan Adobe Campaign och Adobe Target (Classic och Standard) i Adobe Experience Cloud kan du inkludera ett erbjudande från Adobe Target i en e-postutsändning från Adobe Campaign.

Följande princip gäller: När en mottagare öppnar ett e-postmeddelande som skickas via Adobe Campaign kan du med ett anrop till Adobe Target visa en dynamisk version av innehållet. Den här dynamiska versionen beräknas utifrån de regler som anges i förväg när e-postmeddelandet skapas.

>[!NOTE]
>
>Integreringen stöder bara statiska bilder. Resten av innehållet kan inte personaliseras.

Adobe Target kan använda flera typer av data:

* Data från Adobe Campaign datamart
* Segment som är länkade till besökar-ID i Adobe Target, om de data som används inte omfattas av juridiska begränsningar
* Adobe Target data: användaragent, IP-adress, geopositioneringsdata

>[!NOTE]
>
>Du kan även hitta information om integrationen mellan Adobe Campaign och Adobe Target på [Adobe Target hjälpsidor](https://experienceleague.adobe.com/docs/target/using/integrate/campaign-and-target.html).
