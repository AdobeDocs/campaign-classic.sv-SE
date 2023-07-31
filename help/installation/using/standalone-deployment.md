---
product: campaign
title: Fristående driftsättning
description: Fristående driftsättning
feature: Installation, Architecture, Deployment
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1084'
ht-degree: 2%

---

# Fristående driftsättning{#standalone-deployment}



Den här konfigurationen innehåller alla komponenter på samma dator:

* ansökningsprocess (webb),
* leveransprocess (mta),
* omdirigeringsprocess (spårning),
* arbetsflödesprocess och schemalagda uppgifter (wfserver),
* studsa postprocessen (in Mail),
* statistikprocess (stat).

Den övergripande kommunikationen mellan processerna sker enligt följande schema:

![](assets/s_900_ncs_install_standaloneconfig.png)

Den här typen av konfiguration kan köras när du hanterar listor med färre än 100 000 mottagare och med till exempel följande programlager:

* Linux,
* Apache,
* PostgreSQL,
* Fråga.

När volymen växer flyttar en variant av den här arkitekturen databasservern till en annan dator för bättre prestanda.

>[!NOTE]
>
>En befintlig databasserver kan också användas om den har tillräckliga resurser.

## Funktioner {#features}

### Fördelar {#advantages}

* Komplett fristående och låg konfigurationskostnad (inga fakturerbara licenser krävs om öppen källkod-programvaran som anges nedan används).
* Förenklad installation och nätverkskonfiguration.

### Nackdelar {#disadvantages}

* En kritisk dator om det skulle inträffa.
* Begränsad bandbredd vid sändning av meddelanden (enligt vår erfarenhet är det cirka tiotusentals e-postmeddelanden per timme).
* Möjlig fördröjning av programmet vid sändning.
* Programservern måste vara tillgänglig från utsidan (till exempel i DMZ) eftersom den är värd för omdirigeringsservern.

## Installations- och konfigurationssteg {#installation-and-configuration-steps}

### Förhandskrav {#prerequisites}

* JDK,
* Webbserver (IIS, Apache),
* Tillgång till en databasserver
* Studsa postlåda tillgänglig via POP3,
* Skapa två DNS-alias:

   * Den första som exponeras för allmänheten för att spåra och peka mot datorn på dess offentliga immateriella tillgångar.
   * det andra aliaset som visas för interna användare för konsolåtkomst och som pekar på samma dator.

* Brandväggen är konfigurerad att öppna SMTP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 för Oracle, 5432 för PostgreSQL osv.) portar. Mer information finns i [Nätverkskonfiguration](../../installation/using/network-configuration.md).

I följande exempel är parametrarna för instansen:

* Instansens namn: **demo**
* DNS-mask: **console.campaign.net&#42;** (endast för klientkonsolanslutningar och för rapporter)
* Databas: **kampanj:demo@dbsrv**

### Installera och konfigurera (en dator) {#installing-and-configuring--single-machine-}

Använd följande steg:

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

   * För Linux: [Serverns första start](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * För Windows: [Serverns första start](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

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

1. Redigera **config-demo.xml** fil (skapad i föregående steg bredvid **config-default.xml**) och se till att **mta** (leverans), **wfserver** (arbetsflöde), **inMail** (studsmeddelanden) och **stat** (statistik) aktiveras. Konfigurera sedan adressen till statistikservern:

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="localhost"/>
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
   >The **nameServers** parametern används bara i Windows.

   Mer information finns i [Kampanjserverkonfiguration](../../installation/using/configuring-campaign-server.md).

1. Kopiera installationsprogrammet för klientkonsolen **setup-client-7.XXX.exe** till **/datakit/nl/eng/jsp** mapp. [Läs mer](../../installation/using/client-console-availability-for-windows.md).

1. Följ integreringsproceduren för webbservrar (IIS, Apache) som beskrivs i följande avsnitt:

   * För Linux: [Integrering med en webbserver för Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * För Windows: [Integrering med en webbserver för Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Starta webbplatsen och testa omdirigering med URL:en: https://tracking.campaign.net/r/test.

   Webbläsaren måste visa följande meddelande:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   Mer information finns i följande avsnitt:

   * För Linux: [Starta webbservern och testa konfigurationen](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * För Windows: [Starta webbservern och testa konfigurationen](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

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

1. Testa **nlserver web** som använder URL:en: https://console.campaign.net/nl/jsp/logon.jsp

   Den här URL:en ger dig åtkomst till hämtningssidan för klientinstallationsprogrammet.

   Ange **internal** inloggning och tillhörande lösenord när du kommer till åtkomstkontrollsidan. [Läs mer](../../installation/using/client-console-availability-for-windows.md).

   ![](assets/s_ncs_install_access_client.png)

1. Starta Adobe Campaign klientkonsol (från föregående nedladdningssida eller direkt från servern för en Windows-installation), ange serveranslutningens URL till https://console.campaign.net och ansluta med **internal** inloggning.

   Se [den här sidan](../../installation/using/creating-an-instance-and-logging-on.md) och [det här avsnittet](../../installation/using/configuring-campaign-server.md#internal-identifier).

   Guiden Skapa databas visas första gången du loggar in:

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   Följ stegen i guiden och skapa den databas som är associerad med anslutningsinstansen.

   Mer information finns i [Skapa och konfigurera databasen](../../installation/using/creating-and-configuring-the-database.md).

   När databasen har skapats loggar du ut.

1. Logga in igen på klientkonsolen med **admin** logga in utan lösenord och starta distributionsguiden ( **[!UICONTROL Tools > Advanced]** för att slutföra konfigurationen av instansen.

   Mer information finns i [Distribuera en instans](../../installation/using/deploying-an-instance.md).

   De huvudparametrar som ska anges är följande:

   * E-postleverans: avsändare- och svarsadresser samt felpostlådan för avhoppad e-post.
   * Spårning: Fyll i den externa URL som används för omdirigering och den interna URL:en, klicka på **Registrering på spårningsservrar** och validera den sedan på **demo** -instans för spårningsservern.

     Mer information finns i [Spårningskonfiguration](../../installation/using/deploying-an-instance.md#tracking-configuration).

     ![](assets/s_ncs_install_deployment_wiz_09.png)

     Eftersom Adobe Campaign-servern används både som programserver och omdirigeringsserver är den interna URL som används för att samla in spårningsloggar och överföra URL:er en direkt intern anslutning till Tomcat (https://localhost:8080).

   * Studshantering: Ange parametrar för att hantera studsmeddelanden (ta inte **Obearbetade studsmeddelanden** (med hänsyn till).
   * Åtkomst från: Ange två URL:er för rapporter, webbformulär och spegelsidor.

     ![](assets/d_ncs_install_web_url.png)
