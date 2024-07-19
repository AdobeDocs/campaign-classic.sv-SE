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



På den här sidan visas specifika steg som ska utföras innan migreringsprocessen startas. Du måste även läsa [den här sidan](about-migration.md) för mer vägledning.

>[!NOTE]
>
>I det här dokumentet anges kommandona som exempel. De kan variera beroende på din konfiguration.

1. Kontrollera din Adobe Campaign-version: innan du migrerar ska du installera den senaste versionen av den aktuella versionen som du använder.
1. Säkerhetskopiera era data.
1. Kontrollera din miljö: du kan inte ändra databasmotorsystemet (DBMS). Du kan till exempel inte växla från en PostgreSQL-motor till en Oraclena motor. Du kan dock växla till den senaste versionen av databasmotorn. Observera att det inte går att gå från en icke-Unicode-databas till en Unicode-databas.

## Migreringssteg {#migration-steps}

Migreringsproceduren måste utföras på **alla**-servrar och i en viss ordning.

* När det gäller en **fristående plattform** (endatorläge) migreras programmet i sin helhet.
* När det gäller en **standardplattform** (enterprise) är migreringsstegen följande:

   1. Migrera marknadsföringsservern.
   1. Migrera e-postservern (mta).
   1. Migrera omdirigerings- och spårningsservrar (Apache/IIS).

* Om det är en **Cloud Messaging-plattform** är körningsservrarna på Adobe Campaign. Kontakta Adobe Campaign för att koordinera migreringen mellan olika servrar.
* För en **Power Booster- eller Power Cluster-plattform** är migreringsstegen följande:

   1. Migrera omdirigerings- och spårningsservrar (Apache/IIS).
   1. Migrera Power Booster-/klusterservrarna.
   1. Migrera marknadsföringsservern.

## Lösenord {#user-passwords}

I v7 måste operatoranslutningen **internal** och **admin** skyddas av ett lösenord. Vi rekommenderar att du tilldelar lösenord till dessa konton och alla operatörskonton, **före migrering**. Om du inte har angett något lösenord för **internal** kan du inte ansluta. Om du vill tilldela ett lösenord till **internal** anger du följande kommando:

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>Lösenordet **internal** måste vara identiskt för alla spårningsservrar. Mer information finns i avsnitten [Intern identifierare](../../installation/using/configuring-campaign-server.md#internal-identifier) och [Behörigheter](../../platform/using/access-management.md).
