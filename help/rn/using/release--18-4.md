---
title: Version 18.4
seo-title: Version 18.4
description: Version 18.4
seo-description: null
page-status-flag: never-activated
uuid: d132570e-20e6-4550-95bd-176701f43b19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rn
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 4dc87ff3-eb6a-40ac-97ee-00b64cd7718d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3801665574d0cdc9c0caf46fb2f0eede38f1b2cc

---


# Version 18.4{#release-18-4}

## Version 18.4.5 - build 8937{#release-18-4-5-build-8937}

21 november 2018

**Förbättringar**

* Åtgärdade olika problem vid körning av arbetsflöden med MySQL på FDA. (NEO-11652)
* Korrigerade ett problem som gjorde att en del av leveranspopulationen fortfarande var i väntande tillstånd, i vissa fall. (NEO-11336)
* Korrigerade ett intermittent problem med det automatiska SMS-svaret. (NEO-11811)
* Ett problem med att ta bort ID när dirigerade adresser används i en leverans har korrigerats. (NEO-11842)
* Korrigerade ett syntaxfel vid sortering i en arbetsflödesaktivitet för berikning. (NEO-11394)
* Korrigerade ett problem som kunde göra att webbservern kraschade när IIS startades om. (NEO-10862)
* Korrigerade ett problem som kunde få spårningsarbetsflödet att misslyckas efter en bygguppgradering (FDA - SQL). (NEO-11635)
* Korrigerade ett problem som kunde göra att data i arbetsflödeslistan gick förlorade. (NEO-11696)
* Korrigerade ett prestandaproblem när push-meddelanden skickades. (NEO-11787)
* Korrigerade ett problem som gjorde att webbspårning inte kunde användas för &quot;com.au&quot;-domäner (NEO-4385).
* Ett problem med frysning av klient som kan uppstå när komplexa arbetsflöden används har åtgärdats. (NEO-11847)
* Korrigerade ett Oracle-fel när en ny leverans sparades efter att ett element i ett specifikt schema har valts (NEO-11682).
* Korrigerade ett problem vid sökning efter ett fält som innehåller tecken med accenter (FDA/Teradata). Med det externa kontot kan du nu ändra kodningen som används för att kommunicera med Teradata-drivrutinen. (NEO-11818).
* Korrigerade ett spårningsproblem vid överföring av URL:er i ytterligare variabler i ett push-meddelande som kunde leda till felaktigt formaterade eller felaktiga data som togs emot av mobilprogrammet. (NEO-11468, NEO-11960)
* Korrigerade ett problem som orsakade ett visningsproblem vid användning av en värdefördelning med en 1:N-länk. (NEO-11820)
* Korrigerade ett problem som förhindrade massbelastning från att arbeta med Teradata 16.
* Ökade buffertstorleken för tidsstämpel på Teradata för att undvika bindningsproblem med drivrutinen 15.10.
* Förbättrad hantering av index för långa namn, vilket kan orsaka problem efter uppgraderingen.
* Förbättrat delat minne som är tillgängligt under den underordnade processerna.
* Korrigerade ett möjligt dödläge i Apache (spårning).

## Version 18.4.4 - build 8936{#release-18-4-4-build-8936}

1 augusti 2018

**Förbättringar**

