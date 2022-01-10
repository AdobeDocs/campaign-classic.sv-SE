---
product: campaign
title: Migrera en Linux-plattform till Adobe Campaign v7
description: Lär dig hur du migrerar en Linux-plattform till Adobe Campaign v7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 9dc0699c-0fbf-4f8e-81f7-8ca3d7e98798
source-git-commit: 63aca25a8d1ae24ef83849b35a44d1b37cfa5e96
workflow-type: tm+mt
source-wordcount: '1858'
ht-degree: 0%

---

# Migrera en Linux-plattform till Campaign v7{#migrating-in-linux-for-adobe-campaign-v}

![](../../assets/v7-only.svg)

Migreringsstegen i Linux är följande:

1. Stoppa alla tjänster - [Läs mer](#service-stop).
1. Spara databasen - [Läs mer](#back-up-the-database).
1. Avinstallera tidigare Adobe Campaign-versionspaket - [Läs mer](#uninstalling-adobe-campaign-previous-version-packages).
1. Migrera plattformen - [Läs mer](#deploying-adobe-campaign-v7).
1. Starta om tjänsten - [Läs mer](#re-starting-services).

## Tjänststopp {#service-stop}

Stoppa först alla processer med tillgång till databasen på alla berörda datorer.

1. Logga in som **root**.
1. Alla servrar som använder omdirigeringsmodulen (**webmdl** service) måste stoppas. För Apache kör du följande kommando:

   ```
   /etc/init.d/apache2 stop
   ```

1. Logga in igen som **root**.
1. Stoppa Adobe Campaign tidigare versionstjänster på alla servrar.

   ```
   /etc/init.d/nlserver6 stop
   ```

   Om du migrerar från v5.11 kör du följande kommando:

   ```
   /etc/init.d/nlserver5 stop
   ```

1. Kontrollera att Adobe Campaign tjänster är stoppade på alla servrar.

   ```
   ps waux | grep nlserver
   ```

   Listan över aktiva processer visas tillsammans med deras ID (PID).

1. Om en eller flera Adobe Campaign-processer fortfarande är aktiva eller blockerade efter några minuter kan du döda dem.

   ```
   killall nlserver
   ```

1. Om vissa processer fortfarande är aktiva efter några minuter kan du tvinga dem att stängas med kommandot:

   ```
   killall -9 nlserver
   ```

## Säkerhetskopiera databasen {#back-up-the-database}

Hur du gör det beror på vilken version du har av Adobe Campaign.

### För Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Säkerhetskopiera Adobe Campaign-databasen.
1. Logga in som **neolan** och gör en säkerhetskopia av **nl5** katalog med följande kommando:

   ```
   su - neolane
   mv nl5 nl5.back
   ```

   >[!IMPORTANT]
   >
   >Som en försiktighetsåtgärd rekommenderar vi att du packar upp **nl5.back** och spara den på en annan säker plats än servern.

1. Redigera **config-`<instance name>`.xml** (i **nl5.back** mapp), för att förhindra **mta**, **wfserver**, **stat** osv. från att starta automatiskt. Ersätt till exempel **autoStart** med **_autoStart** (fortfarande som **neolan**).

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

### För Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Säkerhetskopiera Adobe Campaign-databasen.
1. Logga in som **neolan** och gör en säkerhetskopia av **nl6** katalog med följande kommando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Som en försiktighetsåtgärd rekommenderar vi att du packar upp **nl6.back** och spara den på en annan säker plats än servern.

1. Redigera **config-`<instance name>`.xml** (i **nl6.back** för att förhindra **mta**, **wfserver**, **stat**, osv. från att starta automatiskt. Ersätt till exempel **autoStart** med **_autoStart** (fortfarande som **Adobe Campaign**).

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

### För Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Säkerhetskopiera Adobe Campaign-databasen.
1. Logga in som **neolan** och gör en säkerhetskopia av **nl6** katalog med följande kommando:

   ```
   su - neolane
   mv nl6 nl6.back
   ```

   >[!IMPORTANT]
   >
   >Som en försiktighetsåtgärd rekommenderar vi att du packar upp **nl6.back** och spara den på en annan säker plats än servern.

## Avinstallera Adobe Campaign tidigare versionspaket {#uninstalling-adobe-campaign-previous-version-packages}

Hur du gör det beror på vilken version du har av Adobe Campaign.

### För v5-paket {#uninstalling-adobe-campaign-v5-packages}

1. Logga in som **root**.
1. Identifiera de Adobe Campaign-paket som har installerats med följande kommando.

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

### För v6-paket {#uninstalling-adobe-campaign-v6-packages}

I det här avsnittet visas hur du avinstallerar Adobe Campaign v6.02- eller v6.1-paket.

1. Logga in som **root**.
1. Identifiera de Adobe Campaign-paket som har installerats med följande kommando.

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

Hur du gör det beror på vilken version du har av Adobe Campaign.

### Från Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5_11-1}

Distribuera Adobe Campaign i två steg:

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
   >När du migrerar från v5.11 installeras Adobe Campaign i **/usr/local/neolane/nl6/** som standard.
   >
   >När paketen har installerats visas följande meddelande: **Alternativet WdbcTimeZone saknas**. Detta är normalt.

1. Om du vill göra installationsprogrammet för klientkonsolen tillgängligt kopierar du det till installationskatalogen för Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Mer information om hur du installerar Adobe Campaign i Linux finns i [det här avsnittet](../../installation/using/installing-campaign-standard-packages.md).

1. Ändra **.bashrd** som matchar **neolan** användare. Logga in som **neolan** och kör följande kommando:

   ```
   su - neolane
   vim ~/.bashrc
   ```

   >[!NOTE]
   >
   >När du loggar in som **neolan** visas följande meddelande: **nl5/env.sh: Ingen sådan fil eller katalog**. Detta är normalt.

   Ersätt i slutet av filen **nl5/env.sh** med **nl6/env.sh**.

1. Logga in som **root** och förbereda instansen med följande kommandon:

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
   >Med dessa kommandon kan du skapa det interna filsystemet Adobe Campaign v6: **conf** katalog (med **config-default.xml** och **serverConf.xml** filer), **var** katalog.

1. Gå till **nl5.back** säkerhetskopiera mapp och kopiera (skriv över) konfigurationsfilerna och undermapparna för varje instans. Logga in som **neolan** och kör följande kommando:

   >[!IMPORTANT]
   >
   >För det första kommandot nedan ska du inte kopiera **config-default.xml** -fil.

   ```
   su - neolane
   
   cp nl5.back/conf/config-<instance name>.xml nl6/conf/
   cp nl5.back/customer.sh nl6/
   cp -r nl5.back/customers/* nl6/customers/
   cp -r nl5.back/var/* nl6/var/
   ```

1. I Adobe Campaign v7 **serverConf.xml** och **config-default.xml** filer, tillämpa de specifika konfigurationer som du hade för Adobe Campaign v5. För **serverConf.xml** -filen använder du **nl5/conf/serverConf.xml.diff** -fil.

   >[!NOTE]
   >
   >När du rapporterar konfigurationer från Adobe Campaign v5 till Adobe Campaign v7 ska du kontrollera att sökvägarna till de fysiska katalogerna leder till Adobe Campaign v7 och inte till Adobe Campaign v5.

1. Eftersom migreringen inte är en allmän installation måste du tvinga fram en omstart av **trackinglogd** service. Öppna **nl6/conf/config-default.xml** filen och se till att **trackinglogd** tjänsten är aktiverad (endast på spårnings-/omdirigeringsservrar):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Om **trackinglogd** tjänsten har inte startats på spårningsservern. Ingen spårningsinformation kommer att vidarebefordras.

1. Läs in Adobe Campaign v7-konfigurationen igen med följande kommando:

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
   >Du måste ange vilken tidszon som ska användas som referens under efteruppgraderingen (med **-timezone** ). I det här fallet använder vi Europa/Paris-tidszonen **-timezone: &quot;Europa/Paris&quot;**.

   >[!NOTE]
   >
   >Vi rekommenderar starkt att du uppgraderar din bas till&quot;multi-timezone&quot;. Mer information om tidszonsalternativ finns i [Tidszoner](../../migration/using/general-configurations.md#time-zones) -avsnitt.

>[!IMPORTANT]
>
>Starta inte Adobe Campaign tjänster än: Ändringar måste fortfarande göras i Apache.

### Från Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-1}

Distribuera Adobe Campaign i två steg:

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

1. Eftersom migreringen inte är en allmän installation måste du tvinga fram en omstart av **trackinglogd** service. Öppna **nl6/conf/config-default.xml** filen och se till att **trackinglogd** tjänsten är aktiverad (endast på spårnings-/omdirigeringsservrar):

   ```
   <trackinglogd autoStart="true"/>
   ```

   >[!IMPORTANT]
   >
   >Om **trackinglogd** tjänsten har inte startats på spårningsservern. Ingen spårningsinformation kommer att vidarebefordras.

1. Gå till **nl6.back** säkerhetskopiera mapp och kopiera (skriv över) konfigurationsfilerna och undermapparna för varje instans. Logga in som **neolan** och kör följande kommando:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Läs in Adobe Campaign v7-konfigurationen igen med följande kommando:

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
   >Flertidszonsläget var endast tillgängligt i v6.02 för PostgreSQL-databasmotorer. Det är nu tillgängligt oavsett vilken version av databasmotorn som används. Vi rekommenderar starkt att du uppgraderar din bas till&quot;multi-timezone&quot;. Mer information om tidszonsalternativ finns i [Tidszoner](../../migration/using/general-configurations.md#time-zones) -avsnitt.

### Från Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-1}

Distribuera Adobe Campaign i två steg:

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
   >Adobe Campaign v7 installeras i **/usr/local/neolane/nl6/** som standard.

1. Om du vill göra installationsprogrammet för klientkonsolen tillgängligt kopierar du det till installationskatalogen för Adobe Campaign:

   ```
   cp setup-client-7.0.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
   ```

   >[!NOTE]
   >
   >Mer information om hur du installerar Adobe Campaign i Linux finns i [det här avsnittet](../../installation/using/installing-campaign-standard-packages.md).

1. Gå till **nl6.back** säkerhetskopiera mapp och kopiera (skriv över) konfigurationsfilerna och undermapparna för varje instans. Logga in som **neolan** och kör följande kommando:

   ```
   su - neolane
   
   cp nl6.back/conf/config*.xml nl6/conf/
   cp nl6.back/customer.sh nl6/
   cp -r nl6.back/customers/* nl6/customers/
   cp -r nl6.back/var/* nl6/var/
   ```

1. Läs in Adobe Campaign v7-konfigurationen igen med följande kommando:

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

I det här skedet måste Apache stoppas. Se: [Tjänststopp](#service-stop).

1. Logga in som **root**.
1. Ändra miljövariablerna i Apache så att de länkas till **nl6** katalog.

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

      I **nlsrv.load** fil, ersätta **nl5** med **nl6**.

      ```
      vi /etc/apache2/mods-available/nlsrv.load
      ```

      Ta bort länken till **nlsrv.conf** och skapa en ny.

      ```
      rm /etc/apache2/mods-available/nlsrv.conf 
      ln -s /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf /etc/apache2/
      mods-available/nlsrv.conf
      ```

   * I **Red Hat**:

      Gå till **/usr/local/apache2/conf** katalog, redigera **http.conf** fil och ersätta **nl5** med **nl6** på följande rader.

      I **RHEL 7/Debian 8**:

      ```
      LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
      Include /usr/local/neolane/nl6/tomcat-6/conf/apache_neolane.conf
      ```

1. Gå till **alias.conf** och ersätta alla **nl5** med **nl6**. Om du vill göra det i Debian kör du följande kommando:

   ```
   vi /etc/apache2/mods-available/alias.conf
   ```

## Säkerhetszoner {#security-zones}

Om du migrerar från v6.02 eller tidigare måste du konfigurera dina säkerhetszoner innan du startar tjänster. Mer information finns i [Säkerhet](../../migration/using/general-configurations.md#security).

## Starta om tjänster {#re-starting-services}

Hur du gör det beror på vilken version du har av Adobe Campaign.

### För Adobe Campaign v5 {#migrating-from-adobe-campaign-v5_11-2}

I **config-`<instance name>`.xml** filer, återaktivera den automatiska starten av **mta**, **wfserver**, **stat**, osv. tjänster.

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
1. Server för mid-sourcing.
1. Marknadsföringsserver.

Innan du går vidare till nästa steg kör du ett fullständigt test av den nya installationen, kontrollerar att det inte finns några regressioner och att allt fungerar genom att följa alla rekommendationer i [Allmänna konfigurationer](../../migration/using/general-configurations.md) -avsnitt.

### För Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6_02-2}

I **config-`<instance name>`.xml** filer, återaktivera den automatiska starten av **mta**, **wfserver**, **stat**, osv. tjänster.

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
1. Server för mid-sourcing.
1. Marknadsföringsserver.

Testa den nya installationen fullständigt, kontrollera att den inte går tillbaka och se till att allt fungerar som det ska genom att följa alla rekommendationer i [Allmänna konfigurationer](../../migration/using/general-configurations.md) -avsnitt.

### För Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6_1-2}

Starta Apache och Adobe Campaign på var och en av följande servrar:

1. Spårnings- och omdirigeringsserver.
1. Server för mid-sourcing.
1. Marknadsföringsserver.

Testa den nya installationen fullständigt, kontrollera att den inte går tillbaka och se till att allt fungerar som det ska genom att följa alla rekommendationer i [Allmänna konfigurationer](../../migration/using/general-configurations.md) -avsnitt.

## Ta bort Adobe Campaign tidigare version {#deleting-and-cleansing-adobe-campaign-v5}

>[!NOTE]
>
>Det här avsnittet gäller endast vid migrering från Adobe Campaign v5.11.

Innan du tar bort och rensar installationen av Adobe Campaign v5 måste du följa följande rekommendationer:

* Få funktionsteamen att göra en fullständig kontroll av den nya installationen.
* Avinstallera endast Adobe Campaign v5 när du är säker på att ingen återställning behövs.

Ta bort **nl5.back** katalog. Logga in som **neolan** och kör följande kommando:

```
su - neolane
rm -rf nl5.back
```

Starta om servern.
