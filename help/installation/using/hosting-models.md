---
solution: Campaign Classic
product: campaign
title: Värdbaserade modeller
description: Upptäck värdmodeller för Campaign
feature: Overview
role: Architect
level: Beginner
translation-type: tm+mt
source-git-commit: 09bd634142f643206c38ac5f881302a5d489ecaf
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 2%

---


# Värdbaserade modeller{#hosting-models}

Adobe Campaign erbjuder ett urval av tre värdmodeller som ger flexibilitet och frihet att välja den bästa modellen, eller modeller som passar företagets behov.

>[!NOTE]
>
>För värdmiljöer i Adobe kan huvudinstallations- och konfigurationssteg bara utföras av Adobe, som att konfigurera servern och anpassa instanskonfigurationsfiler. Mer information om de viktigaste skillnaderna mellan distributionslägen finns på [den här sidan](../../installation/using/capability-matrix.md).

## Managed Services / Hosted

Adobe Campaign kan distribueras som en hanterad tjänst: alla komponenter i Adobe Campaign, inklusive användargränssnittet, körningsmotorn och kundens Campaign-databas är helt värdbaserade för Adobe, inklusive e-postkörning, spegelsidor, spårningsserver och externt riktade webbkomponenter som sidan/inställningscentret för att avbryta prenumerationen och landningssidor.

![](assets/deployment_hosted.png)

Som värdkund utförs de flesta installations- och konfigurationsstegen av Adobe. Du kan anpassa implementeringen i följande avsnitt:

* Konfigurera spårnings- och spegelsidiga URL:er per varumärke. För transaktionsmeddelanden, se [det här avsnittet](../../message-center/using/configuring-multibranding.md).
* Installera klientkonsolen: hänvisa [till detta avsnitt](../../installation/using/installing-the-client-console.md).
* Läs mer om verktyg för slutprodukter och bästa praxis i [den detaljerade dokumentationen](../../delivery/using/about-deliverability.md).
* Konfigurera kampanjalternativ: hänvisa [till detta avsnitt](../../installation/using/configuring-campaign-options.md).
* Konfigurera CRM-anslutningar: hänvisa [till detta avsnitt](../../platform/using/crm-connectors.md).

## Lokalt

Adobe Campaign kan driftsättas lokalt: alla komponenter i Adobe Campaign, inklusive användargränssnittet, körningsmotorn och databasen finns på plats i kundens datacenter. I den här distributionsmodellen hanterar kunden alla uppdateringar och uppgraderingar av programvara och maskinvara, och en dedikerad databasadministratör måste utföra underhålls- och optimeringsuppgifter för att säkerställa instanshanteringen i Campaign.

![](assets/deployment_onpremise.png)

Innan du börjar driftsätta Campaign Classic som en lokal kund måste du uppfylla följande krav och rekommendationer:

* Läs igenom [Kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md) som visar alla versioner av de system och komponenter som stöds för Adobe Campaign.
* Beroende på din miljö kan du läsa [förutsättningarna för Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) och [förutsättningarna för Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md).
* Läs rekommendationer om databasmotorer [i det här avsnittet](../../installation/using/database.md).
* Kontrollera att de nödvändiga lagren för databasåtkomst är installerade på servern och tillgängliga från Adobe Campaign-kontot. [Läs mer](../../installation/using/application-server.md).
* Konfigurera dina nätverk eftersom vissa processer behöver kommunicera med andra eller för att få åtkomst till nätverket och Internet. Detta innebär att vissa TCP-portar måste vara öppna för dessa processer. [Läs ](../../installation/using/network-configuration.md) mer om kraven för nätverkskonfiguration.
* Läs [Checklista för kampanjsäkerhet och sekretess](https://helpx.adobe.com/se/campaign/kb/acc-security.html).
* Kontrollera allmänna riktlinjer för beräkning av maskinvarukrav för lokal distribution [i den här artikeln](https://helpx.adobe.com/se/campaign/kb/hardware-sizing-guide.html).

## Hybrid

När Adobe Campaign-lösningen driftsätts som en hybridmodell finns den på plats hos kunden och körningshanteringen levereras som en molntjänst av Adobe. Adobe Campaign marknadsinstans installeras inuti en kunds brandvägg, så personligt identifierbar information (PII) finns kvar internt och endast data som krävs för att personalisera e-post skickas till molnet för e-postkörning. Körningsinstansen, som finns i molnet, tar emot förfrågningar från instansen On-Premise om att leverera e-postmeddelanden. Den här instansen personaliserar alla e-postmeddelanden och levererar dem. Inga data av något slag lagras permanent i molnet.

![](assets/deployment_hybrid.png)

Som hybrid-kund utförs de flesta installations- och konfigurationsstegen av Adobe. Du kan anpassa implementeringen i följande avsnitt:

* Konfigurera transaktionsmeddelanden: hänvisa [till detta avsnitt](../../message-center/using/transactional-messaging-architecture.md).
* Konfigurera spårnings- och spegelsidiga URL:er per varumärke. För transaktionsmeddelanden, se [det här avsnittet](../../message-center/using/configuring-multibranding.md).
* Installera klientkonsolen: hänvisa [till detta avsnitt](../../installation/using/installing-the-client-console.md).
* Installera inbyggda paket: hänvisa [till detta avsnitt](../../installation/using/installing-campaign-standard-packages.md).
* Leverans: konfigurera [MX-regler](../../installation/using/email-deliverability.md#mx-configuration) och [e-postformat](../../installation/using/email-deliverability.md#managing-email-formats). Läs mer om verktyg för slutprodukter och bästa praxis i [den detaljerade dokumentationen](../../delivery/using/about-deliverability.md).
* Konfigurera kampanjalternativ: hänvisa [till detta avsnitt](../../installation/using/configuring-campaign-options.md).
* Konfigurera en extern databas (Federated Data Access): hänvisa [till detta avsnitt](../../installation/using/about-fda.md).
* Konfigurerar CRM-anslutningar: hänvisa [till detta avsnitt](../../platform/using/crm-connectors.md).
* Om du vill veta mer om principer för distribuering från mellanleverantörer kan du läsa [i det här avsnittet](../../installation/using/mid-sourcing-deployment.md).
