---
title: Återvinning av händelser
seo-title: Återvinning av händelser
description: Återvinning av händelser
seo-description: null
page-status-flag: never-activated
uuid: 55624a41-65a1-4759-8087-6e5d2c5c5b62
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 568a9dec-5818-4666-b858-aa41fe827b92
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# Återvinning av händelser{#event-recycling}

Om det inte går att skicka ett meddelande via en viss kanal kan Adobe Campaign skicka meddelandet igen via en annan kanal. Om till exempel en leverans på SMS-kanalen misslyckas, skickas meddelandet igen med e-postkanalen.

För att göra detta måste du konfigurera ett arbetsflöde som återskapar alla händelser med **leveransfelstatus** och tilldelar dem en annan kanal.

>[!CAUTION]
>
>Det här steget kan bara utföras med ett arbetsflöde och är därför reserverat för expertanvändare. Mer information får du om du kontaktar kontoansvarig på Adobe.

