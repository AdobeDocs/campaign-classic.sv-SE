---
title: Använda tabellen Adobe Campaign Classic-mottagare
description: Lär dig hur du använder den färdiga mottagartabellen i Adobe Campaign Classic när du utformar din datamodell.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 620724e283215df1fb3f10bd0211652b36284b57

---


# Bästa praxis för datamodell{#data-model-best-practices}

Nedan följer några metodtips som bör följas när du utformar din datamodell med stora tabeller och komplexa kopplingar.

* När du använder ytterligare anpassade mottagartabeller måste du ha en dedikerad loggtabell för varje leveransmappning.
* Minska antalet kolumner, särskilt genom att identifiera de som inte används.
* Optimera datamodellens relationer genom att undvika komplexa kopplingar, till exempel kopplingar på flera villkor och/eller flera kolumner.
* Använd alltid numeriska data i stället för teckensträngar för kopplingsnycklar.
* Minska så mycket du kan av djupet för loggbevarande. Om du behöver mer detaljerad historik kan du sammanställa beräkningar och/eller hantera anpassade loggtabeller för att lagra större historik.

Mer detaljerad information om hur du optimerar databasdesignen för större volymer finns i [Klassisk datamodell](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html)för Campaign.
