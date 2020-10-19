---
title: Funktionsmatris för Campaign On-lokalt, Hybrid och Hosted
description: Lär dig de viktigaste skillnaderna mellan värdbaserade och lokala distributioner
page-status-flag: never-activated
uuid: d1c786a1-2691-4966-9108-059004050464
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 582f7ac6-cebe-4b47-8730-bbc16fd6b1bd
translation-type: tm+mt
source-git-commit: c2e1b4cf7051b7f1b9d5f2db0d9f51a733ca2abc
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 10%

---


# Kapacitetsmatris per värdmodell {#capability-matrix-per-model}

Med Adobe Campaign Classic medföljer en uppsättning moduler och alternativ. Vilka moduler som är tillgängliga och hur de används beror på vilken typ av installation du har. I den här artikeln finns mer information om de viktigaste skillnaderna när det gäller vissa funktioner mellan fullständigt värdbaserade (Managed Services) och anläggningsdistributioner.

På den här sidan visas de viktigaste skillnaderna mellan värdbaserade (Managed Services) och lokala distributioner. Specifikationer för hybriddriftsättningar beror på vilka element som ligger hos Adobe och hos er.

De olika värdmodellerna finns [i det här avsnittet](../../installation/using/hosting-models.md).

## Funktionsmatris{#capability-matrix}

| Funktion | Värdbaserad | Hybrid | Lokalt | Detaljer |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Konfigurera Campaign-server | On-demand | Tillgänglig | Tillgänglig | Konfigurationsfilen[för](../../installation/using/the-server-configuration-file.md)servern kan bara ändras av Adobe för värdkunder. |
| BCC för e-post | On-demand | On-demand | Tillgänglig | Kontakta er kontoansvarige för att aktivera e-post-BCC för värdbaserade och hybridbaserade arkitekturer. För lokala installationer följer du riktlinjerna i dokumentationen. [Läs mer](../../installation/using/email-archiving.md) |
| Hantera körningsinstans för Message Center | On-demand | On-demand | Tillgänglig | För värdbaserade distributioner kan vissa inställningar, som att skapa användare på körningsinstansen, endast utföras av Adobe. [Läs mer](../../message-center/using/about-transactional-messaging.md) |
| Hantera en plattform med flera leverantörer | On-demand | On-demand | Tillgänglig | Plattformar med mellanleverantörer som Adobe är värd för kan bara konfigureras av Adobe. |
| Inkorgsåtergivning via Litmus | On-demand | On-demand | Tillgänglig | Du behöver ett Litmus-konto. Du måste kontakta Adobe för att få den information som behövs eller utföra återgivningskonfigurationen för Inkorgen. [Läs mer](../../delivery/using/inbox-rendering.md) |
| Integrera med IMS (Adobe ID) | On-demand | On-demand | On-demand | IMS-etablering utförs av Adobe. Integreringen är en förutsättning för Adobe Experience Cloud-integreringar. [Läs mer](../../integrations/using/about-adobe-id.md) |
| Kryptera/dekryptera data för filöverföringar | On-demand | Tillgänglig | Tillgänglig | För- eller efterbearbetning av filer krävs att du installerar det nödvändiga verktyget på Adobe Campaign-servern. Värdkunder kan använda Campaign Control Panel. [Läs mer](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Zippa/zippa upp filer | On-demand - tillgängligt | Tillgänglig | För- eller efterbearbetning av filer krävs att du installerar det nödvändiga verktyget på Adobe Campaign-servern. Värdkunder kan använda Campaign Control Panel. [Läs mer](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Delegering av domännamn | On-demand | On-demand | Inte tillgängligt | [Läs mer](https://helpx.adobe.com/se/campaign/kb/domain-name-delegation.html) |
| Installera SpamAssassin | On-demand | Tillgänglig | Tillgänglig | Om du installerar SpamAssassin måste du redigera serverkonfigurationsfilen. [Läs mer](../../delivery/using/spamassassin.md) |
| Åtkomst till leveransrapporter | Tillgänglig | On-demand | Tillgänglig | I vissa hybriddistributioner går det inte att komma åt leveransrapporter från marknadsinstansen. |
| Konfigurerar LDAP-autentisering | Inte tillgängligt | Tillgänglig | Tillgänglig | LDAP-konfigurationen är bara möjlig för lokala eller hybridinstallationer. [Läs mer](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data. [Läs mer](../../platform/using/about-fda.md)

>[!CAUTION]
>
>Åtkomst till en extern databas via FDA är endast möjlig för anläggningsinstallationer eller hybridinstallationer, med undantag för [Snowflake-anslutaren](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake).


**Se även**

* [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md)
* [Versionsinformation](../../rn/using/latest-release.md)
* [Campaign Classic-uppgraderingar](../../rn/using/rn-overview.md)
* [Inaktuella och borttagna funktioner](../../rn/using/deprecated-features.md)
* [Gold Standard-versioner](../../rn/using/gold-standard.md)
* [Gold Standard-programmet](https://helpx.adobe.com/se/campaign/kb/gold-standard.html).
