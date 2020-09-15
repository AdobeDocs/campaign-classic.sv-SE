---
title: Version 19.1
seo-title: Version 19.1
description: Version 19.1
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
source-git-commit: edb8f495fff90f51ae00006453b6ec09d84a8f55
workflow-type: tm+mt
source-wordcount: '2639'
ht-degree: 6%

---


# Version 19.1{#release-19-1}

## ![](assets/do-not-localize/limited_2.png) Version 19.1.7 - build 9036 {#release-19-1-7-build-9036}

_15 september 2020_

**Förbättringar**

* Förbättrad användning av nlsrvmod för Apache 2.4-trådar för att korrigera nlsrvmod-krascher.
* Ett problem har korrigerats vid användning av filöverföringsaktiviteten med ett externt Azure-konto och en SSL-kryptering. Anslutningen gjordes via HTTP i stället för HTTPS. (NEO-26720)
* I leveransegenskaper har **[!UICONTROL Archive emails]** alternativet bytt namn **[!UICONTROL Email BCC]** för en bättre användarupplevelse.
* Ett problem med url-cachemekanismen som inte hämtade etiketten eller kategorin har korrigerats.
* Korrigerade ett problem som ledde till att sidans URL:er speglades på ett felaktigt sätt definierades i e-postleveranser (på grund av felaktig ASCII-teckenkontroll). (NEO-26084)
* Listan jarsToSkip i catalina.properties har uppdaterats för att ta bort referensen till en jar-fil som inte längre användes (iOS-meddelanden).
* Korrigerade ett regressionsproblem som förhindrade efter publicering efter efteruppgradering.
* Korrigerade en regression med färdiga leveransrapporter som verkade trunkerade när de exporterades till PDF. (NEO-25757)
* Ett problem som tog bort kodningsparametervärdet vid omdirigering från en spårnings-URL (påverkar japanska tecken) har korrigerats. (NEO-25637)
* Korrigerade ett problem som medförde att osignerade länkar från anpassade domäner blockerades när de borde tillåtas. (NEO-25210)
* Korrigerade en regression som påverkade beräkningsfält i ett arbetsflöde och orsakade att arbetsflödet misslyckades. (NEO-25194)
* Korrigerade ett kompatibilitetsproblem med Microsoft Dynamics (från version 8.2) som kunde förhindra att vissa API-anrop kördes (RetrieveAllEntities). (NEO-24528)
* Ett regressionsproblem som förhindrade anslutningen till en Campaign Standard-instans (felaktig hantering av FOH/FOH2-anslutningen) har korrigerats när funktionen ACS Connector användes. (NEO-23433)
* Ett regressionsproblem i databasanslutningen som gjorde att webbservern hela tiden startades om på grund av ett databaskodningsproblem har åtgärdats. Detta kan leda till överkonsumtion. (NEO-23264)
* Korrigerade ett problem med arbetsflödet för databasrensning som kunde misslyckas på grund av ohanterad datakälla. (NEO-23160 och NEO-23364)
* Rensningsarbetsflödet tömmer nu utgångna listor med grupper om 100 i stället för en i taget.
* Efter växlingen till den [nya sekvens-ID-mekanismen](https://helpx.adobe.com/se/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)publiceras alla webbprogram som uppdaterar mottagartabellen på nytt under efteruppgraderingen.
* Korrigerade ett problem som förhindrade att e-post skickades när det fanns Javascript-kod utanför HTML-innehållstaggen. (NEO-18628)
* Ett problem som förhindrade att spårningsindikatorerna för transaktionsmeddelanden uppdaterades i arbetsflödet för spårning har åtgärdats. (NEO-17770)
* Förbättrade prestanda för guiden Databasuppdatering för att göra färre SQL-satser för att optimera svarstiden.
* Ett kraschproblem som kunde inträffa när spårade URL:er i ett e-postmeddelande avkontrollerades från fliken **Textinnehåll** på grund av en variabel som inte initierats har åtgärdats. (NEO-13545)
* Korrigerade ett problem som förhindrade dig från att överföra filer i en filöverföringsaktivitet med ett externt Azure Blob Storage-konto på grund av en oinitierad variabel (m_pCurlReader). (NEO-13717)
* Korrigerade ett efteruppgraderingsfel som stängde av Apache och webbservern innan webbprogrampubliceringen. (NEO-27155)
* Korrigerade en regression som ledde till att en felaktig tidszon plockades när en tid angavs i en **arbetsflödesaktivitet i schemaläggaren** .

## ![](assets/do-not-localize/orange_2.png) Version 19.1.6 - build 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>Den här versionen är endast avsedd för lokala installationer. För hybriddistributioner fortsätter värdbaserade instanser att köra 9032-versionen. Uppgradera inte din marknadsinstans till 9035-versionen eftersom den inte är kompatibel med 9032.

_3 oktober 2019_

**Förbättringar**

* Ett problem har korrigerats när CRM Connector för Salesforce användes. (NEO-17712)
* Korrigerade ett indexproblem som kunde orsaka prestandaproblem när transaktionsmeddelanden skickades.
* Korrigerade ett prestandaproblem när meddelanden skickades. (NEO-17558)
* Korrigerade ett problem som kunde leda till att vissa meddelanden inte bearbetades av servern för medelkällkod. (NEO-12395)
* Ett problem som förhindrade att SQL Data Management-aktiviteten användes fullt ut har åtgärdats (namngiven SQL Data Management-behörighet saknas).

## ![](assets/do-not-localize/red_2.png) Version 19.1.5 - build 9033{#release-19-1-5-build-9033}

_13 augusti 2019_

**Förbättringar**

* Korrigerade ett problem med SQL-satsen SELECT COUNT som kördes på standarddatabasen i stället för FDA-databasen under dataextraheringen i datahanteringsaktiviteten.
* För att förbättra kundens infrastruktur finns nu en SFTP-proxydeklaration tillgänglig i serverkonfigurationsfilen.
* Korrigerade ett kraschproblem när fältet **Lägg till länkad tabell** var tomt i arbetsflödesaktiviteten **Datainläsning (RDBMS)** . (NEO-12213)
* Ett problem med installationen av paketet midEmitter via kommandoraden har korrigerats.
* Ett nytt autentiseringsalternativ har lagts till som stöd för OAuth-autentiseringsuppgifter i AC-anslutningen med Microsoft Dynamics. (NEO-11982)
* Korrigerade ett problem med UUID-hantering (Unik universell identifierare) som gjorde att arbetsflödesaktiviteterna för fråga och data misslyckades med Hive FDA.
* Korrigerade en regression i Oracle som gjorde att vissa funktioner ansågs vara ogiltiga efter efteruppgradering. (NEO-12759)
* Korrigerade en regression som ledde till att en felaktig tidszon plockades när tiden angavs i en arbetsflödesaktivitet i schemaläggaren.

## ![](assets/do-not-localize/green_2.png) Version 19.1.4 - build 9032{#release-19-1-4-build-9032}

>[!NOTE]
>
>19.1.4 Gold Standard-utgåvorna finns listade på den här [sidan](../../rn/using/gold-standard.md).


## ![](assets/do-not-localize/red_2.png) Version 19.1.2 - build 9029{#release-19-1-2-build-9029}

_21 juni 2019_

**Säkerhetsförbättringar**

* För att optimera säkerheten har Java-biblioteket (Netty) uppdaterats till den senaste versionen (4.1.34). (NEO-12788)

**Förbättringar**

* Korrigerade en regression som är länkad till hantering av domänkolumner, vilket förhindrade att e-postmeddelanden skickades på vissa konfigurationer.
* För att förbättra prestanda har ett _operation=&quot;none&quot;-attribut lagts till i rtEvent SOAP-anrop för att undvika SELECT FOR UPDATE-begäranden.
* Korrigerade ett arbetsflödesvisningsproblem med utgående övergångar efter aktiviteten Testa. (NEO-12727)
* Nu kan vi ta bort dummy-poster som skapats i Microsoft Dynamics under importarbetsflödet.
* Förbättrade behörigheter för att köra säkerhetszonspaketet när ett internt konto används.

## ![](assets/do-not-localize/red_2.png) Version 19.1 - build 9026{#release-19-1-build-9026}

_30 maj 2019_

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
   <td> Kontrollpanelen<br /> </td> 
   <td> <p>Om du vill öka effektiviteten i ditt arbete som Admin-användare hanterar du inställningarna för dina SFTP-servrar genom att övervaka lagringsutrymmet, lägga till IP-adresser i tillåtelselista och installera SSH-nycklar för varje instans. Kontrollpanelen är endast tillgänglig för kunder som har AWS som värd idag (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">inloggning via Experience Cloud idag</a>).</p> <p>Mer information hittar du i den <a href="https://docs.adobe.com/content/help/sv-SE/control-panel/using/control-panel-home.html">detaljerade dokumentationen</a> och <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/administrating/control-panel-acc/control-panel-overview.html">instruktionsvideon</a>. </p><p>Obs! Du behöver inte uppgradera till den senaste Campaign-versionen för att komma åt Kontrollpanelen.</p> </td> 
  </tr> 
    <tr> 
   <td> Verifieringskedja<br /> </td> 
   <td> <p>Som administratör kan du öka produktiviteten genom att övervaka och hantera ändringar som görs i Adobe Campaign Classic-instansen. Granskningsspårningen loggar åtgärder som har gjorts i källscheman, arbetsflöden och alternativ. Du kan snabbt se om ett element har skapats, ändrats eller tagits bort.</p><p>For more information, refer to the <a href="../../production/using/audit-trail.md">detailed documentation</a> and <a href="https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/monitoring/audit-trail.html">how-to video</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Guardrail, robuskhet och skalbarhet<br /> </td> 
   <td> En rad förbättringar har lagts till i Campaign Classic. Förbättringar av säkerhet, stabilitet och skalbarhet visas nedan.<br /> </td> 
  </tr> 
  <tr> 
   <td> Uppdatering av kompatibilitetsmatris<br /> </td> 
   <td> Med den nya versionen har Adobe Campaign nu stöd för följande databassystem. Refer to the <a href="https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html">Compatibility Matrix</a>.<br /> 
    <ul> 
     <li> <p>Oracle 18c</p> </li> 
     <li> <p>MySQL 5.7 (FDA)</p> </li> 
     <li> <p>SQL Server 2017</p> </li> 
     <li> <p>Teradata 16 (FDA)</p> </li> 
     <li> <p>PostgreSQL 11</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Säkerhetsförbättringar**

* Av säkerhetsskäl kan du inte längre infoga godtyckliga kommandon när du använder alternativet **[!UICONTROL Pre-process the file]** i en **[!UICONTROL Data loading (file)]** arbetsflödesaktivitet. Nu finns en nedrullningsbar lista där du kan välja mellan tre alternativ: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) eller **[!UICONTROL Decrypt]** (gpg). XtkSecurity_Disable_Preproc-säkerhetsflaggan har lagts till. För nya kunder anges värdet 0. För befintliga kunder kommer detta alternativ att anges till 1 vid uppgraderingen för att behålla det tidigare beteendet. Refer to this [section](../../workflow/using/data-loading--file-.md).
* Ett problem med lösenordssynlighet som uppstod när anslutningen till ett externt FDA-konto testades utan tidszon har åtgärdats.
* PDFBox-biblioteket har tagits bort.
* Tomcat har uppdaterats till version 7.0.93.
* Ett problem med synlighet för token som uppstod när säkerhetstoken var ogiltig har åtgärdats.
* Korrigerade ett potentiellt XTK-injektionsproblem i WSDL JSP (schemawsdl.jsp).
* Lagringsutrymmet för autentiseringsuppgifter och lösenord i programmets källkod och minne har optimerats.
* PII-visningsbegränsningen har optimerats. (NEO-12339, NEO-12396, NEO-12398, NEO-12339, NEO-12667)
* Åtgärdade inkonsekvenser i hanteringen av hemliga nycklar.
* Samma generiska fel visas nu för misslyckade inloggningsförsök med ett giltigt eller ogiltigt användarnamn.
* Namngivningen på överförda filer har förbättrats.
* Ett nytt XtkSecurity_Disable_GetSetEnv-alternativ har lagts till för att blockera användningen av funktionerna setEnv och getEnv.
* Känslig information döljs nu i programstackens spårning.

**Förbättringar av säkerhetsfunktioner, stabilitet och skalbarhet**

* Lifespan - XtkNewId-sekvensoptimering: de mest använda tabellerna har flyttats från xtkNewId-sekvensen till dedikerade sekvenser. [Läs mer](https://helpx.adobe.com/se/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)
* FDA över HTTP v2: FDA över HTTP-protokollet används ofta vid hybriddriftsättningar, särskilt vid hämtning av breda loggar och leveransförberedelser. Robusiteten har förbättrats för att undvika nätverksproblem och eventuella fel som hämtning eller överföring av data. Detta kräver att byggen i båda ändar av anslutningen är uppdaterade, annars kommer det gamla protokollet fortfarande att användas.
* Arbetsflöde för spårning: spårningsarbetsflödets tillförlitlighet har förbättrats. Flera problem med att spåra logginfogningar/uppdateringar och anpassning av URL-spårning har åtgärdats. Dessutom upptäcker arbetsflödet nu loggproblem som kan leda till fel och stoppa arbetsflödet. Dessa problem har nu ignorerats och bearbetats inte.
* Rensningsarbetsflöde: rensningsarbetsflödet har förbättrats för att undvika potentiella fel och stopp. Detta optimerar databasens storlek och prestanda.
* Inbäddade bilder i transaktionsmeddelanden: vi har lagt till fullständigt stöd för inbäddade bilder i transaktionsmeddelanden för att undvika eventuella krascher eller saknade bilder.
* Databasstorlek - XtkJobLog: en tömningsmekanism har lagts till i tabellen. Detta påverkar databasstorleken positivt.
* BCC-arkivering: standardparametrarna för BCC-arkivering har ändrats för att öka arkiveringshastigheten. [Läs mer](../../installation/using/email-archiving.md#parameters)
* Databasstrukturuppdatering: SQL-begäranden som genereras av guiden Uppdatera databasstruktur har förbättrats för snabbare körning.
* Garantier för operatoråtgärder: flera skyddsräcken har implementerats för att hindra operatorer från att utföra åtgärder som kan påverka plattformens integritet. Inbyggda scheman kan inte längre tas bort via gränssnittet. Arbetsflödets källa-XML kan inte längre redigeras av icke-adminanvändare.
* Två nya alternativ har gjorts tillgängliga: **XtkSecurity_Restrict_EditXML** (gör att du kan inaktivera utgåvan av leveransernas XML-kod) och **NmsOperation_OperationMgtDebug** (gör att du kan övervaka körningen av operationMgt-arbetsflödet). [Läs mer](../../installation/using/configuring-campaign-options.md)

**Andra ändringar**

* Push-meddelanden: har vi nu stöd för alternativet Tråd-ID för iOS-push.
* Förbättrad hantering av index för långa namn, vilket kan orsaka problem efter uppgraderingen.
* Om publiceringsläget är inställt på **[!UICONTROL None]** i distributionsguiden, loggas ett fel och analysen stoppas nu när analysen av en detaljerad leverans analyseras: &quot;Publiceringsläget är inställt på &#39;none&#39;: Det går inte att bädda in bilden. Bilderna visas inte på telefonen.&quot; (NEO-12208)
* Sändningshanteringen har förbättrats för transaktionsmeddelanden. När utsändningsloggar synkroniseras från körningsinstansen till kontrollinstansen uppdateras fältet @lastModified till systemets aktuella datum. Alternativet MC_Update_BlLastModified har lagts till för kontrollinstanser. True betyder att det aktuella datumet kommer att användas för kontrollinstansen (standardbeteende). Falskt innebär att vi använder körningsinstansens utsändningsdatum @lastModified. (NEO-12579)
* Index lades till i kupongtemporära tabeller för att optimera leveransen. (NEO-12437)
* I Analytics-integreringen är det nu tillåtet att hämta AAM segmentdata med tecknet %. (NEO-12025)
* 10 000 poster har tagits bort i heatmap-kartan för arbetsflöde för att åtgärda ett problem med saknade data. (NEO-12329)
* Open Office stöds inte och har nu tagits bort helt från programmet. Om du fortfarande använde den kan du gå över till Library Office eftersom det inte längre fungerar från och med 19.1.
* Nu kan du begränsa skrivåtkomst till Uppdatera dataaktivitet i arbetsflöde med hjälp av sysfilter-attribut. [Läs mer](../../configuration/using/filtering-schemas.md)

**Felkorrigeringar**

* Ett problem som gjorde att certifikatet inte kunde överföras för iOS-mobilpush-meddelanden har korrigerats.
* Potentiella återkommande serverkrascher för transaktionspush-meddelanden har korrigerats. Andra kraschproblem har åtgärdats.
* Ett problem som orsakade rapporteringsavvikelser mellan användaraktiviteter och spårningsrapporter för indikatorn för öppen leverans har korrigerats. (NEO-11742)
* Ett problem med IMS-inloggningen har korrigerats.
* Korrigerade ett problem som kan leda till att bilder saknas i en leverans när en bild läggs till från biblioteket. (NEO-11900)
* Korrigerade ett problem som kunde inträffa vid extrahering av erbjudandeinformation i en direktpostleverans. (NEO-11700)
* Ett problem som kunde påverka SMS-transaktionsmeddelandets prestanda har åtgärdats. (NEO-9812)
* Korrigerade en konsolkrasch som kunde inträffa när alternativet Definierad i en extern fil användes för huvudmålet för en leverans. (NEO-12349)
* Korrigerade ett fel vid analys av ett meddelande som riktade till mottagare för japanska (.JP)-domäner. (NEO-12246)
* Korrigerade ett visningsproblem vid användning av en värdefördelning med en 1:N-länk. (NEO-12212 och NEO-11820)
* Korrigerade ett problem som kunde orsaka NmsMxDomain-fel i MTA-loggarna efter en efteruppgradering. (NEO-12752)
* Ett problem har korrigerats när alternativet Behåll alla ytterligare data från huvuduppsättningen användes i en arbetsflödesaktivitet för anrikning. (NEO-13291)
* Korrigerade ett Tomcat-kraschproblem när push-meddelanden skickades med HTTP2. (NEO-12701)
* Korrigerade ett problem med HTTPRequest-API som inte väntade på att alla återanrop skulle slutföras. (NEO-12628)
* Korrigerade ett problem med datorprocessen med spårningsindikatorer för transaktionsmeddelanden. (NEO-12529)
* Ett problem med användningen av teman i erbjudandehanteringen har korrigerats. (NEO-11804)
* Korrigerade ett prestandaproblem när push-meddelanden skickades. (NEO-11787)
* Ett problem har korrigerats vid förhandsgranskning av utgående XML- eller CSV-fil i offerthantering för direktreklam. (NEO-11290)
* Ett problem har korrigerats vid installation av paketet **Hantera sociala nätverk** (social marknadsföring). (NEO-12081)
* Korrigerade ett problem som hindrade dig från att ta bort ett webbprogram även om du hade rätt åtkomstbehörighet. (NEO-12072)
* Korrigerade ett problem som kunde göra att vissa värden skrevs över vid export och sedan import av ett objekt via XML. Alternativet XtkExport_IncludeDefaultValues har lagts till. Om du anger True (standardbeteende) exporteras alla värden. Om värdet är Falskt skrivs ändringarna över med standardvärdet. (NEO-11979)
* Korrigerade ett problem som gjorde att arbetsflödesaktiviteten misslyckades när en anrikningsaktivitet lades till efter en fråga. **[!UICONTROL Alert]** (NEO-12132)
* Korrigerade ett problem i Oracle-inställningar där förskjutningar för pipeline (utlösare) inte hämtades från databasen som orsakade dubbletter. (NEO-12121)
* Korrigerade ett problem som kunde orsaka visningsfel i pivottabeller när Analytics-integrering användes (NEO-12103)
* Korrigerade ett problem med den beskrivande analysrapporten. (NEO-11414)
* Korrigerade ett problem med CRM-anslutningar när fjärrtabellen innehöll ett fält med ett understreck i namnet.
* Korrigerade ett problem som kunde orsaka ett visningsproblem för valutasymboler i hypotesrapporterna. (NEO-11634)
* Korrigerade ett problem med omdirigering och spårning när vissa tecken användes i spårningslänkar.
* Korrigerade ett problem som gjorde att förhandsgranskningen av erbjudandet inte fungerade korrekt.
* Ett problem med att mjuka studsar inte togs bort från adresstabellen har korrigerats.
* Korrigerade ett JAVA-fel när streckkoder användes.
* Korrigerade ett översättningsfel i webbprogram (NEO-12460)
* Ett problem med arbetsflödesaktiviteten s3 Filöverföring har korrigerats. (NEO-12473)
* Ett problem med datumfält i webbprogram har korrigerats. (NEO-12496)
* Ett problem med att ta bort ID när dirigerade adresser används i en leverans har korrigerats. (NEO-11842)
* Ett problem med kompatibilitet mellan phantomjs och Debian 9 har korrigerats.
* Korrigerade ett fel vid godkännande av innehållet i ett korrektur. (NEO-12725)
* Ett problem med arbetsflödesfunktionen Exkludera den här delmängden från ifyllningen har korrigerats. (NEO-12441)
* Korrigerade ett problem med HTTPRequest-wait-API som inte väntade på att alla återanrop skulle slutföras. (NEO-12628)
* Korrigerade ett problem med aktiviteten Uppdatera delad publik i en delad aktivitet. (NEO-11562)
* Korrigerade ett webbserverkraschproblem. (NEO-12904)
* Ett problem med parametern Nature i transaktionsmallar har korrigerats. (NEO-12334)
* Korrigerade ett kraschproblem i konsolen när spårade URL:er visades i e-posttextredigeraren. (NEO-13122)
* Ett problem med aktiviteten Dela fil när målgrupper importerades från Audience Manager har korrigerats. (NEO-11550)
* Korrigerade ett problem som orsakade fel i snabbklicksrapporten. (NEO-11459)
* Ett problem med erbjudandeåtergivning har korrigerats. (NEO-11565)
* Ett problem med aktiviteten Listuppdatering när målgrupper importerades från Audience Manager har korrigerats. (NEO-11226)
* Ett problem med schemaaktiviteten och tidszonskonfigurationen har korrigerats. (NEO-11662)
* Korrigerade ett problem som gjorde att spårningsarbetsflödet misslyckades om URL:er hade felaktigt format.
* Ett problem med externa konton har korrigerats efter import av mobilprogrampaketet.
* Korrigerade ett problem när en tidszon tilldelades en operator. (NEO-12464)
* Ett problem som kunde orsaka fel i datorloggarna har korrigerats. (NEO-11539 och NEO-8978)
* Ett problem som uppstod när du klickade på ikonen Historik i en sparad rapport korrigerades. (NEO-11620)
* Ett problem har korrigerats vid redigering av en pivottabell i en rapport. (NEO-12068)
