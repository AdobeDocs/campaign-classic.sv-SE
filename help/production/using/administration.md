---
solution: Campaign Classic
product: campaign
title: Administration
description: Administration
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---


# Administration{#administration}

Automatisk start av Adobe Campaign-modulerna (**webb**, **mta**, **wfserver** osv.) tillhandahålls av **nlserver** -servern.

När du installerar Adobe Campaign konfigureras datorn automatiskt så att **nlserver** -tjänsten startar under startsekvensen.

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

* Visa alla påbörjade Adobe Campaign-moduler: **/etc/init.d/nlserver6 pdump** eller **/etc/init.d/nlserver6 status**

   >[!NOTE]
   >
   >Genom att lägga till parametern **-who** till kommandot **pdump** kan du samla in information om aktuella anslutningar (användare och processer).\
   >Statuskommandot **/etc/init.d/nlserver6** (utan parametern &quot;-who&quot;) returnerar:
   >
   >    * 0 om alla processer körs.
   >    * 1 om en process saknas.
   >    * 2 om ingen process körs.
   >    * ett annat värde om ett fel uppstår.


* Starta/stoppa en modul med flera instanser eller en instans (**web**, **trackinglog**, **syslogd**, **mta**, **wfserver******,¥inmail¥):

   **nlserver start`<module>[@<instance>]`**

   **nlserver stop`<module>[@<instance>][-immediate][-noconsole]`**

   Du kan också använda kommandot **för att starta om`<module>[@<instance>]`** en modul.

   Exempel:

   **nlserver start web**

   **nlserver start mta@my_instance**

   **nlserver stop syslogd**

   **nlserver stop wfserver@my_instance**

   **nlserver stop web-Instant**

   **omstart av webbserver**

   >[!NOTE]
   > 
   >    * Om instansen inte anges används standardinstansen.
   >    * I en nödsituation använder du alternativet **-omedelbar** för att framtvinga ett omedelbart stopp i processen (motsvarande Unix-kommandot **Kill -9**).
   >    * Använd alternativet **-noconsole** för att se till att den modul som startas inte visar något på konsolen. Loggarna skrivs till disken via **systemmodulen** .
   >    * Använd alternativet **-utförlig** om du vill visa ytterligare information om processåtgärder.

      >    
      >      
      Exempel:
      >    
      >      
      **webbverbose för omstart av nlserver**
      >    
      >      
      **nlserver start mta@myinstance -verbose**
      >    
      >      
      Med det här alternativet läggs ytterligare loggar till. Vi rekommenderar att du startar processerna igen utan det **-exakta** alternativet när du har hittat den önskade informationen, så att du undviker överlagring av loggar.


* Starta alla Adobe Campaign-processer (samma som att starta tjänsten **nlserver6** ):

   **nlserver watchdog -noconsole**

* Stäng alla Adobe Campaign-processer (motsvarar att stänga av **tjänsten nlserver6** ):

   **avstängning av nlserver**

* Läs in **webbmodulens** konfiguration (och webbservertilläggets modul, om tillämpligt) igen när **serverConf.xml** - och **config-`<instance>  .xml </instance>`** filer har redigerats.

   **nlserver config -reload**

   >[!NOTE]
   >
   >Vissa konfigurationsändringar beaktas inte dynamiskt. Adobe Campaign måste stängas av och sedan startas om.

