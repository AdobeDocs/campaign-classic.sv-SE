---
title: Migreringsmetod
seo-title: Migreringsmetod
description: Migreringsmetod
seo-description: null
page-status-flag: never-activated
uuid: 6b954d5b-cfa3-43c6-ac3d-da9185e9e9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-overview
discoiquuid: 3ac779a7-1f91-4c1c-a439-10d01697326a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# Migreringsmetod{#migration-method}

## Modernisera miljön {#modernizing-your-environment}

Att utföra en migrering kan vara en chans att uppdatera miljön (databasmotorer, operativsystem). Adobe Campaign rekommenderar starkt att du uppgraderar dina produktionsmiljöer till de senaste versionerna.

32-bitarsversioner av databaser och operativsystem stöds fortfarande i v7, men stöds inte längre i framtida versioner av Adobe Campaign. Vi rekommenderar starkt att du uppgraderar din plattform till 64 bitar så snart som möjligt.

I v6.02 var läget &quot;multi timezone&quot; bara tillgängligt för PostgreSQL-databasmotorer. Det erbjuds nu oavsett vilken typ av databasmotor som används. Vi rekommenderar att du omvandlar din bas till en&quot;multi-timezone&quot;-bas. Mer information finns i avsnittet [Tidszoner](../../migration/using/general-configurations.md#time-zones) .

>[!IMPORTANT]
>
>Vissa programversioner som stöds i Adobe Campaign 5.11 och 6.02 stöds inte längre i Adobe Campaign v7.
>
>Mer information om vilka versioner som stöds i Adobe Campaign finns i [kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

## Viktiga migreringssteg {#key-migration-steps}

Det allmänna tillvägagångssättet för migrering till Adobe Campaign v7 beskrivs i avsnittet [Innan migrering](../../migration/using/before-starting-migration.md) påbörjas.

Implementeringsstegen för migrering till Adobe Campaign v7 finns i avsnittet [Krav för migrering till Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .

Vilka konfigurationer som krävs beror på dina befintliga konfigurationer och den ursprungliga versionen av plattformen. Dessa beskrivs i avsnittet [Allmänna konfigurationer](../../migration/using/general-configurations.md) .

## Specifika konfigurationer {#specific-configurations}

De ändringar som gjorts i Adobe Campaign v7 kan också innebära att du måste anpassa vissa specifika konfigurationer som utvecklats i de tidigare versionerna. Därför kan det vara nödvändigt att utföra en granskning av alla dina konfigurationer innan migreringen: kontakta Adobe Campaign om du behöver hjälp.

Särskild uppmärksamhet bör ägnas till exempel specifika inställningar för webbprogram, schematillägg med SQLdata eller schemakloning som inte är i kartong. Mer information finns i avsnittet [Konfigurera din plattform](../../migration/using/configuring-your-platform.md) .

På samma sätt har vissa interna mekanismer ändrats för att svara på den ökade säkerheten i Adobe Campaign: måste du anpassa dessa motsvarande konfigurationer.
