---
solution: Campaign Classic
product: campaign
title: Innan du startar migreringen
description: Innan du startar migreringen
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 1%

---


# Innan du startar migreringen{#before-starting-migration}

>[!NOTE]
>
>I det här dokumentet ges kommandon som är länkade till databasen som exempel. Dessa kan variera beroende på konfiguration. Kontakta databasadministratören.

## Varningar {#warnings}

* Migreringsprocessen får endast utföras av expertanvändare. Du måste få hjälp av minst en databasexpert, en systemadministratör och en programutvecklare från Adobe Campaign.
* Innan du startar migreringen bör du kontrollera att de system och systemkomponenter du använder är kompatibla med v7. Se [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md).
* Om du använder Adobe Campaign Cloud Messaging (mellanlagring) kontaktar du Adobe innan du påbörjar hela migreringsprocessen.
* Innan du startar en migreringsprocess måste du **säkerhetskopiera dina data.**
* Det kan ta flera dagar innan migreringen är klar.
* Adobe Campaign v7 är striktare än version 5.11 och 6.02 vad gäller konfiguration. Detta gäller främst för att undvika problem som till exempel dataskador och för att bevara databasens dataintegritet. Följaktligen kanske vissa funktioner som erbjuds i v5.11 och v6.02 inte längre fungerar i v7 och därför behöver anpassas efter migreringen. Innan du sätter något i produktion rekommenderar vi att du systematiskt testar alla konfigurationer, särskilt arbetsflöden som är nödvändiga för att använda Adobe Campaign.

### Installerad version {#installed-version}

Innan du migrerar bör du installera den senaste versionen av den aktuella versionen som du använder.

Kontrollera versionen på servern genom att gå till menyn **[!UICONTROL Help> About]** på klientkonsolen med kommandot **nlserver pdump**.

### Säkerhetskopiering av data {#data-backup}

Innan du startar en migreringsprocess måste du **säkerhetskopiera dina data.**

### Miljö {#environment}

* Det går inte att ändra databasmotortypen (DBMS). Du kan till exempel inte växla från en PostgreSQL-motor till en Oraclena motor. Du kan dock växla från en Oracle 8-motor till en Oracle 10-motor.
* Det går inte att gå från en icke-Unicode-databas till en Unicode-databas.

### Rekommendation {#recommendation}

Eftersom migreringsproceduren är känslig rekommenderar vi att du läser det här dokumentet noggrant innan du startar proceduren.

## Migreringssteg {#migration-steps}

Migreringsproceduren måste utföras på **alla**-servrar och i en viss ordning.

* När det gäller en **fristående plattform** (endatorläge) migreras programmet i sin helhet.
* För en **standardplattform** (enterprise) är migreringsstegen följande:

   1. Migrera marknadsföringsservern.
   1. Migrera e-postservern (mta).
   1. Migrera omdirigerings- och spårningsservrar (Apache/IIS).

* När det gäller en **Cloud Messaging-plattform** är körningsservrarna värdbaserade på Adobe Campaign. Kontakta Adobe Campaign för att koordinera migreringen mellan olika servrar.
* För en **Power Booster- eller Power Cluster-plattform** är migreringsstegen följande:

   1. Migrera omdirigerings- och spårningsservrar (Apache/IIS).
   1. Migrera Power Booster-/klusterservrarna.
   1. Migrera marknadsföringsservern.

## Användarlösenord {#user-passwords}

I v7 måste operatoranslutningen **internal** och **admin** vara skyddad med ett lösenord. Vi rekommenderar att du tilldelar lösenord till dessa konton och alla operatörskonton, **före migrering**. Om du inte har angett något lösenord för **internal** kommer du inte att kunna ansluta. Om du vill tilldela ett lösenord till **internal** anger du följande kommando:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>Lösenordet för **internal** måste vara identiskt för alla spårningsservrar. Mer information finns i avsnitten [Intern identifierare](../../installation/using/campaign-server-configuration.md#internal-identifier) och [Behörigheter](../../platform/using/access-management.md).

