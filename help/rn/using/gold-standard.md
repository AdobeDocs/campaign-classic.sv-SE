---
product: campaign
title: ”[!DNL Gold Standard]-versioner”
description: Versionsinformation och kompatibilitetsmatris för Campaign Classic [!DNL Gold Standard]
feature: Overview
role: User
level: Beginner
exl-id: 9e3a11b1-3070-4d90-91d5-7c559bdd500e
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: ht
source-wordcount: '1670'
ht-degree: 100%

---

# [!DNL Gold Standard]-versioner {#gold-standard}

![](../../assets/v7-only.svg)

På den här sidan hittar du versionsinformation och kompatibilitetsmatrisen för [!DNL Gold Standard]-versionerna.

## [!DNL Gold Standard]-versionsinformation


### ![](assets/do-not-localize/limited_2.png) [!DNL Gold Standard] version 12{#gs-12}

_7 september 2021_

Build 9032@554dbcd innehåller följande korrigering:

* Korrigerade ett problem som ledde till ett 500-fel när länken till ett webbprogram öppnades i en radleverans med spårning aktiverat.

_27 augusti 2021_

Build 9032@99a3894 innehåller följande korrigeringar:

* Funktionen för att spåra signaturer har förbättrats för att förhindra att fel länkas till hur tredjepartsverktyg (e-postklienter, webbläsare osv.) hanterar specialtecken. URL-parametrar är nu kodade.
* Korrigerade ett problem med datumväljare som kunde resultera i att en konsol visade felmeddelandet för blockering. (NEO-36345)

### ![](assets/do-not-localize/limited_2.png) [!DNL Gold Standard] version 11{#gs-11}

_14 april 2021_

Build 9032@d030c36 innehåller följande korrigering:

* Korrigerade en klientkonsolregression som orsakade bestående felmeddelanden på IMS-anslutningsskärmen. (NEO-34821)
* Konsolbuilden krävs för att upprätthålla [IMS-åtkomst](../../technotes/using/ims-updates.md).

**Endast konsoluppgraderingen är obligatorisk. Ingen serveruppgradering krävs.**

