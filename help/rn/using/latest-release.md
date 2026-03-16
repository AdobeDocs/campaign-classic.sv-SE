---
product: campaign
title: Senaste versionen
description: Senaste versionsinformation om Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 66387e2e008051901fe3385f571d7fe798829100
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Senaste versionen {#latest-release}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i den **senaste Campaign Classic v7-utgåvan**. Varje ny version har en status som materialiseras av en färg. Läs mer om byggstatus för Campaign Classic v7 på [den här sidan](rn-overview.md).

## Version 7.4.3 - build 9392 {#release-7-4-3}

[!BADGE Allmän tillgänglighet]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=sv-SE#rn-statuses" tooltip="Allmän tillgänglighet"}

_16 mars 2026_

>[!CAUTION]
>
> Uppgradering av klientkonsolen är obligatoriskt.

### Säkerhetsförbättringar {#security-7-4-3}

* För att upprätthålla optimal säkerhet, stabilitet och efterlevnad har Debian uppgraderats till version 13 och PostgreSQL till version 17. Se [kompatibilitetsmatrisen](compatibility-matrix.md).

### Korrigeringar {#fixes-7-4-3}

* Korrigerade ett problem där streckkodskomponenten tillät en obegränsad höjdparameter, vilket kan leda till en säkerhetsrisk. (NEO-8984)
* Korrigerade ett problem där uppräkningsfält i listor som skapats via arbetsflöden saknade temporära namnattribut, vilket medförde att felaktiga eller tomma uppräkningsetiketter visades i gränssnittet. (NEO-91158)
* Ett problem har korrigerats där leveransstatistiken inte räknades om fullständigt för vissa leveranser, vilket i synnerhet påverkade resultatindikatorerna. (NEO-88106)
* Ett problem har korrigerats där leveransförberedelsen misslyckades med personaliseringsfel när targetData-fält användes i arbetsflöden med dedupliceringsaktiviteter. (NEO-87693)
* Ett problem har korrigerats där sammanfogning av strängfält med ett tecken med andra strängar misslyckades i PostgreSQL 15 på grund av typkonverteringskrav. (NEO-88028)
* Ett problem har korrigerats där spårningsloggar för samarbetskampanjer i distribuerad marknadsföring inte skrevs till databasen på grund av en felmatchning mellan överordnade och underordnade leverans-ID:n. (NEO-86836)
* Ett problem har korrigerats där leveransloggarna visade meddelanden som annullerade trots att de skickades utan fel, vilket i synnerhet påverkade leveranser med vågplanering. (NEO-7893)
* Ett problem har korrigerats där arbetsflödet för databasrensning inte rensade data effektivt, vilket kan påverka prestandan. (NEO-76439)

