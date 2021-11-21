---
product: campaign
title: Konfigurera åtkomst till SAP HANA
description: Lär dig hur du konfigurerar åtkomst till SAP HANA i FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Konfigurera åtkomst till SAP HANA {#configure-access-to-sap-hana}

![](../../assets/v7-only.svg)

Använd kampanj [Åtkomst till federerade data](../../installation/using/about-fda.md) (FDA) om du vill bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till SAP HANA.

1. Konfigurera [SAP HANA-databas](#sap-config)
1. Konfigurera SAP HANA [externt konto](#sap-external) i Campaign

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

      &quot;InstallDir&quot; motsvarar platsen för **odbcinst.ini** -fil.

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Ange miljövariablerna för Adobe Campaign-servern:

   * **LD_LIBRARY_PATH**: Den bör innehålla länken till SAP Hana-klienten (/usr/sap/hdbclient/libodbcHDB.so) som standard.
   * **ODBCINI**: platsen för filen odbc.ini (till exempel /etc/odbc.ini).

## SAP HANA external account{#sap-external}

Med det externa SAP HANA-kontot kan du ansluta Campaign-instansen till din externa SAP HANA-databas.

1. Från kampanj **[!UICONTROL Explorer]**, klicka **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klicka **[!UICONTROL New]** och markera **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. Så här konfigurerar du **[!UICONTROL SAP Hana]** externt konto måste du ange:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL för SAP Hana-servern

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto
