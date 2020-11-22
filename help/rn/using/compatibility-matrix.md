---
solution: Campaign Classic
product: campaign
title: Kompatibilitetsmatris
description: Kompatibilitetsmatris för Campaign Classic
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 13%

---


# Kompatibilitetsmatris{#compatibility-matrix}

I det här dokumentet visas alla system och komponenter som stöds för [den senaste versionen](../../rn/using/latest-release.md) av **Adobe Campaign Classic**. Produkter och versioner som inte ingår i den här listan är inte kompatibla med Adobe Campaign.

Om du använder Gold Standard läser du i [Gold Standard-kompatibilitetsmatrisen](../../rn/using/compatibility-matrix-gs.md).

## Viktiga anteckningar{#important-notes}

Om inget annat anges stöds alla mindre releaser.

I den [senaste versionen](../../rn/using/latest-release.md)är Adobe Campaign Classic kompatibelt med alla system och verktyg som listas på den här sidan. Eftersom specifika versioner av dessa system och verktyg från tredje part når slutet av livscykeln (EOL) med sina respektive skapare, kommer Adobe Campaign inte längre att vara kompatibelt med dessa versioner, och de kommer att tas bort från vår kompatibilitetsmatris i den kommande produktversionen. Se till att du använder versioner av system som stöds i kompatibilitetsmatrisen för att undvika problem.

Mer information om borttagna objekt finns på [den här sidan](../../rn/using/deprecated-features.md).

>[!CAUTION]
>
>Den här matrisen uppdateras regelbundet med nya objekt som stöds och borttagna objekt.

## Operating Systems{#OperatingSystems}

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
<p>10 (64 bitar)</p>
<p>9 (64 bitar)</p>
<p>8 (64 bitar)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8,x (64 bitar)</p>
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

## Web Servers{#WebServers}

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
</td>
</tr>
</tbody>
</table>

## Verktyg{#Tools}

<table>
<tbody>
<tr>
<td>Java Development Kit (JDK)</td>
<td>
<p>11</p>
<p>9</p>
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

## RDBMS-servrar{#RDBMSservers}

>[!NOTE]
>
>RDBMS-drivrutinen måste matcha RDBMS-serverversionen.

<table>
<tbody>
<tr>
<td>Oracle</td>
<td>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>12.x</p>
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
<p>2012 - SP1 och SP2</p>
<p>Varning: Microsoft SQL Server stöds inte som primär databas när Campaign-servern körs i Linux. <a href="https://docs.adobe.com/content/help/en/campaign-classic/using/installing-campaign-classic/prerequisites-and-recommendations-/database.html#Microsoft_SQL_Server">Läs mer</a>.</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL är standarddatabasservern för hostingmiljöer.

## CRM-kopplingar{#CRMconnectors}

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
<tr><td>Oracle On Demand-API</td>
<td>
<p>Webbtjänster v1.0 API</p>
</td>
</tr>
<tr>
<td>MS Dynamics</td>
<td>
<p>Webb-API: Dynamics 365 On-Local and Online</p>
</td>
</tr>
</tbody>
</table>

## Federated Data Access (FDA){#FederatedDataAccessFDA}

<table>
<tbody>
<tr>
<td>Microsoft Azure synapse Analytics</td>
<td> </td>
</tr>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
</td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>12.x</p>
<p>11.x</p>
<p>10.x</p>
<p>9.6.x</p>
<p>9.5.x</p>
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
<p>version 1 SP12 eller senare</p>
</td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
</tr>
</tbody>
</table>

## Operativsystem för Client Console{#ClientConsoleoperatingsystems}

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
<p>8</p>
<p>10 (rekommenderas för japanska förekomster)</p>
</td>
</tr>
</tbody>
</table>

## Mobile SDK{#MobileSDK}

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
<p>iOS 9-14</p>
<p>med mobil SDK build 1.0.26, kompatibel med 32- och 64-bitarsversioner.</p>
</td>
</tr>
</tbody>
</table>

## Webbläsare{#Browsers}

Den senaste versionen stöds i följande webbläsare: Microsoft Edge, Mozilla Firefox, Google Chrome, Safari.

Internet Explorer 11 stöds.

## Mer som detta{#Morelikethis}

* [Versionsinformation om Campaign Classic](../../rn/using/latest-release.md)
* [Installationshandbok](../../installation/using/general-architecture.md)
* [Föråldrade funktioner och system](../../rn/using/deprecated-features.md)
* [Uppgraderingsprocedur](../../production/using/build-upgrade.md)
