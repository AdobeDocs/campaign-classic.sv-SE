---
product: campaign
title: Konfigurera åtkomst till Microsoft SQL Server
description: Lär dig konfigurera åtkomst till Microsoft SQL Server
feature: Installation, Federated Data Access
exl-id: 65ab4577-3126-4579-8fcc-e93772ebd1e8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# Konfigurera åtkomst till Microsoft SQL Server {#configure-fda-sql}



Använd alternativet **FDA (Federated Data Access**) i kampanjen för att bearbeta information som lagras i en extern Microsoft SQL Server-databas. Följ stegen nedan för att konfigurera åtkomst till [!DNL Microsoft SQL Server].

1. Konfigurera [!DNL Microsoft SQL Server] på [CentOS](#sql-centos).
1. Konfigurera [!DNL Microsoft SQL Server] på [Linux](#sql-linux).
1. Konfigurera [!DNL Microsoft SQL Server] på [Windows](#sql-windows).
1. Konfigurera det [!DNL Microsoft SQL Server] [externa kontot](#sql-external) i Campaign

## Microsoft SQL Server on CentOS {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server] är tillgängligt på CentOS 7 och 6.

Följ stegen nedan för att konfigurera [!DNL Microsoft SQL Server] i CentOS:

1. Hämta och installera SQL ODBC-drivrutinen med följande kommando:

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. I Adobe Campaign kan du sedan konfigurera ditt [!DNL Microsoft SQL Server]-externa konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#sql-external).

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

1. I Adobe Campaign kan du sedan konfigurera ditt [!DNL Microsoft SQL Server]-externa konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#sql-external).

## Microsoft SQL Server i Windows {#sql-windows}

Så här konfigurerar du [!DNL Microsoft SQL Server] i Windows:

1. I Windows klickar du på **[!UICONTROL Control Panel]** &#39;>&#39; **[!UICONTROL System and Security]** &#39;>&#39; **[!UICONTROL Administrative Tools]**&#39;>&#39; **[!UICONTROL ODBC Data Sources (64-bit)]**.

1. Klicka på **[!UICONTROL Add...]** i det nya fönstret **[!UICONTROL ODBC Data Sources (64-bit)]**.

1. Kontrollera om SQL Server Native Client v11 visas i fönstret **[!UICONTROL Create New Data Source]**.

1. Om SQL Server Native Client inte finns med i listan kan du hämta den på [den här sidan](https://www.microsoft.com/en-my/download/details.aspx?id=36434).

1. I Adobe Campaign kan du sedan konfigurera ditt [!DNL Microsoft SQL Server]-externa konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#sql-external).

## Externt Microsoft SQL Server-konto {#sql-external}

Du måste skapa ett externt [!DNL Microsoft SQL Server]-konto för att ansluta Campaign-instansen till din [!DNL Microsoft SQL Server]-externa databas.

1. Klicka på **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** i Campaign **[!UICONTROL Explorer]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som det externa kontots **[!UICONTROL Type]**.

1. Under **[!UICONTROL Configuration]** väljer du [!DNL Microsoft SQL Server] i listrutan **[!UICONTROL Type]**.

   ![](assets/sql.png)

1. Konfigurera autentiseringen av det externa kontot **[!UICONTROL Microsoft SQL Server]**:

   * **[!UICONTROL Server]**: URL för servern [!DNL Microsoft SQL Server].

   * **[!UICONTROL Account]**: Användarens namn.

   * **[!UICONTROL Password]**: Lösenord för användarkonto.

   * **[!UICONTROL Database]**: Namn på databasen (valfritt).

   * **[!UICONTROL Timezone]**: Tidszonen har angetts i [!DNL Microsoft SQL Server]. [Läs mer](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. Klicka på fliken **[!UICONTROL Parameters]** och sedan på knappen **[!UICONTROL Deploy functions]** för att skapa funktioner.

   >[!NOTE]
   >
   >För att alla funktioner ska vara tillgängliga måste du skapa Adobe Campaign SQL-funktionerna i fjärrdatabasen. Mer information finns på [sidan](../../configuration/using/adding-additional-sql-functions.md).

1. Klicka på **[!UICONTROL Save]** när konfigurationen är klar.

Kopplingen stöder följande alternativ:

| Alternativ | Beskrivning |
|---|---|
| Autentisering | Typ av autentisering som stöds av kopplingen. Aktuellt värde: ActiveDirectoryMSI. <br> Mer information finns i exempel 8 i [Microsoft-dokumentationen](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings). |
| Kryptera | Anger om anslutningar använder TLS-kryptering över nätverket. Möjliga värden är **yes/mandatory (18.0 och senare)**, **no/optional (18.0 och senare)** och **strict (18.0 och senare)**. Standardvärdet är **yes** i version 18.0 och senare och **no** i tidigare versioner. <br>Mer information finns i [Microsoft-dokumentationen](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt). |
| TrustServerCertificate | Aktiverar kryptering med ett självsignerat servercertifikat när det används med **Kryptera**. <br>Godkända värden: **yes** eller **no** (standardvärde, vilket innebär att servercertifikatet valideras). |
