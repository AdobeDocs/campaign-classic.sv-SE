---
product: campaign
title: Konfigurera åtkomst till Sybase IQ
description: Lär dig konfigurera åtkomst till Sybase IQ i FDA
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0fdf8259-5cab-4a9d-adb3-6c55ec5c8851
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Konfigurera åtkomst till Sybase IQ {#configure-access-to-sybase-iq}



Använd kampanj **Åtkomst till federerade data** (FDA) om du vill bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till Sybase IQ.

1. Konfigurera [Sybase IQ-databas](#configuring-sybase)
1. Konfigurera Sybase IQ [externt konto](#sybase-external) i Campaign

## Sybase IQ konfiguration {#configuring-sybase}

För att ansluta till en extern Sybase IQ i FDA krävs ytterligare konfigurationer nedan på Adobe Campaign-servern.

>[!NOTE]
>
>Innan du börjar bör du kontrollera att **unixodbc** paketet finns på servern.

1. Installera **iq_odbc**. Ett fel kan uppstå i slutet av installationen. Det här felet kan ignoreras.

1. Installera **iq_client_common**. Ett Java-fel kan uppstå när installationen är klar. Det här felet kan ignoreras.

1. Konfigurera ODBC-drivrutinen. Konfigurationen kan utföras i standardfilerna: /etc/odbc.ini för allmänna parametrar och /etc/odbcinst.ini för att deklarera drivrutiner:

   * **/etc/odbc.ini** (ersätt värden som `<server_alias>` egna tecken):

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

## Sybase IQ externa konto {#sybase-external}

Med det externa Sybase IQ kan du ansluta Campaign-instansen till din externa Sybase IQ.

1. Från kampanj **[!UICONTROL Explorer]**, klicka **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klicka **[!UICONTROL New]** och markera **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. Konfigurera **[!UICONTROL Sybase IQ]** externt konto måste du ange:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Motsvarar ODBC-anslutningen (`<server_alias>`) som definieras i steg 5. Inte nödvändigtvis namnet på själva servern.

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namn på databasen

>[!NOTE]
>
>För Windows måste du installera Sybase IQ-klienten på Adobe Campaign-servern och skapa en ODBC-anslutning. Se till att du skapar en systemdatakälla när Adobe Campaign-servern (nlserver) körs som en tjänst i Windows.
