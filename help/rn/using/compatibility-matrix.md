---
product: campaign
title: Kompatibilitetsmatris för Campaign Classic
description: Kompatibilitetsmatris för Campaign Classic
feature: Release Notes
role: User
level: Beginner
exl-id: b8c1f287-06f4-4c34-8cca-b0c7676abbc2
source-git-commit: b23632d0718d62d61e94e636937b93aa39bbe43f
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 100%

---

# Kompatibilitetsmatris {#compatibility-matrix}

Den [senaste versionen](../../rn/using/latest-release.md) av Adobe Campaign Classic v7 är kompatibel med alla system och verktyg på den här sidan. När specifika versioner av dessa system och verktyg från tredje part når slutet av sin livscykel med sina respektive utgivare är Adobe Campaign inte längre kompatibelt med dessa versioner. De tas sedan bort från vår kompatibilitetsmatris i följande produktversion. Se till att du använder versioner av system som stöds i kompatibilitetsmatrisen för att undvika problem. Besök [den här sidan](../../rn/using/deprecated-features.md) för mer information om inaktuella objekt.

Om inget annat anges stöds alla mindre versioner.

>[!CAUTION]
>
>Den här matrisen uppdateras regelbundet med nya system och verktyg som stöds och inaktuella som tas bort.

## Operativsystem {#OperatingSystems}

Om du är en lokal/hybrid-kund måste du installera Adobe Campaign i något av operativsystemen som listas nedan. Läs mer om installationsstegen för Campaign Classic v7 på [den här sidan](../../installation/using/application-server.md).

