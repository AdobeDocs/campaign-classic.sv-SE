---
title: Kampanjserverkonfiguration
seo-title: Kampanjserverkonfiguration
description: Kampanjserverkonfiguration
seo-description: null
page-status-flag: never-activated
uuid: a1fadad2-e888-4dd8-bc1f-04df16ba7d46
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: f296676e-3bf1-47da-8239-f5ae54e52fc0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4869eb41f942a89c48bc213913c44b70ae777bfc

---


# Kampanjserverkonfiguration{#campaign-server-configuration}

I följande avsnitt beskrivs obligatoriska serverkonfigurationer som garanterar att Adobe Campaign fungerar effektivt för de flesta installationer.

Ytterligare konfigurationer erbjuds i [Konfigurera Campaign-servern](../../installation/using/configuring-campaign-server.md).

>[!NOTE]
>
>Konfigurationer på serversidan kan endast utföras av Adobe för distributioner som hanteras av Adobe. Mer information om de olika distributionerna finns i avsnittet [Värdmodeller](../../installation/using/hosting-models.md) eller i den här [artikeln](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Intern identifierare {#internal-identifier}

Den **interna** identifieraren är en teknisk inloggning som ska användas för installation, administration och underhåll. Inloggningen är inte kopplad till någon instans.

Operatörer som är anslutna med den här inloggningen har alla rättigheter för alla instanser. Den här inloggningen har inget lösenord vid en ny installation. Du måste definiera det här lösenordet manuellt.

Använd följande kommando:

```
nlserver config -internalpassword
```

Därefter visas följande information. Ange och bekräfta lösenordet:

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Konfigurationsfiler {#configuration-files}

Konfigurationsfilerna lagras i mappen **conf** i installationsmappen för Adobe Campaign. Konfigurationen sprids över två filer:

* **`config-<instance>.xml`** (där **instansen** är namnet på instansen): specifik konfiguration för instansen. Om du delar servern mellan flera instanser anger du parametrarna som är specifika för varje instans i den aktuella filen.
* **serverConf.xml**: allmän konfiguration för alla instanser. Den här filen innehåller de tekniska parametrarna för Adobe Campaign-servern: dessa delas av alla instanser. Beskrivningen av några av dessa parametrar beskrivs nedan. Se själva filen för att se alla tillgängliga parametrar. De olika noderna och parametrarna som visas i det här [avsnittet](../../installation/using/the-server-configuration-file.md).

Du kan konfigurera lagringskatalogen (**var** -katalog) för Adobe Campaign-data (loggar, hämtningar, omdirigeringar osv.). Det gör du genom att använda systemvariabeln **XTK_VAR_DIR** :

* I Windows anger du följande värde i systemvariabeln **XTK_VAR_DIR** :

   ```
   D:\log\AdobeCampaign
   ```

* I Linux går du till filen **customer.sh** och anger: **exportera XTK_VAR_DIR=/app/log/AdobeCampaign**.

   Mer information finns i [Anpassa parametrar](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).

## Möjliggöra processer {#enabling-processes}

Adobe Campaign-processer på servern aktiveras (och inaktiveras) via **filen config-default.xml** och **`config-<instance>.xml`** .

Om du vill tillämpa ändringarna på de här filerna måste du köra kommandot **nlserver config -reload** om Adobe Campaign-tjänsten startas.

Det finns två typer av processer: flera instanser och en instans.

* **flera instanser**: en enda process startas för alla instanser. Detta gäller **webb**-, **systemlogd** - och **spårningsloggsprocesser** .

   Aktivering kan konfigureras från filen **config-default.xml** .

   Deklarera en Adobe Campaign-server för åtkomst till klientkonsoler och för omdirigering (spårning):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   I det här exemplet redigeras filen med ett **vi** -kommando i Linux. Den kan redigeras med **.txt** - eller **.xml** -redigerare.

* **mono-instance**: en process startas för varje instans (moduler: **mta**, **wfserver**, **inMail**, **sms** och **stat**).

   Aktivering kan konfigureras med hjälp av instansens konfigurationsfil:

   ```
   config-<instance>.xml
   ```

   Deklarera en server för leverans, köra arbetsflödesinstanser och återställa studentpost:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

## Leveransinställningar {#delivery-settings}

Leveransparametrarna måste konfigureras i mappen **serverConf.xml** .

* **DNS-konfiguration**: Ange leveransdomänen och IP-adresserna (eller värddatorn) för de DNS-servrar som används för att svara på DNS-frågor av MX-typ som görs av MTA-modulen från och **`<dnsconfig>`** med.

   >[!NOTE]
   >
   >Parametern **nameServers** är nödvändig för en installation i Windows. För en installation i Linux måste den lämnas tom.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

De andra leveransparametrarna som är tillgängliga i den här filen visas i [Anpassa leveransparametrar](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).

Se även [E-postleverans](../../installation/using/email-deliverability.md).
