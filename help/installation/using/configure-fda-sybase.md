---
title: Konfigurera åtkomst till Sybase IQ
description: Lär dig konfigurera åtkomst till Sybase IQ i FDA
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# Konfigurera åtkomst till Sybase IQ {#configure-access-to-sybase-iq}

Använd alternativet Campaign **Federated Data Access** (FDA) för att bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till Sybase IQ.

1. Konfigurera [Sybase IQ-databas](#configuring-sybase)
1. Konfigurera Sybase IQ [externa konto](#sybase-external) i Campaign

## sybase IQ-konfiguration {#configuring-sybase}

För att ansluta till en extern Sybase IQ-databas i FDA krävs ytterligare konfigurationer nedan på Adobe Campaign-servern.

>[!NOTE]
>
>Innan du startar kontrollerar du att **Unixodbc** -paketet finns på servern.

1. Installera **iq_odbc**. Ett fel kan uppstå i slutet av installationen. Det här felet kan ignoreras.

1. Installera **iq_client_common**. Ett Java-fel kan uppstå när installationen är klar. Det här felet kan ignoreras.

1. Konfigurera ODBC-drivrutinen. Konfigurationen kan utföras i standardfilerna: /etc/odbc.ini för allmänna parametrar och /etc/odbcinst.ini för att deklarera drivrutiner:

   * **/etc/odbc.ini** (ersätt värden som `<server_alias>` tecken med egna):

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. Lägg till sökvägen för det nya biblioteket libodbc16.so i variabeln LD_LIBRARY_PATH. Så här gör du:

   * Om du använder en customer.sh-fil för att deklarera sökvägen: lägg till sökvägen /opt/sybase/IQ-16_0/lib64 för variabeln LD_LIBRARY_PATH.
   * Annars använder du ett Unix-kommando.

## sybase IQ externt konto {#sybase-external}

Med Sybase IQ externa konto kan du ansluta Campaign-instansen till din externa Sybase IQ-databas.

1. Klicka **[!UICONTROL Explorer]** på **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** i Campaign.

1. Click **[!UICONTROL New]** and select **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. Om du vill konfigurera det **[!UICONTROL Sybase IQ]** externa kontot måste du ange:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Motsvarar ODBC-anslutningen (`<server_alias>`) som definieras i steg 5. Inte nödvändigtvis namnet på själva servern.

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namn på databasen

>[!NOTE]
>
>För Windows måste du installera Sybase IQ-klienten på Adobe Campaign-servern och skapa en ODBC-anslutning. Se till att du skapar en systemdatakälla när Adobe Campaign-servern (nlserver) körs som en tjänst i Windows.

