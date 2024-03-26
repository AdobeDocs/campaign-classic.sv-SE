---
product: campaign
title: Technote - Adobe Campaign systemuppgraderingar
description: Adobe Campaign systemuppgradering
feature: Technote, Upgrade
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 4%

---

# Adobe Campaign 2023 miljöuppgraderingar {#ac-system-upgrade}

Kampanjinfrastrukturen bygger på tredjepartssystem som regelbundet måste uppdateras med de senaste versionerna och korrigeringarna. Dessa uppdateringar är obligatoriska för att säkerställa kontinuitet i tjänsten och säkra kampanjmiljöer från säkerhetsrisker. Dessutom krävs en Campaign-uppgradering för att säkerställa kompatibilitet med systemändringar från tredje part.

Som en **Kund för värdbaserade eller hanterade Cloud Service** får du information från Adobe om dessa uppgraderingar när de behövs. Du måste uppgradera dina miljöer i enlighet med rekommendationerna för att säkerställa efterlevnad.

Som en **Lokal kund eller hybridkund** rekommenderar Adobe att du uppgraderar system- och kampanjversionerna enligt samma kalender.

Av säkerhetsskäl måste du [installera den senaste Campaign-versionen](#ac-upgrade)och sedan uppgradera [operativsystem](#os-upgrade) och/eller [RDBMS (Relation Database Management System)](#pg-upgrade).

>[!NOTE]
>
>Om du har frågor om dessa ändringar kan du kontakta [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Se även [Vanliga frågor om uppgradering av bygge](../../platform/using/faq-build-upgrade.md).
>

## Uppgradering av kampanjbygge {#ac-upgrade}

**Påverkas du?**

Om du påverkas av [uppgradering av operativsystem](#os-upgrade) och/eller [databassystemuppgradering](#pg-upgrade) som beskrivs nedan måste ni uppgradera era Campaign-miljöer till [den senaste 7.3.2-versionen](../../rn/using/latest-release.md#release-7-3-2)som är kompatibelt med dessa system.

**Hur uppdaterar jag?**

* Som kund hos en värdserver eller Managed Cloud Services kommer Adobe att kontakta dig och uppgradera din Campaign-version.
* Som hybridkund informerar Adobe dig om de schemalagda uppgraderingsdatumen för din mellanleverantörsmiljö. Du måste också uppgradera din marknadsföringsmiljö till samma version.
* Som lokal kund ombeds du uppgradera era Campaign-miljöer till den senaste 7.3.2-versionen.


## Uppgradering av operativsystem {#os-upgrade}

**Påverkas du?**

Om ni kör Campaign på ett Debian-operativsystem och vill dra nytta av de senaste säkerhetsuppdateringarna för Debian måste ni flytta er Campaign-infrastruktur till **Debian 11**. Observera att säkerhetssupport för Debian 9 kommer att vara tillgänglig till 30 juni 2023.

**Hur uppdaterar jag?**

* Som värdkund eller hanterad Cloud Service kontaktar Adobe dig och uppgraderar din miljö.
* Som hybridkund informerar Adobe dig om de schemalagda uppgraderingsdatumen för din mellanleverantörsmiljö. Om er marknadsföringsmiljö även körs på Debian måste ni också uppgradera den till Debian 11.
* Som lokal kund ombeds du uppgradera dina miljöer till Debian 11.

## Uppgradering av databassystem {#pg-upgrade}

**Påverkas du?**

Om ditt databassystem för Campaign är PostgreSQL och du vill ha tillgång till de senaste PostgreSQL-innovationerna och säkerhetsuppdateringarna måste du uppgradera till **PostgreSQL 14**. Observera att PostgreSQL 11 når slutet av livscykeln den 9 november 2023.

**Hur uppdaterar jag?**

* Som kund hos en värdserver eller hanterad Cloud Service kommer Adobe att kontakta dig och uppgradera ditt databassystem från PostgreSQL 11 till PostgreSQL 14.
* Om ert marknadsföringsdatabassystem är PostgreSQL måste ni som hybridkund uppgradera det till PostgreSQL 14.
* Som lokal kund ombeds du uppgradera databassystemet till PostgreSQL 14.


## Användbara länkar

* [Uppgradera din miljö](../../production/using/build-upgrade.md)
* [Vanliga frågor och svar om builduppgradering](../../platform/using/faq-build-upgrade.md)
* [Ladda ned den senaste Campaign Classicen](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Gör den nya klientkonsolen tillgänglig för användare](../../installation/using/client-console-availability-for-windows.md)
