---
product: campaign
title: Innan du startar migreringen
description: Innan du startar migreringen
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: 80cf56e330731237d5e7b394381b737f30f8b350
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# Förhandskrav{#before-starting-migration}

![](../../assets/v7-only.svg)

På den här sidan visas specifika steg som ska utföras innan migreringsprocessen startas. Du måste även referera till [den här sidan](about-migration.md) för mer vägledning.

>[!NOTE]
>
>I det här dokumentet anges kommandona som exempel. De kan variera beroende på din konfiguration.

1. Kontrollera din Adobe Campaign-version: innan du migrerar, installera den senaste versionen av den aktuella versionen som du använder.
1. Säkerhetskopiera era data.
1. Kontrollera din miljö: du kan inte ändra databasmotorsystemet (DBMS). Du kan till exempel inte växla från en PostgreSQL-motor till en Oraclena motor. Du kan dock växla till den senaste versionen av databasmotorn. Observera att det inte går att gå från en icke-Unicode-databas till en Unicode-databas.

## Migreringssteg {#migration-steps}

Migreringsförfarandet måste genomföras på **alla** servrar och i en viss ordning.

* Om **fristående plattform** (endatorläge) migreras programmet i sin helhet.
* Om **standardplattform** (enterprise) är migreringsstegen följande:

   1. Migrera marknadsföringsservern.
   1. Migrera e-postservern (mta).
   1. Migrera omdirigerings- och spårningsservrar (Apache/IIS).

* Om **Plattformen Cloud Messaging**, är exekveringsservrarna på Adobe Campaign. Kontakta Adobe Campaign för att koordinera migreringen mellan olika servrar.
* Om **Power Booster- eller Power Cluster-plattform**&#x200B;är migreringsstegen följande:

   1. Migrera omdirigerings- och spårningsservrar (Apache/IIS).
   1. Migrera Power Booster-/klusterservrarna.
   1. Migrera marknadsföringsservern.

## Användarlösenord {#user-passwords}

In v7, **internal** och **admin** -operatoranslutningen måste skyddas av ett lösenord. Vi rekommenderar starkt att du tilldelar lösenord till dessa konton och alla operatörskonton, **före migrering**. Om du inte har angett något lösenord för **internal** kommer du inte att kunna ansluta. Så här tilldelar du ett lösenord till **internal** anger du följande kommando:

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>The **internal** lösenordet måste vara identiskt för alla spårningsservrar. Mer information finns i [Intern identifierare](../../installation/using/configuring-campaign-server.md#internal-identifier) och [Behörigheter](../../platform/using/access-management.md) -avsnitt.
