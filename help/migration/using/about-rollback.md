---
product: campaign
title: Återgå till föregående version
description: Lär dig hur du återställer till den tidigare versionen
audience: migration
content-type: reference
topic-tags: rollback
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Återgå till föregående version{#about-rollback}

Efter en migrering kan du behöva återställa den tidigare versionen av Campaign om det uppstår problem.

Återställningsproceduren beror på den ursprungliga versionen av Campaign.

## Återställa version 6.1

Så här återställer du v6.1 från v7.

1. Återställ säkerhetskopian av databasen och återställ den.
1. Återställ mappen **Adobe Campaign v6.back** (**nl6.back** i Linux), byt namn på den till **Adobe Campaign v6** (**nl6** i Linux) och återställ den till den ursprungliga platsen.
1. Konfigurera om IIS genom att tilldela lyssnarportarna igen för att återupprätta integreringen av Adobe Campaign v6.1 på IIS-webbplatsnivå.
1. Stoppa tjänsten Adobe Campaign v7.
1. Starta om IIS.
1. Starta om tjänsten Adobe Campaign v6.1.

## Återställer till Campaign v6.02

Så här återställer du v6.02 från en v7.

1. Återställ säkerhetskopian av databasen och återställ den.
1. Återställ mappen **Neolane v6.back** (**nl6.back** i Linux), byt namn på den till **Neolane v6** (**nl6** i Linux) och återställ den till den ursprungliga platsen.
1. Konfigurera om IIS genom att tilldela lyssningsporten på nytt för att återupprätta integreringen av Adobe Campaign v6.02 på IIS-webbplatsnivå.
1. Stoppa tjänsten Adobe Campaign v6.1.
1. Starta om IIS.
1. Starta om tjänsten Adobe Campaign v6.02.

## Återställer till Campaign v5.11

Så här återställer du en v5.11 från en v7.

1. Återställ säkerhetskopian av databasen och återställ den.
1. Återställ mappen **Neolane v5.back** (**nl5.back** i Linux), byt namn på den till **Neolane v5** (**nl5** i Linux) och återställ den till den ursprungliga platsen.
1. Konfigurera om IIS genom att tilldela lyssnarportarna igen för att återupprätta integreringen av Neolane v5 på IIS-webbplatsnivå.
1. Stoppa tjänsten Adobe Campaign v7.
1. Starta om IIS.
1. Starta om tjänsten Adobe Campaign v5.
