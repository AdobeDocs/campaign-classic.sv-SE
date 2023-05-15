---
product: campaign
title: Säkerhetskopiera
description: Säkerhetskopiera
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-on-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 0429c3608fbcec98a397cc17fd45cd173cf64b6e
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 2%

---

# Säkerhetskopiera{#backup}



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
