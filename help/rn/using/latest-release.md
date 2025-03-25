---
product: campaign
title: Senaste versionen
description: Senaste versionsinformation för Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 631188b5974eaa4cd1bf667c5df9f2ff0f983cf0
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 24%

---

# Senaste versionen {#latest-release}

Den här sidan listar nya funktioner, förbättringar och korrigeringar som kommer med den **senaste versionen av Campaign Classic v7**. Varje ny version kommer med en status som visas med en färg. Läs mer om versionsstatusen för Campaign Classic v7 på [den här sidan](rn-overview.md).

## Version 7.4.2 – build 9390 {#release-7-4-2}

[!BADGE Begränsad tillgänglighet]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=sv#rn-statuses" tooltip="Begränsad tillgänglighet"}

_21 mars 2025_

>[!AVAILABILITY]
>
>Den här versionen är i **begränsad tillgänglighet** (LA). Den är begränsad till användare av värdtjänster/hanterade tjänster. Den här versionen är snart tillgänglig för hybridkunder och lokala kunder.

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

### Säkerhetsförbättringar {#security-7-4-2}

Den här versionen innehåller flera säkerhetskorrigeringar.

Anslutningen till Adobe lösningar och appar via det externa **[!UICONTROL Adobe Experience Cloud]**-kontot har uppdaterats för att stärka säkerheten.

### Korrigeringar {#release-7-4-2-fixes}

Den här versionen innehåller följande huvudkorrigeringar:

* TLS-/SMPP-anslutning - Åtgärdade SMPP-stabilitetsproblem

* Google BigQuery-korrigeringar:

   * Fasta regressioner för BOOLEAN-datatyper
   * Problem med proxyinställningar har åtgärdats
   * Korrigerade regressioner för DATETIME-datatyper
   * Fast bulklaststabilitet
   * Förbättrade interna tester av ODBC-versioner
   * Ett problem med specialtecken i anslutningssträngen har korrigerats
   * Standardtimeout (5 min) för Google BigQuery-frågor har tagits bort

* MTA (Mail Transfer Agent) - Ett överblivet MTA-underordnat objekt som ska ha statusen **[!UICONTROL Start pending]** har korrigerats.

Följande problem har också åtgärdats i den här versionen:

NEO-47269, NEO-59059, NEO-62455, NEO-65774, NEO-66462, NEO-66989, NEO-77898, NEO-788 43, NEO-79373, NEO-79598, NEO-80145, NEO-80245, NEO-80434, NEO-80683, NEO-8122, NEO-8 1433, NEO-81864, NEO-82351, NEO-82781, NEO-82838, NEO-82923, NEO-83252, NEO-83809, NEO O-83826, NEO-84024, NEO-84553, NEO-85150

