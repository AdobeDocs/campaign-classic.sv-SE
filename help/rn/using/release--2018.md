---
product: campaign
title: Campaign Classic 2018-versioner
description: Läs mer om Campaign Classic 2018-versioner
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
hidefromtoc: true
exl-id: f70fceba-4bbf-4f33-8746-e4405a1cdae6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '5385'
ht-degree: 7%

---

# 2018-versioner{#release-2018}



## Version 18.10

### Version 18.10.6 – build 8985{#release-18-10-6-build-8985}

12 juli 2019

**Förbättringar**

* Nu kan vi ta bort dummy-poster som skapats i Microsoft Dynamics under importarbetsflödet.
* Korrigerade ett problem med arbetsflödesaktiviteten för filinsamlaren som kunde logga fel i en slinga när åtkomst till en fil nekades. (NEO-12085)
* Ett problem som orsakade rapporteringsavvikelser mellan användaraktiviteter och spårningsrapporter för indikatorn för öppen leverans har korrigerats. (NEO-11742)
* Förbättrade behörigheter för att köra säkerhetszonspaketet när ett internt konto används.
* Ett problem som kunde orsaka fel i datorloggarna har korrigerats. (NEO-8978)

### Version 18.10.5 – build 8984{#release-18-10-5-build-8984}

23 april 2019

**Förbättringar**

* Korrigerade ett problem med SQL-deadlock som gjorde att leveransanalysen misslyckades vid samtidig analys/sändning (när två leveranser analyserades samtidigt). (NEO-13026)
* 10 000 poster har tagits bort i heatmap-kartan för arbetsflöde för att åtgärda ett problem med saknade data. (NEO-12329)
* Ett problem har korrigerats när alternativet Behåll alla ytterligare data från huvuduppsättningen användes i en arbetsflödesaktivitet för anrikning. (NEO-13291)

### Version 18.10.4 – build 8983{#release-18-10-4-build-8983}

15 april 2019

**Förbättringar**

* Korrigerade ett problem med datorprocessen med spårningsindikatorer för transaktionsmeddelanden. (NEO-12529, NEO-12581)
* Korrigerade ett problem med HTTPRequest-API som inte väntade på att alla återanrop skulle slutföras. (NEO-12628)
* Index lades till i kupongtemporära tabeller för att optimera leveransen. (NEO-12437)
* Korrigerade ett fel vid analys av ett meddelande som riktade till mottagare för japanska (.JP)-domäner. (NEO-12246)
* I Analytics-integreringen är det nu tillåtet att hämta AAM segmentdata med tecknet %. (NEO-12025)
* Korrigerade ett Tomcat-kraschproblem när push-meddelanden skickades med HTTP2. (NEO-12701)

### Version 18.10.3 – build 8981{#release-18-10-3-build-8981}

29 januari 2019

