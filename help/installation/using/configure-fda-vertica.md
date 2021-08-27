---
solution: Campaign Classic
product: campaign
title: Konfigurera åtkomst till Vertica
description: Lär dig konfigurera åtkomst till Vertica i FDA
audience: platform
content-type: reference
topic-tags: connectors
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 4%

---


# Konfigurera åtkomst till Vertica {#configure-fda-vertica}

![](../../assets/v7-only.svg)

Använd alternativet Campaign **FDA (Federated Data Access**) om du vill bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till [!DNL Vertica].

1. Konfigurera [!DNL Vertica] på [CentOS](#vertica-centos), [Windows](#vertica-windows) eller [Debian](#vertica-debian)
1. Konfigurera [!DNL Vertica] [externt konto](#vertica-external) i Campaign


>[!NOTE]
>
>[!DNL Vertica] anslutningsprogrammet är tillgängligt för hybriddistributioner och driftsättningar på plats. Mer information finns på [den här sidan](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Vertica on CentOS {#vertica-centos}

Följ stegen nedan för att konfigurera [!DNL Vertica] för CentOS:

1. Hämta ODBC-drivrutinerna för [!DNL Vertica]. [Klicka ](https://www.vertica.com/download/vertica/client-drivers/) här och ladda ned den senaste Linux RPM-modulen.

1. Därefter måste du installera unixODBC med följande kommando:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Om du redan har installerat [!DNL Vertica]-servern installeras en ODBC-drivrutin. I så fall ska du uppdatera enheten enligt följande:

   ```
   #Switch to root
   sudo su
   
   #Install the package (add --force to update it)
   rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   
   #Cleanup
   #Remove the ODBC package
   rm vertica-client-x.x.x-x.x86_64.rpm
   ```

1. I Adobe Campaign kan du sedan konfigurera ditt externa [!DNL Vertica]-konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#vertica-external).

## Vertica on Windows {#vertica-windows}

1. Hämta [ODBC-drivrutinen för Windows](https://www.vertica.com/download/vertica/client-drivers/). Om du vill installera drivrutinen för Windows måste du aktivera .NET Framework 3.5, annars försöker installationsguiden automatiskt aktivera och hämta den.

1. Konfigurera ODBC-drivrutinen i Windows. Mer information finns på [den här sidan](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. I Adobe Campaign kan du sedan konfigurera ditt externa [!DNL Vertica]-konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#vertical-external).

## Vertica on Debian {#vertica-debian}

1. Hämta ODBC-drivrutinerna för [!DNL Vertica]. [Klicka på ](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) Hämta.

1. Därefter måste du installera unixODBC med följande kommando:

   ```
   apt-get install unixODBC
   ```

1. Om du redan har installerat [!DNL Vertica]-servern installeras en ODBC-drivrutin. I så fall ska du uppdatera enheten enligt följande:

   ```
   #Switch to root
   sudo su
   
   #Move or copy the downloaded file and change to /root
   mv vertica_9.3..xx_odbc_x86_64_linux.tar.gz /
   cd /
   
   #Uncompress the file you downloaded
   tar vzxf vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Remove the tar.gz since it is not needed anymore
   rm vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   ```

1. I Adobe Campaign kan du sedan konfigurera ditt externa [!DNL Vertica]-konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#vertica-external).

## Vertikalt externt konto {#vertica-external}

Du måste skapa ett externt [!DNL Vertica]-konto för att ansluta Campaign-instansen till din externa [!DNL Vertica]-databas.

1. Klicka på **[!UICONTROL Administration]** **[!UICONTROL Platform]** **[!UICONTROL External accounts]**  i Campaign **[!UICONTROL Explorer]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som **[!UICONTROL Type]** för ditt externa konto.

1. Konfigurera det externa **[!UICONTROL Vertica]**-kontot måste du ange:

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL för  [!DNL Vertica] servern

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namn på databasen
   ![](assets/vertica.png)
