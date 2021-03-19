---
solution: Campaign Classic
product: campaign
title: Konfiguration av kampanjservern
description: Konfiguration av kampanjservern
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 95d0686c4ddeb4e25eb918ca92cbd6a0b1aa1f3c
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 1%

---


# Konfiguration av kampanjservern{#campaign-server-configuration}

I följande avsnitt beskrivs obligatoriska serverkonfigurationer som garanterar att Adobe Campaign fungerar effektivt för de flesta konfigurationer.

Ytterligare konfigurationer finns i [Konfigurera kampanjservern](../../installation/using/configuring-campaign-server.md).

>[!NOTE]
>
>Konfigurationer på serversidan kan bara utföras av Adobe för distributioner som hanteras av Adobe. Mer information om de olika distributionerna finns i avsnittet [Värdmodeller](../../installation/using/hosting-models.md) eller i [kapacitetsmatrisen](../../installation/using/capability-matrix.md).

## Intern identifierare {#internal-identifier}

Identifieraren **internal** är en teknisk inloggning som ska användas för installation, administration och underhåll. Inloggningen är inte kopplad till någon instans.

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

Konfigurationsfilerna lagras i mappen **conf** i Adobe Campaign installationsmapp. Konfigurationen sprids över två filer:

* **`config-<instance>.xml`** (där  **** instansen heter): specifik konfiguration för instansen. Om du delar servern mellan flera instanser anger du parametrarna som är specifika för varje instans i den aktuella filen.
* **serverConf.xml**: allmän konfiguration för alla instanser. Den här filen innehåller de tekniska parametrarna för Adobe Campaign-servern: dessa delas av alla instanser. Beskrivningen av några av dessa parametrar beskrivs nedan. Se själva filen för att se alla tillgängliga parametrar. De olika noderna och parametrarna som listas i det här [avsnittet](../../installation/using/the-server-configuration-file.md).

Du kan konfigurera lagringskatalogen (**var** katalog) för Adobe Campaign-data (loggar, hämtningar, omdirigeringar osv.). Det gör du genom att använda systemvariabeln **XTK_VAR_DIR**:

* I Windows anger du följande värde i systemvariabeln **XTK_VAR_DIR**

   ```
   D:\log\AdobeCampaign
   ```

* I Linux går du till filen **customer.sh** och anger: **exportera XTK_VAR_DIR=/app/log/AdobeCampaign**.

   Mer information finns i [Anpassa parametrar](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).

## Aktivera processer {#enabling-processes}

Adobe Campaign-processer på servern aktiveras (och inaktiveras) via filerna **config-default.xml** och **`config-<instance>.xml`**.

Om du vill tillämpa ändringarna på de här filerna måste du köra kommandot **nlserver config -reload** om Adobe Campaign-tjänsten startas.

Det finns två typer av processer: flera instanser och en instans.

* **flera instanser**: en enda process startas för alla instanser. Detta gäller för **web**, **syslogd** och **trackinglogd**-processer.

   Aktivering kan konfigureras från filen **config-default.xml**.

   Deklarera en Adobe Campaign-server för åtkomst till klientkonsoler och för omdirigering (spårning):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   I det här exemplet redigeras filen med ett **vi**-kommando i Linux. Den kan redigeras med en **.txt** eller **.xml**-redigerare.

* **mono-instance**: en process startas för varje instans (moduler:  **mta**,  **wfserver**,  **inMail**,  **** smand  **stat**).

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

Leveransparametrarna måste konfigureras i mappen **serverConf.xml**.

* **DNS-konfiguration**: Ange leveransdomänen och IP-adresserna (eller värddatorn) för de DNS-servrar som används för att svara på DNS-frågor av MX-typ som görs av MTA-modulen från  **`<dnsconfig>`** och med.

   >[!NOTE]
   >
   >Parametern **nameServers** är nödvändig för en installation i Windows. För en installation i Linux måste den lämnas tom.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Övriga leveransparametrar som är tillgängliga i den här filen visas i [Anpassa leveransparametrar](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).

Se även [E-postleverans](../../installation/using/email-deliverability.md).
