---
product: campaign
title: Vänta
description: Läs mer om aktiviteten Vänta i arbetsflödet
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Workflows
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 4%

---

# Vänta{#wait}



A **Vänta** Aktiviteten aktiverar övergången efter en tidsfördröjning på var som helst mellan några sekunder och flera månader. En vänteuppgift blockerar inte körningen av andra uppgifter. Arbetsflödet kan köra uppgifter parallellt medan den här uppgiften väntar.

Du kan ange etiketten och vänta med redigeraren, som i exemplet nedan:

![](assets/edit_wait.png)

I **[!UICONTROL Duration]** fältet kan värdet uttryckas i valfri enhet: (enligt operatorns nationella inställningar):

* Om nationella inställningar inte anges: **s** i sekunder, **m** i minuter, **h** i timmar, **d** i dagar, **y** i åratal. Vid tidpunkten för godkännandet konverteras värdet automatiskt till den mest läsbara enheten.

  Standardenheten är dagen (**d**).

* Om de regionala inställningarna till exempel är inställda på &quot;Français&quot;: **s** i sekunder, **mn** i minuter, **h** i timmar, **j** i dagar, **m** för månader, **a** i åratal. Vid tidpunkten för godkännandet konverteras värdet automatiskt till den mest läsbara enheten, som i exemplet ovan **90s** konverterades till **1mn 30s**.

  Standardenheten är dagen (**d**).
