---
product: campaign
title: Konfigurera åtkomst till Amazon Redshift
description: Lär dig konfigurera åtkomst till Amazon Redshift i FDA
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
source-git-commit: 6939307c0b33ff662fe4ef9ae0192ae7b500a95c
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 4%

---

# Konfigurera åtkomst till Amazon Redshift {#configure-access-to-redshift}

Använd kampanj **Åtkomst till federerade data** (FDA) om du vill bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till Amazon Redshift.

1. Konfigurera [Amazon Redshift-databas](#configuring-redshift)
1. Konfigurera Amazon Redshift [externt konto](#redshift-external) i Campaign

## Amazon Redshift i Linux {#redshift-linux}

Konfigurera [!DNL Amazon Redshift] i Linux följer du stegen nedan:

1. Kontrollera att följande paket är installerade på din Linux-distribution före ODBC-installationen:

   * För Red Hat/CentOS:

     ```
      yum update
      yum upgrade
      yum install -y grep sed tar wget perl curl
     ```

   * Debian:

     ```
      apt-get update
      apt-get upgrade
      apt-get install -y grep sed tar wget perl curl
     ```

1. Innan du kör skriptet har du tillgång till mer information med `--help` alternativ:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./redshift_odbc-setup.sh --help
   ```

1. Gå till katalogen där skriptet finns och kör följande skript som rotanvändare:

   ```
     cd /usr/local/neolane/nl6/bin/fda-setup-scripts
     ./redshift_odbc-setup.sh
   ```

1. När du har installerat ODBC-drivrutinerna måste du starta om Campaign Classicen. Om du vill göra det kör du följande kommando:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. I Campaign kan du sedan konfigurera [!DNL Amazon Redshift] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#redshift-external).

## Externt Amazon Redshift-konto {#redshift-external}

The [!DNL Amazon Redshift] Med ett externt konto kan du ansluta Campaign-instansen till din externa Amazon Redshift-databas.

1. I Campaign Classic konfigurerar du [!DNL Amazon Redshift] externt konto. Från **[!UICONTROL Explorer]**, klicka **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som ditt externa konto **[!UICONTROL Type]**.

1. Konfigurera **[!UICONTROL Amazon Redshift]** externt konto måste du ange:

   * **[!UICONTROL Type]**: Amazon Redshift

   * **[!UICONTROL Server]**: Namn på DNS

   * **[!UICONTROL Account]**: Användarens namn

   * **[!UICONTROL Password]**: Lösenord för användarkonto

   * **[!UICONTROL Database]**: Namnet på databasen om det inte anges i DSN. Den kan lämnas tom om den anges i DSN

   * **[!UICONTROL Working schema]**: Namnet på ditt arbetsschema. [Läs mer](https://docs.aws.amazon.com/redshift/latest/dg/r_Schemas_and_tables.html)

   * **[!UICONTROL Time zone]**: Servertidszon

   ![](assets/amazon_redshift.png)

1. Klicka på **[!UICONTROL Save]**.
