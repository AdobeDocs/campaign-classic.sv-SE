---
solution: Campaign Classic
product: campaign
title: Externa konton
description: Lär dig hur du skapar externa konton
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 4a17d5e8-c73f-42e7-b641-0fee6a52c5c0
source-git-commit: 54d503e97a4374927c4ebe3ba4e0ec05e51d47db
workflow-type: tm+mt
source-wordcount: '1541'
ht-degree: 8%

---

# Externa konton{#external-accounts}

Adobe Campaign innehåller en uppsättning fördefinierade externa konton. Om du vill konfigurera anslutningar med externa system kan du skapa nya externa konton.

Externa konton används av tekniska processer som tekniska arbetsflöden eller Campaign-arbetsflöden. Om du till exempel konfigurerar en filöverföring i ett arbetsflöde eller ett datautbyte med något annat program (Adobe Target, Experience Manager, osv.) måste du välja ett externt konto.

## Skapa ett externt konto {#creating-an-external-account}

Följ stegen nedan om du vill skapa ett nytt externt konto. Detaljerade inställningar beror på typen av externt konto.

1. I Campaign **[!UICONTROL Explorer]** väljer du **[!UICONTROL Administration]** **[!UICONTROL Platform]** > **[!UICONTROL External accounts]**.

   ![](assets/ext_account_1.png)

1. Klicka på knappen **[!UICONTROL New]**.

   ![](assets/ext_account_2.png)

1. Ange en **[!UICONTROL Label]** och en **[!UICONTROL Internal Name]**.
1. Välj det externa kontot **[!UICONTROL Type]** som du vill skapa.
1. Konfigurera åtkomsten till kontot genom att ange autentiseringsuppgifter beroende på vald extern kontotyp.

   Den nödvändiga informationen tillhandahålls vanligtvis av leverantören för den server som du ansluter till.

1. Markera alternativet **[!UICONTROL Enabled]** för att aktivera anslutningen.
1. Klicka på **[!UICONTROL Save]**.

Det externa kontot skapas och läggs till i listan över externa konton.

## Kampanjspecifika externa konton

### Studsmeddelanden {#bounce-mails-external-account}

Det externa kontot **studs-e-post** anger det externa POP3-kontot som ska användas för att ansluta till e-posttjänsten. Mer information om det här externa kontot finns på den här [sidan](../../workflow/using/inbound-emails.md).

Alla servrar som konfigurerats för POP3-åtkomst kan användas för att ta emot returmeddelanden.

![](assets/ext_account_6.png)

Så här konfigurerar du det externa kontot **[!UICONTROL Bounce mails (defaultPopAccount)]**:

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

### Dirigering{#routing-external-account}

Med det externa **[!UICONTROL Routing]**-kontot kan du konfigurera varje kanal som är tillgänglig i Adobe Campaign beroende på vilka paket som är installerade.

![](assets/ext_account_7.png)

Följande kanaler kan konfigureras:

