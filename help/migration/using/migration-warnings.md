---
solution: Campaign Classic
product: campaign
title: Migreringsvarningar
description: Migreringsvarningar
audience: migration
content-type: reference
topic-tags: migration-overview
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 3%

---


# Migreringsvarningar{#migration-warnings}

* Migreringsprocessen är reserverad för expertanvändare. Du måste få hjälp av minst en databasexpert, en systemadministratör och en programutvecklare från Adobe Campaign.
* Innan du startar migreringen bör du kontrollera att de system och systemkomponenter du använder är kompatibla med v7. Se [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md).
* Om du använder Adobe Campaign Cloud Messaging (tidigare mellanlagring) kontaktar du Adobe Campaign innan du påbörjar hela migreringsprocessen.
* Innan du startar en migreringsprocess måste du **säkerhetskopiera dina data.**
* Det kan ta flera dagar innan migreringen är klar.
* Adobe Campaign v7 är striktare än version 5.11 och 6.02 vad gäller konfiguration. Detta gäller främst för att undvika problem som till exempel dataskador och för att bevara databasens dataintegritet. Följaktligen kanske vissa funktioner som erbjuds i v5.11 och v6.02 inte längre fungerar i v7 och därför behöver anpassas efter migreringen. Innan du sätter något i produktion rekommenderar vi att du systematiskt testar alla konfigurationer, särskilt arbetsflöden som är nödvändiga för att använda Adobe Campaign.

>[!NOTE]
>
>Du måste också läsa avsnittet [Innan du startar migreringen](../../migration/using/before-starting-migration.md).

