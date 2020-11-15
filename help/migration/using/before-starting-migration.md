---
title: Innan du startar migreringen
description: Innan du startar migreringen
page-status-flag: never-activated
uuid: b9325510-2fa5-4be4-9cf0-f37232bbbd8c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: d8877378-fb43-4f32-91c6-60f2f788f916
translation-type: tm+mt
source-git-commit: 99d766cb6234347ea2975f3c08a6ac0496619b41
workflow-type: tm+mt
source-wordcount: '524'
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
* Innan du startar en migreringsprocess **måste** du säkerhetskopiera dina data.
* Det kan ta flera dagar innan migreringen är klar.
* Adobe Campaign v7 är striktare än version 5.11 och 6.02 vad gäller konfiguration. Detta gäller främst för att undvika problem som till exempel dataskador och för att bevara databasens dataintegritet. Följaktligen kanske vissa funktioner som erbjuds i v5.11 och v6.02 inte längre fungerar i v7 och därför behöver anpassas efter migreringen. Innan du sätter något i produktion rekommenderar vi att du systematiskt testar alla konfigurationer, särskilt arbetsflöden som är nödvändiga för att använda Adobe Campaign.

### Installerad version {#installed-version}

Innan du migrerar bör du installera den senaste versionen av den aktuella versionen som du använder.

Kontrollera versionen på servern genom att gå till **[!UICONTROL Help> About]** menyn på klientkonsolen med **kommandot nlserver pdump** .

### Säkerhetskopiering av data {#data-backup}

Innan du startar en migreringsprocess **måste** du säkerhetskopiera dina data.

### Miljö {#environment}

* Det går inte att ändra databasmotortypen (DBMS). Du kan till exempel inte växla från en PostgreSQL-motor till en Oracle-motor. Du kan dock växla från en Oracle 8-motor till en Oracle 10-motor.
* Det går inte att gå från en icke-Unicode-databas till en Unicode-databas.

### Rekommendation {#recommendation}

Eftersom migreringsproceduren är känslig rekommenderar vi att du läser det här dokumentet noggrant innan du startar proceduren.

## Migreringssteg {#migration-steps}

Migreringsproceduren måste utföras på **alla** servrar och i en viss ordning.

* När det gäller en **fristående plattform** (endatorläge) migreras programmet i sin helhet.
* När det gäller en **standardplattform** (enterprise) är migreringsstegen följande:

   1. Migrera marknadsföringsservern.
   1. Migrera e-postservern (mta).
   1. Migrera omdirigerings- och spårningsservrar (Apache/IIS).

* När det gäller en **Cloud Messaging-plattform** finns körningsservrarna på Adobe Campaign. Kontakta Adobe Campaign för att koordinera migreringen mellan olika servrar.
* För en **Power Booster- eller Power Cluster-plattform**&#x200B;är migreringsstegen följande:

   1. Migrera omdirigerings- och spårningsservrar (Apache/IIS).
   1. Migrera Power Booster-/klusterservrarna.
   1. Migrera marknadsföringsservern.

## Användarlösenord {#user-passwords}

I v7 måste **intern** anslutning och **administratörsanslutning** skyddas av ett lösenord. Vi rekommenderar att du tilldelar lösenord till dessa konton och alla operatörskonton **före migreringen**. Om du inte har angett ett lösenord för **intern** anslutning kan du inte ansluta. Om du vill tilldela ett lösenord till **internt** anger du följande kommando:

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>Det **interna** lösenordet måste vara identiskt för alla spårningsservrar. Mer information finns i avsnitten [Intern identifierare](../../installation/using/campaign-server-configuration.md#internal-identifier) och [Om behörigheter](../../platform/using/access-management.md#about-permissions) .

