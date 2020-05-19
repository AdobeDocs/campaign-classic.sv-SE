---
title: Funktioner som tagits bort och ersatts av Campaign Classic
description: På den här sidan visas borttagna och borttagna funktioner i Adobe Campaign Classic
page-status-flag: never-activated
uuid: null
contentOwner: simonetn
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: campaign-classic-deprecated-features
discoiquuid: null
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be148d7cd55097b9014d2f4d3b095c65a5ca8c54
workflow-type: tm+mt
source-wordcount: '1389'
ht-degree: 0%

---


# Föråldrade och borttagna funktioner {#deprecated-and-removed-features}

Adobe utvärderar ständigt produktfunktioner för att identifiera äldre funktioner som bör ersättas med modernare alternativ för att förbättra det totala kundvärdet, alltid under noggrant övervägande av bakåtkompatibilitet. Eftersom Adobe Campaign Classic fungerar med verktyg från tredje part uppdateras kompatibiliteten regelbundet, så att endast de versioner som stöds kan implementeras. Versioner som inte längre är kompatibla med Adobe Campaign Classic visas nedan.

Följande regler gäller för att informera om den förestående borttagningen/ersättningen av Campaign Classic-funktioner:

* Föråldringsanmälan kommer först. Funktioner som inte längre används kan fortfarande vara tillgängliga för befintliga användare, men de kommer inte att förbättras ytterligare eller dokumenteras.
* Borttagning av föråldrade funktioner sker tidigast i följande version. Faktiskt måldatum för borttagning visas på den här sidan.

Den här processen ger kunderna minst en releasecykel för att anpassa implementeringen till en ny version eller en efterföljare till en borttagningsfunktion, innan den faktiska borttagningen.

>[!NOTE]
>Adobe Campaign-releaser och nya funktioner listas i [versionsinformationen](../../rn/using/latest-release.md).


## Föråldrade funktioner {#deprecated-features}

I det här avsnittet visas funktioner som har markerats som borttagna i de senaste Campaign Classic-versionerna.

I allmänhet är funktioner som ska tas bort i en framtida version först inaktuella, med ett alternativ. Dessa funktioner är inte längre tillgängliga för nya kunder i Campaign Classic, eller ska inte användas för nya implementeringar. De tas också bort från produktdokumentationen.

Kunderna rekommenderas att granska om de använder funktionen/funktionen i den aktuella distributionen och planera för att ändra implementeringen så att den använder det alternativ som finns. Se målets borttagningsdatum för att planera miljön och projektuppdateringarna utifrån detta.

