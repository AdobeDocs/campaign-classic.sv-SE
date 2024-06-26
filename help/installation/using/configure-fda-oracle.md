---
product: campaign
title: Konfigurera åtkomst till Oraclet
description: Lär dig hur du konfigurerar åtkomst till Oraclet i FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 320bfbb4-533b-4c45-a46f-c3c8dd68221f
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Konfigurera åtkomst till Oraclet {#configure-access-to-oracle}



Använd kampanj [Åtkomst till federerade data](../../installation/using/about-fda.md) (FDA) om du vill bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till Oraclet.

1. Konfigurera Oracle på [Linux](#oracle-linux) eller [Windows](#azure-windows)
1. Konfigurera Oraclet [externt konto](#oracle-external) i Campaign

## Oracle i Linux {#oracle-linux}

Om du vill ansluta till en extern databas i FDA för ett Oracle krävs ytterligare konfigurationer nedan på Adobe Campaign-servern.

1. Installera Oraclets fullständiga klient som motsvarar din version av Oraclet.
1. Lägg till dina TNS-definitioner i installationen. Om du vill göra det anger du dem i **namn.ora** i databasen /etc/oracle. Om den här databasen inte finns skapar du den.

   Skapa sedan en ny TNS_ADMIN-miljövariabel: exportera TNS_ADMIN=/etc/oracle och starta om datorn.

1. Integrera Oracle med Adobe Campaign-servern (nlserver). Om du vill göra det kontrollerar du att **customer.sh** filen finns i mappen &quot;nl6&quot; i Adobe Campaign serverträdstruktur och att den innehåller länkar till Oraclena bibliotek.

   För en klient i 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Dessa värden (särskilt ORACLE_HOME) beror på installationsdatabaserna. Kontrollera trädstrukturen innan du refererar till dessa värden.

1. Installera de bibliotek som behövs för Oraclet:

   * **libclntsh.so**

     ```
     cd /usr/lib/oracle/<version>/client<architecture>/lib
     ln -s libclntsh.so.<version> libclntsh.so
     ```

   * **libaio1**

     ```
     apt install libaio1
     or
     yum install libaio1
     ```

1. I Campaign Classicen kan du sedan konfigurera [!DNL Oracle] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#oracle-external).

## Oracle i Windows {#oracle-windows}

Om du vill ansluta till en extern databas i FDA för ett Oracle krävs ytterligare konfigurationer nedan på Adobe Campaign-servern.

1. Installera Oraclet client.

1. Skapa en **namn.ora** som innehåller din TNS-definition.

1. Lägg till en TNS_ADMIN-miljövariabel med C:Oracle som värde och starta om datorn.

1. I Campaign Classicen kan du sedan konfigurera [!DNL Oracle] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#oracle-external).

## Oraclets externa konto {#oracle-external}

The [!DNL Oracle] Med ett externt konto kan du ansluta Campaign-instansen till Oraclets externa databas.

1. Från kampanj **[!UICONTROL Explorer]**, markera **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Välj **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som ditt externa konto **[!UICONTROL Type]**.

1. Konfigurera **[!UICONTROL Oracle]** externt konto måste du ange:

   * **[!UICONTROL Type]**: ORACLE

   * **[!UICONTROL Server]**: Namn på DNS

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Time zone]**: Servertidszon

   ![](assets/oracle_config.png)