* Loggarna för e-postarkivering har förbättrats, vilket gör det enklare och tydligare att kontrollera vilka e-postmeddelanden som har levererats eller misslyckats via BCC-arkivering. (NEO-10675)
* Korrigerade ett problem som ledde till att IP-adresser för belastningsutjämnare visades i stället för IP-adresser för kunder i spårningsloggarna. (NEO-11295)
* Korrigerade ett fel med LATIN1-kodning vid användning av en FDA-anslutning till en PostgreSQL-databas. (NEO-11299)
* Ett problem som uppstod när leveransalternativet användes har korrigerats. **[!UICONTROL Prepare the personalization data with a workflow]** (NEO-11047, NEO-11301)
* Korrigerade ett slumpmässigt problem som medförde att egenskaperna för en leverans skrevs över felaktigt. (NEO-11015)
* Ett problem har korrigerats när beräknade fält användes i en **[!UICONTROL Survey answers]** arbetsflödesaktivitet. (NEO-11382)
* Ett problem har korrigerats när data som lagrats i XML användes i en **[!UICONTROL Survey answers]** arbetsflödesaktivitet. (NEO-10816)
* Ett problem som uppstod när servern skulle uppgraderas med build 8935 har korrigerats.
* Korrigerade ett problem som visade oanvändbara fel i efteruppgraderingsloggen när en arbetsflödesaktivitet inte var helt konfigurerad. **[!UICONTROL Survey answers]**
* FDA Teradata: åtgärdade ett problem med automatiskt inkrementerade fält och index i SQL-tabeller.

## Version 18.4.3 - build 8935{#release-18-4-3-build-8935}

22 juni 2018

**Förbättringar**

* Korrigerade ett problem med spårningskodning i Microsoft Edge och Internet Explorer. (NEO-11257)
* Ett problem med bildlänkspersonalisering i LINE-leveranser har korrigerats. (NEO-11077)
* Ett problem som gjorde att ID-sekvensgenereringsmekanismen inte fungerade korrekt har korrigerats. (NEO-11115)
* Korrigerade ett problem som hindrade sekretessbegäranden (GDPR) från att fungera när ett anpassat namnutrymme med en heltalstypsavstämningsnyckel användes. (NEO-11123)
* Korrigerade ett fel som kan inträffa när alternativet används **[!UICONTROL Distribution of values]** i **[!UICONTROL Query]** arbetsflödesaktiviteter. (NEO-10958)
* Ett problem har korrigerats vid synkronisering av erbjudanden från marknadsinstansen till interaktionsinstansen. (NEO-11162)
* Förbättrad hantering av index för långa namn under efteruppgradering

## Version 18.4.2 - build 8932{#release-18-4-2-build-8932}

22 maj 2018

**Förbättringar**

* Ett problem som gjorde att Windows Server-uppdateringen inte fungerade korrekt har korrigerats.
* Korrigerade ett problem i **[!UICONTROL Survey Result]** aktiviteten när data lagrades i XML användes. Rapporten visades felaktigt. (NEO-10816)
* Korrigerade ett prestandaproblem som kan uppstå med inMail-processen när en server för studsade meddelanden används. (NEO-10641)
* Korrigerade ett databasuppgraderingsfel som kan inträffa vid uppgradering av fler än 1 000 scheman.

## Version 18.4 - build 8931{#release-18-4-build-8931}

24 apr 2018

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
   <td> EU:s allmänna dataskyddsförordning (GDPR)<br /> </td> 
   <td> <p>GDPR är EU:s (EU) nya integritetslagstiftning som harmoniserar och moderniserar dataskyddskraven som träder i kraft den 25 maj 2018. GDPR gäller för Adobe Campaign-kunder som lagrar data för registrerade i EU.</p> <p>Förutom de sekretessfunktioner som redan finns i Adobe Campaign (inklusive samtyckeshantering, datalagringsinställningar och användarroller) tar vi denna möjlighet i vår roll som dataprocessor att inkludera ytterligare funktioner för att underlätta din beredskap som Data Controller för vissa GDPR-förfrågningar:</p> 
    <ul> 
     <li> <p>Åtkomst: ger den registrerade möjlighet att få en kopia av sina personuppgifter som samlats in av personuppgiftsansvariga, inklusive data som lagrats i Adobe Campaign.</p> </li> 
     <li> <p>Höger att ta bort: ger den registrerade rätt att radera sina personuppgifter som samlats in av personuppgiftsansvariga, inklusive data som lagrats i Adobe Campaign.</p> </li> 
    </ul> Mer information finns i den <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">detaljerade dokumentationen</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Aktiva profiler<br /> </td> 
   <td> <p>Adobe Campaign innehåller nu en lista över aktiva profiler som uppdateras månadsvis via ett dedikerat arbetsflöde.</p> <p>Mer information finns i den <a href="../../platform/using/about-profiles.md#active-profiles">detaljerade dokumentationen</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> Förbättrad push-koppling för Android<br /> </td> 
   <td> <p>Android-anslutningen har förbättrats med stöd för högre genomströmning. </p> <p>Mer information finns i den <a href="../../delivery/using/configuring-the-mobile-application.md">detaljerade dokumentationen</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Säkerhetsförbättringar**

