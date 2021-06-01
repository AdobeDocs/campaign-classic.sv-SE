---
product: campaign
title: Driftsättning i företagsklass
description: Driftsättning i företagsklass
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 38c14010-203a-47ab-b23d-6f431dab9a88
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1221'
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
* Hög tillgänglighet som är enklare att säkerställa: Endast den dator som är synlig utifrån behöver hanteras med hög tillgänglighet i åtanke.

### Nackdelar {#disadvantages}

Högre kostnader för maskinvara och administration.

### Rekommenderad utrustning {#recommended-equipment}

* Programservrar: 2 GHz processor med fyra kärnor, 4 GB RAM, programvarubaserad RAID 1 80 GB SATA-hårddisk.
* Omdirigeringsservrar: 2 GHz processor med fyra kärnor, 4 GB RAM, programvarubaserad RAID 1 80 GB SATA-hårddisk.

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
   * den andra som visas för interna användare för åtkomst via konsolen och som pekar på en belastningsutjämnare på en virtuell IP-adress (VIP) och som sedan distribueras till de två programservrarna.

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
* DNS-mask: tracking.campaign.net*, console.campaign.net* (programservern hanterar URL:er för klientkonsolanslutningar och rapporter samt för spegelsidor och sidor som inte är prenumerationer)
* Språk: Engelska
* Databas: kampanj:demo@dbsrv

Stegen för installation av den första servern är:

1. Följ installationsproceduren för Adobe Campaign-servern: **nlserver**-paket i Linux eller **setup.exe** i Windows.

   Mer information finns i [Krav för Campaign-installation i Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) och [Krav för Campaign-installation i Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. När Adobe Campaign-servern har installerats startar du programservern (webb) med kommandot **nlserver web -tomcat** (med webbmodulen kan du starta Tomcat i fristående webbserverläge (avlyssning på port 8080) och kontrollera att Tomcat startar korrekt:

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```


   >[!NOTE]
   >
   >Första gången webbmodulen körs skapas filerna **config-default.xml** och **serverConf.xml** i katalogen **conf** under installationsmappen. Alla parametrar som är tillgängliga i **serverConf.xml** listas i det här [avsnittet](../../installation/using/the-server-configuration-file.md).

   Tryck på **Ctrl+C** för att stoppa servern.

   Mer information finns i följande avsnitt:

   * För Linux: [Första start av servern](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * För Windows: [Första start av servern](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. Ändra **det interna** lösenordet med kommandot:

   ```
   nlserver config -internalpassword
   ```

   Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#internal-identifier).

1. Skapa instansen **demo** med DNS-masker för spårning (i det här fallet **tracking.campaign.net**) och åtkomst till klientkonsoler (i det här fallet **console.campaign.net**). Det finns två sätt att göra detta:

   * Skapa instansen via konsolen:

      ![](assets/install_create_new_connexion.png)

      Mer information finns i [Skapa en instans och logga in](../../installation/using/creating-an-instance-and-logging-on.md).

      eller

   * Skapa instansen med kommandorader:

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      Mer information finns i [Skapa en instans](../../installation/using/command-lines.md#creating-an-instance).

1. Redigera filen **config-demo.xml** (skapad via föregående kommando och placerad bredvid filen **config-default.xml**), kontrollera att **mta** (leverans), **wfserver** (arbetsflöde), **inMail** (ombundna e-postmeddelanden) och **status** (statistik) processer är aktiverade och konfigurera sedan adressen till **app**-statistikservern:

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

1. Redigera filen **serverConf.xml** och ange leveransdomänen. Ange sedan IP-adresserna (eller värdadresserna) för de DNS-servrar som används av MTA-modulen för att svara på DNS-frågor av MX-typ.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Parametrarna **nameServers** används bara i Windows.

   Mer information finns i [Kampanjserverkonfiguration](../../installation/using/configuring-campaign-server.md).

1. Kopiera klientkonsolens installationsprogram (**setup-client-7.XX**, **YYY.exe** for v7 eller **setup-client-6.XX**, **YYYY.exe** for v6.1) till **/data/nl/enl g/jsp**-mapp. [Läs mer](../../installation/using/client-console-availability-for-windows.md).

1. Starta Adobe Campaign-servern (**net start nlserver6** i Windows, **/etc/init.d/nlserver6 start** i Linux) och kör kommandot **nlserver pdump** en gång till för att kontrollera om alla aktiverade moduler finns.

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

1. Testa webbmodulen **nlserver** med URL:en: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   Den här URL:en ger dig åtkomst till hämtningssidan för klientinstallationsprogrammet. [Läs mer](../../installation/using/client-console-availability-for-windows.md).

   Ange **intern**-inloggning och tillhörande lösenord när du kommer till åtkomstkontrollsidan.

   ![](assets/s_ncs_install_access_client.png)

### Installera och konfigurera programservern 2 {#installing-and-configuring-the-application-server-2}

Använd följande steg:

1. Installera Adobe Campaign-servern.
1. Kopiera filerna för instansen som du skapade till programservern 1.

   Vi behåller samma instansnamn som programservern 1.

1. Ändra **internal** till samma som programserver 1.
1. Länka databasen till instansen:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Redigera filen **config-demo.xml** (skapad via föregående kommando och placerad bredvid filen **config-default.xml**), kontrollera att **mta** (leverans), **wfserver** (arbetsflöde), **inMail** (ombundna e-postmeddelanden) och **status** (statistik) processer är aktiverade och konfigurera sedan adressen till **app**-statistikservern:

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

1. Redigera filen **serverConf.xml** och fyll i DNS-konfigurationen för MTA-modulen:

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Parametern **nameServers** används bara i Windows.

   Mer information finns i [Kampanjserverkonfiguration](../../installation/using/configuring-campaign-server.md).

1. Starta Adobe Campaign-servrarna.

   Mer information finns i följande avsnitt:

   * För Linux: [Första start av servern](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * För Windows: [Första start av servern](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### Installera och konfigurera frontservrarna {#installing-and-configuring-the-frontal-servers}

Installations- och konfigurationsprocedurerna är identiska på båda datorerna.

Stegen är följande:

1. Installera Adobe Campaign-servern,
1. Följ integreringsproceduren för webbservrar (IIS, Apache) som beskrivs i följande avsnitt:

   * För Linux: [Integrering med en webbserver för Linux](../../installation/using/integration-into-a-web-server-for-linux.md),
   * För Windows: [Integrering med en webbserver för Windows](../../installation/using/integration-into-a-web-server-for-windows.md).

1. Kopiera **config-demo.xml**- och **serverConf.xml**-filerna som skapades under installationen. I filen **config-demo.xml** aktiverar du processen **trackinglogd** och inaktiverar **mta**, **inmail**, **wfserver** och **stat&lt;a11/ > processer.**
1. Redigera filen **serverConf.xml** och fyll i de redundanta spårningsservrarna i parametrarna för omdirigeringen:

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
