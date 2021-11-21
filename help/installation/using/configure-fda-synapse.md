---
product: campaign
title: Konfigurera åtkomst till Synapse
description: Learn how to configure access to Synapse in FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 59d0277a-7588-4504-94e3-50f87b60da8a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 1%

---

# Konfigurera åtkomst till Azure synapse {#configure-access-to-azure-synapse}

![](../../assets/v7-only.svg)

Använd kampanj [Åtkomst till federerade data](../../installation/using/about-fda.md) (FDA) om du vill bearbeta information som lagras i en extern databas. Follow the steps below to configure access to Microsoft Azure Synapse Analytics.

1. Konfigurera Azure synapse på [CentOS](#azure-centos), [Windows](#azure-windows) eller [Debian](#azure-debian)
1. Konfigurera Azure synapse [externt konto](#azure-external) i Campaign

## azure synapse på CentOS {#azure-centos}

>[!CAUTION]
>
>* Du måste ha rotbehörighet för att installera en ODBC-drivrutin.
>* Red Hat Enterprise ODBC-drivrutiner från Microsoft kan också användas med CentOS för att ansluta till SQL Server.
>* Version 13.0 fungerar med Red Hat 6 och 7.


Så här konfigurerar du Azure synapse i CentOS:

1. Installera först ODBC-drivrutinen. Du hittar den i det här [page](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

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

1. After installing the drivers, you can test and verify your ODBC Driver and query your database if needed. Run the following command:

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. I Campaign kan du sedan konfigurera [!DNL Azure Synapse] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#azure-external).

1. Eftersom Azure synapse Analytics kommunicerar via TCP 1433-porten måste du öppna den här porten på din brandvägg. Use the following command:

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >To allow communication from Azure Synapse Analytics&#39; side you might need to add your public IP to the allowlist. Om du vill göra det går du till [Azure-dokumentation](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).

1. Om det är iptables kör du följande kommando:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

## azure synapse i Windows {#azure-windows}

>[!NOTE]
>
>Detta gäller endast version 13 av ODBC-drivrutinen, men Adobe Campaign Classic kan även använda drivrutinerna 11.0 och 10.0 för SQL Server Native Client.

To configure Azure Synapse on Windows:

1. First, install the Microsoft ODBC driver. You can find it in [this page](https://www.microsoft.com/en-us/download/details.aspx?id=50420).

1. Choose the following files to install:

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. När ODBC-drivrutinen har installerats kan du testa den om det behövs. Se denna [sida](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server) för mer information om detta.

1. I Campaign Classic kan du sedan konfigurera [!DNL Azure Synapse] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#azure-external).

1. Eftersom Azure synapse Analytics kommunicerar via TCP 1433-porten måste du öppna den här porten i Windows Defender-brandväggen. Mer information finns i [Windows-dokumentation](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

## Azure Synapse on Debian {#azure-debian}

**Förhandskrav:**

* You will need root privileges to install a ODBC driver.
* Rullning krävs för att installera paketet mSolbcsql. Om du inte har det installerat kör du följande kommando:

   ```
   sudo apt-get install curl
   ```

To configure Azure Synapse on Debian:

1. First, install the Microsoft ODBC driver for SQL Server. Använd följande kommandon för att installera ODBC-drivrutinen 13.1 för SQL Server:

   ```
   sudo su
   curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
   curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
   exit
   sudo apt-get update
   sudo ACCEPT_EULA=Y apt-get install msodbcsql
   ```

1. Om du får följande fel **&quot;Det gick inte att hitta metoddrivrutinen /usr/lib/apt/methods/https&quot;** vid anrop **sudo apt-get update** ska du köra kommandot:

   ```
   sudo apt-get install apt-transport-https ca-certificates
   ```

1. You now need to install mssql-tools with the following commands. Mssq-tools behövs för att använda BCP-verktyget och köra frågor.

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

1. I Campaign Classic kan du nu konfigurera [!DNL Azure Synapse] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#azure-external).

1. Aktivera den utgående TCP 1433-porten för värdnamnet med följande kommando för att konfigurera iptables på Debian för att säkerställa anslutningen med Azure synapse Analytics:

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >Om du vill tillåta kommunikation från Azure synapse Analytics-sidan kan du behöva lägga till ditt offentliga IP-värde i tillåtelselista. Om du vill göra det går du till [Azure-dokumentation](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules).


## azure synapse external account {#azure-external}

The [!DNL Azure Synapse] external account allows you to connect your Campaign instance to your Azure Synapse external database.

Skapa [!DNL Azure Synapse] externt konto följer du stegen nedan:

1. From Campaign **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som ditt externa konto **[!UICONTROL Type]**.

   ![](assets/azure_1.png)

1. Configure the [!DNL Azure Synapse] external account, you must specify:

   * **[!UICONTROL Type]**: azure synapse Analytics

   * **[!UICONTROL Server]**: AZURE SYNAPSE-serverns URL

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Name of the database
