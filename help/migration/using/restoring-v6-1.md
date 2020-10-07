---
title: Återställa version 6.1
seo-title: Återställa version 6.1
description: Återställa version 6.1
seo-description: null
page-status-flag: never-activated
uuid: 3fb71b6f-4d70-4814-a885-4d414a542eca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: e510482c-a56d-4254-90f8-19bd5c545e30
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 9%

---


# Återställa version 6.1{#restoring-v}

Så här återställer du v6.1 från v7.

1. Återställ säkerhetskopian av databasen och återställ den.
1. Återställ mappen **Adobe Campaign v6.back** (**nl6.back** i Linux), byt namn på den till **Adobe Campaign v6** (**nl6** i Linux) och återställ den till dess ursprungliga plats.
1. Konfigurera om IIS genom att tilldela lyssnarportarna igen för att återupprätta integreringen av Adobe Campaign v6.1 på IIS-webbplatsnivå.
1. Stoppa tjänsten Adobe Campaign v7.
1. Starta om IIS.
1. Starta om tjänsten Adobe Campaign v6.1.

