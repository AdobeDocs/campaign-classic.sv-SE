---
title: Åtkomst till en extern databas
seo-title: Åtkomst till en extern databas
description: Åtkomst till en extern databas
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fecfff477b0750782c87c017a15e306acac4c61d
workflow-type: tm+mt
source-wordcount: '2865'
ht-degree: 0%

---


# Specifika konfigurationer efter databastyp {#specific-configurations-by-database-type}

Beroende på vilka externa databaser du vill kunna komma åt från Adobe Campaign måste du utföra vissa specifika konfigurationer. Dessa konfigurationer innebär i princip att installera drivrutiner och deklarera miljövariabler som tillhör varje RDBMS på Adobe Campaign-servern.

Som regel måste du installera motsvarande klientlager på den externa databasen på Adobe Campaign-servern.

>[!NOTE]
>
>Kompatibla versioner visas i [Campaign-kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA).

## Konfigurera åtkomst till Azure Synapse {#configure-access-to-azure-synapse}

### Azure synapse external account {#azure-external}

Med det [!DNL Azure] externa kontot kan du ansluta Campaign-instansen till din externa Azure Synapse-databas.
Så här skapar du ett externt [!DNL Azure Synapse] konto:

1. Konfigurera ditt [!DNL Azure Synapse] externa konto i Campaign Classic. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Klicka på **[!UICONTROL Create]**.

1. Konfigurera det [!DNL Azure Synapse] externa kontot måste du ange:

   * **[!UICONTROL Type]**: Azure Synapse Analytics

   * **[!UICONTROL Server]**: URL för Azure Synapse-servern

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namn på databasen
   ![](assets/azure_1.png)

### Azure Synapse i CentOS {#azure-centos}

**Förutsättningar:**

* Du måste ha rotbehörighet för att installera en ODBC-drivrutin.
* Red Hat Enterprise ODBC-drivrutiner från Microsoft kan också användas med CentOS för att ansluta till SQL Server.
* Version 13.0 fungerar med Red Hat 6 och 7.

Så här konfigurerar du Azure Synapse på CentOS:

1. Installera först ODBC-drivrutinen. Du hittar den på den här [sidan](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

   >[!NOTE]
   >
   >Detta gäller endast version 13 av ODBC-drivrutinen.

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   # Uninstall if already installed Unix ODBC driver
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   
   sudo ACCEPT_EULA=Y yum install msodbcsql
   
   sudo ACCEPT_EULA=Y yum install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   
   # the Microsoft driver expects unixODBC to be here /usr/lib64/libodbc.so.1, so add soft links to the '.so.2' files
   cd /usr/lib64
   sudo ln -s libodbccr.so.2   libodbccr.so.1
   sudo ln -s libodbcinst.so.2 libodbcinst.so.1
   sudo ln -s libodbc.so.2     libodbc.so.1
   
   # Set the path for unixODBC
   export ODBCINI=/usr/local/etc/odbc.ini
   export ODBCSYSINI=/usr/local/etc
   source ~/.bashrc
   
   #Add a DSN information to /etc/odbc.ini
   sudo vi /etc/odbc.ini
   
   #Add the following:
   [Azure Synapse Analytics]
   Driver      = ODBC Driver 13 for SQL Server
   Description = Azure Synapse Analytics DSN
   Trace       = No
   Server      = [insert your server here]
   ```

1. Om det behövs kan du installera utvecklingsrubriker för unixODBC genom att köra följande kommando:

   ```
   sudo yum install unixODBC-devel
   ```

1. När du har installerat drivrutinerna kan du testa och verifiera ODBC-drivrutinen och fråga databasen om det behövs. Kör följande kommando:

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. I Campaign Classic kan du sedan konfigurera ditt [!DNL Azure Synapse] externa konto. Mer information om hur du konfigurerar ditt externa konto finns i det här [avsnittet](../../platform/using/specific-configuration-database.md#azure-external).

1. Eftersom Azure Synapse Analytics kommunicerar via TCP 1433-porten måste du öppna den här porten på din brandvägg. Använd följande kommando:

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >Om du vill tillåta kommunikation från Azure Synapse Analytics-sidan kan du behöva lägga till din offentliga IP-adress i listan över tillåtna. Om du vill göra det läser du i [Azure-dokumentationen](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

1. Om det är iptables kör du följande kommando:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

### Azure Synapse i Windows {#azure-windows}

>[!NOTE]
>
>Detta gäller endast version 13 av ODBC-drivrutinen, men Adobe Campaign Classic kan även använda SQL Server Native Client-drivrutinerna 11.0 och 10.0.

Så här konfigurerar du Azure Synapse i Windows:

1. Installera först Microsoft ODBC-drivrutinen. Du hittar den på den här [sidan](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

1. Välj följande filer att installera:

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. När ODBC-drivrutinen har installerats kan du testa den om det behövs. Mer information finns på den här [sidan](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server).

1. I Campaign Classic kan du sedan konfigurera ditt [!DNL Azure Synapse] externa konto. Mer information om hur du konfigurerar ditt externa konto finns i det här [avsnittet](../../platform/using/specific-configuration-database.md#azure-external).

1. Eftersom Azure Synapse Analytics kommunicerar via TCP 1433-porten måste du öppna den här porten i Windows Defender-brandväggen. Mer information finns i [Windows-dokumentationen](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

### Azure Synapse på Debian {#azure-debian}

**Förutsättningar:**

* Du måste ha rotbehörighet för att installera en ODBC-drivrutin.
* Rullning krävs för att installera paketet mSolbcsql. Om du inte har det installerat kör du följande kommando:

   ```
   sudo apt-get install curl
   ```

Så här konfigurerar du Azure Synapse på Debian:

1. Installera först Microsoft ODBC-drivrutinen för SQL Server. Använd följande kommandon för att installera ODBC-drivrutinen 13.1 för SQL Server:

   ```
   sudo su
   curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
   curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
   exit
   sudo apt-get update
   sudo ACCEPT_EULA=Y apt-get install msodbcsql
   ```

1. Om du får följande felmeddelande **&quot;Metoddrivrutinen /usr/lib/apt/methods/https could not found&quot;** när **sudo apt-get update** anropas bör du köra kommandot:

   ```
   sudo apt-get install apt-transport-https ca-certificates
   ```

1. Nu måste du installera mssql-tools med följande kommandon. Mssq-tools behövs för att använda BCP-verktyget och köra frågor.

   ```
   sudo ACCEPT_EULA=Y apt-get install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

1. Om det behövs kan du installera utvecklingsrubriker för unixODBC genom att köra följande kommando:

   ```
   sudo yum install unixODBC-devel
   ```

1. När du har installerat drivrutinerna kan du testa och verifiera ODBC-drivrutinen och fråga databasen om det behövs. Kör följande kommando:

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. I Campaign Classic kan du nu konfigurera ditt [!DNL Azure Synapse] externa konto. Mer information om hur du konfigurerar ditt externa konto finns i det här [avsnittet](../../platform/using/specific-configuration-database.md#azure-external).

1. Om du vill konfigurera iptables på Debian för att säkerställa anslutningen med Azure Synapse Analytics aktiverar du den utgående TCP 1433-porten för ditt värdnamn med följande kommando:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >Om du vill tillåta kommunikation från Azure Synapse Analytics-sidan kan du behöva lägga till din offentliga IP-adress i listan över tillåtna. Om du vill göra det läser du i [Azure-dokumentationen](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

## Konfigurera åtkomst till Snowflake {#configure-access-to-snowflake}

>[!NOTE]
>
>[!DNL Snowflake] anslutning finns för värdbaserade och lokala distributioner. For more on this, refer to [this article](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

![](assets/snowflake_3.png)

### Snöflinga externt konto {#snowflake-external}

Med det [!DNL Snowflake] externa kontot kan du ansluta Campaign-instansen till din externa Snowflake-databas.

1. Konfigurera ditt [!DNL Snowflake] externa konto i Campaign Classic. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Välj det inbyggda **[!UICONTROL Snowflake]** externa kontot.

1. Konfigurera det **[!UICONTROL Snowflake]** externa kontot måste du ange:

   * **[!UICONTROL Server]**: URL för [!DNL Snowflake] servern

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namn på databasen
   ![](assets/snowflake.png)

1. Klicka på **[!UICONTROL Parameters]** fliken och sedan på **[!UICONTROL Deploy functions]** knappen för att skapa funktioner.

   ![](assets/snowflake_2.png)

Kopplingen stöder följande alternativ:

| Alternativ | Beskrivning |
|---|---|
| arbetsschema | Databasschema som ska användas för arbetsregister |
| lagerställe | Namnet på standardlagerstället som ska användas. Det åsidosätter användarens standardvärde. |
| TimeZoneName | Som standard är den tom, vilket innebär att systemtidszonen för programservern i Campaign Classic används. Alternativet kan användas för att framtvinga TIMEZONE-sessionsparametern. <br>Mer information finns på [den här sidan](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | WEEK_START-sessionsparameter. Standardinställningen är 0. <br>Mer information finns på [den här sidan](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
| AnvändCachedResult | USE_CACHED_RESULTS sessionsparameter. Standardinställningen är TRUE. Det här alternativet kan användas för att inaktivera cachelagrade Snowflake-resultat. <br>Mer information finns på [den här sidan](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |

### Snöflinga i CentOS {#snowflake-centos}

1. Hämta ODBC-drivrutinerna för [!DNL Snowflake]. [Klicka här](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) för att påbörja nedladdningen.
1. Du måste sedan installera ODBC-drivrutinerna på CentOS med följande kommando:

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. När du har hämtat och installerat ODBC-drivrutinerna måste du starta om Campaign Classic. Om du vill göra det kör du följande kommando:

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. I Campaign Classic kan du sedan konfigurera ditt [!DNL Snowflake] externa konto. Mer information om hur du konfigurerar ditt externa konto finns i det här [avsnittet](../../platform/using/specific-configuration-database.md#snowflake-external).

### Snöflinga på Debian {#snowflake-debian}

1. Hämta ODBC-drivrutinerna för [!DNL Snowflake]. [Klicka här](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) för att påbörja nedladdningen.

1. Du måste sedan installera ODBC-drivrutinerna på Debian med följande kommando:

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. När du har hämtat och installerat ODBC-drivrutinerna måste du starta om Campaign Classic. Om du vill göra det kör du följande kommando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. I Campaign Classic kan du sedan konfigurera ditt [!DNL Snowflake] externa konto. Mer information om hur du konfigurerar ditt externa konto finns i det här [avsnittet](../../platform/using/specific-configuration-database.md#snowflake-external).

### Snöflinga i Windows {#snowflake-windows}

1. Hämta [ODBC-drivrutinen för Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). Observera att du behöver administratörsbehörighet för att installera drivrutinen. For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Konfigurera ODBC-drivrutinen. For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. I Campaign Classic kan du sedan konfigurera ditt [!DNL Snowflake] externa konto. Mer information om hur du konfigurerar ditt externa konto finns i det här [avsnittet](../../platform/using/specific-configuration-database.md#snowflake-external).

## Konfigurera åtkomst till Hadoop 3.0 {#configure-access-to-hadoop-3}

För att ansluta till en extern Hadoop-databas i FDA krävs följande konfigurationer på Adobe Campaign-servern. Observera att den här konfigurationen är tillgänglig för både Windows och Linux.

1. Hämta ODBC-drivrutinerna för Hadoop beroende på vilken OS-version du har. Drivrutiner finns på [den här sidan](https://www.cloudera.com/downloads.html).

1. Du måste sedan installera ODBC-drivrutinerna och skapa ett DSN för din Hive-anslutning. Instruktioner finns på [den här sidan](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. När du har hämtat och installerat ODBC-drivrutinerna måste du starta om Campaign Classic. Om du vill göra det kör du följande kommando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. I Campaign Classic kan du sedan konfigurera ditt externa konto för snöflake. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Klicka **[!UICONTROL Create]** och välj **[!UICONTROL External database]** kontotyp.

1. Om du vill konfigurera det **[!UICONTROL  Hadoop]** externa kontot måste du ange:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: DNS-namn

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namnet på databasen om det inte anges i DSN. Den kan lämnas tom om den anges i DSN

   * **[!UICONTROL Time zone]**: Tidszon för server
   ![](assets/hadoop3.png)

Kopplingen stöder följande ODBC-alternativ:

| Namn | Värde |
|---|---|
| ODBCMgr | iODBC |
| lagerställe | 1/2/4 |

Kopplingen stöder även följande Hive-alternativ:

| Namn | Värde | Beskrivning |
|---|---|---|
| bulkKey | Åtkomstnyckel för Azure-blob eller DataLake | För wasb:// eller wasbs:// massinläsare (dvs. om massinläsningsverktyget börjar med wasb:// eller wasbs://). <br>Det är åtkomstnyckeln för blob- eller DataLake-bucket för massinläsning. |
| hdfsPort | portnummer <br>inställt på 8020 som standard | För HDFS-massinläsning (d.v.s. om massinläsningsverktyget börjar med webhdfs:// eller webhdfss://). |
| buficknummer | 20 | Antal grupper när en klustrad tabell skapas. |
| fileFormat | PARQUET | Standardfilformat för arbetsregister. |

## Konfigurera åtkomst till Hadoop 2.1 {#configure-access-to-hadoop}

### För Windows {#for-windows}

1. Installera ODBC- och [Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886) -drivrutiner för Windows.
1. Skapa DSN (namn på datakälla) genom att köra administrationsverktyget för ODBC-datakälla. Du kan ändra ett system-DSN-exempel för Hive.

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. Skapa det externa Hadoop-kontot, vilket beskrivs i [det här](../../platform/using/external-accounts.md#hadoop-external-account) sidavsnittet.

### För Linux {#for-linux}

1. Installera unixodbc för Linux.

   ```
   apt-get install unixodbc
   ```

1. Hämta och installera ODBC-drivrutiner för Apache Hive från HortonWorks: [https://www.hortonworks.com/downloads/](https://www.hortonworks.com/downloads/).

   ```
   dpkg -i hive-odbc-native_2.1.10.1014-2_amd64.deb
   ```

1. Kontrollera ODBC-filens plats.

   ```
   root@campadpac71:/tmp# odbcinst -j
   unixODBC 2.3.1
   DRIVERS............: /etc/odbcinst.ini
   SYSTEM DATA SOURCES: /etc/odbc.ini
   FILE DATA SOURCES..: /etc/ODBCDataSources
   USER DATA SOURCES..: /root/.odbc.ini
   SQLULEN Size.......: 8
   SQLLEN Size........: 8
   SQLSETPOSIROW Size.: 8
   ```

1. Skapa DSN (Data Source Name) och redigera filen odbc.ini. Skapa sedan ett DSN för din Hive-anslutning.

   Här är ett exempel för HDInsight som skapar en anslutning som kallas&quot;viral&quot;:

   ```
   [ODBC Data Sources]
   vorac 
   
   [vorac]
   Driver=/usr/lib/hive/lib/native/Linux-amd64-64/libhortonworkshiveodbc64.so
   HOST=vorac.azurehdinsight.net
   PORT=443
   Schema=sm_tst611
   HiveServerType=2
   AuthMech=6
   UID=admin
   PWD=<your password here>
   HTTPPath=
   UseNativeQuery=1
   ```

   >[!NOTE]
   >
   >Parametern **UseNativeQuery** är mycket viktig. Campaign är Hive-medveten och fungerar inte korrekt om inte UseNativeQuery har angetts. Vanligtvis skriver drivrutinen eller Hive SQL Connector om frågor och ändrar kolumnordningen.

   Inställningen av autentisering beror på konfigurationen av Hive/Hadoop. För HD Insight använder du till exempel AuthMech=6 för användar-/lösenordsautentisering enligt beskrivningen [här](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm).

1. Exportera variablerna.

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. Konfigurera drivrutiner för Hortonworks via /usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini.

   Du måste använda UTF-16 för att kunna ansluta till Campaign och unix-odbc (libodbcinst).

   ```
   [Driver]
   
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=/usr/lib/hive/lib/native/hiveodbc/ErrorMessages/
   LogLevel=0
   LogPath=/tmp/hive
   SwapFilePath=/tmp
   
   ODBCInstLib=libodbcinst.so
   ```

1. Nu kan du testa anslutningen med isql.

   ```
   isql vorac
   isql vorac -v
   ```

1. Skapa det externa Hadoop-kontot, vilket beskrivs i [det här](../../platform/using/external-accounts.md#hadoop-external-account) sidavsnittet.

## Konfigurera åtkomst till Netezza {#configure-access-to-netezza}

För att ansluta till en extern Netezza-databas i FDA krävs ytterligare konfigurationer nedan på Adobe Campaign-servern:

1. Installera ODBC-drivrutinerna för Netezza, enligt det operativsystem du använder:

   * **nz-linuxclient-v7.2.0.0.tar.gz** för Linux. Markera den mapp som motsvarar ditt operativsystem (Linux eller Linux64) och starta uppackningskommandot. Du kan lämna installationen som ska utföras i den databas som föreslås som standard: &quot;/usr/local/nz&quot;.
   * **nz-winclient-v7.2.0.0.zip** för Windows. Zippa upp filen och starta det körbara skript som hör till ditt operativsystem: nzodbcsetup.exe eller nzodbcsetup64.exe. Följ instruktionerna i guiden för att slutföra installationen av drivrutinerna.

1. Konfigurera ODBC-drivrutinen. Konfigurationen kan utföras i standardfilerna: **/etc/odbc.ini** för allmänna parametrar och **/etc/odbcinst.ini** för att deklarera drivrutiner.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot; motsvarar platsen för filen odbcinst.ini.

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. Ange miljövariablerna för Adobe Campaign-servern:

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib och /usr/local/nz/lib64. &quot;/usr/local/nz&quot; motsvarar den installationsdatabas som finns som standard när du installerar drivrutinerna. Här måste du ange vilken databas du har valt för installationen.
   * **ODBCINI**: platsen för filen odbc.ini (till exempel /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: platsen för filen odbc.ini. Netezza kräver också den andra variabeln för att kunna använda filen odbc.ini.

1. I Campaign Classic kan du sedan konfigurera ditt externa Netezza-konto. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. Om du vill konfigurera det **[!UICONTROL Netezza]** externa kontot måste du ange:

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**: URL för Netezza-servern

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namn på databasen

>[!NOTE]
>
>Åtgärder för scheman som innehåller automatiskt genererade primärnycklar beaktas inte.
>
>Tabellen använder **Organizer on** -satsen för det första indexvärdet som definieras i schemat. Eftersom den här satsen är begränsad till 1 till 4 kolumner med Netezza, får indexet inte innehålla fler än 4 kolumner.

## Konfigurera åtkomst till Oracle {#configure-access-to-oracle}

För att ansluta till en extern Oracle-databas i FDA krävs ytterligare konfigurationer nedan på Adobe Campaign-servern.

### För Linux {#for-linux-1}

1. Installera den fullständiga Oracle-klienten som motsvarar din version av Oracle.
1. Lägg till dina TNS-definitioner i installationen. Om du vill göra det anger du dem i en **namnfil.ora** i databasen /etc/oracle. Om den här databasen inte finns skapar du den.

   Skapa sedan en ny TNS_ADMIN-miljövariabel: exportera TNS_ADMIN=/etc/oracle och starta om datorn.

1. Integrera Oracle med Adobe Campaign-servern (nlserver). Det gör du genom att kontrollera att filen **customer.sh** finns i mappen &quot;nl6&quot; i trädstrukturen för Adobe Campaign och att den innehåller länkar till Oracle-biblioteken.

   Exempel: för en klient i 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Dessa värden (särskilt ORACLE_HOME) beror på installationsdatabaserna. Kontrollera trädstrukturen innan du refererar till dessa värden.

1. Installera de bibliotek som krävs för Oracle:

   * **libclntsh.so**

      ```
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

   * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

### För Windows {#for-windows-1}

1. Installera Oracle-klienten.
1. I mappen C:Oracle skapar du en **namnfil.ora** som innehåller din TNS-definition.

   Lägg till en TNS_ADMIN-miljövariabel med C:Oracle som-värde och starta om datorn.

## Konfigurera åtkomst till Sybase IQ {#configure-access-to-sybase-iq}

För att ansluta till en extern Sybase IQ-databas i FDA krävs ytterligare konfigurationer nedan på Adobe Campaign-servern:

1. Kontrollera att Unixodbc-paketet finns på servern.
1. Installera **iq_odbc**. Ett fel kan uppstå i slutet av installationen. Det här felet kan ignoreras.
1. Installera **iq_client_common**. Ett Java-fel kan uppstå när installationen är klar. Det här felet kan ignoreras.
1. Konfigurera ODBC-drivrutinen. Konfigurationen kan utföras i standardfilerna: /etc/odbc.ini för allmänna parametrar och /etc/odbcinst.ini för att deklarera drivrutiner:

   * **/etc/odbc.ini** (ersätt värden som `<server_alias>` tecken med egna):

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. Lägg till sökvägen för det nya biblioteket libodbc16.so i variabeln LD_LIBRARY_PATH. Så här gör du:

   * Om du använder en customer.sh-fil för att deklarera sökvägen: lägg till sökvägen /opt/sybase/IQ-16_0/lib64 för variabeln LD_LIBRARY_PATH.
   * Annars använder du ett Unix-kommando.

1. I Campaign Classic kan du sedan konfigurera ditt externa Sybase IQ-konto. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. Om du vill konfigurera det **[!UICONTROL Sybase IQ]** externa kontot måste du ange:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Motsvarar ODBC-anslutningen (`<server_alias>`) som definieras i steg 5. Inte nödvändigtvis namnet på själva servern.

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namn på databasen

>[!NOTE]
>
>För Windows måste du installera Sybase IQ-klienten på Adobe Campaign-servern och skapa en ODBC-anslutning. Se till att du skapar en systemdatakälla när Adobe Campaign-servern (nlserver) körs som en tjänst i Windows.

## Konfigurera åtkomst till Teradata {#configure-access-to-teradata}

För anslutning till en extern Teradata-databas i FDA krävs vissa ytterligare konfigurationer på Adobe Campaign-servern. Mer information om hur du konfigurerar Teradata-databasen finns i den här [artikeln](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html).

1. Installera [ODBC-drivrutinen för Teradata](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   Den består av tre paket som kan installeras på Red Hat (eller CentOS)/Suse i följande ordning:

   * TeraGSS
   * tdicu1510 (installera den med setup_wrapper.sh)
   * tdodbc1510 (installera den med setup_wrapper.sh)

1. Konfigurera ODBC-drivrutinen. Konfigurationen kan utföras i standardfilerna: **/etc/odbc.ini** för allmänna parametrar och /etc/odbcinst.ini för att deklarera drivrutiner:

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot; motsvarar platsen för filen **odbcinst.ini** .

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      teradata=Installed
      
      [teradata]
      Driver=/opt/teradata/client/15.10/lib64/tdata.so
      APILevel=CORE
      ConnectFunctions=YYY
      DriverODBCVer=3.51
      SQLLevel=1
      ```

1. Ange miljövariablerna för Adobe Campaign-servern:

   * **LD_LIBRARY_PATH**: /opt/teradata/client/15.10/lib64 och /opt/teradata/client/15.10/odbc_64/lib.
   * **ODBCINI**: platsen för filen odbc.ini (till exempel /etc/odbc.ini).
   * **NLSPATH**: plats för filen opermsgs.cat (/opt/teradata/client/15.10/msg/opermsgs.cat)

1. I Campaign Classic kan du sedan konfigurera ditt externa Teradata-konto. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. Om du vill konfigurera det **[!UICONTROL Teradata]** externa kontot måste du ange:

   * **[!UICONTROL Type]**: Teradata

   * **[!UICONTROL Server]**: URL för Teradata-servern

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namn på databasen

## Konfigurera åtkomst till SAP HANA {#configure-access-to-sap-hana}

Anslutning till en extern SAP HANA-databas i FDA kräver vissa ytterligare konfigurationer på Adobe Campaign-servern:

1. Installera ODBC-drivrutinerna för SAP HANA, enligt det operativsystem du använder:

   * **hdb_client_linux.tgz** för Linux. När du har packat upp en fil startar du kommandot hdbinst och följer instruktionerna för att slutföra installationen av drivrutinerna.
   * **hdb_client_windows.zip** för Windows. Zippa upp filen och starta den körbara filen: **hdbinst.exe**. Följ instruktionerna i guiden för att slutföra installationen av drivrutinerna.

1. Konfigurera ODBC-drivrutinen. Konfigurationen kan utföras i standardfilerna: /etc/odbc.ini för allmänna parametrar och /etc/odbcinst.ini för att deklarera drivrutiner.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      &quot;InstallDir&quot; motsvarar platsen för filen **odbcinst.ini** .

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Ange miljövariablerna för Adobe Campaign-servern:

   * **LD_LIBRARY_PATH**: Den bör innehålla länken till SAP Hana-klienten (/usr/sap/hdbclient/libodbcHDB.so) som standard.
   * **ODBCINI**: platsen för filen odbc.ini (till exempel /etc/odbc.ini).

1. I Campaign Classic kan du sedan konfigurera ditt externa SAP Hana-konto. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. Om du vill konfigurera det **[!UICONTROL SAP Hana]** externa kontot måste du ange:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL för SAP Hana-servern

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto
