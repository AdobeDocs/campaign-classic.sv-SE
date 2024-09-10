---
product: campaign
title: Externa konton
description: Lär dig hur du skapar externa konton
feature: Installation, Application Settings, External Account
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 4a17d5e8-c73f-42e7-b641-0fee6a52c5c0
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1757'
ht-degree: 7%

---

# Externa konton{#external-accounts}

Adobe Campaign innehåller en uppsättning fördefinierade externa konton. Om du vill konfigurera anslutningar med externa system kan du skapa nya externa konton.

Externa konton används av tekniska processer som tekniska arbetsflöden eller Campaign-arbetsflöden. Om du till exempel konfigurerar en filöverföring i ett arbetsflöde eller ett datautbyte med något annat program (Adobe Target, Experience Manager, osv.) måste du välja ett externt konto.

## Skapa ett externt konto {#creating-an-external-account}

Följ stegen nedan om du vill skapa ett nytt externt konto. Detaljerade inställningar beror på typen av externt konto.

1. Välj **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** från kampanj **[!UICONTROL Explorer]**.

   ![](assets/ext_account_1.png)

1. Klicka på knappen **[!UICONTROL New]**.

   ![](assets/ext_account_2.png)

1. Ange en **[!UICONTROL Label]** och en **[!UICONTROL Internal Name]**.
1. Välj det externa kontot **[!UICONTROL Type]** som du vill skapa.
1. Konfigurera åtkomsten till kontot genom att ange autentiseringsuppgifter beroende på vald extern kontotyp.

   Den nödvändiga informationen tillhandahålls vanligtvis av leverantören för den server som du ansluter till.

1. Markera alternativet **[!UICONTROL Enabled]** om du vill aktivera anslutningen.
1. Klicka på **[!UICONTROL Save]**.

Det externa kontot skapas och läggs till i listan över externa konton.

## Kampanjspecifika externa konton

### Studsa e-post {#bounce-mails-external-account}

Det externa **studs-e-postkontot** anger det externa POP3-kontot som ska användas för att ansluta till e-posttjänsten. Mer information om det här externa kontot finns på [sidan](../../workflow/using/inbound-emails.md).

Alla servrar som konfigurerats för POP3-åtkomst kan användas för att ta emot returmeddelanden.

![](assets/ext_account_6.png)

Så här konfigurerar du det externa kontot **[!UICONTROL Bounce mails (defaultPopAccount)]**:

* **[!UICONTROL Server]**

  URL för POP3-servern.

* **[!UICONTROL Port]**

  Portnummer för POP3-anslutning. Standardporten är 10.

* **[!UICONTROL Account]**

  Användarens namn.

* **[!UICONTROL Password]**

  Lösenord för användarkonto.

* **[!UICONTROL Encryption]**

  Typ av vald kryptering mellan **[!UICONTROL By default]**, **[!UICONTROL POP3 + STARTTLS]**, **[!UICONTROL POP3]** eller **[!UICONTROL POP3S]**.

* **[!UICONTROL Function]**

  Inkommande e-post eller SOAP

>[!IMPORTANT]
>
>Innan du konfigurerar ditt POP3-externa konto med Microsoft OAuth 2.0 måste du först registrera programmet i Azure-portalen. Mer information finns på [den här sidan](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app).

Om du vill konfigurera en extern POP3 med **Microsoft OAuth 2.0** markerar du alternativet **[!UICONTROL Microsoft OAuth 2.0]** och fyller i följande fält:

