---
title: Uppgraderar
seo-title: Uppgraderar
description: Uppgraderar
seo-description: null
page-status-flag: never-activated
uuid: f24552d4-6bdf-411c-a1f2-b8f339c311f4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: f8e3633d-7232-44a5-842b-1a70c4f2bca2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Uppgraderar{#upgrading}

Innan du startar uppgraderingsprocessen bör du fastställa och bekräfta vilken version av Adobe Campaign som ska uppgraderas till och läsa [versionsinformationen](https://docs.campaign.adobe.com/doc/AC/en/RN.html).

>[!CAUTION]
>
>Vi rekommenderar att du gör en säkerhetskopiering av databasen för varje instans innan du uppdaterar. Mer information finns i [Säkerhetskopiera](../../production/using/backup.md).\
>Om du vill uppgradera kontrollerar du att du har behörighet och behörighet att komma åt instanser och loggar.

>[!NOTE]
>
>Se även [installationsguiden](../../installation/using/general-architecture.md) och hur du kommer igång med [uppgraderingen](http://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) .

## I Windows {#in-windows}

Om du vill uppdatera Adobe Campaign i en ny version när du levererar en ny version bör du göra följande i Windows:

* [Stäng av tjänster](#shut-down-services),
* [Uppgradera serverprogrammet](#upgrade-the-adobe-campaign-server-application)Adobe Campaign,
* [Synkronisera resurser](#synchronize-resources),
* [Starta om tjänsterna](#restart-services).

Information om hur du uppdaterar klientkonsolen finns i [det här avsnittet](../../installation/using/client-console-availability-for-windows.md).

### Stäng av tjänster {#shut-down-services}

Om du vill ersätta alla filer med den nya versionen måste du stänga alla instanser av servertjänsten.

1. Stäng av följande tjänster:

   * Webbtjänster (IIS):

      **iisreset /stop**

   * Adobe Campaign-tjänsten: **net stop nlserver6**
   >[!CAUTION]
   >
   >Du måste också se till att omdirigeringsservern (webmdl) stoppas så att filen **nlsrvmod.dll** som används av IIS kan ersättas med den nya versionen.

1. Kontrollera att inga åtgärder är aktiva genom att köra kommandot **nlserver pdump** . Följande bör komma upp:

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   Du kan använda Aktivitetshanteraren i Windows för att kontrollera att alla processer har stoppats.

### Uppgradera serverprogrammet Adobe Campaign {#upgrade-the-adobe-campaign-server-application}

Så här kör du uppgraderingsfilen:

1. Kör **setup.exe**.

   Om du vill hämta den här filen går du till Adobe Campaign Support-sidan ( [https://support.neolane.net/](https://support.neolane.net/)) via länken **Download Center** .

1. Välj installationsläge: välj **[!UICONTROL Update or repair]**
1. Klicka på **[!UICONTROL Next]** .
1. Klicka på **[!UICONTROL Finish]** .

   Installationsprogrammet kopierar sedan de nya filerna.

1. När åtgärden är klar klickar du på **[!UICONTROL Finish]** .

### Synkronisera resurser {#synchronize-resources}

Använd följande kommandorad:

**nlserver config -postupgrade -allinstances**

Detta gör att du kan utföra följande åtgärder:

* Synkronisera resurser,
* uppdateringsscheman,
* uppdatera databasen.

>[!NOTE]
>
>Den här åtgärden bör endast utföras en gång och endast på en (**nlserver web**) programserver.

Kontrollera sedan om synkroniseringen har genererat fel eller varningar. Mer information finns i [Lösa uppgraderingskonflikter](#resolving-upgrade-conflicts).

### Starta om tjänster {#restart-services}

De tjänster som ska startas om är:

* Webbtjänster (IIS):

   **iisreset /start**

* Adobe Campaign-tjänsten: nästa **start nlserver6**

## I Linux {#in-linux}

Så här uppdaterar du Adobe Campaign i en ny version när en ny version levereras:

* [Hämta uppdaterade paket](#obtain-updated-packages),
* [Uppdatera](#perform-an-update),
* [Starta om webbservern](#reboot-the-web-server).

Information om hur du uppdaterar klientkonsolen finns i [det här avsnittet](../../installation/using/client-console-availability-for-linux.md).

>[!NOTE]
>
>Från och med bygge 8757 behövs inte längre något tredjepartsbibliotek.

### Hämta uppdaterade paket {#obtain-updated-packages}

Börja med att återställa båda de uppdaterade paketen i Adobe Campaign: gå till Adobe Campaign Support-sidan ( [https://support.neolane.net/](https://support.neolane.net/)) via länken **Download Center** .

Filen är **nlserver6-v7-XXX.rpm**

### Utför en uppdatering {#perform-an-update}

* RPM-baserad distribution (RedHat, SuSe)

   Kör som rot för att installera dem:

   ```
   $rpm -Uvh nlserver6-v7-XXXX.rpm
   ```

   där XXX är versionen av filen.

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
>Fullständiga installationsprocedurer beskrivs i [detta avsnitt](../../installation/using/installing-campaign-standard-packages.md). Resurserna synkroniseras automatiskt, men du måste se till att inga fel inträffar. Mer information finns i [Lösa uppgraderingskonflikter](#resolving-upgrade-conflicts).

### Starta om webbservern {#reboot-the-web-server}

Du måste stänga Apache för att det nya biblioteket ska kunna användas.

Om du vill göra det kör du följande kommando:

```
/etc/init.d/apache stop
```

>[!CAUTION]
>
>* Skriptet kan heta **httpd** istället för **apache**.
>* Du MÅSTE köra det här kommandot tills du får följande svar:
   >Den här åtgärden krävs för att Apache ska kunna använda det nya biblioteket.
>



Starta sedan om Apache:

```
/etc/init.d/apache start
```

## Lösa uppgraderingskonflikter {#resolving-upgrade-conflicts}

Under resurssynkroniseringen kan du med kommandot **postupgrade** upptäcka om synkroniseringen har genererat fel eller varningar.

### Visa synkroniseringsresultatet {#view-the-synchronization-result}

Det finns två sätt att visa synkroniseringsresultatet:

* I kommandoradsgränssnittet materialiseras felen med en trippelkniv **>>>** och synkroniseringen stoppas automatiskt. Varningar materialiseras med en dubbel skiftning **>>** och måste åtgärdas när synkroniseringen är klar. När uppgraderingen är klar visas en sammanfattning i kommandotolken. Den kan se ut så här:

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   Om varningen gäller en resurskonflikt måste användaren åtgärda den.

* Loggfilen **postupgrade_`<server version number>_<time of postupgrade>`.log** innehåller synkroniseringsresultatet. Den är som standard tillgänglig i följande katalog: **`<installation directory>/var/<instance/postupgrade`**. Fel och varningar indikeras av fel- och varningsattributen.

### Lösa konflikter {#resolving-conflicts}

Använd följande process för att lösa konflikter:

1. Gå till Adobe Campaign-trädet **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. Markera den konflikt som du vill lösa i listan.

Det finns tre sätt att lösa en konflikt:

* **[!UICONTROL Declare as resolved]** : kräver att användaren gör något i förväg.
* **[!UICONTROL Accept the new version]** : rekommenderas om resurserna i Adobe Campaign inte har ändrats av användaren.
* **[!UICONTROL Keep the current version]** : betyder att uppdateringen inte godkänns.

   >[!CAUTION]
   >
   >Om du väljer det här upplösningsläget kanske du inte har någon nytta av korrigeringar i den nya versionen.

Om du väljer att lösa konflikten manuellt gör du så här:

1. I fönstrets nedre del söker du efter **_konfliktsträngen_** för att hitta enheterna med konflikter. Entiteten som installerades med den nya versionen innehåller det **nya** argumentet, entiteten som matchar den tidigare versionen innehåller **cus** -argumentet.

   ![](assets/s_ncs_production_conflict002.png)

1. Ta bort den version som du inte vill behålla. Ta bort strängen **_conflict_argument_** för entiteten som du håller kvar.

   ![](assets/s_ncs_production_conflict003.png)

1. Gå till konflikten som du har löst. Klicka på **[!UICONTROL Actions]** ikonen och välj **[!UICONTROL Declare as resolved]** .
1. Spara ändringarna: konflikten är nu löst.

### God praxis {#best-practices}

Ett uppdateringsfel kan vara länkat till databaskonfigurationen. Kontrollera att konfigurationerna som utförs av den tekniska administratören och databasadministratören är kompatibla.

En Unicode-databas får till exempel inte bara tillåta lagring av LATIN1-data.

## Varna klientkonsolerna om den tillgängliga uppdateringen {#warn-the-client-consoles-of-the-available-update}

### I Windows {#in-windows-1}

Hämta och kopiera filen på den dator där (**nlserver web**) Adobe Campaign-programservern är installerad

**setup-client-6.** XXXX **.exe**

in **[path of the application]**datakitnlengthsp

Nästa gång klientkonsolerna är anslutna visas ett fönster som informerar användarna om tillgängligheten till en uppdatering och ger dem möjlighet att ladda ned och installera den.

>[!NOTE]
>
>Kontrollera att IIS_XPG-användaren har rätt läsbehörighet för den här installationsfilen och se [installationsguiden](../../installation/using/general-architecture.md) för mer information.

### I Linux {#in-linux-1}

Hämta följande paket på den dator där Adobe Campaign-programservern (**nlserver web**) är installerad:

**setup-client-6.** XXXX **.exe**

och kopiera den, spara som **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

Nästa gång klientkonsolerna är anslutna visas ett fönster som informerar användarna om tillgängligheten till en uppdatering och ger dem möjlighet att ladda ned och installera den.

>[!NOTE]
>
>Kontrollera att Apache-användaren har rätt läsbehörighet för den här installationsfilen och se [installationsguiden](../../installation/using/general-architecture.md) för mer information.

