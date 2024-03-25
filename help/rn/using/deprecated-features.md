---
product: campaign
title: Funktioner som är inaktuella och har tagits bort i Campaign Classic
description: Den här sidan beskriver inaktuella och borttagna funktioner i Adobe Campaign Classic
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
role: User
level: Beginner
exl-id: d60d67de-6618-4f3b-be4a-ad7633ab5645
source-git-commit: 59156851156338c9462781d31ce81a651362f2da
workflow-type: tm+mt
source-wordcount: '1558'
ht-degree: 100%

---

# Inaktuella och borttagna funktioner {#deprecated-and-removed-features}



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
   <td><strong>Information</strong></td>
  </tr>
<tr>
 <td>Social marknadsföring med Facebook</td>
 <td>Social marknadsföring med Facebook är nu inaktuell. Du kan använda X (tidigare Twitter) för att publicera inlägg på sociala medier, eller samarbeta med Adobe för att skapa en anpassad kanal.
 <p></p>
  <!--p>Target removal date: End of 2023</p-->
  </td>
</tr>
<tr>
 <td>ACS-anslutning</td>
 <td>ACS-anslutning (Prime-erbjudande) är nu inaktuell. Du kan använda funktionerna export/import för Campaign för att extrahera och mata in data i båda produkterna.<p></p>
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
   <p>Om du använder den här kopplingen måste du anpassa implementeringen efter den. <a href="../../platform/using/gs-aa.md">Läs mer</a></p>
  </td>
 </tr>
    <tr>
  <td>Övervakningsrapport om teknisk levererbarhet<br></td>
   <td><p>Övervakningsrapporten för teknisk levererbarhet är inte längre tillgänglig. Den hade tagits bort i Campaign 21.1.3-versionen.</p>
   <!--p>If needed, you can receive this report daily by email until the feature removal date. To request it, open a specific <a href="https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html">Support Case</a> and specify the name of the instance and the email address(es) to send the report to.</p--> 
  </td>
 </tr>
  <tr>
  <td>OAuth-autentisering (OAuth och JWT)<br></td>
  <td><p> Integreringsautentisering med utlösare som ursprungligen baserades på oAUTH-autentiseringsinställningar för åtkomst till pipeline har nu ändrats och flyttats till Adobe I/O. Detta autentiseringsläge har nu fasats ut med versionen Campaign 20.3.<p>
  <p>Om du använde integrering med utlösare kan du lära dig hur du anpassar implementeringen <a href="../../integrations/using/configuring-adobe-io.md">på den här sidan</a>.</p> 
  <p>Mer information om inaktuell OAauth-autentisering finns på den här <a href="https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md">sidan</a></p> 
  <!--p><em>Target removal date: October 20, 2021. Hosted environments benefit from an extension until May 25, 2022. </em></p-->
  </td>
  </tr>
   <td>Rapportering<br></td>
   <td><p>Efter Adobe Flash Player EOL är mätarrapporten och diagramåtergivningsmotorn inte längre tillgängliga. <a href="../../reporting/using/creating-a-new-report.md">Läs mer</a></p>
  </tr>
  <tr>  
   <td>Faxkanal<br></td>
   <td><p>Faxkanalen är inte längre tillgänglig från och med Campaign 21.1.3. <a href="../../delivery/using/steps-about-delivery-creation-steps.md">Läs mer</a></p>
  </tr>
  <tr>
  <td>Demdex-domän<br></td>
  <td><p> Från och med Campaign version 21.1.3 är demdex-domänen som används för att importera och exportera målgrupper till Adobe Experience Cloud inte längre tillgänglig. <a href="../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md">Läs mer</a></p> 
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
   <td>Från och med Campaign 19.1 finns API:er i Campaign Classic på en dedikerad sida. Om du använder den äldre filen jsapi.chm bör du nu använda <a href="https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=sv">den nya versionen online</a>.</td>
  </tr> 
  <tr> 
   <td>Orkestrering i Campaign – förutsägande marknadsföring</td>
   <td>Från och med Campaign 18.10 är de förutsägande marknadsföringsfunktionerna inte längre tillgängliga.</td>
  </tr> 
  <tr> 
   <td>Webbapplikationer – mikrowebbplatser</td>
   <td>Från och med Campaign 18.10 är mikrowebbplatser inte längre tillgängliga. Du kan förbättra säkerheten genom att begränsa åtkomsten till enbart dedikerade domäner i konfigurationsfiler i Adobe Campaign och använda anpassade webbadresser i Campaign genom att använda DNS-alias.</td>
  </tr> 
  <tr> 
   <td>Push-meddelanden – iOS Binary-koppling</td>
   <td>Enligt Apples rekommendation har Adobe tagit bort den gamla binära iOS-kopplingen från och med Campaign 18.10. Den mer kapabla och effektiva HTTP/2-baserade kopplingen är redan tillgänglig.</td>
  </tr> 
  <tr> 
   <td>API:et decryptString</td>
   <td><p>Från och med Campaign 18.6 är API:et <em>decryptString</em> av säkerhetsskäl inte längre tillgängligt som standard för nya installationer.</p> 
   <p>I samband med en efteruppgradering till 18.6 (och senare) är detta API inte längre aktiverat och har ersatts av funktionen <em>decryptPassword</em>. <a href="https://experienceleague.adobe.com/developer/campaign-api/api/f-decryptPassword.html?hl=decrypt">Läs mer</a></p></td>
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

