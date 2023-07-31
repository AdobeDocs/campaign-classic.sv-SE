---
product: campaign
title: Konfigurationsprincip
description: Konfigurationsprincip
feature: Monitoring, Configuration
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 7%

---

# Konfigurationsprincip{#configuration-principle}



Adobe Campaign-plattformen bygger på samma koncept som med virtuella värdar som används av Apache. I det här läget kan du dela en server genom att tilldela den flera instanser. Instanser är helt skilda från varandra och fungerar med sin egen databas och konfigurationsfil.

För en viss server finns det två element som är gemensamma för alla Adobe Campaign-instanser:

* The **internal** lösenord: det här är det allmänna administratörslösenordet. Det är vanligt för alla instanser av en viss programserver.

  >[!IMPORTANT]
  >
  >Logga in med **Intern** måste du ha definierat ett lösenord i förväg. Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#internal-identifier).

* Flera tekniska serverkonfigurationer: dessa konfigurationer kan alla överlagras i den specifika konfigurationen för en instans.

Konfigurationsfilerna sparas i **conf** installationskatalogen. Konfigurationen är uppdelad i tre filer:

* **serverConf.xml**: övergripande konfiguration för alla instanser.
* **config-**`<instance>`**XML** (där **`<instance>`** är instansnamnet): specifik konfiguration för en instans.
* **serverConf.xml.diff**: delta mellan den inledande konfigurationen och den aktuella konfigurationen. Filen genereras automatiskt av programmet och får inte ändras manuellt. Den används för att automatiskt sprida användarändringar när en version uppdateras.

En instanskonfiguration läses in enligt följande:

* Modulen läser in **serverConf.xml** -fil för att hämta de parametrar som delas av alla instanser.
* Sedan laddas **config-**`<instance>`**XML** -fil. Värdena i den här filen har prioritet framför värdena i **serverConf.xml**.

  Dessa två filer har samma format. Valfritt värde i **serverConf.xml** kan överläsas för en viss instans i **config-`<instance>`XML** -fil.

Det här operativläget ger stor flexibilitet för konfigurationer.
