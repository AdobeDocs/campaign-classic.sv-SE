---
product: campaign
title: Funktioner som är inaktuella och har ersatts i Campaign Classic
description: Den här sidan beskriver inaktuella och borttagna funktioner i Adobe Campaign Classic
feature: Overview
role: User
level: Beginner
exl-id: d60d67de-6618-4f3b-be4a-ad7633ab5645
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1645'
ht-degree: 98%

---

# Inaktuella och borttagna funktioner {#deprecated-and-removed-features}

![](../../assets/v7-only.svg)

Adobe utvärderar ständigt produktfunktioner för att identifiera äldre funktioner som bör ersättas med modernare alternativ för att förbättra det övergripande kundvärdet. Detta sker alltid under noggrant övervägande gällande bakåtkompatibilitet. Eftersom Adobe Campaign Classic fungerar med verktyg från tredje part uppdateras kompatibiliteten regelbundet, vilket innebär att endast de versioner som stöds kan implementeras. Versioner som inte längre är kompatibla med Adobe Campaign Classic visas nedan och i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md).

Följande regler tillämpas för att informera om den förestående borttagningen/ersättningen av funktioner i Campaign Classic:

* Tillkännagivande av utfasning kommer först. Även om inaktuella funktioner fortfarande kan vara tillgängliga och stöd finns för befintliga användare förbättras de inte och dokumenteras inte ytterligare.
* Borttagning av inaktuella funktioner sker tidigast i följande version. Faktiskt måldatum för borttagning tillkännages på den här sidan.

Den här processen ger kunderna minst en cykel av versioner för att anpassa implementeringen till en ny version eller efterföljare till en inaktuell funktion innan den faktiska borttagningen.

>[!NOTE]
>Adobe Campaign-versioner och nya funktioner listas i [versionsinformationen](../../rn/using/latest-release.md).

## Inaktuella funktioner {#deprecated-features}

I det här avsnittet listas funktioner som har markerats som inaktuella i de senaste versionerna av Campaign Classic.

I allmänhet är de funktioner som ska tas bort i en framtida version de första att bli inaktuella. Dessa funktioner är inte längre tillgängliga för nya Campaign Classic-kunder eller ska inte användas för nya implementeringar. De tas också bort från produktdokumentationen.

Kunder uppmanas att se över om de använder funktionen i den aktuella driftsättningen och planera för en ändring av implementeringen. Se måldatumet för borttagning för att planera miljön och projektuppdateringar utifrån detta.

<table> 
 <tbody> 
   <tr>
   <td><strong>Funktion</strong></td>
   <td><strong>Ersättning</strong></td>
  </tr>
    <tr>
  <td>Adobe Analytics Data Connector<br></td>
   <td><p>Från och med Campaign 21.1.3 är Adobe Analytics Data Connector inaktuell.</p>
   <p>Om du använder den här kopplingen måste du anpassa implementeringen efter den. <a href="../../platform/using/adobe-analytics-connector.md">Läs mer</a></p>
  <p><em>Måldatum för borttagning: 1 mars 2022</em></p>
  </td>
 </tr>
    <tr>
  <td>Övervakningsrapport om teknisk levererbarhet<br></td>
   <td><p>Övervakningsrapporten om teknisk levererbarhet är föråldrad från och med Campaign version 21.1.</p>
   <p>Om det behövs kan du få den här rapporten via e-post varje dag fram tills funktionen tas bort. Du begär den genom att öppna ett specifikt <a href="https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html">supportärende</a> och ange namnet på instansen och e-postadressen eller e-postadresserna som rapporten ska skickas till.</p> 
   <p>Adobe rekommenderar att du samarbetar med levererbarhetsteamet för att definiera de bästa verktygen för att övervaka instansens levererbarhetsförmåga.</p>
  <p><em>Måldatum för borttagning: i slutet av 2021</em></p>
  </td>
 </tr>
  <tr>
  <td>OAuth-autentisering (OAuth och JWT)<br></td>
  <td><p> Från och med Campaign version 20.3 har autentisering av utlösarintegreringen, som ursprungligen baserades på oAUTH-autentiseringsinställningar för åtkomst till pipelines, nu ändrats och flyttats till Adobe I/O. <p>
  <p>Om du använder den här utlösarintegreringen måste du anpassa implementeringen i enlighet med detta. <a href="../../integrations/using/configuring-adobe-io.md">Läs mer</a></p> 
  <p>Mer information om inaktuell OAauth-autentisering finns på den här <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md">sidan</a></p> 
  <p><em>Måldatum för borttagning: nov 2021</em></p>
  </td>
  </tr>
 </tbody> 
