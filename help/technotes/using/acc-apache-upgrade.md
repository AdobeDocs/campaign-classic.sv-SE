---
product: campaign
title: Technote - Adobe Campaign - säkerhetsuppdatering av Apache-version
description: Adobe Campaign - säkerhetsuppdatering av Apache-version
hide: true
hidefromtoc: true
source-git-commit: 086d03cf0ceb5c2db7ded0c2bedb1b0514257d8a
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Adobe Campaign - säkerhetsuppdatering av Apache-version {#apache-update}

Campaign Classic arbetar med verktyg från tredje part och kompatibiliteten uppdateras regelbundet, så att endast de versioner som stöds kan implementeras och de senaste korrigeringarna och förbättringarna kan utnyttjas.

Adobe Campaign innehåller Apache Tomcat som fungerar som startpunkt i programservern via HTTP och är integrerat med Apache Web Server. Apache Software Foundation har släppt Apache HTTP Server 2.4.53. Denna version åtgärdar säkerhetsluckor - CVE-2021-44790 och CVE-2021-44224 - en som kan utnyttjas av en angripare för att ta kontroll över den drabbade datorn. Läs mer i [Apache 2.4.53-meddelande](https://downloads.apache.org/httpd/Announcement2.4.html){target=&quot;_blank&quot;}.

Adobe Campaign-teamet kommer att genomföra säkerhetsuppgraderingen av Apache-versionen av **31 maj 2022** för att minska denna Apache-sårbarhet och göra instansmiljön säkrare. Denna uppgradering gäller alla Managed Services-kunder som använder en sårbar version av Apache HHTP Server. Om du påverkas kontaktade Adobe dig redan för att informera dig om uppgraderingen.

Uppgraderingen förväntas att köras automatiskt utanför kontorstid så att du kan fortsätta använda Campaign-tjänsten utan avbrott.

Din(a) instans(er) som inte är i produktion kommer att uppgraderas av våra team först innan vi uppgraderar dina produktionsinstanser. Eftersom detta är en automatisk uppgraderingsprocess behöver du inte vidta några åtgärder. Om du får problem kan du kontakta [Adobe kundtjänst](https://experienceleague.adobe.com/?support-solution=Campaign#support).

Eftersom uppgraderingen skulle behöva starta om Apache förväntar vi oss att driftstoppet inte överstiger 10 minuter inom den tidsrymd som anges nedan.

## Vanliga frågor och svar {#apache-faq}

* **Varför är detta en obligatorisk uppgradering?**

   Den aktuella Apache-versionen är sårbar och kan utgöra ett säkerhetshot. Det är viktigt att dina Campaign-instanser uppgraderas till den senaste tillämpliga Apache-versionen för att hantera säkerhetsrisken.


* **Vilka kunder vill uppgradera?**

   Alla kunder vars Campaign-miljöer implementeras på äldre Apache-versioner kommer att uppgraderas till den senaste tillämpliga Apache-versionen.

* **Vilka är de förväntade driftsavbrotten?**

   Förväntat driftstopp är under 10 min.


* **Kräver kunden några åtgärder för denna säkerhetsuppgradering?**

   Inga åtgärder krävs eftersom säkerhetsuppgraderingen körs automatiskt.


* **Vilka valideringar behöver kunderna köra?**

   Ingen specifik testning krävs för denna säkerhetsuppgradering. Om något problem uppstår, var vänlig och kontakta [Adobe kundtjänst](https://experienceleague.adobe.com/?support-solution=Campaign#support)


* **Kan jag begära en ändring av datum/tid för den schemalagda säkerhetsuppgraderingsplatsen?**

   Eftersom det här är en säkerhetskorrigering rekommenderar vi att du anpassar dig till det befintliga schemat.


För alla andra frågor kan du kontakta [Adobe kundtjänst](https://experienceleague.adobe.com/?support-solution=Campaign#support).
