---
product: campaign
title: Innan du startar migreringen
description: Innan du startar migreringen
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: d666bc0b-596a-4908-9364-7df5bb8d68d0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

---

# Förhandskrav{#before-starting-migration}



På den här sidan visas specifika steg som ska utföras innan migreringsprocessen startas. Du måste även referera till [den här sidan](about-migration.md) för mer vägledning.

>[!NOTE]
>
>I det här dokumentet anges kommandona som exempel. De kan variera beroende på din konfiguration.

1. Kontrollera din Adobe Campaign-version: innan du migrerar ska du installera den senaste versionen av den aktuella versionen som du använder.
1. Säkerhetskopiera era data.
1. Kontrollera din miljö: du kan inte ändra databasmotorsystemet (DBMS). Du kan till exempel inte växla från en PostgreSQL-motor till en Oraclena motor. Du kan dock växla till den senaste versionen av databasmotorn. Observera att det inte går att gå från en icke-Unicode-databas till en Unicode-databas.

## Migreringssteg {#migration-steps}

Migreringsförfarandet måste genomföras på **alla** servrar och i en viss ordning.

* I fallet med **fristående plattform** (endatorläge) migreras programmet i sin helhet.
* I fallet med **standardplattform** (enterprise) är migreringsstegen följande:

   1. Migrera marknadsföringsservern.
   1. Migrera e-postservern (mta).
   1. Migrera omdirigerings- och spårningsservrar (Apache/IIS).

* I fallet med **Plattformen Cloud Messaging**, är exekveringsservrarna på Adobe Campaign. Kontakta Adobe Campaign för att koordinera migreringen mellan olika servrar.
* I fallet med **Power Booster- eller Power Cluster-plattform**&#x200B;är migreringsstegen följande:

   1. Migrera omdirigerings- och spårningsservrar (Apache/IIS).
   1. Migrera Power Booster-/klusterservrarna.
   1. Migrera marknadsföringsservern.

## Lösenord {#user-passwords}

In v7, **internal** och **admin** -operatoranslutningen måste skyddas av ett lösenord. Vi rekommenderar starkt att du tilldelar lösenord till dessa konton och alla operatörskonton, **före migrering**. Om du inte har angett något lösenord för **internal** kommer du inte att kunna ansluta. Tilldela ett lösenord till **internal** anger du följande kommando:

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>The **internal** lösenordet måste vara identiskt för alla spårningsservrar. Mer information finns i [Intern identifierare](../../installation/using/configuring-campaign-server.md#internal-identifier) och [Behörigheter](../../platform/using/access-management.md) -avsnitt.