</table>

## Borttagna funktioner {#removed-features}

I det här avsnittet visas funktioner som har tagits bort från Campaign Classic.

<table> 
 <tbody>
  <tr> 
   <td><strong>Område – funktion</strong></td>
   <td><strong>Ersättning</strong></td> 
  </tr>
  <tr>  
   <td>Faxkanal<br></td>
   <td><p>Faxkanalen är inte längre tillgänglig från och med Campaign 21.1.3. <a href="../../delivery/using/steps-about-delivery-creation-steps.md">Läs mer</a></p>
  <tr>
  <td>Demdex-domän<br></td>
  <td><p> Från och med Campaign version 21.1.3 är demdex-domänen som används för att importera och exportera målgrupper till Adobe Experience Cloud inte längre tillgänglig. <a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">Läs mer</a></p> 
  </td>
  </td>
  </tr>
   <tr> 
   <td>Windows NT-autentisering<br></td>
   <td><p>Från och med Campaign version 20.3 har Windows NT-autentisering tagits bort från de tillgängliga autentiseringsmetoderna när en ny databas konfigureras med en Microsoft SQL-server. <a href="../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine">Läs mer</a></p></td>
  </tr>
   <tr> 
   <td>Filbaserad e-postarkivering<br></td>
   <td><p>Från och med Campaign 20.2 är filbaserad e-postarkivering inte längre tillgänglig. E-postarkivering är nu tillgänglig via en dedikerad e-postadress som är osynlig för leveransmottagarna. <a href="../../installation/using/email-archiving.md">Läs mer</a></p></td>
  </tr> 
   <tr> 
   <td>Hantera potentiella kunder</td>
   <td><p>Från och med Campaign 20.2 är paketet med hantering av potentiella kunder inte längre tillgängligt. Liknande funktioner kan implementeras via andra ändringar i interna arbetsflödesaktiviteter och datamodeller.</p></td>
   </tr>
   <tr>
   <td>Dokumentation för API:er i Campaign – filen jsapi.chm</td>
   <td>Från och med Campaign 19.1 finns API:er i Campaign Classic på en dedikerad sida. Om du använder den äldre filen jsapi.chm bör du nu använda <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html">den nya versionen online</a>.</td>
  </tr> 
  <tr> 
   <td>Orkestrering i Campaign – förutsägande marknadsföring</td>
   <td>Från och med Campaign 18.10 är de förutsägande marknadsföringsfunktionerna inte längre tillgängliga.</td>
  </tr> 
  <tr> 
   <td>Webbapplikationer – mikrowebbplatser</td>
   <td>Från och med Campaign 18.10 är mikrowebbplatser inte längre tillgängliga. Du kan förbättra säkerheten genom att begränsa åtkomsten till enbart dedikerade domäner i konfigurationsfiler i Adobe Campaign och använda anpassade webbadresser i Campaign genom att använda DNS-alias. <a href="https://helpx.adobe.com/se/campaign/kb/domain-name-delegation.html">Läs mer</a></td>
  </tr> 
  <tr> 
   <td>Push-meddelanden – iOS Binary-koppling</td>
   <td>Enligt Apples rekommendation har Adobe tagit bort den gamla binära iOS-kopplingen från och med Campaign 18.10. Den mer kapabla och effektiva HTTP/2-baserade kopplingen är redan tillgänglig.</td>
  </tr> 
  <tr> 
   <td>API:et decryptString</td>
   <td><p>Från och med Campaign 18.6 är API:et <em>decryptString</em> av säkerhetsskäl inte längre tillgängligt som standard för nya installationer.</p> 
   <p>I samband med en efteruppgradering till 18.6 (och senare) är detta API inte längre aktiverat och har ersatts av funktionen <em>decryptPassword</em>. <a href="https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/f-decryptPassword.html?hl=decrypt">Läs mer</a></p></td>
  </tr> 
   <tr> 
   <td>Mobilkanal – MMS- och WAP-push-meddelanden</td>
   <td>Från och med Campaign 18.4 är kanalerna MMS och Wap Push inte längre tillgängliga. Som ersättning kan du använda <a href="../../delivery/using/sms-channel.md">SMS</a>- och <a href="../../delivery/using/about-mobile-app-channel.md">push</a>-leveranser.</td>
  </tr> 
   <tr> 
   <td>Mobilkanal – LINE v1</td>
   <td>Från och med Campaign 18.4 är LINE Connect-paketet inte längre tillgängligt. Adobe rekommenderar att du använder det nya LINE Channel-paketet som ersättning. <a href="../../delivery/using/line-channel.md">Läs mer</a></td>
  </tr>
 </tbody> 
