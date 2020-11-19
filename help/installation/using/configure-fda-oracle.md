---
title: Konfigurera åtkomst till Oracle
description: Lär dig konfigurera åtkomst till Oracle i FDA
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
source-wordcount: '352'
ht-degree: 0%

---


# Konfigurera åtkomst till Oracle {#configure-access-to-oracle}

Använd alternativet Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) för att bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till Oracle.

1. Konfigurera Oracle i [Linux](#oracle-linux) eller [Windows](#azure-windows)
1. Konfigurera Oracle [externa konto](#oracle-external) i Campaign

## Oracle i Linux {#oracle-linux}

För att ansluta till en extern Oracle-databas i FDA krävs ytterligare konfigurationer nedan på Adobe Campaign-servern.

1. Installera den fullständiga Oracle-klienten som motsvarar din version av Oracle.
1. Lägg till dina TNS-definitioner i installationen. Om du vill göra det anger du dem i en **namnfil.ora** i databasen /etc/oracle. Om den här databasen inte finns skapar du den.

   Skapa sedan en ny TNS_ADMIN-miljövariabel: exportera TNS_ADMIN=/etc/oracle och starta om datorn.

1. Integrera Oracle i Adobe Campaign-servern (nlserver). Det gör du genom att kontrollera att filen **customer.sh** finns i mappen &quot;nl6&quot; i trädstrukturen för Adobe Campaign och att den innehåller länkarna till Oracle-biblioteken.

   Exempel: för en klient i 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Dessa värden (särskilt ORACLE_HOME) beror på installationsdatabaserna. Kontrollera trädstrukturen innan du refererar till dessa värden.

1. Installera de bibliotek som krävs för Oracle:

   * **libclntsh.so**

      ```
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

   * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

1. I Campaign Classic kan du sedan konfigurera ditt [!DNL Oracle] externa konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#oracle-external).

## Oracle i Windows {#oracle-windows}

För att ansluta till en extern Oracle-databas i FDA krävs ytterligare konfigurationer nedan på Adobe Campaign-servern.

1. Installera Oracle-klienten.

1. I mappen C:Oracle skapar du en **DNNAMes.ora** -fil som innehåller din TNS-definition.

1. Lägg till en TNS_ADMIN-miljövariabel med C:Oracle som värde och starta om datorn.

1. I Campaign Classic kan du sedan konfigurera ditt [!DNL Oracle] externa konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#oracle-external).

## Oracle externt konto {#oracle-external}

Med det [!DNL Oracle] externa kontot kan du ansluta Campaign-instansen till din externa Oracle-databas.

1. I Campaign **[!UICONTROL Explorer]** väljer du **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Välj **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som det externa kontots **[!UICONTROL Type]**.

1. Konfigurera det **[!UICONTROL Oracle]** externa kontot måste du ange:

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**: DNS-namn

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Time zone]**: Tidszon för server

   ![](assets/oracle_config.png)

