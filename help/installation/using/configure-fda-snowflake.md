---
solution: Campaign Classic
product: campaign
title: Konfigurera åtkomst till Snowflake
description: Lär dig hur du konfigurerar åtkomst till Snowflake i FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 10%

---


# Konfigurera åtkomst till Snowflake {#configure-access-to-snowflake}

Använd alternativet Campaign **Federated Data Access** (FDA) för att bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till [!DNL Snowflake].

1. Konfigurera [!DNL Snowflake] i [CentOS](#snowflake-centos), [Windows](#snowflake-windows) eller [Debian](#snowflake-debian)
1. Konfigurera det [!DNL Snowflake][externa kontot](#snowflake-external) i Campaign


>[!NOTE]
>
>[!DNL Snowflake] anslutning finns för värdbaserade och lokala distributioner. Se denna [sida](../../installation/using/capability-matrix.md) för mer information om detta.

![](assets/snowflake_3.png)

## Snowflake på CentOS {#snowflake-centos}

Så här konfigurerar du [!DNL Snowflake] i CentOS:

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

1. I Campaign kan du sedan konfigurera ditt [!DNL Snowflake] externa konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#snowflake-external).

## Snowflake i Windows {#snowflake-windows}

1. Hämta [ODBC-drivrutinen för Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html). Observera att du behöver administratörsbehörighet för att installera drivrutinen. Se denna [sida](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html) för mer information om detta

1. Konfigurera ODBC-drivrutinen. Se denna [sida](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver) för mer information om detta

1. I Campaign kan du sedan konfigurera ditt [!DNL Snowflake] externa konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#snowflake-external).

## Snowflake på Debian {#snowflake-debian}

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

1. I Campaign kan du sedan konfigurera ditt [!DNL Snowflake] externa konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#snowflake-external).

## Snowflake external account {#snowflake-external}

Du måste skapa ett [!DNL Snowflake] externt konto för att ansluta Campaign-instansen till din [!DNL Snowflake] externa databas.

1. Klicka **[!UICONTROL Explorer]** på **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** i Campaign.

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
| TimeZoneName | Som standard är den tom, vilket innebär att systemtidszonen för programservern i Campaign Classic används. Alternativet kan användas för att framtvinga TIMEZONE-sessionsparametern. <br>Se denna [sida](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone) för mer information om detta. |
| WeekStart | WEEK_START-sessionsparameter. Standardinställningen är 0. <br>Se denna [sida](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start) för mer information om detta. |
| AnvändCachedResult | USE_CACHED_RESULTS sessionsparameter. Standardinställningen är TRUE. Det här alternativet kan användas för att inaktivera cachelagrade resultat i Snowflake. <br>Se denna [sida](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html) för mer information om detta. |