<table> 
<tbody> 
<td><strong>Operativsystem</strong></td>
<td><strong>Operativsystemversion</strong></td>
<td><strong>Lägsta Campaign-version</strong></td>
<tr> 
<td>CentOs</td>
<td>
<p>7.x</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>Debian</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>RHEL</td>
<td>
<p>9.x</p>
<p>8.x</p>
<p>7.x</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4</p>
<p>v7.2</p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!IMPORTANT]
>
>Om du använder RHEL måste du kunna inaktivera [SELinux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#selinux) eller låta dina utvecklare skriva anpassade SELinux-regler för att kontrollera att en aktiverad SELinux inte orsakar problem med åtgärder i Campaign.

## Webbservrar {#WebServers}

Som lokal kund/hybridkund måste du, beroende på ditt operativsystem, integrera Campaign i en av de webbservrar som anges nedan. Mer information om konfigurationssteg för webbservrar finns på [den här sidan](../../installation/using/integration-into-a-web-server-for-windows.md) (för Windows) och [den här sidan](../../installation/using/integration-into-a-web-server-for-linux.md) (för Linux).

<table>
<tbody>
<tr>
<td>Microsoft IIS</td>
<td>
<p>10.0 på Windows Server</p>
</td>
</tr>
<tr>
<td>Apache</td>
<td>
<p>2,4</p>
</td>
</tr>
</tbody>
</table>

## Verktyg {#Tools}

Som lokal kund/hybridkund måste du installera och konfigurera de verktyg som anges nedan. [Läs mer](../../installation/using/application-server.md).

<table>
<tbody>
<td><strong>Verktyg</strong></td>
<td><strong>Version</strong></td>
<td><strong>Lägsta Campaign-version</strong></td>
<tr>
<td><p>Java Development Kit (JDK)</p>
<p>Läs mer på <a href="../../installation/using/application-server.md#jdk" target="_blank">den här sidan</a>.</p>
</td>
<td>
<p>11</p>
<p>9</p>
<p>8</p>
<p></p>
</td>
<td>
<p>krävs från och med v7.4.1</p>
<p>tills v7.4.1</p>
<p>tills v7.4.1</p>
</tr>
<tr>
<td><p>Libre Office</p></td>
<td>
<p>7 (och föregående versioner om de är inbäddade i systemet)</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td><p>SpamAssassin</p></td>
<td>
<p>3.4.x</p>
</td>
<td>
<p></p>
</td>
</tbody>
</table>

## Relation Database Management Systems (RDBMS) {#RDBMSservers}

Om du är en lokal kund/hybridkund måste du installera och konfigurera en av de databaser som listas nedan. [Läs mer](../../installation/using/creating-and-configuring-the-database.md).


<table>
<tbody>
<td><strong>Databassystem</strong></td>
<td><strong>Databasversion</strong></td>
<td><strong>Lägsta Campaign-version</strong></td>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g R2</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>
<p>v7.3.2</p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>Microsoft SQL Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>* RDBMS-drivrutinen måste matcha RDBMS-serverversionen.
>
>* Microsoft SQL Server stöds inte som primär databas när Campaign-servern körs i Linux. [Läs mer](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers).
>
>* Du kan också använda Amazon RDS för PostgreSQL med versionerna som anges ovan.
>
>* PostgreSQL är RDBMS för värd/hanterade molntjänstmiljöer.


## CRM-kopplingar {#CRMconnectors}

CRM (Customer Relationship Management)-system som är kompatibla med Adobe Campaign listas nedan. [Läs mer](../../platform/using/crm-connectors.md) om CRM-kopplingar i Campaign.

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

Externa databaser som är kompatibla med [modulen för federerad dataåtkomst](../../installation/using/about-fda.md) i Adobe Campaign, listas nedan. Kompatibiliteten beror på din [värdmodell](../../installation/using/hosting-models.md).

Miljöerna **Managed Services** (värd), **Hybrid** och **Lokal** kan ansluta Campaign till följande externa databassystem:

<table>
<tbody>
<td><strong>Databassystem</strong></td>
<td><strong>Databasversion</strong></td>
<td><strong>Lägsta Campaign-version</strong></td>
<tr>
<td>Amazon Redshift</td>
<td><p> </p>
<td>v7.0 19.1.4</td>
</td>
</tr>
<tr>
<td>Google BigQuery</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>PostgreSQL</td>
<td>
<p>14.x</p>
<p>13.x</p>
<p>12.x</p>
<p>11.x</p>
</td>
<td>v7.0 19.1.4</td>
</tr>
<tr>
<td>Snowflake</td>
<td> </td>
<td>v7.2</td>
</tr>
<tr>
<td>Vertica Analytics</td>
<td> </td>
<td>v7.0 19.1.4 </td>
</tr>
</tbody>
</table>

Miljöerna **Hybrid** och **Lokal** kan dessutom ansluta Campaign till följande externa databassystem. Dessa system är **inte kompatibla** med Campaigns **Managed Services**-värdmiljöer.

<table>
<tbody>
<td><strong>Databassystem</strong></td>
<td><strong>Databasversion</strong></td>
<td><strong>Lägsta Campaign-version</strong></td>
<tr>
<td>Microsoft Azure Synapse Analytics</td>
<td> </td>
<td></td>
</tr>
<tr><td>MySQL</td>
<td>
<p>8</p>
<p>5.7</p>
</td>
<td>
<p>v7.3</p>
<p></p>
</td>
</tr>
<tr>
<td>Netezza</td>
<td>
<p>v7.2</p>
</td>
<td></td>
</tr>
<tr>
<td>Oracle</td>
<td>
<p>23c</p>
<p>19c</p>
<p>18c</p>
<p>12c</p>
<p>11g</p>
</td>
<td>
<p>v7.4</p>
<p></p>
<p></p>
<p></p>
<p></p>
</td>
</tr>
<tr>
<td>SAP HANA</td>
<td>
<p>version 1 SPS 12</p>
</td>
<td></td>
</tr>
<tr><td>SQL Server</td>
<td>
<p>2022 (från och med Campaign v7.4)</p>
<p>2019</p>
<p>2017</p>
<p>2016</p>
<p>2014</p>
<p>2012 SP1 och SP2</p>
</td>
<td></td>
</tr>
<tr>
<td>Sybase</td>
<td>
<p>IQ 16</p>
<p>ASE 15.7</p>
</td>
<td></td>
</tr>
<tr>
<td>Teradata</td>
<td>
<p>17.x</p>
<p>16.x (senaste versionen)</p>
</td>
<td></td>
</tr>
<tr><td>Hadoop via HiveSQL</td>
<td>
<p>HortonWorks HDP 2.4.X, 2.5.x, 2.6.x</p>
<p>HDInsight 3.4 (HDP 2.4), 3.5 (HDP 2.5), 3.6 (HDP 2.6)</p>
<p>Cloudera CDH6.x</p>
</td>
<td></td>
</tr>
</tbody>
</table>


## Klientkonsol {#ClientOS}

Följande operativsystem och webbläsare **krävs** för att använda [klientkonsolen i Campaign](../../installation/using/installing-the-client-console.md).

### Operativsystem

<table>
<tbody>
<td><strong>System</strong></td>
<td><strong>OS-version</strong></td>
<td><strong>Lägsta Campaign-version</strong></td>
<tr>
<td>Microsoft Windows</td>
<td>
<p>11</p>
<p>10</p>
</td>
<td>
<p>v7.3</p>
<p></p>
<p></p>
</tr>
<tr>
<td>Microsoft Windows Server</td>
<td>
<p>2022</p>
<p>2019</p>
<p>2016</p>
</td>
<td>
<p>v7.4.1</p>
<p>v7.2.1</p>
<p></p>
</tbody>
</table>

### Microsoft WebView2-körtid {#webview}

Den senaste versionen av Microsoft Edge WebView2 är obligatorisk för Campaign-klientkonsolen.

Ladda ned Microsoft Edge WebView2 från [webbplatsen för Microsoft Developer](https://www.adobe.com/go/acc-ms-webview2-runtime-download).


## Mobil-SDK {#MobileSDK}

Du kan också använda Campaign för att [skicka pushnotiser](../../delivery/using/about-mobile-app-channel.md) via mobil-SDK:et i Adobe Experience Platform genom att konfigurera Adobe Campaign-tillägget i användargränssnittet för datainsamling.

Campaign-SDK:et är [inaktuellt](deprecated-features.md) från och med Campaign v7.4. För att säkerställa en smidig övergång för den befintlig implementeringen till AEP mobilt SDK kan du fortfarande använda det i operativsystemen som anges nedan<!--, using the associated [mobile SDK](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)-->.


<table>
<tbody>
<tr>
<td>Google Android</td>
<td>
<p>7–14</p>
<p>med mobil SDK version 1.1.1.</p>
<p>Android 13 och 14 stöds från och med Campaign v7.4.</p>
<p>Android 12 stöds från och med Campaign v7.3.</p>
</td>
</tr>
<tr>
<td>Apple iOS</td>
<td>
<p>iOS 9–17</p>
<p>med mobil SDK version 1.0.26.</p>
<p>Apple iOS 15 stöds från och med Campaign v7.3. </p>
<p>Apple iOS 16 och 17 stöds från och med Campaign v7.4.</p>
</td>
</tr>
</tbody>
</table>

## Webbläsare {#Browsers}

Följande webbläsare, i sin senaste versionen, är kompatibla med Campaign för [Webbåtkomst](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

* Google Chrome
* Microsoft Edge
* Mozilla Firefox
* Safari



>[!MORELIKETHIS]
>
>* [Versionsinformation om Campaign Classic ](../../rn/using/latest-release.md)
>* [Allmän arkitektur i Campaign](../../installation/using/general-architecture.md)
>* [Rekommendationer på maskinvarustorlek](../../technotes/using/hardware-sizing.md)
>* [Inaktuella funktioner och system](../../rn/using/deprecated-features.md)
>* [Procedur för versionsuppgradering](../../production/using/build-upgrade.md)
