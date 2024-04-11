---
product: campaign
title: Administration
description: Administration
feature: Monitoring
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Administration{#administration}



Automatisk start av Adobe Campaign-modulerna (**webb**, **mta**, **wfserver**, osv.) tillhandahålls av **nlserver** server.

Om du installerar Adobe Campaign konfigureras datorn automatiskt så att **nlserver** startar under startsekvensen.

Följande kommandon används för att starta och stänga av Adobe Campaign-tjänsten manuellt:

* I Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* I Linux (som rot):

   * **/etc/init.d/nlserver6 - start**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>Från och med 20.1 rekommenderar vi att du använder följande kommando i stället (för Linux): **systemctl start nlserver** / **systemctl stop nlserver**

Här är en lista med vanliga administrationskommandon som är tillgängliga i Linux (som **Adobe Campaign**):

* Visa alla påbörjade Adobe Campaign-moduler: **/etc/init.d/nlserver6 pdump** eller **/etc/init.d/nlserver6-status**

  >[!NOTE]
  >
  >Lägga till **-vem** parametern till **pdump** Med -kommandot kan du samla in information om aktuella anslutningar (användare och processer).\
  >The **/etc/init.d/nlserver6-status** -kommandot (utan parametern&quot;-who&quot;) returneras:
  >
  >    * 0 om alla processer körs.
  >    * 1 om en process saknas.
  >    * 2 om ingen process körs.
  >    * ett annat värde om ett fel uppstår.
  >

* Starta/stoppa en modul med flera instanser eller en instans (**webb**, **trackinglogd**, **syslogd**, **mta**, **wfserver**, **inmail**):

  **nlserver start`<module>[@<instance>]`**

  **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

  Du kan också använda **omstart av nlserver`<module>[@<instance>]`** om du vill starta om en modul.

  Exempel:

  **nlserver start web**

  **nlserver start mta@my_instance**

  **nlserver stop syslogd**

  **nlserver stop wfserver@my_instance**

  **nlserver stop web-Instant**

  **omstart av webbserver**

  >[!NOTE]
  >
  >* Om instansen inte anges används standardinstansen.
  >* I händelse av en kris ska du använda **-Instant** möjlighet att framtvinga ett omedelbart stopp av processen (motsvarande Unix-kommando) **döda -9**).
  >* Använd **-noconsole** för att se till att den modul som startas inte visar något på konsolen. Loggarna skrivs till disken via **syslogd** -modul.
  >* Använd **-verbose** om du vill visa ytterligare information om processåtgärder.
  >
  >   Exempel:
  >
  >   **webbverbose för omstart av nlserver**
  >
  >   **nlserver start mta@myinstance -verbose**
  >
  >   Med det här alternativet läggs ytterligare loggar till. Vi rekommenderar att du startar processerna igen utan **-verbose** för att undvika överlagring av loggar när du har hittat den önskade informationen.

* Starta alla Adobe Campaign-processer (motsvarar att starta **nlserver6** service):

  **nlserver watchdog -noconsole**

* Stäng alla Adobe Campaign-processer (motsvarar att stänga av **nlserver6** service):

  **avstängning av nlserver**

* Läs in **nlserver web** modulkonfiguration (och webbservertilläggsmodulen, om tillämpligt) när **serverConf.xml** och **config-`<instance>  .xml </instance>`** filer har redigerats.

  **nlserver config -reload**

  >[!NOTE]
  >
  >Vissa konfigurationsändringar tas inte med i beräkningen dynamiskt. Adobe Campaign måste stängas av och sedan startas om.
