---
title: Version 18.10
seo-title: Version 18.10
description: Version 18.10
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a8c4face331ab6d646480322c0f53a7147251aa6

---


# Version 18.10{#release-18-10}

## Version 18.10.6 - build 8985{#release-18-10-6-build-8985}

12 juli 2019

**Förbättringar**

* Nu kan vi ta bort dummy-poster som skapats i Microsoft Dynamics under importarbetsflödet.
* Korrigerade ett problem med arbetsflödesaktiviteten för filinsamlaren som kunde logga fel i en slinga när åtkomst till en fil nekades. (NEO-12085)
* Ett problem som orsakade rapporteringsavvikelser mellan användaraktiviteter och spårningsrapporter för indikatorn för öppen leverans har korrigerats. (NEO-11742)
* Förbättrade behörigheter för att köra säkerhetszonspaketet när ett internt konto används.
* Ett problem som kunde orsaka fel i datorloggarna har korrigerats. (NEO-8978)

## Version 18.10.5 - build 8984{#release-18-10-5-build-8984}

23 april 2019

**Förbättringar**

* Korrigerade ett problem med SQL-deadlock som gjorde att leveransanalysen misslyckades vid samtidig analys/sändning (när två leveranser analyserades samtidigt). (NEO-13026)
* 10 000 poster har tagits bort i heatmap-kartan för arbetsflöde för att åtgärda ett problem med saknade data. (NEO-12329)
* Ett problem har korrigerats när alternativet Behåll alla ytterligare data från huvuduppsättningen användes i en arbetsflödesaktivitet för anrikning. (NEO-13291)

## Version 18.10.4 - build 8983{#release-18-10-4-build-8983}

15 april 2019

**Förbättringar**

* Korrigerade ett problem med datorprocessen med spårningsindikatorer för transaktionsmeddelanden. (NEO-12529, NEO-12581)
* Korrigerade ett problem med HTTPRequest-API som inte väntade på att alla återanrop skulle slutföras. (NEO-12628)
* Index lades till i kupongtemporära tabeller för att optimera leveransen. (NEO-12437)
* Korrigerade ett fel vid analys av ett meddelande som riktade till mottagare för japanska (.JP)-domäner. (NEO-12246)
* I Analytics-integreringen tillåts nu hämtning av AAM-segmentdata med tecknet %. (NEO-12025)
* Korrigerade ett Tomcat-kraschproblem när push-meddelanden skickades med HTTP2. (NEO-12701)

## Version 18.10.3 - build 8981{#release-18-10-3-build-8981}

29 januari 2019

