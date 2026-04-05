---
product: campaign
title: Funktioner som tagits bort och ersatts av Campaign Classic
description: På den här sidan visas borttagna och borttagna funktioner i Adobe Campaign Classic
feature: Release Notes
role: User
level: Beginner
exl-id: d60d67de-6618-4f3b-be4a-ad7633ab5645
source-git-commit: 647709dd4b0c70c342be03d3012bc02f10ff2c00
workflow-type: tm+mt
source-wordcount: '1675'
ht-degree: 0%

---

# Föråldrade och borttagna funktioner {#deprecated-and-removed-features}



Adobe utvärderar ständigt produktfunktioner för att identifiera äldre funktioner som bör ersättas med modernare alternativ för att förbättra det totala kundvärdet, alltid under noggrant övervägande av bakåtkompatibilitet. När Adobe Campaign Classic arbetar med verktyg från tredje part uppdateras kompatibiliteten regelbundet, så att endast de versioner som stöds kan implementeras. Versioner som inte längre är kompatibla med Adobe Campaign Classic visas nedan och i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md).

Följande regler gäller för att informera om den förestående borttagningen/ersättningen av Campaign Classic-funktioner:

* Föråldringsanmälan kommer först. Funktioner som inte längre används är fortfarande tillgängliga och stöds av befintliga användare, men de kommer inte att förbättras ytterligare och inte heller dokumenteras.
* Borttagning av föråldrade funktioner kommer att ske tidigast i följande version. Faktiskt måldatum för borttagning visas på den här sidan.

Den här processen ger kunderna minst en releasecykel för att anpassa implementeringen till en ny version eller en efterföljare till en borttagningsfunktion, innan den faktiska borttagningen.

>[!NOTE]
>Adobe Campaign-versioner och nya funktioner listas i [versionsinformationen](../../rn/using/latest-release.md).

## Föråldrade funktioner {#deprecated-features}

I det här avsnittet visas funktioner som markerats som borttagna i de senaste Campaign Classic-versionerna.

I allmänhet är de funktioner som ska tas bort i en framtida version först inaktuella. Dessa funktioner är inte längre tillgängliga för nya Campaign Classic-kunder eller ska inte användas för nya implementeringar. De tas också bort från produktdokumentationen.

Kunder uppmanas att granska om de använder funktionen/funktionen i den aktuella distributionen och planera för en ändring av implementeringen. Se målets borttagningsdatum för att planera miljön och projektuppdateringarna utifrån detta.

<table> 
 <tbody> 
   <tr>
   <td><strong>Funktion</strong></td>
   <td><strong>Information</strong></td>
  </tr>
  <tr>
 <td>Campaign (Neolane) legacy SDK</td>
 <td><p>Campaign (Neolane) SDK för mobilapplikationer är nu föråldrat. Använd i stället Adobe Experience Platform Mobile SDK genom att konfigurera Adobe Campaign-tillägget i användargränssnittet för datainsamling. Adobe Experience Platform Mobile SDK hjälper er att driva Adobe Experience Cloud lösningar och tjänster i era mobilappar. SDK-konfigurationen hanteras via användargränssnittet för datainsamling för flexibel konfiguration och utbyggbara, regelbaserade integreringar. Lär dig hur du konfigurerar mobilappskanalen i <a href="https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/push/push-settings">dokumentationen för Campaign v8</a>.</p>
<p>Måldatum: 31 juli 2025 </p>
</td>
</tr>
<tr>
 <td>Social marknadsföring med Facebook</td>
 <td><p>Social marknadsföring med Facebook är nu föråldrat. Du kan använda X-integrering (tidigare Twitter-integrering) för att publicera på sociala medier, eller arbeta med Adobe för att skapa en anpassad kanal.</p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
<tr>
 <td>ACS Connector</td>
 <td><p>ACS Connector (Prime-erbjudande) är nu föråldrat. Du kan använda funktioner för Campaigns export/import för att extrahera och mata in data i båda produkterna.</p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
 </tbody> 
</table>

## Borttagna funktioner {#removed-features}

I det här avsnittet visas funktioner som har tagits bort från Campaign Classic.

<table> 
 <tbody>
  <tr> 
   <td><strong>Funktion</strong></td>
   <td><strong>Information</strong></td>
  <tr>  
      <tr>
  <td>Adobe Analytics Data Connector<br></td>
   <td><p>Adobe Analytics Data Connector togs bort den 17 augusti 2022. Den hade tagits bort i Campaign 21.1.3-versionen.</p>
   <p>Om du använder den här kopplingen måste du anpassa implementeringen i enlighet med detta. <a href="../../integrations/using/gs-aa.md">Läs mer</a></p>
  </td>
 </tr>
    <tr>
  <td>Övervakningsrapport för teknisk leverans<br></td>
   <td><p>Övervakningsrapporten för teknisk leverans är inte längre tillgänglig. Den hade tagits bort i Campaign 21.1.3-versionen.</p>
   <!--p>If needed, you can receive this report daily by email until the feature removal date. To request it, open a specific <a href="https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html">Support Case</a> and specify the name of the instance and the email address(es) to send the report to.</p--> 
  </td>
 </tr>
  <tr>
  <td>OAuth-autentisering (OAuth och JWT)<br></td>
  <td><p> Integreringsautentisering med utlösare som ursprungligen baserades på OAuth-autentiseringsinställningar för åtkomst av pipeline har nu ändrats och flyttats till Adobe I/O. Autentiseringsläget har tagits bort i Campaign 20.3.<p>
  <p>Om du använde integrering med utlösare kan du lära dig hur du anpassar implementeringen <a href="../../integrations/using/about-triggers.md#implement"> på den här sidan</a>.</p> 
  <p>Mer information om OAuth-autentiseringsavskrivning finns på <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md">sidan</a></p> 
  <!--p><em>Target removal date: October 20, 2021. Hosted environments benefit from an extension until May 25, 2022. </em></p-->
  </td>
  </tr>
   <td>Rapportering<br></td>
   <td><p>Efter Adobe Flash Player EOL är mätarrapporten och diagramåtergivningsmotorn inte längre tillgängliga. <a href="../../reporting/using/creating-a-new-report.md">Läs mer</a></p>
  </tr>
  <tr>  
   <td>Faxkanal<br></td>
   <td><p>Faxkanalen är inte längre tillgänglig från och med Campaign 21.1.3. <a href="https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html" target="_blank">Läs mer i dokumentationen för Campaign v8</a></p>
  </tr>
  <tr>
  <td>Demdex domain<br></td>
  <td><p> Från och med Campaign 21.1.3 är demodomänen som används för att importera och exportera målgrupper till Adobe Experience Cloud inte längre tillgänglig. <a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">Läs mer</a></p> 
  </td>
  </tr>
   <tr> 
   <td>Windows NT-autentisering<br></td>
   <td><p>Från och med Campaign 20.3 har Windows NT-autentisering tagits bort från de tillgängliga autentiseringsmetoderna när en ny databas konfigureras med en Microsoft SQL Server. <a href="../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine">Läs mer</a></p></td>
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
   <td>Från och med Campaign 19.1 finns Campaign Classic API:er på en dedikerad sida. Om du använde den äldre jsapi.chm-filen bör du nu referera till <a href="https://experienceleague.adobe.com/developer/campaign-api/api/index.html">den nya onlineversionen</a>.</td>
  </tr> 
  <tr> 
   <td>Kampanjsamordning - prediktiv marknadsföring</td>
   <td>Från och med Campaign 18.10 är de prediktiva marknadsföringsfunktionerna inte längre tillgängliga.</td>
  </tr> 
  <tr> 
   <td>Webbprogram - Microsites</td>
   <td>Från och med Campaign 18.10 är Microsites inte längre tillgängliga. Du kan förbättra säkerheten genom att begränsa åtkomsten till enbart dedikerade domäner i Adobe Campaign konfigurationsfiler och använda anpassade URL:er i Campaign genom att använda DNS-alias.</td>
  </tr> 
  <tr> 
   <td>Push-meddelanden - iOS Binary Connector</td>
   <td>Enligt Apple rekommendation har Adobe tagit bort den gamla iOS Binary Connector-funktionen från och med Campaign 18.10. Den mer kapabla och mer effektiva HTTP/2-baserade kopplingen är redan tillgänglig.</td>
  </tr> 
  <tr> 
   <td>decryptString API</td>
   <td><p>Från och med Campaign 18.6-versionen är <em>dekrypptString</em>-API:t inte längre tillgängligt som standard för nya installationer.</p> 
   <p>I samband med en efteruppgradering till 18.6 (och senare) är detta API inte längre aktiverat och har ersatts med funktionen <em>dekrypptPassword</em> . <a href="https://experienceleague.adobe.com/developer/campaign-api/api/f-decryptPassword.html?hl=decrypt">Läs mer</a></p></td>
  </tr> 
   <tr> 
   <td>Mobilkanal - MMS- och WAP-push-meddelanden</td>
   <td>Från och med Campaign 18.4 är kanalerna MMS och Wap Push inte längre tillgängliga. Som ersättning kan du utnyttja <a href="../../delivery/using/sms-channel.md">SMS</a>- och <a href="../../delivery/using/about-mobile-app-channel.md">push</a>-leveranser.</td>
  </tr> 
   <tr> 
   <td>Mobilkanal - LINE v1</td>
   <td>Från och med Campaign 18.4 är LINE Connect-paketet inte längre tillgängligt. Adobe rekommenderar att du använder det nya LINE Channel-paketet som ersättning. <a href="../../delivery/using/line-channel.md">Läs mer</a></td>
  </tr>
 </tbody> 
</table>

<!--
## Deprecated compatibility {#deprecated-compatibility}

The following systems are deprecated for Campaign Classic. Please refer to the [Compatibility matrix](../../rn/using/compatibility-matrix.md) to upgrade to a newer version or move to a new system before the compatibility ends.
-->

## Kompatibilitetsslut {#end-of-compatibility}

>[!CAUTION]
>
>Adobe Campaign Classic är kompatibelt med alla system och verktyg som listas i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md). När specifika versioner av dessa system och verktyg från tredje part når slutet av livscykeln (EOL) med sina respektive skapare är Adobe Campaign inte längre kompatibelt med dessa versioner: de tillkännages som inaktuella och tas sedan bort från vår kompatibilitetsmatris i den följande produktversionen. Se till att du har de versioner av system som stöds i kompatibilitetsmatrisen för att undvika problem.

### Klientkonsol {#client-console-eol}

Adobe Campaign Classic Client Console kan inte längre köras på följande system eftersom de har tagits bort av redigeraren. Kunder som kör Campaign Client Console på någon av dessa versioner måste uppgradera till den senaste versionen före målets borttagningsdatum. Se [Kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md).

* Windows Server 2003, 2008, 2008 R2
* Windows 7, XP, Vista

>[!NOTE]
>Från och med Campaign 20.1 är Campaign Classic Client Console 32-bitar inte längre kompatibla med de senaste versionerna av Campaign. Du måste använda 64-bitars Client Console.

### Operativsystem {#o-s-eol}

* Från och med version 7.3.4 är Adobe Campaign inte längre kompatibelt med Red Hat Enterprise Linux (RHEL) 7.

* Från och med version 7.3.1 är Adobe Campaign inte längre kompatibelt med Windows 8 och Windows Server 2012.

* Från och med version 22.1 är Adobe Campaign inte längre kompatibelt med CentOs 8.x (64 bitar). CentOS Linux 8 nådde slutet av livscykeln (EOL) den 31 december 2021. [Läs mer](https://www.centos.org/centos-linux-eol/).

  Om du använder det här operativsystemet ska du anpassa implementeringen därefter. CentOS 7.x (64 bitar) och RHEL 8.x/7.x (64 bitar) stöds fortfarande.

* Från och med version 21.1.3 är Adobe Campaign inte längre kompatibelt med Debian 8.

* Från och med version 19.1 är Adobe Campaign inte längre kompatibelt med följande operativsystem.

   * CentOS 6. [Läs mer](https://wiki.centos.org/Download)
   * Debian 7. [Läs mer](https://wiki.debian.org/DebianReleases)
   * RHEL 6.x [Läs mer](https://access.redhat.com/support/policy/updates/errata)
   * Windows Server 2008. [Läs mer](https://support.microsoft.com/en-us/lifecycle/search/1163)
   * SLES 11. [Läs mer](https://www.suse.com/lifecycle)

### Webbservrar {#web-server-eol}

Från och med 19.1-vårutgåvan är Adobe Campaign inte längre kompatibelt med följande webbserver.

* Apache 2.2. [Läs mer](https://httpd.apache.org/)
* Microsoft IIS 7. [Läs mer](https://support.microsoft.com/en-us/lifecycle/search/810)

### verktyg {#tools-eol}

Från och med vårutgåvan 19.1 är Adobe Campaign inte längre kompatibelt med följande verktyg.

* Java JDK 7. [Läs mer](https://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Library Office 3.5 / 4.3 / 5.x, utom när det är inbäddat i ett annat verktyg. [Läs mer](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Databasmotorer {#dbe-eol}

Adobe stöder inte följande databasmotorer eftersom de har tagits bort av redigeraren. Kunder som kör dessa versioner måste uppgradera till den senaste versionen eller byta till en annan.

Se [Kampanjkompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md) för att få tillgång till listan över kompatibla versioner.

**FEDERATED DATA ACCESS (FDA)**

Från och med version 20.2 är Adobe Campaign inte längre kompatibelt med följande FDA-server:

* DB2 UDB 10.5

Från och med vårutgåvan 19.1 är Adobe Campaign inte längre kompatibelt med följande FDA-servrar:

* PostgreSQL 9.3.
* MySQL 5.5.
* DB2 9.5.
* Teradata 14-14.1.

Campaign Classic är inte kompatibelt med följande servrar i FDA (Federated Data Access). Använd senare versioner eller system.

* DB2 UDB 9.5, 9.7.
* Oracle 9i, 10G R2.
* PostgreSQL-versioner upp till 9,6 har nått slutet av livscykeln.
* MSSQL 2000, 2005, 2008 R2.
* MySQL 5.1.
* InfiniDB har nått slutet av livscykeln.
* Teradata 13.1
* Netezza 6.02, 7.0. Netezza har nått slutet av sitt liv.
* AsterData 5.0. AsterData har nått slutet av livscykeln.
* Sybase IQ 15.2, 15.4, 15.5 och Sybase ASE 15.0.
* Hadoop via HiveSQL: Hadoop 2.7.3, HiveSQL 1.2.1. Adobe Campaign Classic har fortfarande stöd för de listade versionerna av Hadoop via HiveSQL via FDA (Federated Data Access), men dessa versioner sammanfogas med: HortonWorks (HDP 2.4.X, 2.5.x, 2.6.x) och HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)

**RDBMS-SERVER**

Från och med vårutgåvan 19.1 är Adobe Campaign inte längre kompatibelt med följande RDBMS-servrar:

* Oracle 10GR2
* PostgreSQL 9.0 till 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7

PostgreSQL-versioner upp till 9,6 har nått slutet av livscykeln. De stöds därför inte av Adobe Campaign.

### SMS-anslutningar {#sms-eol}

Från och med version 20.2 har äldre SMS-anslutningar tagits bort. Adobe Campaign är inte kompatibelt med:

* Allmänt SMPP (SMPP version 3.4 med stöd för binärt läge)
* Sybase365 (SAP SMS 365)
* CLX Communications
* Tele2
* O2
* iOS

### CRM-anslutningar {#crm-connectors}

Från och med Campaign 21.1 är följande CRM-anslutningar inte längre kompatibla med Campaign:

* Soap API - lokal: 2007, 2015, 2016
* Soap API - Online: 2015, 2016
* Webb-API - Microsoft Dynamics CRM 2016
* Webb-API - Microsoft Dynamics CRM 2016 uppdatering 1
* Oracle On Demand-API
