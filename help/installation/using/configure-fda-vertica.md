---
product: campaign
title: Konfigurera åtkomst till Vertica
description: Lär dig konfigurera åtkomst till Vertica i FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: 0cfe8439007b56014eba497c511904c4f11b39ce
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 4%

---

# Konfigurera åtkomst till Vertica {#configure-fda-vertica}

![](../../assets/v7-only.svg)

Använd kampanj **Åtkomst till federerade data** (FDA) om du vill bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till [!DNL Vertica].

1. Konfigurera [!DNL Vertica] på [CentOS](#vertica-centos), [Windows](#vertica-windows) eller [Debian](#vertica-debian)
1. Konfigurera [!DNL Vertica] [externt konto](#vertica-external) i Campaign


>[!NOTE]
>
>[!DNL Vertica] anslutningsprogrammet är tillgängligt för hybriddistributioner och driftsättningar på plats. Mer information finns på [den här sidan](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Vertica on CentOS {#vertica-centos}

Konfigurera [!DNL Vertica] i CentOS följer du stegen nedan:

1. Ladda ned ODBC-drivrutiner för [!DNL Vertica]. [Klicka här](https://www.vertica.com/download/vertica/client-drivers/) och ladda ned senaste Linux RPM.

1. Därefter måste du installera unixODBC med följande kommando:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. Om du tidigare har installerat [!DNL Vertica] Servern kommer en ODBC-drivrutin redan att installeras. I så fall ska du uppdatera enheten enligt följande:

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

1. I Adobe Campaign kan du sedan konfigurera [!DNL Vertica] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#vertica-external).

## Vertica on Windows {#vertica-windows}

1. Ladda ned [ODBC-drivrutin för Windows](https://www.vertica.com/download/vertica/client-drivers/). Om du vill installera drivrutinen för Windows måste du aktivera .NET Framework 3.5, annars försöker installationsguiden automatiskt aktivera och hämta den.

1. Konfigurera ODBC-drivrutinen i Windows. Mer information finns på [den här sidan](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. I Adobe Campaign kan du sedan konfigurera [!DNL Vertica] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#vertical-external).

## Vertica on Debian {#vertica-debian}

1. Ladda ned ODBC-drivrutiner för [!DNL Vertica]. [Klicka här](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) börja ladda ned.

1. Därefter måste du installera unixODBC med följande kommando:

   ```
   apt-get install unixODBC
   ```

1. Om du tidigare har installerat [!DNL Vertica] Servern kommer en ODBC-drivrutin redan att installeras. I så fall ska du uppdatera enheten enligt följande:

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

1. I Adobe Campaign kan du sedan konfigurera [!DNL Vertica] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#vertica-external).

## Vertikalt externt konto {#vertica-external}

Du måste skapa en [!DNL Vertica] externt konto för att ansluta Campaign-instansen till [!DNL Vertica] extern databas.

1. Från kampanj **[!UICONTROL Explorer]**, klicka **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som ditt externa konto **[!UICONTROL Type]**.

1. Konfigurera **[!UICONTROL Vertica]** externt konto måste du ange:

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**: URL för [!DNL Vertica] server

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namn på databasen
   ![](assets/vertica.png)
