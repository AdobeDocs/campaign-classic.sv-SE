---
product: campaign
title: Konfigurationsprincip
description: Konfigurationsprincip
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

---

# Konfigurationsprincip{#configuration-principle}

Adobe Campaign-plattformen bygger på samma koncept som med virtuella värdar som används av Apache. I det här läget kan du dela en server genom att tilldela den flera instanser. Instanser är helt skilda från varandra och fungerar med sin egen databas och konfigurationsfil.

För en viss server finns det två element som är gemensamma för alla Adobe Campaign-instanser:

* Lösenordet **internal**: det här är det allmänna administratörslösenordet. Det är vanligt för alla instanser av en viss programserver.

   >[!IMPORTANT]
   >
   >Om du vill logga in med identifieraren **Internal** måste du ha definierat ett lösenord i förväg. Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#internal-identifier).

* Flera tekniska serverkonfigurationer: dessa konfigurationer kan alla överladdas i den specifika konfigurationen för en instans.

Konfigurationsfilerna sparas i katalogen **conf** i installationskatalogen. Konfigurationen är uppdelad i tre filer:

* **serverConf.xml**: övergripande konfiguration för alla instanser.
* **config-**`<instance>`**.xml** (där  **`<instance>`** är instansnamnet): specifik konfiguration för en instans.
* **serverConf.xml.diff**: delta mellan den inledande konfigurationen och den aktuella konfigurationen. Filen genereras automatiskt av programmet och får inte ändras manuellt. Den används för att automatiskt sprida användarändringar när en version uppdateras.

En instanskonfiguration läses in enligt följande:

* Modulen läser in filen **serverConf.xml** för att hämta de parametrar som delas av alla instanser.
* Sedan läses filen **config-**`<instance>`**.xml** in. Värdena i den här filen har prioritet framför värdena i **serverConf.xml**.

   Dessa två filer har samma format. Alla värden i **serverConf.xml** kan överladdas för en viss instans i filen **config-`<instance>`.xml**.

Det här operativläget ger stor flexibilitet för konfigurationer.
