---
solution: Campaign Classic
product: campaign
title: Konfigurera åtkomst till Netezza
description: Lär dig konfigurera åtkomst till Netezza i FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# Konfigurera åtkomst till Netezza {#configure-access-to-netezza}

Använd alternativet Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) för att bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till Netezza.

1. Installera och konfigurera [Netezza-drivrutiner](#netezza-config)
1. Konfigurera Netezza [externa konto](#netezza-external) i Campaign

## Netezza-konfiguration {#netezza-config}

För att ansluta till en extern Netezza-databas i FDA krävs ytterligare konfigurationer nedan på Adobe Campaign-servern:

1. Installera ODBC-drivrutinerna för Netezza enligt det operativsystem du använder:

   * **nz-linuxclient-v7.2.0.0.tar.gz** för Linux. Markera den mapp som motsvarar ditt operativsystem (Linux eller Linux64) och starta uppackningskommandot. Du kan lämna installationen som ska utföras i den databas som föreslås som standard: &quot;/usr/local/nz&quot;.
   * **nz-winclient-v7.2.0.0.zip** för Windows. Zippa upp filen och starta det körbara skript som hör till ditt operativsystem: nzodbcsetup.exe eller nzodbcsetup64.exe. Följ instruktionerna i guiden för att slutföra installationen av drivrutinerna.

1. Konfigurera ODBC-drivrutinen. Konfigurationen kan utföras i standardfilerna: **/etc/odbc.ini** för allmänna parametrar och **/etc/odbcinst.ini** för att deklarera drivrutiner.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot; motsvarar platsen för filen odbcinst.ini.

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. Ange miljövariablerna för Adobe Campaign-servern:

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib och /usr/local/nz/lib64. &quot;/usr/local/nz&quot; motsvarar den installationsdatabas som finns som standard när du installerar drivrutinerna. Här måste du ange vilken databas du har valt för installationen.
   * **ODBCINI**: platsen för filen odbc.ini (till exempel /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: platsen för filen odbc.ini. Netezza kräver också den andra variabeln för att använda filen odbc.ini.

## Netezza externt konto {#netezza-external}

Med Netezza externa konto kan du ansluta Campaign-instansen till din externa Netezza-databas.

1. Klicka **[!UICONTROL Explorer]** på **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** i Campaign.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. Om du vill konfigurera det **[!UICONTROL Netezza]** externa kontot måste du ange:

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**: URL för Netezza-servern

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namn på databasen

>[!NOTE]
>
>Åtgärder för scheman som innehåller automatiskt genererade primärnycklar beaktas inte.
>
>Tabellen använder **Organizer on** -satsen för det första indexvärdet som definieras i schemat. Eftersom den här satsen är begränsad till 1 till 4 kolumner med Netezza, får indexet inte innehålla fler än 4 kolumner.
