---
product: campaign
title: Administration
description: Administration
feature: Monitoring
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 12a255fe-66f9-40ce-b19e-c24322c2e009
source-git-commit: b7dedddc080d1ea8db700fabc9ee03238b3706cc
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# Administration{#administration}

Automatisk start av Adobe Campaign-modulerna (**web**, **mta**, **wfserver** osv.) tillhandahålls av servern **nlserver**.

Om du installerar Adobe Campaign konfigureras datorn automatiskt så att tjänsten **nlserver** startar under startsekvensen.

Följande kommandon används för att starta och stänga av Adobe Campaign-tjänsten manuellt:

* I Windows:

   * **net start nlserver6**
   * **net stop nlserver6**

* I Linux (som rot):

   * **/etc/init.d/nlserver6 start**
   * **/etc/init.d/nlserver6 stop**

>[!NOTE]
>
>Från 20.1 rekommenderar vi att du använder följande kommando i stället (för Linux): **systemctl start nlserver** / **systemctl stop nlserver**

Här är en lista över vanliga administrationskommandon som är tillgängliga i Linux (som **Adobe Campaign**):

* Visa alla påbörjade Adobe Campaign-moduler: **/etc/init.d/nlserver6 pdump** eller **/etc/init.d/nlserver6 status**

  >[!NOTE]
  >
  >Genom att lägga till parametern **-who** i kommandot **pdump** kan du samla in information om aktuella anslutningar (användare och processer).\
  >Kommandot **/etc/init.d/nlserver6 status** (utan parametern &quot;-who&quot;) returnerar:
  >
  >    * 0 om alla processer körs.
  >    * 1 om en process saknas.
  >    * 2 om ingen process körs.
  >    * ett annat värde om ett fel uppstår.
  >

* Starta/stoppa en modul med flera instanser eller en instans (**web**, **trackinglog**, **syslog**, **mta**, **wfserver**, **inmail**):

  **nlserver start`<module>[@<instance>]`**

  **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

  Du kan också använda kommandot **nlserver start`<module>[@<instance>]`** för att starta om en modul.

  Exempel:

  **nlserver start web**

  **nlserver start mta@my_instance**

  **nlserver stop syslogd**

  **nlserver stop wfserver@my_instance**

  **nlserver stop web-direct**

  **nlserver startar om webb**

  >[!NOTE]
  >
  >* Om instansen inte anges används standardinstansen.
  >* I en nödsituation använder du alternativet **-direct** för att framtvinga ett omedelbart stopp i processen (motsvarande Unix-kommandot **Kill -9**).
  >* Använd alternativet **-noconsole** för att kontrollera att den modul som startas inte visar något på konsolen. Dess loggar skrivs till disken via modulen **syslogd**.
  >* Använd alternativet **-utförlig** om du vill visa ytterligare information om processåtgärder.
  >
  >   Exempel:
  >
  >   **nlserver startar om webb-verbose**
  >
  >   **nlserver start mta@myinstance -verbose**
  >
  >   Med det här alternativet läggs ytterligare loggar till. Vi rekommenderar att du startar processerna igen utan alternativet **-verbose** när du har hittat den önskade informationen, för att undvika överlagring av loggar.

* Starta alla Adobe Campaign-processer (motsvarar att starta tjänsten **nlserver6**):

  **nlserver watchdog -noconsole**

* Stäng alla Adobe Campaign-processer (motsvarar att stänga av tjänsten **nlserver6**):

  **ingen avstängning av server**

* Läs in modulkonfigurationen **nlserver web** igen (och webbservertilläggets modul, där det är tillämpligt) när filerna **serverConf.xml** och **config-`<instance>  .xml </instance>`** har redigerats.

  **nlserver config -reload**

  >[!NOTE]
  >
  >Vissa konfigurationsändringar tas inte med i beräkningen dynamiskt. Adobe Campaign måste stängas av och sedan startas om.
