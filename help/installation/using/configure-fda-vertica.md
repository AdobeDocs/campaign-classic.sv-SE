---
product: campaign
title: Konfigurera åtkomst till Vertica analytics
description: Lär dig konfigurera åtkomst till Vertica analytics i FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: ae235d39c4a78e0a2507f6baaebbdc9986dbf995
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 2%

---

# Konfigurera åtkomst till Vertica analytics {#configure-fda-vertica}

![](../../assets/v7-only.svg)

Använd kampanj **Åtkomst till federerade data** (FDA) om du vill bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till [!DNL Vertica Analytics].

1. Konfigurera [!DNL Vertica Analytics] på [CentOS](#vertica-centos), [Windows](#vertica-windows) eller [Debian](#vertica-debian)
1. Konfigurera [!DNL Vertica Analytics] [externt konto](#vertica-external) i Campaign

![](assets/snowflake_3.png)

## vertica analytics på CentOS {#vertica-centos}

Konfigurera [!DNL Vertica Analytics] i CentOS följer du stegen nedan:

1. Ladda ned ODBC-drivrutiner för [!DNL Vertica Analytics]. [Klicka här](https://www.vertica.com/download/vertica/client-drivers/) och ladda ned senaste Linux RPM.

1. Därefter måste du installera unixODBC med följande kommando:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Om du tidigare har installerat [!DNL Vertica Analytics] Servern kommer en ODBC-drivrutin redan att installeras. I så fall ska du uppdatera enheten enligt följande:

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

1. I Adobe Campaign kan du sedan konfigurera [!DNL Vertica Analytics] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#vertica-external).

## vertica analytics i Windows {#vertica-windows}

1. Ladda ned [ODBC-drivrutin för Windows](https://www.vertica.com/download/vertica/client-drivers/). Om du vill installera drivrutinen för Windows måste du aktivera .NET Framework 3.5, annars försöker installationsguiden automatiskt aktivera och hämta den.

1. Konfigurera ODBC-drivrutinen i Windows. Mer information finns på [den här sidan](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. I Adobe Campaign kan du sedan konfigurera [!DNL Vertica Analytics] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#vertical-external).

## vertica analytics på Debian {#vertica-debian}

1. Ladda ned ODBC-drivrutiner för [!DNL Vertica Analytics]. [Klicka här](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) börja ladda ned.

1. Därefter måste du installera unixODBC med följande kommando:

   ```
   apt-get install unixODBC
   ```

1. Om du tidigare har installerat [!DNL Vertica Analytics] Servern kommer en ODBC-drivrutin redan att installeras. I så fall ska du uppdatera enheten enligt följande:

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

1. I Adobe Campaign kan du sedan konfigurera [!DNL Vertica Analytics] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#vertica-external).

## vertica analytics externa konto {#vertica-external}

Du måste skapa en [!DNL Vertica Analytics] externt konto för att ansluta Campaign-instansen till [!DNL Vertica Analytics] extern databas.

1. Från kampanj **[!UICONTROL Explorer]**, klicka **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som ditt externa konto **[!UICONTROL Type]**.

1. Konfigurera **[!UICONTROL Vertica Analytics]** externt konto måste du ange:

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL för [!DNL Vertica Analytics] server

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namn på databasen

   ![](assets/vertica.png)

Kopplingen stöder följande alternativ:

| Option | Beskrivning |
|---|---|
| TimeZoneName | Som standard är den tom, vilket innebär att systemtidszonen för programservern i Campaign Classic används. Alternativet kan användas för att framtvinga TIMEZONE-sessionsparametern. |

