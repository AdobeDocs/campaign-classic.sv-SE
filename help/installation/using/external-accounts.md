---
product: campaign
title: Externa konton
description: Lär dig hur du skapar externa konton
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 4a17d5e8-c73f-42e7-b641-0fee6a52c5c0
source-git-commit: ae235d39c4a78e0a2507f6baaebbdc9986dbf995
workflow-type: tm+mt
source-wordcount: '1818'
ht-degree: 7%

---

# Externa konton{#external-accounts}

![](../../assets/v7-only.svg)

Adobe Campaign innehåller en uppsättning fördefinierade externa konton. Om du vill konfigurera anslutningar med externa system kan du skapa nya externa konton.

Externa konton används av tekniska processer som tekniska arbetsflöden eller Campaign-arbetsflöden. Om du till exempel konfigurerar en filöverföring i ett arbetsflöde eller ett datautbyte med något annat program (Adobe Target, Experience Manager, osv.) måste du välja ett externt konto.

## Skapa ett externt konto {#creating-an-external-account}

Följ stegen nedan om du vill skapa ett nytt externt konto. Detaljerade inställningar beror på typen av externt konto.

1. Från kampanj **[!UICONTROL Explorer]**, markera **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

   ![](assets/ext_account_1.png)

1. Klicka på knappen **[!UICONTROL New]**.

   ![](assets/ext_account_2.png)

1. Ange **[!UICONTROL Label]** och **[!UICONTROL Internal Name]**.
1. Välj ditt externa konto **[!UICONTROL Type]** vilken du vill skapa.
1. Konfigurera åtkomsten till kontot genom att ange autentiseringsuppgifter beroende på vald extern kontotyp.

   Den nödvändiga informationen tillhandahålls vanligtvis av leverantören för den server som du ansluter till.

1. Kontrollera **[!UICONTROL Enabled]** för att aktivera anslutningen.
1. Klicka på **[!UICONTROL Save]**.

Det externa kontot skapas och läggs till i listan över externa konton.

## Kampanjspecifika externa konton

### Studsmeddelanden {#bounce-mails-external-account}

The **Studsa meddelanden** externt konto anger det externa POP3-konto som ska användas för att ansluta till e-posttjänsten. Mer information om det här externa kontot finns i [page](../../workflow/using/inbound-emails.md).

Alla servrar som konfigurerats för POP3-åtkomst kan användas för att ta emot returmeddelanden.

![](assets/ext_account_6.png)

Så här konfigurerar du **[!UICONTROL Bounce mails (defaultPopAccount)]** externt konto:

* **[!UICONTROL Server]**

   URL för POP3-servern.

* **[!UICONTROL Port]**

   Portnummer för POP3-anslutning. Standardporten är 110.

* **[!UICONTROL Account]**

   Användarens namn.

* **[!UICONTROL Password]**

   Lösenord för användarkonto.

* **[!UICONTROL Encryption]**

   Typ av vald kryptering mellan **[!UICONTROL By default]**, **[!UICONTROL POP3 + STARTTLS]**, **[!UICONTROL POP3]** eller **[!UICONTROL POP3S]**.

* **[!UICONTROL Function]**

   Inkommande e-post eller SOAP-router

>[!IMPORTANT]
>
>Innan du konfigurerar ditt POP3-externa konto med Microsoft OAuth 2.0 måste du först registrera programmet i Azure-portalen. Mer information finns på [den här sidan](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app).

Konfigurera en POP3 extern med **Microsoft OAuth 2.0**, kontrollera **[!UICONTROL Microsoft OAuth 2.0]** och fylla i följande fält:

* **[!UICONTROL Azure tenant]**

   Azure ID (eller katalog (klientorganisations-ID) finns i **Grundläggande** listruta med programöversikt i Azure-portalen.

* **[!UICONTROL Azure Client ID]**

   Klient-ID (eller program-ID (klient)) finns i **Grundläggande** listruta med programöversikt i Azure-portalen.

* **[!UICONTROL Azure Client secret]**

   Klienthemligt ID finns i **Klienthemligheter** kolumn från **Certifikat och hemligheter** menyn för ditt program i Azure-portalen.

* **[!UICONTROL Azure Redirect URL]**

   Omdirigerings-URL:en finns i **Autentisering** menyn för ditt program i Azure-portalen. Det ska sluta med följande syntax `nl/jsp/oauth.jsp`, t.ex. `https://redirect.adobe.net/nl/jsp/oauth.jsp`.

När du har angett de olika inloggningsuppgifterna kan du klicka på **[!UICONTROL Setup the connection]** för att slutföra konfigurationen av ditt externa konto.

### Dirigering{#routing-external-account}

The **[!UICONTROL Routing]** Med ett externt konto kan du konfigurera varje kanal som är tillgänglig i Adobe Campaign beroende på vilka paket som är installerade.

![](assets/ext_account_7.png)

Följande kanaler kan konfigureras:

* [E-post](../../installation/using/deploying-an-instance.md#email-channel-parameters)
* [Mobil (SMS)](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)
* [Telefon](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Direktmeddelande](../../delivery/using/about-direct-mail-channel.md)
* [byrå](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Twitter](../../social/using/configuring-publishing-on-twitter.md)
* [iOS](../../delivery/using/configuring-the-mobile-application.md)
* [Android-kanal](../../delivery/using/configuring-the-mobile-application-android.md)

### Körningsinstans  {#execution-instance-external-account}

Om du har en uppdelad arkitektur måste du ange de körningsinstanser som är länkade till kontrollinstansen och ansluta dem. Mallar för transaktionsmeddelanden distribueras till körningsinstansen

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

   URL för servern där körningsinstansen är installerad.

* **[!UICONTROL Account]**

   Namnet på kontot måste matcha Message Center Agent enligt operatormappen.

* **[!UICONTROL Password]**

   Lösenord för kontot enligt definitionen i mappen operator.

Mer information om den här konfigurationen finns i [page](../../message-center/using/configuring-instances.md#control-instance).

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

Om du vill veta var du hittar dessa autentiseringsuppgifter kan du läsa detta [page](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials).

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

Så här lägger du till SSH-nycklar i Windows:

1. Skapa **STARTSIDA** systemvariabel med ett värde angivet som installationskatalog.

2. Lägg till din privata nyckel i `/$HOME/.ssh/id_rsa` mapp.

3. Starta om Adobe Campaign tjänster.

### Extern databas (FDA) {#external-database-external-account}

Använd **Extern databas** skriv ett externt konto för att ansluta till en extern databas. Läs mer om FDA-alternativet (Federated Data Access) i [det här avsnittet](../../installation/using/about-fda.md).

Externa databaser som är kompatibla med Campaign listas i [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md)

![](assets/ext_account_11.png)

Konfigurationsinställningarna för det externa kontot beror på databasmotorn. Läs mer i följande avsnitt:

* Konfigurera åtkomst till [vertica analytics](../../installation/using/configure-fda-vertica.md)
* Konfigurera åtkomst till [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Konfigurera åtkomst till [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)
* Konfigurera åtkomst till [azure synapse](../../installation/using/configure-fda-synapse.md)
* Konfigurera åtkomst till [Hadoop](../../installation/using/configure-fda-hadoop.md)
* Konfigurera åtkomst till [Oracle](../../installation/using/configure-fda-oracle.md)
* Konfigurera åtkomst till [Netezza](../../installation/using/configure-fda-netezza.md)
* Konfigurera åtkomst till [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* Konfigurera åtkomst till [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Konfigurera åtkomst till [sybase IQ](../../installation/using/configure-fda-sybase.md)
* Konfigurera åtkomst till [Teradata](../../installation/using/configure-fda-teradata.md)

### Facebook Connect {#facebook-connect-external-account}

The **[!UICONTROL Facebook Connect]** Med ett externt konto kan du visa personaliserat innehåll i dina Facebook-program, vilket gör det enklare att hitta potentiella kunder via det sociala nätverket.

För varje Facebook-program måste du skapa en **[!UICONTROL Facebook Connect]** skriv ett externt konto. Mer information finns i [page](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/ext_account_12.png)

* **[!UICONTROL Hosting mode]**

   Värdläge för programmet mellan **[!UICONTROL hosted by a partner]** eller **[!UICONTROL hosted by this instance]**.

* **[!UICONTROL Application ID]**

   Program-ID för ditt Facebook-program.

* **[!UICONTROL Application secret]**

   Programhemlighet för ditt Facebook-program.

Om du väljer värdserver för det här instansläget måste webbadressen för den säkra arbetsytan klistras in i **Facebook webbspel (https)** fält på Facebook

Om du vill veta var du hittar dessa autentiseringsuppgifter kan du läsa detta [page](https://developers.facebook.com/docs/facebook-login/access-tokens).

## Externa konton för integrering av lösningar i Adobe

### Adobe Experience Cloud {#adobe-experience-cloud-external-account}

Om du vill ansluta till Adobe Campaign-konsolen med en Adobe ID måste du konfigurera **[!UICONTROL Adobe Experience Cloud (MAC)]** externt konto.

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

   ID för din organisation. Om du vill hitta ditt organisations-ID går du till [den här sidan](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=sv){_blank}.

* **[!UICONTROL Association mask]**

   Syntax som gör att konfigurationsnamn i Enterprise Dashboard kan synkroniseras med grupper i Adobe Campaign.

* **[!UICONTROL Server]**

   URL för din Adobe Experience Cloud-instans.

* **[!UICONTROL Tenant]**

   Namn på din Adobe Experience Cloud-klient.

Mer information om den här konfigurationen finns i [den här sidan](../../integrations/using/configuring-ims.md).

## Webbanalys {#web-analytics-external-account}

The **[!UICONTROL Web Analytics]** Med ett externt konto kan du vidarebefordra data från Adobe Analytics till Adobe Campaign i form av segment. Omvänt skickas indikatorer och attribut för e-postkampanjer som levereras av Adobe Campaign till Adobe Analytics Connector.

![](assets/ext_account_10.png)

För det här externa kontot måste beräkningsformeln för spårade URL:er förbättras och anslutningen mellan de två lösningarna måste godkännas. Se denna [sida](../../platform/using/adobe-analytics-connector.md#external-account-classic) för mer information om detta.

### Adobe Experience Manager {#adobe-experience-manager-external-account}

The **[!UICONTROL AEM (AEM instance)]** Med ett externt konto kan ni hantera innehållet i era e-postleveranser samt formulären direkt i Adobe Experience Manager.

![](assets/ext_account_5.png)

* **[!UICONTROL Server]**

   URL för Adobe Experience Manager-servern.

* **[!UICONTROL Port]**

   Kontonamn som används för att ansluta till Adobe Experience Manager-redigeringsinstansen.

* **[!UICONTROL Password]**

   Lösenord som används för att ansluta till Adobe Experience Manager-redigeringsinstansen.

Mer information om detta hittar du i det här [avsnittet](../../integrations/using/about-adobe-experience-manager.md).

## Externa konton för CRM Connector

### Microsoft Dynamics CRM {#microsoft-dynamics-crm-external-account}

>[!NOTE]
>
> **[!UICONTROL On-premise]** och **[!UICONTROL Office 365]** distributionstyperna är nu inaktuella. [Läs mer](../../rn/using/deprecated-features.md).

The **[!UICONTROL Microsoft Dynamics CRM]** Med ett externt konto kan du importera och exportera Microsoft Dynamics-data till Adobe Campaign.

Läs mer om Campaign - Microsoft Dynamics CRM Connector i detta [page](../../platform/using/crm-ms-dynamics.md).

Med **[!UICONTROL Web API]** distributionstyp och **[!UICONTROL Password credentials]** autentisering måste du ange följande information:

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

   Det konto som används för att logga in på Microsoft CRM.

* **[!UICONTROL Server]**

   URL till din Microsoft CRM-server.

   Hitta Microsoft CRM **[!UICONTROL Server URL]**&#x200B;öppnar du ditt Microsoft Dynamics CRM-konto och klickar sedan på **Dynamics 365** och välj din app. Du kan sedan hitta **[!UICONTROL Server URL]** i webbläsarens adressfält, t.ex. `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Client identifier]**

   Klient-ID som kan hittas från Microsoft Azure-hanteringsportalen i **[!UICONTROL Update your code]** kategori, **[!UICONTROL Client ID]** fält.

* **[!UICONTROL CRM version]**

   Välj **[!UICONTROL Dynamics CRM 365]** CRM-version.

Med **[!UICONTROL Web API]** distributionstyp och **[!UICONTROL Certificate]** autentisering måste du ange följande information:

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

   URL till din Microsoft CRM-server.

   Hitta Microsoft CRM **[!UICONTROL Server URL]**&#x200B;öppnar du ditt Microsoft Dynamics CRM-konto och klickar sedan på **Dynamics 365** och välj din app. Du kan sedan hitta **[!UICONTROL Server URL]** i webbläsarens adressfält, t.ex. `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Private Key (Base64 encoded)]**

   Observera att den privata nyckeln måste kodas till Base64.

   Om du vill göra det kan du använda hjälp av en Base64-kodare eller kommandoraden `base64 -w0 private.key` för Linux.

* **[!UICONTROL Custom Key identifier]**

* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

   Klient-ID som kan hittas från Microsoft Azure-hanteringsportalen i **[!UICONTROL Update your code]** kategori, **[!UICONTROL Client ID]** fält.

* **[!UICONTROL CRM version]**

   CRM-version mellan **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** eller **[!UICONTROL Dynamics CRM 2016]**.

Mer information om den här konfigurationen finns i [page](../../platform/using/crm-connectors.md).

### Salesforce.com CRM  {#salesforce-crm-external-account}

The **[!UICONTROL Salesforce CRM]** Med ett externt konto kan du importera och exportera Salesforce-data till Adobe Campaign.

![](assets/ext_account_17.png)

Om du vill konfigurera det externa Salesforce CRM-kontot så att det fungerar med Adobe Campaign måste du ange följande information:

* **[!UICONTROL Account]**

   Det konto som används för att logga in i Salesforce CRM.

* **[!UICONTROL Password]**

   Lösenord som används för att logga in i Salesforce CRM.

* **[!UICONTROL Client identifier]**

   Om du vill veta var du kan hitta din klientidentifierare kan du läsa detta [page](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL Security token]**

   Om du vill veta var du hittar din säkerhetstoken kan du läsa detta [page](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL API version]**

   Välj version av API:t.

För det här externa kontot måste du konfigurera Salesforce CRM med konfigurationsguiden.

Mer information om den här konfigurationen finns i [page](../../platform/using/crm-connectors.md).

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

   Om du vill veta var du hittar ditt ID för AWS-åtkomstnyckel kan du läsa detta [page](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

* **[!UICONTROL Secret access key to AWS]**

   Om du vill veta var du hittar din hemliga åtkomstnyckel till AWS kan du läsa detta [page](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

* **[!UICONTROL AWS Region]**

   Läs mer om AWS [page](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

* The **[!UICONTROL Use server side encryption]** kan du lagra filen i S3-krypterat läge.

Om du vill veta var du hittar nyckel-ID:t och den hemliga åtkomstnyckeln kan du läsa Amazon webbtjänster [dokumentation](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

### Azure Blob Storage {#azure-blob-external-account}

The **Azure Blob Storage** externt konto kan användas för att importera eller exportera data till Adobe Campaign med en **[!UICONTROL Transfer file]** arbetsflödesaktivitet. Mer information om detta hittar du i det här [avsnittet](../../workflow/using/file-transfer.md).

![](assets/ext_account_23.png)

Så här konfigurerar du **[!UICONTROL Azure external account]** om du vill arbeta med Adobe Campaign måste du ange följande:

* **[!UICONTROL Server]**

   URL för din Azure Blob-lagringsserver.

* **[!UICONTROL Encryption]**

   Typ av vald kryptering mellan **[!UICONTROL None]** eller **[!UICONTROL SSL]**.

* **[!UICONTROL Access key]**

   Ta reda på var du hittar **[!UICONTROL Access key]**, se [page](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).