<!--## Deprecated compatibility {#deprecated-compatibility}

The following systems are deprecated for Campaign Classic. Please refer to the [Compatibility matrix](../../rn/using/compatibility-matrix.md) to upgrade to a newer version or move to a new system before the compatibility ends.-->

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


* Från och med version 22.1 är Adobe Campaign inte längre kompatibelt med CentOs 8.x (64 bitars). CentOS Linux 8 nådde slutet av sin livscykel (EOL) den 31 december 2021. [Läs mer](https://www.centos.org/centos-linux-eol/).

  Om du använde det här operativsystemet ska du anpassa implementeringen därefter. CentOS 7.x (64 bitars) och RHEL 8.x/7.x (64 bitars) stöds fortfarande.

* Från och med version 21.1.3 är Adobe Campaign inte längre kompatibelt med Debian 8.

* Från och med version 19.1 är Adobe Campaign inte längre kompatibelt med följande operativsystem.

   * CentOS 6. [Läs mer](https://wiki.centos.org/Download)
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

* Java JDK 7. [Läs mer](https://www.oracle.com/technetwork/java/javase/eol-135779.html)
* Libre Office 3.5/4.3/5.x utom när det är inbäddat i ett annat verktyg. [Läs mer](https://wiki.documentfoundation.org/ReleasePlan/Archive#End-of-Life_Releases)

### Databasmotorer {#dbe-eol}

Adobe har inte stöd för följande databasmotorer eftersom de har tagits bort av redigeraren. Kunder som kör dessa versioner måste uppgradera till den senaste versionen eller byta till en annan.

Se [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md) för Campaign för att få tillgång till en lista över kompatibla versioner.

**FDA (FEDERERAD DATAÅTKOMST)**

Från och med version 20.2 är Adobe Campaign inte längre kompatibelt med följande FDA-server:

* DB2 UDB 10.5

Från och med vårversionen 19.1 är Adobe Campaign inte längre kompatibelt med följande FDA-servrar:

* PostgreSQL 9.3.
* MySQL 5.5.
* DB2 9.5.
* Teradata 14 – 14.1.

Campaign Classic är inte kompatibelt med följande servrar i federerad dataåtkomst (FDA). Använd senare versioner eller system.

* DB2 UDB 9.5, 9.7.
* Oracle 9i och 10G R2.
* PostgreSQL-versioner upp till 9.6 har nått slutet av livscykeln.
* MSSQL 2000, 2005 och 2008 R2.
* MySQL 5.1.
* InfiniDB har nått slutet av sin livscykel.
* Teradata 13, 13.1.
* Netezza 6.02 och 7.0. Netezza har nått slutet av sin livscykel.
* AsterData 5.0. AsterData har nått slutet av sin livscykel.
* Sybase IQ 15.2, 15.4, 15.5 och Sybase ASE 15.0.
* Hadoop via HiveSQL: Hadoop 2.7.3 och HiveSQL 1.2.1. Adobe Campaign Classic har fortfarande stöd för de listade versionerna av Hadoop via HiveSQL via federerad dataåtkomst (FDA). Dessa versioner slås dock ihop med: HortonWorks (HDP 2.4.X, 2.5.x och 2.6.x) och HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5) och 3.6 (HDP 2.6)

**RDBMS-SERVER**

Från och med vårversionen 19.1 är Adobe Campaign inte längre kompatibelt med följande RDBMS-servrar:

* Oracle 10GR2
* PostgreSQL 9.0 till 9.3
* SQL Server 2005
* MySQL 5.1
* DB2 UDB 9.7

PostgreSQL-versioner upp till 9.6 har nått slutet av livscykeln. De stöds därför inte av Adobe Campaign.

### SMS-kopplingar {#sms-eol}

Från och med version 20.2 är äldre SMS-kopplingar inaktuella. Adobe Campaign är inte kompatibelt med:

* Generisk SMPP (SMPP version 3.4 med stöd för binärt läge)
* Sybase365 (SAP SMS 365)
* CLX Communications
* Tele2
* O2
* iOS

### CRM-kopplingar {#crm-connectors}

Följande CRM-kopplingar är inte längre kompatibla med Campaign från och med Campaign version 21.1:

* Soap API – lokal: 2007, 2015 och 2016
* Soap API – online: 2015 och 2016
* Webb-API – Microsoft Dynamics CRM 2016
* Webb-API – Microsoft Dynamics CRM 2016 uppdatering 1
* Oracle On Demand-API