>[!CAUTION]
>
>Det här bygget har återkallats. Uppgradera [till den senaste versionen](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) eller kontakta [teknisk support](https://support.neolane.net/).

**Förbättringar**

* Ett problem med arbetsflödesaktiviteten s3 Filöverföring har korrigerats. (NEO-12473)
* Ett problem med spårningsarbetsflödet som kunde misslyckas har åtgärdats. (NEO-12520)
* Ett problem med IMS-inloggningen har korrigerats.
* Korrigerade ett problem med förhandsgranskning och godkännande av innehåll i transaktionsmeddelanden när ett stort erbjudande-ID användes.
* Ett problem med arbetsflödet MID-sourcing (leveransräknare) har korrigerats.
* Ett problem med databasstrukturuppdateringen som tog bort nya index för NmsRecipient har korrigerats.
* Korrigerade en konsolkrasch som kunde inträffa när alternativet Definierad i en extern fil användes för huvudmålet för en leverans. (NEO-12349)
* Korrigerade flera InMail-krascher.
* Ett problem har korrigerats när en arbetsflödesaktivitet för att uppdatera data användes för att ta bort poster som lagrats i en FDA Teradata-databas.
* Åtgärdade inkonsekvenser i hanteringen av hemliga nycklar.
* Ett problem med anrikningsaktiviteten när ett fält skrevs som: xml=true och calculate=true
* Korrigerade ett problem med teckenigenkänning när push-meddelanden skickades till ett mobilprogram.
* Korrigerade ett problem som förhindrade växling från FDA till SOAP-synkroniseringsmetod i ett externt konto med medelkälla.

## Version 18.10.2 - build 8978{#release-18-10-2-build-8978}

6 december 2018

>[!CAUTION]
>
>Det här bygget har återkallats. Uppgradera [till den senaste versionen](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) eller kontakta [teknisk support](https://support.neolane.net/).

**Förbättringar**

* Åtgärdade olika problem vid körning av arbetsflöden med MySQL på FDA. (NEO-11652)
* Korrigerade ett prestandaproblem när push-meddelanden skickades. (NEO-11787)
* Ett problem med att ta bort ID när dirigerade adresser används i en leverans har korrigerats. (NEO-11842)
* Ett problem med frysning av klient som kan uppstå när komplexa arbetsflöden används har åtgärdats. (NEO-11847)
* Korrigerade ett visningsproblem vid användning av en värdefördelning med en 1:N-länk. (NEO-11820)
* Korrigerade ett Oracle-fel i heatmap-kartan för arbetsflöde.
* Korrigerade ett fel när ett erbjudande lades till i en anrikningsaktivitet.
* Ett anslutningsproblem för SQL-datahantering har korrigerats.
* Korrigerade ett problem med genereringen av temporära arbetsflödestabellnamn vid negativa ID:n.
* Korrigerade ett problem med beräkningen av arbetsflödets varaktighet i Workflow HeatMap.


## Version 18.10 - build 8977{#release-18-10-build-8977}

5 nov 2018

>[!CAUTION]
>
>Det här bygget har återkallats. Uppgradera [till den senaste versionen](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) eller kontakta [teknisk support](https://support.neolane.net/).

**Vad är nytt?**

<table> 
 <thead> 
  <tr> 
   <th> Funktionalitet<br /> </th> 
   <th> Beskrivning<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Förbättringar av push-meddelanden<br /> </td> 
   <td> Ett antal förbättringar har implementerats för push-meddelanden i Adobe Campaign:<br /> 
    <ul> 
     <li> <p>Spåra tysta meddelanden i iOS </p> </li> 
     <li> <p>Skicka feedback vid registreringssamtal iOS</p> </li> 
     <li> <p>Förbättra förberedelsehastigheten för iOS-leverans</p> </li> 
    </ul> <p>Som en del av GCM-avskrivningen av Google tillåter nu Android V2-kopplingen bara anslutningar till FCM-servern.</p><p>Mer information finns i den <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">detaljerade dokumentationen</a>. Den manuella uppgraderingen till FCM finns i den här <a href="https://helpx.adobe.com/campaign/kb/migrate-to-fcm.html">artikeln</a>. </p> </td> 
  </tr> 
  <tr> 
   <td> SQL Data Management-aktivitet<br /> </td> 
   <td> <p>En ny datahanteringsarbetsflödesaktivitet har lagts till. Med <strong>SQL Data Management</strong> -aktiviteten kan du skriva eller kopiera och klistra in dina egna SQL-skript för att skapa och fylla i arbetstabeller (endast FDA). </p> <p>Mer information finns i den <a href="../../workflow/using/sql-data-management.md">detaljerade dokumentationen</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Arbetsflödesövervakning<br /> </td> 
   <td> <p>Med nya Adobe Campaign Workflow HeatMap har plattformsadministratörerna en snabb grafisk representation av alla samtidiga arbetsflöden, vilket gör att de kan övervaka belastningen på instansen och planera arbetsflödena utifrån detta.</p> <p>Mer information finns i den <a href="../../workflow/using/heatmap.md">detaljerade dokumentationen</a>.</p> <p>Workflow HeatMap-paketet är också tillgängligt på begäran för byggen före 8977 (med början build 8700). Mer information om hur du begär och installerar programmet finns på <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">den här sidan</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Säkerhetsförbättringar**

* Korrigerade ett säkerhetsproblem som kunde leda till sårbarheter för attacker med SSRF (Server Side Request Forgery) och DoS-attacker (denial of service). (NEO-11453)
* Innehåll (spåra omdirigering, spegelsidor, undersökningar osv.) kommer nu att hanteras av Campaign med X-Robots-Tag: nocache-huvud. Detta förhindrar att innehållet indexeras av sökmotorer på Internet. (NEO-11101)
* Korrigerade ett XTK-injektionsproblem i prenumerations-API (nms:subscription:Unsubscribe och nms:subscription:Subscribe).
* Korrigerade ett XTK-injektionsproblem i webbprogrammet för avprenumeration.
* Lösenord som inte visades på ett säkert sätt i vissa SMS-loggar har tagits bort.

**Förbättringar**

* Campaign Classic API:er finns nu på en [dedikerad sida](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html). Om du använde filen jsapi.chm bör du nu hänvisa till den nya onlineversionen.
* PostgreSQL 10, Debian 9 och Teradata 16.20 stöds nu. Se [Kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).
* När du skapar en SFTP-anslutning kan du nu använda proxyautentisering. Mer information finns i den [detaljerade dokumentationen](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration) (NEO-9868)
* Alternativet **för datumberäkningsformeln** är nu tillgängligt i leveransegenskaperna när du skapar en enskild leverans med hjälp av mallen för direktmeddelandeleverans. (NEO-9792)
* Domännamnshanteringen har förbättrats för cookie-spårning och webbprogram. Mer information finns i avsnittet &quot;Technical Evolutions&quot; nedan.
* Importen av delade resurser i Adobe Marketing Cloud på en leverans- eller landningssida har förbättrats vad gäller säkerhet och prestanda.
* Det finns en ny kryssruta i det externa kontot för mobilkanaler som gör att du kan använda detaljerade SMPP-spår i loggfilen, vilket gör att dessa utdata är direkt tillgängliga från Adobe Campaign-gränssnittet.
* I utsändningarna görs nu en skillnad mellan det maximala antalet anslutningar och det maximala antalet meddelanden per timme. När gränserna nås är det sedan möjligt att veta varför genomströmningen är begränsad. Tidigare gällde samma meddelande (&quot;kvoten uppfylldes&quot;) i båda fallen.
* Du kan nu ange ett SQL-skript som ska köras när du hämtar en anslutning från poolen. Skriptet kan användas för att ange standardschema. Skriptet används efter frågebanding. (NEO-11256)
* Campaign SDK lagrar inte längre användar-ID:t så att det uppfyller våra PII-regler. Data lagras nu som en hash.
* När du importerar en XML-fil för paketexport stöder Campaign nu att det finns strukturlistor i filen, även om kodningen uttryckligen deklareras i den.

**Teknisk utveckling**

Klient- och serveruppgradering

>[!CAUTION]
>
>Om du har en server som har uppdaterats till 18.10 måste du använda en 18.10-klient för att få åtkomst till servern. 18.10-klienten kan ansluta till en äldre serverversion.

Hantering av domännamn

Domännamnshanteringen har förbättrats för cookie-spårning och webbprogram.

Nu stöds alla domännamn på andrahandsnivå med två bokstäver som standard (till exempel .aa.com). För mer komplexa domännamn (t.ex. domäner på andrahandsnivå med tre bokstäver som .com.au) måste du lägga till dem i alternativet **cookieDomains** i serverConf (under taggen redirection). Här är ett exempel:

```
<redirection cookiedomain="http://toureiffel.paris">
```

Indexförbättringar

Index för NmsRecipient har omarbetats. Detta bör förbättra prestanda för frågor som använder den här tabellen. Om du har gjort ett tillägg till NmsRecipient kanske du vill verifiera att du inte har index som duplicerar de nya indexen (för att minimera utrymmesanvändningen på databasservern). (NEO-8228)

På PostgreSql kan du nu skapa index som optimerar &quot;LIKE &#39;string%&#39;&quot; (eller &quot;begin with&quot;) när du använder en UTF-8-kollation. Om du utför andra åtgärder i samma kolumn (till exempel sortera efter eller förena) krävs ett annat standardindex. På schemasidan görs detta genom att indexOption=&quot;searchFromStart&quot; läggs till i indexdefinitionen (det skapar ett varchar_pattern_ops-index i stället för ett standardträdindex). Exempel (på NmsRecipient):

```
<dbindex name="email2"> <!-- optimize order by/join (and startWith if not PostgreSql with an UTF-8 collation) operations -->
  <keyfield xpath="@email"/>
</dbindex>
<dbindex name="email3" indexOption="searchFromStart"><!-- optimize startsWith operation on PostgreSql when a UTF-8 collation is used; create no index in other cases-->
  <keyfield xpath="@email" />
</dbindex>
```

Nya index har lagts till i NmsRtEvent och NmsEventHistory (i kolumnen &quot;Schemalagd&quot;), vilket bör förbättra visningstiden för motsvarande formulär (NEO-11738).

Dessa indexändringar kan leda till att tiden som krävs för att utföra uppgraderingen ökar.

**Patchar**

* Korrigerade ett fel som förhindrade att filer från arbetsflödesaktiviteten för **webbhämtning** hämtades. (NEO-11105)
* Korrigerade ett fel som ibland lämnade arbetsflödet **Skicka indikatorer och kampanjattribut** i feltillstånd (NEO-10820).
* Korrigerade ett problem som tog bort mottagarlistan som skapades efter att Listuppdateringsaktiviteten kördes i ett arbetsflöde. (NEO-11696)
* Korrigerade ett problem som felaktigt visade kampanjerna en månad framåt i Campaign-kalendern (på en japansk instans). (NEO-11445)
* Ett problem som gjorde att Analytics-konfigurationen inte kunde visas på fliken Web Analytics i leveransegenskaperna har korrigerats. (NEO-11619)
* Korrigerade ett fel som visades när indataformuläret nms:delivery skulle redigeras och sparas. (NEO-10973)
* Korrigerade ett fel i konfigurationen av det externa kontot som uppstod när ett arbetsflöde som innehåller en filöverföringsaktivitet kördes. (NEO-11012)
* Korrigerade ett problem som returnerade tomma rader när funktionen zcat användes för att läsa in filer i datainläsningsaktiviteten. (NEO-11273)
* Korrigerade ett fel som genererade duplicerade breda loggar under leveransanalysen. (NEO-11360)
* Ett problem som ledde till leveransfel på grund av att en sekundärlänknyckel saknas efter att Enrichment-aktiviteten kördes i ett arbetsflöde har åtgärdats. (NEO-11537)
* Korrigerade ett problem som förhindrade att Adobe Campaign avinstallerades eller reparerades när installationssökvägen innehöll specifika kinesiska GB18030-tecken.
* Korrigerade ett problem som kopplade vissa spårningsloggar till fel leverans. (NEO-11412)
* Korrigerade ett problem som kunde orsaka att vissa delar av leveransloggarna fortfarande hade väntande status längre än förväntat. (NEO-11336)
* Korrigerade ett fel som uppstod när en fråga redigerades för att lägga till en kupong i en leverans. (NEO-11037)
* Korrigerade ett problem i rapporter som fick diagrammen att alltid beräkna summan av värdena oavsett vilken aggregerad operator som valdes. (NEO-10913)
* Eftersom funktionen &quot;request.scheme&quot; är inaktuell har den tagits bort från JSAPI-dokumentationen. (NEO-10828)
* Ett problem som gjorde att vissa användare med tidszonskonfigurationer inte kunde logga in på Adobe Campaign har korrigerats. (NEO-10712)
* Ett problem som uppstod när ett externt mobilkanalskonto konfigurerades med den utökade allmänna SMPP-anslutningen har åtgärdats: om du angav att använda olika parametrar för mottagaren skulle sändaren felaktigt använda dessa parametrar i stället för sina egna parametrar.
* Korrigerade ett problem som gjorde att schemalagda leveranser misslyckades när en frekvens för tryckregeln angavs, eftersom leveranserna hela tiden räknades om efter den första skiljedomsförfarandet. (NEO-10016)
* Korrigerade ett problem som gjorde att IIS-webbservern kraschade under programpoolens återvinningsprocess (i biblioteket nlsrvmod.dll). (NEO-10862)
* Korrigerade ett problem som kunde förhindra sökning av en mottagare på skärmen **Profiler och Mål** . (NEO-8228)
* Korrigerade ett problem som kunde leda till ett timeout-fel vid åtkomst till mappen Händelsehistorik i ett stort antal poster. (NEO-11738)
* Korrigerade ett problem som kunde leda till att mottagare av LINE-leverans felaktigt returnerades som &quot;Onåbar&quot;. (NEO-10833)
* Ett problem har korrigerats när en arbetsflödesfråga kördes med en extra kolumn i Oracle. (NEO-11615)
* En förbättring har gjorts för att säkerställa att stängda anslutningar inte sparas i anslutningspoolen under för lång tid. (NEO-11392)
* Ett problem har korrigerats vid användning av en arbetsflödesaktivitet med mål (fråga, datainläsning (RDBMS) osv.) via FDA ansluts till en extern Oracle-tabell som innehåller UTF8-tecken (i tabellnamnet, fältnamnet osv.) och som även innehåller en primärnyckelbegränsning med ett systemgenererat standardbegränsningsnamn. (NEO-10714)
* Korrigerade ett problem som kunde förhindra att HTML-innehållet i en leverans togs bort. (NEO-11327)
* Korrigerade ett problem med förhandsgranskningen av XML- och CSV-filer i ett direktbrev efter att en kampanj har körts. (NEO-11290)
* Ett problem har korrigerats vid sortering av data i en arbetsflödesaktivitet för berikning. (NEO-11394)
* Ett problem har korrigerats vid sortering av data i en anpassad rapport. (NEO-10896)
* Korrigerade ett problem som ledde till fel när inställningen useVault användes med Teradata. (NEO-11399)
* Ett problem som gjorde att Adobe Campaign-klientkonsolen kraschade när flera frågerader togs bort har åtgärdats. (NEO-10744)
* Korrigerade ett problem som förhindrade att tryckregler tillämpades i vissa fall vid leverans av direktreklam. (NEO-9004)
* Ett problem som uppstod när datainläsningsaktiviteten användes för att importera en kolumn med datatypen&quot;time&quot; har korrigerats: tidsavgränsaren återställs även sedan den tagits bort. (NEO-10743)
* Ett problem som gjorde att mappen Leveranser inte kunde visas i körningsmappslistan i leveransegenskaperna när en återkommande leverans redigerades har åtgärdats. (NEO-11094)
* Korrigerade ett problem som gjorde att visningsfönstret inte kunde visa mer än 200 poster som resultatmål för en Query-aktivitet i ett arbetsflöde. (NEO-11195)
* Korrigerade ett fel i Oracle som förhindrade att en DELETE-fråga kördes med fler än 1 000 valda element. (NEO-11171)
* Korrigerade ett problem som ledde till att URL:er kodades som spårade URL:er i de ytterligare parametrarna för en leverans av ett push-meddelande från Android. (NEO-11468)
* Korrigerade ett skriptfel som uppstod i rapporten för användaraktiviteter när parametrarna angavs till&quot;Ett dagintervall&quot; och&quot;Öppnar&quot;. (NEO-11655)
* Korrigerade ett problem som uppstod vid anslutning till servern med mellanlagring eller till meddelandecentret via en autentiserad webbproxy. (NEO-11309)
* Korrigerade ett Oracle-fel som uppstod när en ny leveranskomposition sparades efter att ett element i ett specifikt schema **baserat på en SQL-vy** har valts. (NEO-11682)
* Korrigerade ett problem som ledde till att avvisade filer som innehöll falska positiva värden vid bearbetning av en ZIP-fil som innehåller en CSV-fil via en inläsningsfilaktivitet med alternativet Dekomprimering.
* xtkjoblog rensas nu av rensningen.

