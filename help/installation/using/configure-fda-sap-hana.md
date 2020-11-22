---
solution: Campaign Classic
product: campaign
title: Konfigurera åtkomst till SAP HANA
description: Lär dig konfigurera åtkomst till SAP HANA i FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# Konfigurera åtkomst till SAP HANA {#configure-access-to-sap-hana}

Använd alternativet Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) för att bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till SAP HANA.

1. Konfigurera [SAP HANA-databas](#sap-config)
1. Konfigurera SAP HANA [externa konto](#sap-external) i Campaign

## SAP HANA-drivrutiner {#sap-config}

För att ansluta till en extern SAP HANA-databas i FDA krävs vissa ytterligare konfigurationer på Adobe Campaign-servern:

1. Installera ODBC-drivrutinerna för SAP HANA enligt det operativsystem du använder:

   * **hdb_client_linux.tgz** för Linux. När du har packat upp en fil startar du kommandot hdbinst och följer instruktionerna för att slutföra installationen av drivrutinerna.
   * **hdb_client_windows.zip** för Windows. Zippa upp filen och starta den körbara filen: **hdbinst.exe**. Följ instruktionerna i guiden för att slutföra installationen av drivrutinerna.

1. Konfigurera ODBC-drivrutinen. Konfigurationen kan utföras i standardfilerna: /etc/odbc.ini för allmänna parametrar och /etc/odbcinst.ini för att deklarera drivrutiner.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      &quot;InstallDir&quot; motsvarar platsen för filen **odbcinst.ini** .

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Ange miljövariablerna för Adobe Campaign-servern:

   * **LD_LIBRARY_PATH**: Den bör innehålla länken till SAP Hana-klienten (/usr/sap/hdbclient/libodbcHDB.so) som standard.
   * **ODBCINI**: platsen för filen odbc.ini (till exempel /etc/odbc.ini).

## SAP HANA externt konto{#sap-external}

Med SAP HANA externa konto kan du ansluta Campaign-instansen till din externa SAP HANA-databas.

1. Klicka **[!UICONTROL Explorer]** på **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** i Campaign.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. Om du vill konfigurera det **[!UICONTROL SAP Hana]** externa kontot måste du ange:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL för SAP Hana-servern

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto
