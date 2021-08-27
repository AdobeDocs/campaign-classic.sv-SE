---
product: campaign
title: Migreringsmetod
description: Migreringsmetod
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: dd4d068b-f414-448f-8d9a-eedf44e7b6e6
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 1%

---

# Migreringsmetod{#migration-method}

![](../../assets/v7-only.svg)

## Modernisera miljön {#modernizing-your-environment}

Att utföra en migrering kan vara en chans att uppdatera miljön (databasmotorer, operativsystem). Adobe Campaign rekommenderar starkt att du uppgraderar dina produktionsmiljöer till de senaste versionerna.

32-bitarsversioner av databaser och operativsystem stöds fortfarande i v7, men stöds inte längre i framtida versioner av Adobe Campaign. Vi rekommenderar starkt att du uppgraderar din plattform till 64 bitar så snart som möjligt.

I v6.02 var läget &quot;multi timezone&quot; bara tillgängligt för PostgreSQL-databasmotorer. Det erbjuds nu oavsett vilken typ av databasmotor som används. Vi rekommenderar att du omvandlar din bas till en&quot;multi-timezone&quot;-bas. Mer information finns i avsnittet [Tidszoner](../../migration/using/general-configurations.md#time-zones).

>[!IMPORTANT]
>
>Vissa programversioner som stöds i Adobe Campaign 5.11 och 6.02 stöds inte längre i Adobe Campaign v7.
>
>Mer information om vilka versioner som stöds av Adobe Campaign finns i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md).

## Viktiga migreringssteg {#key-migration-steps}

Den allmänna proceduren för migrering till Adobe Campaign v7 beskrivs i avsnittet [Innan du startar migreringen](../../migration/using/before-starting-migration.md).

Implementeringsstegen för migrering till Adobe Campaign v7 beskrivs i avsnittet [Krav för migrering till Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md).

Vilka konfigurationer som krävs beror på dina befintliga konfigurationer och den ursprungliga versionen av plattformen. Dessa beskrivs i avsnittet [Allmänna konfigurationer](../../migration/using/general-configurations.md).

## Specifika konfigurationer {#specific-configurations}

De ändringar som gjorts i Adobe Campaign v7 kan också innebära att du måste anpassa vissa specifika konfigurationer som utvecklats i tidigare versioner. Därför kan det vara nödvändigt att utföra en granskning av alla dina konfigurationer innan migreringen: kontakta Adobe Campaign om du behöver hjälp.

Särskild uppmärksamhet bör ägnas till exempel specifika inställningar för webbprogram, schematillägg med SQLdata eller schemakloning som inte är i kartong. Mer information finns i avsnittet [Konfigurera din plattform](../../migration/using/configuring-your-platform.md).

På samma sätt har vissa interna mekanismer ändrats för att svara på den ökade säkerheten inom Adobe Campaign: måste du anpassa dessa motsvarande konfigurationer.
