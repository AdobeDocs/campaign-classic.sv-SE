---
title: Konfigurationsprincip
seo-title: Konfigurationsprincip
description: Konfigurationsprincip
seo-description: null
page-status-flag: never-activated
uuid: 6315d526-b820-46ab-96c7-e64e101c6a7d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: d08ff769-da93-4f86-8802-f0fb5b051ece
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# Konfigurationsprincip{#configuration-principle}

Adobe Campaign-plattformen bygger på konceptet med instanser, liknande det med virtuella värdar som används av Apache. I det här läget kan du dela en server genom att tilldela den flera instanser. Instanser är helt skilda från varandra och fungerar med sin egen databas och konfigurationsfil.

För en viss server finns det två element som är gemensamma för alla Adobe Campaign-instanser:

* Det **interna** lösenordet: det här är det allmänna administratörslösenordet. Det är vanligt för alla instanser av en viss programserver.

   >[!CAUTION]
   >
   >Om du vill logga in med den **interna** identifieraren måste du ha definierat ett lösenord i förväg. Mer information finns i [det här avsnittet](../../installation/using/campaign-server-configuration.md#internal-identifier).

* Flera tekniska serverkonfigurationer: dessa konfigurationer kan alla överladdas i den specifika konfigurationen för en instans.

Konfigurationsfilerna sparas i installationskatalogens **conf** -katalog. Konfigurationen är uppdelad i tre filer:

* **serverConf.xml**: övergripande konfiguration för alla instanser.
* **config-**`<instance>`**.xml** (där **`<instance>`** är instansnamnet): specifik konfiguration för en instans.
* **serverConf.xml.diff**: delta mellan den inledande konfigurationen och den aktuella konfigurationen. Filen genereras automatiskt av programmet och får inte ändras manuellt. Den används för att automatiskt sprida användarändringar när en version uppdateras.

En instanskonfiguration läses in enligt följande:

* Modulen läser in **filen serverConf.xml** för att hämta de parametrar som delas av alla instanser.
* Sedan läses filen **config-**`<instance>`**.xml** in. Värdena i den här filen har prioritet framför värdena i **serverConf.xml**.

   Dessa två filer har samma format. Alla värden i **serverConf.xml** kan läsas in för en viss instans i **filen config-`<instance>`.xml** .

Det här operativläget ger stor flexibilitet för konfigurationer.
