---
title: Fristående driftsättning
seo-title: Fristående driftsättning
description: Fristående driftsättning
seo-description: null
page-status-flag: never-activated
uuid: 48ce793e-cb9f-4102-898f-758512cb9bf2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 9834638f-a8bb-4969-9f8d-99b8d9fdb1ca
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5f3ceab5ee82587d9f1829792bdabf2209f793cd

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

### Förutsättningar {#prerequisites}

* JDK,
* Webbserver (IIS, Apache),
* Tillgång till en databasserver
* Studsa postlåda tillgänglig via POP3,
* Skapa två DNS-alias:

   * Den första som exponeras för allmänheten för att spåra och peka mot datorn på dess offentliga immateriella tillgångar.
   * det andra aliaset som visas för interna användare för konsolåtkomst och som pekar på samma dator.

* Brandväggen har konfigurerats för att öppna STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 för Oracle, 5432 för PostgreSQL osv.) portar. Mer information finns i [Nätverkskonfiguration](../../installation/using/network-configuration.md).

I följande exempel är parametrarna för instansen:

* Instansens namn: **demo**
* DNS-mask: **console.campaign.net*** (endast för klientkonsolanslutningar och för rapporter)
* Databas: **kampanj:demo@dbsrv**

### Installera och konfigurera (en dator) {#installing-and-configuring--single-machine-}

Använd följande steg:

