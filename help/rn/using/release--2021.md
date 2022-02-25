---
product: campaign
title: Campaign Classic 2021-versioner
description: Läs mer om Campaign Classic 2021-versioner
feature: Overview
role: User
level: Beginner
exl-id: 0cd6bf20-da72-4cf0-9f5d-d4e8acdd324d
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: ht
source-wordcount: '2543'
ht-degree: 100%

---

# 2021-versioner{#release-2021}

## Version 7.1 (21.1)

>[!CAUTION]
>Använd menyn **[!UICONTROL Help > About...]** för att kontrollera din Adobe Campaign [-version och buildnummer ](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Observera dock att för alla versioner mellan 9277 och 9343 som listas på den här sidan visar versionsnumret 7.0 i stället för 7.1.

### ![](assets/do-not-localize/limited_2.png) Version 21.1.4 – build 9343 {#release-21-1-4-build-9343}

_8 oktober 2021_

**Felkorrigeringar**

* Förbättrade korrigeringen av faktureringsarbetsflödet som är tillgänglig i version 9342. Den krävde en manuell omstart av arbetsflödet för att korrigeringen skulle tillämpas. Nu startar efteruppgraderingen automatiskt om arbetsflödet.

* Ett problem har åtgärdats som kunde förhindra en korrekt hantering av erbjudanden när du använde modulen **Interaktion** med alternativet [Power Booster](../../installation/using/power-booster-and-power-cluster.md). (NEO-39263)

* Korrigerade ett fel: ”Det gick inte att hitta IP-tillhörigheten xxx på mittservern xxx” som kan inträffa vid leverans när mer än en IP-tillhörighet används på en instans med flera källor. (NEO-37514)

### ![](assets/do-not-localize/limited_2.png) version 21.1.4 – build 9342 {#release-21-1-4-build-9342}

_7 september 2021_

**Säkerhetsförbättring**

* Korrigerade ett säkerhetsproblem för att förstärka skyddet mot katalogbläddringsattacker. (NEO-28547)

**Förbättringar**

* Efter att livscykeln har upphört har Flash tagits bort från alla relaterade Campaign-funktioner och -komponenter och ersatts med HTML5. Diagramtypen **Mätare** har tagits bort. (NEO-30330) [Läs mer](../../reporting/using/creating-a-chart.md)
* När du installerar klientkonsolen i Windows kontrollerar installationsprogrammet nu om det finns en överordnad registernod och skapar en om den saknas. Detta förhindrar potentiella problem när konsolen startas. (NEO-34854)
* Funktionen för att spåra signaturer har förbättrats för att förhindra att fel länkas till hur tredjepartsverktyg (e-postklienter, webbläsare osv.) hanterar specialtecken. URL-parametrar är nu kodade.

**Andra ändringar**

* Korrigerade en regression som introducerades i 21.1.3 med det nya skyddet för faktureringsarbetsflödet. Faktureringsarbetsflödet kördes på fel instanser och kraschade vid försök att skicka faktureringsrapporten som inte genererades. Du måste starta om arbetsflödet manuellt för att korrigeringen ska tillämpas.
* Tidigare inaktuella Microsoft CRM-anslutningar (Office 365 och lokala distributioner) har tagits bort från gränssnittet. [Läs mer](../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft)
* Efter migreringen till Tomcat 8 har IIS-installationsskriptet uppdaterats för att åtgärda IIS-integreringsproblem. (NEO-31019)
* Identifieringen av datakällan har förbättrats på flikarna data och schema i fönstret för arbetsflödesövergångarna **Visa population**.
* Databasindex som saknas har lagts till i följande scheman för att förhindra problem med databasuppdatering: xtk:rights, nms:dlvExclusion, nms:seedMember och nms:trackingUrl

**Felkorrigeringar**

* Korrigerade ett problem som förhindrade att Hot Click-rapporten fungerade när erbjudanden länkades till leveransen. (NEO-26295)
* Korrigerade ett problem med aktiviteten **Delarbetsflöde** när körningen inte genererade en utdatatabell. (NEO-36242)
* Korrigerade olika problem vid export av rapporten **Beskrivande analys** som en PDF-fil. (NEO-25847)
* Korrigerade ett problem som kan leda till att leveranser misslyckas när en extern e-postleverans används. (NEO-37435)
* Korrigerade ett fel vid anslutning till Microsoft CRM med webb-API. Felmeddelandet har tagits bort eftersom funktioner inte påverkades.
* Korrigerade ett problem med borttagning av dubbletter i spårningsloggar när mittservern angavs som relä mellan spårnings- och marknadsföringsservrar. (NEO-36285)
* Korrigerade en regression som förhindrade att Vault användes som ett specifikt kodarkiv.
* Korrigerade ett problem som förhindrade dig från att använda variabler i arbetsflödesaktiviteten **Berikning** när den inkommande övergången kom från en FDA-datakälla.
* Korrigerade ett problem som kunde leda till brutna URL:er i e-postmeddelanden.

### ![](assets/do-not-localize/limited_2.png) version 21.1.3 – build 9330 {#release-21-1-3-build-9330}

_5 june 2021_

**Nyheter**


<table>
<thead>
<tr>
<th><strong>Ny arbetsflödesaktivitet: ändra datakälla</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>Med den nya arbetsflödesaktiviteten <b>Ändra datakälla</b> kan du ändra datakällan för arbetsflödets arbetstabell. Detta ger större flexibilitet vid datahantering över olika datakällor (FDA- och lokal databas).</p>
<p>I Adobe Campaign-arbetsflöden hanteras data med hjälp av arbets- (eller tillfälliga) tabeller. När arbetsflödet körs delar arbetstabeller data mellan arbetsflödesaktiviteter. Som standard skapas arbetstabeller i samma databas som källan för de data som vi ställer frågor på.</p>
<p>Mer information finns i den <a href="../../workflow/using/change-data-source.md">detaljerade dokumentationen</a>.</p>
</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr>
<th><strong>Integration med Adobe Journey Orchestration</strong><br/></th>
</tr>
</thead>
<tbody>
<tr>
<td>
<p>Integrationen mellan Journey Orchestration och Adobe Campaign Classic är nu GA. Det gör att Journey Orchestration kan skicka e-post, push-meddelanden och SMS med transaktionella meddelandefunktioner i Adobe Campaign Classic </p>
<p>Kopplingen mellan Journey Orchestration och instanser i Campaign Classic är konfigurerad av Adobe vid etableringstidpunkten.</p>
<p>Mer information finns i <a href="https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=sv">dokumentationen om Journey Orchestration</a>. Ett steg-för-steg-exempel visas i det här <a href="https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=sv">avsnittet</a></p>
</td>
</tr>
</tbody>
</table>

<table> 
<thead>
<tr> 
<th> <strong>Förbättringar av LINE-kanaler</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Följande förbättringar har lagts till i LINE-kanalen:
</p>
<ul> 
<li><p>Stöd för videomeddelandetypen LINE</p></li>
<li><p>Stöd för API för partnerregistrering för LINE</p></li>
<li><p>Stöd för att skicka meddelanden igen i händelse av fel på serversidan i LINE eller timeout i nätverket</p></li>
</ul>
<p>Mer information finns i den <a href="../../delivery/using/line-channel.md">detaljerade dokumentationen</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Vertica FDA-koppling</strong><br/> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Nu kan du ansluta din instans i Adobe Campaign Classic till din externa Vertica-databas. Den här anslutningen hanteras via ett nytt externt konto.</p>
<p>Mer information finns i den <a href="../../installation/using/configure-fda-vertica.md">detaljerade dokumentationen</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Google BigQuery FDA connector</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Nu kan du ansluta din instans i Adobe Campaign Classic till din externa Google Big Query-databas. Den här anslutningen hanteras via ett nytt externt konto.
</p>
<p>Mer information finns i den <a href="../../installation/using/configure-fda-google-big-query.md">detaljerade dokumentationen</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

**Säkerhetsförbättringar**

* Åtkomst till API-metoden **xtk:session#GetCnxInfo** som returnerar den fullständiga anslutningsinformationen för databasen är nu begränsad till enbart administratörsanvändare. (NEO-27779)
* Den inaktuella funktionen decryptString har ersatts med decryptPassword i CRM-relaterade JavaScript-filer.
* Funktionen för att spåra signaturer har förbättrats för att minska risken för fel vid spårning av omdirigering när tredjepartsverktyg (e-postklienter, webbläsare, säkerhetsverktyg för säkra länkar) ändrar den spårade länken.
* Korrigerade ett problem som kunde förhindra att spårade URL:er fungerade när de innehöll versaler. Signeringsfunktionen för spårade URL:er är nu skiftlägeskänslig. (NEO-28414)

**Kompatibilitetsuppdateringar**

Campaign har nu stöd för följande system:
* Google BigQuery FDA connector
* Vertica FDA-koppling
* PostgreSQL 13

Läs mer i [kompatibilitetsmatrisen för Campaign](../../rn/using/compatibility-matrix.md).

**Inaktuella funktioner**

* Från och med Campaign 21.1 är Adobe Analytics Data Connector inaktuell. Om du använder den här kopplingen måste du anpassa implementeringen med den nya kopplingen Adobe Analytics Connector.
Mer information finns i den [detaljerade dokumentationen](../../technotes/using/aa-connector-migration.md).
* Stöd för Debian 8 är nu inaktuellt.
* Efter borttagningen av Oracle CRM i 20.3 har det relaterade externa kontot tagits bort från gränssnittet.

Läs mer på sidan [Funktioner som är inaktuella eller har tagits bort](../../rn/using/deprecated-features.md).

**Förbättringar**

* Extra kontroller har lagts till när ett arbetsflöde sparas för att säkerställa att aktivitetsnamnen är unika och att övergångar alltid följs av en aktivitet.
* Det tekniska arbetsflödet **Fakturering (billing)** innehåller nu de uppgifter som ursprungligen utfördes av arbetsflödet **Antal aktiva faktureringsprofiler** (billingActiveContactCount) som har tagits bort. E-postrapporten som skickas varje månad av arbetsflödet innehåller nu information om antalet aktiva profiler för instansen. [Läs mer](../../workflow/using/about-technical-workflows.md).
* Det nya attributet **_keyOnMData** har lagts till för att kunna använda en nyckel för åtgärder på PM-data.

**Andra ändringar**

* Ett skydd har lagts till för att endast tillåta att det [tekniska arbetsflödet för fakturering](../../production/using/monitoring-processes.md#billing-report) körs på marknadsföringsinstansen.
* Den öppna tredjepartsversionen för Windows har uppdaterats till version 1.1.1h.
* I Debian-paketbeskrivningen har nlserver ändrats till Adobe Campaign Classic-server.

**Felkorrigeringar**

* Ett problem har korrigerats vid redigering av tidsgränsen för sessionen för att logga ut användare efter en viss tid där användarna var inloggade även efter den angivna tiden.
* Korrigerade ett problem där leveranser visades som skrivskyddade men fortfarande kunde redigeras i leveransegenskaperna.
* Korrigerade ett fel som gjorde att redigeringsverktygsfältet försvann när ett webbprogram designades.
* Korrigerade ett fel som visade textversionen av ett e-postmeddelande med Adobe Campaign Classic-rubriker när en länk till ett e-postmeddelande lades till. (NEO-29211
* När du använder FDA över HTTP-anslutningar låstes arbetsflödet **Mid-sourcing (leveransloggar)** (defaultMidSourcingLog) i den tidsram som angetts av alternativet **NmsMidSourcing_LogsPeriodHour**. Detta förhindrade att poster uppdaterades med data som inträffade efter den här angivna tidsramen. (NEO-30833)
* Ett problem som uppstod efter att arbetsflödet för meddelandecentersynkronisering kördes har korrigerats. Varje gång en leveransobjektsmapp flyttades till en anpassad mapp, flyttade arbetsflödet leveranserna tillbaka till den generiska **transaktionsmeddelandehistoriken**-mappen. (NEO-27445)
* Korrigerade ett fel som visade ett felmeddelande när **Sändningsstatistik**, **Spåra indikatorer** och **Statistik för delningsaktiviteterna** skulle visas.
* Arbetsflödesaktiviteten **Oracle On Demand** har tagits bort från gränssnittet efter borttagning av Oracle CRM-koppling.
* Korrigerade ett problem som stoppade körningen av arbetsflöden efter den dagliga omstarten av arbetsflödesservermodulen (wfserver). (NEO-30047)
* Korrigerade ett fel som förhindrade att MX-hanteringsdokumentet uppdaterades, vilket kunde påverka IP-anseendet negativt. (NEO-29897)
* Åtgärdade problem som orsakade webbprocesskrascher när ett SOAP-anrop togs emot. (NEO-28796 och NEO-29600)
* Korrigerade ett problem som gjorde att skapandet av FDA-index i SAP HANA misslyckades. (NEO-29664)
* Korrigerade ett problem som kunde behålla transaktionsmeddelanden i **Väntar**-läge när SOAP-anrop som innehöll en rubrik utfördes. (NEO-28737)
* Ett problem som uppstod när Teradata FDA-kopplingen användes har korrigerats: alla temporära tabeller skapades endast på en nod i klustret, vilket kan göra att hela poolutrymmet förbrukas och Teradata kraschar. De temporära tabellerna genereras nu på många noder. (NEO-28230)
* Ett problem har korrigerats vid användning av webbprogram som ledde till att spårningstaggar genererade felaktiga primärnycklar till schemat **nms:trackingURL**. (NEO-27931)
* Kompatibiliteten med ODBC 3.x har förbättrats för att säkerställa felmeddelandets exakthet.
* Korrigerade ett problem som kunde leda till konsolkrascher när anpassade innehållsmallar användes i e-postleveranser. (NEO-31547)
* Korrigerade ett problem som hindrade Tomcat från att skicka giltiga svar på grund av en långsam anslutning eller stor svarsstorlek. (NEO-30858)
* Korrigerade ett problem som kunde inträffa vid läsning av UUID från en PostgreSQL-databas.
* Korrigerade ett problem som kunde leda till prestandaproblem vid sökning efter offertdata som var länkade till erbjudanden. (NEO-27554)
* Korrigerade ett problem som ledde till att webbprocessen inte svarade när IMS-tjänsten aktiverades men inte svarade.
* Korrigerade ett problem som hindrade dig från att skicka en leverans med en grupp korrektur på grund av en specifik kopplingsmekanism som inte kunde leverera personanpassning. (NEO-14391)
* Korrigerade ett problem där en avisering inte kunde skickas med aviseringsaktiviteten om en fråga och en berikningsaktivitet var riktade till leveransregistret. (NEO-25157)

### ![](assets/do-not-localize/red_2.png) version 21.1.2 – build 9282 {#release-21-1-2-build-9282}

_15 april 2021_

* Lösenordshanteringen har förbättrats för att optimera säkerheten.
* Korrigerade ett problem som kunde orsaka MTA-krascher.

### ![](assets/do-not-localize/red_2.png) version 21.1.1 – build 9277 {#release-21-1-1-build-9277}

_22 februari 2021_

**Säkerhetsförbättringar**

* Konsolens autentiseringsmekanism har förbättrats för att optimera säkerheten. (NEO-26944)
* Korrigerade ett säkerhetsproblem för att förstärka skyddet mot problem med SSRF (Server Side Request Forgery). (NEO-28532)

**Kompatibilitetsuppdateringar**

Campaign har nu stöd för följande system:

* API för Salesforce version 49 stöds nu när det externa Salesforce CRM-kontot används.

**Inaktuella funktioner**

Rapporten **Teknisk leveransövervakning** är nu inaktuell.

Läs mer på sidan [Funktioner som är inaktuella eller har tagits bort](../../rn/using/deprecated-features.md).

**Förbättringar**

**Tjänsten Email Feedback Service (EFS)** är en skalbar tjänst som hämtar in feedback direkt från det förbättrade MTA-programmet och därmed ökar rapporteringens noggrannhet. Denna funktion lanseras som en privat betaversion och kommer successivt att finnas tillgänglig för alla kunder i framtida versioner.

* Alla kategorier av feedback hämtas nu in för en fullständig och exakt rapportering.
* Beräkningen av indikatorn Levererad baseras nu på feedback i realtid från det förbättrade MTA-programmet för ökad precision och reaktivitet.
* EFS löser problemet med förseningar genom synkroniserad rapportering av mjuka studsar.

Mer information finns i den [detaljerade dokumentationen](../../delivery/using/sending-with-enhanced-mta.md#efs).
Om du är intresserad av att delta i den här privata betaversionen ska du fylla i det här [formuläret](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u). Vi kontaktar dig sedan.

**Andra ändringar**

* Överföringshastigheten har förbättrats för stora spårningsloggar genom komprimering.
* Arbetsflödets värmekarta har förbättrats för att undvika timeout när arbetsflöden med flera aktiviteter körs. (NEO-27423).
* Korrigerade ett problem som gjorde att ett erbjudande kunde presenteras även om slutdatumet hade passerats. Campaign Classic tar nu hänsyn till slutdatumets hela tidsstämpel, i stället för enbart datumet. (NEO-27590)
* Länken Google+ har tagits bort från personaliseringsblocket **Dela på sociala nätverk**.
* Korrigerade ett problem efter implementeringen av en felkorrigering i den senaste versionen. En kontroll lades till i värdnamnet vid anslutning med SSL/TLS,vilket ledde till att SMS-leveranser misslyckades. Verifiering av värdnamn har inaktiverats för de flesta protokoll såsom POP3, SMS och HTTP med proxy och certifikatkontrollen för det externa SMS-kontot har förbättrats med tre värden (NEO-29581). [Läs mer](../../delivery/using/sms-protocol.md#skip-tls)

**Felkorrigeringar**

* Korrigerade ett problem som gjorde att kortkommandona för Tabb, Retur och Esc inte kunde användas på den nya inloggningsskärmen.
* Korrigerade ett problem där ett uppdateringsfel gjorde att namnet på ett nyligen skapat arbetsflöde ersattes med standardvärdet efter att det hade sparats (NEO-26106).
* Korrigerade ett problem som uppstod när arbetsflöden kördes där ett nytt fält lades till som en del av en **berikande**-aktivitet före en **leverans**-aktivitet med en målkartläggning av en **extern fil**: oönskade fält lades till i målkartläggningen av den **externa filen**. (NEO-27687)
* Korrigerade ett problem som gjorde att vissa tecken i källkoden ändrades när ett webbprogram, som hade skapats och sparats tidigare, öppnades igen. (NEO-27597)
* Korrigerade ett problem som kunde inträffa vid uppgradering till en ny version som innehöll den nya signaturfunktionen för spårning av länkar (från version 19.1.4 och Campaign 20.2): när flera mallar var kopplade till en händelse kunde en uppgradering göra att fel mall valdes när transaktionsmeddelandet skickades. (NEO-28326)
* Korrigerade ett problem som gjorde att MTA inte svarade och inte kunde bearbeta leveranser om den inte startades om. (NEO-27455)
* Korrigerade ett problem med MSSQL-databasen relaterat till tidszonshantering under massöverföringsåtgärder för en kolumn av typ datum/tid. (NEO-27375)
* Korrigerade ett problem med arbetsflödesfrågor när xkt-funktioner i Redshift användes. SubDays, SubSeconds, SubMinutes och SubHours accepterar nu båda typerna av tidstämplar i Redshift (NEO-24962).
* Korrigerade ett problem som visade ett skriptfelmeddelande när en rapport med anonym åtkomst skulle förhandsgranskas. (NEO-27081)
* Korrigerade ett problem som kunde minska minnesanvändningen på servern vid leveransanalys.
* Korrigerade ett problem som kunde förhindra instansen från att fungera när vissa komplexa frågor skulle köras.
* Korrigerade ett problem som kunde förhindra att det tekniska arbetsflödet för **synkronisering av Twitter-sidor** kördes. (NEO-28634)
* Korrigerade ett problem som kunde visa ett felmeddelande relaterat till funktionen decryptPassword när man försökte publicera på Twitter med hjälp av leveransmallen **Tweet (twitter)**. (NEO-28216)
* Korrigerade ett fel som uppstod när en **Javascript**-aktivitet användes för att göra en HTTP-begäran i ett arbetsflöde. När portnumret hade definierats i värdnamnet misslyckades anropet med följande fel (NEO-29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Korrigerade ett problem som förhindrade att nya leveranser med måldatapersonalisering skickades (NEO-30323).
* Korrigerade ett problem där flera krascher inträffade i marknadsföringsinstansen som orsakade en minnesdump.
* Korrigerade ett problem som medförde att arbetsflödet **Spårning** misslyckades med följande fel (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Korrigerade ett problem som uppstod när en leverans skapades och sparades på fliken **Målinrikta och arbetsflöde** i en kampanj: förhandsgranskningen misslyckas med följande fel (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Korrigerade ett fel som uppstod när ett externt konto skulle skapas mellan en marknadsföringsinstans och en Adobe Campaign Standard-instans eller mid-sourcing-instans i Campaign Classic samt med alternativet ”DisableFOH2=1”. När alternativet ”DisableFOH2=1” används i det externa kontot stängdes inte anslutningarna korrekt och detta resulterar i följande fel (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Korrigerade ett fel med SMS när anslutningsproblem uppstod mellan servern och leverantören. Anslutningen inaktiverades sedan automatiskt av det underordnade MTA-objektet. Adobe Campaign Classic försökte inte ansluta till den felaktiga anslutningen så länge som ett nytt underordnat objekt inte hade startats.