* **[!UICONTROL Azure tenant]**

  Azure ID (eller katalog (klientorganisations-ID) finns i listrutan **Grundläggande** i programöversikten i Azure-portalen.

* **[!UICONTROL Azure Client ID]**

  Klient-ID (eller program-ID (klient)) finns i listrutan **Grundläggande** i programöversikten i Azure-portalen.

* **[!UICONTROL Azure Client secret]**

  Klienthemligt ID finns i kolumnen **Klienthemligheter** på menyn **Certifikat och hemligheter** i ditt program på Azure-portalen.

* **[!UICONTROL Azure Redirect URL]**

  Omdirigerings-URL:en finns på menyn **Autentisering** för ditt program i Azure-portalen. Den ska sluta med följande syntax `nl/jsp/oauth.jsp`, t.ex. `https://redirect.adobe.net/nl/jsp/oauth.jsp`.

När du har angett dina olika autentiseringsuppgifter kan du klicka på **[!UICONTROL Setup the connection]** för att slutföra konfigurationen av det externa kontot.

### Routning{#routing-external-account}

Med det externa kontot **[!UICONTROL Routing]** kan du konfigurera varje kanal som är tillgänglig i Adobe Campaign beroende på vilka paket som är installerade.

![](assets/ext_account_7.png)

Följande kanaler kan konfigureras:

* [E-post](#email-routing-external-account)
* [Mobil (SMS)](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)
* [Telefon](../../delivery/using/communication-channels.md#other-channels)
* [Direktmeddelande](../../delivery/using/about-direct-mail-channel.md)
* [Byrå](../../delivery/using/communication-channels.md#other-channels)
* [X (tidigare Twitter)](../../social/using/about-social-marketing.md)
* [iOS](../../delivery/using/configuring-the-mobile-application.md)
* [Android](../../delivery/using/configuring-the-mobile-application-android.md)

### E-postroutning {#email-routing-external-account}

Det externa kontot för e-postroutning tillhandahålls som standard, anpassat efter din konfiguration.

Som en lokal/blandad kund kan du skapa nya externa routningskonton eller uppdatera parametrar enligt beskrivningen nedan. Den här konfigurationen är reserverad för expertanvändare och kan påverka leveransmöjligheterna. Kontakta Adobe kundtjänst eller er Adobe-representant om du har några frågor.

* Du kan använda en **MID-sourcing**, **Extern**-routning eller en **massutskick**.

* För leveranslägena **Gruppera** och **Mid-sourcing** kan du ange varumärkesparametrar på fliken **Varumärke**. De här parametrarna används för att åsidosätta [standardparametrarna](../../installation/using/deploying-an-instance.md#email-channel-parameters) för **URL:en för speglingssidan** och **feladressen** med inställningar som är specifika för ditt varumärke.

  ![](assets/ext-account-branding.png)

* Mer information om hur du konfigurerar ett externt konto med mellanleverantörer finns i [det här avsnittet](mid-sourcing-server.md)

### Körningsinstans  {#execution-instance-external-account}

Om du har en uppdelad arkitektur måste du ange de körningsinstanser som är länkade till kontrollinstansen och ansluta dem. Transaktionsmeddelandemallar distribueras till körningsinstansen.

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

  URL för servern där körningsinstansen är installerad.

* **[!UICONTROL Account]**

  Namnet på kontot måste matcha Message Center Agent enligt operatormappen.

* **[!UICONTROL Password]**

  Lösenord för kontot enligt definitionen i mappen operator.

Mer information om den här konfigurationen finns på [sidan](../../message-center/using/configuring-instances.md#control-instance).

## Tillgång till externa systemkonton

### FTP {#ftp-external-account}

Med det externa FTP-kontot kan du konfigurera och testa åtkomst till en server utanför Adobe Campaign. Om du vill konfigurera anslutningar med externa system, t.ex. FTP-servrar 898 som används för filöverföringar, kan du skapa egna externa konton. Se denna [sida](../../workflow/using/file-transfer.md) för mer information om detta.

Om du vill göra det anger du den adress och de autentiseringsuppgifter som ska användas för att upprätta anslutningen till FTP-servern i det här externa kontot

![](assets/ext_account_8.png)

* **[!UICONTROL Server]**

  FTP-serverns namn.

* **[!UICONTROL Port]**

  Portnummer för FTP-anslutning. Standardporten är 21.

* **[!UICONTROL Account]**

  Användarens namn.

* **[!UICONTROL Password]**

  Lösenord för användarkonto.

* **[!UICONTROL Encryption]**

  Typ av vald kryptering mellan **[!UICONTROL None]** eller **[!UICONTROL SSL]**.

Om du vill veta var du hittar de här autentiseringsuppgifterna kan du gå till [sidan](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials).

### SFTP {#sftp-external-account}

Med det externa SFTP-kontot kan du konfigurera och testa åtkomst till en server utanför Adobe Campaign. Om du vill konfigurera anslutningar till externa system, t.ex. SFTP, som används för filöverföringar, kan du skapa egna externa konton. Se denna [sida](../../workflow/using/file-transfer.md) för mer information om detta.

![](assets/ext_account_4.png)

* **[!UICONTROL Server]**

  URL för SFTP-servern.

* **[!UICONTROL Port]**

  Portnummer för FTP-anslutning. Standardporten är 22.

* **[!UICONTROL Account]**

  Kontonamn som används för att ansluta till SFTP-servern.

* **[!UICONTROL Password]**

  Lösenord som används för att ansluta till SFTP-servern.

<!--To add SSH keys on Windows:

1. Create the **HOME** environment variable with value set as the installation directory.

2. Add your private key to the `/$HOME/.ssh/id_rsa` folder.

3. Restart the Adobe Campaign services.
-->

### Extern databas (FDA) {#external-database-external-account}

Använd det externa kontot av typen **Extern databas** för att ansluta till en extern databas. Läs mer om FDA-alternativet (Federated Data Access) i [det här avsnittet](../../installation/using/about-fda.md).

Externa databaser som är kompatibla med Campaign listas i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md)

![](assets/ext_account_11.png)

Konfigurationsinställningarna för det externa kontot beror på databasmotorn. Läs mer i följande avsnitt:

* Konfigurera åtkomst till [Vertica analytics](../../installation/using/configure-fda-vertica.md)
* Konfigurera åtkomst till [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Konfigurera åtkomst till [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)
* Konfigurera åtkomst till [Azure synapse](../../installation/using/configure-fda-synapse.md)
* Konfigurera åtkomst till [Hadoopet](../../installation/using/configure-fda-hadoop.md)
* Konfigurera åtkomst till [Oraclet](../../installation/using/configure-fda-oracle.md)
* Konfigurera åtkomst till [Netezza](../../installation/using/configure-fda-netezza.md)
* Konfigurera åtkomst till [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* Konfigurera åtkomst till [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Konfigurera åtkomst till [Sybase IQ](../../installation/using/configure-fda-sybase.md)
* Konfigurera åtkomst till [Teradata](../../installation/using/configure-fda-teradata.md)


## Externa konton för integrering av lösningar i Adobe

### Adobe Experience Cloud {#adobe-experience-cloud-external-account}

Om du vill ansluta till Adobe Campaign-konsolen med en Adobe ID måste du konfigurera det externa kontot **[!UICONTROL Adobe Experience Cloud (MAC)]**.

![](assets/ext_account_9.png)

* **[!UICONTROL IMS server]**

  URL för IMS-servern. Se till att både fas- och produktionsinstanser pekar på samma IMS-produktionsslutpunkt.

* **[!UICONTROL IMS scope]**

  Omfattningar som definieras här måste vara en delmängd av de som tillhandahålls av IMS.

* **[!UICONTROL IMS client identifier]**

  ID för IMS-klienten.

* **[!UICONTROL IMS client secret]**

  Autentiseringsuppgifter för din IMS-klienthemlighet.

* **[!UICONTROL Callback server]**

  Åtkomst-URL för din Adobe Campaign-instans.

* **[!UICONTROL IMS organization ID]**

  ID för din organisation. Information om hur du hittar ditt organisations-ID finns på [den här sidan](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=sv){_blank}.

* **[!UICONTROL Association mask]**

  Syntax som gör att konfigurationsnamn i Enterprise Dashboard kan synkroniseras med grupper i Adobe Campaign.

* **[!UICONTROL Server]**

  URL för din Adobe Experience Cloud-instans.

* **[!UICONTROL Tenant]**

  Namn på din Adobe Experience Cloud-klient.

Mer information om den här konfigurationen finns på [den här sidan](../../integrations/using/configuring-ims.md).

## Web Analytics {#web-analytics-external-account}

Med det externa kontot **[!UICONTROL Web Analytics]** kan du vidarebefordra data från Adobe Analytics till Adobe Campaign i form av segment. Omvänt skickas indikatorer och attribut för e-postkampanjer som levereras av Adobe Campaign till Adobe Analytics Connector.

![](assets/ext_account_10.png)

För det här externa kontot måste beräkningsformeln för spårade URL:er förbättras och anslutningen mellan de två lösningarna måste godkännas. Se denna [sida](../../integrations/using/gs-aa.md) för mer information om detta.

### Adobe Experience Manager {#adobe-experience-manager-external-account}

Med det externa kontot **[!UICONTROL AEM (AEM instance)]** kan du hantera innehållet i e-postleveranser och dina formulär direkt i Adobe Experience Manager.

![](assets/ext_account_5.png)

* **[!UICONTROL Server]**

  URL för Adobe Experience Manager-servern.

* **[!UICONTROL Port]**

  Kontonamn som används för att ansluta till Adobe Experience Manager-redigeringsinstansen.

* **[!UICONTROL Password]**

  Lösenord som används för att ansluta till Adobe Experience Manager-redigeringsinstansen.

Mer information om detta hittar du i det här [avsnittet](../../integrations/using/about-adobe-experience-manager.md).

## Externa konton för CRM Connector

### MICROSOFT DYNAMICS CRM {#microsoft-dynamics-crm-external-account}

>[!NOTE]
>
> Distributionstyperna **[!UICONTROL On-premise]** och **[!UICONTROL Office 365]** är nu inaktuella. [Läs mer](../../rn/using/deprecated-features.md).

Med det externa kontot **[!UICONTROL Microsoft Dynamics CRM]** kan du importera och exportera Microsoft Dynamics-data till Adobe Campaign.

Läs mer om Campaign - Microsoft Dynamics CRM Connector på den här [sidan](../../platform/using/crm-ms-dynamics.md).

Med distributionstypen **[!UICONTROL Web API]** och autentiseringen **[!UICONTROL Password credentials]** måste du ange följande information:

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

  Det konto som används för att logga in på Microsoft CRM.

* **[!UICONTROL Server]**

  URL till din Microsoft CRM-server.

  Om du vill hitta din Microsoft CRM **[!UICONTROL Server URL]** öppnar du ditt Microsoft Dynamics CRM-konto, klickar på **Dynamics 365** och väljer din app. Du kan sedan hitta din **[!UICONTROL Server URL]** i webbläsarens adressfält, t.ex. `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Client identifier]**

  Klient-ID som kan hittas från Microsoft Azure-hanteringsportalen i fältet **[!UICONTROL Update your code]**, **[!UICONTROL Client ID]**.

* **[!UICONTROL CRM version]**

  Välj CRM-version **[!UICONTROL Dynamics CRM 365]**.

Med distributionstypen **[!UICONTROL Web API]** och autentiseringen **[!UICONTROL Certificate]** måste du ange följande information:

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

  URL till din Microsoft CRM-server.

  Om du vill hitta din Microsoft CRM **[!UICONTROL Server URL]** öppnar du ditt Microsoft Dynamics CRM-konto, klickar på **Dynamics 365** och väljer din app. Du kan sedan hitta din **[!UICONTROL Server URL]** i webbläsarens adressfält, t.ex. `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Private Key (Base64 encoded)]**

  Observera att den privata nyckeln måste kodas till Base64.

  Det gör du genom att använda en Base64-kodare eller kommandoraden `base64 -w0 private.key` för Linux.

* **[!UICONTROL Custom Key identifier]**

* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

  Klient-ID som kan hittas från Microsoft Azure-hanteringsportalen i fältet **[!UICONTROL Update your code]**, **[!UICONTROL Client ID]**.

* **[!UICONTROL CRM version]**

  CRM-version mellan **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** eller **[!UICONTROL Dynamics CRM 2016]**.

Mer information om den här konfigurationen finns på [sidan](../../platform/using/crm-connectors.md).

### Salesforce.com CRM  {#salesforce-crm-external-account}

Med det externa kontot **[!UICONTROL Salesforce CRM]** kan du importera och exportera Salesforce-data till Adobe Campaign.

![](assets/ext_account_17.png)

Om du vill konfigurera det externa Salesforce CRM-kontot så att det fungerar med Adobe Campaign måste du ange följande information:

* **[!UICONTROL Account]**

  Det konto som används för att logga in på Salesforce CRM.

* **[!UICONTROL Password]**

  Lösenord som används för att logga in på Salesforce CRM.

* **[!UICONTROL Client identifier]**

  Om du vill veta var du kan hitta din klient-ID kan du läsa den här [sidan](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL Security token]**

  Om du vill veta var du kan hitta din säkerhetstoken kan du gå till [sidan](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL API version]**

  Välj version av API:t.

För det här externa kontot måste du konfigurera Salesforce CRM med konfigurationsassistenten.

Mer information om den här konfigurationen finns på [sidan](../../platform/using/crm-connectors.md).

## Externa konton för dataöverföring

### Amazon Simple Storage Service (S3) {#amazon-simple-storage-service--s3--external-account}

Kopplingen Amazon Simple Storage Service (S3) kan användas för att importera eller exportera data till Adobe Campaign. Den kan ställas in i en arbetsflödesaktivitet. Se denna [sida](../../workflow/using/file-transfer.md) för mer information om detta.

![](assets/ext_account_3.png)

När du konfigurerar det nya externa kontot måste du ange följande information:

* **[!UICONTROL AWS S3 Account Server]**

  URL-adressen till servern ska fyllas i enligt följande:

  ```
  <S3bucket name>.s3.amazonaws.com/<s3object path>
  ```

* **[!UICONTROL AWS access key ID]**

  Information om var du hittar ditt ID för AWS-åtkomstnyckel finns på [sidan](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

* **[!UICONTROL Secret access key to AWS]**

  Om du vill veta var du hittar din hemliga åtkomstnyckel till AWS kan du läsa den här [sidan](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

* **[!UICONTROL AWS Region]**

  Mer information om AWS finns på [sidan](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

* Med kryssrutan **[!UICONTROL Use server side encryption]** kan du lagra filen i S3-krypterat läge.

Mer information om var du hittar åtkomstnyckel-ID och hemlig åtkomstnyckel finns i [dokumentationen för Amazon Web Services](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

### Azure Blob Storage {#azure-blob-external-account}

Det externa **Azure Blob Storage**-kontot kan användas för att importera eller exportera data till Adobe Campaign med hjälp av en **[!UICONTROL Transfer file]**-arbetsflödesaktivitet. Mer information om detta hittar du i det här [avsnittet](../../workflow/using/file-transfer.md).

![](assets/ext_account_23.png)

Om du vill konfigurera **[!UICONTROL Azure external account]** så att den fungerar med Adobe Campaign måste du ange följande information:

* **[!UICONTROL Server]**

  URL för din Azure Blob-lagringsserver.

* **[!UICONTROL Encryption]**

  Typ av vald kryptering mellan **[!UICONTROL None]** eller **[!UICONTROL SSL]**.

* **[!UICONTROL Access key]**

  Om du vill veta var du hittar din **[!UICONTROL Access key]** kan du läsa den här [sidan](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).