</table>

## Inaktuell kompatibilitet {#deprecated-compatibility}

Följande system är inaktuella i Campaign Classic. Se [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md) för att uppgradera till en nyare version eller gå över till ett nytt system innan kompatibiliteten upphör.

### Adobe Campaign version 20.2  {#compat-20-2-release}

Från och med version 20.2 har äldre SMS-kopplingar blivit inaktuella. Se [avsnittet Inaktuella funktioner](#deprecated-features)

## Kompatibilitet upphör {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic är kompatibelt med alla system och verktyg som listas i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md). När specifika versioner av dessa system och verktyg från tredje part når slutet av sin livscykel med sina respektive utgivare är Adobe Campaign inte längre kompatibelt med dessa versioner. De tillkännages som inaktuella och tas sedan bort från vår kompatibilitetsmatris i den följande produktversionen. Se till att du använder versioner av system som stöds i kompatibilitetsmatrisen för att undvika problem.

### Klientkonsol {#client-console-eol}

Klientkonsolen i Adobe Campaign Classic kan inte längre köras på följande system eftersom de har tagits bort av redigeraren. Kunder som kör klientkonsolen i Campaign på någon av dessa versioner måste uppgradera till den senaste versionen före måldatumet för borttagning. Se [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md).

* Windows Server 2003, 2008 och 2008 R2
* Windows 7, XP och Vista

>[!NOTE]
>Från och med Campaign version 20.1 är klientkonsolen i Campaign Classic som körs med 32 bitar inte längre kompatibel med de senaste versionerna av Campaign. Du måste använda klientkonsolen med 64 bitar.

### Operativsystem {#o-s-eol}

Från och med version 21.1.3 är stödet för Debian 8 föråldrat.

Från och med version 19.1 är Adobe Campaign inte längre kompatibelt med följande operativsystem.

* CentOS 6 [Läs mer](https://wiki.centos.org/Download)
* Debian 7. [Läs mer](https://wiki.debian.org/DebianReleases)
* RHEL 6.x [Läs mer](https://access.redhat.com/support/policy/updates/errata)
* Windows Server 2008. [Läs mer](https://support.microsoft.com/en-us/lifecycle/search/1163)
* SLES 11. [Läs mer](https://www.suse.com/lifecycle)

### Webbservrar {#web-server-eol}

Från och med vårversionen 19.1 är Adobe Campaign inte längre kompatibelt med följande webbserver.

* Apache 2.2. [Läs mer](https://httpd.apache.org/)
* Microsoft IIS 7. [Läs mer](https://support.microsoft.com/en-us/lifecycle/search/810)

### Verktyg {#tools-eol}

Från och med vårversionen 19.1 är Adobe Campaign inte längre kompatibelt med följande verktyg.

* Java JDK 7. [Läs mer](http://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5/4.3/5.x utom när det är inbäddat i ett annat verktyg. [Läs mer](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Databasmotorer {#dbe-eol}

Adobe har inte stöd för följande databasmotorer eftersom de har tagits bort av redigeraren. Kunder som kör dessa versioner måste uppgradera till den senaste versionen eller byta till en annan.

Se [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md) för Campaign för att få tillgång till en lista över kompatibla versioner.

**FDA (FEDERERAD DATAÅTKOMST)**

Från och med version 20.2 är Adobe Campaign inte längre kompatibelt med följande FDA-server:

* DB2 UDB 10.5

Från och med vårversionen 19.1 är Adobe Campaign inte längre kompatibelt med följande FDA-servrar:

* PostgreSQL 9.3. [Läs mer](https://www.postgresql.org/support/versioning)
* MySQL 5.5. [Läs mer](http://www.fromdual.com/support-for-mysql-from-oracle)
* DB2 9.5. [Läs mer](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Teradata 14–14.1. [Läs mer](https://community.teradata.com/t5/Database/Teradata-Database-Product-Life-Cycle/td-p/35068)

Campaign Classic är inte kompatibelt med följande servrar i federerad dataåtkomst (FDA).

* DB2 UDB 9.5 och 9.7. Stöd finns för senare versioner av DB2 via federerad dataåtkomst (FDA). [Läs mer](http://www-01.ibm.com/support/docview.wss?uid=swg21168270)
* Oracle 9i och 10G R2. Stöd finns för senare versioner av Oracle Server via federerad dataåtkomst (FDA). [Läs mer](http://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf)
* PostgreSQL 8.3, 8.4, 9.0, 9.1 och 9.2. Stöd finns för senare versioner av PostgreSQL via federerad dataåtkomst (FDA). [Läs mer](https://www.postgresql.org/support/versioning)
* MSSQL 2000, 2005 och 2008 R2. Stöd finns för senare versioner av SQL Server via federerad dataåtkomst (FDA). [Läs mer](https://support.microsoft.com/en-us/lifecycle/search/1044)
* MySQL 5.1. Stöd finns för senare versioner av MySQL via federerad dataåtkomst (FDA). [Läs mer](https://en.wikipedia.org/wiki/InfiniDB)
* InfiniDB har nått slutet av sin livscykel. [Läs mer](https://www.mysql.com/support)
* Teradata 13 och 13.1. Stöd finns för senare versioner av Teradata via federerad dataåtkomst (FDA). [Läs mer](https://www.info.teradata.com/download.cfm?ItemID=1007255)
* Netezza 6.02 och 7.0. Netezza har nått slutet av sin livscykel. [Läs mer](https://en.wikipedia.org/wiki/Netezza)
* AsterData 5.0. AsterData har nått slutet av sin livscykel. [Läs mer](https://en.wikipedia.org/wiki/Aster_Data_Systems)
* Sybase IQ 15.2, 15.4 och 15.5 samt Sybase ASE 15.0. Stöd finns för senare versioner av Sybase via federerad dataåtkomst (FDA). [Läs mer](https://sites.google.com/site/dbatipsandtricks/time-tracker)
* Hadoop via HiveSQL: Hadoop 2.7.3 och HiveSQL 1.2.1. Adobe Campaign Classic har fortfarande stöd för de listade versionerna av Hadoop via HiveSQL via federerad dataåtkomst (FDA). Dessa versioner slås dock ihop med: HortonWorks (HDP 2.4.X, 2.5.x och 2.6.x) och HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5) och 3.6 (HDP 2.6)

**RDBMS-SERVER**

Från och med vårversionen 19.1 är Adobe Campaign inte längre kompatibelt med följande RDBMS-servrar:

* Oracle 10GR2
* PostgreSQL 9.0 till 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7

### SMS-kopplingar {#sms-eol}

Adobe Campaign är inte kompatibelt med följande SMS-servrar:

* Generisk SMPP (SMPP version 3.4 med stöd för binärt läge)
* Sybase365 (SAP SMS 365)
* CLX Communications
* Tele2
* O2
* iOS

### CRM-kopplingar {#crm-connectors}

Från och med Campaign 21.1 är följande CRM-anslutningar inte längre kompatibla med Campaign:

* Soap API – lokal: 2007, 2015 och 2016
* Soap API – online: 2015 och 2016
* Webb-API - Microsoft Dynamics CRM 2016
* Webb-API - Microsoft Dynamics CRM 2016 uppdatering 1
* Oracle On Demand-API
