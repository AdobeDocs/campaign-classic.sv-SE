---
product: campaign
title: Senaste versionen
description: Senaste versionsinformation för Campaign Classic v7
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 52e9925932e9b802a92f317b0950a1e933499b56
workflow-type: ht
source-wordcount: '2008'
ht-degree: 100%

---

# Senaste versionen{#latest-release}

![](../../assets/v7-only.svg)

Den här sidan listar nya funktioner, förbättringar och korrigeringar som kommer med den **senaste versionen av Campaign Classic v7**. Varje ny version kommer med en status som visas med en färg. Läs mer om versionsstatusen för Campaign Classic v7 på [den här sidan](rn-overview.md).

## ![](assets/do-not-localize/limited_2.png) Version 7.3.1 – build 9352 {#release-7-3-1}

_1 juli 2022_

**Nyheter**

<table> 
<thead>
<tr> 
<th> <strong>Tidskänsliga meddelanden</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>I iOS 15 har Apple lagt till en funktion för känsliga meddelanden som ger programutvecklaren kontroll över att kringgå fokusläget när ett meddelande anses vara känsligt och sedan måste nå användaren i realtid.</p>
<p>Läs mer om hur du skapar ett känsligt meddelande i den <a href="../../delivery/using/create-notifications-ios.md">detaljerade dokumentationen</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Kompatibilitetsuppdateringar**

* Adobe Campaign SDK har nu stöd för Android 12 och iOS 15 för push-meddelanden.
* Adobe Campaign är nu kompatibelt med MySQL 8.
* Adobe Campaign är nu kompatibelt med Windows 11.
* Adobe Campaign är nu kompatibelt med Debian 11.

