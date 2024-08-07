---
product: campaign
title: Återgå till föregående version
description: Lär dig hur du återställer till den tidigare versionen
feature: Upgrade
audience: migration
content-type: reference
topic-tags: rollback
hide: true
hidefromtoc: true
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 0%

---

# Återgå till föregående version{#about-rollback}



Efter en migrering kan du behöva återställa den tidigare versionen av Campaign om det uppstår problem.

Återställningsproceduren beror på den ursprungliga versionen av Campaign.

Så här återställer du v6.1 från v7.

1. Återställ säkerhetskopian av databasen och återställ den.
1. Återställ mappen **Adobe Campaign v6.back** (**nl6.back** i Linux), byt namn på den till **Adobe Campaign v6** (**nl6** i Linux) och återställ den till dess ursprungliga plats.
1. Konfigurera om IIS genom att tilldela lyssnarportarna igen för att återupprätta integreringen av Adobe Campaign v6.1 på IIS-webbplatsnivå.
1. Stoppa tjänsten Adobe Campaign v7.
1. Starta om IIS.
1. Starta om tjänsten Adobe Campaign v6.1.

<!--
	
## Restore to Campaign v6.02

Here is the procedure to restore a v6.02 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v6.back** folder (**nl6.back** in Linux), rename it to **Neolane v6** (**nl6** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Adobe Campaign v6.02 at IIS Website level.
1. Stop the Adobe Campaign v6.1 service.
1. Re-start IIS.
1. Restart the Adobe Campaign v6.02 service.

## Restore to Campaign v5.11

Here is the procedure to restore a v5.11 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v5.back** folder (**nl5.back** in Linux), rename it to **Neolane v5** (**nl5** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Neolane v5 at IIS Website level.
1. Stop the Adobe Campaign v7 service.
1. Re-start IIS.
1. Re-start the Adobe Campaign v5 service.

-->