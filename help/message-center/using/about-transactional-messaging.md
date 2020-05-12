---
title: Om transaktionsmeddelanden
seo-title: Om transaktionsmeddelanden
description: Om transaktionsmeddelanden
seo-description: null
page-status-flag: never-activated
uuid: c854daac-8756-44f3-a4e2-be31177ab9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: 97df4bd5-a8e3-48f4-87c8-fa090ea3f771
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f4ecdab4c17a6ba8deb3b98079f57bb7a9adf4a0
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---


# Om transaktionsmeddelanden{#about-transactional-messaging}

Transactional Messaging (Message Center) är en Campaign-modul som är utformad för att hantera utlösarmeddelanden. Dessa meddelanden genereras från händelser som utlöses från informationssystem och kan vara: Faktura, orderbekräftelse, leveransbekräftelse, lösenordsändring, meddelande om att produkten inte är tillgänglig, kontoutdrag eller skapande av webbkonto till exempel.

>[!IMPORTANT]
>
>Transactional messaging kräver en specifik licens. Kontrollera licensavtalet.

Adobe Campaign Message Center-modulen är integrerad i ett informationssystem som returnerar händelser som ska ändras till personaliserade transaktionsmeddelanden. Dessa meddelanden kan skickas individuellt eller gruppvis via e-post, SMS eller push-meddelanden.

I den här specifika arkitekturen separeras körningscellen från kontrollinstansen, vilket ger högre tillgänglighet och bättre lasthantering.

>[!NOTE]
>
>Om du vill skapa nya användare för MSMQ-körningsinstanser på Adobe Cloud måste du kontakta Adobes kundtjänst. Message Center-användare är specifika operatorer som kräver dedikerad behörighet för att få åtkomst till mappar för &#39;Real time events&#39; (nmsRtEvent).
