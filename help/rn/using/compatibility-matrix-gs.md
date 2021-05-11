---
solution: Campaign Classic
product: campaign
title: Kompatibilitetsmatris för Campaign [!DNL Gold Standard]
description: Kompatibilitetsmatris för  [!DNL Gold Standard] -versionen av Campaign Classic
feature: Översikt
role: Business Practitioner
level: Beginner
exl-id: 5c0ccaf6-7f82-4e4b-9247-261dbd0f127c
translation-type: tm+mt
source-git-commit: 548ed5710cced016606283198f81a8f13c65ac10
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 91%

---

# [!DNL Gold Standard] Kompatibilitetsmatris{#compatibility-matrix-gs}

Det här dokumentet beskriver alla system och komponenter som stöds för builden 19.1 av **Adobe Campaign Classic[!DNL Gold Standard]**. Produkter och versioner som inte ingår i den här listan är inte kompatibla med den här versionen av Adobe Campaign.

## Viktiga anteckningar{#important-notes-gs}

Om inget annat anges stöds alla mindre versioner.

Adobe Campaign Classic är kompatibelt med alla system och verktyg som listas på den här sidan. När specifika versioner av dessa system och verktyg från tredje part når slutet av sin livscykel med sina respektive utgivare är Adobe Campaign inte längre kompatibelt med dessa versioner. De tas sedan bort från vår kompatibilitetsmatris i följande produktversion. Se till att du använder versioner av system som stöds i kompatibilitetsmatrisen för att undvika problem.

## Operativsystem{#OperatingSystems-gs}

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

## Webbservrar{#WebServers-gs}

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

## Verktyg{#Tools-gs}

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
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 – SP1 och SP2</p>
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
>PostgreSQL är den standardiserade databasservern för värdbaserade miljöer.

## CRM-kopplingar{#CRMconnectors-gs}

<table>
<tbody>
<tr>
<td>API för Salesforce-anslutning</td>
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
<tr><td>Oracle On Demand-API</td>
<td>
<p>API för Webbtjänster v1.0</p>
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

## Federerad dataåtkomst (FDA){#FederatedDataAccessFDA-gs}

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


## Klientkonsol {#ClientConsoleoperatingsystems}

:varning: Följande operativsystem och webbläsare krävs för att använda Campaign Client Console.

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

### Webbläsare

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

## Mobile SDK{#MobileSDK}

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

## Webbläsare{#Browsers}

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

## Mer som detta{#Morelikethis-gs}

* [Versionsinformation om Campaign Classic ](../../rn/using/latest-release.md)
* [Installationshandbok](../../installation/using/general-architecture.md)
* [Inaktuella funktioner och system](../../rn/using/deprecated-features.md)
* [Procedur för versionsuppgradering](https://helpx.adobe.com/sv/campaign/kb/acc-build-upgrade.html)
