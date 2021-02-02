---
solution: Campaign Classic
product: campaign
title: Om transaktionsmeddelanden
description: 'Skicka utlösarmeddelanden baserat på händelser som genererats från informationssystem. '
audience: message-center
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 3%

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
>Om du vill skapa nya användare för Message Center-körningsinstanser på Adobe Cloud måste du kontakta [Adobe kundtjänst](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Message Center-användare är specifika operatorer som kräver dedikerad behörighet för att få åtkomst till mappar för &#39;Real time events&#39; (nmsRtEvent).
