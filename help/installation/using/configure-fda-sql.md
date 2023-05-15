---
product: campaign
title: Konfigurera åtkomst till Microsoft SQL Server
description: Lär dig konfigurera åtkomst till Microsoft SQL Server
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 65ab4577-3126-4579-8fcc-e93772ebd1e8
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 1%

---

# Konfigurera åtkomst till Microsoft SQL Server {#configure-fda-sql}



Använd kampanj **Åtkomst till federerade data** (FDA) om du vill bearbeta information som lagras i en extern Microsoft SQL Server-databas. Följ stegen nedan för att konfigurera åtkomst till [!DNL Microsoft SQL Server].

1. Konfigurera [!DNL Microsoft SQL Server] på [CentOS](#sql-centos).
1. Konfigurera [!DNL Microsoft SQL Server] på [Linux](#sql-linux).
1. Konfigurera [!DNL Microsoft SQL Server] på [Windows](#sql-windows).
1. Konfigurera [!DNL Microsoft SQL Server] [externt konto](#sql-external) i Campaign

## Microsoft SQL Server on CentOS {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server] finns i CentOS 7 och 6.

Konfigurera [!DNL Microsoft SQL Server] i CentOS följer du stegen nedan:

1. Hämta och installera SQL ODBC-drivrutinen med följande kommando:

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. I Adobe Campaign kan du sedan konfigurera [!DNL Microsoft SQL Server] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#sql-external).

## Microsoft SQL Server i Linux {#sql-linux}

>[!NOTE]
>
> Om du kör en äldre version av Adobe Campaign (före 7.2.1) måste du installera `unix ODBC drivers`.

1. Hämta MS ODBC-drivrutinen från [den här sidan](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/).

1. Kör följande kommando som rotanvändare:

   ```
   # install the mssql odbc that was downloaded
   dpkg -i msodbcsql17_17.7.1.1-1_amd64.deb
   # accept the license terms
   ```

1. I Adobe Campaign kan du sedan konfigurera [!DNL Microsoft SQL Server] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#sql-external).

## Microsoft SQL Server i Windows {#sql-windows}

Konfigurera [!DNL Microsoft SQL Server] i Windows:

1. I Windows klickar du på **[!UICONTROL Control Panel]** &#39;>&#39; **[!UICONTROL System and Security]** &#39;>&#39; **[!UICONTROL Administrative Tools]**&#39;>&#39; **[!UICONTROL ODBC Data Sources (64-bit)]**.

1. Från **[!UICONTROL ODBC Data Sources (64-bit)]** nytt fönster, klicka **[!UICONTROL Add...]**.

1. Kontrollera om SQL Server Native Client v11 finns listad i **[!UICONTROL Create New Data Source]** -fönstret.

1. Om SQL Server Native Client inte finns med i listan kan du ladda ned den i [den här sidan](https://www.microsoft.com/en-my/download/details.aspx?id=36434).

1. I Adobe Campaign kan du sedan konfigurera [!DNL Microsoft SQL Server] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#sql-external).

## Externt Microsoft SQL Server-konto {#sql-external}

Du måste skapa en [!DNL Microsoft SQL Server] externt konto för att ansluta Campaign-instansen till [!DNL Microsoft SQL Server] extern databas.

1. Från kampanj **[!UICONTROL Explorer]**, klicka **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som ditt externa konto **[!UICONTROL Type]**.

1. Under **[!UICONTROL Configuration]**, markera [!DNL Microsoft SQL Server] från **[!UICONTROL Type]** nedrullningsbar meny.

   ![](assets/sql.png)

1. Konfigurera **[!UICONTROL Microsoft SQL Server]** autentisering av externt konto:

   * **[!UICONTROL Server]**: URL för [!DNL Microsoft SQL Server] server.

   * **[!UICONTROL Account]**: Användarens namn.

   * **[!UICONTROL Password]**: Lösenord för användarkonto.

   * **[!UICONTROL Database]**: Databasens namn (valfritt).

   * **[!UICONTROL Timezone]**: Tidszon inställd på [!DNL Microsoft SQL Server]. [Läs mer](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. Klicka på **[!UICONTROL Parameters]** tabben **[!UICONTROL Deploy functions]** för att skapa funktioner.

   >[!NOTE]
   >
   >För att alla funktioner ska vara tillgängliga måste du skapa Adobe Campaign SQL-funktionerna i fjärrdatabasen. Mer information finns i [page](../../configuration/using/adding-additional-sql-functions.md).

1. Klicka **[!UICONTROL Save]** när konfigurationen är klar.

Kopplingen stöder följande alternativ:

| Option | Beskrivning |
|---|---|
| Autentisering | Typ av autentisering som stöds av kopplingen. Aktuellt värde som stöds: ActiveDirectoryMSI. <br> Mer information finns i exempel 8 av [Microsoft-dokumentation](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings). |
| Kryptera | Anger om anslutningar använder TLS-kryptering över nätverket. Möjliga värden är **ja/obligatoriskt (18.0 och senare)**, **no/optional (18.0 and later)** och **strikt (18.0 och senare)**. Standardvärdet är **ja** i version 18.0 och senare och **no** i tidigare versioner. <br>Mer information finns i [Microsoft-dokumentation](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt). |
| TrustServerCertificate | Aktiverar kryptering med ett självsignerat servercertifikat när det används med **Kryptera**. <br>Godkända värden: **ja** eller **no** (standardvärde, vilket innebär att servercertifikatet valideras). |
