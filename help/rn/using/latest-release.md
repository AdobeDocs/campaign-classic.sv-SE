---
product: campaign
title: Senaste versionen
description: Senaste versionsinformation för Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: c5aa626c166f513084d5fa141f307aba8bd57d36
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 99%

---

# Senaste versionen {#latest-release}

Den här sidan listar nya funktioner, förbättringar och korrigeringar som kommer med den **senaste versionen av Campaign Classic v7**. Varje ny version kommer med en status som visas med en färg. Läs mer om versionsstatusen för Campaign Classic v7 på [den här sidan](rn-overview.md).

## Version 7.4.2 – build 9390 {#release-7-4-2}

[!BADGE Allmän tillgänglighet]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=sv#rn-statuses" tooltip="Allmän tillgänglighet"}

_2 april 2025_

>[!AVAILABILITY]
>
>Den här versionen är i **begränsad tillgänglighet** (LA). Den är begränsad till endast användare av värdtjänster/hanterade tjänster. Den här versionen är snart tillgänglig för hybridkunder och kunder på plats.

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

### Säkerhetsförbättringar {#security-7-4-2}

Den här versionen innehåller flera säkerhetskorrigeringar.

Anslutningen till lösningar och appar från Adobe via det externa **[!UICONTROL Adobe Experience Cloud]**-kontot har uppdaterats för att stärka säkerheten.

### Korrigeringar {#release-7-4-2-fixes}

Den här versionen kommer med följande huvudkorrigeringar:

* TLS-/SMPP-anslutning – korrigerade SMPP-stabilitetsproblem

* Google BigQuery-korrigeringar:

   * Korrigerade regressioner för BOOLEAN-datatyper
   * Korrigerade problem med proxyinställningar
   * Korrigerade regressioner för DATETIME-datatyper
   * Korrigerade bulklaststabilitet
   * Förbättrade interna tester av ODBC-versioner
   * Korrigerade ett problem med specialtecken i anslutningssträngen
   * Standardtimeout (5 min) för Google BigQuery-frågor har tagits bort

* MTA (Mail Transfer Agent) – korrigerade ett överblivet MTA-underordnat element som ska ha statusen **[!UICONTROL Start pending]**.

Följande problem har också korrigerats i den här versionen:

NEO-47269, NEO-59059, NEO-62455, NEO-65774, NEO-66462, NEO-66989, NEO-77898, NEO-78843, NEO-79373, NEO-79598, NEO-80145, NEO-80245, NEO-80434, NEO-80683, NEO-81222, NEO-81433, NEO-81864, NEO-82351, NEO-82781, NEO-82838, NEO-82923, NEO-83252, NEO-83809, NEO-83826, NEO-84024, NEO-84553, NEO-85150

