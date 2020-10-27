---
title: Standardkompatibilitetsmatris för guld
description: Kompatibilitetsmatris för Campaign Classic för Gold Standard
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7p
translation-type: tm+mt
source-git-commit: e615b2420d126cd42ed52257491282b36975f9ff
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 13%

---


# Standardkompatibilitetsmatris för guld{#compatibility-matrix-gs}

I det här dokumentet finns en lista över alla system och komponenter som stöds för byggen med **Adobe Campaign Classic Gold Standard** 19.1. Produkter och versioner som inte ingår i den här listan är inte kompatibla med Adobe Campaign.

## Viktiga anteckningar{#important-notes-gs}

Om inget annat anges stöds alla mindre releaser.

Adobe Campaign Classic är kompatibelt med alla system och verktyg som listas på den här sidan. Eftersom specifika versioner av dessa system och verktyg från tredje part når slutet av livscykeln (EOL) med sina respektive skapare, kommer Adobe Campaign inte längre att vara kompatibelt med dessa versioner, och de kommer att tas bort från vår kompatibilitetsmatris i den kommande produktversionen. Se till att du använder versioner av system som stöds i kompatibilitetsmatrisen för att undvika problem.

## Operating Systems{#OperatingSystems-gs}

<table> 
<tbody> 
<tr> 
<td>CentOs</td>
<td>
<p>8,x (64 bitar)</p>
<p>7.x (64 bitar)</p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>9 (64 bitar)</p>
<p>8 (64 bitar)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>7.x (64 bitar)</p>
<p><strong>Viktigt:</strong> Om du använder RHEL måste du kunna inaktivera SELinux eller låta dina arkitekter skriva anpassade SELinux-regler för att kontrollera att en aktiverad SELinux inte orsakar problem med Campaign-åtgärder.</p>
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

## Web Servers{#WebServers-gs}

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 i Windows Server 2016</p>
<p>8.5 i Windows Server 2012 R2</p>
<p>8.0 i Windows Server 2012 - Windows 8</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2.4 för RHEL7 - CentOS 7, Debian 8/9, Windows (64 bitar)</p>
<p>2.2 för RHEL6 - Endast CentOS 6 (64 bitar)</p>
</td>
</tr>
</tbody>
</table>

## Verktyg{#Tools-gs}

<table>
<tbody>
<tr>
<td>Java Development Kit (JDK)</td>
<td>
<p>8</p>
<p>Ansökan har godkänts för Java Development Kit (JDK) som utvecklats av Oracle samt för OpenJDK.</p>
</td>
</tr>
<tr>
<td>Libre</td>
<td>
<p>6 (och tidigare versioner om de är inbäddade i systemet)</p>
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

## RDBMS-servrar{#RDBMSservers-gs}

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
<p>2018</p>
<p>2018 R2</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 - SP1 och SP2</p>
<p>Varning: Microsoft SQL Server stöds inte som primär databas när Campaign-servern körs i Linux. <a href="https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">Läs mer</a>.</p>
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
>PostgreSQL är standarddatabasservern för hostingmiljöer.

## CRM connectors{#CRMconnectors-gs}

<table>
<tbody>
<tr>
<td>Salesforce-anslutnings-API</td>
<td>
<p>API-version 37</p>
</td>
</tr>
<tr>
<td>SFDC API</td>
<td>
<p>API version 21</p>
<p>API-version 15</p>
</td>
</tr>
<tr><td>API för Oracle On Demand</td>
<td>
<p>Webbtjänster v1.0 API</p>
</td>
</tr>
<tr>
<td>MS Dynamics</td>
<td>
<p>Soap API - lokal: 2007, 2015, 2016</p>
<p>Soap API - online: 2015, 2016</p>
<p>Webb-API - lokalt och online: 365, 2016, 2016 uppdatering 1</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA-gs}

<table>
<tbody>
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
<p>version 1 SP12 eller senare</p>
</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
</tr>
</tbody>
</table>

## Operativsystem för Client Console{#ClientConsoleoperatingsystems-gs}

<table>
<tbody>
<tr>
<td>Windows Server</td>
<td>
<p>2016</p>
<p>2012</p>
</td>
</tr>
<tr>
<td>Windows</td>
<td>
<p>Seven</p>
<p>8</p>
<p>10 (rekommenderas för japanska förekomster)</p>
</td>
</tr>
</tbody>
</table>

## Mobile SDK{#MobileSDK-gs}

<table>
<tbody>
<tr>
<td>Android</td>
<td>
<p>7.x, 8.x, 9.0</p>
<p>med mobil SDK build 1.0.27.</p>
</td>
</tr>
<tr>
<td>iOS</td>
<td>
<p>iOS 9-12</p>
<p>med mobil SDK build 1.0.25, kompatibel med 32- och 64-bitarsversioner.</p>
</td>
</tr>
</tbody>
</table>

## Webbläsare{#Browsers-gs}

Den senaste versionen stöds i följande webbläsare: Microsoft Edge, Mozilla Firefox, Google Chrome, Safari.

Internet Explorer 11 stöds.

## Mer som detta{#Morelikethis-gs}

* [Versionsinformation om Campaign Classic](../../rn/using/latest-release.md)
* [Installationshandbok](../../installation/using/general-architecture.md)
* [Föråldrade funktioner och system](../../rn/using/deprecated-features.md)
* [Uppgraderingsprocedur](https://helpx.adobe.com/se/campaign/kb/acc-build-upgrade.html)
