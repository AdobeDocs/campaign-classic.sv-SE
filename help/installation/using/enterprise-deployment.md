---
product: campaign
title: Driftsättning i företagsklass
description: Driftsättning i företagsklass
feature: Installation, Architecture, Deployment
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 38c14010-203a-47ab-b23d-6f431dab9a88
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1225'
ht-degree: 3%

---

# Driftsättning i företagsklass{#enterprise-deployment}



Detta är den mest fullständiga konfigurationen. Den bygger på standardkonfigurationen för bättre säkerhet och tillgänglighet:

* dedikerade omdirigeringsservrar bakom en HTTP- eller TCP-belastningsutjämnare, för skalbarhet och tillgänglighet,
* två programservrar för förbättrad genomströmning och failover-kapacitet (feltolerans) som isoleras i LAN.

Allmän kommunikation mellan servrar och processer sker enligt följande schema:

![](assets/s_901_ncs_install_enterpriseconfig.png)

Med den här typen av konfiguration kan den förväntade genomströmningen överstiga 100 000 e-postmeddelanden per timme med lämplig bandbredd och justering.

## Funktioner {#features}

### Fördelar {#advantages}

* Optimerad säkerhet: Endast de servrar som ska exponeras för utsidan installeras på datorn i DMZ.
* Hög tillgänglighet som är lättare att säkerställa: Endast den dator som är synlig utifrån behöver hanteras med hög tillgänglighet i åtanke.

### Nackdelar {#disadvantages}

Högre kostnader för maskinvara och administration.

### Rekommenderad utrustning {#recommended-equipment}

* Programservrar: 2 GHz-processor med fyra kärnor, 4 GB RAM-minne, program RAID 1 80 GB SATA-hårddisk.
* Omdirigeringsservrar: 2 GHz-processor med fyra kärnor, 4 GB RAM-minne, programvara RAID 1 80 GB SATA-hårddisk.

>[!NOTE]
>
>Det går att återanvända en befintlig belastningsutjämnare för trafik till omdirigeringsservrarna.

## Installations- och konfigurationssteg {#installation-and-configuration-steps}

### Förhandskrav {#prerequisites}

* JDK på båda programservrarna,
* Webbserver (IIS, Apache) på båda frontalerna,
* Tillgång till en databasserver på båda programservrarna,
* Studsa postlåda tillgänglig via POP3,
* Två DNS-alias skapas på belastningsutjämnaren:

   * Den första som exponeras för allmänheten för spårning och som pekar mot belastningsutjämnaren på en virtuell IP-adress (VIP) och som sedan distribueras till de två frontservrarna.
   * den andra som exponeras för interna användare för åtkomst via konsolen och som pekar på en belastningsutjämnare på en virtuell IP-adress (VIP) och som sedan distribueras till de två programservrarna.

