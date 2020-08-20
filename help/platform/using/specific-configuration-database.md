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
source-git-commit: 3b752b283a14bc75954fe46da5a21970c1e17fa1
workflow-type: tm+mt
source-wordcount: '1833'
ht-degree: 2%

---


# Konfigurera FDA-anslutningar {#specific-configurations-by-database-type}

Beroende på vilka externa databaser du vill kunna komma åt från Adobe Campaign måste du utföra vissa specifika konfigurationer. Dessa konfigurationer innebär i princip att installera drivrutiner och deklarera miljövariabler som tillhör varje RDBMS på Adobe Campaign-servern.

Mer information om äldre anslutningar som Teradata, Hadoop 2.1 och Netezza finns på den här [sidan](../../platform/using/legacy-connectors.md).

Som regel måste du installera motsvarande klientlager på den externa databasen på Adobe Campaign-servern.

>[!NOTE]
>
>Kompatibla versioner visas i [Campaign-kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA).

## Konfigurera åtkomst till Azure Synapse {#configure-access-to-azure-synapse}

### Azure synapse external account {#azure-external}

Med det [!DNL Azure] externa kontot kan du ansluta Campaign-instansen till din externa Azure Synapse-databas.
Så här skapar du ett externt [!DNL Azure Synapse] konto:

1. Konfigurera ditt [!DNL Azure Synapse] externa konto i Campaign Classic. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som det externa kontots **[!UICONTROL Type]**.

1. Konfigurera det [!DNL Azure Synapse] externa kontot måste du ange:

   * **[!UICONTROL Type]**: Azure Synapse Analytics

   * **[!UICONTROL Server]**: URL för Azure Synapse-servern

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namn på databasen

   ![](assets/azure_1.png)

### Azure Synapse i CentOS {#azure-centos}

