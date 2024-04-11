---
product: campaign
title: Serverkonfigurationsfilen
description: Serverkonfigurationsfilen
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 70cd6a4b-c839-4bd9-b9a7-5a12e59c0cbf
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '8068'
ht-degree: 1%

---

# Serverkonfigurationsfilen{#the-server-configuration-file}

Den övergripande konfigurationen av Adobe Campaign definieras i **serverConf.xml** -filen som finns i **conf** installationskatalogen. I det här avsnittet visas alla olika noder och parametrar för **serverConf.xml** -fil.

>[!NOTE]
>
>Konfigurationer på serversidan kan bara utföras av Adobe för distributioner som hanteras av Adobe. Mer information om de olika distributionerna finns i [Värdmodeller](../../installation/using/hosting-models.md) avsnitt eller till [den här sidan](../../installation/using/capability-matrix.md). Installations- och konfigurationsstegen för värdbaserade modeller och hybridmodeller beskrivs i detta [section](../../installation/using/hosting-models.md).

De första parametrarna finns i **delad** nod. Dessa är relaterade till instansen. De kan användas av alla nlserver-kommandon (nlserver web, nlserver wfserver osv.). De andra avsnitten är relaterade till ett specifikt underkommando på servern.

**Delade parametrar**

* [autentisering](#authentication)
* [dataStore](#datastore)
* [dnsConfig](#dnsconfig)
* [exec](#exec)
* [htmlToPdf](#htmltopdf)
* [ims](#ims)
* [javaScript](#javascript)
* [mailExchanger](#mailexchanger)
* [modul](#module)
* [övervakning](#monitoring)
* [ooconv](#ooconv)
* [proxyConfig](#proxyconfig)
* [threadPool](#threadpool)
* [urlPermission](#urlpermission)
* [cusHeaders](#cusheaders)
* [xtkJobs](#xtkjobs)

**Andra parametrar**

* [arkivering](#archiving)
* [inMail](#inmail)
* [interactiond](#interactiond)
* [mta](#mta)
* [nmac](#nmac)
* [rörlig](#pipelined)
* [reparation](#repair)
* [securityZone](#securityzone)
* [sms](#sms)
* [stat](#stat)
* [syslogd](#syslogd)
* [spårning](#tracking)
* [trackinglogd](#trackinglogd)
* [webb](#web)
* [wfserver](#wfserver)

## autentisering {#authentication}

Här är de olika parametrarna för **autentisering** nod:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> checkIPConsistent<br /> </td> 
   <td> Aktivera IP-adresskontroll.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultMode<br /> </td> 
   <td> Standardidentifieringsläge.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> nl<br /> </td> 
  </tr> 
  <tr> 
   <td> longSessionTimeOutSec<br /> </td> 
   <td> Timeout för långa sessioner i sekunder.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 129600<br /> </td> 
  </tr> 
  <tr> 
   <td> securityTimeOutSec<br /> </td> 
   <td> Timeout för säkerhetstoken i sekunder.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionCacheSec<br /> </td> 
   <td> Cachevaraktighet: sessionsinformationens cache i sekunder.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTimeOutSec<br /> </td> 
   <td> Tidsgräns för session i sekunder.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
 </tbody> 
</table>

### XTK {#xtk}

Här är de olika parametrarna för **autentisering > XTK** nod:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> internalPassword<br /> </td> 
   <td> Lösenord för internt konto.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> internalSecurityZone<br /> </td> 
   <td> Intern kontosäkerhetszon: auktoriserad zon för det interna kontot.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 'lan'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## dataStore {#datastore}

Här är de olika parametrarna för **dataStore** nod. Det är här serverdatakällorna definieras.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> exportDirectory<br /> </td> 
   <td> Exportkatalog: sökväg till målkatalog för exporterade data.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/export/' <br /> </td> 
  </tr> 
  <tr> 
   <td> extraSandboxedDirectories<br /> </td> 
   <td> Extra sandlådekataloger: andra banor som ska läggas till i sandlådan (separerade med koma).<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> '/home/customers/,/sftp/' <br /> </td> 
  </tr> 
  <tr> 
   <td> formCacheTimeToLive<br /> </td> 
   <td> Fördröjning för förfallodatum för formulärcache: tidsgräns i sekunder efter vilken en cachepost ogiltigförklaras. O betyder att cacheposter bara uppdateras vid publiceringstidpunkten.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> värdar<br /> </td> 
   <td> DNS-masker: lista med DNS-masker som den här instansen använder (kommaseparerade, kan använda * och ? mönster).<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> *'<br /> </td> 
  </tr> 
  <tr> 
   <td> interactionCacheTimeToLive<br /> </td> 
   <td> Fördröjning för JSSP-cache för interaktion: timeout i sekunder efter vilken en cachepost ogiltigförklaras. Ett negativt värde innebär att cachen alltid blir ogiltig. 0, tomma eller ogiltiga värden anses vara 60.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> lang<br /> </td> 
   <td> Instansspråk (uppräkning). Möjliga värden är 'fr_FR' (Français), 'en_GB' (English (UK)), 'en_US' (English (US)), 'de_DE' (Deutsch) och 'ja_JP' (japanska).<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 'en_US'<br /> </td> 
  </tr> 
  <tr> 
   <td> uploadDirectory<br /> </td> 
   <td> Uppladdningsmapp: sökväg till målkatalog för överförda data.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/upload/' <br /> </td> 
  </tr> 
  <tr> 
   <td> uploadAllowlist<br /> </td> 
   <td> Auktoriserade filer som ska laddas ned avgränsade med ','. Strängen måste vara ett giltigt, reguljärt java-uttryck. Se <a href="file-res-management.md" target="_blank">Begränsa överförbara filer</a>.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> '.+' <br /> </td> 
  </tr> 
  <tr> 
   <td> useVault<br /> </td> 
   <td> Lagra hemligheter i valv: använd Hashicorp Vault.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultSecretPath<br /> </td> 
   <td> Hemlig sökväg i valv<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> '/v1/secrets/campaign/'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultTokenPath<br /> </td> 
   <td> Lokal sökväg till filen som innehåller vaulttoken. $(HOME) kan användas i den här sökvägen (men inte i andra miljövariabler).<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> '$(HOME)/.vaulttoken'<br /> </td> 
  </tr> 
  <tr> 
   <td> vaultUrl<br /> </td> 
   <td> Hashicorp Vault URL <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> viewCacheTimeToLive<br /> </td> 
   <td> Giltighetsperiod för visningscache: timeout i sekunder efter vilken en cachepost ogiltigförklaras. Ett negativt värde innebär att cachen alltid blir ogiltig. 0, tomma eller ogiltiga värden anses vara 60.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> workingDirectory<br /> </td> 
   <td> XPath för arbetskatalogen.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> workingDirectory: XPath för arbetskatalogen. Standard: '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/workspace/'<br /> </td> 
  </tr> 
 </tbody> 
</table>

### proxyAdjust {#proxyadjust}

Här är de olika parametrarna för **dataStore > proxyAdjust** nod. URL:er som matchar det reguljära uttrycket genereras om baserat på den URL som definieras i urlBase.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> urlBase<br /> </td> 
   <td> Bas att använda när externa URL:er genereras. Exempel: https://server.domain.com<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Reguljärt uttryck som matchar URL:er. Exempel: http://server\.lan\.net.*<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
 </tbody> 
</table>

### dataSource {#datasource}

Här är de olika parametrarna för **dataStore > dataSource** nod.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Namn på datakälla<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> standard<br /> </td> 
  </tr> 
 </tbody> 
</table>

I **dataStore > dataSource > dbcnx** -nod, konfigurera anslutningsinställningarna:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NChar<br /> </td> 
   <td> Unicode-lagring<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> dbSchema<br /> </td> 
   <td> Arbetsyta<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> krypterad<br /> </td> 
   <td> Krypterat lösenord<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> inloggning<br /> </td> 
   <td> Konto<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> lösenord<br /> </td> 
   <td> Lösenord<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> provider<br /> </td> 
   <td> Typ (uppräkning). Möjliga värden är 'Oracle', 'MSSQL' (Microsoft SQL Server), 'PostgreSQL' (PostgreSQL), 'Teradata', 'DB2', 'MySQL', 'Netezza', 'AsterData', 'SAPHANA' (SAP HANA), 'RedShift' (Amazon Redshift), 'ODBC' (ODBC (Sybase ASE), Sybase IQ), 'Relay' (HTTP-relä till fjärrdatabas).<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> oracle<br /> </td> 
  </tr> 
  <tr> 
   <td> server<br /> </td> 
   <td> Server<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> tidszon<br /> </td> 
   <td> Tidszon: se <a href="../../installation/using/time-zone-management.md" target="_blank">Tidszonshantering</a>.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> unicodeData<br /> </td> 
   <td> Unicode-data i databasen<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> useTimestampTZ<br /> </td> 
   <td> Datumfält med tidszon: se <a href="../../installation/using/time-zone-management.md" target="_blank">Tidszonshantering</a>.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

I **dataStore > dataSource > sqlParams** -nod, konfigurera SQL-parametrar:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> funcPrefix<br /> </td> 
   <td> Funktionsprefix<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
 </tbody> 
</table>

I **dataStore > dataSource > pool** -nod, konfigurera parametrarna för den associerade anslutningspoolen:

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> aliveTestDelaySec<br /> </td> 
   <td> Fördröjning mellan giltighetskontroller för anslutning.<br /> </td> 
   <td> Kort<br /> </td> 
  </tr> 
  <tr> 
   <td> freeCnx<br /> </td> 
   <td> Antal kostnadsfria anslutningar i poolen.<br /> </td> 
   <td> Kort<br /> </td> 
  </tr> 
  <tr> 
   <td> maxCnx<br /> </td> 
   <td> Maximalt antal tillåtna anslutningar innan en ny anslutning nekas. Se det här <a href="https://helpx.adobe.com/campaign/kb/how-to-increase-the-maximum-number-of-database-connections-from-.html">technote</a>.<br /> </td> 
   <td> Kort<br /> </td> 
  </tr> 
  <tr> 
   <td> maxIdleDelaySec<br /> </td> 
   <td> Maximal inaktivitetstid för anslutning. 0 betyder standardvärde.<br /> </td> 
   <td> Kort<br /> </td> 
  </tr> 
 </tbody> 
</table>

### virtualDir {#virtualdir}

Här är de olika parametrarna för **dataStore > virtualDir** nod. Detta är konfigurationen av den virtuella katalogen till den verkliga katalogmappningen.

Mer information finns i [Hantera offentliga resurser](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Namnet på den virtuella katalogen <br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
  <tr> 
   <td> bana<br /> </td> 
   <td> Fullständig sökväg till den faktiska katalogen<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
 </tbody> 
</table>

Här är standardkonfigurationen:

```
<virtualDir name="images" path="$(XTK_INSTALL_DIR)/var/res/img/"/>
<virtualDir name="formCache" path="$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/formCache/"/>
<virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)"/>
```

### preprocessCommand {#preprocesscommand}

Här är de olika parametrarna för **dataStore > preprocessCommand** nod. Detta är de auktoriserade kommandona för förbearbetning av arbetsflödesaktiviteten Läs in fil.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> kommando<br /> </td> 
   <td> Kommandorad <br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Etikett för kommandorad<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Kommandoradsnamn<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
 </tbody> 
</table>

Här är standardkonfigurationen:

```
<preprocessCommand command="" label="None" name="none"/>
<preprocessCommand command="zcat &quot;$fileName&quot;" label="Decompression" name="zcat"/><preprocessCommand command="gpg --decrypt &quot;$fileName&quot;" label="Decrypt" name="gpg"/>
```

## dnsConfig {#dnsconfig}

Här är de olika parametrarna för **dnsConfig** (DNS-konfiguration) nod.

Mer information finns i [section](../../installation/using/configuring-campaign-server.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> Domännamn: standarddomännamn. Används av kommandot SMTP HELO. Som standard använder nätverksparametrarna för det första nätverksgränssnittet som deklarerats i Windows, eller tolkar file/etc/resolv.conf under Linux (domän eller sökpost). <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> nameServers<br /> </td> 
   <td> DNS-server: kommaavgränsad lista över DNS-servrar. Se anmärkningen nedan.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> försök igen<br /> </td> 
   <td> Antal försök för en DNS-fråga.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Timeout i millisekunder för en DNS-fråga.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 5000<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Anteckning på **nameSevers**: som standard använder nätverket
>parametrar för det första nätverksgränssnittet som deklarerats i Windows
>inte definierad i UNIX. Definierar domännamnsservrar (DNS)
>används av MTA för att hämta e-postväxlaren deklarerad för
>en domän.
>
>Om det här värdet inte definieras söker MTA efter den här informationen i värdnätverkskonfigurationen. Om flera DNS-adresser är möjliga måste de olika DNS-adresserna avgränsas med kommatecken (exempel: 212.155.207.1,212.155.207.2). Om leveransservern har flera nätverksgränssnitt är den DNS-lista som används av MTA den första. I det här fallet rekommenderar vi att du anger **nameServer** för att undvika tvetydighet.

>[!CAUTION]
>
>Om din nätverksvärdkonfiguration använder DHCP kommer MTA inte att hitta den DNS-lista som DHCP tillhandahåller. I det här fallet rekommenderar vi att du anger DNS-listan i nätverksparametrarna på Kontrollpanelen i Windows.

## exec {#exec}

Här är de olika parametrarna för **exec** (kommandokörning)-nod.

Mer information finns i [Begränsa tillåtna externa kommandon](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> svartlistFile<br /> </td> 
   <td> Sökväg till filen som innehåller de kommandon som ska läggas till i tillåtelselista. <br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
  <tr> 
   <td> användare<br /> </td> 
   <td> Kör kommandon som en annan användare.<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
 </tbody> 
</table>

## htmlToPdf {#htmltopdf}

Här är de olika parametrarna för **htmlToPdf** nod. Det här är konfigurationen för tjänsten för konvertering av webbsidor till PDF-dokument.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> kommando<br /> </td> 
   <td> Kommandorad för att köra konverteringen (i "annat"-läge).<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessusCount<br /> </td> 
   <td> Max. Antal konverteringsprocesser som tillåts samtidigt på en dator.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> läge<br /> </td> 
   <td> Verktyg som ska användas för konverteringen. Möjliga värden är: phantomjs, wkhtmltopdf, other, disabled<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 'phantomjs' <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Timeout för en konvertering: maximal konverteringstid i sekunder. Efter detta tröskelvärde stoppas konverteringsprocessen och ett fel uppstår.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 120<br /> </td> 
  </tr> 
  <tr> 
   <td> utförlig<br /> </td> 
   <td> Utförligt läge: starta i detaljerat läge för att diagnostisera eventuella fel.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> waitTime<br /> </td> 
   <td> Fördröjning vid väntan på en process: fördröjning i sekunder, när alla processer används samtidigt och när en process väntar på att frigöras. Om den här fördröjningen överskrids stoppas konverteringen och ett fel uppstår. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
 </tbody> 
</table>

Exempel på fantomjs:

```
phantomjs - -ignore-ssl-errors=true '$(XTK_INSTALL_DIR)/bin/htmlToPdf.js' '-out:{outPdf}' '-post:{postFile}' '-url:{originUrl}' -sessiontoken:{sessiontoken} -format:{format} -orientation:{orientation} -marginTop:{marginTop} -marginLeft:{marginLeft} -marginRight:{marginRight} -marginBottom:{marginBottom}
```

## ims {#ims}

Här är de olika parametrarna för **ims** nod. Det här är konfigurationen för Campaign som ansluter till en annan tjänst med [IMS](../../integrations/using/about-adobe-id.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> authIMSClientId<br /> </td> 
   <td> Klient-ID<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSClientSecret<br /> </td> 
   <td> Hemlig nyckel (krypterad i AES)<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSCode<br /> </td> 
   <td> Auktoriseringskod (krypterad i AES)<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSEndpoint<br /> </td> 
   <td> URL för IMS-server<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> https://ims-na1.adobelogin.com'<br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientId<br /> </td> 
   <td> Klient-ID för tekniskt konto<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAClientSecret<br /> </td> 
   <td> Teknisk kontohemlig nyckel (krypterad i AES)<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAId<br /> </td> 
   <td> Tekniskt konto-ID<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authIMSTAPrivateKey<br /> </td> 
   <td> Privat nyckel för tekniskt konto (krypterat i AES)<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## JavaScript {#javascript}

Här är de olika parametrarna för **javaScript** nod. Detta är konfigurationen för JavaScript-tolken.

Mer information finns i [Rapporteringsdokumentation](../../reporting/using/actions-on-reports.md#memory-allocation).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxMB<br /> </td> 
   <td> Maximal storlek i MB innan skräpinsamlaren körs.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 512 <br /> </td> 
  </tr> 
  <tr> 
   <td> stackSizeKB<br /> </td> 
   <td> Storlek på varje stacksegment i kilooktetter. Detta är en justeringsparameter för minneshantering som de flesta användare inte bör justera. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mailExchanger {#mailexchanger}

Här är de olika parametrarna för **mailExchanger** nod. Detta är konfigurationen för SMTP-servern.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> mxAddress<br /> </td> 
   <td> SMTP-server: SMTP-serverns IP-adress för överföring av e-post.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> mxPort<br /> </td> 
   <td> TCP-porten för SMTP-servern som används för e-postöverföringen.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## modul {#module}

Här är de olika parametrarna för **modul** nod. Det här är konfigurationen för modulen för namnutrymmesbegränsningar xtk.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> defaultNameSpace<br /> </td> 
   <td> Standardnamnutrymme som används när en ny entitet skapas.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 'cus'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## övervakning {#monitoring}

Här är de olika parametrarna för **övervakning** nod. Detta är övervakningstjänstens konfiguration.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPreparationJobsSec<br /> </td> 
   <td> Maximal beredningstid: varaktighet i sekunder efter vilken en leveransåtgärd inte längre ska förberedas.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
  <tr> 
   <td> unixScript<br /> </td> 
   <td> Unix-skript kördes av övervakningstjänsten.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> winScript<br /> </td> 
   <td> Windows-skript som ska köras av övervakningstjänsten.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## ooconv {#ooconv}

Här är de olika parametrarna för **ooconv** nod. Detta är konfigurationen för dokumentkonverteringsservern.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxConversions<br /> </td> 
   <td> Maximalt antal konverteringar som en OpenOffice-server får utföra. Servern startas om efter det här numret.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxServerIdleSec<br /> </td> 
   <td> Maximal inaktiv tid för OpenOffice-servern innan den tvångsavslutas.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 7200<br /> </td> 
  </tr> 
  <tr> 
   <td> portRange<br /> </td> 
   <td> Intervall för portar som OpenOffice-servrarna lyssnar på.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 8101-8110<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL för dokumentkonverteringsservern.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> http://localhost:8080/nl/jsp/ooconv.jsp'<br /> </td> 
  </tr> 
 </tbody> 
</table>

## proxyConfig {#proxyconfig}

Här är de olika parametrarna för **proxyConfig** nod. Detta är konfigurationen av proxyparametrar.

Mer information finns i [Konfiguration för proxyanslutning](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> aktiverad<br /> </td> 
   <td> Använd en proxyserver.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> åsidosätta<br /> </td> 
   <td> Undantag: förteckning över adresser för vilka proxyparametrar ska ignoreras.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> localhost* <br /> </td> 
  </tr> 
  <tr> 
   <td> useSingleProxy<br /> </td> 
   <td> Unik proxyserver: använd samma konfiguration för alla typer av proxyservrar.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### HTTP-proxy/säker proxy {#http-proxy---secure-proxy-}

I **proxyConfig > HTTP-proxy/säker proxy** -nod konfigurerar du följande parametrar.

Mer information finns i [Konfiguration för proxyanslutning](file-res-management.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> adress<br /> </td> 
   <td> Proxyserverns adress<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
  <tr> 
   <td> inloggning<br /> </td> 
   <td> Inloggning för anslutning till proxyservern<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
  <tr> 
   <td> lösenord<br /> </td> 
   <td> Lösenord för anslutningen till proxyservern<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Proxyserverport<br /> </td> 
   <td> Kort<br /> </td> 
  </tr> 
 </tbody> 
</table>

## threadPool {#threadpool}

Här är de olika parametrarna för **threadPool** nod.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxThreadCount<br /> </td> 
   <td> Högsta antal trådar i poolen. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## urlPermission {#urlpermission}

Här är de olika parametrarna för **urlPermission** nod. Det här är listan med URL:er som JavaScript-koden har åtkomst till.

Lista över domäner och reguljära uttryck som anger om en URL som påträffas i Javascript-koden kan användas eller inte av Adobe Campaign-servern.

Om det inte går att hitta URL:en utförs standardåtgärden enligt det angivna standardläget.

Mer information finns i [Skydd av utgående anslutning](../../installation/using/configuring-campaign-server.md#url-permissions).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> åtgärd<br /> </td> 
   <td> Standardåtgärd om URL:en inte finns i den auktoriserade listan (uppräkning). Möjliga värden är 'ignore' (auktorisera utan varningsmeddelande, detta kräver att skyddet inaktiveras), 'warn' (auktorisera och skicka ett varningsmeddelande) och 'deny' (förhindra åtkomst till URL:en).<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> neka<br /> </td> 
  </tr> 
  <tr> 
   <td> debugTrace<br /> </td> 
   <td> Felsökningsspårning av URL-markeringsmekanismen: skapar ytterligare meddelanden under URL-verifieringsprocessen.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

## cusHeaders {#cusheaders}

Med den här noden kan du lägga till specifika huvuden i begäranden som utförs när en fil överförs från en extern server. CND (Content Delivery Networks) kan begära en specifik rubrik för att lita på den som gjorde begäran. Dessa rubriker kan användas för att förbättra förtroendet för Campaign-begäranden, särskilt när skräddarsydda dokument laddas ned för varje mottagare i leveranssteget. Ett stort antal resurshämtningsbegäranden kan tolkas som en DDos-attack. Med dnsPattern kan du ange specifika rubriknamn och värden för olika CDN:er utifrån deras domännamn.

```
  <!-- List of custom headers added to request. 
         -->
    <cusHeaders>

    <!-- Pattern of DNS name or domain 
         value :  dnsPattern: All or part of the URL's domain to verify, * is a wild card Default:  -->
      <dnsPattern value="">

    <!-- Header Name and Value 
           headerName :  Header Name 
           headerValue :  Header Value -->
        <headerDef headerName="" headerValue=""/>

      </dnsPattern>

    </cusHeaders> 
```

### url {#url}

Lägg till en **url** nod med följande parametrar:

Mer information finns i [Skydd av utgående anslutning](../../installation/using/configuring-campaign-server.md#url-permissions).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dnsSuffix<br /> </td> 
   <td> Domännamnet, eller domänens överordnade, som berörs av URL:en: hela eller en del av URL:ens domän som ska verifieras, för att påskynda verifieringen. URL:en verifieras endast med avseende på det reguljära uttrycket om dess domän innehåller dsnSuffix.<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
  <tr> 
   <td> urlRegEx<br /> </td> 
   <td> Reguljärt uttryck för att förfina verifiering av URL:er som tillhör den här domänen: reguljärt uttryck som URL:en måste verifiera, om det motsvarar dnsSuffix.<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
 </tbody> 
</table>

Om en post uppfyller **dnsSuffix** men inte **urlRegEx**, undersöks följande post.

Om du till exempel vill tillåta åtkomst till alla URL:er för domänen business.com kan vi definiera två poster:

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;http://.&#42;&quot;

och

dnsSuffix=&quot;business.com&quot; urlRegEx=&quot;https://.&#42;&quot;

Här är standardkonfigurationen:

```
<url dnsSuffix="api.omniture.com" urlRegEx="https://api.omniture.com/genesis/i/3.1.*"   />
<url dnsSuffix="omniture.com" urlRegEx="https://api[1-5].omniture.com/genesis/i/3.1.*"  />
<url dnsSuffix="marketing.adobe.com"                     urlRegEx="https://.*"                                    />
<url dnsSuffix="fcm.googleapis.com"                      urlRegEx="https://fcm.googleapis.com/fcm/send.*"       />
<url dnsSuffix="graph.facebook.com"                      urlRegEx="https://.*"                                    />
<url dnsSuffix="api.line.me"                             urlRegEx="https://api.line.me/.*"                      />
<url dnsSuffix="api.twitter.com"                         urlRegEx="https://api.twitter.com/1.1.*"              />
<url dnsSuffix="adobeid-na1.services.adobe.com"          urlRegEx="https://.*"                                    />
<url dnsSuffix="adobeid-na1-stg1.services.adobe.com"     urlRegEx="https://.*"                                    />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nms/jsp/.*"              />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/nl/jsp/.*"               />
<url dnsSuffix="localhost"                               urlRegEx="http://localhost:8080/xtk/jsp/.*"              />
```

## xtkJobs {#xtkjobs}

Här är de olika parametrarna för **xtkJobs** nod. Det här är konfigurationen för serverjobben.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Uppdateringsperiod för minnesstatus för serverbearbetning (i ms).<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## arkivering {#archiving}

Här är de olika parametrarna för **arkivering** nod. Detta är konfigurationen för de slutförda arkiveringsåtgärderna i bakgrunden.

Mer information finns i [Aktivera e-postarkivering (lokalt)](../../installation/using/email-archiving.md#activating-email-archiving--on-premise-).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> obtainLimit<br /> </td> 
   <td> Antal EML som ska bearbetas samtidigt<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> archivingType<br /> </td> 
   <td> Arkiveringsstrategi för skickade meddelanden (uppräkning). Möjliga värden är '0' (ingen arkivering) och '1' (överför arkivering av skickade meddelanden till en SMTP-server).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparametrar<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisk start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> compressBatchSize<br /> </td> 
   <td> Storlek på ett komprimerat arkiv: maximalt antal filer i ett komprimerat arkiv.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 10000<br /> </td> 
  </tr> 
  <tr> 
   <td> compressionFormat<br /> </td> 
   <td> Komprimeringsformat som används vid arkivering (uppräkning). Möjliga värden är '0' (ingen komprimering) och '1' (komprimera skickade meddelanden med zip-format).<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationDelay<br /> </td> 
   <td> Fördröjning före automatisk arkivering av obearbetade e-postmeddelanden: antal dagar innan obearbetade e-postmeddelanden arkiveras.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID för JavaScript som ska köras när processen startas.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en viss process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en given process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollDelay<br /> </td> 
   <td> Fördröjning (i sekunder) mellan varje uppdateringshändelse.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tid på dagen då processen startas om automatiskt. Se <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisk processomstart</a>.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeArchivesDelay<br /> </td> 
   <td> Antal dagar innan obearbetade e-postmeddelanden tas bort.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 7<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioritet i början. Moduler med låg prioritet startas först och stoppas senast. Systemmodulen måste därför ha prioriteten 0.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpBccAddress<br /> </td> 
   <td> Arkiverar måldestination<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpEnableTLS<br /> </td> 
   <td> Aktivera stöd för SMTPS: aktiverar leveransen av e-post i felsäkert läge (STARTTLS/SMTPS) när det stöds av fjärrservern.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpNbConnection<br /> </td> 
   <td> Antal anslutningar till den arkiverande SMTP-servern.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayAddress<br /> </td> 
   <td> Kommaavgränsad lista med DNS-namn eller IP-adresser för SMTP-relä som ska användas. <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> smtpRelayPort<br /> </td> 
   <td> SMTP-serverns IP-port.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

## inMail {#inmail}

Här är de olika parametrarna för **inMail** nod. Detta är konfigurationen för modulen för inkommande e-posthantering.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparametrar<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisk start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> checkInstanceName<br /> </td> 
   <td> Verifiera instansnamn: Om true måste namnet på Adobe Campaign-instansen i Message-ID-rubrikerna vara detsamma som för den aktuella instansen. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> defaultForwardAddress<br /> </td> 
   <td> Vidarebefordringsadress: standardadress för e-postöverföring bearbetas inte av en regel. <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> errorForwardAddress<br /> </td> 
   <td> Adress för fel: standardadress som används för att överföra ogiltiga e-postmeddelanden (felaktig MIME-kodning). <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> ignoreSize<br /> </td> 
   <td> Ignorera meddelandestorlek: används för att ignorera storleken på ett meddelande som returneras av POP3-servrar. I det här fallet förväntar sig modulen"." i slutet av meddelandena. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> inMailPeriodSec<br /> </td> 
   <td> Meddelandeläsperiod: avsökningsfrekvens för meddelandekö.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID för JavaScript som ska köras när processen startas.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxBroadLog<br /> </td> 
   <td> Maximalt antal loggar som ska uppdateras: definierar maximalt antal loggmeddelanden som ska sparas i minnet innan databasen uppdateras.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerSession<br /> </td> 
   <td> Maximalt antal meddelanden som ska läsas under POP3-sessionen.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 200<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en viss process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en given process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionTTLSec<br /> </td> 
   <td> Sessionslängd: maximal varaktighet för meddelandebearbetningssession.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popMailPeriodSec<br /> </td> 
   <td> POP3-avsökningsperiod<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> popQueueSize<br /> </td> 
   <td> Köstorlek för lästa meddelanden<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> popTimeoutSec<br /> </td> 
   <td> Tidsgräns för kommunikation med POP3-servern. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tid på dagen då processen startas om automatiskt. Se <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisk processomstart</a>.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriodSec<br /> </td> 
   <td> Frekvens för återinläsning av databas för konton som ska avsökas.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioritet i början. Moduler med låg prioritet startas först och stoppas senast. Systemmodulen måste därför ha prioriteten 0.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

### msgDump {#msgdump}

I **inMail > msgDump** -nod konfigurerar du följande parametrar. Detta är konfigurationen för dumpen av bearbetade meddelanden.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dump<br /> </td> 
   <td> Spara alla inkommande meddelanden i textformat. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> msgPath<br /> </td> 
   <td> Sökväg till meddelandedumpen.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> /tmp/inMail<br /> </td> 
  </tr> 
 </tbody> 
</table>

## interactiond {#interactiond}

Här är de olika parametrarna för **interactiond** nod. Detta är konfigurationen av skrivdaemon för inkommande interaktionshändelser.

Mer information finns i [Interaktion - databuffert](../../installation/using/interaction-data-buffer.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparametrar<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisk start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> callDataSize<br /> </td> 
   <td> Max. antalet tecken som lagras i det delade minnet för anropsdata.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID för JavaScript som ska köras när processen startas<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en viss process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en given process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedEnentries<br /> </td> 
   <td> Max. antal händelser som lagras i det delade minnet.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> nextOffersSize<br /> </td> 
   <td> Maximalt antal berättigade erbjudanden sorterade direkt efter offerter som ska lagras för statistik.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tid på dagen då processen startas om automatiskt. Se <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisk processomstart</a>.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioritet i början. Moduler med låg prioritet startas först och stoppas senast. Systemmodulen måste därför ha prioriteten 0.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> statsPeriod<br /> </td> 
   <td> Samlingstid i sekunder för svarstidsstatistik. 0 betyder att statistisk lagring har inaktiverats.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> targetKeySize<br /> </td> 
   <td> Max. antal tecken som lagras i det delade minnet för att identifiera individer.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 16<br /> </td> 
  </tr> 
 </tbody> 
</table>

## mta {#mta}

Här är de olika parametrarna för **mta** nod. Detta är konfigurationen för leveransagenter.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparametrar<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> '-tracefilter:nlmta' <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisk start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataLogPath<br /> </td> 
   <td> Spara sökvägen för skickade e-postmeddelanden: Om den inte är tom sparas sökvägen där alla källfiler för skickade e-postmeddelanden sparas. <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> debugPath<br /> </td> 
   <td> Dumpa katalog:iOm den inte är tom kopierar du MIME-kuvert med skickade e-postmeddelanden i den här katalogen. Används för felsökning. <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> dnsRequestLogDelayMs<br /> </td> 
   <td> Fördröjning för DNS-frågeloggar: tid i millisekunder för att visa loggarna.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> errorPeriodSec<br /> </td> 
   <td> Felstatistikfrekvens: tid mellan generering av statistik och lagring i databasen. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID för JavaScript som ska köras när processen startas.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logEmailErrors<br /> </td> 
   <td> Generera felstatistik och lagra dem i databasen.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> logLevel<br /> </td> 
   <td> Visa loggmeddelandenas nivå. Allvarlighetsnivån för loggarna som skrivits i databasen. Loggmeddelanden som genereras av MTA skrivs inte alltid i databasen. Med den här parametern kan du definiera från vilken nivå ett meddelande ska skrivas i databasen. Om du definierar nivå 2 skrivs även meddelanden på nivå 1 och 0, medan endast meddelanden på nivå 1 och 0 skrivs om du definierar nivå 1. Möjliga värden är: 0 (fel), 1 (varning), 2 (info)<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMemoryMb<br /> </td> 
   <td> Maximal minnesstorlek (i MB) som en dataprocess kan använda. Över denna gräns startas processen om så att minnet som används frigörs till systemet.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en viss process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en given process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> minConnectionsToLog<br /> </td> 
   <td> Tröskelvärde för anslutning som ska beaktas. Felstatistik genereras inte för en angiven sökväg om det totala antalet anslutningar för den period som anges av errorPeriodSec är strikt lägre än tröskelvärdet.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> minErrorsToLog<br /> </td> 
   <td> Feltröskel att ta hänsyn till: Felstatistik genereras inte för en angiven sökväg om det totala antalet fel för den period som anges av errorPeriodSec är strikt lägre än tröskeln.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> minMessagesToLog<br /> </td> 
   <td> Tröskelvärde för meddelanden som ska beaktas. Felstatistik genereras inte för en angiven sökväg om det totala antalet meddelanden som skickats för den period som anges av errorPeriodSec är strikt lägre än tröskelvärdet.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Meddelanderelä: HostName:Port som används för att vidarebefordra meddelanden.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tid på dagen då processen startas om automatiskt. Se <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisk processomstart</a>.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeDataLogDelay<br /> </td> 
   <td> Fördröjning innan arkiverade e-postmeddelanden tas bort: antal dagar innan arkiverade e-postmeddelanden i den katalog som anges i dataLogPath tas bort.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 15<br /> </td> 
  </tr> 
  <tr> 
   <td> retryLostMessages<br /> </td> 
   <td> Försök med förlorade meddelanden igen: delar av leveranser provas igen om den underordnade processen är död.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioritet i början. Moduler med låg prioritet startas först och stoppas senast. Systemmodulen måste därför ha prioriteten 0.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> signEmailLinks<br /> </td> 
   <td> Aktivera signaturmekanismen. Detta förbättrar säkerheten vid spårning av länkar i e-post.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr>
  <tr> 
   <td> statServerAddress<br /> </td> 
   <td> Adress till servern för leveransstatistik, angiven som 
    &lt;dns or="" ip=""&gt; 
      <code>[</code>: 
     &lt;port&gt; 
       <code>]</code>. Se 
      <a href="../../installation/using/email-deliverability.md#coordinates-of-the-statistics-server" target="_blank">Statistikserverns koordinater</a>. 
      <br /> 
     </td> 
   <td> Sträng<br /> </td> 
   <td> Om inget anges är standardporten 7777.<br /> </td> 
  </tr> 
  <tr> 
   <td> startServerTLSSupport<br /> </td> 
   <td> Aktivera TLS per domän: aktiverar TLS som kan konfigureras av MX (kräver en uppdaterad statistikserver).<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true <br /> </td> 
  </tr> 
  <!--tr> 
   <td> statServerVersion<br /> </td> 
   <td> Protocol version used: communication protocol version (1 for a v5.11 and 6.0.2 server, 2 for a v6.1 server).<br /> </td> 
   <td> String<br /> </td> 
   <td> If undefined, the latest version is used. <br /> </td> 
  </tr--> 
  <tr> 
   <td> useMomentum<br /> </td> 
   <td> Om värdet är "true" använder instansen <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">Förbättrad MTA</a>.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td>b 
  </tr>
  <tr> 
   <td> verifyMode<br /> </td> 
   <td> Verifieringsläge: aktiverar verifieringsläget (ingen fysisk överföring av meddelanden, används för simulering och tester).<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> workingPath<br /> </td> 
   <td> Arbetskatalog: plats för tillfälliga filer som används av MTA för att kommunicera med dess underordnade processer.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/var/$(INSTANCE_NAME)/mta/' <br /> </td> 
  </tr> 
  <tr> 
   <td> xMailer<br /> </td> 
   <td> X-Mailer-fält: värdet för fältet X-Mailer i SMTP-e-posthuvudet.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 'nlserver, Build $(PRODUCT_VERSION)'<br /> </td> 
  </tr>  
 </tbody> 
</table>

### cache {#cache}

I **cache** -nod konfigurerar du följande parametrar. Detta är den lokala filcachekonfigurationen.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> maxPeriodSec<br /> </td> 
   <td> Återanvänds efter: punkt, uttryckt i sekunder, efter vilken filen automatiskt tas bort från cachen för att frigöra lagringsutrymme.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 244800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSizeOnDiskMb<br /> </td> 
   <td> Maximal cachestorlek (MB).<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1024<br /> </td> 
  </tr> 
  <tr> 
   <td> purgePeriodSec<br /> </td> 
   <td> Tömningsfrekvens: period i sekunder mellan körningar av cacheminnets tömningsmekanism.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 3600<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relä {#relay}

I **mta > relay** -nod konfigurerar du följande parametrar. Det här är konfigurationen för e-postservern för meddelandeleveransen.

Listan hanteras på samma sätt som en lista över MX som returneras av en MX DNS-fråga. Vanligtvis används den första MX så länge den är tillgänglig, sedan används nästa så vidare.

Mer information finns i [SMTP-relä](../../installation/using/configuring-campaign-server.md#smtp-relay).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> adress<br /> </td> 
   <td> Kommaavgränsad lista med DNS-namn eller IP-adresser för SMTP-relä som ska användas. <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> SMTP-serverns IP-port.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
 </tbody> 
</table>

### master {#master}

I **mta > master** -nod konfigurerar du följande parametrar. Detta är huvudserverns konfiguration.

Mer information finns i [section](../../installation/using/configuring-campaign-server.md#mta-child-processes).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Databasavsökningsfrekvens för de jobb som ska levereras. Detta värde anger databassökningsfrekvensen (i sekunder). För att få en lista över jobb som väntar på leverans kommer MTA att regelbundet avsöka databasen. Om inget jobb väntar definieras avsökningsperioden av det här värdet. Om ett jobb har överförts till en underordnad server, minskas annars avsökningstiden automatiskt till en sekund så att ett nytt jobb kan bearbetas igen så snart som möjligt, dvs. så snart en underordnad server är tillgänglig igen. Detta innebär inte att databasfrågan kommer att utföras varje sekund tills en underordnad server blir tillgänglig igen. En databasåtkomst sker faktiskt bara när minst en underordnad server blir tillgänglig.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBaseRetryDelaySec<br /> </td> 
   <td> Väntar på period efter ett databasanslutningsfel. Ett databasanslutningsfel orsakas vanligtvis av själva databasservern. Servern kan också stoppas i underhållssyfte, till exempel. Parametern DataBaseRetryDelay definierar varaktigheten mellan två anslutningsförsök om en databasanslutning misslyckas.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> domainKeysReloadPeriodSec<br /> </td> 
   <td> Giltighetsperiod för cachen med privata nycklar (DomainKeys). Privata nycklar som används för att signera e-postmeddelanden efter DomainKeys-rekommendationen (http://antispam.yahoo.com/domainkeys) lagras som alternativ i databasen. Parametern domainKeysReloadPeriodSec definierar hur många sekunder som MTA kan behålla dessa nycklar i ett cacheminne. Efter den här fördröjningen måste alla nycklar läsas in från databasen igen.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSpareServers<br /> </td> 
   <td> Maximalt antal underordnade servrar. Representerar det maximala antalet servrar som körs. Vi rekommenderar att du begränsar det här antalet till ett optimalt värde som är kompatibelt med serverns minnesresurser. Detta kan kontrolleras under en leverans. Det använda minnet bör inte överstiga en tredjedel av det tillgängliga fysiska minnet, annars används växlingen. Se <a href="../../installation/using/configuring-campaign-server.md#mta-child-processes" target="_blank">MTA-underprocesser</a>.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> minSpareServers<br /> </td> 
   <td> Minsta antal underordnade servrar. MTA försöker hålla åtminstone så många servrar igång. Om det är mindre startas nya servrar om varje sekund tills det här värdet uppnås.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> startSpareServers<br /> </td> 
   <td> Antal underordnade servrar vid start. Antalet underordnade servrar övervakas dynamiskt. När MTA startas skapas så många underordnade servrar som det här värdet anger. I vanliga fall går det inte att starta underordnade servrar snabbare än en server per sekund för att spara värdresurser. När MTA startas åsidosätts dock den här begränsningen så att underordnade servrar blir tillgängliga så snart som möjligt.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
 </tbody> 
</table>

### child {#child}

I **mta > child** -nod konfigurerar du följande parametrar. Detta är konfigurationen för underordnade servrar.

Mer information finns i [Optimering av e-postutskick](../../installation/using/email-deliverability.md#email-sending-optimization).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> extraArgs<br /> </td> 
   <td> Valfria kommandoradsargument <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> idleChildTimeoutSec<br /> </td> 
   <td> Timeout tills underordnade inaktiva servrar stoppas. Om en underordnad server har en inaktiv tid som är större än den här parametern tar den automatiskt slut för att frigöra värdresurser.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> maxAgeSec<br /> </td> 
   <td> Maximal kvarhållningstid för meddelanden. Om ett förberett meddelande inte kunde skickas på grund av strypning eller inte kunde ansluta till mål-MTA, överges meddelandet och kommer att bearbetas vid nästa försök.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxGCMConnectPerChild<br /> </td> 
   <td> Maximalt antal parallella Http-begäranden till FCM som initierats av varje underordnad server.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 8<br /> </td> 
  </tr> 
  <tr> 
   <td> maxMsgPerChild<br /> </td> 
   <td> Maximalt antal meddelanden per underordnad server. Varje underordnad MTA behandlar detta antal meddelanden och dör. Det är viktigt att ange ett tal så att minnes- eller resursläckor i MTA är ofarliga (vanligen några tusen). Även om det inte finns några kända minnesläckor i MTA-koden är de inbäddade JavaScript- och XSL-motorerna inte helt tillförlitliga.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 5000000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWaitMessages<br /> </td> 
   <td> Väntande meddelanden: maximalt antal meddelanden som väntar på att levereras i minnet. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> 2000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxWorkingSetMb<br /> </td> 
   <td> Maximal minnesstorlek (i MB) som en underordnad process kan använda. Processen stoppas ovanför denna gräns så att minnet som används frigörs till systemet. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> 128<br /> </td> 
  </tr> 
  <tr> 
   <td> soapConnectorTimeoutSec<br /> </td> 
   <td> Timeout (i sekunder) efter vilken en SOAP-anslutning för en leveranskontakt överges.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> startWithFirstMX<br /> </td> 
   <td> Börja alltid med högsta prioritet MX.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Maximalt antal försök i följd när programmet återupptas.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 48<br /> </td> 
  </tr> 
 </tbody> 
</table>

I **mta > child > smtp** -nod konfigurerar du följande parametrar. Detta är konfigurationen för SMTP-sessioner.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enableTLS<br /> </td> 
   <td> Aktiverar leveransen av e-postmeddelanden i felsäkert läge (STARTTLS/SMTPS) när det stöds av fjärrservern.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> idleSessionTimeoutSec<br /> </td> 
   <td> Tidsgräns för inaktiv session. Den här parametern används bara om sessionen återanvänds för att skicka flera meddelanden till en viss domän. När MTA har slutfört meddelandeöverföringen stängs inte den SMTP-session som den har använt systematiskt. Om ett meddelande är klart att skickas för samma domän återanvänds samma SMTP-session och därför stängs inte sessionen automatiskt. Med parametern IdleSessionTimeout kan du definiera den tid under vilken en SMTP-session kan vara aktiv och vänta på ett annat meddelande. När tiden har gått ut stängs sessionen automatiskt.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> initialDelaySec<br /> </td> 
   <td> Inledande fördröjning innan anslutningen försöker igen. Fördröjningen dubbleras varje gång anslutningen misslyckas.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSessionsPerChild<br /> </td> 
   <td> Högsta antal SMTP-sessioner per underordnad server. MTA initierar en SMTP-anslutning med mottagaren MTA för att leverera ett meddelande. Det maximala antalet samtidiga och aktiva SMTP-sessioner för en viss underordnad server begränsas av det här värdet. Om du multiplicerar det här värdet med maxSpareServers får du det maximala antalet meddelanden som kan bearbetas samtidigt av en viss underordnad server.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

I **mta > child > smtp > IPAfinity** -nod konfigurerar du följande parametrar. Detta är konfigurationen av hanteringen av tillhörigheter med IP-adresser för optimerad utgående SMTP-trafik.

Mer information finns i [Lista över IP-adresser som ska användas](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use) och [Hantera utgående SMTP-trafik med tillhörigheter](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> localDomain<br /> </td> 
   <td> Domännamn: lokalt domännamn länkat till IP-adressen. Används när ett SMTP HELO-kommando utfärdas.<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Logiskt namn: namn som är länkade till tillhörigheten av användare. Namn avgränsas med semikolon.<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
 </tbody> 
</table>

I **mta > child > smtp > IP** -nod konfigurerar du följande parametrar.

Mer information finns i [Lista över IP-adresser som ska användas](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> adress<br /> </td> 
   <td> Associerad fysisk adress. Exempel: "192.168.0.1"<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
  <tr> 
   <td> publicId<br /> </td> 
   <td> Associerat ID för offentlig adress. Används som nyckel för statistikservern. Måste vara numeriskt. Se det här <a href="../../installation/using/email-deliverability.md#managing-ip-addresses">section</a>.<br /> </td> 
   <td> Lång<br /> </td> 
  </tr> 
  <tr> 
   <td> vikt<br /> </td> 
   <td> Anger användningsfrekvensen för denna IP i förhållande till andra IP-adresser (större vikter leder till högre frekvenser).<br /> </td> 
   <td> Lång<br /> </td> 
  </tr> 
  <tr> 
   <td> includeDomains<br /> </td> 
   <td> Kommaavgränsad lista med domänmasker som ska inkluderas.<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
  <tr> 
   <td> excludeDomains<br /> </td> 
   <td> Kommaavgränsad lista med domänmasker som ska uteslutas.<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
  <tr> 
   <td> heloHost<br /> </td> 
   <td> Datornamn länkat till IP-adressen. Används när ett SMTP HELO-kommando utfärdas.<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
 </tbody> 
</table>

## nmac {#nmac}

Här är de olika parametrarna för **nmac** nod. Det här är konfigurationen för push-meddelandeleveranser.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> useHTTPProxy<br /> </td> 
   <td> Använd HTTP-proxy som definierats i shared/proxyHTTP. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### relä {#relay-1}

Här är de olika parametrarna för **nmac > relay** nod. Detta konfigurerar användningen av ett relä för meddelandeleveransen (iOS http2-anslutning).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> adress<br /> </td> 
   <td> DNS-adress eller namn på relä som ska användas. <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Reläport<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 443<br /> </td> 
  </tr> 
  <tr> 
   <td> trustedCertsChain<br /> </td> 
   <td> Certifikatkedja (PEM-fil). Användbar när du använder en modellserver.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

## rörlig {#pipelined}

Här är de olika parametrarna för **rörlig** nod. Det här är konfigurationen för händelsebearbetningsmodulen för Pipeline-tjänster.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> appName<br /> </td> 
   <td> Namnet på programmet som genereras i Developer-anslutningen när den offentliga nyckeln sparas. <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparametrar<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> authGatewayEndpoint<br /> </td> 
   <td> URL för att hämta en gatewaytoken.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> https://api.omniture.com' <br /> </td> 
  </tr> 
  <tr> 
   <td> authPrivateKey<br /> </td> 
   <td> Privat nyckel för att erhålla tokens (krypterad i AES med alternativet XtkKey).<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisk start <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> disableAuth<br /> </td> 
   <td> Inaktivera autentisering: anslut till Pipeline-tjänster utan autentisering. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> 2<br /> </td> 
  </tr> 
  <tr> 
   <td> discoverPipelineEndpoint<br /> </td> 
   <td> URL som identifierar URL:en för Pipeline Services.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> https://producer-pipeline-pnw.adobe.net'<br /> </td> 
  </tr> 
  <tr> 
   <td> dumpStatePeriodSec<br /> </td> 
   <td> Period för att spara status: den frekvens med vilken processens interna information sparas i en fil. Inaktiv om 0. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> 0<br /> </td> 
  </tr> 
  <tr> 
   <td> forceradPipelineEndpoint<br /> </td> 
   <td> Avlyssna URL: tvinga avlyssnings-URL:en för Pipeline Services. <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID för JavaScript som ska köras när processen startas.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en viss process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en given process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> monitorServerPort<br /> </td> 
   <td> Statusserverport: HTTP-serverport som gör att du kan kontrollera processens status. Inaktiv om 0.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 7781<br /> </td> 
  </tr> 
  <tr> 
   <td> pointerFlushMessageCount<br /> </td> 
   <td> Pekaren lagras i databasen varje gång som det här antalet meddelanden bearbetas.<br /> </td> 
   <td> <br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> pekareFlushPeriodSec<br /> </td> 
   <td> Fördröjning innan pekaren lagras: pekaren lagras i databasen minst en gång under den här perioden (användbart vid låg aktivitet).<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tid på dagen då processen startas om automatiskt. Se <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisk processomstart</a>.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> processingJSThreads<br /> </td> 
   <td> Antal trådar för händelsebearbetning med en anpassad JavaScript-koppling.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> processingThreads<br /> </td> 
   <td> Antal trådar för händelsebearbetning.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 4<br /> </td> 
  </tr> 
  <tr> 
   <td> retryPeriodSec<br /> </td> 
   <td> Fördröjning mellan bearbetning om ett fel uppstår.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> retryValiditySec<br /> </td> 
   <td> Överge efter den här perioden: avbryt händelsen om bearbetningen fortfarande misslyckas efter den här perioden.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioritet i början. Moduler med låg prioritet startas först och stoppas senast. Systemmodulen måste därför ha prioriteten 0.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## reparation {#repair}

Här är de olika parametrarna för **reparation** nod. Detta är konfigurationen för databasreparationsmodulen.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> repairActionDelayMin<br /> </td> 
   <td> Reparationsmodul för leveransåtgärder: fördröjning (i minuter) efter vilken leveransåtgärder kan bearbetas av reparationsmodulen. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
 </tbody> 
</table>

## securityZone {#securityzone}

Här är de olika parametrarna för **securityZone** nod.

Mer information finns i [Definiera säkerhetszoner](../../installation/using/security-zones.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> allowDebug<br /> </td> 
   <td> Auktorisera felsökningsläge för webbprogram.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowEmptyPassword<br /> </td> 
   <td> Ge användaren behörighet att använda programmet utan lösenord.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowHTTP<br /> </td> 
   <td> Auktorisera användningen av HTTP för operatörsinloggning.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowSQLInjection<br /> </td> 
   <td> Auktorisera användningen av SQLDATA i uttryck.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> allowUserPassword<br /> </td> 
   <td> Auktorisera användar-/lösenordssessionstoken.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> label<br /> </td> 
   <td> Etikett<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Internt namn<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> sessionTokenOnly<br /> </td> 
   <td> Använd inte säkerhetstoken.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> showErrors<br /> </td> 
   <td> Visa felinformation<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

Här är standardkonfigurationen:

```
<securityZone allowDebug="false" allowHTTP="false" allowSQLInjection="false" label="Public Network" name="public">
  <subNetwork name="all" label="All addresses" mask="*" proxy="127.0.0.1, ::1"/>

  <securityZone allowDebug="true" allowHTTP="false" allowSQLInjection="false" label="Private Network (VPN)"
                name="vpn" showErrors="true">

    <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" allowUserPassword="false"
                  allowSQLInjection="false" label="Private Network (LAN)" name="lan" sessionTokenOnly="true"
                  showErrors="true">
      <subNetwork name="lan1" label="Lan 1" mask="192.168.0.0/16" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan2" label="Lan 2" mask="172.16.0.0/12" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan3" label="Lan 3" mask="10.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost" label="Localhost" mask="127.0.0.0/8" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6"  label="Lan (IPv6)" mask="fc00::/7" proxy="127.0.0.1, ::1"/>
      <subNetwork name="lan6b" label="Lan (IPv6)" mask="fe80::/10" proxy="127.0.0.1, ::1"/>
      <subNetwork name="localhost6" label="Localhost (IPv6)" mask="::1/128" proxy="127.0.0.1, ::1"/>
    </securityZone>

  </securityZone>
</securityZone>
```

### subNetwork {#subnetwork}

Här är de olika parametrarna för **securityZone > subNetwork** nod.

Mer information finns i [Definiera säkerhetszoner](../../installation/using/security-zones.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> label<br /> </td> 
   <td> Etikett<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> NewLabel()<br /> </td> 
  </tr> 
  <tr> 
   <td> mask<br /> </td> 
   <td> Mask eller adress<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> name<br /> </td> 
   <td> Internt namn<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> NewName() <br /> </td> 
  </tr> 
  <tr> 
   <td> proxy<br /> </td> 
   <td> Mask eller adress för (omvänd) proxy som används av det här undernätverket för att komma åt instansen. I det här fallet kommer rubriken"X-Forwarded-For" att testas i stället för den här proxyn.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 127.0.0.1 <br /> </td> 
  </tr> 
 </tbody> 
</table>

## sms {#sms}

Här är de olika parametrarna för **sms** nod. Detta är konfigurationen för den inkommande SMS-hanteringsmodulen.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparametrar<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisk start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataRetentionDays<br /> </td> 
   <td> Maximalt antal dagar som SMPP-anslutaren lagrar filer.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 60<br /> </td> 
  </tr> 
  <tr> 
   <td> dataSizeMo<br /> </td> 
   <td> Maximal storlek i MB för SMPP-arbetsfilerna.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 512<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID för JavaScript som ska köras när processen startas.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> keepAlivePeriod<br /> </td> 
   <td> Återkommande kontinuitetsram för session: max. i sekunder mellan två bildrutor för att meddela att mottagande session fortfarande är aktiverad.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 25<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en viss process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en given process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> pollPeriod<br /> </td> 
   <td> Sökfrekvens: avsökningsperiod för SMS-konto.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tid på dagen då processen startas om automatiskt. Se <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisk processomstart</a>.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> reloadPeriod<br /> </td> 
   <td> Frekvens för omladdning av konto: frekvens för återinläsning av databas för konton som ska avsökas.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioritet i början. Moduler med låg prioritet startas först och stoppas senast. Systemmodulen måste därför ha prioriteten 0.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> srReadDelay<br /> </td> 
   <td> Antal sekunder för sen SR-bearbetning: endast SR med ett återställningsdatum som är tidigare än den aktuella tiden minus den varaktighet i sekunder som anges av srReadDelay. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> 600<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Tidsgräns för kommunikation med SMS-gateway.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
 </tbody> 
</table>

### netsize {#netsize}

Här är de olika parametrarna för **sms > netsize** nod.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> netsizeConnectionTimeout<br /> </td> 
   <td> Timeout i sekunder vid anslutning med Netsize.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
 </tbody> 
</table>

## stat {#stat}

Här är de olika parametrarna för **stat** nod. Detta är konfigurationen för MTA-statistikmodulen.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparametrar<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisk start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID för JavaScript som ska köras när processen startas.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en viss process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en given process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> port<br /> </td> 
   <td> Serverlyssningsporten. Se det här <a href="../../installation/using/email-deliverability.md#definition-of-the-server-port">section</a>.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tid på dagen då processen startas om automatiskt. Se <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisk processomstart</a>.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioritet i början. Moduler med låg prioritet startas först och stoppas senast. Systemmodulen måste därför ha prioriteten 0.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## syslogd {#syslogd}

Här är de olika parametrarna för **syslogd** nod. Detta är konfigurationen för modulen Logghantering.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparametrar<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisk start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID för JavaScript som ska köras när processen startas.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxFileSizeMb<br /> </td> 
   <td> Maximal storlek i MB för en loggfil. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> maxNumberOfLoginsFiles<br /> </td> 
   <td> Maximalt antal logins.log-filer att behålla. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> 365<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en viss process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en given process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tid på dagen då processen startas om automatiskt. Se <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisk processomstart</a>.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioritet i början. Moduler med låg prioritet startas först och stoppas senast. Systemmodulen måste därför ha prioriteten 0.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>

## spårning {#tracking}

Här är de olika parametrarna för **spårning** nod. Detta är spårningsserverns konfiguration.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparametrar<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisk start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> blockRedirectForUnsignedTrackingLink<br /> </td> 
   <td> Inaktivera felformaterade URL:er som genererats från tidigare versioner.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> conversionPeriodSec<br /> </td> 
   <td> Konsolideringsperiod<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 300<br /> </td> 
  </tr> 
  <tr> 
   <td> dedupOpenPeriodMin<br /> </td> 
   <td> Ta bort öppningar: ta bort öppna spårningsloggar för att begränsa effekterna av förhandsgranskningar i e-postläsare som Outlook.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePercent<br /> </td> 
   <td> Ignorera upp till X % av felen: uppdatera inte spårningsindikatorer så länge som andelen journaler som inte redan har beaktats inte når det här värdet. <br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> errorIgnorePeriod<br /> </td> 
   <td> Uppdatera felindikatorer: maximal varaktighet innan felindikatorerna beräknas om.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> indikatornsVaraktighet<br /> </td> 
   <td> Beräkningsindikatorer under: varaktighet efter giltighetsdatumet för en leverans efter vilken konsoliderade indikatorer inte längre beräknas.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 2592000<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID för JavaScript som ska köras när processen startas <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> logCountPerRequest<br /> </td> 
   <td> Antal loggar som begärts av anrop till fjärrspårningsservern.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en viss process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en given process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceAPIKey<br /> </td> 
   <td> API-nyckel för slutpunktsintegrering för tjänsten i Phishbowl. Detta skyddar omdirigering av felformaterade URL:er som genereras från äldre byggen. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> phishbowlServiceEndpoint<br /> </td> 
   <td> Slutpunkt för integreringen av slutpunkten för tjänsten Phishbowl. Detta skyddar omdirigering av felformaterade URL:er som genereras från äldre byggen.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tid på dagen då processen startas om automatiskt. Se <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisk processomstart</a>.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioritet i början. Moduler med låg prioritet startas först och stoppas senast. Systemmodulen måste därför ha prioriteten 0.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePercent<br /> </td> 
   <td> Ignorera upp till X % av spårningen: uppdatera inte spårningsindikatorer så länge som förhållandet för journaler som inte redan har beaktats inte når det här värdet.<br /> </td> 
   <td> Byte<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingIgnorePeriod<br /> </td> 
   <td> Indikatorer för uppdateringsspårning: maximal varaktighet innan spårningsindikatorer beräknas om.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 86400<br /> </td> 
  </tr> 
  <tr> 
   <td> userAgentCacheSize<br /> </td> 
   <td> Storlek på cache för webbläsaridentifierare.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
 </tbody> 
</table>

## trackinglogd {#trackinglogd}

Här är de olika parametrarna för **trackinglogd** nod. Detta är konfigurationen för spårningsloggens skrivdaemon.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparametrar<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisk start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID för JavaScript som ska köras när processen startas <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxCreateFileRetry<br /> </td> 
   <td> Maximalt antal skrivförsök: maximalt antal filer som kan skapas vid skrivfel i loggfiler.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> maxLogsSizeOnDiskMb<br /> </td> 
   <td> Största loggstorlek: största utrymme som används av loggar på disk (i MB). Får inte vara mindre än 100 MB. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> 500<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en viss process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en given process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> maxSharedLogs<br /> </td> 
   <td> Maximalt antal loggar: maximalt antal loggar som lagras i delat minne. Kan inte vara mindre än 10000. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> 25000<br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tid på dagen då processen startas om automatiskt. Se <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisk processomstart</a>.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> purgeLogsPeriod<br /> </td> 
   <td> Antal loggar före tömning: antal loggar som infogats innan tömningen av loggfiler påbörjades. Får inte vara lägre än 50000.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 50000<br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioritet i början. Moduler med låg prioritet startas först och stoppas senast. Systemmodulen måste därför ha prioriteten 0.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> webTrackingParamSize<br /> </td> 
   <td> Maximalt antal tecken som har sparats i delat minne för extra parametrar för webbspårning.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 64<br /> </td> 
  </tr> 
 </tbody> 
</table>

## webb {#web}

Här är de olika parametrarna för **webb** nod. Detta är konfigurationen för webbmodulen.

Mer information finns i [section](configuring-campaign-server.md#default-port-for-tomcat).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> JVMOptions<br /> </td> 
   <td> Alternativ för den JVM som skickas som en sträng.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> MaxThreads<br /> </td> 
   <td> Maximalt antal trådar.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 75<br /> </td> 
  </tr> 
  <tr> 
   <td> MinSpareThreads<br /> </td> 
   <td> Minsta antal trådar.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 5<br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparametrar<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisk start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> controlPort<br /> </td> 
   <td> Tomcat-lyssningskontrollport: se <a href="configure-tomcat.md" target="_blank">Konfigurera Tomcat</a>.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 8005<br /> </td> 
  </tr> 
  <tr> 
   <td> httpPort<br /> </td> 
   <td> Tomcat HTTP-lyssningsporten: se <a href="configure-tomcat.md" target="_blank">Konfigurera Tomcat</a>.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 8080<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID för JavaScript som ska köras när processen startas.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxDeliveryQueueSize<br /> </td> 
   <td> Köns storlek för SubmitDelivery-anrop: maximalt antal SubmitDelivery SOAP-anrop som kan ställas i kö.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 50<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en viss process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en given process<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Meddelanderelä: HostName:Port som aktiverar vidarebefordran av meddelanden.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tid på dagen då processen startas om automatiskt. Se <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisk processomstart</a>.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioritet i början. Moduler med låg prioritet startas först och stoppas senast. Systemmodulen måste därför ha prioriteten 0.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
  <tr> 
   <td> startSoapRouterInModule<br /> </td> 
   <td> Starta SOAP-routern i modulläge.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
 </tbody> 
</table>

### jsp {#jsp}

Här är de olika parametrarna för **webb > jsp** nod. Detta är konfigurationen för parametrarna som används av JSP:erna.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debug<br /> </td> 
   <td> Körning av JSP i felsökningsläge eller inte.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> downloadPath<br /> </td> 
   <td> Hämtningsmapp: hämtningssökväg till installationsprogram för klientkonsolerna.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> '$(XTK_INSTALL_DIR)/datakit/nl/eng/jsp'<br /> </td> 
  </tr> 
  <tr> 
   <td> foFileName<br /> </td> 
   <td> Sökväg till .fo-fil.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> soapRouter<br /> </td> 
   <td> URL för SOAP-router (http://myserver/xxx, http://jni eller mailto:xxx).<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> http://jni'<br /> </td> 
  </tr> 
 </tbody> 
</table>

The **web > jsp > classpath** noden innehåller listan med alla klassökvägar som ska användas när JVM startas. Här är standardkonfigurationen:

```
'$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar
          $(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-coyote.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/annotations-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/catalina.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/websocket-api.jar
          $(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat7-websocket.jar
          $(XTK_INSTALL_DIR)/java/lib/pdfbox-2.0.4.jar
          $(XTK_INSTALL_DIR)/java/lib/FontBox-0.1.0.jar
          $(XTK_INSTALL_DIR)/java/lib/AGJavaEndpoint.22.jar
          $(XTK_INSTALL_DIR)/java/lib/NSGConstants.jar
          $(XTK_INSTALL_DIR)/java/lib/smpp.jar
          $(XTK_INSTALL_DIR)/java/lib/nlweb.jar
          $(XTK_INSTALL_DIR)/java/lib/jcaptcha-all.jar
          $(XTK_INSTALL_DIR)/java/lib/apns-1.0.0.Beta6-jar-with-dependencies.jar
          $(XTK_INSTALL_DIR)/java/lib/commons-collections-3.2.2.jar
          $(XTK_INSTALL_DIR)/java/lib/jcommon-1.0.16.jar
          $(XTK_INSTALL_DIR)/java/lib/jfreechart-1.0.13.jar
          $(XTK_INSTALL_DIR)/java/lib/barcode4j-light.jar
          $(XTK_INSTALL_DIR)/java/lib/zxing.jar
          $(XTK_INSTALL_DIR)/java/lib/raztec.jar
          $(XTK_INSTALL_DIR)/java/lib/gson-2.7.jar
          $(XTK_INSTALL_DIR)/java/lib/alpn-api-1.1.3.v20160715.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-all-4.1.6.Final.jar
          $(XTK_INSTALL_DIR)/java/lib/netty-tcnative-boringssl-static-1.1.33.Fork22.jar
          $(XTK_INSTALL_DIR)/java/lib/pushy-0.8.1.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-api-1.7.21.jar
          $(XTK_INSTALL_DIR)/java/lib/slf4j-simple-1.7.21.jar'
```

### jssp {#jssp}

Här är de olika parametrarna för **webb > jssp** nod. Detta är konfigurationen av parametrarna som används av JSSP:erna.

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> collectsGarbageAfterRequest<br /> </td> 
   <td> Aktiverar skräpinsamlaren för JavaScript-kontexten efter varje fråga.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeToLive<br /> </td> 
   <td> Maximalt antal sidor som hanteras av en JavaScript-kontext. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1000<br /> </td> 
  </tr> 
 </tbody> 
</table>

The **web > jsp > classpath** noden innehåller listan med alla klassökvägar som ska användas när JVM startas.

### relä {#relay-2}

Här är de olika parametrarna för **webb > relä** nod. Detta är konfigurationen av reläet för HTTP-begäranden mellan två zoner.

Mer information finns i [section](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> debugRelay<br /> </td> 
   <td> Starta HTTP-relämodulen på webbservern i felsökningsläge.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInAuthority<br /> </td> 
   <td> Otillåtna tecken (domän): lista över förbjudna tecken i avsnittet 'auktoritet' i en URI.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> '.?#@/:' <br /> </td> 
  </tr> 
  <tr> 
   <td> forbiddenCharsInPath<br /> </td> 
   <td> Otillåtna tecken (sökväg): lista med förbjudna tecken i sökvägsavsnittet i en URI.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> '?#/'<br /> </td> 
  </tr> 
  <tr> 
   <td> modDir<br /> </td> 
   <td> Värde för alternativet mod_dir i modulen: lista med filer som ska användas under en fråga i en mapp.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> index.md <br /> </td> 
  </tr> 
  <tr> 
   <td> startRelay<br /> </td> 
   <td> Starta HTTP-relämodulen.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> startRelayInModule<br /> </td> 
   <td> Starta HTTP-relämodulen i webbservern. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Vänta innan du tar bort bannlyst url.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> '60'<br /> </td> 
  </tr> 
 </tbody> 
</table>

Lägg till en **web > relay > url** noden för varje URL att vidarebefordra (infogningsordningen definierar prioritet) med följande parametrar.

Mer information finns i [Dynamisk sidsäkerhet och vidarebefordran](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) och [section](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IPMask<br /> </td> 
   <td> Auktoriserade IP-adresser: kommaseparerad lista över IP-källadresser som tillåts använda reläet för den här masken.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> neka<br /> </td> 
   <td> Neka åtkomst till dessa URL:er (returnera ett HTTP 403-fel)<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> hostMask<br /> </td> 
   <td> DNS-alias som ska vidarebefordras: kommaavgränsad lista över DNS-aliasmasker som ska vidarebefordras (t.ex. '*.adobe.com').<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> httpAllowed<br /> </td> 
   <td> HTTP-åtkomst auktoriserad oavsett säkerhetszon (som webApps). <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayHost<br /> </td> 
   <td> Lägg till ursprunglig värd: använd HTTP-huvudet "Host" i den ursprungliga begäran vid återutläggning.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> relayPath<br /> </td> 
   <td> Lägg till inledande URL-sökväg: lägg till den fullständiga sökvägen för URL:erna som ska skickas till målsidans URL. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> status<br /> </td> 
   <td> Synkroniseringsstatus för en offentlig resurs (uppräkning). Möjliga värden är 'normal' (normal körning), 'svartlist' (url som läggs till blockeringslista vid fel 404) och 'free' (filöverföring på reservserver om sådan finns).<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> normal<br /> </td> 
  </tr> 
  <tr> 
   <td> targetUrl<br /> </td> 
   <td> Målsidans URL: se <a href="configure-tomcat.md" target="_blank">Konfigurera Tomcat</a>.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> timeout<br /> </td> 
   <td> Maximal körningstid (i sekunder) för begäran som vidarebefordras.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> urlPath<br /> </td> 
   <td> Mask of URLs to relay (ex: /nl*, *.jsp).<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Här är standardkonfigurationen:

```
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true"
     status="normal" targetUrl="http://localhost:7781" timeout="" urlPath="/pipelined/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/view/*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="*ooconv.jsp*"/>
<url IPMask="" deny="true" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/res/*.jsp*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/sc.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/interactionProposal.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/zoneJson.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/barcode.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/captcha.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nms/jsp/webForm.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/xtk/jsp/zoneinfo.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="*/facebookCallback.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/m.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/nl/jsp/s.jsp"/>

<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nms/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/xtk/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/nl/jsp/*.jsp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="*.jssp"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="true" urlPath="/webApp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/report/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="blacklist" httpAllowed="false" urlPath="/jssp/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="false" urlPath="/strings/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/interaction/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/barcode/*"/>
<url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080"
     timeout="" status="normal" httpAllowed="true" urlPath="/lineImage/*"/>

<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/favicon.*"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.md"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.png"/>
<url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" targetUrl=""
     timeout="" status="spare" httpAllowed="true" urlPath="/*.jpg"/>
```

Lägg till en **web > relay > responseHeader** nod för varje HTTP-huvud som ska läggas till i svar som vidarebefordras till relä.

Mer information finns i [Hantera HTTP-huvuden](../../installation/using/configuring-campaign-server.md#managing-http-headers).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> name<br /> </td> 
   <td> Rubriknamn<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
  <tr> 
   <td> value<br /> </td> 
   <td> Huvudvärde <br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
 </tbody> 
</table>

Här är standardkonfigurationen:

```
<responseHeader name="X-XSS-Protection" value="1; mode=block"/>
```

### omdirigering {#redirection}

Här är de olika parametrarna för **webb > omdirigering** nod. Detta är konfigurationen för omdirigeringsmodulen.

Mer information finns i [section](../../installation/using/deploying-an-instance.md#synchronizing-public-resources).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> IMSOrgId<br /> </td> 
   <td> Organisations-ID: unik organisationsidentifierare i Adobe Experience Cloud, som särskilt används för VisitorID-tjänsten och IMS SSO. <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> P3PCompactPolicy<br /> </td> 
   <td> Värde som beskriver principen som används för permanenta cookies (kompatibelt med P3P-principformatet). <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> "CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"<br /> </td> 
  </tr> 
  <tr> 
   <td> cookieDomain<br /> </td> 
   <td> Kommaavgränsad lista över domäner som ska konfigureras för att explicit ange din domän att ange cookie. <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> databaseId<br /> </td> 
   <td> Databasidentifierare som är associerad med spårningsinstansen.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> defLogCount<br /> </td> 
   <td> Antal loggar per anrop: antal loggar som returneras som standard vid anrop av metoden GetTrackingLogs.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 30<br /> </td> 
  </tr> 
  <tr> 
   <td> expirationURL<br /> </td> 
   <td> Sidan för omdirigering som har upphört att gälla: URL:en till webbsidan används som standard av omdirigeringsservern när omdirigeringen för en leveransåtgärd har upphört att gälla.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxJobsInCache<br /> </td> 
   <td> Maximalt antal jobb: maximalt antal leveransåtgärder i cache. Får inte vara lägre än 50. <br /> </td> 
   <td> Lång<br /> </td> 
   <td> 100<br /> </td> 
  </tr> 
  <tr> 
   <td> showSourceIP<br /> </td> 
   <td> Om värdet är false är värdet för sourceIP i svaret som returneras av r/test en tom sträng. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirection<br /> </td> 
   <td> Starta omdirigeringstjänsten.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> startRedirectionInModule<br /> </td> 
   <td> Starta omdirigeringstjänsten i modulläge.<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> true<br /> </td> 
  </tr> 
  <tr> 
   <td> trackWebVisitors<br /> </td> 
   <td> Webbspårning: skapa loggar för de sidor som besökts av okända användare. <br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> trackingPassword<br /> </td> 
   <td> Lösenord som används av omdirigeringsservern.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

Här är de olika parametrarna för **web > redirection > freeServer** nod.

Mer information finns i [Spårning av överflödiga](../../installation/using/configuring-campaign-server.md#redundant-tracking).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> enabledIf<br /> </td> 
   <td> Ta hänsyn till om: spårningsservern tas med i beräkningen om uttrycket returnerar true. <br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> id<br /> </td> 
   <td> Namn<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 1<br /> </td> 
  </tr> 
  <tr> 
   <td> url<br /> </td> 
   <td> URL för extra omdirigeringsserver<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

### spamCheck {#spamcheck}

Här är de olika parametrarna för **web > spamCheck** nod. Det här är konfigurationen för utvärderingsparametrarna för e-postskräppostbedömning.

Mer information finns i [Konfigurera SpamAssassin](../../installation/using/configuring-spamassassin.md).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> kommando<br /> </td> 
   <td> Kommando som ska köras för att utvärdera skräppostbakgrundsmusiken i ett e-postmeddelande (t.ex. perl spamcheck.pl).<br /> </td> 
   <td> Sträng<br /> </td> 
  </tr> 
 </tbody> 
</table>

## wfserver {#wfserver}

Här är de olika parametrarna för **wfserver** nod. Detta är arbetsflödets processkonfiguration.

Mer information finns i [Arbetsflöden och tillhörighet med hög tillgänglighet](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

<table> 
 <thead> 
  <tr> 
   <th> Parameter </th> 
   <th> Beskrivning </th> 
   <th> Typ </th> 
   <th> Standardvärde </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> tillhörighet<br /> </td> 
   <td> Tillhörighet<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> args<br /> </td> 
   <td> Startparametrar<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> autoStart<br /> </td> 
   <td> Automatisk start<br /> </td> 
   <td> Boolean<br /> </td> 
   <td> false<br /> </td> 
  </tr> 
  <tr> 
   <td> dataBasePoolPeriodSec<br /> </td> 
   <td> Period<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 20<br /> </td> 
  </tr> 
  <tr> 
   <td> initScript<br /> </td> 
   <td> ID för JavaScript som ska köras när processen startas.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryAlertMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en viss process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1800<br /> </td> 
  </tr> 
  <tr> 
   <td> maxProcessMemoryWarningMb<br /> </td> 
   <td> Minnesförbrukningsvarning: varning om mängden RAM som förbrukas (i MB) av en given process.<br /> </td> 
   <td> Lång<br /> </td> 
   <td> 1600<br /> </td> 
  </tr> 
  <tr> 
   <td> notifRelay<br /> </td> 
   <td> Meddelanderelä: HostName:Port som aktiverar vidarebefordran av meddelanden.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> <br /> </td> 
  </tr> 
  <tr> 
   <td> processRestartTime<br /> </td> 
   <td> Tid på dagen då processen startas om automatiskt. Se <a href="../../installation/using/configuring-campaign-server.md#automatic-process-restart" target="_blank">Automatisk processomstart</a>.<br /> </td> 
   <td> Sträng<br /> </td> 
   <td> 06:00:00' <br /> </td> 
  </tr> 
  <tr> 
   <td> runLevel<br /> </td> 
   <td> Prioritet i början. Moduler med låg prioritet startas först och stoppas senast. Systemmodulen måste därför ha prioriteten 0.<br /> </td> 
   <td> Kort<br /> </td> 
   <td> 10<br /> </td> 
  </tr> 
 </tbody> 
</table>