>[!CAUTION]
>
>Det här bygget har återkallats. Please [uppgradera till den senaste versionen](../../production/using/build-upgrade.md)  eller kontakt [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
* Korrigerade ett problem som förhindrade växling från FDA till SOAP-synkroniseringsmetod i ett externt MID-källkonto.

### Version 18.10.2 – build 8978{#release-18-10-2-build-8978}

6 december 2018

>[!CAUTION]
>
>Det här bygget har återkallats. Please [uppgradera till den senaste versionen](../../production/using/build-upgrade.md) eller kontakt [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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


### Version 18.10.1 – build 8977{#release-18-10-build-8977}

5 nov 2018

>[!CAUTION]
>
>Det här bygget har återkallats. Please [uppgradera till den senaste versionen](../../production/using/build-upgrade.md) eller kontakt [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Nyheter**

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
     <li> <p>Skicka feedback vid registreringssamtal i iOS</p> </li> 
     <li> <p>Snabbare färdigställande av iOS</p> </li> 
    </ul> <p>Som en del av GCM-avskrivningen av Google tillåter nu Android V2-kopplingen bara anslutningar till FCM-servern.</p><p>Mer information finns i den <a href="../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md">detaljerade dokumentationen</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> SQL Data Management-aktivitet<br /> </td> 
   <td> <p>En ny datahanteringsarbetsflödesaktivitet har lagts till. The <strong>SQL Data Management</strong> kan du skriva eller kopiera och klistra in egna SQL-skript för att skapa och fylla i arbetstabeller (endast FDA). </p> <p>Mer information finns i den <a href="../../workflow/using/sql-data-management.md">detaljerade dokumentationen</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Arbetsflödesövervakning<br /> </td> 
   <td> <p>Med nya Adobe Campaign Workflow HeatMap kan plattformsadministratörerna snabbt visa upp alla samtidiga arbetsflöden, vilket gör att de kan övervaka belastningen på instansen och planera arbetsflödena därefter.</p> <p>Mer information finns i den <a href="../../workflow/using/heatmap.md">detaljerade dokumentationen</a>.</p> <p>Workflow HeatMap-paketet är också tillgängligt på begäran för byggen före 8977 (med början build 8700). Mer information om hur du begär och installerar det finns i <a href="https://helpx.adobe.com/campaign/kb/install-workflow-heatmap-package.html">den här sidan</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Säkerhetsförbättringar**

* Korrigerade ett säkerhetsproblem som kunde leda till sårbarheter för attacker med SSRF (Server Side Request Forgery) och DoS-attacker (denial of service). (NEO-11453)
* Innehåll (spåra omdirigering, spegelsidor, undersökningar osv.) kommer nu att hanteras av Campaign med X-Robots-Tag: nocache-huvud. Detta förhindrar att innehållet indexeras av sökmotorer på Internet. (NEO-11101)
* Ett XTK-injektionsproblem i prenumerations-API har korrigerats (nms):subscription:Avbeställ prenumerationer och telefonnummer:subscription:Prenumerera).
* Korrigerade ett XTK-injektionsproblem i webbprogrammet för avprenumeration.
* Lösenord som inte visades på ett säkert sätt i vissa SMS-loggar har tagits bort.

**Förbättringar**

* API:er i Campaign Classic finns nu på en [dedikerad sida](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=sv). Om du använder filen jsapi.chm bör du nu använda den nya versionen online.
* PostgreSQL 10, Debian 9 och Teradata 16.20 stöds nu. Se [kompatibilitetsmatrisen](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html).
* När du skapar en SFTP-anslutning kan du nu använda proxyautentisering. Mer information finns i [detaljerad dokumentation](../../installation/using/file-res-management.md) (NEO-9868)
* The **Formel för datumberäkning** är nu tillgängligt i leveransegenskaperna när du skapar en enskild leverans med hjälp av mallen för direktleverans. (NEO-9792)
* Domännamnshanteringen har förbättrats för cookie-spårning och webbprogram. Mer information finns i avsnittet &quot;Technical Evolutions&quot; nedan.
* Importen av Adobe Marketing Cloud delade resurser på en leverans- eller landningssida har förbättrats vad gäller säkerhet och prestanda.
* Det finns en ny kryssruta i det externa kontot för mobilkanaler som gör att du kan aktivera detaljerade SMPP-spår i loggfilen, vilket gör att dessa utdata är direkt tillgängliga från Adobe Campaign-gränssnittet.
* I utsändningarna görs nu en skillnad mellan det maximala antalet anslutningar och det maximala antalet meddelanden per timme. När gränserna nås är det sedan möjligt att veta varför genomströmningen är begränsad. Tidigare gällde samma meddelande (&quot;kvoten uppfylldes&quot;) i båda fallen.
* Du kan nu ange ett SQL-skript som ska köras när du hämtar en anslutning från poolen. Skriptet kan användas för att ange standardschema. Skriptet används efter frågebanding. (NEO-11256)
* Campaign SDK lagrar inte längre användar-ID:t så att det uppfyller våra PII-regler. Data lagras nu som en hash.
* När du importerar en XML-fil för paketexport stöder Campaign nu att det finns strukturlistor i filen, även om kodningen uttryckligen deklareras i den.

**Tekniska utvecklingar**

Klient- och serveruppgradering

>[!CAUTION]
>
>Om du har en server som har uppdaterats till 18.10 måste du använda en 18.10-klient för att få åtkomst till servern. 18.10-klienten kan ansluta till en äldre serverversion.

Hantering av domännamn

Domännamnshanteringen har förbättrats för cookie-spårning och webbprogram.

Nu stöds alla domännamn på andrahandsnivå med två bokstäver som standard (till exempel .aa.com). För mer komplexa domännamn (t.ex. domäner på andrahandsnivå med tre bokstäver som .com.au) måste du lägga till dem i **cookieDomains** alternativet för serverConf (under taggen redirection). Här är ett exempel:

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

**Korrigeringar**

* Ett fel som förhindrade filer från **Webbnedladdning** arbetsflödesaktiviteten hämtas. (NEO-11105)
* Ett fel som ibland lämnade **Skicka indikatorer och kampanjattribut** arbetsflödet i feltillstånd (NEO-10820).
* Korrigerade ett problem som tog bort mottagarlistan som skapades efter att Listuppdateringsaktiviteten kördes i ett arbetsflöde. (NEO-11696)
* Korrigerade ett problem som felaktigt visade kampanjerna en månad framåt i Campaign-kalendern (på en japansk instans). (NEO-11445)
* Ett problem som gjorde att Analytics-konfigurationen inte kunde visas på fliken Web Analytics i leveransegenskaperna har korrigerats. (NEO-11619)
* Korrigerade ett fel som visades när indataformuläret nms:delivery skulle redigeras och sparas. (NEO-10973)
* Korrigerade ett fel i konfigurationen av det externa kontot som uppstod när ett arbetsflöde som innehåller en filöverföringsaktivitet kördes. (NEO-11012)
* Korrigerade ett problem som returnerade tomma rader när funktionen zcat användes för att läsa in filer i datainläsningsaktiviteten. (NEO-11273)
* Korrigerade ett fel som genererade duplicerade breda loggar under leveransanalysen. (NEO-11360)
* Ett problem som ledde till leveransfel på grund av att en sekundärlänknyckel saknas efter att Enrichment-aktiviteten kördes i ett arbetsflöde har åtgärdats. (NEO-11537)
* Korrigerade ett fel som förhindrade att Adobe Campaign avinstallerades eller reparerades när installationssökvägen innehöll specifika kinesiska GB18030-tecken.
* Korrigerade ett problem som kopplade vissa spårningsloggar till fel leverans. (NEO-11412)
* Korrigerade ett problem som kunde orsaka att vissa delar av leveransloggarna fortfarande hade väntande status längre än förväntat. (NEO-11336)
* Korrigerade ett fel som uppstod när en fråga redigerades för att lägga till en kupong i en leverans. (NEO-11037)
* Korrigerade ett problem i rapporter som fick diagrammen att alltid beräkna summan av värdena oavsett vilken aggregerad operator som valdes. (NEO-10913)
* Eftersom funktionen &quot;request.scheme&quot; är inaktuell har den tagits bort från JSAPI-dokumentationen. (NEO-10828)
* Ett problem som gjorde att vissa användare med tidszonskonfigurationer inte kunde logga in på Adobe Campaign har åtgärdats. (NEO-10712)
* Ett problem som uppstod när ett externt mobilkanalskonto konfigurerades med den utökade allmänna SMPP-anslutningen har åtgärdats: om du angav att använda olika parametrar för mottagaren skulle sändaren felaktigt använda dessa parametrar i stället för sina egna parametrar.
* Korrigerade ett problem som gjorde att schemalagda leveranser misslyckades när en frekvens för tryckregeln angavs, eftersom leveranserna hela tiden räknades om efter den första skiljedomsförfarandet. (NEO-10016)
* Korrigerade ett problem som gjorde att IIS-webbservern kraschade under programpoolens återvinningsprocess (i biblioteket nlsrvmod.dll). (NEO-10862)
* Korrigerat ett problem som kunde förhindra sökning av en mottagare i **Profiler och mål** skärm. (NEO-8228)
* Korrigerade ett problem som kunde leda till ett timeout-fel vid åtkomst till mappen Händelsehistorik i ett stort antal poster. (NEO-11738)
* Korrigerade ett problem som kunde leda till att mottagare av LINE-leverans felaktigt returnerades som &quot;Onåbar&quot;. (NEO-10833)
* Ett problem har korrigerats när en arbetsflödesfråga kördes med en extra kolumn i Oraclet. (NEO-11615)
* En förbättring har gjorts för att säkerställa att stängda anslutningar inte sparas i anslutningspoolen under för lång tid. (NEO-11392)
* Ett problem har korrigerats vid användning av en arbetsflödesaktivitet med mål (fråga, datainläsning (RDBMS) osv.) via FDA ansluts till en extern Oraclena tabell som innehåller UTF8-tecken (i tabellnamnet, fältnamnet osv.) och som även innehåller en primärnyckelbegränsning med ett systemgenererat standardbegränsningsnamn. (NEO-10714)
* Korrigerade ett problem som kunde förhindra att HTML-innehållet i en leverans togs bort. (NEO-11327)
* Korrigerade ett problem med förhandsgranskningen av XML- och CSV-filer i ett direktbrev efter att en kampanj har körts. (NEO-11290)
* Ett problem har korrigerats vid sortering av data i en arbetsflödesaktivitet för berikning. (NEO-11394)
* Ett problem har korrigerats vid sortering av data i en anpassad rapport. (NEO-10896)
* Korrigerade ett problem som ledde till fel när inställningen useVault användes med Teradata. (NEO-11399)
* Korrigerade ett problem som gjorde att Adobe Campaign klientkonsol kraschade när flera frågerader togs bort. (NEO-10744)
* Korrigerade ett problem som förhindrade att tryckregler tillämpades i vissa fall vid leverans av direktreklam. (NEO-9004)
* Ett problem som uppstod när datainläsningsaktiviteten användes för att importera en kolumn med datatypen&quot;time&quot; har korrigerats: tidsavgränsaren återställs även sedan den tagits bort. (NEO-10743)
* Ett problem som gjorde att mappen Leveranser inte kunde visas i körningsmappslistan i leveransegenskaperna när en återkommande leverans redigerades har åtgärdats. (NEO-11094)
* Korrigerade ett problem som gjorde att visningsfönstret inte kunde visa mer än 200 poster som resultatmål för en Query-aktivitet i ett arbetsflöde. (NEO-11195)
* Korrigerade ett fel i Oraclet som förhindrade att en DELETE-fråga kördes med fler än 1 000 markerade element. (NEO-11171)
* Korrigerade ett problem som ledde till att URL:er kodades som spårade URL:er i de ytterligare parametrarna för en leverans av ett push-meddelande från Android. (NEO-11468)
* Korrigerade ett skriptfel som uppstod i rapporten för användaraktiviteter när parametrarna angavs till&quot;Ett dagintervall&quot; och&quot;Öppnar&quot;. (NEO-11655)
* Korrigerade ett problem som uppstod vid anslutning till servern med mellanlagring eller till meddelandecentret via en autentiserad webbproxy. (NEO-11309)
* Korrigerade ett Oracle-fel som inträffade när en ny leveranskomposition sparades efter att ett element i ett specifikt schema markerats **baserat på en SQL-vy**. (NEO-11682)
* Korrigerade ett problem som ledde till att avvisade filer som innehöll falska positiva värden vid bearbetning av en ZIP-fil som innehåller en CSV-fil via en inläsningsfilaktivitet med alternativet Dekomprimering.
* xtkjoblog rensas nu av rensningen.

## Version 18.6

### Version 18.6.2 – build 8949{#release-18-6-3-build-8949}

22 augusti 2018

>[!CAUTION]
>
>Det här bygget har återkallats. Please [uppgradera till den senaste versionen](../../production/using/build-upgrade.md) eller kontakt [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Nyheter**

<table> 
 <thead> 
  <tr> 
   <th> Funktionalitet<br /> </th> 
   <th> Beskrivning<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Frågeränder<br /> </td> 
   <td> <p>När flera Campaign-användare ansluter till samma externa FDA-Teradata-konto kan du nu skicka ett frågeband (nyckel/värde-par) som är specifikt för varje användare. Varje gång en Campaign-användare utför en fråga i Teradata-databasen kan Adobe Campaign nu skicka metadata som är kopplade till användaren. Dessa data, som består av en lista med nycklar och värden, kan sedan användas av Teradata-administratörer för revision eller för att hantera åtkomsträttigheter, till exempel.</p><p>Mer information finns i den <a href="../../installation/using/external-accounts.md">detaljerade dokumentationen</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Förbättringar**

* Loggarna för e-postarkivering har förbättrats, vilket gör det enklare och tydligare att kontrollera vilka e-postmeddelanden som har levererats eller misslyckats via BCC-arkivering. (NEO-10675)
* Korrigerade ett problem som ledde till att IP-adresser för belastningsutjämnare visades i stället för IP-adresser för kunder i spårningsloggarna. (NEO-11295)
* Korrigerade ett slumpmässigt problem som medförde att egenskaperna för en leverans skrevs över felaktigt. (NEO-11015)
* Korrigerade ett syntaxfel vid sortering av resultat för anrikningsaktivitet. (NEO-11394)
* Ett problem har korrigerats när beräknade fält används i en **[!UICONTROL Survey answers]** arbetsflödesaktivitet. (NEO-11382)
* Tomcat har uppdaterats för att förhindra utnyttjande av sårbarheter. (NEO-11503)
* Korrigerade ett fel med LATIN1-kodning vid användning av en FDA-anslutning till en PostgreSQL-databas. (NEO-11299)
* Ett problem som uppstod när **[!UICONTROL Prepare the personalization data with a workflow]** leveransalternativ. (NEO-11047)
* Korrigerade ett efteruppgraderingsfel som förhindrade att SMS skickades när en utökad anslutning användes.
* Förbättrad import/export av paket (logg och region lades till i gränssnittet).
* Ett problem som visade oanvändbara fel i efteruppgraderingsloggen när en **[!UICONTROL Survey answers]** arbetsflödesaktiviteten har inte konfigurerats fullständigt.

**Tekniska utvecklingar**

Frågeränder

En specifik nyckel (PROXYUSER eller PROXYROLE) används för att associera en Teradata användare eller roll med en Campaign-användare. En ny behörighet har lagts till för att använda den här proxyanvändaren/rollen. Du måste lägga till behörigheten GRANT CONNECT VIA till databaskontot (den som definieras i Teradatans externa konto).

En ny flik har lagts till i Teradatans externa konton. The **[!UICONTROL Query banding]** -fliken innehåller följande alternativ:

* **[!UICONTROL Active]**: om du vill aktivera funktionen.
* **[!UICONTROL Default]**: Ange ett standardfrågeband som ska användas om en användare inte har något associerat frågeband. Om inget standardfrågeband har definierats kan de användare som inte har något associerat frågeband inte använda Teradata.
* **[!UICONTROL Users]**: för varje användare anger du ett frågefält. Du kan lägga till så många nyckel-/värdepar du behöver. Till exempel: &quot;priority=1;workload=high;&quot;

Mer information om frågeflätning finns i följande artiklar:

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

### Version 18.6.1 – build 8947{#release-18-6-build-8947}

25 juni 2018

>[!CAUTION]
>
>Det här bygget har återkallats. Please [uppgradera till den senaste versionen](../../production/using/build-upgrade.md) eller kontakt [teknisk support](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Nyheter**

<table> 
 <thead> 
  <tr> 
   <th> Funktionalitet<br /> </th> 
   <th> Beskrivning<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Säkerhetsförbättringar<br /> </td> 
   <td> Ett antal säkerhetsförbättringar har lagts till i Campaign Classic. Förbättringar och korrigeringar visas nedan.<br /> </td> 
  </tr> 
  <tr> 
   <td> Stöd för Windows Server 2016<br /> </td> 
   <td> Adobe Campaign är nu kompatibelt med Windows Server 2016. Se <a href="https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html">Kompatibilitetsmatris för Campaign Classic</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Säkerhetsförbättringar**

decryptString

The **decryptString** funktionen är föråldrad. Se [Föråldrade och borttagna funktioner](deprecated-features.md) artikel.

För nya kunder används den här funktionen nu bara för att dekryptera mottagarens krypterade ID på landningssidor. Om du vill dekryptera lösenord som lagras i ett externt konto använder du det nya **decryptPassword** funktion.

För befintliga kunder ändras inte funktionens beteende, men vi rekommenderar att du använder **decryptPassword** i stället för **decryptString**. The **XtkSecurity_Unsafe_DecryptString** Kompatibilitetsalternativet läggs till av efteruppgraderingen och aktiveras som standard, så att du kan fortsätta använda funktionen. Om du vill inaktivera **decryptString**, avaktivera alternativet.

decryptPassword

The **decryptPassword** funktionen har lagts till. Du kan dekryptera ett lösenord som lagras i ett externt konto. Se [JSAPI](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html) mer information.

Fil-API:er

För nya installationer är mappåtkomst via fil-API:er begränsad till **var**, **sftp** och temporära mappar för Adobe Campaign.

För befintliga kunder har fil-API:er inte längre åtkomst till **conf** Adobe Campaign. The **XtkSecurity_Disable_JSFileSandboxing** Kompatibilitetsalternativet läggs till av efteruppgraderingen och aktiveras som standard, så att du kan fortsätta komma åt de andra mapparna. Om du vill begränsa åtkomsten till **var**, **sftp** och tillfälliga mappar med Adobe Campaign inaktiverar du alternativet.

**Lappa**

* Ett problem som kunde påverka SMS-transaktionsmeddelandets prestanda har åtgärdats. (NEO-9812)

## Version 18.4

### Version 18.4.5 – build 8937{#release-18-4-5-build-8937}

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
* Ett problem har korrigerats vid sökning efter ett fält som innehåller tecken med accenter (FDA/Teradata). Med det externa kontot kan du nu ändra kodningen som används för att kommunicera med Teradata-drivrutinen. (NEO-11818).
* Korrigerade ett spårningsproblem vid överföring av URL:er i ytterligare variabler i ett push-meddelande som kunde leda till felaktigt formaterade eller felaktiga data som togs emot av mobilprogrammet. (NEO-11468, NEO-11960)
* Korrigerade ett problem som orsakade ett visningsproblem vid användning av en värdefördelning med en 1:N-länk. (NEO-11820)
* Korrigerade ett problem som förhindrade massbelastning från att arbeta med Teradata 16.
* Ökade buffertstorleken för tidsstämpling på Teradata för att undvika bindningsproblem med drivrutinen 15.10.
* Förbättrad hantering av index för långa namn, vilket kan orsaka problem efter uppgraderingen.
* Förbättrat delat minne som är tillgängligt under den underordnade processerna.
* Korrigerade ett möjligt dödläge i Apache (spårning).


### Version 18.4.4 – build 8936{#release-18-4-4-build-8936}

1 augusti 2018

**Förbättringar**

* Loggarna för e-postarkivering har förbättrats, vilket gör det enklare och tydligare att kontrollera vilka e-postmeddelanden som har levererats eller misslyckats via BCC-arkivering. (NEO-10675)
* Korrigerade ett problem som ledde till att IP-adresser för belastningsutjämnare visades i stället för IP-adresser för kunder i spårningsloggarna. (NEO-11295)
* Korrigerade ett fel med LATIN1-kodning vid användning av en FDA-anslutning till en PostgreSQL-databas. (NEO-11299)
* Ett problem som uppstod när **[!UICONTROL Prepare the personalization data with a workflow]** leveransalternativ. (NEO-11047, NEO-11301)
* Korrigerade ett slumpmässigt problem som medförde att egenskaperna för en leverans skrevs över felaktigt. (NEO-11015)
* Ett problem har korrigerats när beräknade fält används i en **[!UICONTROL Survey answers]** arbetsflödesaktivitet. (NEO-11382)
* Ett problem har korrigerats när data som lagrats i XML i en **[!UICONTROL Survey answers]** arbetsflödesaktivitet. (NEO-10816)
* Ett problem som uppstod när servern skulle uppgraderas med build 8935 har korrigerats.
* Ett problem som visade oanvändbara fel i efteruppgraderingsloggen när en **[!UICONTROL Survey answers]** arbetsflödesaktiviteten har inte konfigurerats fullständigt.
* FDA-Teradata: åtgärdade ett problem med automatiskt inkrementerade fält och index i SQL-tabeller.

### Version 18.4.3 – build 8935{#release-18-4-3-build-8935}

22 juni 2018

**Förbättringar**

* Korrigerade ett problem med spårningskodning i Microsoft Edge och Internet Explorer. (NEO-11257)
* Ett problem med bildlänkspersonalisering i LINE-leveranser har korrigerats. (NEO-11077)
* Ett problem som gjorde att ID-sekvensgenereringsmekanismen inte fungerade korrekt har korrigerats. (NEO-11115)
* Korrigerade ett problem som hindrade sekretessbegäranden (GDPR) från att fungera när ett anpassat namnutrymme med en heltalstypsavstämningsnyckel användes. (NEO-11123)
* Ett fel som kan inträffa när **[!UICONTROL Distribution of values]** alternativ i **[!UICONTROL Query]** arbetsflödesaktiviteter. (NEO-10958)
* Ett problem har korrigerats vid synkronisering av erbjudanden från marknadsinstansen till interaktionsinstansen. (NEO-11162)
* Förbättrad hantering av index för långa namn under efteruppgradering

### Version 18.4.2 – build 8932{#release-18-4-2-build-8932}

22 maj 2018

**Förbättringar**

* Ett problem som gjorde att Windows Server-uppdateringen inte fungerade korrekt har korrigerats.
* Ett problem i **[!UICONTROL Survey Result]** när du använder data som lagras i XML. Rapporten visades felaktigt. (NEO-10816)
* Korrigerade ett prestandaproblem som kan uppstå med inMail-processen när en server för studsade meddelanden används. (NEO-10641)
* Korrigerade ett databasuppgraderingsfel som kan inträffa vid uppgradering av fler än 1 000 scheman.

### Version 18.4.1 – build 8931{#release-18-4-build-8931}

24 apr 2018

**Nyheter**

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
   <td> <p>GDPR är EU:s (EU) nya integritetslagstiftning som harmoniserar och moderniserar dataskyddskraven som träder i kraft den 25 maj 2018. GDPR gäller för Adobe Campaign-kunder som innehar uppgifter för registrerade personer som bor i EU.</p> <p>Förutom de sekretessfunktioner som redan finns i Adobe Campaign (inklusive samtyckeshantering, datalagringsinställningar och användarroller) tar vi denna möjlighet i vår roll som dataprocessor att inkludera ytterligare funktioner för att underlätta din beredskap som Data Controller för vissa GDPR-förfrågningar:</p> 
    <ul> 
     <li> <p>Åtkomst: ger den registrerade möjlighet att få en kopia av sina personuppgifter som samlats in av personuppgiftsansvariga, inklusive data som lagrats i Adobe Campaign.</p> </li> 
     <li> <p>Höger att ta bort: ger den registrerade rätt att få sina personuppgifter som samlats in av personuppgiftsansvariga raderade, inklusive data som lagrats i Adobe Campaign.</p> </li> 
    </ul> Mer information finns i den <a href="https://helpx.adobe.com/se/campaign/kb/acc-privacy.html">detaljerade dokumentationen</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Aktiva profiler<br /> </td> 
   <td> <p>Adobe Campaign tillhandahåller nu en lista över aktiva profiler som uppdateras varje månad via ett dedikerat arbetsflöde.</p> <p>Mer information finns i den <a href="../../platform/using/about-profiles.md#active-profiles">detaljerade dokumentationen</a>.</p> </td> 
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

* **LINE-kanal - förbättrad arkitektur**: Liksom för alla andra kanaler i Adobe Campaign stöds nu LINE-kanalen för alla distributionstyper: värdbaserad, hybridbaserad och lokal.
* **Automatisk sekvensgenerering**: ID-genereringsmekanismen har förbättrats för att öka livscykeln för Campaign-instanser med stora mängder objekt.

**Andra ändringar**

* Ett nytt läge är tillgängligt för paketimport via kommandoraden, vilket tillåter cirkulära beroenden (rekommenderas inte för stora paket). Mer information finns i avsnittet&quot;Tekniska lösningar&quot;. (NEO-8979)
* Förbättrade prestanda för stor datainläsning vid Teradata och åtgärdade ett problem som hindrade från att visa rätt värde för data som bearbetats i loggen. (NEO-10429)
* Nu går det att importera målgrupper från Audience Manager med delade filer. Tidigare importerades bara den sista filen i segmentet av det tekniska arbetsflödet importSharedAudience. (NEO-10156)
* I Windows har standardinstallationssökvägen för Campaign-servern ändrats. När du startar 64-bitarsversionen är standardinstallationssökvägen nu: **C:\Program Files\Adobe\Adobe Campaign Classic v7** i stället för **C:\Program Files (x86)\Adobe\Adobe Campaign Classic v7**
* MX-standardreglerna har förbättrats så att fler domäner inkluderas och genomströmningen optimeras.
* Tvingade åtkomstbegränsningar för distributionsguidens SOAP-anrop (xtk:serverOptions#SaveOptions).
* Det föråldrade biblioteket weka.jar har tagits bort och OpenSSL-biblioteket har uppdaterats för säkerhetsoptimering.
* Förbättrat tekniskt arbetsflöde för fakturering för att säkra instansernas prestanda.
* Administratörernas möjlighet att ange eller återställa lösenordet för en operator har återställts. Om du vill göra det högerklickar du på en operator och väljer **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** och ange operatorns nya lösenord. Vi rekommenderar att operatorer ändrar sina lösenord när de först återansluter. Mer information finns i den [detaljerade dokumentationen](../../production/using/lost-password.md).
* För att ge stöd åt den nya multitenancy-funktionen i Adobe Target kan en ny&quot;at_property&quot;-parameter nu läggas till i URL:er när alternativ och externa konton konfigureras för integrering med Target. Det värde som ska användas för den här parametern finns i Adobe Target och kommer att användas av Campaign när anrop till Target görs. Mer information finns i den [detaljerade dokumentationen](../../integrations/using/inserting-a-dynamic-image.md).
* Du kan nu ange en standardstartsida som ska öppnas när du klickar på en bild som hanteras av Adobe Target. Tidigare ledde klickningen på den bilden till standardbilduppsättningen när e-postmeddelandet skapades i stället. Mer information finns i den [detaljerade dokumentationen](../../integrations/using/inserting-a-dynamic-image.md).
* Tillagd **Aktivera SMPP-spår** -kryssrutan i det externa kontot för att framtvinga spårningsutdata. Mer information finns i den [detaljerade dokumentationen](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account).

**Tekniska utvecklingar**

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
      <node expr="@id"/> <!-- implicitly added before 18.4, you can add it manually on your query, if you relied on this implicit order clauses --!>
   </orderBy>
</queryDef>
```

Funktionen urlEncode

JavaScript-funktionen urlEncode fungerade inte korrekt för icke-ASCII-tecken. Den har korrigerats och bör nu fungera med alla Unicode-tecken (inklusive japanska tecken). Om du förlitar dig på urlEncode-beteendet för icke-ASCII-tecken måste du anpassa koden.

Nytt läge för paketimport

Ett nytt läge är tillgängligt för paketimport via kommandoraden, vilket tillåter cirkulära beroenden (rekommenderas inte för stora paket). Befintliga funktioner behålls. En ny flagga för sådana paket med cirkelberoenden **-usejs** har lagts till i kommandoradspaketimporten. När den körs används JSEngine på samma sätt som när paketimporten utförs från gränssnittet.

```
nlserver package -instance:fresh -import:sup-packInstallTest.xml -verbose -usejs
```

**Korrigeringar**

* Ett synkroniseringsproblem har korrigerats vid replikering av leverans- och spårningsloggar från Adobe Campaign Standard till Adobe Campaign Classic. (NEO-10023)
* Korrigerade ett problem med hanteringen av fel- och loggtabeller i Teradata när ett ETL-arbetsflöde återupptogs efter ett fel vid en snabb inläsning. Tabellerna Fel och Logg tas nu bort korrekt varje gång arbetsflödet återupptas. (NEO-10672)
* Korrigerade ett efteruppgraderingsfel som innebar att Hive-paketet (som behövs för Hadoopet) skulle installeras automatiskt om FDA-paketet installerades. (NEO-10592)
* Ett fel som behandlade ogiltiga domäner som en **Ej definierad** fel. (NEO-10248)
* Korrigerade ett problem som duplicerade loggar i tabellen deliveryLogStats när push-leveranser för android skickades. (NEO-10234)
* Korrigerade ett problem som kunde leda till att vissa streckkodsformat inte kunde läsas av streckkodsläsare. (NEO-10125)
* Ett problem med JavaScript-funktionen urlEncode har korrigerats när icke-ASCII-tecken användes. Mer information finns i avsnittet&quot;Tekniska lösningar&quot;. (NEO-10123)
* Ett problem som orsakade att en fråga kördes med sha256-funktioner i Teradata-databaser har korrigerats. (NEO-10119)
* Ett arbetsflödesminnesfel som kan uppstå i SalesForce-aktiviteten när mycket stora SalesForce-tabeller används har åtgärdats. (NEO-9900)
* Ett problem med **Generera komplement** för arbetsflödesaktiviteter när FDA används. (NEO-9878)
* Ett problem som kunde leda till **Behandlad** och **Lyckades** mätvärden uppdateras inte i marknadsföringsinstansen när mellanleverantörer används. (NEO-9454)
* Fasta regler för icke-reproposition av interaktion när över 10 kB totalt erbjuder i plattformen (NEO-9352)
* Ett problem som kunde förhindra att målet för en leverans angavs när en extern XML-fil användes har åtgärdats. (NEO-9312)
* Korrigerade ett problem som kunde leda till arbetsflödesfel när en hypotes kördes på ett erbjudande och status för förslaget uppdaterades. (NEO-9304)
* Korrigerade fel som uppstod under leveransanalys när tryckregler användes baserat på ett attribut i Android-leveransmappningen. (NEO-9202)
* Korrigerade ett problem vid sortering efter kolumner i mottagarlistan som kunde resultera i prestandaproblem. Mer information om queryDef-ändringarna finns i avsnittet &quot;Technical evolutions&quot; nedan. (NEO-9042)
* Ett problem har korrigerats där länkarna i ett e-postmeddelande om godkännande kunde peka på en felaktig inloggnings-URL, särskilt när en Federated ID inloggningstyp används. (NEO-9011)
* Korrigerade ett problem som kunde leda till att fel datum visades i datumväljarna för rapporter för vissa tidszoner. (NEO-9007)
* Korrigerade ett problem som gjorde att målet för en utgående databas inte kunde visas när en FDA SQL-databas användes. (NEO-8924)
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
