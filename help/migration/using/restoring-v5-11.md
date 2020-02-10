---
title: Återställer v5.11
seo-title: Återställer v5.11
description: Återställer v5.11
seo-description: null
page-status-flag: never-activated
uuid: 4480c97c-5845-483c-a17b-644f05783b4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: ef778333-8e50-402b-9a69-78ac94497c67
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# Återställer v5.11{#restoring-v}

Så här återställer du en v5.11 från en v7.

1. Återställ säkerhetskopian av databasen och återställ den.
1. Återställ mappen **Neolane v5.back** (**nl5.back** i Linux), byt namn på den till **Neolane v5** (**nl5** i Linux) och återställ den till dess ursprungliga plats.
1. Konfigurera om IIS genom att tilldela lyssnarportarna igen för att återupprätta integreringen av Neolane v5 på IIS-webbplatsnivå.
1. Stoppa tjänsten Adobe Campaign v7.
1. Starta om IIS.
1. Starta om tjänsten Adobe Campaign v5.

