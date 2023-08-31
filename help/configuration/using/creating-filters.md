---
product: campaign
title: Skapa filter
description: Lär dig hur du skapar filter för en anpassad tabell
feature: Profiles, Custom Resources
role: Data Engineer, Developer
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
exl-id: 6fad3dac-9af0-4796-adcf-d1de4b255aca
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 5%

---

# Skapa filter{#creating-filters}

Precis som den inbyggda mottagartabellen som medföljer Adobe Campaign kan den nya mottagartabellen få en uppsättning fördefinierade filter.

Dessa filter kommer att vara tillgängliga i målurvalsfönstret med samma funktioner som segment för mottagare (med parameterindataformulär, mappar osv.).

1. Gå till **[!UICONTROL Administration > Configuration > Predefined filters]** nod.
1. Skapa ett nytt filter.
1. Ange **[!UICONTROL Label]** för filtret, markera sedan det schema som matchar den externa mottagartabellen i **[!UICONTROL Document type]** fält.
1. Skapa **[!UICONTROL filtering conditions]** baserat på fälten i ditt schema.
1. Spara filtret.
