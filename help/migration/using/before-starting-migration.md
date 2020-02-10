---
title: Innan du startar migreringen
seo-title: Innan du startar migreringen
description: Innan du startar migreringen
seo-description: null
page-status-flag: never-activated
uuid: b9325510-2fa5-4be4-9cf0-f37232bbbd8c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: d8877378-fb43-4f32-91c6-60f2f788f916
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f460c79a763c6a207656c54351a4c685f2a78a03

---


# Innan du startar migreringen{#before-starting-migration}

>[!NOTE]
>
>I det här dokumentet ges kommandon som är länkade till databasen som exempel. Dessa kan variera beroende på konfiguration. Kontakta databasadministratören.

## Varningar {#warnings}

### Installerad version {#installed-version}

Innan du migrerar bör du installera den senaste versionen av den aktuella versionen som du använder.

Kontrollera versionen på servern genom att gå till **[!UICONTROL Help> About]** menyn på klientkonsolen med **kommandot nlserver pdump** .

### Säkerhetskopiering av data {#data-backup}

Innan du startar en migreringsprocess **måste** du säkerhetskopiera dina data.

### Miljö {#environment}

* Det går inte att ändra databasmotortypen (DBMS). Du kan till exempel inte växla från en PostgreSQL-motor till en Oracle-motor. Du kan dock växla från en Oracle 8-motor till en Oracle 10-motor.
* Det går inte att gå från en icke-Unicode-databas till en Unicode-databas.

### Rekommendation {#recommendation}

Eftersom migreringsproceduren är särskilt känslig rekommenderar vi att du läser detta dokument noggrant innan du börjar proceduren.

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

>[!NOTE]
>
>Kommunikation mellan en v6.02-marknadsföringsserver och en v7 Cloud Messaging- eller Power Booster-/Cluster-server är möjlig. Om du ändå bestämmer dig för att behålla din v6.02-marknadsföringsserver måste den uppdateras med den senaste v6.02-versionen innan du migrerar till Cloud Messaging eller Power Booster/Cluster.

## Användarlösenord {#user-passwords}

I v7 måste **intern** anslutning och **administratörsanslutning** skyddas av ett lösenord. Vi rekommenderar att du tilldelar lösenord till dessa konton och alla operatörskonton **före migreringen**. Om du inte har angett ett lösenord för **intern** anslutning kan du inte ansluta. Om du vill tilldela ett lösenord till **internt** anger du följande kommando:

```
nlserver config -internalpassword
```

>[!CAUTION]
>
>Det **interna** lösenordet måste vara identiskt för alla spårningsservrar. Mer information finns i avsnitten [Intern identifierare](../../installation/using/campaign-server-configuration.md#internal-identifier) och [Om behörigheter](../../platform/using/access-management.md#about-permissions) .

