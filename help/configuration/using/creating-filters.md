---
product: campaign
title: Skapa filter
description: Lär dig hur du skapar filter för en anpassad tabell
feature: Profiles, Custom Resources
role: Data Engineer, Developer
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
exl-id: 6fad3dac-9af0-4796-adcf-d1de4b255aca
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 3%

---

# Skapa filter{#creating-filters}

Precis som den inbyggda mottagartabellen som medföljer Adobe Campaign kan den nya mottagartabellen få en uppsättning fördefinierade filter.

Dessa filter kommer att vara tillgängliga i målurvalsfönstret med samma funktioner som segment för mottagare (med parameterindataformulär, mappar osv.).

1. Gå till noden **[!UICONTROL Administration > Configuration > Predefined filters]**.
1. Skapa ett nytt filter.
1. Ange **[!UICONTROL Label]** för filtret och välj sedan det schema som matchar den externa mottagartabellen i fältet **[!UICONTROL Document type]**.
1. Skapa din **[!UICONTROL filtering conditions]** baserat på fälten i ditt schema.
1. Spara filtret.
