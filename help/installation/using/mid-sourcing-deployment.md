---
title: Distribution från olika källor
seo-title: Distribution från olika källor
description: Distribution från olika källor
seo-description: null
page-status-flag: never-activated
uuid: e359c486-7ee6-4295-80fc-4c371a0ef068
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 19220d8e-9494-46b4-9aa0-4c4a729aea96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# Distribution från olika källor{#mid-sourcing-deployment}

Denna konfiguration är en optimal mellanlösning mellan en värdkonfiguration (ASP) och internalisering. De utåtriktade komponenterna utförs på en&quot;server med mellanleverantörer&quot; på Adobe Campaign.

>[!NOTE]
>
>Om du vill konfigurera den här typen av distribution måste du skaffa ett lämpligt alternativ. Kontrollera licensavtalet.

Allmän kommunikation mellan servrar och processer sker enligt följande schema:

![](assets/s_ncs_install_midsourcing.png)

* Modulerna för exekvering och studshantering är inaktiverade på instansen.
* Programmet är konfigurerat att utföra meddelandekörning på en fjärrserver med &quot;mellanlagring&quot; som drivs med SOAP-anrop (via HTTP eller HTTPS).

## Funktioner {#features}

### Fördelar {#advantages}

* Förenklad serverkonfiguration: Kunden behöver inte konfigurera utåtriktade moduler (mta och inMail).
* Begränsad användning av bandbredd: Eftersom körningen utförs av servern med mellanlagring krävs bara tillräcklig bandbredd för att skicka personaliseringsdata till servern med mellanlagring.
* Hög tillgänglighet är inte längre något internt problem: Felet har flyttats till servern med mellanlagring (omdirigering, spegelsidor, exekveringsservrar osv.).
* Databasen lämnar inte företaget: Endast data som är nödvändiga för att samla ihop meddelandena skickas till servern med mellanlagring (HTTPS kan användas för detta).
* Den här typen av driftsättning kan vara en lösning för arkitekturer med stora volymer (många mottagare i databasen) och ett betydande leveransflöde.

### Nackdelar {#disadvantages}

* Visning av meddelandekörningsinformation och rapportfunktioner fördröjs något på grund av den tid det tar att få tillbaka information från mittkällservern.
* Undersökningar och webbformulär finns kvar på klientplattformen.

### Rekommenderad utrustning {#recommended-equipment}

* Programserver: 2 GHz processor med fyra kärnor, 4 GB RAM, programvarubaserad RAID 1 80 GB SATA-hårddisk.
* Databasserver: 3 GHz två processorer med fyra kärnor, minst 4 GB RAM, maskinvarubaserad RAID 10 SAS-hårddisk på 1 5 000 v/min, antalet beroende på databasens storlek och förväntade prestanda.

>[!NOTE]
>
>Omdirigering och hantering från mellanleverantörer är separata element, men spårningsservern delas i allmänhet med servrarna från mellanleverantörer.

## Installations- och konfigurationssteg {#installation-and-configuration-steps-}

### Förutsättningar {#prerequisites}

* JDK på programservern.
* Åtkomst till en databasserver på programservern.
* Brandväggen är konfigurerad att öppna HTTP- (80) eller HTTPS-portar (443) till mittkällservern.

### Installera och konfigurera (driftsättning från mellanleverantörer) {#installing-and-configuring--mid-sourcing-deployment-}

Se [Mid-sourcing-servern](../../installation/using/mid-sourcing-server.md).