Se [kompatibilitetsmatrisen för Campaign](../../rn/using/compatibility-matrix.md#OperatingSystems).

**Förbättringar**

* Efter att Microsoft Internet Explorer 11 har nått slutet av sin livscykel använder nu HTML-återgivningsmotorn för Adobe Services (inloggningssida) i klientkonsolen Edge Chromium. Observera att Microsoft Internet Explorer 11 fortfarande är HTML-återgivningsmotorn för instrumentpaneler i klientkonsolen.  Dessutom måste Microsoft Edge Webview 2-körtid nu installeras för alla installationer av klientkonsolen (från och med buildversionen 7.3 av Campaign Classic). [Läs mer](../../installation/using/installing-the-client-console.md)
* Hanteringen av databasanslutningar i Adobe Campaign har förbättrats för att optimera stabiliteten.
* Microsoft Exchange Online OAuth 2.0-autentisering för POP3 stöds nu i Campaign. [Läs mer](../../installation/using/external-accounts.md#bounce-mails-external-account)
* Olika problem vid användning av en berikande arbetsflödesaktivitet med externa data har åtgärdats. (NEO-38069)
* SAP Hana FDA-anslutningen har uppdaterats för att fungera med den senaste SAP Hana-databasversionen (2.x).
* Teradata FDA-anslutningen har uppdaterats för att fungera med den senaste Teradata-versionen (17).
* I 20.2 introducerades stöd för tokenbaserad autentisering för iOS-leveranser av nya leveranser och leveransmallar. I 7.2 lades en korrigering till efter uppgraderingen för att tillämpa det tokenbaserade autentiseringsstödet på maximalt 10 000 tidigare skapade leveranser och leveransmallar. I 7.3 har korrigeringen förbättrats och gränsen har tagits bort.

**Korrigeringar**

* Ett fel från den tidigare versionen som gjorde att användare inte kunde ändra storlek på inloggningssidan för IMS har åtgärdats. (NEO-30085)
* Ett fel som uppstod när innehållshanterarpaketet installerades på en befintlig instans har åtgärdats. (NEO-32349)
* Ett problem i menyn **Kampanjer** där ett meddelande om ”pågående åtgärd” visades kontinuerligt har åtgärdats. (NEO-44904)
* Ett problem som uppstod när Adobe Analytics är aktiverat och som tog bort BID (Broadlog ID) och CID (Campaign ID) från URL:en när ett e-postmeddelande med en URL skickades utan att leveransen sparades har åtgärdats. (NEO-38678)
* Ett problem vid överföring av en bild till mappen Offentliga resurser i en instans med Message Center-specifik konfiguration har åtgärdats. Följande felmeddelande visades: ”Det gick inte att överföra bilderna till spårningsservrarna”. (NEO-38546, NEO-45572)
* Ett problem som gjorde att systemet kraschade när konfigurationen skulle återskapas från felaktiga konfigurationsfiler har åtgärdats. (NEO-38752)
* Ett problem som kunde leda till att leveransindikatorer inte uppdaterades korrekt har åtgärdats. (NEO-44827)
* Ett problem som kunde leda till ett fel efter uppgraderingen när komplexa frågor användes har åtgärdats. (NEO-43648)
* Ett problem som kunde förhindra att förhandsgranskning av webapps fungerade har åtgärdats. (NEO-43242)
* Ett problem som kunde leda till att leveransförberedelser misslyckades när en extern målmappningsfil användes i ett arbetsflöde med en datainläsningsaktivitet (fil) har åtgärdats. (NEO-43691)
* Ett problem som kunde leda till krascher och krävde en fullständig omstart av instansen har åtgärdats. (NEO-44645)
* Ett problem som kunde förhindra att resultat lästes in i Färgdiagram över arbetsflöde har åtgärdats. (NEO-43360)
* Ett problem som kunde leda till anslutningsproblem när den externa FDA-anslutningen användes har åtgärdats. (NEO-42722)
* Ett problem med korrektur vid användning av adressersättning och undantag för kontrollgrupper har åtgärdats. (NEO-39695)
* Ett problem som kunde leda till arbetsflödesfel på grund av ett problem med Snowflake-anslutningen har åtgärdats. (NEO-46299)
* Ett fel som kunde frysa klientkonsolen på grund av ett ogiltigt tecken i ett anpassningsblock har åtgärdats. (NEO-45761)
* Ett problem som kunde leda till anslutningsproblem när ett externt konto för Snowflake skapades som en extern databas har åtgärdats. (NEO-45744)
* Ett problem som kunde leda till att tabellinformation visades som skyddad av attributet visibleif har åtgärdats. (NEO-37865)
* Ett problem som kunde visa felmeddelandet ”$ är inte definierad” under leveransanalysfasen har åtgärdats. (NEO-32940)
* Ett problem som orsakade att leveranser associerades med fel eventtype har åtgärdats. (NEO-45743)
* Ett problem som kunde leda till krascher på grund av tillfälliga kärndumpar (NEO-30549) har åtgärdats
* Ett problem som kunde leda till krascher när felaktig HTML-kod används i en leverans har åtgärdats. (NEO-40385)
* Ett problem som kunde förhindra icke-administratörer från att få åtkomst till fliken **Analys** i leveransegenskaperna har åtgärdats. (NEO-34025)
* Ett problem som kunde förhindra att en bild laddades upp i segmentläge från en extern server under meddelandeförberedelsen har åtgärdats. (NEO-40307)

## ![](assets/do-not-localize/green_2.png) Version 7.2.2 – build 9349 {#release-7-2-2}

_1 mars 2022_

>[!NOTE]
>
> Den här builden är kompatibel med v7.2.1 av klientkonsolen.

**Felkorrigeringar**

* Åtgärdade ett problem vid konfigurering av det externa **Web Analytics**-kontot, vilket gjorde att integreringsstatusen alltid visade ”Integration slutförd” även när fel uppstod. (NEO-36672)
* Åtgärdade flera efteruppgraderingsfel relaterade till sekvens-ID-mekanismen när det fanns negativa ID:n. (NEO-43205, NEO-42846, NEO-42845)
* Åtgärdade ett problem vid användning av det externa **Web Analytics**-kontot med återkommande och kontinuerliga leveranser, vilket gjorde att data från det externa kontot delvis gick förlorade. (NEO-38548)
* Åtgärdade ett problem som saktade ner efteruppgraderingen vid uppdatering av NmsActiveContact-tabellen. (NEO-43206)
* Åtgärdade ett problem med efteruppgraderingsfel som uppstod om färdiga mappar hade flyttats från noden **Administration** till någon annan plats. (NEO-42875)
* Åtgärdade ett problem vid användning av en arbetsflödesaktivitet **Uppdatera data** som kunde förhindra att mottagarschemat uppdaterades med mottagardata från en extern Google Cloud-databas. (NEO-42343)
* Åtgärdade ett problem under efteruppgraderingen relaterat till Adobe Analytics-anslutningen. (NEO-43318, NEO-38136)
* Åtgärdade ett problem där CUID är överskrivet av &#39;VALUE_TO_CHANGE&#39; under efteruppgraderingen. (NEO-43267)
* Åtgärdade ett problem som ledde till fel vid synkronisering av instanser för mid-sourcing och marknadsföring i en multi-mid-konfiguration. (NEO-10432)
* Åtgärdade ett problem som orsakade ett fel när leveransarbetsflödet uppdaterades när fler än 1 000 utsändningsloggar fanns samtidigt. (NEO-40276)
* Åtgärdade ett problem som förhindrade indikatorer för andelen öppnade leveranser och andelen klickade leveranser från att uppdateras automatiskt. (NEO-43253)

## ![](assets/do-not-localize/limited_2.png) Version 7.2.1 – build 9346 {#release-7-2-1}

_10 januari 2022_

**Säkerhetsförbättring**

Flera säkerhetsförbättringar har gjorts i FDA-konton:

* När du konfigurerar ditt externa FDA-konto kan du nu logga in på ditt Snowflake-konto med autentisering via nyckelpar för förbättrad autentiseringssäkerhet. [Läs mer](../../installation/using/configure-fda-snowflake.md)
* När du konfigurerar ett externt FDA-konto kan du nu logga in på ditt Azure Synapse Analytics-konto med hjälp av den systemtilldelade hanterade identiteten. [Läs mer](../../installation/using/configure-fda-synapse.md#azure-external)
* Alla referenser till log4j-biblioteket har tagits bort från Campaign för att säkerställa optimal säkerhet.

**Kompatibilitetsuppdateringar**

Adobe Campaign är nu kompatibelt med Windows Server 2019. Se [kompatibilitetsmatrisen för Campaign](../../rn/using/compatibility-matrix.md#OperatingSystems).

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
