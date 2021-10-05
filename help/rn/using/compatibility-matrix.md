---
product: campaign
title: Kompatibilitetsmatris för Campaign Classic
description: Kompatibilitetsmatris för Campaign Classic
feature: Overview
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: 134f248fbcd456573365d5b32831b75dac4b73de
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 86%

---

# Kompatibilitetsmatris{#compatibility-matrix}

![](../../assets/v7-only.svg)

Det här dokumentet listar alla system och komponenter som stöds för [den senaste builden](../../rn/using/latest-release.md) av **Adobe Campaign Classic v7**. Produkter och versioner som inte ingår i den här listan är inte kompatibla med Adobe Campaign.

Se kompatibilitetsmatrisen för [[!DNL Gold Standard] ](../../rn/using/compatibility-matrix-gs.md), om du använder [!DNL Gold Standard].

## Viktiga anteckningar{#important-notes}

Om inget annat anges stöds alla mindre versioner.

Den [senaste versionen](../../rn/using/latest-release.md) av Adobe Campaign Classic är kompatibel med alla system och verktyg som listas på den här sidan. När specifika versioner av dessa system och verktyg från tredje part når slutet av sin livscykel med sina respektive utgivare är Adobe Campaign inte längre kompatibelt med dessa versioner. De tas sedan bort från vår kompatibilitetsmatris i den följande produktversionen. Se till att du använder versioner av system som stöds i kompatibilitetsmatrisen för att undvika problem.

Besök [den här sidan](../../rn/using/deprecated-features.md) för mer information om inaktuella objekt.

>[!CAUTION]
>
>Den här matrisen uppdateras regelbundet med nya objekt som stöds och inaktuella objekt som tas bort.

## Operativsystem{#OperatingSystems}

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
<p>10 (64 bitars)</p>
<p>9 (64 bitars)</p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>8.x (64 bitars)</p>
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

## Webbservrar{#WebServers}

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
<p>13.x</p>
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
<p>2012 – SP1 och SP2</p>
<p>Varning: Microsoft SQL Server stöds inte som primär databas när Campaign-servern körs i Linux. [Läs mer](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers).</p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>PostgreSQL är standarddatabasservern för värdbaserade miljöer.

## CRM-kopplingar{#CRMconnectors}

CRM-system som är kompatibla med Adobe Campaign listas nedan. [Läs ](../../platform/using/crm-connectors.md) mer om Campaign CRM-anslutningar.

<table>
<tbody>
<tr>
<td>Kopplings-API för Salesforce</td>
<td>
<p>API-version 49</p>
</td>
</tr>
<tr>
<td>Microsoft Dynamics-koppling</td>
<td>
<p>Webb-API</p>
</td>
</tr>
</tbody>
</table>

## Federerad dataåtkomst (FDA){#FederatedDataAccessFDA}

Externa databaser som är kompatibla med Adobe Campaign [Federated Data Access Module](../../installation/using/about-fda.md) listas nedan.

<table>
<tbody>
<tr>
<td>Vertica</td>
<td> </td>
</tr>
<tr>
<td>Google Big Query</td>
<td> </td>
</tr>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
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
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>13.x</p>
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
<p>version 1 SPS 12</p>
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

## Client Console {#ClientConsoleoperatingsystems}

Följande operativsystem och webbläsare **krävs** för att använda [Campaign Client Console](../../installation/using/installing-the-client-console.md).

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

[]
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


## Mobilt SDK{#MobileSDK}

Du kan använda Campaign för att [skicka push-meddelanden](../../delivery/using/about-mobile-app-channel.md) på de operativsystem som listas nedan med hjälp av den associerade [mobil-SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md).

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

Följande webbläsare är kompatibla med Campaign för [webbåtkomst](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

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


## Mer som det här{#Morelikethis}

* [Versionsinformation om Campaign Classic ](../../rn/using/latest-release.md)
* [Kampanjens allmänna arkitektur](../../installation/using/general-architecture.md)
* [Rekommendationer för maskinvarustorlek](../../technotes/using/hardware-sizing.md)
* [Inaktuella funktioner och system](../../rn/using/deprecated-features.md)
* [Procedur för builduppgradering](../../production/using/build-upgrade.md)
