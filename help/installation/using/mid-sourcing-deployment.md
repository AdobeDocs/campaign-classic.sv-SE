---
product: campaign
title: Driftsättning via mid-sourcing
description: Driftsättning via mid-sourcing
feature: Installation, Architecture, Deployment
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 8a4d7ef1-de5b-4aee-a527-1b74d987ba61
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 3%

---

# Driftsättning via mid-sourcing{#mid-sourcing-deployment}



Denna konfiguration är en optimal mellanlösning mellan en värdkonfiguration (ASP) och internalisering. Utomvända körningskomponenter utförs på en&quot;server med mellanleverantörer&quot; på Adobe Campaign.

>[!NOTE]
>
>Om du vill konfigurera den här typen av distribution måste du skaffa ett lämpligt alternativ. Kontrollera licensavtalet.

Allmän kommunikation mellan servrar och processer sker enligt följande schema:

![](assets/s_ncs_install_midsourcing.png)

* Modulerna för exekvering och studshantering är inaktiverade på instansen.
* Programmet är konfigurerat för att utföra meddelandekörning på en fjärrserver med &quot;mellanlagring&quot; som drivs med SOAP-anrop (via HTTP eller HTTPS).

## Funktioner {#features}

### Fördelar {#advantages}

* Förenklad serverkonfiguration: Kunden behöver inte konfigurera utåtriktade moduler (mta och inMail).
* Begränsad användning av bandbredd: Eftersom körningen utförs av servern med mellanlagring behövs bara tillräcklig bandbredd för att skicka personaliseringsdata till servern med mellanlagring.
* Hög tillgänglighet är inte längre något internt problem: Problemet skiftas till servern med mellanlagring (omdirigering, spegelsidor, exekveringsservrar osv.).
* Databasen lämnar inte företaget: Endast data som behövs för att samla ihop meddelandena skickas till servern med mellanlagring (HTTPS kan användas för detta).
* Den här typen av driftsättning kan vara en lösning för arkitekturer med stora volymer (många mottagare i databasen) och ett betydande leveransflöde.

### Nackdelar {#disadvantages}

* Visning av meddelandekörningsinformation och rapportfunktioner fördröjs något på grund av den tid det tar att få tillbaka information från mittkällservern.
* Undersökningar och webbformulär finns kvar på klientplattformen.

### Rekommenderad utrustning {#recommended-equipment}

* Programserver: 2 GHz-processor med fyra kärnor, 4 GB RAM-minne, program RAID 1 80 GB SATA-hårddisk.
* Databasserver: 3 GHz två processorer med fyra kärnor, minst 4 GB RAM, maskinvarubaserad RAID 10 SAS-hårddisk på 1 5 000 v/min, antalet beroende på databasens storlek och förväntade prestanda.

>[!NOTE]
>
>Omdirigering och hantering från mellanleverantörer är separata element, men spårningsservern kommer i allmänhet att delas med servrarna från mellanleverantörer.

## Installations- och konfigurationssteg {#installation-and-configuration-steps-}

### Förhandskrav {#prerequisites}

* JDK på programservern.
* Åtkomst till en databasserver på programservern.
* Brandväggen är konfigurerad att öppna HTTP- (80) eller HTTPS-portar (443) till mittkällservern.

### Installera och konfigurera (driftsättning från mellanleverantörer) {#installing-and-configuring--mid-sourcing-deployment-}

Se [Server för mellanleverantörer](../../installation/using/mid-sourcing-server.md).