* Expandering av externa entiteter har nu inaktiverats för att förhindra potentiella attacker från oautentiserade användare. (NEO-10173)
* Förbättrade behörigheter som förhindrar standardanvändare från att ändra instanskonfigurationsparametrar som URL:er för programåtkomst, LDAP-inställningar osv. (NEO-10171)
* Ett problem som kunde visa känslig information via stackspår har korrigerats. Felinformationen loggas nu i bakänden till en plats som inte är tillgänglig från det externa nätverket. (NEO-10176)
* Förbättrade behörigheter som förhindrar standardanvändare från att visa en administratörs överförda dokument och/eller exporterade paket. (NEO-10170)

**Förbättringar**

* **LINE-kanal - förbättrad** arkitektur: Liksom för alla andra kanaler i Adobe Campaign stöds nu LINE-kanalen för alla distributionstyper: värdbaserad, hybridbaserad och lokal.
* **Automatisk sekvensgenerering**: ID-genereringsmekanismen har förbättrats för att öka livscykeln för Campaign-instanser med stora mängder objekt. Mer information finns i denna [technote](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html).

**Andra ändringar**

* Ett nytt läge är tillgängligt för paketimport via kommandoraden, vilket tillåter cirkulära beroenden (rekommenderas inte för stora paket). Mer information finns i avsnittet&quot;Tekniska lösningar&quot;. (NEO-8979)
* Förbättrade prestanda för stor datainläsning i Teradata och åtgärdade ett problem som hindrade från att visa rätt värde för data som bearbetats i loggen. (NEO-10429)
* Det går nu att importera målgrupper från Audience Manager med delade filer. Tidigare importerades bara den sista filen i segmentet av det tekniska arbetsflödet importSharedAudience. (NEO-10156)
* I Windows har standardinstallationssökvägen för Campaign-servern ändrats. När du startar 64-bitarsversionen är standardinstallationssökvägen nu: **C:\Program Files\Adobe\Adobe Campaign Classic v7** i stället för **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* MX-standardreglerna har förbättrats så att fler domäner inkluderas och genomströmningen optimeras.
* Tvingade åtkomstbegränsningar för distributionsguidens SOAP-anrop (xtk:serverOptions#SaveOptions).
* Det föråldrade biblioteket weka.jar har tagits bort och OpenSSL-biblioteket har uppdaterats för säkerhetsoptimering.
* Förbättrat tekniskt arbetsflöde för fakturering för att säkra instansernas prestanda.
* Administratörernas möjlighet att ange eller återställa lösenordet för en operator har återställts. Om du vill göra det högerklickar du på en operator, väljer **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** och anger operatörens nya lösenord. Vi rekommenderar att operatorer ändrar sina lösenord när de först återansluter. Mer information finns i den [detaljerade dokumentationen](../../production/using/lost-password.md).
* För att ge stöd åt den nya multitenancy-funktionen i Adobe Target kan en ny&quot;at_property&quot;-parameter nu läggas till i URL:er när alternativ och externa konton konfigureras för integrering med Target. Värdet som ska användas för den här parametern finns i Adobe Target och kommer att användas av Campaign när anrop till Target görs. Mer information finns i den [detaljerade dokumentationen](../../integrations/using/inserting-a-dynamic-image.md).
* Du kan nu ange en standardstartsida som ska öppnas när du klickar på en bild som hanteras av Adobe Target. Tidigare ledde klickningen på den bilden till standardbilduppsättningen när e-postmeddelandet skapades i stället. Mer information finns i den [detaljerade dokumentationen](../../integrations/using/inserting-a-dynamic-image.md).
* Lagt till kryssrutan **Aktivera SMPP-spår** i det externa kontot för att framtvinga spårningsutdata. Mer information finns i den [detaljerade dokumentationen](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Teknisk utveckling**

queryDef

queryDef har ändrats angående &quot;orderBy&quot;-satsen. Före ändringen skulle primärnyckeln för den efterfrågade tabellen läggas till i &quot;orderBy&quot;-satsen. I vissa databasmotorer (minst efter progressiv) förhindras användningen av index (alla fält i orderBy-satsen måste täckas av samma index). Om du var beroende av det här beteendet måste du lägga till primärnyckeln explicit i din orderBy-sats.

Om du till exempel har följande fråga:

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
     <node expr="@logDate"/>
   </orderBy>
</queryDef>`
```

Den skulle implicit delas som (före 18.4-ändringarna):

```
<queryDef operation="select" schema="xtk:job" startPath="/" xtkschema="xtk:queryDef">
  <select>
     <node expr="@id"/>
   </select>
   <orderBy>
      <node expr="@logDate"/>
      <node expr="@id"/> <!-- implicitely added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

Funktionen urlEncode

JavaScript-funktionen urlEncode fungerade inte korrekt för icke-ASCII-tecken. Den har korrigerats och bör nu fungera med alla Unicode-tecken (inklusive japanska tecken). Om du förlitar dig på urlEncode-beteendet för icke-ASCII-tecken måste du anpassa koden.

Nytt läge för paketimport

Ett nytt läge är tillgängligt för paketimport via kommandoraden, vilket tillåter cirkulära beroenden (rekommenderas inte för stora paket). Befintliga funktioner behålls. För sådana paket med cirkelberoenden har en ny flagga **-usejs** lagts till i kommandoradspaketimporten. När den körs används JSEngine på samma sätt som när paketimporten utförs från gränssnittet.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**Patchar**

* Ett synkroniseringsproblem har korrigerats vid replikering av leverans- och spårningsloggar från Adobe Campaign Standard till Adobe Campaign Classic. (NEO-10023)
* Korrigerade ett problem med hanteringen av fel- och loggtabeller i Teradata när ett ETL-arbetsflöde återupptogs efter ett fel i en snabb inläsningsåtgärd. Tabellerna Fel och Logg tas nu bort korrekt varje gång arbetsflödet återupptas. (NEO-10672)
* Korrigerade ett efteruppgraderingsfel som innebar att Hive-paketet (som behövs för Hadoop) skulle installeras automatiskt om FDA-paketet installerades. (NEO-10592)
* Korrigerade ett fel som behandlade ogiltiga domäner som ett **odefinierat** fel. (NEO-10248)
* Korrigerade ett problem som duplicerade loggar i tabellen deliveryLogStats när push-leveranser för android skickades. (NEO-10234)
* Korrigerade ett problem som kunde leda till att vissa streckkodsformat inte kunde läsas av streckkodsläsare. (NEO-10125)
* Ett problem med JavaScript-funktionen urlEncode har korrigerats när icke-ASCII-tecken användes. Mer information finns i avsnittet&quot;Tekniska lösningar&quot;. (NEO-10123)
* Ett problem som orsakade att en fråga kördes med sha256-funktioner i Teradata-databaser har korrigerats. (NEO-10119)
* Ett arbetsflödesminnesfel som kan uppstå i SalesForce-aktiviteten när mycket stora SalesForce-tabeller används har åtgärdats. (NEO-9900)
* Korrigerade ett problem med **alternativet Generate-komplement** vid målarbetsflödesaktiviteter när FDA användes. (NEO-9878)
* Korrigerade ett problem som kunde leda till att värdena för **Behandlad** och **Slutfört** inte uppdaterades på marknadsinstansen när mellanleverantörer användes. (NEO-9454)
* Fasta regler för icke-reproposition av interaktion när över 10 kB totalt erbjuder i plattformen (NEO-9352)
* Ett problem som kunde förhindra att målet för en leverans angavs när en extern XML-fil användes har åtgärdats. (NEO-9312)
* Korrigerade ett problem som kunde leda till arbetsflödesfel när en hypotes kördes på ett erbjudande och status för förslaget uppdaterades. (NEO-9304)
* Korrigerade fel som uppstod under leveransanalys när tryckregler användes baserat på ett attribut i Android-leveransmappningen. (NEO-9202)
* Korrigerade ett problem vid sortering efter kolumner i mottagarlistan som kunde resultera i prestandaproblem. Mer information om queryDef-ändringarna finns i avsnittet &quot;Technical evolutions&quot; nedan. (NEO-9042)
* Ett problem har korrigerats där länkarna i ett e-postmeddelande för godkännande kunde peka på en felaktig inloggnings-URL, särskilt när en Federated ID-inloggningstyp används. (NEO-9011)
* Korrigerade ett problem som kunde leda till att fel datum visades i datumväljarna för rapporter för vissa tidszoner. (NEO-9007)
* Korrigerade ett problem som hindrade från att visa målet för en utgående databas när en FDA SQL-databas användes. (NEO-8924)
* Korrigerade ett problem som medförde att MS Dynamics CRM-kopplingen inte kunde hämta data under de första 7 dagarna i månaden. (NEO-8803)
* Ett fel med Analytics-integrering som gjorde att användare inte kunde inkludera internationella tecken har korrigerats. (NEO-8719)
* Korrigerade ett problem som kunde aktivera redigering av arbetsflöden utan rätt behörighet. (NEO-8708)
* Korrigerade ett problem med FDA över HTTP när Message Center användes i en hybridarkitektur, vilket ledde till att anslutningen bröts eller att anslutningen bröts (timeout). (NEO-8438)
* Korrigerade arbetsflödesfel i inkrementell frågeaktivitet för negativa ID:n. (NEO-8229)
* Korrigerade ett problem som kunde leda till att dubbla rullningslister visades på vissa skärmar. (NEO-8208)
* Korrigerade ett problem som ledde till att ett felmeddelande visades när guiden Uppdatera databasstruktur kördes. PostUpgrade byter namn på index med namn som är längre än 30. Tänk på att för stora tabeller tar det tid att ersätta indexet. (NEO-7983)
* Ett problem med att spårningsloggar inte synkroniserades korrekt från körningsinstansen i Message Center till kontrollinstansen har åtgärdats. (NEO-7286)
* Ett prestandaproblem med anrikningsaktiviteten för erbjudanden har korrigerats. (NEO-7263)
* Korrigerade ett problem som förhindrade att funktionen DaysAgo användes när en Redshift-databas efterfrågades via FDA. (NEO-7099)
* Korrigerade en regression i datahanteringen som förhindrade att index skapades i arbetsflödesaktiviteter som påminner om Enrichment.
* Ett problem som kunde inträffa när externa resurser skapades med titeln @id har åtgärdats
* Korrigerade ett problem som kunde inträffa vid överföring av zippade filer via en FTP-server eller vid överföring av filer med jokertecken i filnamnet.
* Ett problem med uppräkningar av lång bastyp i externa anpassade resurser som skapats i Campaign Standard har korrigerats.
* Korrigerade ett problem som kunde leda till att SMS skickades även när anslutningen med providern misslyckades, vilket ledde till att SMS-meddelanden gick förlorade.
* Korrigerade ett fel som gjorde att en SMTP-anslutning fastnade på obestämd tid.
* Korrigerade ett problem med trycktypologiregler under meddelandeförberedelsen när en LINE-mappning användes eller när filtrerings- och målscheman skiljde sig.
