---
title: Återställer v6.02
seo-title: Återställer v6.02
description: Återställer v6.02
seo-description: null
page-status-flag: never-activated
uuid: df21209b-4825-42fa-a303-f383f872abb5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: 4f65ba19-e9f0-4425-b640-f27c61394859
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# Återställer v6.02{#restoring-v}

Så här återställer du v6.02 från en v7.

1. Återställ säkerhetskopian av databasen och återställ den.
1. Återställ mappen **Neolane v6.back** (**nl6.back** i Linux), byt namn på den till **Neolane v6** (**nl6** i Linux) och återställ den till dess ursprungliga plats.
1. Konfigurera om IIS genom att tilldela lyssningsporten på nytt för att återupprätta integreringen av Adobe Campaign v6.02 på IIS-webbplatsnivå.
1. Stoppa tjänsten Adobe Campaign v6.1.
1. Starta om IIS.
1. Starta om tjänsten Adobe Campaign v6.02.

