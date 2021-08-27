---
product: campaign
title: Säkerhetskopiera
description: Säkerhetskopiera
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 2%

---

# Säkerhetskopiera{#backup}

![](../../assets/v7-only.svg)

Säkerhetskopiering är nödvändigt för att undvika dataförlust i händelse av problem (oavsett om det är fysiskt eller systemrelaterat) på en dator.

Data lagras på två olika platser:

* fysiska filer lagras i Adobe Campaign kataloger,
* andra data lagras i databasen.

De flesta data finns i databasen. Detta motsvarar 99 % av den information som ska säkerhetskopieras.

## Fysiska filer {#physical-files}

Filerna är uppdelade i flera kategorier:

* Konfigurationsfiler som finns i **nl6/conf**

   Med dessa kan du snabbt konfigurera om Adobe Campaign.

* Omdirigeringsfiler ** nl6/var/`<instancename>`/redir**

   Dessa finns på spårningsservrarna (kallas ofta frontservrar) och inkluderar alla tidigare kampanjomdirigeringar. De används fortfarande av tidigare kampanjer.

* Loggfiler: **nl6/var/`<instancename>`/log**

   Dessa kan användas för att spåra problem.

Kataloger som ska säkerhetskopieras är därför:

* nl6/conf

* nl6/var/`<instanceName>`/redir (för varje instans)

* nl6/var/`<instanceName>`/log (valfritt)

* nl6/var/`<instanceName>`/relay (valfritt)

>[!IMPORTANT]
>
>Det är viktigt att säkerhetskopiera databasen.

## Databas {#database}

Databasen innehåller all information som visas i Adobe Campaign Rich Client Console samt alla affärsdata.

Ditt värdföretag och deras databasadministratörer ansvarar för den här åtgärden.