>[!CAUTION]
>
> * Om du ansluter till Campaign med ditt Adobe ID via Adobe Identity Management Service (IMS), är uppgradering obligatoriskt för både Campaign-servern och klientkonsolen för att kunna ansluta till Campaign efter **den 30 juni 2021**. [Läs mer](../../technotes/using/ims-updates.md)
> * Den här versionen innehåller en [säkerhetskorrigering](https://helpx.adobe.com/se/security/products/campaign/apsb21-04.html): Uppgraderingen är obligatorisk för att öka din miljösäkerhet.
> * Om du använder integreringen av Experience Cloud Triggers via oAuth-autentisering måste du gå över till Adobe I/O som beskrivs [på den här sidan](../../integrations/using/configuring-adobe-io.md). Det inaktuella autentiseringsläget oAuth med Campaign [har tagits bort](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) i **september 2021**. Värdmiljöer drar nytta av en förlängning till **23 februari 2022**. Kontakta Adobes kundtjänst för att förlänga supporten till februari 2022 om du är en lokal- eller hybridkund. Du måste ange [AppID:et för OAuth-applikationen](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) till Adobe.
>
>Läs mer i [[!DNL Gold Standard] avsnittet](../../rn/using/gold-standard.md)

_2 mars 2021_

Build 9032@10c2709 innehåller följande korrigering:

* Korrigerade en regression som förhindrade användning av vissa komponenter i konsolen, som datumväljaren och bildhantering i leveranser. (NEO-31453, NEO-31454)

**Endast konsoluppgraderingen är obligatorisk. Ingen serveruppgradering krävs.**

>[!NOTE]
>
> Anslut till [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) för att hämta den nya versionen. Läs om hur du föreslår en konsoluppdatering för alla slutanvändare [på den här sidan](../../installation/using/client-console-availability-for-windows.md).

_22 december 2020_

Version 9032@d3b452f innehåller följande förbättringar och korrigeringar:

* Anslutningsprotokollet har uppdaterats för att följa den nya IMS-autentiseringsmekanismen.

* Integreringsautentisering för utlösare som ursprungligen baserades på oAUTH-autentiseringsinställningar för åtkomst till pipelines har nu ändrats och flyttats till Adobe I/O. [Läs mer](../../integrations/using/configuring-adobe-io.md)

* Då [support för det äldre binära protokollet i iOS APN:er har upphört](https://developer.apple.com/news/?id=c88acm2b) uppdateras alla instanser som använder det här protokollet till HTTP/2-protokollet under efteruppgraderingen.

* Korrigerade ett säkerhetsproblem för att förstärka skyddet mot problem med SSRF (Server Side Request Forgery). (NEO-27777)

* Korrigerade ett problem som kunde få arbetsflöden att inte fungera när en **Berikandeaktivitet** kördes. (NEO-17338)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] version 10{#gs-10}

_7 juli 2020_

Build 9032@efd8a94 har följande korrigering:

Korrigerade ett problem som hindrade spårning från att fungera när signaturfunktionen var inaktiverad. (NEO-26411)

>[!CAUTION]
>
>Vi rekommenderar att du uppgraderar klientkonsolen till den som finns i den här versionen. Se [den här sidan](../../installation/using/installing-the-client-console.md)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] version 9{#gs-9}

_22 juni 2020_

Build 9032@800be2e har följande korrigeringar:

* iOS HTTP2-kopplingen har förbättrats (tredjepartsuppdateringar och felhantering). (NEO-25904, NEO-25903 och NEO-25799)

Följande korrigeringar är relaterade till spårningslänkens säkerhetsmekanism (läs mer i [checklistan försäkerhet och sekretess](https://helpx.adobe.com/se/campaign/kb/acc-security.html#signature-mechanism)):

* Korrigerade ett problem som hindrade spårningen av ”meddelandeklickningar” från att fungera (iOS- och Android-push-meddelanden). (NEO-25965)
* Korrigerade ett problem som kunde hindra dig från att öppna/klicka på spårnings-URL:er när du använde vissa äldre versioner av Outlook.  (NEO-25688)
* Korrigerade ett problem som förhindrade spårning av URL:er, som använder fragment i personaliseringsparametrar (ankartaggar med pundtecken), från att fungera. (NEO-25774)
* Korrigerade ett problem med tjänsten mot nätfiske. (NEO-25283)
* Korrigerade ett problem med spårning när särskilda anpassade spårningsformler användes. (NEO-25277)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] version 8{#gs-8}

_29 april 2020_

Build 9032@3a9dc9c har följande korrigeringar:

* Förbättrad säkerhet vid spårning av länkar i e-postmeddelanden. Detta är aktiverat som standard för alla kunder. Det finns ytterligare en förbättrad säkerhetsfunktion som kan aktiveras genom att kontakta kundtjänst. Mer information om funktionen och stegen för icke-värdbaserade kunder som vill aktivera den finns i [checklistan över säkerhet och sekretess](https://helpx.adobe.com/se/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>Om du upplever problem med push-meddelanden när du använder spårningslänkar eller leveranser med ankartaggar rekommenderar vi att du inaktiverar den nya signaturfunktionen för spårningslänkar. Förfarandet beskrivs [på den här sidan](https://helpx.adobe.com/se/campaign/kb/acc-security.html#signature-mechanism)

* Korrigerade ett problem som kunde förhindra att bilder visades i Line-leveranser. (NEO-23207)
* Ett problem med **filöverföringar** som hindrade SFTP-nyckelbaserad autentisering från att fungera i Debian 9 har korrigerats. (NEO-23183)
* Korrigerade ett problem som kunde påverka push-meddelanden när de skickades med hög frekvens. (NEO-20516)
* Korrigerade ett problem vid hantering av svar på erbjudanden som kunde leda till att webbservern kraschar. (NEO-19482)
* Korrigerade ett problem i LibreOffice-hanteringen som hindrade dig från att exportera rapporter. (NEO-20982)
* Korrigerade ett problem som orsakade ett fel när flera arbetsflöden uppgraderades med en undersökningsaktivitet.
* Förbättrad LibreOffice-hantering för att undvika fel vid förhandsgranskning av e-postmeddelanden med .odt-filer.
* Förbättrad hantering av Apache-kopplingar för att undvika latens i webbtjänsten.
* Förbättrad visning av versionstaggar (7 siffror) på menyn **Om**.
* Korrigerade en regression i listhanteringen som förhindrade att erbjudanden publicerades.
* Korrigerade en regression som fick arbetsflödet för rensning att krascha.
* Korrigerade en mindre regression i loggfilerna för arbetsflödet för rensning.

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] version 6{#gs-6}

_9 mars 2020_

Build 9032@19f73c5 har följande korrigering:

* Korrigerade ett problem med externa konton som använder FTP över SSL. (NEO-20498)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] version 5{#gs-5}

_17 december 2019_

Build 9032@d6b8062 har följande korrigering:

* Korrigerade ett problem med spårning i följande kommunikationskanaler: mobil (SMS, MMS), push (iOS, Android) och sociala nätverk (Facebook, Twitter). (NEO-19595)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] version 4{#gs-4}

_11 december 2019_

Build 9032@bc4a935 har följande korrigering:

* Korrigerade ett problem med prestandan när meddelanden skickades med en MSSQL-databas. (NEO-17558)

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] version 3{#gs-3}

_20 november 2019_

Build 9032@3468c7b har följande korrigeringar:

* Korrigerade ett problem med inloggningen via IMS-autentisering. (NEO-17312)
* Korrigerade ett problem när kumulativa rapporter för flera leveranser visades. (NEO-18165)
* Korrigerade ett problem som kunde blockera eller få webbservern att krascha.

### ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] version 2{#gs-2}

_19 september 2019_

Build 9032@cee805c har följande korrigeringar:

* Korrigerade ett problem när CRM-kopplingen för Salesforce användes. (NEO-17712)
* Korrigerade ett problem med index som kunde orsaka prestandaproblem när transaktionsmeddelanden skickades.

### ![](assets/do-not-localize/red_2.png) version 19.1.4 – build 9032{#release-19-1-4-build-9032}

_13 augusti 2019_

Den första versionen 19.1.4 innehåller följande korrigeringar:

* Korrigerade ett problem med schemaläggaraktiviteten som genererade oönskade felmeddelanden under guidekonfigurationen. Återställer uppdatering från NEO-11662. (NEO-17097)
* Korrigerade en regression som orsakades av NEO-12727 och som kunde leda till att arbetsflöden stoppades när en testaktivitet kördes två gånger. (NEO-16835)
* Korrigerade ett problem som ledde till att en felaktig HTTP-kod returnerades (HTTP 200 OK i stället för HTTP 403 Forbidden) när en ogiltig eller utgången sessionstoken användes i API-anrop. (NEO-16826)
* Korrigerade ett problem med DKIM-nyckeln som inte längre var inbäddad i e-postmeddelanden vilket orsakade leveransproblem. (NEO-16804)
* Korrigerade flera problem med arbetsflödesplanering. Arbetsflödena schemalades att köras en gång om dagen utan att konfigurationen av Scheduler hade beaktats. (NEO-16619 och NEO-16426)


## [!DNL Gold Standard]-kompatibilitetsmatris{#compatibility-matrix-gs}

Det här avsnittet listar alla system och komponenter som stöds för versioner 19.1 av **Adobe Campaign Classic[!DNL Gold Standard]**. Produkter och versioner som inte ingår i den här listan är inte kompatibla med den här versionen av Adobe Campaign.

>[!CAUTION]
>Om inget annat anges stöds alla mindre versioner.
>
>Adobe Campaign Classic är kompatibelt med alla system och verktyg som listas på den här sidan. När specifika versioner av dessa system och verktyg från tredje part når slutet av sin livscykel med sina respektive utgivare är Adobe Campaign inte längre kompatibelt med dessa versioner. De tas sedan bort från vår kompatibilitetsmatris i följande produktversion. Se till att du använder versioner av system som stöds i kompatibilitetsmatrisen för att undvika problem.

### Operativsystem{#OperatingSystems-gs}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8.x (64 bitars)</p>
<p>7.x (64 bitars)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>9 (64 bitars)</p>
<p>8 (64 bitars)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x (64 bitars)</p>
<p><strong>Viktigt:</strong> Om du använder RHEL måste du kunna inaktivera SELinux eller låta dina utvecklare skriva anpassade SELinux-regler för att kontrollera att en aktiverad SELinux inte orsakar problem med åtgärder i Campaign.</p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012 R2</p>
<p>2012</p>
</td>
</tr>
</tbody>
</table>

### Webbservrar{#WebServers-gs}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 i Windows Server 2016</p>
<p>8.5 i Windows Server 2012 R2</p>
<p>8.0 i Windows Server 2012 – Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 för RHEL7 – CentOS 7, Debian 8/9, Windows (64 bitars)</p>
<p>2.2 för RHEL6 – endast CentOS 6 (64 bitars)</p>
</td>
</tr>
</tbody>
</table>

### Verktyg{#Tools-gs}

<table>
<tbody>
<tr>
<td>Java Development Kit (JDK)</td>
<td>
<p>8</p>
<p>Programvaran har godkänts för Java Development Kit (JDK) som har utvecklats av Oracle samt för OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre Office</td>
<td>
<p>6 (och föregående versioner om de är inbäddade i systemet)</p>
</td>
</tr>
<tr>
<td>SpamAssassin</td>
<td>
<p>3.4.x</p>
</td>
</tr>
</tbody>
</table>

### RDBMS-servrar{#RDBMSservers-gs}

>[!NOTE]
>
>RDBMS-drivrutinen måste matcha RDBMS-serverversionen.

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
<p>9.4.x</p>
<p>Obs! Du kan också använda Amazon RDS för PostgreSQL med de versioner som anges ovan.</p>
</td>
</tr>
<tr>
<td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 – SP1 och SP2</p>
<p>Varning: Microsoft SQL Server stöds inte som primär databas när Campaign-servern körs i Linux.</p>
</td>
</tr>
<tr>
<td>DB2 UDB</td>
<td>
<p>9.7</p>
<p>Varning: DB2 UDB tillåts inte för nya installationer.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL är standarddatabasservern för värdbaserade miljöer.

### CRM-kopplingar{#CRMconnectors-gs}

<table>
<tbody>
<tr>
<td>Kopplings-API för Salesforce</td>
<td>
<p>API-version 37</p>
</td>
</tr>
<tr>
<td>SFDC API</td>
<td>
<p>API-version 21</p>
<p>API-version 15</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics</td>
<td>
<p>Soap API – lokal: 2007, 2015 och 2016</p>
<p>Soap API – online: 2015 och 2016</p>
<p>Webb-API – lokalt och online: 365, 2016, 2016 uppdatering 1</p>
</td>
</tr>
</tbody>
</table>

### Federerad dataåtkomst (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.4.x</p>
</td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 och SP2</p>
</td>
</tr>
<tr><td>MySQL</td>
<td>
<p>5.7</p>
</td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>16.20</p>
<p>16</p>
<p>15.10</p>
<p>15.0</p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>7.2</p>
</td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>version 1 SPS 12</p>
</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
</td>
</tr>
</tbody>
</table>


### Client Console {#ClientConsoleoperatingsystems}

:warning: Följande operativsystem och webbläsare krävs för att använda klientkonsolen i Campaign.

### Operativsystem

<table>
<tbody>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Microsoft Windows</td>
<td>
<p>8</p>
<p>10 (rekommenderas för japanska instanser)</p>
</td>
</tr>
</tbody>
</table>

#### Webbläsare

<table>
<tbody>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>

### Mobilt SDK{#MobileSDK}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x, 8.x, 9.0</p>
<p>med mobil SDK version 1.0.27.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9–14</p>
<p>med mobil SDK version 1.0.26, kompatibel med 32- och 64-bitarsversioner.</p>
</td>
</tr>
</tbody>
</table>

### Webbläsare{#Browsers}

Följande webbläsare är kompatibla med Campaign for Web Access.

<table>
<tbody>
<tr>
<td>
<p>Microsoft Edge</p>
</td>
<td>
<p>Senaste versionen</p>
</td>
</tr>
<tr>
<td>
<p>Mozilla Firefox</p>
</td>
<td>
<p>Senaste versionen</p>
</td>
</tr>
<tr>
<td>
<p>Google Chrome</p>
</td>
<td>
<p>Senaste versionen</p>
</td>
</tr>
<tr>
<td>
<p>Safari</p>
</td>
<td>
<p>Senaste versionen</p>
</td>
</tr>
<tr>
<td>
<p>Microsoft Internet Explorer</p>
</td>
<td>
<p>11</p>
</td>
</tr>
</tbody>
</table>
