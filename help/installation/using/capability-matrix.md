---
solution: Campaign Classic
product: campaign
title: Funktionsmatris för Campaign On-lokalt, Hybrid och Hosted
description: Lär dig de viktigaste skillnaderna mellan värdbaserade och lokala distributioner
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 18%

---


# Funktionsmatris {#capability-matrix-per-model}

Med Adobe Campaign Classic medföljer en uppsättning moduler och alternativ. Vilka moduler som är tillgängliga och hur de används beror på vilken typ av installation du har. I den här artikeln finns mer information om de viktigaste skillnaderna när det gäller vissa funktioner mellan fullständigt värdbaserade (Managed Services) och anläggningsdistributioner.

På den här sidan visas de viktigaste skillnaderna mellan värdbaserade (Managed Services) och lokala distributioner. Specifikationer för hybriddriftsättningar beror på vilka element som ligger hos Adobe och hos er.

De olika värdmodellerna finns [i det här avsnittet](../../installation/using/hosting-models.md).

## Tillgänglighet per distributionsmodell {#capability-matrix}

| Funktion | Värdbaserad | Hybrid | Lokalt | Detaljer |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Konfigurera Campaign-server | On-demand | Tillgänglig | Tillgänglig | [Läs mer](../../installation/using/the-server-configuration-file.md) |
| BCC för e-post | On-demand | On-demand | Tillgänglig | [Läs mer](../../installation/using/email-archiving.md) |
| Hantera körningsinstans för Message Center | On-demand | On-demand | Tillgänglig | [Läs mer](../../message-center/using/about-transactional-messaging.md) |
| Hantera en plattform med flera leverantörer | On-demand | On-demand | Tillgänglig | [Läs mer](../../installation/using/mid-sourcing-server.md) |
| Inkorgsåtergivning via Litmus | On-demand | On-demand | Tillgänglig | [Läs mer](../../delivery/using/inbox-rendering.md) |
| Integrera med IMS (Adobe ID) | On-demand | On-demand | On-demand | [Läs mer](../../integrations/using/about-adobe-id.md) |
| Kryptera/dekryptera data för filöverföringar | On-demand | Tillgänglig | Tillgänglig | [Läs mer](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Zippa/zippa upp filer | On-demand | Tillgänglig | Tillgänglig | [Läs mer](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| Delegering av domännamn | On-demand | On-demand | Inte tillgängligt | [Läs mer](https://helpx.adobe.com/se/campaign/kb/domain-name-delegation.html) |
| Installera SpamAssassin | On-demand | Tillgänglig | Tillgänglig | [Läs mer](../../delivery/using/spamassassin.md) |
| Åtkomst till leveransrapporter | Tillgänglig | On-demand | Tillgänglig | [Läs mer](../../delivery/using/monitoring-deliverability.md) |
| Konfigurerar LDAP-autentisering | Inte tillgängligt | Tillgänglig | Tillgänglig | [Läs mer](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data. [Läs mer](../../installation/using/about-fda.md)

>[!CAUTION]
>
>Åtkomst till en extern databas via FDA är endast möjlig för anläggningsinstallationer eller hybridinstallationer, med undantag för [Snowflake-anslutaren](../../installation/using/configure-fda-snowflake.md).


**Se även**

* [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md)
* [Versionsinformation](../../rn/using/latest-release.md)
* [Campaign Classic-uppgraderingar](../../rn/using/rn-overview.md)
* [Inaktuella och borttagna funktioner](../../rn/using/deprecated-features.md)
* [Gold Standard-versioner](../../rn/using/gold-standard.md)
* [Gold Standard](https://helpx.adobe.com/se/campaign/kb/gold-standard.html)
