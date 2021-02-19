---
solution: Campaign Classic
product: campaign
title: Konfigurera åtkomst till Sybase IQ
description: Lär dig konfigurera åtkomst till Sybase IQ i FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# Konfigurera åtkomst till Sybase IQ {#configure-access-to-sybase-iq}

Använd alternativet Campaign **FDA (Federated Data Access**) om du vill bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till Sybase IQ.

1. Konfigurera [Sybase IQ-databas](#configuring-sybase)
1. Konfigurera det externa Sybase IQ [kontot](#sybase-external) i Campaign

## sybase IQ configuration {#configuring-sybase}

För att ansluta till en extern Sybase IQ-databas i FDA krävs ytterligare konfigurationer nedan på Adobe Campaign-servern.

>[!NOTE]
>
>Kontrollera att **unixodbc**-paketet finns på servern innan du startar.

1. Installera **iq_odbc**. Ett fel kan uppstå i slutet av installationen. Det här felet kan ignoreras.

1. Installera **iq_client_common**. Ett Java-fel kan uppstå när installationen är klar. Det här felet kan ignoreras.

1. Konfigurera ODBC-drivrutinen. Konfigurationen kan utföras i standardfilerna: /etc/odbc.ini för allmänna parametrar och /etc/odbcinst.ini för att deklarera drivrutiner:

   * **/etc/odbc.ini** (ersätt värden som  `<server_alias>` tecken med egna):

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

1. Klicka på **[!UICONTROL Administration]** **[!UICONTROL Platform]** **[!UICONTROL External accounts]**  i Campaign **[!UICONTROL Explorer]**.

1. Klicka på **[!UICONTROL New]** och välj **[!UICONTROL External database]** som **[!UICONTROL Type]**.

1. Om du vill konfigurera det externa kontot **[!UICONTROL Sybase IQ]** måste du ange:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Motsvarar ODBC-anslutningen (`<server_alias>`) som definieras i steg 5. Inte nödvändigtvis namnet på själva servern.

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namn på databasen

>[!NOTE]
>
>För Windows måste du installera Sybase IQ-klienten på Adobe Campaign-servern och skapa en ODBC-anslutning. Se till att du skapar en systemdatakälla när Adobe Campaign-servern (nlserver) körs som en tjänst i Windows.