* [E-post](../../installation/using/deploying-an-instance.md#email-channel-parameters)
* [Mobil (SMS)](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)
* [Telefon](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Direktmeddelande](../../delivery/using/about-direct-mail-channel.md)
* [byrå](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Facebook](../../social/using/publishing-on-facebook-walls.md#delegating-write-access-to-adobe-campaign)
* [Twitter](../../social/using/configuring-publishing-on-twitter.md)
* [iOS-kanal](../../delivery/using/configuring-the-mobile-application.md)
* [Android-kanal](../../delivery/using/configuring-the-mobile-application-android.md)


### Körningsinstans {#execution-instance-external-account}

Om du har en uppdelad arkitektur måste du ange de körningsinstanser som är länkade till kontrollinstansen och ansluta dem. Mallar för transaktionsmeddelanden distribueras till körningsinstansen

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

   URL för servern där körningsinstansen är installerad.

* **[!UICONTROL Account]**

   Namnet på kontot måste matcha Message Center Agent enligt operatormappen.

* **[!UICONTROL Password]**

   Lösenord för kontot enligt definitionen i mappen operator.

Mer information om den här konfigurationen finns på den här [sidan](../../message-center/using/configuring-instances.md#control-instance).


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

Om du vill veta var du hittar dessa autentiseringsuppgifter kan du gå till den här [sidan](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials).

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

### Extern databas (FDA) {#external-database-external-account}

Använd **extern databas** för att ansluta till en extern databas. Läs mer om FDA-alternativet (Federated Data Access) i [det här avsnittet](../../installation/using/about-fda.md).

Externa databaser som är kompatibla med Campaign listas i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md)

![](assets/ext_account_11.png)

Konfigurationsinställningarna för det externa kontot beror på databasmotorn. Läs mer i följande avsnitt:

* Konfigurera åtkomst till [Azure synapse](../../installation/using/configure-fda-synapse.md)
* Konfigurera åtkomst till [Hadoop](../../installation/using/configure-fda-hadoop.md)
* Konfigurera åtkomst till [Oracle](../../installation/using/configure-fda-oracle.md)
* Konfigurera åtkomst till [Netezza](../../installation/using/configure-fda-netezza.md)
* Konfigurera åtkomst till [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* Konfigurera åtkomst till [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Konfigurera åtkomst till [Sybase IQ](../../installation/using/configure-fda-sybase.md)
* Konfigurera åtkomst till [Teradata](../../installation/using/configure-fda-teradata.md)

### Facebook Connect {#facebook-connect-external-account}

Med det externa **[!UICONTROL Facebook Connect]**-kontot kan du visa anpassat innehåll i dina Facebook-program, vilket gör det enklare att hitta potentiella kunder via det här sociala nätverket.

För varje Facebook-program måste du skapa ett externt konto av typen **[!UICONTROL Facebook Connect]**. Mer information finns på [sida](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/ext_account_12.png)

* **[!UICONTROL Hosting mode]**

   Programmets värdläge mellan **[!UICONTROL hosted by a partner]** eller **[!UICONTROL hosted by this instance]**.

* **[!UICONTROL Application ID]**

   Program-ID för ditt Facebook-program.

* **[!UICONTROL Application secret]**

   Programhemlighet för ditt Facebook-program.

Om du väljer värdserver för det här instansläget måste webbadressen för den säkra arbetsytan klistras in i fältet **Facebook webbspel (https)** i Facebook

Om du vill veta var du hittar dessa autentiseringsuppgifter kan du gå till den här [sidan](https://developers.facebook.com/docs/facebook-login/access-tokens).

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

   ID för din IMS-organisation. Information om hur du hittar ditt organisations-ID finns på [den här sidan](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html) (**Var hittar jag mitt IMS-organisations-ID?**).

* **[!UICONTROL Association mask]**

   Syntax som gör att konfigurationsnamn i Enterprise Dashboard kan synkroniseras med grupper i Adobe Campaign.

* **[!UICONTROL Server]**

   URL för din Adobe Experience Cloud-instans.

* **[!UICONTROL Tenant]**

   Namn på din Adobe Experience Cloud-klient.

Mer information om den här konfigurationen finns på [den här sidan](../../integrations/using/configuring-ims.md).

## Webbanalys {#web-analytics-external-account}

Med det externa **[!UICONTROL Web Analytics (Adobe Analytics - Data connector)]**-kontot kan du vidarebefordra data från Adobe Analytics till Adobe Campaign i form av segment. Omvänt skickas indikatorer och attribut för e-postkampanjer som levereras av Adobe Campaign till Adobe Analytics - Datakoppling.

![](assets/ext_account_10.png)

För det här externa kontot måste beräkningsformeln för spårade URL:er förbättras och anslutningen mellan de två lösningarna måste godkännas. Se denna [sida](../../platform/using/adobe-analytics-data-connector.md#step-2--create-the-external-account-in-campaign) för mer information om detta.

### Adobe Experience Manager {#adobe-experience-manager-external-account}

Med det externa **[!UICONTROL AEM (AEM instance)]**-kontot kan du hantera innehållet i e-postleveranser och formulär direkt i Adobe Experience Manager.

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

Med det externa **[!UICONTROL Microsoft Dynamics CRM]**-kontot kan du importera och exportera Microsoft Dynamics-data till Adobe Campaign.

Läs mer om Campaign - Microsoft Dynamics CRM Connector på den här [sidan](../../platform/using/crm-ms-dynamics.md).

>[!NOTE]
>
> **[!UICONTROL On-premise]** och  **[!UICONTROL Office 365]** distributionstyperna är nu föråldrade. [Läs mer](../../rn/using/deprecated-features.md).

Med distributionstypen **[!UICONTROL Web API]** och verifieringen **[!UICONTROL Password credentials]** måste du ange följande information:

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

   Konto som används för att logga in i Microsoft CRM.

* **[!UICONTROL Server]**

   URL till din Microsoft CRM-server.

* **[!UICONTROL Client identifier]**

   Klient-ID som kan hittas från Microsoft Azure-hanteringsportalen i fältet **[!UICONTROL Update your code]**, **[!UICONTROL Client ID]**.

* **[!UICONTROL CRM version]**

   CRM-version mellan **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** eller **[!UICONTROL Dynamics CRM 2016]**.

Med distributionstypen **[!UICONTROL Web API]** och verifieringen **[!UICONTROL Certificate]** måste du ange följande information:

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

   URL till din Microsoft CRM-server.

* **[!UICONTROL Private Key (Base64 encoded)]**

   Privat nyckel kodad till Base64

* **[!UICONTROL Custom Key identifier]**

* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

   Klient-ID som kan hittas från Microsoft Azure-hanteringsportalen i fältet **[!UICONTROL Update your code]**, **[!UICONTROL Client ID]**.

* **[!UICONTROL CRM version]**

   CRM-version mellan **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** eller **[!UICONTROL Dynamics CRM 2016]**.

Mer information om den här konfigurationen finns på den här [sidan](../../platform/using/crm-connectors.md).

### Salesforce.com CRM {#salesforce-crm-external-account}

Med det externa **[!UICONTROL Salesforce CRM]**-kontot kan du importera och exportera Salesforce-data till Adobe Campaign.

![](assets/ext_account_17.png)

Om du vill konfigurera det externa Salesforce CRM-kontot så att det fungerar med Adobe Campaign måste du ange följande information:

* **[!UICONTROL Account]**

   Det konto som används för att logga in i Salesforce CRM.

* **[!UICONTROL Password]**

   Lösenord som används för att logga in i Salesforce CRM.

* **[!UICONTROL Client identifier]**

   Om du vill veta var du hittar din klientidentifierare kan du gå till den här [sidan](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL Security token]**

   Om du vill veta var du hittar din säkerhetstoken kan du gå till den här [sidan](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL API version]**

   Välj version av API:t.

För det här externa kontot måste du konfigurera Salesforce CRM med konfigurationsguiden.

Mer information om den här konfigurationen finns på den här [sidan](../../platform/using/crm-connectors.md).

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

   Information om var du hittar ditt ID för AWS-åtkomstnyckel finns på den här [sidan](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

* **[!UICONTROL Secret access key to AWS]**

   Information om var du hittar din hemliga åtkomstnyckel till AWS finns på den här [sidan](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

* **[!UICONTROL AWS Region]**

   Mer information om AWS-regionen finns på den här [sidan](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

* Med kryssrutan **[!UICONTROL Use server side encryption]** kan du lagra filen i S3-krypterat läge.

Mer information om var du hittar nyckel-ID och hemlig åtkomstnyckel finns i Amazon Web services [dokumentation](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

### Azure Blob Storage (#azure-blob-external-account)

Det externa kontot **Azure Blob storage** kan användas för att importera eller exportera data till Adobe Campaign med en **[!UICONTROL Transfer file]**-arbetsflödesaktivitet. Mer information om detta hittar du i det här [avsnittet](../../workflow/using/file-transfer.md).

![](assets/ext_account_23.png)

Om du vill konfigurera **[!UICONTROL Azure external account]** så att det fungerar med Adobe Campaign måste du ange följande information:

* **[!UICONTROL Server]**

   URL för din Azure Blob-lagringsserver.

* **[!UICONTROL Encryption]**

   Typ av vald kryptering mellan **[!UICONTROL None]** eller **[!UICONTROL SSL]**.

* **[!UICONTROL Access key]**

   Om du vill veta var du hittar **[!UICONTROL Access key]** kan du gå till den här [sidan](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).
