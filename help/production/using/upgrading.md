---
product: campaign
title: Uppgradera till en ny version
description: Lär dig tekniska steg att uppgradera till en ny version
feature: Monitoring, Upgrade
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 1%

---

# Uppgradera till en ny version (lokalt){#upgrading}



Innan du påbörjar uppgraderingen bör du kontrollera vilken version av Adobe Campaign som ska uppgraderas och läsa [Versionsinformation](../../rn/using/latest-release.md) .

>[!IMPORTANT]
>
>* Adobe rekommenderar starkt att du gör en säkerhetskopia av databasen för varje instans innan du uppdaterar. Mer information hittar du i [det här avsnittet](../../production/using/backup.md).
>* Om du vill uppgradera kontrollerar du att du har behörighet och behörighet att komma åt instanser och loggar.
>* Läs [det här avsnittet](../../installation/using/general-architecture.md) och [uppgradering](https://helpx.adobe.com/se/campaign/kb/acc-build-upgrade.html) kapitlet innan du börjar.
>

## Windows {#in-windows}

I en Windows-miljö följer du stegen nedan för att uppdatera Adobe Campaign till en ny version:

* [Stäng av tjänster](#shut-down-services),
* [Uppgradera programservern](#upgrade-the-adobe-campaign-server-application),
* [Synkronisera resurser](#synchronize-resources),
* [Starta om tjänster](#restart-services).

Information om hur du uppdaterar klientkonsolen finns i [det här avsnittet](../../installation/using/client-console-availability-for-windows.md).

### Stäng av tjänster {#shut-down-services}

Om du vill ersätta alla filer med den nya versionen måste du stänga alla instanser av servertjänsten.

1. Stäng av följande tjänster:

   * Webbtjänster (IIS):

     **iisreset /stop**

   * Adobe Campaign-tjänst: **net stop nlserver6**

   >[!IMPORTANT]
   >
   >Du måste också se till att omdirigeringsservern (webmdl) är stoppad så att **nlsrvmod.dll** som används av IIS kan ersättas med den nya versionen.

1. Kontrollera att inga aktiviteter är aktiva genom att köra **nlserver pdump** -kommando. Följande bör komma upp:

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   Du kan använda Aktivitetshanteraren i Windows för att kontrollera att alla processer har stoppats.

### Uppgradera Adobe Campaign serverprogram {#upgrade-the-adobe-campaign-server-application}

Så här kör du uppgraderingsfilen:

1. Kör **setup.exe**.

   Om du vill hämta filen ansluter du till [Programdistributionsportal](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) med dina inloggningsuppgifter. Läs mer om programvarudistribution i [den här sidan](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html).

1. Välj installationsläge: välj **[!UICONTROL Update or repair]**
1. Klicka **[!UICONTROL Next]** .
1. Klicka **[!UICONTROL Finish]** .

   Installationsprogrammet kopierar sedan de nya filerna.

1. När åtgärden är klar klickar du på **[!UICONTROL Finish]** .

### Synkronisera resurser {#synchronize-resources}

Använd följande kommandorad:

**nlserver config -postupgrade -allinstances**

Detta gör att du kan utföra följande åtgärder:

* Synkronisera resurser
* Uppdatera scheman
* uppdatera databasen

>[!NOTE]
>
>Den här åtgärden bör endast utföras en gång och endast på en (**nlserver web**).

Kontrollera sedan om synkroniseringen har genererat fel eller varningar. Mer information finns i [Lösa uppgraderingskonflikter](#resolving-upgrade-conflicts).

### Starta om tjänster {#restart-services}

De tjänster som ska startas om är:

* Webbtjänster (IIS):

  **iisreset /start**

* Adobe Campaign-tjänst: **net start nlserver6**

## Linux {#in-linux}

I en Linux-miljö följer du stegen nedan för att uppdatera Adobe Campaign till en ny version:

* [Ladda ned uppdaterade paket](#obtain-updated-packages),
* [Utför uppdateringen](#perform-an-update),
* [Starta om webbservern](#reboot-the-web-server).

[Läs mer om tillgänglighet för klientkonsolen](../../installation/using/client-console-availability-for-windows.md).

>[!NOTE]
>
>Från och med bygge 8757 behövs inte längre något tredjepartsbibliotek.

### Hämta uppdaterade paket {#obtain-updated-packages}

Börja med att återställa båda de uppdaterade paketen av Adobe Campaign: anslut till [Programdistributionsportal](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) med dina inloggningsuppgifter. Läs mer om programvarudistribution i [den här sidan](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html).

Filen är **nlserver6-v7-XXX.rpm**

### Utför en uppdatering {#perform-an-update}

* RPM-baserad distribution (RedHat, SuSe)

  Kör som rot för att installera dem:

  ```
  $rpm -Uvh nlserver6-v7-XXXX.rpm
  ```

  Där XXX är versionen av filen.

  RPM-filen är beroende av paket som du kan hitta på CentOS/Red Hat-distributioner. Om du inte vill använda vissa av dessa beroenden kan du behöva använda alternativet &quot;nodeps&quot; för rpm:

  ```
  rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
  ```

* DEB-baserad distribution (Debian)

  Kör som rot för att installera dem:

  ```
  dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
  ```

>[!NOTE]
>
>Fullständiga installationsprocedurer beskrivs i [det här avsnittet](../../installation/using/installing-campaign-standard-packages.md). Resurserna synkroniseras automatiskt, men du måste se till att inga fel inträffar. Mer information finns i [Lös uppgraderingskonflikter](#resolving-upgrade-conflicts).

### Starta om webbservern {#reboot-the-web-server}

Du måste stänga Apache för att det nya biblioteket ska kunna användas.

Om du vill göra det kör du följande kommando:

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* Skriptet kan anropas **httpd** i stället för **apache**.
>* Du MÅSTE köra det här kommandot tills du får följande svar:
>
>   Den här åtgärden krävs för att Apache ska kunna använda det nya biblioteket.

Starta sedan om Apache:

```
/etc/init.d/apache start
```

## Lös uppgraderingskonflikter {#resolving-upgrade-conflicts}

Under resurssynkroniseringen **postuppgradering** Med -kommandot kan du identifiera om synkroniseringen har genererat fel eller varningar.

### Visa synkroniseringsresultatet {#view-the-synchronization-result}

Det finns två sätt att visa synkroniseringsresultatet:

* I kommandoradsgränssnittet materialiseras fel med en trippelvinklad **>>** och synkroniseringen stoppas automatiskt. Varningar materialiseras av en dubbel skiftning **>>** och måste lösas när synkroniseringen är klar. När uppgraderingen är klar visas en sammanfattning i kommandotolken. Den kan se ut så här:

  ```
  2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
  2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
  2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
  2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
  2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
  2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
  ```

  Om varningen gäller en resurskonflikt måste användaren åtgärda den.

* The **postupgrade_`<server version number>_<time of postupgrade>`.log** loggfilen innehåller synkroniseringsresultatet. Den är som standard tillgänglig i följande katalog: **`<installation directory>/var/<instance/postupgrade`**. Fel och varningar indikeras av fel- och varningsattributen.

### Lös konflikter {#resolving-conflicts}

Använd följande process för att lösa konflikter:

1. Gå till Adobe Campaign **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. Markera den konflikt som du vill lösa i listan.

Det finns tre sätt att lösa en konflikt:

* **[!UICONTROL Declare as resolved]** : kräver åtgärd från användaren i förväg.
* **[!UICONTROL Accept the new version]** : rekommenderas om resurserna som tillhandahålls med Adobe Campaign inte har ändrats av användaren.
* **[!UICONTROL Keep the current version]** : betyder att uppdateringen inte godkänns.

  >[!IMPORTANT]
  >
  >Om du väljer det här upplösningsläget kanske du inte har någon nytta av korrigeringar i den nya versionen.

Om du väljer att lösa konflikten manuellt gör du så här:

1. Sök efter **_konflikt_** sträng för att hitta entiteter med konflikter. Enheten som installerats med den nya versionen innehåller **new** argument, entiteten som matchar den tidigare versionen innehåller **kus** argument.

   ![](assets/s_ncs_production_conflict002.png)

1. Ta bort den version som du inte vill behålla. Ta bort **_conflict_argument_** sträng för den entitet som du håller.

   ![](assets/s_ncs_production_conflict003.png)

1. Gå till konflikten som du har löst. Klicka på **[!UICONTROL Actions]** ikon och markera **[!UICONTROL Declare as resolved]** .
1. Spara dina ändringar: konflikten är nu löst.

### Bästa praxis {#best-practices}

Ett uppdateringsfel kan vara länkat till databaskonfigurationen. Kontrollera att konfigurationerna som utförs av den tekniska administratören och databasadministratören är kompatibla.

En Unicode-databas får till exempel inte bara tillåta lagring av LATIN1-data.

## Varna klientkonsolerna om den tillgängliga uppdateringen {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

På datorn där Adobe Campaign programserver är installerad (**nlserver web**), hämta och kopiera filen  **setup-client-6.XXXX.exe** i n **[programmets sökväg]/datakit/nl/eng/jsp**.

Nästa gång klientkonsolerna är anslutna visas ett fönster som informerar användarna om tillgängligheten till en uppdatering och ger dem möjlighet att ladda ned och installera den.

>[!NOTE]
>
>Kontrollera att IIS_XPG-användaren har rätt läsbehörighet för den här installationsfilen och läs mer i [installationsguide](../../installation/using/general-architecture.md) för mer information.

### Linux {#in-linux-1}

På datorn där Adobe Campaign-programservern finns (**nlserver web**) är installerat, hämta  **setup-client-6.XXXX.exe** paketera och kopiera det, spara som **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

Nästa gång klientkonsolerna är anslutna visas ett fönster som informerar användarna om tillgängligheten till en uppdatering och ger dem möjlighet att ladda ned och installera den.

>[!NOTE]
>
>Kontrollera att Apache-användaren har rätt läsbehörighet för den här installationsfilen och se [installationsguide](../../installation/using/general-architecture.md) för mer information.
