---
product: campaign
title: Senaste versionen
description: Senaste versionsinformation för Campaign Classic v7
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: e4cd327d1495987e7d32bd1b903c8fe5de2813f2
workflow-type: tm+mt
source-wordcount: '1273'
ht-degree: 82%

---

# Senaste versionen{#latest-release}

![](../../assets/v7-only.svg)

Den här sidan listar nya funktioner, förbättringar och korrigeringar som kommer med den **senaste versionen av Campaign Classic v7**. Varje ny version kommer med en status som visas med en färg. Läs mer om versionsstatusen för Campaign Classic v7 på [den här sidan](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) Version 7.2.2 – build 9349 {#release-7-2-2}

_1 mars 2022_

**Felkorrigeringar**

* Ett problem som uppstod när **Web Analytics** externt konto, vilket gjorde att integreringsstatusen alltid visade &quot;Integreringen lyckades&quot; även när fel uppstod. (NEO-36672)
* Korrigerade flera efteruppgraderingsfel relaterade till sekvens-ID-mekanismen när det fanns negativa ID:n. (NEO-43205, NEO-42846 och NEO-42845)
* Ett problem som uppstod när **Web Analytics** externt konto med återkommande och kontinuerliga leveranser, vilket medförde att data från det externa kontot delvis förlorades. (NEO-38548)
* Korrigerade ett fel som gjorde efteruppgraderingen långsammare när NmsActiveContact-tabellen uppdaterades. (NEO-43206)
* Korrigerade ett fel efter uppgraderingen som uppstod om mappar som inte är installerade hade flyttats från **Administration** till en annan plats. (NEO-42875)
* Ett problem när ett **Uppdatera data** arbetsflödesaktivitet som kan förhindra att mottagarschemat uppdateras med mottagardata från en extern Google Cloud-databas. (NEO-42343)
* Ett problem som rör Adobe Analytics-anslutningen har korrigerats under efteruppgraderingen. (NEO-43318, NEO-38136)
* Korrigerade ett överskrivet CUID med VALUE_TO_CHANGE-problem under efteruppgraderingen. (NEO-43267)
* Korrigerade ett problem som ledde till fel vid synkronisering av instanser för medelkällning och marknadsföring i en flermittskonfiguration. (NEO-10432)
* Korrigerade ett problem som orsakade ett fel när leveransarbetsflödet uppdaterades när fler än 1 000 utsändningar fanns samtidigt. (NEO-40276)
* Ett problem som gjorde att leveransindikatorerna för öppna och klickfrekvens inte kunde uppdateras automatiskt har åtgärdats. (NEO-43253)

## ![](assets/do-not-localize/limited_2.png) Version 7.2.1 – build 9346 {#release-7-2-1}

_10 januari 2022_

**Säkerhetsförbättring**

Flera säkerhetsförbättringar har gjorts i FDA-konton:

* När du konfigurerar ditt externa FDA-konto kan du nu logga in på ditt Snowflake-konto med autentisering via nyckelpar för förbättrad autentiseringssäkerhet. [Läs mer](../../installation/using/configure-fda-snowflake.md)
* När du konfigurerar ett externt FDA-konto kan du nu logga in på ditt Azure Synapse Analytics-konto med hjälp av den systemtilldelade hanterade identiteten. [Läs mer](../../installation/using/configure-fda-synapse.md#azure-external)
* Alla referenser till log4j-biblioteket har tagits bort från Campaign för att säkerställa optimal säkerhet.

**Kompatibilitetsuppdateringar**

Adobe Campaign är nu kompatibelt med Windows Server 2019. Se [Matris för kampanjkompatibilitet](../../rn/using/compatibility-matrix.md#OperatingSystems).

**Förbättringar**

* Microsoft Dynamics CRM 365 Connector

   Kritiska korrigeringar har tillämpats för webb-API:et Microsoft Dynamics Connector:

   * Korrigerade ett problem, under en import som utlöstes av ett arbetsflöde, som gjorde att null-värden för fält av strängtyp sparades som null i stället för som tomma värden.
   * Korrigerade ett problem som ledde till följande fel för import eller export av data med webb-API-anrop: ”Ogiltig URI: URI-schemat är för långt”.
   * Korrigerade olika problem med import av data som innehåller sökfält från Microsoft Dynamics 365.

* Google BigQuery FDA Connector

   * Google BigQuery FDA Connector är nu tillgänglig för värdbaserade distributioner. [Läs mer](../../installation/using/configure-fda-google-big-query.md)
   * Stöd har lagts till för att aktivera anslutningar till en proxyserver för Google BigQuery FDA Connector. Nödvändiga proxyalternativ kan ställas in via fältet Alternativ i konfigurationen av det externa kontot. [Läs mer](../../installation/using/configure-fda-google-big-query.md#google-external)

**Andra ändringar**

* Åtgärdsaktiviteterna Microsoft CRM, Salesforce och Oracle CRM On Demand har tagits bort från gränssnittet efter deras utfasning. Om du vill konfigurera datasynkroniseringen mellan Adobe Campaign och ett CRM-system kan du använda CRM-anslutningsaktiviteten. [Läs mer](../../workflow/using/crm-connector.md)
* Fältet **[!UICONTROL Encrypted identifier]** har lagts till i besökarschemat (nms:besökare). Det här fältet beräknas och ska användas för webbprogram. Detta gäller när Line-kanalen är konfigurerad på instansen för mid-sourcing.
* CRM-datakällor kan nu användas med aktiviteten **Ändra datakälla**.
* Ett nytt alternativ har lagts till i egenskaperna **Felhantering** för arbetsflödesaktiviteter: alternativet **Avbryta vid fel** stoppar automatiskt arbetsflödet. Du kommer inte att kunna starta om den efteråt (NEO-29661). [Läs mer](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* En dedikerad sekvens används nu för att generera primärnycklarna för tabellen nmsGroup, som används för att skapa statistiska grupper av mottagare. Sekvensen xtknewId användes tidigare. (NEO-30832)
* Lade till stöd för gruppuppdateringsoperationer med CRM-anslutningsaktiviteten.
* Förbättrad prestanda för behandlingstid för transaktionsmeddelanden. (NEO-40370)

**Felkorrigeringar**

* Korrigerade ett problem när en leverans skapades som ledde till ett fel på fliken **Bilder** i fönstret **Spårning och bilder**. Detta inträffade när en automatisk proxykonfiguration användes. (NEO-33260)
* Korrigerade ett problem som kunde förhindra dig från att ladda upp en fil till en Debian 10-server (HTTPS) i synkront läge.
* Korrigerade ett problem som kunde förhindra att poster i leveransstatistiktabellen (`nmsDeliveryLogStats`) rensades från instansen för mid-sourcing under databasrensning efter att de relaterade leveranserna hade raderats. (NEO-31034)
* Korrigerade ett problem som gjorde att du inte kunde skicka mobilappsmeddelanden på iOS när du använde tokenbaserad autentisering (NEO-38640).
* Korrigerade ett problem som kunde visa skriptfelmeddelanden när rapporter skulle skapas och konfigureras (NEO-38393).
* Korrigerade ett problem som kunde göra att arbetsflödet för spårning misslyckades på Oracle på grund av att stora volymer av leveransindikatorer uppdateras samtidigt (NEO-39653).
* Korrigerade ett problem som kunde förhindra att en leverans skickades på grund av ett fel som uppstod när en kontrolltypologi kördes (NEO-39833).
* Korrigerade ett fel på landningssidor som kunde förhindra att specialtecken visas korrekt på HTML-sidorna i onlineenkätsvar (NEO-39438).
* Korrigerade ett problem som kunde förhindra konsolen i Campaign Classic från att fungera när du högerklickade på någon av mapparna på Utforskarfliken (NEO-38884).
* Korrigerade ett fel vid användning av en tidigare skapad leveransmall kopplad till ett Web Analytics-konto i en ny leverans där Web Analytics-konfigurationen saknades. (NEO-28666)
* Korrigerade ett problem som kunde förhindra dig från att förhandsgranska mobila leveranser som var kopplade till ett arbetsflöde.
* Korrigerade ett fel som förhindrade att anpassade spårnings-URL:er omdirigeras när URL-signaturmekanismen för spårning av länkar aktiverades.
* Korrigerade ett problem som kunde orsaka fel efter uppgraderingen på grund av ett problem med indexhantering.
* Korrigerade ett fel som uppstod vid användning av sökfältsdatatyper med Microsoft Dynamics CRM i **Import**- eller **Export**-arbetsflödesaktiviteter.
* Korrigerade ett problem som kunde förhindra dig från att logga in på konsolen på grund av ett proxykonfigurationsproblem. (NEO-38388)
* Korrigerade ett regressionsproblem som förhindrade funktionen **Rensa mappen** från att fungera som den ska. (NEO-37459)
* Korrigerade ett problem som ledde till ett felaktigt begärandefel när xml-datafält användes med Microsoft Dynamics CRM-kontot om den refererade xml-filen innehöll dubbla citattecken.
* Korrigerade ett problem som orsakade att problem med nätverkstimeout inte loggades korrekt som problem med skriptavbrott i stället för nätverksfel. Detta problem uppstod vid HTTP-begäranden som inkluderades i JavaScript-aktiviteter. (NEO-38079)
* Korrigerade ett problem som returnerade felaktiga resultat när funktionerna Amazon Redshift HoursDiff och MinutesDiff kördes när tidskomponenten skulle extraheras.(NEO-31673)
* Korrigerade ett problem som hindrade rapporten **Hot Clicks** från att laddas för leveranser sedan build 9182. (NEO-28900)
* Korrigerade ett fel som ersatte &amp;-symbolen i en URL med teckenenhetsreferens (`&amp;`) som hindrar användare från att komma åt URL:en kopplad till en QR-kod. (NEO-28621)
* Korrigerade ett problem som skapade ett nytt externt konto varje gång en användare skapade ett nytt kampanjarbetsflöde och en leveransaktivitet länkad till ett Web Analytics-konto. Detta orsakades av ett saknat ID i leveransobjektet webAnalyticsAccount. (NEO-39691)
* Korrigerade ett problem som kunde förhindra arbetsflödesaktiviteten **Läslista** från att fungera när listan identifierades i databasen med ett negativt ID. (NEO-39607)
* Korrigerade ett problem som kunde leda till att arbetsflödet **Mid-sourcing (leveransloggar)** misslyckades. (NEO-39662)
* Korrigerade ett problem som kunde förhindra dig från att förhandsgranska e-postleveranser som var kopplade till ett arbetsflöde. (NEO-37840)
* Korrigerade ett problem som kunde medföra att giltiga tabeller som innehöll listvärden raderades av arbetsflödet för databasrensning. (NEO-34911)
* Korrigerade ett problem som kunde få faktureringsarbetsflödet att krascha på marknadsinstanser.
