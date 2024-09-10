---
product: campaign
title: Konfigurera åtkomst till [!DNL Vertica Analytics]
description: Lär dig konfigurera åtkomst till  [!DNL Vertica Analytics]  i FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# Konfigurera åtkomst till [!DNL Vertica Analytics] {#configure-fda-vertica}



Använd alternativet **FDA (Federated Data Access**) i kampanjen om du vill bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till [!DNL Vertica Analytics].

1. Konfigurera [!DNL Vertica Analytics] på [CentOS](#vertica-centos), [Windows](#vertica-windows) eller [Debian](#vertica-debian)
1. Konfigurera det [!DNL Vertica Analytics] [externa kontot](#vertica-external) i Campaign

![](assets/snowflake_3.png)

## [!DNL Vertica Analytics] i CentOS {#vertica-centos}

Följ stegen nedan för att konfigurera [!DNL Vertica Analytics] i CentOS:

1. Hämta ODBC-drivrutiner för [!DNL Vertica Analytics]. [Klicka här](https://www.vertica.com/download/vertica/client-drivers/) och hämta den senaste Linux RPM-modulen.

1. Därefter måste du installera unixODBC med följande kommando:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Om du redan har installerat servern [!DNL Vertica Analytics] installeras en ODBC-drivrutin. I så fall ska du uppdatera enheten enligt följande:

   ```
   #Switch to root
   sudo su
   
   #Install the package (add --force to update it)
   rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica Analytics and save
   [VerVertica Analyticstica]
   Description = Vertica Analytics ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica Analytics"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica Analytics
   Database = VMart
   Servername = # The name of the server where Vertica Analytics is installed. Use localhost if Vertica Analytics is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   
   #Cleanup
   #Remove the ODBC package
   rm vertica-client-x.x.x-x.x86_64.rpm
   ```

1. I Adobe Campaign kan du sedan konfigurera ditt [!DNL Vertica Analytics]-externa konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#vertica-external).

## [!DNL Vertica Analytics] i Windows {#vertica-windows}

1. Hämta [ODBC-drivrutinen för Windows](https://www.vertica.com/download/vertica/client-drivers/). Om du vill installera drivrutinen för Windows måste du aktivera .NET Framework 3.5, annars försöker installationsassistenten att aktivera och hämta den automatiskt.

1. Konfigurera ODBC-drivrutinen i Windows. Mer information finns på [sidan](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. I Adobe Campaign kan du sedan konfigurera ditt [!DNL Vertica Analytics]-externa konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#vertical-external).

## [!DNL Vertica Analytics] på Debian {#vertica-debian}

1. Hämta ODBC-drivrutiner för [!DNL Vertica Analytics]. [Klicka här](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) för att påbörja hämtningen.

1. Därefter måste du installera unixODBC med följande kommando:

   ```
   apt-get install unixODBC
   ```

1. Om du redan har installerat servern [!DNL Vertica Analytics] installeras en ODBC-drivrutin. I så fall ska du uppdatera enheten enligt följande:

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
   
   #Add a section for Vertica Analytics and save
   [Vertica Analytics]
   Description = Vertica Analytics ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica Analytics"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica Analytics
   Database = VMart
   Servername = # The name of the server where Vertica Analytics is installed. Use localhost if Vertica Analytics is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   ```

1. I Adobe Campaign kan du sedan konfigurera ditt [!DNL Vertica Analytics]-externa konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#vertica-external).

## [!DNL Vertica Analytics] externt konto {#vertica-external}

Du måste skapa ett externt [!DNL Vertica Analytics]-konto för att ansluta Campaign-instansen till din [!DNL Vertica Analytics]-externa databas.

1. Klicka på **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** i Campaign **[!UICONTROL Explorer]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som det externa kontots **[!UICONTROL Type]**.

1. Konfigurera det externa **[!UICONTROL Vertica Analytics]**-kontot måste du ange:

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL för servern [!DNL Vertica Analytics]

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namn på databasen

   ![](assets/vertica.png)

Kopplingen stöder följande alternativ:

| Alternativ | Beskrivning |
|---|---|
| TimeZoneName | Som standard är den tom, vilket innebär att systemtidszonen för Campaign Classicens programserver används. Alternativet kan användas för att framtvinga TIMEZONE-sessionsparametern. |

