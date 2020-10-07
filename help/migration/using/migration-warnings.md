---
title: Migreringsvarningar
seo-title: Migreringsvarningar
description: Migreringsvarningar
seo-description: null
page-status-flag: never-activated
uuid: 35361471-881c-4aaf-a57b-ed7e89a97eae
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-overview
discoiquuid: 1fa1fe0f-c392-413a-9fa0-d1b4e10e2e5e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 6%

---


# Migreringsvarningar{#migration-warnings}

* Migreringsprocessen är reserverad för expertanvändare. Du måste få hjälp av minst en databasexpert, en systemadministratör och en programutvecklare från Adobe Campaign.
* Innan du startar migreringen bör du kontrollera att de system och systemkomponenter du använder är kompatibla med v7. Se [kompatibilitetsmatrisen](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html).
* Om du använder Adobe Campaign Cloud Messaging (tidigare mellanlagring) kontaktar du Adobe Campaign innan du påbörjar hela migreringsprocessen.
* Innan du startar en migreringsprocess **måste** du säkerhetskopiera dina data.
* Det kan ta flera dagar innan migreringen är klar.
* Adobe Campaign v7 är striktare än version 5.11 och 6.02 vad gäller konfiguration. Detta gäller främst för att undvika problem som till exempel dataskador och för att bevara databasens dataintegritet. Följaktligen kanske vissa funktioner som erbjuds i v5.11 och v6.02 inte längre fungerar i v7 och därför behöver anpassas efter migreringen. Innan du sätter något i produktion rekommenderar vi att du systematiskt testar alla konfigurationer, särskilt arbetsflöden som är nödvändiga för att använda Adobe Campaign.

>[!NOTE]
>
>Du måste också läsa avsnittet [Innan du startar migreringen](../../migration/using/before-starting-migration.md) .

