---
title: Värdbaserade modeller
seo-title: Värdbaserade modeller
description: Värdbaserade modeller
seo-description: null
page-status-flag: never-activated
uuid: a9e035d9-326b-4e14-8f05-a22fe38d172b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 3175b9ab-e305-4f19-8267-d6172fa07a2a
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 3%

---


# Värdbaserade modeller{#hosting-models}

Adobe Campaign erbjuder ett urval av tre värdmodeller som ger flexibilitet och frihet att välja den bästa modellen, eller modeller som passar företagets behov.

>[!NOTE]
>
>För värdmiljöer i Adobe kan huvudinstallations- och konfigurationssteg bara utföras av Adobe, som att konfigurera servern och anpassa instanskonfigurationsfiler. Mer information om de viktigaste skillnaderna mellan distributionslägen finns i [den här artikeln](https://helpx.adobe.com/se/campaign/kb/acc-on-prem-vs-hosted.html).

* **Managed Services (värd)**

   Adobe Campaign kan distribueras som en hanterad tjänst: alla komponenter i Adobe Campaign, inklusive användargränssnittet, körningsmotorn och kundens Campaign-databas är helt värdbaserade för Adobe, inklusive e-postkörning, spegelsidor, spårningsserver och externt riktade webbkomponenter som sidan/inställningscentret för att avbryta prenumerationen och landningssidor. Adobe allokerar upp till tre instanser i molnet - utveckling, testning/scen och produktion. Installations- och konfigurationsstegen för den här värdmodellen beskrivs [i det här avsnittet](../../installation/using/hosted-model.md).

   ![](assets/deployment_hosted.png)

* **Lokalt**

   Adobe Campaign kan driftsättas lokalt: alla komponenter i Adobe Campaign, inklusive användargränssnittet, körningsmotorn och databasen finns på plats i kundens datacenter. I den här distributionsmodellen hanterar kunden alla uppdateringar och uppgraderingar av programvara och maskinvara, och en dedikerad databasadministratör måste utföra underhålls- och optimeringsuppgifter för att säkerställa instanshanteringen i Campaign. Riktlinjer för driftsättning för lokala kunder presenteras [i det här avsnittet](../../installation/using/before-starting.md).

   ![](assets/deployment_onpremise.png)

* **Hybrid**

   När Adobe Campaign-lösningen driftsätts som en hybridmodell finns den på plats hos kunden och körningshanteringen levereras som en molntjänst av Adobe. Adobe Campaign marknadsinstans installeras inuti en kunds brandvägg, så personligt identifierbar information (PII) finns kvar internt och endast data som krävs för att personalisera e-post skickas till molnet för e-postkörning. Körningsinstansen, som finns i molnet, tar emot förfrågningar från instansen On-Premise om att leverera e-postmeddelanden. Den här instansen personaliserar alla e-postmeddelanden och levererar dem. Inga data av något slag lagras permanent i molnet. Installations- och konfigurationsstegen för den här värdmodellen beskrivs [i det här avsnittet](../../installation/using/hybrid-model.md).

   ![](assets/deployment_hybrid.png)

