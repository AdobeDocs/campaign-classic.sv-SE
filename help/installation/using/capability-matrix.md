---
product: campaign
title: Funktionsmatris för Campaign On-lokalt, Hybrid och Hosted
description: Lär dig de viktigaste skillnaderna mellan värdbaserade och lokala distributioner
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 18%

---

# Kapacitetsmatris per modell{#capability-matrix-per-model}

Med Adobe Campaign Classic medföljer en uppsättning moduler och alternativ. Vilka moduler som är tillgängliga och hur de används beror på vilken typ av installation du har. I den här artikeln finns mer information om de viktigaste skillnaderna när det gäller vissa funktioner mellan fullständigt värdbaserade (Managed Services) och anläggningsdistributioner.

På den här sidan visas de viktigaste skillnaderna mellan värdbaserade (Managed Services) och lokala distributioner. Specifikationer för hybriddriftsättningar beror på vilka element som ligger hos Adobe och hos er.

De olika värdmodellerna introduceras [i det här avsnittet](../../installation/using/hosting-models.md).

## Tillgänglighet per distributionsmodell {#capability-matrix}

| Funktion | Värdbaserad | Hybrid | Lokalt | Detaljer |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Konfigurera Campaign-servern | On-demand | Tillgänglig | Tillgänglig | [Läs mer](../../installation/using/the-server-configuration-file.md) |
| BCC för e-post | On-demand | On-demand | Tillgänglig | [Läs mer](../../installation/using/email-archiving.md) |
| Hantera körningsinstans för Message Center | On-demand | On-demand | Tillgänglig | [Läs mer](../../message-center/using/about-transactional-messaging.md) |
| Hantera en plattform med flera leverantörer | On-demand | On-demand | Tillgänglig | [Läs mer](../../installation/using/mid-sourcing-server.md) |
| Inkorgsåtergivning via Litmus | On-demand | On-demand | Tillgänglig | [Läs mer](../../delivery/using/inbox-rendering.md) |
| Integrera med IMS (Adobe ID) | On-demand | On-demand | On-demand | [Läs mer](../../integrations/using/about-adobe-id.md) |
| Kryptera/dekryptera data för filöverföringar | On-demand | Tillgänglig | Tillgänglig | [Läs mer](../../platform/using/unzip-decrypt.md) |
| Zippa/zippa upp filer | On-demand | Tillgänglig | Tillgänglig | [Läs mer](../../platform/using/unzip-decrypt.md) |
| Delegering av domännamn | On-demand | On-demand | Inte tillgängligt | [Läs mer](https://helpx.adobe.com/se/campaign/kb/domain-name-delegation.html) |
| Installera SpamAssassin | On-demand | Tillgänglig | Tillgänglig | [Läs mer](../../delivery/using/spamassassin.md) |
| Åtkomst till leveransrapporter | Tillgänglig | On-demand | Tillgänglig | [Läs mer](../../delivery/using/monitoring-deliverability.md) |
| Konfigurerar LDAP-autentisering | Inte tillgängligt | Tillgänglig | Tillgänglig | [Läs mer](../../installation/using/connecting-through-ldap.md) |


## Åtkomst till federerade data{#fda}

Adobe Campaign tillhandahåller alternativet **FDA (Federated Data Access**) för att bearbeta information som lagras i en eller flera externa databaser: kan du få åtkomst till externa data utan att ändra datastrukturen i Adobe Campaign. [Läs mer](../../installation/using/about-fda.md)

>[!CAUTION]
>
>Åtkomst till en extern databas via FDA är bara möjlig för lokala eller hybridinstallationer, förutom med [Snowflake-anslutaren](../../installation/using/configure-fda-snowflake.md).


**Se även**

* [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md)
* [Versionsinformation](../../rn/using/latest-release.md)
* [Campaign Classic-uppgraderingar](../../rn/using/rn-overview.md)
* [Inaktuella och borttagna funktioner](../../rn/using/deprecated-features.md)
* [[!DNL Gold Standard]-versioner ](../../rn/using/gold-standard.md)
* [[!DNL Gold Standard] program](../../rn/using/gs-overview.md)
