---
product: campaign
title: Konfigurera åtkomst till Google BigQuery
description: Lär dig konfigurera åtkomst till Google BigQuery i FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 2%

---

# Konfigurera åtkomst till Google BigQuery {#configure-fda-google-big-query}



Använd alternativet Adobe Campaign Classic **FDA (Federated Data Access)** om du vill bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till [!DNL Google BigQuery].

1. Konfigurera [!DNL Google BigQuery] i [Windows](#google-windows) eller [Linux](#google-linux)
1. Konfigurera det [!DNL Google BigQuery] [externa kontot](#google-external) i Adobe Campaign Classic
1. Konfigurera massinläsning av [!DNL Google BigQuery]-anslutning på [Windows](#bulk-load-windows) eller [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery]-anslutningen är tillgänglig för värdbaserade distributioner, hybriddistributioner och lokala distributioner. Mer information finns på [den här sidan](../../installation/using/capability-matrix.md).

![](assets/snowflake_3.png)

## Google BigQuery i Windows {#google-windows}

### Drivrutinen har konfigurerats i Windows {#driver-window}

1. Hämta [ODBC-drivrutinen för Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. Konfigurera ODBC-drivrutinen i Windows. Mer information finns på [den här sidan](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf).

1. Adobe Campaign Classic kräver följande parametrar för att [!DNL Google BigQuery]-anslutningen ska fungera:

   * **[!UICONTROL Project]**: skapa eller använda ett befintligt projekt.

     Mer information finns på [sidan](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Service account]**: skapa ett tjänstkonto.

     Mer information finns på [sidan](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]**: **[!UICONTROL Service account]** kräver en **[!UICONTROL Key File]** för en [!DNL Google BigQuery]-anslutning via ODBC.

     Mer information finns på [sidan](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** är valfritt för en ODBC-anslutning. Eftersom varje fråga måste tillhandahålla datauppsättningen där tabellen finns, är det obligatoriskt att ange **[!UICONTROL Dataset]** för [!DNL Google BigQuery] FDA Connector i Adobe Campaign Classic.

     Mer information finns på [sidan](https://cloud.google.com/bigquery/docs/datasets).

1. I Adobe Campaign Classic kan du sedan konfigurera ditt [!DNL Google BigQuery]-externa konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#google-external).

### Massinläsning har konfigurerats i Windows {#bulk-load-window}

>[!NOTE]
>
>Python måste vara installerat för att Google Cloud SDK ska fungera.
>
>Vi rekommenderar att du använder Python3, se [sidan](https://www.python.org/downloads/).

Med Bulk Load Tool går det snabbare att överföra filer, vilket uppnås med Google Cloud SDK.

1. Hämta 64-bitars Windows-arkivet (x86_64) från den här [sidan](https://cloud.google.com/sdk/docs/downloads-versioned-archives) och extrahera det i motsvarande katalog.

1. Kör skriptet `google-cloud-sdk\install.sh`. Du måste acceptera inställningen för variabeln path.

1. Kontrollera att sökvägsvariabeln `...\google-cloud-sdk\bin` har angetts efter installationen. Om inte, lägg till det manuellt.

1. I filen `..\google-cloud-sdk\bin\bq.cmd` lägger du till den lokala variabeln `CLOUDSDK_PYTHON` som dirigerar om till platsen för Python-installationen.

   Exempel:

   ![](assets/google-big-query_1.png)

1. Starta om Adobe Campaign Classic för att ta hänsyn till ändringarna.

## Google BigQuery i Linux {#google-linux}

### Drivrutinen har konfigurerats i Linux {#driver-linux}

Observera att skript och kommandon måste köras av rotanvändaren innan du konfigurerar drivrutinen. Vi rekommenderar även att du använder Google DNS 8.8.8.8 när du kör skriptet.

Så här konfigurerar du [!DNL Google BigQuery] i Linux:

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

1. Uppdatera systemet före installation:

   * För Red Hat/CentOS:

     ```
     # install unixODBC driver manager
     yum install -y unixODBC
     ```

   * Debian:

     ```
     # install unixODBC driver manager
     apt-get install -y odbcinst1debian2 libodbc1 odbcinst unixodbc
     ```

1. Innan du kör skriptet kan du få mer information genom att ange —help-argumentet:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh --help
   ```

1. Gå till katalogen där skriptet finns och kör följande skript som rotanvändare:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh
   ```

### Massinläsning konfigurerad för Linux {#bulk-load-linux}

>[!NOTE]
>
>Python måste vara installerat för att Google Cloud SDK ska fungera.
>
>Vi rekommenderar att du använder Python3, se [sidan](https://www.python.org/downloads/).

Med Bulk Load Tool går det snabbare att överföra filer, vilket uppnås med Google Cloud SDK.

1. Kontrollera att följande paket är installerade på din Linux-distribution före ODBC-installationen:

   * För Red Hat/CentOS:

     ```
     yum update
     yum upgrade
     yum install -y python3
     ```

   * Debian:

     ```
     apt-get update
     apt-get upgrade
     apt-get install -y python3
     ```

1. Gå till katalogen där skriptet finns och kör följande skript:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_sdk-setup.sh
   ```

## Externt Google BigQuery-konto {#google-external}

Du måste skapa ett externt [!DNL Google BigQuery]-konto för att ansluta din Adobe Campaign Classic-instans till din [!DNL Google BigQuery]-externa databas.

1. I Adobe Campaign Classic **[!UICONTROL Explorer]** klickar du på **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som det externa kontots **[!UICONTROL Type]**.

1. Konfigurera det externa [!DNL Google BigQuery]-kontot måste du ange:

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**: E-postadress till din **[!UICONTROL Service account]**. Mer information finns i [Google Cloud-dokumentationen](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Project]**: Namn på **[!UICONTROL Project]**. Mer information finns i [Google Cloud-dokumentationen](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**: välj **[!UICONTROL Click here to upload]** om du väljer att överföra nyckeln via Adobe Campaign Classic.

      * **[!UICONTROL Enter manually the key file path]**: kopiera/klistra in den absoluta sökvägen i det här fältet om du väljer att använda en befintlig nyckel.

   * **[!UICONTROL Dataset]**: Namn på **[!UICONTROL Dataset]**. Mer information finns i [Google Cloud-dokumentationen](https://cloud.google.com/bigquery/docs/datasets-intro).

   ![](assets/google-big-query.png)

Kopplingen stöder följande alternativ:

| Alternativ | Beskrivning |
|:-:|:-:|
| ProxyType | Typ av proxy som används för att ansluta till BigQuery via ODBC- och SDK-anslutningar. </br>HTTP (standard), http_no_tunnel, sockor4 och sockor5 stöds för närvarande. |
| ProxyHost | Värdnamn eller IP-adress dit proxyn kan nås. |
| ProxyPort | Portnummer som proxyn körs på, till exempel 8080 |
| ProxyUid | Användarnamn som används för autentiserad proxy |
| ProxyPwd | ProxyUid-lösenord |
| bqpath | Observera att detta endast gäller för massinläsningsverktyg (Cloud SDK). </br> Om du vill undvika att använda variabeln PATH eller om katalogen google-cloud-sdk måste flyttas till en annan plats, kan du med det här alternativet ange den exakta sökvägen till bin-katalogen i molnet på servern. |
| GCloudConfigName | Observera att detta gäller från och med version 7.3.4 och endast för massinläsningsverktyg (Cloud SDK).</br> Google Cloud SDK använder konfigurationer för att läsa in data i BigQuery-tabeller. Konfigurationen med namnet `accfda` lagrar parametrarna för att läsa in data. Med det här alternativet kan användare ange ett annat namn för konfigurationen. |
| GCloudDefaultConfigName | Observera att detta gäller från och med version 7.3.4 och endast för massinläsningsverktyg (Cloud SDK).</br> Den aktiva Google Cloud SDK-konfigurationen kan inte tas bort utan att den aktiva taggen först överförs till en ny konfiguration. Den här tillfälliga konfigurationen är nödvändig för att återskapa huvudkonfigurationen för inläsning av data. Standardnamnet för den tillfälliga konfigurationen är `default`, vilket kan ändras vid behov. |
| GCloudRecreateConfig | Observera att detta gäller från och med version 7.3.4 och endast för massinläsningsverktyg (Cloud SDK).</br> När värdet är `false` avstår massinläsningsfunktionen från att försöka återskapa, ta bort eller ändra Google Cloud SDK-konfigurationerna. I stället fortsätter programmet med datainläsning med den befintliga konfigurationen på datorn. Den här funktionen är värdefull när andra åtgärder är beroende av Google Cloud SDK-konfigurationer. </br> Om användaren aktiverar det här motoralternativet utan rätt konfiguration kommer massinläsningsmekanismen att skicka ett varningsmeddelande: `No active configuration found. Please either create it manually or remove the GCloudRecreateConfig option`. Om du vill förhindra fler fel återgår den till att använda ODBC-standardmetoden för gruppinläsning av ODBC-matris. |

