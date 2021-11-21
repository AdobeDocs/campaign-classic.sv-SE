---
product: campaign
title: Konfigurera åtkomst till Google BigQuery
description: Lär dig konfigurera åtkomst till Google BigQuery i FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 6d53ba957fb567a9a921544418a73a9bde37c97b
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 2%

---

# Konfigurera åtkomst till Google BigQuery {#configure-fda-google-big-query}

![](../../assets/v7-only.svg)

Använd Adobe Campaign Classic **Åtkomst till federerade data** (FDA) om du vill bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till [!DNL Google BigQuery].

1. Konfigurera [!DNL Google BigQuery] på [Windows](#google-windows) eller [Linux](#google-linux)
1. Konfigurera [!DNL Google BigQuery] [externt konto](#google-external) i Adobe Campaign Classic
1. Konfigurera [!DNL Google BigQuery] massinläsning av koppling på [Windows](#bulk-load-windows) eller [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] anslutningsprogrammet är tillgängligt för hybriddistributioner och driftsättningar på plats. Mer information finns på [den här sidan](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Google BigQuery i Windows {#google-windows}

### Drivrutinen har konfigurerats i Windows {#driver-window}

1. Ladda ned [ODBC-drivrutin för Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Konfigurera ODBC-drivrutinen i Windows. Mer information finns på [den här sidan](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf).

1. För [!DNL Google BigQuery] för att Adobe Campaign Classic ska fungera krävs följande parametrar för att ansluta:

   * **[!UICONTROL Project]**: skapa eller använda ett befintligt projekt.

      Mer information finns i [page](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Service account]**: skapa ett tjänstkonto.

      Mer information finns i [page](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]**: den **[!UICONTROL Service account]** kräver **[!UICONTROL Key File]** för [!DNL Google BigQuery] anslutning via ODBC.

      Mer information finns i [page](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** är valfritt för en ODBC-anslutning. Eftersom varje fråga måste ange datauppsättningen där tabellen finns, anger du en **[!UICONTROL Dataset]** är obligatoriskt för [!DNL Google BigQuery] FDA Connector i Adobe Campaign Classic.

      Mer information finns i [page](https://cloud.google.com/bigquery/docs/datasets).

1. I Adobe Campaign Classic kan du sedan konfigurera [!DNL Google BigQuery] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#google-external).

### Massinläsning har konfigurerats i Windows {#bulk-load-window}

>[!NOTE]
>
>Python måste vara installerat för att Google Cloud SDK ska fungera.
>
>Vi rekommenderar att du använder Python3. [page](https://www.python.org/downloads/).

Med Bulk Load Tool går det snabbare att överföra filer, vilket uppnås med Google Cloud SDK.

1. Hämta 64-bitars Windows-arkiv (x86_64) från detta [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives) och extrahera den i motsvarande katalog.

1. Kör `google-cloud-sdk\install.sh` skript. Du måste acceptera inställningen för variabeln path.

1. Kontrollera att variabeln path finns efter installationen `...\google-cloud-sdk\bin` är inställt. Om inte, lägg till det manuellt.

1. I  `..\google-cloud-sdk\bin\bq.cmd` fil, lägga till `CLOUDSDK_PYTHON` lokal variabel, som kommer att dirigeras om till platsen för Python-installationen.

   Exempel:

   ![](assets/google-big-query_1.png)

1. Starta om Adobe Campaign Classic för att ta hänsyn till ändringarna.

## Google BigQuery i Linux {#google-linux}

### Drivrutinen har konfigurerats i Linux {#driver-linux}

1. Innan du installerar ODBC-drivrutinen måste du uppdatera datorn. Kör följande kommando i Linux eller CentOS:

   ```
   yum update
   # install unixODBC driver manager
   yum install unixODBC
   ```

1. Du måste sedan installera drivrutinshanteraren unixODBC med följande kommando:

   ```
   # switch to root user
   sudo su
   ```

   På Debian:

   ```
   apt-get update
   apt-get upgrade
   # install unixODBC driver manager
   apt-get install unixODBC
   ```

1. Ladda ned [Magnitude Simba Linux ODBC Driver (.tar.gz)](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers). Överför sedan Tarball-filen till en tillfällig mapp på datorn eller använd wget-kommandot:

   ```
   # in this example driver version is 2.3.1.1001
   wget https://storage.googleapis.com/simba-bq-release/odbc/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux.tar.gz
   ```

1. Extrahera huvudkulfilen enligt följande **TarballName** är namnet på det tarbollspaket som innehåller föraren:

   ```
   tar --directory=/tmp -zxvf [TarballName]
   ```

1. Gå till den mapp du extraherade och extrahera den inre kulfilen som motsvarar drivrutinens version. Installera den i en annan tillfällig mapp i följande exempel: BigQueryDriver:

   ```
   mkdir /tmp/BigQueryDriver/
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   tar --directory=/tmp/BigQueryDriver/ -zxvf SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version].tar.gz
   ```

1. Gå till den tillfälliga platsen där huvudkulfilen extraherades och kopiera `GoogleBigQueryODBC.did` och `setup/simba.googlebigqueryodbc.ini` filer till den nya mappen som skapades i föregående steg:

   ```
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   cp GoogleBigQueryODBC.did /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   cp setup/simba.googlebigqueryodbc.ini /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   ```

1. Skapa installationskatalogen enligt följande:

   ```
   mkdir -p /opt/simba/googlebigqueryodbc/
   ```

1. Kopiera innehållet i katalogen till den nya installationskatalogen:

   ```
   cp -r /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/* /opt/simba/googlebigqueryodbc/
   ```

1. Ersätt `<INSTALLDIR>` med `/opt/simba/googlebigqueryodbc` in `simba.googlebigqueryodbc.ini` i installationskatalogen:

   ```
   cd /opt/simba/googlebigqueryodbc/lib/
   sed -i 's/<INSTALLDIR>/\/opt\/simba\/googlebigqueryodbc/g' simba.googlebigqueryodbc.ini
   ```

1. Ändra `DriverManagerEncoding` till UTF-16 och `SwapFilePath` in `simba.googlebigqueryodbc.ini`. Om det behövs kan du även ändra loggningsinställningarna.

   Följande är ett exempel på en uppdaterad konfigurationsfil för hela drivrutinen:

   ```
   # /opt/simba/googlebigqueryodbc/lib/simba.googlebigqueryodbc.ini
   [Driver]
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=opt/simba/googlebigqueryodbc/ErrorMessages
   LogLevel=6
   LogPath=/tmp
   SwapFilePath=/tmp
   ```

1. Om du använder en systemdrivrutinsfil eller någon annan aktuell `odbcinst.ini` fil, konfigurera `/etc/odbcinst.ini` för att peka på platsen för Google BigQuery-drivrutinen `/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb[Bitness].so`.

   Exempel:

   ```
   # /etc/odbcinst.ini
   # Make sure to use Simba ODBC Driver for Google BigQuery as a driver name.
   
   [ODBC Drivers]
   Simba ODBC Driver for Google BigQuery=Installed
   
   [Simba ODBC Driver for Google BigQuery]
   Description=Simba ODBC Driver for Google BigQuery(64-bit)
   Driver=/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   ```

1. Hitta platsen för unixODBC-drivrutinshanterarbiblioteken och lägg till `unixODBC` och `googlebigqueryodbc` bibliotekssökvägar till `LD_LIBRARY_PATH environment` variabel.

   ```
   find / -name 'lib*odbc*.so*' -print
   #output:
   /usr/lib/x86_64-linux-gnu/libodbccr.so.2
   /usr/lib/x86_64-linux-gnu/libodbcinst.so.2.0.0
   /usr/lib/x86_64-linux-gnu/libodbccr.so.1
   .
   .
   /opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   
   #the command would look like this
   export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/simba/googlebigqueryodbc:/usr/lib
   ```

1. I Adobe Campaign Classic kan du sedan konfigurera [!DNL Google BigQuery] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#google-external).

### Massinläsning konfigurerad för Linux {#bulk-load-linux}

>[!NOTE]
>
>Python måste vara installerat för att Google Cloud SDK ska fungera.
>
>Vi rekommenderar att du använder Python3. [page](https://www.python.org/downloads/).

Med Bulk Load Tool går det snabbare att överföra filer, vilket uppnås med Google Cloud SDK.

1. Ladda ned 64-bitars Linux-arkiv (x86_64) i detta [page](https://cloud.google.com/sdk/docs/downloads-versioned-archives) och extrahera i motsvarande katalog.

1. Kör `google-cloud-sdk\install.sh` skript. Du måste acceptera inställningen för variabeln path.

1. Kontrollera att variabeln path finns efter installationen `...\google-cloud-sdk\bin` är inställt. Om inte, lägg till det manuellt.

1. Om du inte vill använda `PATH` eller om du vill flytta `google-cloud-sdk` till en annan plats använder du `bqpath` alternativvärde vid konfigurering av **[!UICONTROL External account]** för att ange den exakta sökvägen till bin-katalogen på datorn.

1. Starta om Adobe Campaign Classic för att ta hänsyn till ändringarna.

## Externt Google BigQuery-konto {#google-external}

Du måste skapa en [!DNL Google BigQuery] externt konto för att ansluta din Adobe Campaign Classic-instans till [!DNL Google BigQuery] extern databas.

1. Från Adobe Campaign Classic **[!UICONTROL Explorer]**, klicka **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som ditt externa konto **[!UICONTROL Type]**.

1. Konfigurera [!DNL Google BigQuery] externt konto måste du ange:

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**: E-post till **[!UICONTROL Service account]**. Mer information finns i [Google Cloud-dokumentation](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Project]**: Ditt namn **[!UICONTROL Project]**. Mer information finns i [Google Cloud-dokumentation](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**: välj **[!UICONTROL Click here to upload]** om du väljer att överföra nyckeln via Adobe Campaign Classic.

      * **[!UICONTROL Enter manually the key file path]**: kopiera/klistra in den absoluta sökvägen i det här fältet om du väljer att använda en befintlig nyckel.
   * **[!UICONTROL Dataset]**: Ditt namn **[!UICONTROL Dataset]**. Mer information finns i [Google Cloud-dokumentation](https://cloud.google.com/bigquery/docs/datasets-intro).
   ![](assets/google-big-query.png)
