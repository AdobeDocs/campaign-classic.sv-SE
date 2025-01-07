---
product: campaign
title: Technote - Adobe Campaign systemuppgraderingar
description: Adobe Campaign systemuppgradering
feature: Technote, Upgrade
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 4%

---

# Adobe Campaign 2023 miljöuppgraderingar {#ac-system-upgrade}

Kampanjinfrastrukturen bygger på tredjepartssystem som regelbundet måste uppdateras med de senaste versionerna och korrigeringarna. Dessa uppdateringar är obligatoriska för att säkerställa kontinuitet i tjänsten och säkra kampanjmiljöer från säkerhetsrisker. Dessutom krävs en Campaign-uppgradering för att säkerställa kompatibilitet med systemändringar från tredje part.

Som **värdkund eller hanterad Cloud Service** informerar Adobe dig om dessa uppgraderingar när de behövs. Du måste uppgradera dina miljöer i enlighet med rekommendationerna för att säkerställa efterlevnad.

Som **lokal kund eller hybrid-kund** rekommenderar Adobe att du uppgraderar system- och kampanjversionerna enligt samma kalender.

Av säkerhetsskäl måste du [installera den senaste Campaign-versionen](#ac-upgrade) och sedan uppgradera ditt [operativsystem](#os-upgrade) och/eller ditt [Relation Database Management System (RDBMS)](#pg-upgrade).

>[!NOTE]
>
>Kontakta [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om du har frågor om de här ändringarna. Se även [Vanliga frågor om uppgradering av bygge](../../platform/using/faq-build-upgrade.md).
>

## Uppgradering av kampanjbygge {#ac-upgrade}

**Påverkas du?**

Om du påverkas av [operativsystemsuppgraderingen](#os-upgrade) och/eller [databassystemuppgraderingen](#pg-upgrade) som anges nedan, måste du uppgradera dina Campaign-miljöer till [den senaste 7.3.2-versionen](../../rn/using/latest-release.md#release-7-3-2), som är kompatibel med dessa system.

**Hur uppdaterar jag?**

* Som kund hos en värdserver eller Managed Cloud Services kommer Adobe att kontakta dig och uppgradera din Campaign-version.
* Som hybridkund informerar Adobe dig om de schemalagda uppgraderingsdatumen för din mellanleverantörsmiljö. Du måste också uppgradera din marknadsföringsmiljö till samma version.
* Som lokal kund ombeds du uppgradera era Campaign-miljöer till den senaste 7.3.2-versionen.


## Uppgradering av operativsystem {#os-upgrade}

**Påverkas du?**

Om du kör Campaign på ett Debian-operativsystem måste du flytta din Campaign-infrastruktur till **Debian 11** för att få tillgång till de senaste Debian-säkerhetsuppdateringarna. Observera att säkerhetssupport för Debian 9 kommer att vara tillgänglig till 30 juni 2023.

**Hur uppdaterar jag?**

* Som värdkund eller hanterad Cloud Service kontaktar Adobe dig och uppgraderar din miljö.
* Som hybridkund informerar Adobe dig om de schemalagda uppgraderingsdatumen för din mellanleverantörsmiljö. Om er marknadsföringsmiljö även körs på Debian måste ni också uppgradera den till Debian 11.
* Som lokal kund ombeds du uppgradera dina miljöer till Debian 11.

## Uppgradering av databassystem {#pg-upgrade}

**Påverkas du?**

Om ditt databassystem för Campaign är PostgreSQL, och du vill ha tillgång till de senaste PostgreSQL-innovationerna och säkerhetsuppdateringarna, måste du uppgradera till **PostgreSQL 14**. Observera att PostgreSQL 11 når slutet av livscykeln den 9 november 2023.

**Hur uppdaterar jag?**

* Som kund hos en värdserver eller hanterad Cloud Service kommer Adobe att kontakta dig och uppgradera ditt databassystem från PostgreSQL 11 till PostgreSQL 14.
* Om ert marknadsföringsdatabassystem är PostgreSQL måste ni som hybridkund uppgradera det till PostgreSQL 14.
* Som lokal kund ombeds du uppgradera databassystemet till PostgreSQL 14.


## Användbara länkar

* [Uppgradera din miljö](../../production/using/build-upgrade.md)
* [Vanliga frågor och svar om builduppgradering](../../platform/using/faq-build-upgrade.md)
* [Hämta den senaste Campaign Classicen](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Gör den nya klientkonsolen tillgänglig för användare](../../installation/using/client-console-availability-for-windows.md)
