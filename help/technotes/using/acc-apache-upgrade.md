---
product: campaign
title: Technote - Adobe Campaign - säkerhetsuppdatering av Apache-version
description: Adobe Campaign - säkerhetsuppdatering av Apache-version
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Adobe Campaign - säkerhetsuppdatering av Apache-version {#apache-update}

>[!CAUTION]
>Den här artikeln gäller för: **Campaign Classic v7 Managed Services**-kunder, **Campaign v8**-kunder och **Campaign Standard**-kunder.

Adobe Campaign fungerar med verktyg från tredje part och kompatibiliteten uppdateras regelbundet, så att endast de versioner som stöds kan implementeras och de senaste korrigeringarna och förbättringarna kan utnyttjas.

Adobe Campaign innehåller Apache Tomcat som fungerar som startpunkt i programservern via HTTP och är integrerat med Apache Web Server. Apache Software Foundation har släppt Apache HTTP Server 2.4.53. Denna version åtgärdar sårbarheter som kan utnyttjas av en angripare för att ta kontroll över den drabbade datorn. Läs mer i [Apache 2.4.53-meddelande](https://downloads.apache.org/httpd/Announcement2.4.html){target="_blank"}.

Adobe Campaign-teamet kommer att genomföra säkerhetsuppgraderingen av Apache-versionen senast den **15 juni 2022** för att minska denna Apache-säkerhetslucka och göra instansmiljön säkrare. Uppgraderingen gäller alla Managed Services-kunder i Campaign Classic v7, Campaign v8 och Campaign Standarder som kör en sårbar version av Apache HTTP Server. Om du påverkas kontaktade Adobe dig redan för att informera dig om uppgraderingen.

Uppgraderingen förväntas att köras automatiskt utanför kontorstid så att du kan fortsätta använda Campaign-tjänsten utan avbrott.

Din(a) icke-produktionsinstans(er) kommer att uppgraderas av Adobe först, sedan kommer dina produktionsinstanser att uppgraderas. Eftersom detta är en automatisk uppgraderingsprocess som ägs av Adobe behöver du inte vidta några åtgärder. Om du får problem kontaktar du [Adobe kundtjänst](https://experienceleague.adobe.com/sv?support-solution=Campaign#support).


>[!NOTE]
>Denna uppgradering kräver att webbservern Apache startas om. Nedtiden överstiger inte 10 minuter inom den tidsperiod som anges nedan.
> 

## Vanliga frågor och svar {#apache-faq}

* **Varför är detta en obligatorisk uppgradering?**

  Den aktuella Apache-versionen är sårbar och kan utgöra ett säkerhetshot. Det är viktigt att dina Campaign-instanser uppgraderas till den senaste tillämpliga Apache-versionen för att hantera säkerhetsrisken.

* **Vilka kunder riktar sig till för säkerhetsuppgraderingar?**

  Alla kunder som använder Campaign-miljöer som har implementerats i äldre Apache-versioner uppgraderas till den senaste tillämpliga Apache-versionen.

* **Vad är den förväntade nedtiden?**

  Förväntat driftstopp är under 10 minuter.

* **Behöver kunden några åtgärder för säkerhetsuppgraderingen?**

  Inga åtgärder krävs eftersom säkerhetsuppgraderingen körs automatiskt.

* **Vilken påverkan har de kampanjer/arbetsflöden som körs under underhållsperioden?**

  Under underhållsperioden stoppas både arbetsflödet och posttjänsterna och de schemalagda aktiviteterna körs inte. Alla pågående aktiviteter eller processer som körs avbryts under driftstoppet tills servern startas om. När aktiviteten har slutförts och servern har startats om återupptas alla tjänster.

* **Vilka valideringar måste köras av kunderna?**

  Ingen specifik testning krävs för denna säkerhetsuppgradering. Om något problem uppstår kan du kontakta [Adobe kundtjänst](https://experienceleague.adobe.com/sv?support-solution=Campaign#support).


* **Kan jag begära en ändring av datum/tid för den schemalagda säkerhetsuppgraderingsplatsen?**

  Eftersom det här är en säkerhetskorrigering rekommenderar vi att du anpassar dig till det befintliga schemat.


Om du har andra frågor kan du kontakta [Adobe kundtjänst](https://experienceleague.adobe.com/sv?support-solution=Campaign#support).
