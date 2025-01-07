---
product: campaign
title: Säkerhetskopiera
description: Säkerhetskopiera
feature: Monitoring
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: e5ef6aba-dc22-4c8d-9fbb-13d507181b65
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 1%

---

# Säkerhetskopiera{#backup}

Säkerhetskopiering är nödvändigt för att undvika dataförlust i händelse av problem (oavsett om det är fysiskt eller systemrelaterat) på en dator.

Data lagras på två olika platser:

* fysiska filer lagras i Adobe Campaign kataloger,
* andra data lagras i databasen.

De flesta data finns i databasen. Detta motsvarar 99 % av den information som ska säkerhetskopieras.

## Fysiska filer {#physical-files}

Filerna är uppdelade i flera kategorier:

* Konfigurationsfiler som lagras i **nl6/conf** gör att du snabbt kan konfigurera om Adobe Campaign.

* Omdirigeringsfiler, som lagras i **nl6/var/`<instance-name>`/redir**, finns på spårningsservrarna (kallas ofta för &quot;front&quot;) och innehåller alla tidigare kampanjomdirigeringar. De används fortfarande av tidigare kampanjer.

* Loggfiler som lagras i **nl6/var/`<instance-name>`/log** kan användas för att spåra problem.

Kataloger som ska säkerhetskopieras är därför:

* nl6/conf

* nl6/var/`<instance-name>`/redir (för varje instans)

* nl6/var/`<instance-name>`/log (valfritt)

* nl6/var/`<instance-name>`/relay (valfritt)


## Databas {#database}

>[!IMPORTANT]
>
>Databasen måste säkerhetskopieras.


Databasen innehåller all information som visas i Adobe Campaign Rich Client Console samt alla affärsdata.

Ditt värdföretag, och deras databasadministratörer, ansvarar för den här åtgärden.