* Brandväggen har konfigurerats för att öppna STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 för Oracle, 5432 för PostgreSQL osv.) portar. Mer information finns i avsnittet [Databasåtkomst](../../installation/using/network-configuration.md#database-access).

>[!CAUTION]
>
>Om programservrarna pekar på en enda databasinstans läses schemat i paketet inte in på den andra instansen när du har importerat ett standardpaket till en instans.
>  
>Om programservrarna pekar på en enda databasinstans läses schemat inte in på den andra instansen efter att schemat ändrats för en instans.
>
>Om du vill återställa dessa problem måste du starta om web@default i den andra instansen där ett fel uppstod.

### Installera och konfigurera programservern 1 {#installing-and-configuring-the-application-server-1}

I följande exempel är parametrarna för instansen:

* Instansens namn: demo
* DNS-mask: tracking.campaign.net&#42;, console.campaign.net&#42; (programservern hanterar URL:er för klientkonsolanslutningar och rapporter och för spegelsidor och sidor som inte kan prenumereras)
* Språk: Engelska
* Databas: kampanj:demo@dbsrv

Stegen för installation av den första servern är:

1. Följ installationsproceduren för Adobe Campaign-servern: **nlserver** paket i Linux eller **setup.exe** i Windows.

   Mer information finns i [Krav för Campaign-installation i Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) och [Krav för Campaign-installation i Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. När Adobe Campaign-servern är installerad startar du programservern (webben) med kommandot **nlserver web -tomcat** (Med webbmodulen kan du starta Tomcat i fristående läge för webbserver som lyssnar på port 8080) och se till att Tomcat startar korrekt:

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```


   >[!NOTE]
   >
   >Första gången webbmodulen körs skapas **config-default.xml** och **serverConf.xml** filer i **conf** under installationsmappen. Alla parametrar som är tillgängliga i **serverConf.xml** finns listade i [section](../../installation/using/the-server-configuration-file.md).

   Tryck **Ctrl+C** för att stoppa servern.

   Mer information finns i följande avsnitt:

   * För Linux: [Serverns första start](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * För Windows: [Serverns första start](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. Ändra **internal** lösenord med kommandot:

   ```
   nlserver config -internalpassword
   ```

   Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Skapa **demo** instans med DNS-masker för spårning (i det här fallet **tracking.campaign.net**) och åtkomst till klientkonsoler (i det här fallet **console.campaign.net**). Det finns två sätt att göra detta:

   * Skapa instansen via konsolen:

     ![](assets/install_create_new_connexion.png)

     Mer information finns i [Skapa en instans och logga in](../../installation/using/creating-an-instance-and-logging-on.md).

     eller

   * Skapa instansen med kommandorader:

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
     ```

     Mer information finns i [Skapa en instans](../../installation/using/command-lines.md#creating-an-instance).

1. Redigera **config-demo.xml** filen (skapad med föregående kommando och placerad intill **config-default.xml** -fil), kontrollera att **mta** (leverans), **wfserver** (arbetsflöde), **inMail** (återbundna mejl) och **stat** (statistik) processer aktiveras och sedan konfigureras adressen för **app** statistikserver:

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Redigera **serverConf.xml** och ange leveransdomänen och ange sedan IP-adresserna (eller värdadresserna) för de DNS-servrar som används av MTA-modulen för att svara på DNS-frågor av MX-typ.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >The **nameServers** parametrar används bara i Windows.

   Mer information finns i [Kampanjserverkonfiguration](../../installation/using/configuring-campaign-server.md).

1. Kopiera installationsprogrammet för klientkonsolen **setup-client-7.XX**, **YYYY.exe** till **/datakit/nl/eng/jsp** mapp. [Läs mer](../../installation/using/client-console-availability-for-windows.md).

1. Starta Adobe Campaign-servern (**net start nlserver6** i Windows, **/etc/init.d/nlserver6 - start** i Linux) och köra kommandot **nlserver pdump** en gång till för att kontrollera om det finns alla aktiverade moduler.

   >[!NOTE]
   >
   >Från och med 20.1 rekommenderar vi att du använder följande kommando i stället (för Linux): **systemctl start nlserver**


   ```
   12:09:54 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   syslogd@default (7611) - 9.2 MB
   stat@demo (5988) - 1.5 MB
   inMail@demo (7830) - 11.9 MB
   watchdog (27369) - 3.1 MB
   mta@demo (7831) - 15.6 MB
   wfserver@demo (7832) - 11.5 MB
   web@default (28671) - 40.5 MB
   ```

   Med det här kommandot kan du även se version och versionsnummer för den Adobe Campaign-server som är installerad på datorn.

1. Testa **nlserver web** modul som använder URL: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   Den här URL:en ger dig åtkomst till hämtningssidan för klientinstallationsprogrammet. [Läs mer](../../installation/using/client-console-availability-for-windows.md).

   Ange **internal** inloggning och tillhörande lösenord när du kommer till åtkomstkontrollsidan.

   ![](assets/s_ncs_install_access_client.png)

### Installera och konfigurera programservern 2 {#installing-and-configuring-the-application-server-2}

Använd följande steg:

1. Installera Adobe Campaign-servern.
1. Kopiera filerna för instansen som du skapade till programservern 1.

   Vi behåller samma instansnamn som programservern 1.

1. Ändra **internal** på samma sätt som programserver 1.
1. Länka databasen till instansen:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Redigera **config-demo.xml** filen (skapad med föregående kommando och placerad intill **config-default.xml** -fil), kontrollera att **mta** (leverans), **wfserver** (arbetsflöde), **inMail** (återbundna mejl) och **stat** (statistik) processer aktiveras och sedan konfigureras adressen för **app** statistikserver:

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#enabling-processes).

1. Redigera **serverConf.xml** och fylla i DNS-konfigurationen för MTA-modulen:

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >The **nameServers** parametern används bara i Windows.

   Mer information finns i [Kampanjserverkonfiguration](../../installation/using/configuring-campaign-server.md).

1. Starta Adobe Campaign servrar.

   Mer information finns i följande avsnitt:

   * För Linux: [Serverns första start](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * För Windows: [Serverns första start](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### Installera och konfigurera frontservrarna {#installing-and-configuring-the-frontal-servers}

Installations- och konfigurationsprocedurerna är identiska på båda datorerna.

Stegen är följande:

1. Installera Adobe Campaign-servern,
1. Följ integreringsproceduren för webbservrar (IIS, Apache) som beskrivs i följande avsnitt:

   * För Linux: [Integrering med en webbserver för Linux](../../installation/using/integration-into-a-web-server-for-linux.md),
   * För Windows: [Integrering med en webbserver för Windows](../../installation/using/integration-into-a-web-server-for-windows.md).

1. Kopiera **config-demo.xml** och **serverConf.xml** filer som skapas under installationen. I **config-demo.xml** -fil, aktivera **trackinglogd** bearbeta och inaktivera **mta**, **inmail**, **wfserver** och **stat** -processer.
1. Redigera **serverConf.xml** och fylla i de redundanta spårningsservrarna i parametrarna för omdirigeringen:

   ```
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. Starta webbplatsen och testa omdirigeringen från URL:en: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   Webbläsaren bör visa följande meddelanden (beroende på vilken URL som omdirigeras av belastningsutjämnaren):

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   eller

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Mer information finns i följande avsnitt:

   * För Linux: [Starta webbservern och testa konfigurationen](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration),
   * För Windows: [Starta webbservern och testa konfigurationen](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration).

1. Starta Adobe Campaign-servern.
