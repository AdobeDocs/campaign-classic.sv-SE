---
title: Migrera i Linux för Adobe Campaign v7
seo-title: Migrera i Linux för Adobe Campaign v7
description: Migrera i Linux för Adobe Campaign v7
seo-description: null
page-status-flag: never-activated
uuid: 47870ea4-b07b-4db7-8094-7a8b6f4b6936
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: 8f6519e8-5c8d-4974-b193-a9f1cf78b3a3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# Migrera i Linux för Adobe Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

## Allmänt förfarande {#general-procedure}

Migreringsstegen i Linux är följande:

1. Stoppa tjänster: se [Tjänststopp](#service-stop).
1. Spara databasen: se [Säkerhetskopiera databasen och den befintliga installationen](#back-up-the-database-and-the-existing-installation).
1. Avinstallera tidigare versionspaket för Adobe Campaign: se [Avinstallera paket](#uninstalling-adobe-campaign-previous-version-packages)för tidigare versioner av Adobe Campaign.
1. Migrera plattformen: se [Distribuera Adobe Campaign v7](#deploying-adobe-campaign-v7).
1. Starta om tjänsten: se [Omstarttjänster](#re-starting-services).

## Tjänststopp {#service-stop}

Stoppa först alla processer med tillgång till databasen på alla berörda datorer.

1. Logga in som **rot**.
1. Alla servrar som använder omdirigeringsmodulen (**webmdl** -tjänsten) måste stoppas. För Apache kör du följande kommando:

   ```
   /etc/init.d/apache2 stop
   ```

1. Logga in igen som **rot**.
1. Stoppa tidigare versionstjänster för Adobe Campaign på alla servrar.

   ```
   /etc/init.d/nlserver6 stop
   ```

   Om du migrerar från v5.11 kör du följande kommando:

   ```
   /etc/init.d/nlserver5 stop
   ```

1. Kontrollera att Adobe Campaign-tjänsterna är stoppade på varje server.

   ```
   ps waux | grep nlserver
   ```

   Listan över aktiva processer visas tillsammans med deras ID (PID).

1. Om en eller flera Adobe Campaign-processer fortfarande är aktiva eller blockerade efter några minuter ska du döda dem.

   ```
   killall nlserver
   ```

1. Om vissa processer fortfarande är aktiva efter några minuter kan du tvinga dem att stängas med kommandot:

   ```
   killall -9 nlserver
   ```

## Säkerhetskopiera databasen och den befintliga installationen {#back-up-the-database-and-the-existing-installation}

Proceduren beror på din tidigare version av Adobe Campaign.

### Migrera från Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Säkerhetskopiera Adobe Campaign-databasen.
1. Logga in som **neolane** och gör en säkerhetskopia av **katalogen nl5** med följande kommando:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >Som en försiktighetsåtgärd rekommenderar vi att du packar mappen **nl5.back** och sparar den på en annan säker plats än servern.

1. Redigera **config-`<instance name>`.xml** (i mappen **nl5.back** ) för att förhindra **mta**, **wfserver**, **** stat¥ osv. från att starta automatiskt. Ersätt till exempel **autoStart** med **_autoStart** (fortfarande som **neolane**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### Migrera från Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Säkerhetskopiera Adobe Campaign-databasen.
1. Logga in som **neolane** och gör en säkerhetskopia av katalogen **nl6** med följande kommando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Som en försiktighetsåtgärd rekommenderar vi att du packar mappen **nl6.back** och sparar den på en annan säker plats än servern.

1. Redigera **config-`<instance name>`.xml** (i mappen **nl6.back** ) för att förhindra **mta**, **wfserver**, **** stat osv. från att starta automatiskt. Ersätt till exempel **autoStart** med **_autoStart** (fortfarande som **Adobe Campaign**).

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

### Migrera från Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Säkerhetskopiera Adobe Campaign-databasen.
1. Logga in som **neolane** och gör en säkerhetskopia av katalogen **nl6** med följande kommando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Som en försiktighetsåtgärd rekommenderar vi att du packar mappen **nl6.back** och sparar den på en annan säker plats än servern.

## Avinstallerar paket för tidigare versioner av Adobe Campaign {#uninstalling-adobe-campaign-previous-version-packages}

Proceduren beror på din tidigare version av Adobe Campaign.

### Avinstallerar Adobe Campaign v5-paket {#uninstalling-adobe-campaign-v5-packages}

1. Logga in som **rot**.
1. Identifiera Adobe Campaign-paketen som installerats med följande kommando.

   * I **Debian**:

      ```
      dpkg -l | grep nl
      ```

      Listan med installerade paket visas:

      ```
      ii  nlserver5                       5762                     nlserver5-5762
      ii  nlthirdparty5                   5660                     nlthirdparty5-5660
      ```

   * I **Red Hat**:

      ```
      rpm -qa | grep nl
      ```

1. Avinstallera Adobe Campaign v5-paket.

   * I **Debian**:

      ```
      dpkg --purge nlserver5 nlthirdparty5
      ```

   * I **Red Hat**:

      ```
      rprm -ev nlserver5 nlthirdparty5
      ```

### Avinstallerar Adobe Campaign v6-paket {#uninstalling-adobe-campaign-v6-packages}

I det här avsnittet visas hur du avinstallerar Adobe Campaign v6.02- eller v6.1-paket.

1. Logga in som **rot**.
1. Identifiera Adobe Campaign-paketen som installerats med följande kommando.

   * I **Debian**:

      ```
      dpkg -l | grep nl
      ```

      Listan med installerade paket visas:

      ```
      ii  nlserver6                       XXXX                     nlserver6-XXXX
      ii  nlthirdparty6                   XXXX                     nlthirdparty6-XXXX
      ```

   * I **Red Hat**:

      ```
      rpm -qa | grep nl
      ```

1. Avinstallera Adobe Campaign v6-paket.

   * I **Debian**:

      ```
      dpkg --purge nlserver6 nlthirdparty6
      ```

   * I **Red Hat**:

      ```
      rprm -ev nlserver6 nlthirdparty6
      ```

## Distribuera Adobe Campaign v7 {#deploying-adobe-campaign-v7}

Proceduren beror på din tidigare version av Adobe Campaign.

### Migrera från Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

Distributionen av Adobe Campaign omfattar två faser:

* Installera Adobe Campaign v7-paket: den här åtgärden måste utföras på varje server.
* Uppgraderingen: det här kommandot måste startas för varje instans.

Så här distribuerar du Adobe Campaign:

1. Installera de senaste Adobe Campaign v7-paketen med följande kommando:

   * I **Debian**:

      ```
      dpkg -i nlserver6-XXXX-linux-2.6-intel.deb
      ```

   * I **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-0.x86_64.rpm
      ```
   >[!IMPORTANT]
   >
   >Du måste installera paketen utan problem innan du går vidare till nästa steg.

   >[!NOTE]
   >
   >Vid migrering från v5.11 installeras Adobe Campaign som standard i katalogen **/usr/local/neolane/nl6/** .
   >
   >När paketen har installerats visas följande meddelande: Alternativet **&#39;WdbcTimeZone&#39; saknas**. Detta är normalt.

1. Om du vill göra installationsprogrammet för klientkonsolen tillgängligt kopierar du det till installationskatalogen för Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Mer information om hur du installerar Adobe Campaign i Linux finns i [det här avsnittet](../../installation/using/installing-campaign-standard-packages.md).

1. Ändra **.base** -filen som matchar **neolane** -användaren. Logga in som **neolane** och kör följande kommando:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >När du loggar in som **neolane** visas följande meddelande: **nl5/env.sh: Ingen sådan fil eller katalog**. Detta är normalt.

   Ersätt **nl5/env.sh** med **nl6/env.sh** i slutet av filen.

1. Logga in som **rot** och förbered instansen med följande kommandon:

   ```
   /etc/init.d/nlserver6 start   
   Starting nlserver6: [  OK  ]
   ```

   ```
   /etc/init.d/nlserver6 stop
   Stopping nlserver6: [  OK  ]
   ```

   >[!NOTE]
   >
   >Med dessa kommandon kan du skapa det interna filsystemet i Adobe Campaign v6: **conf** -katalogen (med **filerna config-default.xml** och **serverConf.xml** ), **var** -katalogen.

1. Gå till säkerhetskopieringsmappen **nl5.back** och kopiera (skriv över) konfigurationsfilerna och undermapparna för varje instans. Logga in som **neolane** och kör följande kommando:

   >[!IMPORTANT]
   >
   >Kopiera inte filen **config-default.xml** för det första kommandot nedan.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. I Adobe Campaign v7 **serverConf.xml** - och **config-default.xml** -filerna använder du de specifika konfigurationer du hade för Adobe Campaign v5. För **filen serverConf.xml** använder du filen **nl5/conf/serverConf.xml.diff** .

   >[!NOTE]
   >
   >När du rapporterar konfigurationer från Adobe Campaign v5 till Adobe Campaign v7 ska du kontrollera att sökvägarna till de fysiska katalogerna leder till Adobe Campaign v7 och inte till Adobe Campaign v5.

1. Eftersom migrering inte är en allmän installation måste du tvinga fram en omstart av **spårloggstjänsten** . Det gör du genom att öppna filen **nl6/conf/config-default.xml** och se till att tjänsten **Trackinglog** är aktiverad (endast på spårnings-/omdirigeringsservrar):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Om **spårningsloggtjänsten** inte har startats på spårningsservern vidarebefordras ingen spårningsinformation.

1. Läs in konfigurationen för Adobe Campaign v7 igen med följande kommando:

   ```
   nlserver config -reload
   ```

1. Starta efteruppgraderingen med följande kommando (fortfarande som **neolan**):

   ```
   su - neolane
   nlserver config -timezone:<time zone> -postupgrade -instance:<instance name>
   ```

   >[!IMPORTANT]
   >
   >Du måste ange vilken tidszon som ska användas som referens under efteruppgraderingen (med alternativet **-timezone** ). I det här fallet använder vi tidszonen Europa/Paris **: &quot;Europa/Paris&quot;**.

   >[!NOTE]
   >
   >Vi rekommenderar starkt att du uppgraderar din bas till&quot;multi-timezone&quot;. Mer information om tidszonsalternativ finns i avsnittet [Tidszoner](../../migration/using/general-configurations.md#time-zones) .

>[!IMPORTANT]
>
>Starta inte Adobe Campaign-tjänsterna än: Ändringar måste fortfarande göras i Apache.

### Migrera från Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

Distributionen av Adobe Campaign omfattar två faser:

* Installera Adobe Campaign v7-paket: den här åtgärden måste utföras på varje server.
* Uppgraderingen: det här kommandot måste startas för varje instans.

Så här distribuerar du Adobe Campaign:

1. Installera de senaste Adobe Campaign v7-paketen med följande kommando:

   * I **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * I **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >Du måste installera paketen utan problem innan du går vidare till nästa steg.

   >[!NOTE]
   >
   >Adobe Campaign v7 installeras som standard i samma katalog som Adobe Campaign v6.02: **/usr/local/neolane/nl6/**.

1. Om du vill göra installationsprogrammet för klientkonsolen tillgängligt kopierar du det till installationskatalogen för Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Mer information om hur du installerar Adobe Campaign i Linux finns i [det här avsnittet](../../installation/using/installing-campaign-standard-packages.md).

1. Eftersom migrering inte är en allmän installation måste du tvinga fram en omstart av **spårloggstjänsten** . Det gör du genom att öppna filen **nl6/conf/config-default.xml** och se till att tjänsten **Trackinglog** är aktiverad (endast på spårnings-/omdirigeringsservrar):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Om **spårningsloggtjänsten** inte har startats på spårningsservern vidarebefordras ingen spårningsinformation.

1. Gå till säkerhetskopieringsmappen **nl6.back** och kopiera (skriv över) konfigurationsfilerna och undermapparna för varje instans. Logga in som **neolane** och kör följande kommando:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Läs in konfigurationen för Adobe Campaign v7 igen med följande kommando:

   ```
   nlserver config -reload
   ```

1. Starta efteruppgraderingen med följande kommando (fortfarande som **neolan**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

   >[!NOTE]
   >
   >Flertidszonsläget var endast tillgängligt i v6.02 för PostgreSQL-databasmotorer. Det är nu tillgängligt oavsett vilken version av databasmotorn som används. Vi rekommenderar starkt att du uppgraderar din bas till&quot;multi-timezone&quot;. Mer information om tidszonsalternativ finns i avsnittet [Tidszoner](../../migration/using/general-configurations.md#time-zones) .

### Migrera från Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-1}

Distributionen av Adobe Campaign omfattar två faser:

* Installera Adobe Campaign v7-paket: den här åtgärden måste utföras på varje server.
* Uppgraderingen: det här kommandot måste startas för varje instans.

Så här distribuerar du Adobe Campaign:

1. Installera de senaste Adobe Campaign v7-paketen med följande kommando:

   * I **Debian**:

      ```
      dpkg -i nlserver6-XXXX-amd64_debX.deb
      ```

   * I **Red Hat**:

      ```
      rpm -Uvh nlserver6-XXXX-x86_64_rhX.rpm
      ```
   >[!IMPORTANT]
   >
   >Du måste installera paketen utan problem innan du går vidare till nästa steg.

   >[!NOTE]
   >
   >Adobe Campaign v7 installeras som standard i katalogen **/usr/local/neolane/nl6/** .

1. Om du vill göra installationsprogrammet för klientkonsolen tillgängligt kopierar du det till installationskatalogen för Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Mer information om hur du installerar Adobe Campaign i Linux finns i [det här avsnittet](../../installation/using/installing-campaign-standard-packages.md).

1. Gå till säkerhetskopieringsmappen **nl6.back** och kopiera (skriv över) konfigurationsfilerna och undermapparna för varje instans. Logga in som **neolane** och kör följande kommando:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Läs in konfigurationen för Adobe Campaign v7 igen med följande kommando:

   ```
   nlserver config -reload
   ```

1. Starta efteruppgraderingen med följande kommando (fortfarande som **neolan**):

   ```
   su - neolane
   nlserver config -postupgrade -instance:<instance name>
   ```

## Migrera omdirigeringsservern (Apache) {#migrating-the-redirection-server--apache-}

>[!NOTE]
>
>Det här avsnittet gäller endast vid migrering från Adobe Campaign v5.11.

I det här skedet måste Apache stoppas. Se: Stoppa [tjänsten](#service-stop).

1. Logga in som **rot**.
1. Ändra miljövariablerna i Apache så att de länkas till katalogen **nl6** .

   * I **Debian**:

      ```
      vi /etc/apache2/envvars
      ```

   * I **Red Hat**:

      ```
      vi /usr/local/apache2/bin/envvars
      ```

1. Kör sedan följande kommandon:

   * I **Debian**:

      Ersätt **nl5** med **nl6** i filen nlsrv.load ****.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      Ta bort länken för **filen nlsrv.conf** och skapa en ny.

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * I **Red Hat**:

      Gå till katalogen **/usr/local/apache2/conf** , redigera filen **http.conf** och ersätt **nl5** med **nl6** på följande rader.

      I **RHEL 7/Debian 8**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Gå till filen **alias.conf** och ersätt alla **nl5** med **nl6**. Om du vill göra det i Debian kör du följande kommando:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## Säkerhetszoner {#security-zones}

Om du migrerar från v6.02 eller tidigare måste du konfigurera dina säkerhetszoner innan du startar tjänster. Mer information finns i [Säkerhet](../../migration/using/general-configurations.md#security).

## Tjänster som startas om {#re-starting-services}

Proceduren beror på din tidigare version av Adobe Campaign.

### Migrera från Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-2}

I **filen config-`<instance name>`.xml** återaktiverar du den automatiska starten av **mta**, **wfserver**, **stat** osv. tjänster.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="localhost"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Starta Apache och Adobe Campaign på var och en av följande servrar:

1. Spårnings- och omdirigeringsserver.
1. Server för mellanpublicering.
1. Marknadsföringsserver.

Innan du går vidare till nästa steg kör du ett fullständigt test av den nya installationen, kontrollerar att det inte finns några regressioner och att allt fungerar genom att följa alla rekommendationer i avsnittet [Allmänna konfigurationer](../../migration/using/general-configurations.md) .

### Migrera från Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

I **filen config-`<instance name>`.xml** återaktiverar du den automatiska starten av **mta**, **wfserver**, **stat** osv. tjänster.

```
<?xml version='1.0'?>
<serverconf>
  <shared>
    <dataStore hosts="myServer*" lang="en_US">
      <dataSource name="default">
        <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
      </dataSource>
    </dataStore>
  </shared>

  <mta autoStart="true" statServerAddress="myStatServer"/>
  <stat autoStart="true"/>
  <wfserver autoStart="true"/>
  <inMail autoStart="true"/>
  <sms autoStart="false"/>
</serverconf>
```

Starta Apache och Adobe Campaign på var och en av följande servrar:

1. Spårnings- och omdirigeringsserver.
1. Server för mellanpublicering.
1. Marknadsföringsserver.

Testa den nya installationen fullständigt, kontrollera att den inte går tillbaka och se till att allt fungerar korrekt genom att följa alla rekommendationer i avsnittet [Allmänna konfigurationer](../../migration/using/general-configurations.md) .

### Migrera från Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-2}

Starta Apache och Adobe Campaign på var och en av följande servrar:

1. Spårnings- och omdirigeringsserver.
1. Server för mellanpublicering.
1. Marknadsföringsserver.

Testa den nya installationen fullständigt, kontrollera att den inte går tillbaka och se till att allt fungerar korrekt genom att följa alla rekommendationer i avsnittet [Allmänna konfigurationer](../../migration/using/general-configurations.md) .

## Ta bort och rensa Adobe Campaign v5 {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>Det här avsnittet gäller endast vid migrering från Adobe Campaign v5.11.

Innan du tar bort och rensar installationen av Adobe Campaign v5 måste du följa följande rekommendationer:

* Få funktionsteamen att göra en fullständig kontroll av den nya installationen.
* Avinstallera bara Adobe Campaign v5 när du är säker på att ingen återställning behövs.

Ta bort katalogen **nl5.back** . Logga in som **neolane** och kör följande kommando:

```
su - neolane
rm -rf nl5.back
```

Starta om servern.
