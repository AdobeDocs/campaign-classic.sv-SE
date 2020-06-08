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
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e46325ab8f68a0b71198aee9cf04f2b1eb97fdd3
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 0%

---


# Föråldrade och borttagna funktioner {#deprecated-and-removed-features}

Adobe utvärderar ständigt produktfunktioner för att identifiera äldre funktioner som bör ersättas med modernare alternativ för att förbättra det totala kundvärdet, alltid under noggrant övervägande av bakåtkompatibilitet. Eftersom Adobe Campaign Classic fungerar med verktyg från tredje part uppdateras kompatibiliteten regelbundet, så att endast de versioner som stöds kan implementeras. Versioner som inte längre är kompatibla med Adobe Campaign Classic visas nedan och i [kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Följande regler gäller för att informera om den förestående borttagningen/ersättningen av Campaign Classic-funktioner:

* Föråldringsanmälan kommer först. Funktioner som inte längre används är fortfarande tillgängliga och stöds av befintliga användare, men de kommer inte att förbättras ytterligare och inte heller dokumenteras.
* Borttagning av föråldrade funktioner sker tidigast i följande version. Faktiskt måldatum för borttagning visas på den här sidan.

Den här processen ger kunderna minst en releasecykel för att anpassa implementeringen till en ny version eller en efterföljare till en borttagningsfunktion, innan den faktiska borttagningen.

>[!NOTE]
>Adobe Campaign-releaser och nya funktioner listas i [versionsinformationen](../../rn/using/latest-release.md).

## Föråldrade funktioner {#deprecated-features}

I det här avsnittet visas funktioner som har markerats som borttagna i de senaste Campaign Classic-versionerna.

I allmänhet är de funktioner som ska tas bort i en framtida version först inaktuella. Dessa funktioner är inte längre tillgängliga för nya kunder i Campaign Classic, eller ska inte användas för nya implementeringar. De tas också bort från produktdokumentationen.

Kunder uppmanas att granska om de använder funktionen/funktionen i den aktuella distributionen och planera för en ändring av implementeringen. Se målets borttagningsdatum för att planera miljön och projektuppdateringarna utifrån detta.

<table> 
 <tbody> 
   <tr>
   <td><strong>Funktion</strong></td>
   <td><strong>Ersättning</strong></td> 
  </tr>
   <tr>
  <td>SMS-anslutningar<br></td>
  <td><p> Från och med version 20.2 har följande SMS-anslutningar tagits bort.<p>
   <ul>
   <li>NetSize</li>
   <li>Allmänt SMPP (SMPP version 3.4 med stöd för binärt läge)</li>
   <li>Sybase365 (SAP SMS 365)</li>
   <li>CLX Communications</li>
   <li>Tele2</li>
   <li>O2</li>
   <li>iOS</li>
   </ul>
  <p>Om du använder någon av dessa anslutningar måste du anpassa implementeringen i enlighet med detta. <a href="../../delivery/using/sms-channel.md">Läs mer</a></p> 
  <p>Lär dig hur du migrerar äldre anslutningar i <a href="https://helpx.adobe.com/campaign/kb/sms-connector.html">den här tekniken</a>.</p>
  <p><em>Datum för målborttagning: 2021</em></p>
  </td> 
 </tr>
  <tr>  
   <td>Faxkanal<br></td>
   <td><p>Faxkanalen är föråldrad från och med version 20.2.</p> 
   <p>Om du använder den här kanalen måste du anpassa implementeringen efter det. <a href="../../delivery/using/communication-channels.md">Läs mer</a> om Campaign-kanaler.</p>
   <p><em>Datum för målborttagning: 2021</em></p></td>
  </tr>
 </tbody> 
</table>

## Borttagna funktioner {#removed-features}

I det här avsnittet visas funktioner som har tagits bort från Campaign Classic.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Område - funktion</strong></td>
   <td><strong>Ersättning</strong></td> 
  </tr> 
   <tr> 
   <td>Filbaserad e-postarkivering<br></td>
   <td><p>Från och med Campaign 20.2 är filbaserad e-postarkivering inte längre tillgänglig. E-postarkivering är nu tillgänglig via en dedikerad e-postadress för hemlig kopia. <a href="../../installation/using/email-archiving.md">Läs mer</a></p></td>
  </tr> 
   <tr> 
   <td>Leadhantering</td>
   <td><p>Från och med Campaign 20.2 är Leads Management-paketet inte längre tillgängligt. Liknande funktioner kan implementeras via andra interna arbetsflödesaktiviteter och datamodellsändringar.</p></td>
   </tr>
   <tr>
   <td>Dokumentation för kampanj-API:er - jsapi.chm-fil</td>
   <td>Från och med Campaign 19.1 finns Campaign Classic-API:er tillgängliga på en dedikerad sida. Om du använde den äldre jsapi.chm-filen bör du nu hänvisa till <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">den nya onlineversionen</a>.</td>
  </tr> 
  <tr> 
   <td>Kampanjsamordning - prediktiv marknadsföring</td>
   <td>Från och med Campaign 18.10 är de prediktiva marknadsföringsfunktionerna inte längre tillgängliga.</td>
  </tr> 
  <tr> 
   <td>Webbprogram - mikrowebbplatser</td>
   <td>Från och med Campaign 18.10 är Microsites inte längre tillgängliga. Ni kan förbättra säkerheten genom att begränsa åtkomsten till enbart dedikerade domäner i konfigurationsfiler för Adobe Campaign och använda personaliserade URL:er i Campaign genom att använda DNS-alias. <a href="https://helpx.adobe.com/campaign/kb/domain-name-delegation.html">Läs mer</a></td>
  </tr> 
  <tr> 
   <td>Push-meddelanden - binär iOS-anslutning</td>
   <td>Enligt Apples rekommendation har Adobe tagit bort den gamla binära iOS-kopplingen från och med Campaign 18.10. Den mer kapabla och mer effektiva HTTP/2-baserade kopplingen är redan tillgänglig.</td>
  </tr> 
  <tr> 
   <td>decryptString API</td>
   <td><p>Från och med Campaign 18.6 är API:t <em>dekrypptString</em> av säkerhetsskäl inte längre tillgängligt som standard för nya installationer.</p> 
   <p>I samband med en efteruppgradering till 18.6 (och senare) är denna API inte längre aktiverad och har ersatts av funktionen <em>dekrypptPassword</em> . <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">Läs mer</a></p></td>
  </tr> 
   <tr> 
   <td>Mobilkanal - MMS- och WAP-push-meddelanden</td>
   <td>Från och med Campaign 18.4 är kanalerna MMS och Wap Push inte längre tillgängliga. Som ersättning kan du använda <a href="../../delivery/using/sms-channel.md">SMS</a> och <a href="../../delivery/using/about-mobile-app-channel.md">push</a> -leveranser.</td>
  </tr> 
   <tr> 
   <td>Mobilkanal - LINE v1</td>
   <td>Från och med Campaign 18.4 är LINE Connect-paketet inte längre tillgängligt. Adobe rekommenderar att du använder det nya LINE Channel-paketet som ersättning. <a href="../../delivery/using/line-channel.md">Läs mer</a></td>
  </tr> 
 </tbody> 
</table>

## Undertryckt kompatibilitet {#deprecated-compatibility}

Följande system är föråldrade för Campaign Classic. Se [kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) för att uppgradera till en nyare version eller gå till ett nytt system innan kompatibiliteten upphör.

### Adobe Campaign 20.2 {#compat-20-2-release}

Från och med version 20.2 är följande system föråldrat för Campaign Classic. Kompatibiliteten upphör i version 20.3 - september 2020.

* Klientkonsol: Windows 7
* Äldre SMS-anslutningar (se avsnittet Föråldrade funktioner nedan)

### Adobe Campaign 19.2  {#compat-19-2-release}

Från och med version 19.2 har följande operativsystem tagits bort för Campaign Classic. Kompatibiliteten upphör 2020 för EOY.

* Webbserver: Apache 2.2.
* Operativsystem: CentOS 6.

Se [kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) för att uppgradera till en nyare version eller gå till ett nytt system.

## Kompatibilitetsslut {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic är kompatibelt med alla system och verktyg som listas i [kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html). När specifika versioner av dessa system och verktyg från tredje part når slutet av livscykeln med sina respektive skapare är Adobe Campaign inte längre kompatibelt med dessa versioner: de tillkännages som inaktuella och tas sedan bort från vår kompatibilitetsmatris i den följande produktversionen. Se till att du har de versioner av system som stöds i kompatibilitetsmatrisen för att undvika problem.

### Klientkonsol {#client-console-eol}

Adobe Campaign Classic Client Console kan inte längre köras på följande system eftersom de har tagits bort av redigeraren. Kunder som kör Campaign Client Console på någon av dessa versioner måste uppgradera till den senaste versionen före målets borttagningsdatum. Se [Kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

* Windows Server 2003, 2008, 2008 R2
* Windows XP, Vista

>[!NOTE]
>Från och med Campaign 20.1 är Campaign Classic Client Console 32 bitar inte längre kompatibelt med de senaste versionerna av Campaign. Du måste använda 64-bitars Client Console.


### Operativsystem {#o-s-eol}

Från och med version 19.1 är Adobe Campaign inte längre kompatibelt med följande operativsystem.

* Debian 7. [Läs mer](https://wiki.debian.org/DebianReleases)
* RHEL 6.x [Läs mer](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008. [Läs mer](https://support.microsoft.com/en-us/lifecycle/search/1163)
* SLES 11. [Läs mer](https://www.suse.com/lifecycle)

### Webbservrar {#web-server-eol}

Från och med vårutgåvan 19.1 är Adobe Campaign inte längre kompatibelt med följande webbserver.

* Microsoft IIS 7. [Läs mer](https://support.microsoft.com/en-us/lifecycle/search/810)

### verktyg {#tools-eol}

Från och med vårutgåvan 19.1 är Adobe Campaign inte längre kompatibelt med följande verktyg.

* Java JDK 7. [Läs mer](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Library Office 3.5 / 4.3 / 5.x, utom när det är inbäddat i ett annat verktyg. [Läs mer](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Databasmotorer {#dbe-eol}

Adobe stöder inte följande databasmotorer eftersom de har tagits bort av redigeraren. Kunder som kör dessa versioner måste uppgradera till den senaste versionen eller byta till en annan.

Se [Campaign Classic-kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) för att få tillgång till listan över kompatibla versioner.

**FDA (FEDERATED DATA ACCESS)**

Från och med vårutgåvan 19.1 är Adobe Campaign inte längre kompatibelt med följande FDA-servrar.

* PostgreSQL 9.3. [Läs mer](https://www.postgresql.org/support/versioning)
* MySQL 5.5. [Läs mer](http://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5. [Läs mer](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Teradata 14-14.1. [Läs mer](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

Campaign Classic är inte kompatibelt med följande servrar i FDA (Federated Data Access).

* DB2 UDB 9.5, 9.7. Den senaste versionen av DB2 stöds av FDA (Federated Data Access). [Läs mer](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i, 10G R2. Senare versioner av Oracle stöds via FDA (Federated Data Access). [Läs mer](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3, 8.4, 9.0, 9.1, 9.2. Senare versioner av PostgreSQL stöds via FDA (Federated Data Access). [Läs mer](https://www.postgresql.org/support/versioning)
* MSSQL 2000, 2005, 2008 R2. Senare versioner av SQL Server stöds via FDA (Federated Data Access). [Läs mer](https://support.microsoft.com/en-us/lifecycle/search/1044)
* MySQL 5.1. Senare versioner av MySQL stöds via FDA (Federated Data Access). [Läs mer](https://en.wikipedia.org/wiki/InfiniDB)
* InfiniDB har nått slutet av livscykeln. [Läs mer](https://www.mysql.com/support)
* Teradata 13, 13.1. Senare versioner av Teradata stöds via FDA (Federated Data Access). [Läs mer](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* Netezza 6.02, 7.0. Netezza har nått slutet av livet. [Läs mer](https://en.wikipedia.org/wiki/Netezza)
* AsterData 5.0. AsterData har nått slutet av livet. [Läs mer](https://en.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2, 15.4, 15.5 och Sybase ASE 15.0. Senare versioner av Sybase stöds via FDA (Federated Data Access). [Läs mer](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* Hadoop via HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic kommer fortfarande att ha stöd för de listade versionerna av Hadoop via HiveSQL via FDA (Federated Data Access), men dessa versioner sammanfogas med: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) och HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**RDBMS-SERVER**

Adobe Campaign är inte kompatibelt med följande RDBMS-servrar:
* Oracle 10GR2
* PostgreSQL 9.0 till 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7