**Förhandskrav:**

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
   >Om du vill tillåta kommunikation från Azure Synapse Analytics-sidan kan du behöva lägga till din offentliga IP-adress i tillåtelselista. Om du vill göra det läser du i [Azure-dokumentationen](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

1. Om det är iptables kör du följande kommando:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

### Azure Synapse i Windows {#azure-windows}

>[!NOTE]
>
>Detta gäller endast version 13 av ODBC-drivrutinen, men Adobe Campaign Classic kan även använda drivrutinerna 11.0 och 10.0 för SQL Server Native Client.

Så här konfigurerar du Azure Synapse i Windows:

1. Installera först Microsoft ODBC-drivrutinen. Du hittar den på den här [sidan](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

1. Välj följande filer att installera:

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. När ODBC-drivrutinen har installerats kan du testa den om det behövs. Se denna [sida](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server) för mer information om detta.

1. I Campaign Classic kan du sedan konfigurera ditt [!DNL Azure Synapse] externa konto. Mer information om hur du konfigurerar ditt externa konto finns i det här [avsnittet](../../platform/using/specific-configuration-database.md#azure-external).

1. Eftersom Azure Synapse Analytics kommunicerar via TCP 1433-porten måste du öppna den här porten i Windows Defender-brandväggen. For more on this, refer to [Windows documentation](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

### Azure Synapse på Debian {#azure-debian}

**Förhandskrav:**

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
   >Om du vill tillåta kommunikation från Azure Synapse Analytics-sidan kan du behöva lägga till din offentliga IP-adress i tillåtelselista. Om du vill göra det läser du i [Azure-dokumentationen](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

## Konfigurera åtkomst till Snowflake {#configure-access-to-snowflake}

>[!NOTE]
>
>[!DNL Snowflake] anslutning finns för värdbaserade och lokala distributioner. For more on this, refer to [this article](https://helpx.adobe.com/se/campaign/kb/acc-on-prem-vs-hosted.html).

![](assets/snowflake_3.png)

### Snowflake external account {#snowflake-external}

Med det [!DNL Snowflake] externa kontot kan du ansluta Campaign-instansen till din externa Snowflake-databas.

1. Konfigurera ditt [!DNL Snowflake] externa konto i Campaign Classic. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som det externa kontots **[!UICONTROL Type]**.

1. Konfigurera det **[!UICONTROL Snowflake]** externa kontot måste du ange:

   * **[!UICONTROL Type]**: [!DNL Snowflake]

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
| TimeZoneName | Som standard är den tom, vilket innebär att systemtidszonen för programservern i Campaign Classic används. Alternativet kan användas för att framtvinga TIMEZONE-sessionsparametern. <br>[Se denna sida](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone) för mer information om detta. |
| WeekStart | WEEK_START-sessionsparameter. Standardinställningen är 0. <br>[Se denna sida](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start) för mer information om detta. |
| AnvändCachedResult | USE_CACHED_RESULTS sessionsparameter. Standardinställningen är TRUE. Det här alternativet kan användas för att inaktivera cachelagrade resultat i Snowflake. <br>[Se denna sida](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html) för mer information om detta. |

### Snowflake på CentOS {#snowflake-centos}

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

### Snowflake på Debian {#snowflake-debian}

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

### Snowflake i Windows {#snowflake-windows}

1. Hämta [ODBC-drivrutinen för Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). Observera att du behöver administratörsbehörighet för att installera drivrutinen. For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. Konfigurera ODBC-drivrutinen. For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. I Campaign Classic kan du sedan konfigurera ditt [!DNL Snowflake] externa konto. Mer information om hur du konfigurerar ditt externa konto finns i det här [avsnittet](../../platform/using/specific-configuration-database.md#snowflake-external).

## Konfigurera åtkomst till Hadoop 3.0 {#configure-access-to-hadoop-3}

### Hadoop-externt konto {#hadoop-external}

Med det [!DNL Hadoop] externa kontot kan du ansluta Campaign-instansen till din externa Hadoop-databas.

1. Konfigurera ditt [!DNL Hadoop] externa konto i Campaign Classic. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som det externa kontots **[!UICONTROL Type]**.

1. Konfigurera det **[!UICONTROL Hadoop]** externa kontot måste du ange:

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

### Konfigurera Hadoop 3.0 {#configuring-hadoop}

För att ansluta till en extern Hadoop-databas i FDA krävs följande konfigurationer på Adobe Campaign-servern. Observera att den här konfigurationen är tillgänglig för både Windows och Linux.

1. Hämta ODBC-drivrutinerna för Hadoop beroende på vilken OS-version du har. Drivrutiner finns på [den här sidan](https://www.cloudera.com/downloads.html).

1. Du måste sedan installera ODBC-drivrutinerna och skapa ett DSN för din Hive-anslutning. Instruktioner finns på [den här sidan](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. När du har hämtat och installerat ODBC-drivrutinerna måste du starta om Campaign Classic. Om du vill göra det kör du följande kommando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. I Campaign Classic kan du sedan konfigurera ditt [!DNL Hadoop] externa konto. Mer information om hur du konfigurerar ditt externa konto finns i det här [avsnittet](../../platform/using/specific-configuration-database.md#hadoop-external).

## Konfigurera åtkomst till Oracle {#configure-access-to-oracle}

### Externt Oracle-konto {#oracle-external}

Med det [!DNL Oracle] externa kontot kan du ansluta Campaign-instansen till din externa Hadoop-databas.

1. Konfigurera ditt [!DNL oracle] externa konto i Campaign Classic. From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som det externa kontots **[!UICONTROL Type]**.

1. Konfigurera det **[!UICONTROL Oracle]** externa kontot måste du ange:

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**: DNS-namn

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Time zone]**: Tidszon för server

   ![](assets/oracle_config.png)

### Oracle på Linux {#for-linux-1}

För att ansluta till en extern Oracle-databas i FDA krävs ytterligare konfigurationer nedan på Adobe Campaign-servern.

1. Installera den fullständiga Oracle-klienten som motsvarar din version av Oracle.
1. Lägg till dina TNS-definitioner i installationen. Om du vill göra det anger du dem i en **namnfil.ora** i databasen /etc/oracle. Om den här databasen inte finns skapar du den.

   Skapa sedan en ny TNS_ADMIN-miljövariabel: exportera TNS_ADMIN=/etc/oracle och starta om datorn.

1. Integrera Oracle med din Adobe Campaign-server (nlserver). Det gör du genom att kontrollera att filen **customer.sh** finns i mappen &quot;nl6&quot; i trädstrukturen för Adobe Campaign och att den innehåller länkar till Oracle-biblioteken.

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

1. I Campaign Classic kan du sedan konfigurera ditt [!DNL Oracle] externa konto. Mer information om hur du konfigurerar ditt externa konto finns i det här [avsnittet](../../platform/using/specific-configuration-database.md#oracle-external).

### Oracle i Windows {#for-windows-1}

För att ansluta till en extern Oracle-databas i FDA krävs ytterligare konfigurationer nedan på Adobe Campaign-servern.

1. Installera Oracle-klienten.

1. I mappen C:Oracle skapar du en **namnfil.ora** som innehåller din TNS-definition.

1. Lägg till en TNS_ADMIN-miljövariabel med C:Oracle som-värde och starta om datorn.

1. I Campaign Classic kan du sedan konfigurera ditt [!DNL Oracle] externa konto. Mer information om hur du konfigurerar ditt externa konto finns i det här [avsnittet](../../platform/using/specific-configuration-database.md#oracle-external).