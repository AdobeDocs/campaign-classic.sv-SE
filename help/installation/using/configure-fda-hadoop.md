---
product: campaign
title: Konfigurera åtkomst till Hadoopet
description: Lär dig hur du konfigurerar åtkomst till Hadoopet i FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: e3a97e55-dd8b-41e1-b48c-816d973f62a8
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Konfigurera åtkomst till Hadoopet {#configure-access-to-hadoop}



Använd alternativet **FDA (Federated Data Access**) i kampanjen om du vill bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till Hadoopet.

1. Konfigurera [Hadoopen databas](#configuring-hadoop)
1. Konfigurera Hadoopet [externt konto](#hadoop-external) i Campaign

## Konfigurera Hadoop 3.0 {#configuring-hadoop}

För att ansluta till en extern Hadoop-databas i FDA krävs följande konfigurationer på Adobe Campaign-servern. Observera att den här konfigurationen är tillgänglig för både Windows och Linux.

1. Hämta ODBC-drivrutinerna för Hadoop beroende på vilken OS-version du har. Drivrutiner finns på [den här sidan](https://www.cloudera.com/downloads.html).

1. Du måste sedan installera ODBC-drivrutinerna och skapa ett DSN för din Hive-anslutning. Instruktioner finns på [den här sidan](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. När du har hämtat och installerat ODBC-drivrutinerna måste du starta om Campaign Classicen. Om du vill göra det kör du följande kommando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. I Campaign Classicen kan du sedan konfigurera ditt [!DNL Hadoop]-externa konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#hadoop-external).

## Hadoopets externa konto {#hadoop-external}

Med det externa kontot [!DNL Hadoop] kan du ansluta Campaign-instansen till Hadoopets externa databas.

1. Konfigurera ditt externa [!DNL Hadoop]-konto i Campaign Classicen. Klicka på **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]** i **[!UICONTROL Explorer]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som det externa kontots **[!UICONTROL Type]**.

1. Konfigurera det externa **[!UICONTROL Hadoop]**-kontot måste du ange:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Namn på DNS

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namnet på databasen om det inte anges i DSN. Den kan lämnas tom om den anges i DSN

   * **[!UICONTROL Time zone]**: Serverns tidszon

   ![](assets/hadoop3.png)

Kopplingen stöder följande ODBC-alternativ:

| Namn | Värde |
|---|---|
| ODBCMgr | iODBC |
| lagerställe | 1/2/4 |

Kopplingen har även stöd för följande Hive-alternativ:

| Namn | Värde | Beskrivning |
|---|---|---|
| bulkKey | Åtkomstnyckel för Azure-blob eller DataLake | För wasb:// eller wasbs:// massinläsare (dvs. om massinläsningsverktyget börjar med wasb:// eller wasbs://). <br>Det är åtkomstnyckeln för blob- eller DataLake-bucket för massinläsning. |
| hdfsPort | portnummer <br>som standard är 8020 | För HDFS-massinläsning (dvs. om massinläsningsverktyget börjar med webhdfs:// eller webhdfss://). |
| bucketNumber | 20 | Antal grupper när en klustrad tabell skapas. |
| fileFormat | PARQUET | Standardfilformat för arbetsregister. |


## Konfigurerar Hadoop 2.1 {#configure-access-hadoop-2}

Om du behöver ansluta till Hadoop 2.1 följer du stegen som beskrivs nedan för [Windows](#for-windows) eller [Linux](#for-linux).

### Hadoop 2.1 för Windows {#for-windows}

1. Installera ODBC- och [Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886)-drivrutiner för Windows.
1. Skapa DSN (Data Source Name) genom att köra administrationsverktyget ODBC DataSource. Du kan ändra ett system-DSN-exempel för Hive.

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. Skapa Hadoopets externa konto, vilket beskrivs i [det här avsnittet](#hadoop-external).

### Hadoop 2.1 för Linux {#for-linux}

1. Installera unixodbc för Linux.

   ```
   apt-get install unixodbc
   ```

1. Hämta och installera ODBC-drivrutiner för Apache Hive från HortonWorks: [https://www.cloudera.com/downloads.html](https://www.cloudera.com/downloads.html).

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
   >Parametern **UseNativeQuery** här är mycket viktig. Campaign är Hive-medveten och fungerar inte korrekt om inte UseNativeQuery har angetts. Vanligtvis skriver drivrutinen eller Hive SQL Connector om frågor och ändrar kolumnordningen.

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

1. Skapa Hadoopets externa konto, vilket beskrivs i [det här avsnittet](#hadoop-external).
