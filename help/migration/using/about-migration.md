---
product: campaign
title: Migrering till Campaign Classic
description: Lär dig hur du migrerar till Campaign Classic från en tidigare Campaign-version
audience: migration
content-type: reference
topic-tags: migration-overview
exl-id: 3050238d-6f77-4ffa-9aef-677ab8009388
source-git-commit: 2594e4943ba24ae65d1fc005da589dc674aa2b0f
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 3%

---

# Kom igång med migreringen{#about-migration}

![](../../assets/v7-only.svg)

Det här dokumentet innehåller information om förutsättningarna för en migrering, stegen för en migrering till Adobe Campaign Classic v7. Steg och valfria inställningar beror på din konfiguration.

Migreringsprocessen måste utföras med försiktighet, dess konsekvenser måste beaktas fullt ut i förväg och förfarandet måste utföras rigoröst. Den får endast utföras av en expertanvändare. Vi rekommenderar att du kontaktar [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) innan någon migreringsprocess inleds.

Migreringen måste testas i test-/scenmiljön i förväg för att säkerställa att den fungerar smidigt och utan fel. Migrering av produktionsmiljön får endast utföras när den migrerade testmiljön har validerats fullständigt.

>[!NOTE]
>
>Nya funktioner och förbättringar som ingår i Adobe Campaign v7 beskrivs i [Versionsinformation](../../rn/using/latest-release.md).


## Förhandskrav

* Migreringsprocessen måste utföras av expertanvändare. Du måste få hjälp av minst en databasexpert, en systemadministratör och en programutvecklare från Adobe Campaign.
* Innan du startar migreringen bör du kontrollera att de system och systemkomponenter som du använder är kompatibla med v7. [Läs mer](../../rn/using/compatibility-matrix.md).
* Om du använder Adobe Campaign Cloud Messaging (installation från mellanleverantörer) kontaktar du Adobe kundtjänst innan du startar.
* Innan du startar en migreringsprocess bör du **måste** säkerhetskopiera dina data.
* Det kan ta flera dagar innan migreringen är klar.
* Adobe Campaign v7 är en säkrare version än de tidigare: Detta påverkar konfigurationsriktlinjerna för att undvika problem som till exempel korrupta data och för att bevara databasens dataintegritet. Som kund ansvarar du för att testa alla konfigurationer, inklusive arbetsflöden.

Fler förutsättningar finns i [den här sidan](../../migration/using/before-starting-migration.md).


## Moderniserad miljö {#modernizing-your-environment}

Att utföra en migrering kan vara en chans att uppdatera miljön (databasmotorer, operativsystem). Adobe Campaign rekommenderar starkt att du uppgraderar dina produktionsmiljöer till de senaste versionerna.

>[!CAUTION]
>
>Mer information om vilka versioner som stöds av Adobe Campaign v7 finns i [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md).

## Viktiga migreringssteg {#key-migration-steps}

Det allmänna tillvägagångssättet för migrering till Adobe Campaign v7 beskrivs i [den här sidan](../../migration/using/before-starting-migration.md).


## Specifika konfigurationer {#specific-configurations}

De ändringar som gjorts i Adobe Campaign v7 kan också innebära att du måste anpassa vissa specifika konfigurationer som utvecklats i tidigare versioner. Därför kan det vara nödvändigt att utföra en granskning av alla dina konfigurationer innan migreringen: kontakta Adobe Campaign om du behöver hjälp.

Särskild uppmärksamhet bör ägnas till exempel specifika inställningar för webbprogram, schematillägg med SQLdata eller schemakloning som inte är i kartong. För mer information om detta hittar du i [det här avsnittet](../../migration/using/configuring-your-platform.md).

På samma sätt har vissa interna mekanismer ändrats för att svara på den ökade säkerheten inom Adobe Campaign: måste du anpassa dessa konfigurationer i enlighet med detta.