1. Följ installationsproceduren för Adobe Campaign-servern: **nlserver** -paket i Linux eller **setup.exe** i Windows.

   Mer information finns i [Krav för Campaign-installation i Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) och [Krav för Campaign-installation i Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. När Adobe Campaign-servern har installerats startar du programservern (webben) med kommandot **nlserver web -tomcat** (med webbmodulen kan du starta Tomcat i fristående webbserverläge som avlyssnar port 8080) och se till att Tomcat startar korrekt:

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >Första gången webbmodulen körs skapas filerna **config-default.xml** och **serverConf.xml** i katalogen **conf** under installationsmappen. Alla parametrar som finns i **serverConf.xml** listas i det här [avsnittet](../../installation/using/the-server-configuration-file.md).

   Tryck på **Ctrl+C** för att stoppa servern.

   Mer information finns i följande avsnitt:

   * För Linux: Serverns [](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)första start,
   * För Windows: Serverns [](../../installation/using/installing-the-server.md#first-start-up-of-the-server)första start.

1. Ändra det **interna** lösenordet med kommandot:

   ```
   nlserver config -internalpassword
   ```

   Mer information finns i [Intern identifierare](../../installation/using/campaign-server-configuration.md#internal-identifier).

1. Skapa **demoinstansen** med DNS-maskerna för spårning (i det här fallet **tracking.campaign.net**) och åtkomst till klientkonsoler (i det här fallet **console.campaign.net**). Det finns två sätt att göra detta:

   * Skapa instansen via konsolen:

      ![](assets/install_create_new_connexion.png)

      Mer information finns i [Skapa en instans och logga in](../../installation/using/creating-an-instance-and-logging-on.md).

      eller

   * Skapa instansen med kommandorader:

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      Mer information finns i [Skapa en instans](../../installation/using/command-lines.md#creating-an-instance).

1. Redigera filen **config-demo.xml** (som skapades i det föregående steget bredvid **config-default.xml**) och kontrollera att processerna **mta** (delivery), **wfserver** (workflow), **inMail** **** (studsade meddelanden) och¥stat (statistik) är aktiverade. Konfigurera sedan adressen till statistikservern:

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

   Mer information finns i [Aktivera processer](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. Redigera filen **serverConf.xml** och ange leveransdomänen. Ange sedan IP-adresserna (eller värdadresserna) för de DNS-servrar som används av MTA-modulen för att svara på DNS-frågor av MX-typ.

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >Parametern **nameServers** används bara i Windows.

   Mer information finns i [Kampanjserverkonfiguration](../../installation/using/campaign-server-configuration.md).

1. Kopiera klientkonsolens installationsprogram (**setup-client-7.XX**, **YYY.exe** för v7 eller **setup-client-6.XX**, **YYYY.exe** för v6.1) till mappen **/data/nl/eng/jsp** .

   Mer information finns i följande avsnitt:

   * För Linux: Tillgänglighet [för klientkonsol för Linux](../../installation/using/client-console-availability-for-linux.md)
   * För Windows: Tillgänglighet [för klientkonsolen för Windows](../../installation/using/client-console-availability-for-windows.md)

1. Följ integreringsproceduren för webbservrar (IIS, Apache) som beskrivs i följande avsnitt:

   * För Linux: Integrering [med en webbserver för Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * För Windows: Integrering [med en webbserver för Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Starta webbplatsen och testa omdirigering med URL:en: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test).

   Webbläsaren måste visa följande meddelande:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   Mer information finns i följande avsnitt:

   * För Linux: Starta [webbservern och testa konfigurationen](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * För Windows: Starta [webbservern och testa konfigurationen](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Starta Adobe Campaign-servern (**starta nlserver6** i Windows, **/etc/init.d/nlserver6 i Linux) och kör kommandot** nlserver pdump **** en gång till för att kontrollera om alla aktiverade moduler finns.

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

   Med det här kommandot kan du även se version och versionsnummer för Adobe Campaign-servern som är installerad på datorn.

1. Testa webbmodulen **på** servern med URL-adressen: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test)

   Den här URL:en ger dig åtkomst till hämtningssidan för klientinstallationsprogrammet.

   Ange den **interna** inloggningen och tillhörande lösenord när du kommer till åtkomstkontrollsidan.

   ![](assets/s_ncs_install_access_client.png)

   Mer information finns i följande avsnitt:

   * För Linux: Tillgänglighet [för klientkonsol för Linux](../../installation/using/client-console-availability-for-linux.md)
   * För Windows: Tillgänglighet [för klientkonsolen för Windows](../../installation/using/client-console-availability-for-windows.md)

1. Starta Adobe Campaign-klientkonsolen (från föregående hämtningssida eller direkt från servern för en Windows-installation), ange serveranslutningens URL till [https://console.campaign.net](https://console.campaign.net) och anslut med den **interna** inloggningen.

   Se [Skapa en instans och logga in](../../installation/using/creating-an-instance-and-logging-on.md) och [Intern identifierare](../../installation/using/campaign-server-configuration.md#internal-identifier).

   Guiden Skapa databas visas första gången du loggar in:

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   Följ stegen i guiden och skapa den databas som är associerad med anslutningsinstansen.

   Mer information finns i [Skapa och konfigurera databasen](../../installation/using/creating-and-configuring-the-database.md).

   När databasen har skapats loggar du ut.

1. Logga in på klientkonsolen igen med **administratörsinloggningen** utan lösenord och starta distributionsguiden ( **[!UICONTROL Tools > Advanced]** menyn) för att slutföra konfigurationen av instansen.

   Mer information finns i [Distribuera en instans](../../installation/using/deploying-an-instance.md).

   De huvudparametrar som ska anges är följande:

   * E-postleverans: avsändare- och svarsadresser samt felpostlådan för avhoppad e-post.
   * Spårning: Fyll i den externa URL som används för omdirigering och den interna URL:en, klicka på **Registrering på spårningsservern** och validera den sedan på **demoinstansen** av spårningsservern.

      Mer information finns i [Spårningskonfiguration](../../installation/using/deploying-an-instance.md#tracking-configuration).

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      Eftersom Adobe Campaign-servern används både som programserver och omdirigeringsserver är den interna URL som används för att samla in spårningsloggar och överföra URL:er en direkt intern anslutning till Tomcat (https://localhost:8080).

   * Studsningshantering: Ange parametrarna för att hantera studsmeddelanden (ta inte hänsyn till avsnittet **Obearbetade studsmeddelanden** ).
   * Åtkomst från: Ange de två URL:erna för rapporter, webbformulär och spegelsidor.

      ![](assets/d_ncs_install_web_url.png)

