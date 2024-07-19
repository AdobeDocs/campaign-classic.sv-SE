---
product: campaign
title: Konfigurera åtkomst till SAP HANA
description: Lär dig konfigurera åtkomst till SAP HANA i FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Konfigurera åtkomst till SAP HANA {#configure-access-to-sap-hana}



Använd alternativet [FDA (Federated Data Access](../../installation/using/about-fda.md)) i kampanjen om du vill bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till SAP HANA.

1. Konfigurera [SAP HANA-databasen](#sap-config)
1. Konfigurera det [externa SAP HANA-kontot](#sap-external) i Campaign

## SAP HANA-drivrutiner {#sap-config}

Anslutning till en extern SAP HANA-databas i FDA kräver vissa ytterligare konfigurationer på Adobe Campaign-servern:

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

     &quot;InstallDir&quot; motsvarar platsen för filen **odbcinst.ini**.

   * **/etc/odbcinst.ini**

     ```
     [HDBODBC]
     Description = "SmartCloudPT HANA"
     Driver = /usr/sap/hdbclient/libodbcHDB.so
     ```

1. Ange miljövariablerna för Adobe Campaign-servern:

   * **LD_LIBRARY_PATH**: Den ska innehålla länken till din SAP Hana-klient (/usr/sap/hdbclient/libodbcHDB.so) som standard.
   * **ODBCINI**: plats för filen odbc.ini (till exempel /etc/odbc.ini).

## SAP HANA external account{#sap-external}

Med det externa SAP HANA-kontot kan du ansluta Campaign-instansen till din externa SAP HANA-databas.

1. Klicka på **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** i Campaign **[!UICONTROL Explorer]**.

1. Klicka på **[!UICONTROL New]** och välj **[!UICONTROL External database]** som **[!UICONTROL Type]**.

1. Om du vill konfigurera det externa kontot **[!UICONTROL SAP Hana]** måste du ange:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL för SAP Hana-servern

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto
