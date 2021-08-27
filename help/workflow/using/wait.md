---
product: campaign
title: Vänta
description: Läs mer om aktiviteten Vänta i arbetsflödet
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---

# Vänta{#wait}

![](../../assets/common.svg)

En **Wait**-aktivitet aktiverar övergången efter en tidsfördröjning på mellan några sekunder och flera månader. En vänteuppgift blockerar inte utförandet av andra uppgifter. arbetsflödet kan köra uppgifter parallellt medan den här uppgiften väntar.

Du kan ange etiketten och vänta med redigeraren, som i exemplet nedan:

![](assets/edit_wait.png)

I fältet **[!UICONTROL Duration]** kan värdet uttryckas i valfri enhet: (enligt operatörens regionala inställningar):

* Om nationella inställningar inte anges: **s** för sekunder, **m** för minuter, **h** för timmar, **d** för dagar, **y** för år. Vid tidpunkten för godkännandet konverteras värdet automatiskt till den mest läsbara enheten.

   Standardenheten är dagen (**d**).

* Om de regionala inställningarna till exempel är inställda på &quot;Français&quot;: **s** för sekunder, **mn** för minuter, **h** för timmar, **j** för dagar, **m** för månader, **a** för år. Vid tidpunkten för godkännandet konverteras värdet automatiskt till den mest läsbara enheten, som i exemplet ovan **90s** konverterades till **1mn 30s**.

   Standardenheten är dagen (**d**).
