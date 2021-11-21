---
product: campaign
title: Återgå till föregående version
description: Lär dig hur du återställer till den tidigare versionen
audience: migration
content-type: reference
topic-tags: rollback
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Återgå till föregående version{#about-rollback}

![](../../assets/v7-only.svg)

Efter en migrering kan du behöva återställa den tidigare versionen av Campaign om det uppstår problem.

Återställningsproceduren beror på den ursprungliga versionen av Campaign.

## Återställa version 6.1

Så här återställer du v6.1 från v7.

1. Återställ säkerhetskopian av databasen och återställ den.
1. Återställ **Adobe Campaign v6.back** mapp (**nl6.back** i Linux), byt namn till **Adobe Campaign v6** (**nl6** i Linux) och återställa den till sin ursprungliga plats.
1. Konfigurera om IIS genom att tilldela lyssnarportarna igen för att återupprätta integreringen av Adobe Campaign v6.1 på IIS-webbplatsnivå.
1. Stoppa tjänsten Adobe Campaign v7.
1. Starta om IIS.
1. Starta om tjänsten Adobe Campaign v6.1.

## Återställer till Campaign v6.02

Så här återställer du v6.02 från en v7.

1. Återställ säkerhetskopian av databasen och återställ den.
1. Återställ **Neolane v6.back** mapp (**nl6.back** i Linux), byt namn till **Neolane v6** (**nl6** i Linux) och återställa den till sin ursprungliga plats.
1. Konfigurera om IIS genom att tilldela lyssningsporten på nytt för att återupprätta integreringen av Adobe Campaign v6.02 på IIS-webbplatsnivå.
1. Stoppa tjänsten Adobe Campaign v6.1.
1. Starta om IIS.
1. Starta om tjänsten Adobe Campaign v6.02.

## Återställer till Campaign v5.11

Så här återställer du en v5.11 från en v7.

1. Återställ säkerhetskopian av databasen och återställ den.
1. Återställ **Neolane v5.back** mapp (**nl5.back** i Linux), byt namn till **Neolane v5** (**nl5** i Linux) och återställa den till sin ursprungliga plats.
1. Konfigurera om IIS genom att tilldela lyssnarportarna igen för att återupprätta integreringen av Neolane v5 på IIS-webbplatsnivå.
1. Stoppa tjänsten Adobe Campaign v7.
1. Starta om IIS.
1. Starta om tjänsten Adobe Campaign v5.
