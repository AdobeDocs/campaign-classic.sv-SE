---
product: campaign
title: Technote - Adobe Campaign - säkerhetsuppdatering av Apache-version
description: Adobe Campaign - säkerhetsuppdatering av Apache-version
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: a3eae4e253f66f5a651ffe0458f60b1f8bdf2258
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Adobe Campaign - säkerhetsuppdatering av Apache-version {#apache-update}

>[!CAUTION]
>Den här artikeln gäller för: **Campaign Classic v7 Managed Services** kunder, **Campaign v8** kunder och **Campaign Standard** kunder.

Adobe Campaign fungerar med verktyg från tredje part och kompatibiliteten uppdateras regelbundet, så att endast de versioner som stöds kan implementeras och de senaste korrigeringarna och förbättringarna kan utnyttjas.

Adobe Campaign innehåller Apache Tomcat som fungerar som startpunkt i programservern via HTTP och är integrerat med Apache Web Server. Apache Software Foundation har släppt Apache HTTP Server 2.4.53. Denna version åtgärdar sårbarheter som kan utnyttjas av en angripare för att ta kontroll över den drabbade datorn. Läs mer i [Apache 2.4.53-meddelande](https://downloads.apache.org/httpd/Announcement2.4.html){target=&quot;_blank&quot;}.

Adobe Campaign-teamet kommer att genomföra säkerhetsuppgraderingen av Apache-versionen av **15 juni 2022** för att minska denna Apache-sårbarhet och göra instansmiljön säkrare. Uppgraderingen gäller alla Managed Services-kunder med Campaign Classic v7, Campaign v8 och Campaign Standarder som använder en sårbar version av Apache HTTP Server. Om du påverkas kontaktade Adobe dig redan för att informera dig om uppgraderingen.

Uppgraderingen förväntas att köras automatiskt utanför kontorstid så att du kan fortsätta använda Campaign-tjänsten utan avbrott.

Din(a) icke-produktionsinstans(er) kommer att uppgraderas av Adobe först, sedan kommer din(a) produktionsinstans(er) att uppgraderas. Eftersom detta är en automatisk uppgraderingsprocess som ägs av Adobe behöver du inte vidta några åtgärder. Om du får problem kan du kontakta [Adobe kundtjänst](https://experienceleague.adobe.com/?support-solution=Campaign#support).


>[!NOTE]
>Denna uppgradering kräver att webbservern Apache startas om. Nedtiden överstiger inte 10 minuter inom den tidsperiod som anges nedan.

## Vanliga frågor och svar {#apache-faq}

* **Varför är detta en obligatorisk uppgradering?**

   Den aktuella Apache-versionen är sårbar och kan utgöra ett säkerhetshot. Det är viktigt att dina Campaign-instanser uppgraderas till den senaste tillämpliga Apache-versionen för att hantera säkerhetsrisken.

* **Vilka kunder vill uppgradera?**

   Alla kunder som använder Campaign-miljöer som har implementerats i äldre Apache-versioner uppgraderas till den senaste tillämpliga Apache-versionen.

* **Vilka är de förväntade driftsavbrotten?**

   Förväntat driftstopp är under 10 minuter.

* **Kräver kunden några åtgärder för denna säkerhetsuppgradering?**

   Inga åtgärder krävs eftersom säkerhetsuppgraderingen körs automatiskt.

* **Hur påverkar det pågående kampanjerna/arbetsflödena under underhållsperioden?**

   Under underhållsperioden stoppas både arbetsflödet och posttjänsterna och de schemalagda aktiviteterna körs inte. Alla pågående aktiviteter eller processer som körs avbryts under driftstoppet tills servern startas om. När aktiviteten har slutförts och servern har startats om återupptas alla tjänster.

* **Vilka valideringar behöver kunderna köra?**

   Ingen specifik testning krävs för denna säkerhetsuppgradering. Om något problem uppstår, var vänlig och kontakta [Adobe kundtjänst](https://experienceleague.adobe.com/?support-solution=Campaign#support).


* **Kan jag begära en ändring av datum/tid för den schemalagda säkerhetsuppgraderingsplatsen?**

   Eftersom det här är en säkerhetskorrigering rekommenderar vi att du anpassar dig till det befintliga schemat.


För alla andra frågor kan du kontakta [Adobe kundtjänst](https://experienceleague.adobe.com/?support-solution=Campaign#support).