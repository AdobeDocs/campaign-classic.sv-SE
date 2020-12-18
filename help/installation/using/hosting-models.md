---
solution: Campaign Classic
product: campaign
title: Värdbaserade modeller
description: Upptäck värdmodeller för Campaign
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 1%

---


# Värdbaserade modeller{#hosting-models}

Adobe Campaign erbjuder ett urval av tre värdmodeller som ger flexibilitet och frihet att välja den bästa modellen, eller modeller som passar företagets behov.

>[!NOTE]
>
>För värdmiljöer i Adobe kan huvudinstallations- och konfigurationssteg bara utföras av Adobe, som att konfigurera servern och anpassa instanskonfigurationsfiler. Mer information om de viktigaste skillnaderna mellan distributionslägen finns på [den här sidan](../../installation/using/capability-matrix.md).

* **Managed Services (värd)**

   Adobe Campaign kan distribueras som en hanterad tjänst: alla komponenter i Adobe Campaign, inklusive användargränssnittet, körningsmotorn och kundens Campaign-databas är helt värdbaserade för Adobe, inklusive e-postkörning, spegelsidor, spårningsserver och externt riktade webbkomponenter som sidan/inställningscentret för att avbryta prenumerationen och landningssidor. Adobe allokerar upp till tre instanser i molnet - utveckling, testning/scen och produktion. Installations- och konfigurationsstegen för den här värdmodellen visas [i det här avsnittet](../../installation/using/hosted-model.md).

   ![](assets/deployment_hosted.png)

* **Lokalt**

   Adobe Campaign kan driftsättas lokalt: alla komponenter i Adobe Campaign, inklusive användargränssnittet, körningsmotorn och databasen finns på plats i kundens datacenter. I den här distributionsmodellen hanterar kunden alla uppdateringar och uppgraderingar av programvara och maskinvara, och en dedikerad databasadministratör måste utföra underhålls- och optimeringsuppgifter för att säkerställa instanshanteringen i Campaign. Riktlinjer för driftsättning för lokala kunder presenteras [i det här avsnittet](../../installation/using/before-starting.md).

   ![](assets/deployment_onpremise.png)

* **Hybrid**

   När Adobe Campaign-lösningen driftsätts som en hybridmodell finns den på plats hos kunden och körningshanteringen levereras som en molntjänst av Adobe. Adobe Campaign marknadsinstans installeras inuti en kunds brandvägg, så personligt identifierbar information (PII) finns kvar internt och endast data som krävs för att personalisera e-post skickas till molnet för e-postkörning. Körningsinstansen, som finns i molnet, tar emot förfrågningar från instansen On-Premise om att leverera e-postmeddelanden. Den här instansen personaliserar alla e-postmeddelanden och levererar dem. Inga data av något slag lagras permanent i molnet. Installations- och konfigurationsstegen för den här värdmodellen visas [i det här avsnittet](../../installation/using/hybrid-model.md).

   ![](assets/deployment_hybrid.png)

