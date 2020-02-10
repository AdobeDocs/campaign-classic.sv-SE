---
title: Säkerhetskopiera
seo-title: Säkerhetskopiera
description: Säkerhetskopiera
seo-description: null
page-status-flag: never-activated
uuid: 50134154-a671-4534-b48d-a9e2c42e8f1a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 870ab0f2-1bd7-42e7-8d83-a08a520b6587
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# Säkerhetskopiera{#backup}

Säkerhetskopiering är nödvändigt för att undvika dataförlust i händelse av problem (oavsett om det är fysiskt eller systemrelaterat) på en dator.

Data lagras på två olika platser:

* fysiska filer lagras i Adobe Campaign-katalogerna,
* andra data lagras i databasen.

De flesta data finns i databasen. Detta motsvarar 99 % av den information som ska säkerhetskopieras.

## Fysiska filer {#physical-files}

Filerna är uppdelade i flera kategorier:

* Konfigurationsfiler i **nl6/conf**

   Med dessa kan ni snabbt konfigurera om Adobe Campaign.

* Omdirigeringsfiler ** nl6/var/`<instancename>`/redir**

   Dessa finns på spårningsservrarna (kallas ofta frontservrar) och inkluderar alla tidigare kampanjomdirigeringar. De används fortfarande av tidigare kampanjer.

* Loggfiler: **nl6/var/`<instancename>`/log**

   Dessa kan användas för att spåra problem.

Kataloger som ska säkerhetskopieras är därför:

* nl6/conf

* nl6/var/`<instanceName>`/redir (för varje instans)

* nl6/var/`<instanceName>`/log (valfritt)

* nl6/var/`<instanceName>`/relay (valfritt)

>[!CAUTION]
>
>Det är viktigt att säkerhetskopiera databasen.

## Databas {#database}

Databasen innehåller all information som visas i Adobe Campaign-klientkonsolen samt alla affärsdata.

Ditt värdföretag och deras databasadministratörer ansvarar för den här åtgärden.