### Adobe Campaign 18.6 {#ac-18-6-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Yta</strong></td>
   <td><strong>Funktion</strong></td> 
   <td><strong>Ersättning</strong></td> 
  </tr> 
   <tr> 
   <td>Javascript SDK Security<br> </td>
   <td>decryptString<br> </td>
   <td><p>Av säkerhetsskäl är <em>dekrypptString</em> API inte längre tillgängligt som standard för nya installationer.</p> 
   <p>I samband med en efteruppgradering till 18.6 (och senare) är denna API inte längre aktiverad och har ersatts av funktionen <em>dekrypptPassword</em> .</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Adobe Campaign 18.4 {#ac-18-4-release}

<table> 
 <tbody> 
  <tr> 
   <td><strong>Yta</strong></td>
   <td><strong>Funktion</strong></td> 
   <td><strong>Ersättning</strong></td> 
  </tr> 
   <tr> 
   <td>E-postarkivering<br> </td>
   <td>Filbaserad arkivering<br> </td>
   <td><p>E-postarkivering är nu tillgänglig via en dedikerad e-postadress för hemlig kopia. <a href="../../installation/using/email-archiving.md">Läs mer</a>.</p> 
   <p><em>Datum för målborttagning: Kampanjversion 20.2 - juni 2020</em></p><br> </td>
  </tr> 
   <tr> 
   <td>Leadhantering<br> </td>
   <td>Leads<br> </td>
   <td><p>Leads Management-paketet i Adobe Campaign Classic förenklade processen att bygga upp och underhålla hela livscykeln för leads. Liknande funktioner kan implementeras via andra interna arbetsflödesaktiviteter och datamodellsändringar.</p> 
   <p><em>Datum för målborttagning: Kampanjversion 20.2 - juni 2020</em></p><br> </td>
  </tr> 
 </tbody> 
</table>


## Undertryckt kompatibilitet {#deprecated-compatibility}

### Adobe Campaign 20.1-utgåvan {#compat-20-1-release}

Från och med den 20.1 februari är följande system föråldrat för Campaign Classic. Kompatibiliteten upphör i version 20.2 - juni 2020.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Yta</strong></td>
   <td><strong>Ersättning</strong></td> 
  </tr> 
   <tr> 
   <td>Campaign Classic Client Console 32 bitar<br> </td>
   <td><p>Campaign Classic Client Console 64 bitar</p><br> </td>
  </tr> 
 </tbody> 
</table>

### Adobe Campaign 19.2  {#compat-19-2-release}

Från och med hösten 19.2 används inte följande operativsystem för Campaign Classic. Kompatibiliteten upphör 2020 för EOY.

* Webbserver: Apache 2.2. [Läs mer](https://wiki.centos.org/About/Product)
* Operativsystem: CentOS 6. [Läs mer](https://wiki.centos.org/About/Product)

Se [kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) för att uppgradera till en nyare version eller gå till ett nytt system.

## Borttagna funktioner {#removed-features}

I det här avsnittet visas funktioner som har tagits bort från Campaign Classic.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Område - funktion</strong></td>
   <td><strong>Ersättning</strong></td> 
   <td><strong>Version</strong></td> 
  </tr> 
   <tr> 
   <td>Dokumentation för kampanj-API:er - jsapi.chm-fil<br> </td>
   <td>Campaign Classic-API:er finns nu på en dedikerad sida. Om du använde filen jsapi.chm bör du nu hänvisa till <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">den nya onlineversionen</a>.</td>
   <td>19.1</td>
  </tr> 
  <tr> 
   <td>Kampanjsamordning - prediktiv marknadsföring</td>
   <td>En stor del av de prediktiva marknadsföringsfunktionerna i Adobe Campaign Classic har varit konsumtionen av prediktiva modeller. Arbetsflödesaktiviteten för prediktiv marknadsföring kommer att tas bort i en kommande version, men Adobe Campaign kommer även i fortsättningen att stödja användningen av prediktiva modeller från externa källor via andra arbetsflödesaktiviteter.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Webbprogram - mikrowebbplatser</td>
   <td>Förbättra säkerheten genom att begränsa åtkomsten till endast dedikerade domäner i konfigurationsfiler för Adobe Campaign. Du kan fortfarande använda anpassade URL:er i Campaign genom att använda DNS-alias. <a href="https://helpx.adobe.com/campaign/kb/domain-name-delegation.html">Läs mer</a>.</td>
   <td>18.10</td>
  </tr> 
  <tr> 
   <td>Push-meddelanden - binär iOS-anslutning<br> </td>
   <td>Enligt Apples rekommendation kommer Adobe att ta bort den gamla binära iOS-kopplingen. Den mer kapabla och mer effektiva HTTP/2-baserade kopplingen är redan tillgänglig.</td>
   <td>18.10</td>
  </tr> 
   <tr> 
   <td>Mobilkanal - MMS- och WAP-push-meddelanden</td>
   <td>Kanalerna MMS och Wap Push är inte längre tillgängliga. Som ersättning kan du använda <a href="../../delivery/using/sms-channel.md">SMS</a> och <a href="../../delivery/using/about-mobile-app-channel.md">push</a> -leveranser.</td>
   <td>18.4</td>
  </tr> 
   <tr> 
   <td>Mobilkanal - LINE v1</td>
   <td>LINE Connect-paketet är inte längre tillgängligt för installation i Adobe Campaign Classic. Adobe rekommenderar att du använder det nya LINE Channel-paketet för att skicka LINE-meddelanden. <a href="../../delivery/using/line-channel.md">Läs mer</a>.</td>
   <td>18.4</td>
  </tr> 
 </tbody> 
</table>

## Kompatibilitetsslut {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic är kompatibelt med alla system och verktyg som listas i [kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html). När specifika versioner av dessa system och verktyg från tredje part når slutet av livscykeln med sina respektive skapare är Adobe Campaign inte längre kompatibelt med dessa versioner: de tillkännages som inaktuella och tas sedan bort från vår kompatibilitetsmatris i den följande produktversionen. Se till att du har de versioner av system som stöds i kompatibilitetsmatrisen för att undvika problem.

### Klientkonsol {#client-console-eol}

Adobe Campaign Classic Client Console kan inte längre köras på följande system eftersom de har tagits bort av redigeraren. Kunder som kör Campaign Client Console på någon av dessa versioner måste uppgradera till den senaste versionen före målets borttagningsdatum. Se [Kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

### Operativsystem {#o-s-eol}

Från och med version 19.1 är Adobe Campaign inte längre kompatibelt med följande operativsystem.

* Debian 7. [Läs mer](https://wiki.debian.org/DebianReleases).
* RHEL 6.x [Läs mer](https://access.redhat.com/support/policy/updates/errata).
* Windows Server 2008. [Läs mer](https://support.microsoft.com/en-us/lifecycle/search/1163).
* SLES 11. [Läs mer](https://www.suse.com/lifecycle).

### Webbservrar {#web-server-eol}

Från och med vårutgåvan 19.1 är Adobe Campaign inte längre kompatibelt med följande webbserver.

* Microsoft IIS 7. [Läs mer](https://support.microsoft.com/en-us/lifecycle/search/810).

### verktyg {#tools-eol}

Från och med vårutgåvan 19.1 är Adobe Campaign inte längre kompatibelt med följande verktyg.

* Java JDK 7. [Läs mer](http://www.oracle.com/technetwork/java/javase/eol-135779.html).
* Library Office 3.5 / 4.3 / 5.x, utom när det är inbäddat i ett annat verktyg. [Läs mer](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases).

### Databasmotorer {#dbe-eol}

Adobe stöder inte följande databasmotorer eftersom de har tagits bort av redigeraren. Kunder som kör dessa versioner måste uppgradera till den senaste versionen eller byta till en annan.

Se [Campaign Classic-kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) för att få tillgång till listan över kompatibla versioner.

**FDA (FEDERATED DATA ACCESS)**

Från och med vårutgåvan 19.1 är Adobe Campaign inte längre kompatibelt med följande FDA-servrar.

* Oracle 11G. [Läs mer](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 9.3. [Läs mer](https://www.postgresql.org/support/versioning).
* MySQL 5.5. &lt;[Läs mer](http://www.fromdual.com/support-for-mysql-from-oracle).
* DB2 9.5. [Läs mer](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Teradata 14-14.1. [Läs mer](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068).

Campaign Classic är inte kompatibelt med följande servrar i FDA (Federated Data Access).

* DB2 UDB 9.5, 9.7. Den senaste versionen av DB2 stöds av FDA (Federated Data Access). [Läs mer](http://www-01.ibm.com/support/docview.wss?uid=swg21168270).
* Oracle 9i, 10G R2. Senare versioner av Oracle stöds via FDA (Federated Data Access). [Läs mer](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Senare versioner av PostgreSQL stöds via FDA (Federated Data Access). [Läs mer](https://www.postgresql.org/support/versioning).
* MSSQL 2000, 2005, 2008 R2. Senare versioner av SQL Server stöds via FDA (Federated Data Access). [Läs mer](https://support.microsoft.com/en-us/lifecycle/search/1044).
* MySQL 5.1. Senare versioner av MySQL stöds via FDA (Federated Data Access). [Läs mer](https://en.wikipedia.org/wiki/InfiniDB).
* InfiniDB har nått slutet av livscykeln. [Läs mer](https://www.mysql.com/support).
* Teradata 13, 13.1. Senare versioner av Teradata stöds via FDA (Federated Data Access). [Läs mer](https://www.info.teradata.com/download.cfm?ItemID=1007255).
* Netezza 6.02, 7.0. Netezza har nått slutet av livet. [Läs mer](https://en.wikipedia.org/wiki/Netezza).
* AsterData 5.0. AsterData har nått slutet av livet. [Läs mer](https://en.wikipedia.org/wiki/Aster_Data_Systems).
* Sybase IQ 15.2, 15.4, 15.5 och Sybase ASE 15.0. Senare versioner av Sybase stöds via FDA (Federated Data Access). [Läs mer](https://sites.google.com/site/dbatipsandtricks/time-tracker).
* Hadoop via HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic kommer fortfarande att ha stöd för de listade versionerna av Hadoop via HiveSQL via FDA (Federated Data Access), men dessa versioner sammanfogas med: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) och HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**RDBMS-SERVER**

Adobe Campaign är inte kompatibelt med följande RDBMS-servrar:
* Oracle 10GR2, 11G
* PostgreSQL 9.0 till 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
