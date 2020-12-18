---
solution: Campaign Classic
product: campaign
title: Driftsättning via mid-sourcing
description: Driftsättning via mid-sourcing
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 1%

---


# Driftsättning via mid-sourcing{#mid-sourcing-deployment}

Denna konfiguration är en optimal mellanlösning mellan en värdkonfiguration (ASP) och internalisering. Utomvända körningskomponenter utförs på en&quot;server med mellanleverantörer&quot; på Adobe Campaign.

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

### Installera och konfigurera (distribuering från mellanleverantörer) {#installing-and-configuring--mid-sourcing-deployment-}

Se [Mid-sourcing-server](../../installation/using/mid-sourcing-server.md).
