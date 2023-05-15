---
product: campaign
title: Campaign Classic 2019-versioner
description: Läs mer om Campaign Classic 2019-versioner
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
hidefromtoc: true
exl-id: 8a36a542-e095-4208-b624-e59845592863
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '4825'
ht-degree: 24%

---

# 2019-versioner{#release-2019}



## Version 19.2{#release-19-2}

### ![](assets/do-not-localize/limited_2.png) Version 19.2.4 – build 9082 {#release-19-2-4-build-9082}

_15 april 2021_

* Korrigerade en klientkonsolregression som orsakade bestående felmeddelanden på IMS-anslutningsskärmen. (NEO-34821)

**Endast konsoluppgraderingen är obligatorisk. Ingen serveruppgradering krävs.**

>[!NOTE]
>
> Anslut till [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) för att hämta den nya versionen. Läs om hur du föreslår en konsoluppdatering för alla slutanvändare [på den här sidan](../../installation/using/client-console-availability-for-windows.md).

_22 mars 2021_

* Korrigerade en regression som förhindrade användning av vissa komponenter i konsolen, som datumväljaren och bildhantering i leveranser. (NEO-31453, NEO-31454)

**Endast konsoluppgraderingen är obligatorisk. Ingen serveruppgradering krävs.**

>[!NOTE]
>
> Anslut till [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) för att hämta den nya versionen. Läs om hur du föreslår en konsoluppdatering för alla slutanvändare [på den här sidan](../../installation/using/client-console-availability-for-windows.md).

_23 december 2020_

>[!CAUTION]
>
> * Den här versionen inkluderar ett nytt anslutningsprotokoll: Om du ansluter till Campaign via Adobe Identity Service (IMS) är en uppgradering obligatorisk för både Campaign-servern och klientkonsolen för att kunna ansluta till Campaign efter **30 juni 2021**. [Läs mer](../../technotes/using/ims-updates.md)
>
> * Den här versionen innehåller en [säkerhetskorrigering](https://helpx.adobe.com/se/security/products/campaign/apsb21-04.html): Uppgraderingen är obligatorisk för att öka din miljösäkerhet.



* Anslutningsprotokollet har uppdaterats för att följa den nya IMS-autentiseringsmekanismen.
* Korrigerade ett säkerhetsproblem för att förstärka skyddet mot problem med SSRF (Server Side Request Forgery). (NEO-27777)

### ![](assets/do-not-localize/red_2.png) Version 19.2.3 – build 9081 {#release-19-2-3-build-9081}

_7 februari 2020_

**Förbättringar**

* Korrigerade ett regressionsproblem på grund av implementeringen av SSL-certifieringen som gjorde att användaranslutningen misslyckades på Windows-servern. (NEO-20629)
* Ett problem som visade ett felaktigt versionstaggnummer i **Om** -menyn.


### ![](assets/do-not-localize/red_2.png) Version 19.2 – build 9080 {#release-19-2-build-9080}

_2 december 2019_

**Nyheter**

<table> 
 <thead> 
  <tr> 
   <th> <strong>California Consumer Privacy Act (CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA är delstaten Kaliforniens nya integritetslagstiftning som harmoniserar och moderniserar dataskyddskraven som träder i kraft den 1 januari 2020. CCPA gäller för Adobe Campaign-kunder som lagrar data för registrerade i Kalifornien.</p>
    <p>Förutom de sekretessfunktioner som redan finns (inklusive samtyckeshantering, datalagringsinställningar och användarroller) kan Adobe Campaign underlätta din beredskap för CCPA:</p>
    <ul>
      <li>Rätt till åtkomst och rätt att ta bort: vi utnyttjar de funktioner som tillkommit för GDPR. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">Läs mer</a></li>
      <li>Ni kan spåra om en konsument har valt att sälja personuppgifter. Därför måste du utöka profiltabellen och lägga till en <strong>Avanmäl dig för CCPA</strong> fält. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">Läs mer</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Övervakning av direktarbetsflöde</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Nu kan du övervaka körningsstatusen för alla arbetsflöden på instansen med fördefinierade vyer.</p>
   <p>Mer information finns i den <a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">detaljerade dokumentationen</a>.</p></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Interaktivt material med AMP</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Med Adobe Campaign kan du testa den nya interaktiva <a href="https://amp.dev/about/email/">AMP för e-post</a> -format, som gör att marknadsförarna kan inkludera AMP-komponenter i meddelanden för att förbättra e-postupplevelsen med avancerat, dynamiskt och interaktivt innehåll som kan användas direkt i själva meddelandet.</p>
   <p>Den här funktionen lanseras som en betaversion.</p>
   <p>Mer information finns i den <a href="../../delivery/using/defining-interactive-content.md">detaljerade dokumentationen</a> och <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">självstudievideon</a>.</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Säkra SMS-meddelanden (TLS)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Skyddat SMS stöds nu via den utökade allmänna SMPP-anslutningen. Detta tillåter en krypterad anslutning till providern.</p> <p><strong>Varning</strong> Den här funktionen kräver ett aktuellt certifikat på alla servrar. Ogiltiga, återkallade eller utgångna certifikat genererar fel som påverkar SMS-sändningsfunktionerna.</p><p>Mer information finns i den <a href="https://helpx.adobe.com/se/campaign/kb/sms-connector-protocol-and-settings.html">detaljerade dokumentationen</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Säkerhetsförbättringar**

* Korrigerade säkerhetsluckor med cross site scripting i Campaign-gränssnittet - validering av indata och utdatakodning. (NEO-16810)
* Ett säkerhetsproblem i profilauktoriseringen som kunde ge åtkomst till obehöriga data har åtgärdats genom att principen för begränsning av inloggning förstärks. (NEO-14445)

**Förbättringar**

* Optimering av minnesförbrukning för push-meddelanden.
* För optimering av prestanda och lagring är hanteringen av **inloggningar.log** filen har förbättrats. Filen delas nu upp i flera filer, en gång om dagen med högst 365 filer bevarade. [Läs mer](../../production/using/log-files.md)
* Det externa Microsoft Dynamics CRM-kontot kan nu konfigureras med hjälp av lösenordsautentiseringsuppgifter (lösenord + användarnamn) eller certifikat (privat nyckel). [Läs mer](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Vissa förbättringar har lagts till i Hadoopets FDA-anslutning för att förbättra tillförlitligheten
* En särskild skyddsmodul har lagts till för att kontrollera diskutrymmet innan offentliga resurser kan överföras till servern.
* Nytt [Kampanjalternativ](../../installation/using/configuring-campaign-options.md) har lagts till:
   * The **WdbcKillSessionPolicy** konfigurationsalternativet gör att du kan påverka **Ovillkorligt stopp** beteende för alla arbetsflöden och PostgreSQL-databasfrågor.
   * The **NmsOperation_DeliveryPreparationWindow** kan du definiera antalet dagar över vilka leveranser med inkonsekvent status ska uteslutas från antalet pågående leveranser.
   * The **WdbcOptions_TempDbName** gör att du kan konfigurera en separat databas för arbetsregister på Microsoft SQL Server. Detta optimerar säkerhetskopiering och replikering. [Läs mer](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * The **XtkCleanup_NoStats** har förbättrats för PostgreSQL för att bättre kunna styra hur lagringsoptimeringssteget i arbetsflödet för databasrensning fungerar. [Läs mer](../../production/using/database-cleanup-workflow.md#statistics-update)
* En mekanism för kontoutelåsning har lagts till i **logon()** API. Det förhindrar ytterligare inloggningsförsök efter ett visst antal misslyckade inloggningsförsök i följd inom en angiven tidsram.
* En ny **Maximal körtid för personalisering** i leveransegenskaperna gör att du kan definiera en timeout-period för personaliseringen, för att förhindra att personaliseringsfasen körs för länge. [Läs mer](../../delivery/using/personalization-fields.md#timing-out-personalization)
* The **ftp-protokoll** har lagts till så att du kan använda en proxykonfiguration för SFTP-anslutningar. [Läs mer](../../installation/using/file-res-management.md)
* Nytt stöd för proxyåtkomst till en extern SFTP-server för lokala miljöer.
* Ett specifikt skyddsutkast har lagts till för att förhindra installation av paket som inte är kompatibla med Campaign-instansen. [Läs mer](../../installation/using/installing-campaign-standard-packages.md)

_Föråldrade system_

Följande system är nu [föråldrad](deprecated-features.md) för Campaign Classic-implementeringar:
* Apache 2.2
* Centrum 6

Kontrollera att du har de versioner av alla system som stöds och som finns i den senaste kampanjkompatibilitetsmatrisen. [Läs mer](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

Version 1.0.26 av iOS SDK är nu tillgänglig. I den här nya versionen har vi lagt till stöd för iOS 13. Den nya versionen har nu stöd för meddelandeprioritet och den nya processen för hantering av registreringstoken för push-meddelanden i iOS 13. Om du kör program på en tidigare version av SDK måste du kompilera om programmen med den nya SDK:n. Kontakta SDK för att få tillgång till [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Korrigeringar**

* Ett kraschproblem när **Lägg till länkad tabell** fältet var tomt i **Inläsning av data (RDBMS)** arbetsflödesaktivitet. (NEO-12213)
* Korrigerade ett problem som kunde leda till att vissa meddelanden inte bearbetades av servern för medelkällkod. (NEO-12395)
* Ett problem i databasrensningsarbetsflödet när frågebandningsalternativet används med Teradata har korrigerats. (NEO-12399)
* Ett problem som påverkade leveransanalysen med typologiregeln inklusive domänen ne.jp har korrigerats. (NEO-12609)
* Korrigerade ett problem relaterat till SMS över TLS-uppdateringar som innebar en mer restriktiv certifikatprincip. Uppdateringarna kan leda till ett anslutningsfel mellan marknadsförings- och mellanleverantörsservrar om certifikatet är inaktuellt. (NEO-17698)
* Ett problem som uppstod när **Testanslutning** på ett externt konto i en miljö med flera källor och vaultautentisering. (NEO-12722)
* Korrigerade ett problem med frågor som använder datumfunktioner med en FDA-Hadoopen anslutning. (NEO-12847)
* Korrigerade ett problem när en bild skulle ersättas i e-postredigeraren. (NEO-13098)
* Korrigerade ett problem som kan leda till fel efter uppgraderingen i mappar som har tagits bort eller flyttats till en annan plats. (NEO-13118)
* Ett problem med bildvisning när **Definiera bild per enhetsskärmstorlek** på LINE-meddelanden. (NEO-13228)
* Korrigerade ett leveransförberedelseproblem när **Exkludera dubblettadress under leverans** alternativet är inte markerat. (NEO-13240)
* Ett problem i arbetsflöden när **Filöverföring** aktivitet för att hämta filer med **Ta bort källfilerna efter överföringen** med ett namn som innehåller ett blanksteg. (NEO-13411)
* Ett problem med rensning av Tomcat-cachen som kan leda till minnesproblem har åtgärdats. (NEO-13456)
* Ett problem har korrigerats vid installation av **Kontroll över erbjudandemotorn med körningsinstans** inbyggt paket för en befintlig kontrollinstans som körs i Microsoft SQL 2017. (NEO-13539)
* Ett kraschproblem som kunde inträffa när spårade URL:er avkontrollerades i ett e-postmeddelande från **Textinnehåll** på grund av en icke-initierad variabel. (NEO-13545)
* Korrigerade ett kodningsproblem för det kinesiska avsändarnamnet. (NEO-13837)
* Korrigerade ett fel som kunde uppstå när undersökningssvarsdata från Utforskaren visades. (NEO-14590)
* Korrigerade ett problem som kunde leda till diskrepans mellan leveransloggklassificeringen och karantäntabellen. (NEO-16547)
* Ett problem med DKIM-nycklar som inte var inbäddade i e-postmeddelanden har korrigerats. (NEO-16804)
* Korrigerade ett problem som visade fel felkod när en ogiltig sessionstoken användes i kontexten för API-anrop för att utlösa händelser. Felkoden var HTTP 200 OK i stället för HTTP 403 Forbidden. (NEO-16826)
* Ett problem som orsakade att leveransrapporter visades via webbåtkomst har korrigerats. (NEO-17015)
* Ett IMS-autentiseringsproblem som uppstod vid inloggning på Adobe Campaign har korrigerats. (NEO-17312)
* Korrigerade ett problem som förhindrade att e-postmeddelanden i karantän togs bort av sekretesshanteringsprocessen. (NEO-17314)
* Problem med genomströmning har korrigerats efter uppgradering till 9031 med SQL-databas. (NEO-17558)
* Ett problem som påverkade CRM Connector med Salesforce har korrigerats. (NEO-17712)
* Ett timeout-problem vid import av data från en extern SFTP har korrigerats. (NEO-19723)
* Ett problem har korrigerats vid åtkomst till prediktiva modeller. (NEO-19713)
* Ett problem som påverkar slumpmässig provtagning i har korrigerats **Dela** arbetsflödesaktivitet med Hadoop FDA-databas. (NEO-16636)
* Korrigerade en regression för Oraclet, vilket gjorde att vissa funktioner ansågs vara ogiltiga efter efteruppgraderingen. (NEO-12759)


## Version 19.1{#release-19-1}

### ![](assets/do-not-localize/limited_2.png) Version 19.1.8 – build 9039 {#release-19-1-8-build-9039}

_15 april 2021_

* Korrigerade en klientkonsolregression som orsakade bestående felmeddelanden på IMS-anslutningsskärmen. (NEO-34821)
* Korrigerade en regression som kunde blockera arbetsflödesdataexporten till en FDA-databas (Teradata, Snowflake).

**Endast konsoluppgraderingen är obligatorisk. Ingen serveruppgradering krävs.**

>[!NOTE]
>
> Anslut till [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) för att hämta den nya versionen. Läs om hur du föreslår en konsoluppdatering för alla slutanvändare [på den här sidan](../../installation/using/client-console-availability-for-windows.md).

_22 mars 2021_

* Korrigerade en regression som förhindrade användning av vissa komponenter i konsolen, som datumväljaren och bildhantering i leveranser. (NEO-31453, NEO-31454)

**Endast konsoluppgraderingen är obligatorisk. Ingen serveruppgradering krävs.**

>[!NOTE]
>
> Anslut till [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) för att hämta den nya versionen. Läs om hur du föreslår en konsoluppdatering för alla slutanvändare [på den här sidan](../../installation/using/client-console-availability-for-windows.md).

_16 december 2020_

>[!CAUTION]
>
> * Den här versionen inkluderar ett nytt anslutningsprotokoll: Om du ansluter till Campaign via Adobe Identity Service (IMS) är en uppgradering obligatorisk för både Campaign-servern och klientkonsolen för att kunna ansluta till Campaign efter **30 juni 2021**. [Läs mer](../../technotes/using/ims-updates.md)
> * Den här versionen innehåller en [säkerhetskorrigering](https://helpx.adobe.com/se/security/products/campaign/apsb21-04.html): Uppgraderingen är obligatorisk för att öka din miljösäkerhet.
> * Om du använder integreringen av Experience Cloud Triggers via oAuth-autentisering måste du gå över till Adobe I/O som beskrivs [på den här sidan](../../integrations/using/configuring-adobe-io.md). Det inaktuella autentiseringsläget oAuth med Campaign [har tagits bort](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) i **september 2021**. Värdmiljöer drar nytta av en förlängning till **23 februari 2022**. Kontakta Adobe kundtjänst för support på plats eller som hybridkund till februari 2022. Du måste ange [AppID:et för OAuth-applikationen](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) till Adobe.



**Förbättringar**

* Anslutningsprotokollet har uppdaterats för att följa den nya IMS-autentiseringsmekanismen.
* Integreringsautentisering med utlösare som ursprungligen baserades på AUTH-autentiseringsinställningar för åtkomst till pipeline har ändrats och flyttats till Adobe I/O. [Läs mer](../../integrations/using/configuring-adobe-io.md)
* Då support för det äldre binära protokollet i iOS APN:er har upphört uppdateras alla instanser som använder det här protokollet till HTTP/2-protokollet under efteruppgraderingen.
* Korrigerade ett säkerhetsproblem för att förstärka skyddet mot problem med SSRF (Server Side Request Forgery). (NEO-27777)
* Ett problem som orsakade inaktivering av SMPP-anslutningen efter ett anslutningsfel har korrigerats, vilket förhindrar att andra SMS-leveranser skickas och leder till prestandaproblem.
* Korrigerade ett problem som visade felaktiga procentvärden när en beskrivande rapport genererades via en arbetsflödesaktivitet. (NEO-14314)
* Korrigerade ett leveransförberedelseproblem när **Exkludera dubblettadress under leverans** alternativet avmarkerades. (NEO-13240)
* Korrigerade ett problem som kunde få arbetsflöden att inte fungera när en **Berikandeaktivitet** kördes. (NEO-17338)
* Korrigerade ett problem i arbetsflöden när poster hämtades från en extern databas och infogades i databasen i Campaign. (NEO-26359)
* Korrigerade ett problem med serverkraschar genom att förhindra minnesfel när uttrycksanalysen rensades.
* Ett problem som förhindrade **NoNull** från att arbeta i Oracle-databaser efter uppgradering till build 9032. (NEO-26488)
* Korrigerade ett problem som uppstod när man redigerade en beskrivning av en kampanjmall som hindrade knappen **Spara** från att visas när symboler såsom japanska tecken kopierades och klistrades in. (NEO-27071)
* Korrigerade ett problem som förhindrade att beskrivningen av en kampanj eller kampanjmall sparades när användaren klickade utanför fönstret innan denne klickade på knappen **Spara**. (NEO-27449)
* Korrigerade ett problem med proxykonfigurationen som förhindrade dig från att logga in på Adobe Campaign efter den senaste Windows 10-uppdateringen. (NEO-27813)
* Korrigerade ett problem relaterat till hanteringen av tomma rader i loggfiler, vilket orsakade fel i MTA-processbeteendet och ledde till prestandaförsämringar vid leveransen.

**Tekniska utvecklingar**

Tomcat har uppdaterats från version 7 (7.0.103) till version 8 (8.5.57). Katalogen `tomcat-7` ersätts med en `tomcat-8`-katalog. I Windows har nu _iis_neolane_setup.vbs_ och _apache_neolane.conf_ installerats i katalogen `conf` (i stället för i `tomcat-7/conf` som tidigare). I Linux finns nu _apache_neolane.conf_ installerat i katalogen `conf`.

I Linux används nu en systemenhet för start av servertjänsten i stället för skriptet /etc/init.d/nlserver6. Migreringen till det nya startschemat utförs automatiskt när du installerar paketet 19.1.8. /etc/init.d/nlserver6 finns fortfarande men för interaktion med nlserver-tjänsten (start, omstart, stopp osv.) rekommenderar vi att du använder systemctl-kommandot direkt.


### ![](assets/do-not-localize/red_2.png) Version 19.1.7 – build 9036 {#release-19-1-7-build-9036}

_15 september 2020_

**Förbättringar**

* Förbättrad användning av nlsrvmod för Apache 2.4-trådar för att korrigera nlsrvmod-krascher.
* Ett problem har korrigerats vid användning av filöverföringsaktiviteten med ett externt Azure-konto och en SSL-kryptering. Anslutningen gjordes via HTTP i stället för HTTPS. (NEO-26720)
* Ett problem med url-cachemekanismen som inte hämtade etiketten eller kategorin har korrigerats.
* Korrigerade ett problem som ledde till att spegelsidans URL:er definierades på ett felaktigt sätt i e-postleveranser (på grund av felaktig ASCII-teckenkontroll). (NEO-26084)
* Listan jarsToSkip i catalina.properties har uppdaterats för att ta bort referensen till en jar-fil som inte längre används (iOS-meddelanden).
* Korrigerade ett regressionsproblem som förhindrade efter publicering efter efteruppgradering.
* Korrigerade en regression med färdiga leveransrapporter som verkade trunkerade när de exporterades till PDF. (NEO-25757)
* Korrigerade ett problem som raderade kodning av parametervärde vid omdirigering från en spårnings-URL (inverkan på japanska tecken). (NEO-25637)
* Korrigerade ett problem som medförde att osignerade länkar från anpassade domäner blockerades när de borde tillåtas. (NEO-25210)
* Korrigerade en regression som påverkade beräknade fält i ett arbetsflöde och orsakade att arbetsflödet slutade fungera. (NEO-25194)
* Korrigerade ett kompatibilitetsproblem med Microsoft Dynamics (från version 8.2) som kunde förhindra att vissa API-anrop kördes (RetrieveAllEntities). (NEO-24528)
* Korrigerade ett regressionsproblem vid användning av ACS Connector-funktionen som förhindrade anslutningen till en instans i Campaign Standard (felaktig hantering av FOH/FOH2-anslutningen). (NEO-23433)
* Korrigerade ett regressionsproblem i databasanslutningen som orsakade att webbservern hela tiden startades om på grund av ett problem med databaskodningen. Detta kan leda till överkonsumtion. (NEO-23264)
* Korrigerade ett problem med arbetsflödet för databasrensning som kunde sluta fungera på grund av en ohanterad datakälla. (NEO-23160 och NEO-23364)
* Arbetsflödet för rensning tömmer nu utgångna listor med grupper om 100 i stället för en i taget.
* Efter bytet till mekanismen för nytt sekvens-ID publiceras alla webbapplikationer som uppdaterar mottagartabellen på nytt, under efteruppgraderingen.
* Ett problem som förhindrade att e-post skickades när det fanns Javascript-kod utanför innehållstaggen för HTML har åtgärdats. (NEO-18628)
* Ett problem som förhindrade att spårningsindikatorerna för transaktionsmeddelanden uppdaterades i arbetsflödet för spårning har åtgärdats. (NEO-17770)
* Förbättrade prestanda för guiden Databasuppdatering för att göra färre SQL-satser för att optimera svarstiden.
* Ett kraschproblem som kunde inträffa när spårade URL:er avkontrollerades i ett e-postmeddelande från **Textinnehåll** på grund av en icke-initierad variabel. (NEO-13545)
* Korrigerade ett problem som förhindrade dig från att överföra filer i en filöverföringsaktivitet med ett externt Azure Blob Storage-konto på grund av en oinitierad variabel (m_pCurlReader). (NEO-13717)
* Korrigerade ett problem med en efteruppgradering som stängde av Apache och webbservern innan webbapplikationens publicering. (NEO-27155)
* Korrigerade en regression som ledde till att en felaktig tidszon plockades när tiden angavs i en **Schemaläggare** arbetsflödesaktivitet.


### ![](assets/do-not-localize/red_2.png) Version 19.1.6 – build 9035 {#release-19-1-6-build-9035}

>[!CAUTION]
>
>Den här versionen är endast avsedd för lokala installationer. För hybriddistributioner fortsätter värdbaserade instanser att köra 9032-versionen. Uppgradera inte din marknadsinstans till 9035-versionen eftersom den inte är kompatibel med 9032.

_3 oktober 2019_

**Förbättringar**

* Korrigerade ett problem när CRM-kopplingen för Salesforce användes. (NEO-17712)
* Korrigerade ett problem med index som kunde orsaka prestandaproblem när transaktionsmeddelanden skickades.
* Korrigerade ett prestandaproblem när meddelanden skickades. (NEO-17558)
* Korrigerade ett problem som kunde leda till att vissa meddelanden inte bearbetades av servern för medelkällkod. (NEO-12395)
* Ett problem som förhindrade att SQL Data Management-aktiviteten användes fullt ut har åtgärdats (namngiven SQL Data Management-behörighet saknas).

### ![](assets/do-not-localize/red_2.png) Version 19.1.5 – build 9033{#release-19-1-5-build-9033}

_13 augusti 2019_

**Förbättringar**

* Korrigerade ett problem med SQL-satsen SELECT COUNT som kördes på standarddatabasen i stället för FDA-databasen under dataextraheringen i datahanteringsaktiviteten.
* För att förbättra kundens infrastruktur finns nu en SFTP-proxydeklaration tillgänglig i serverkonfigurationsfilen.
* Ett kraschproblem när **Lägg till länkad tabell** fältet var tomt i **Inläsning av data (RDBMS)** arbetsflödesaktivitet. (NEO-12213)
* Ett problem med installationen av paketet midEmitter via kommandoraden har korrigerats.
* Ett nytt autentiseringsalternativ har lagts till som stöd för OAuth-autentiseringsuppgifter i AC-anslutningen med Microsoft Dynamics. (NEO-11982)
* Korrigerade ett problem med UUID-hantering (Unik universell identifierare) som gjorde att arbetsflödesaktiviteterna för fråga och data misslyckades med Hive FDA.
* Korrigerade en regression för Oraclet, vilket gjorde att vissa funktioner ansågs vara ogiltiga efter efteruppgraderingen. (NEO-12759)
* Korrigerade en regression som ledde till att en felaktig tidszon plockades när tiden angavs i en arbetsflödesaktivitet i schemaläggaren.

### ![](assets/do-not-localize/green_2.png) version 19.1.4 – build 9032{#release-19-1-4-build-9032}


>[!NOTE]
>
>19.1.4 [!DNL Gold Standard] finns listade i den här [page](../../rn/using/gold-standard.md).


### ![](assets/do-not-localize/red_2.png) Version 19.1.2 – build 9029{#release-19-1-2-build-9029}

_21 juni 2019_

**Säkerhetsförbättringar**

* För att optimera säkerheten har Java-biblioteket (Netty) uppdaterats till den senaste versionen (4.1.34). (NEO-12788)

**Förbättringar**

* Korrigerade en regression som är länkad till hantering av domänkolumner, vilket förhindrade att e-postmeddelanden skickades på vissa konfigurationer.
* För att förbättra prestanda har ett _operation=&quot;none&quot;-attribut lagts till i rtEvent SOAP-anrop för att undvika SELECT FOR UPDATE-begäranden.
* Korrigerade ett arbetsflödesvisningsproblem med utgående övergångar efter aktiviteten Testa. (NEO-12727)
* Nu kan vi ta bort dummy-poster som skapats i Microsoft Dynamics under importarbetsflödet.
* Förbättrade behörigheter för att köra säkerhetszonspaketet när ett internt konto används.


### ![](assets/do-not-localize/red_2.png) Version 19.1 – build 9026{#release-19-1-build-9026}

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
   <td> <p>Om du vill öka effektiviteten i ditt arbete som Admin-användare hanterar du inställningarna för dina SFTP-servrar genom att övervaka lagringsutrymmet, lägga till IP-adresser i tillåtelselista och installera SSH-nycklar för varje instans. Kontrollpanelen är endast tillgänglig för kunder som har AWS som värd idag (<a href="https://experiencecloud.adobe.com/campaign/controlpanel/">logga in via Experience Cloud idag</a>).</p> <p>Mer information hittar du i den <a href="https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=sv">detaljerade dokumentationen</a> och <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/control-panel-overview.html?lang=sv">instruktionsvideon</a>. </p><p>Obs! Du behöver inte uppgradera till den senaste Campaign-versionen för att komma åt Kontrollpanelen.</p> </td> 
  </tr> 
    <tr> 
   <td> Granskningskedja<br /> </td> 
   <td> <p>Som administratör kan du öka produktiviteten genom att övervaka och hantera ändringar som görs i Adobe Campaign Classic-instansen. Granskningsspårningen loggar åtgärder som har gjorts i källscheman, arbetsflöden och alternativ. Du kan snabbt se om ett element har skapats, ändrats eller tagits bort.</p><p>Mer information finns i <a href="../../production/using/audit-trail.md">detaljerad dokumentation</a> och <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/monitoring/audit-trail.html">instruktionsvideo</a>.</p></td> 
  </tr> 
  <tr> 
   <td> Guardrail, robuskhet och skalbarhet<br /> </td> 
   <td> En rad förbättringar har lagts till i Campaign Classic. Förbättringar av säkerhet, stabilitet och skalbarhet visas nedan.<br /> </td> 
  </tr> 
  <tr> 
   <td> Uppdatering av kompatibilitetsmatris<br /> </td> 
   <td> Med den nya versionen har Adobe Campaign nu stöd för följande databassystem. Se <a href="https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html">Kompatibilitetsmatris</a>.<br /> 
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

* Av säkerhetsskäl kan du inte längre infoga godtyckliga kommandon när du använder **[!UICONTROL Pre-process the file]** i en **[!UICONTROL Data loading (file)]** arbetsflödesaktivitet. Nu finns en nedrullningsbar lista där du kan välja mellan tre alternativ: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) eller **[!UICONTROL Decrypt]** (gpg). XtkSecurity_Disable_Preproc-säkerhetsflaggan har lagts till. För nya kunder anges värdet 0. För befintliga kunder kommer detta alternativ att anges till 1 vid uppgraderingen för att behålla det tidigare beteendet. Se detta [section](../../workflow/using/data-loading--file-.md).
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

* Lifespan - XtkNewId-sekvensoptimering: de mest använda tabellerna har flyttats från xtkNewId-sekvensen till dedikerade sekvenser.
* FDA över HTTP v2: FDA över HTTP-protokollet används ofta vid hybriddriftsättningar, särskilt vid hämtning av breda loggar och leveransförberedelser. Robusiteten har förbättrats för att undvika nätverksproblem och eventuella fel som hämtning eller överföring av data. Detta kräver att byggen i båda ändar av anslutningen är uppdaterade, annars kommer det gamla protokollet fortfarande att användas.
* Arbetsflöde för spårning: spårningsarbetsflödets tillförlitlighet har förbättrats. Flera problem med att spåra logginfogningar/uppdateringar och anpassning av URL-spårning har åtgärdats. Dessutom upptäcker arbetsflödet nu loggproblem som kan leda till fel och stoppa arbetsflödet. Dessa problem har nu ignorerats och bearbetats inte.
* Rensningsarbetsflöde: rensningsarbetsflödet har förbättrats för att undvika potentiella fel och stopp. Detta optimerar databasens storlek och prestanda.
* Inbäddade bilder i transaktionsmeddelanden: vi har lagt till fullständigt stöd för inbäddade bilder i transaktionsmeddelanden för att undvika eventuella krascher eller saknade bilder.
* Databasstorlek - XtkJobLog: en tömningsmekanism har lagts till i tabellen. Detta påverkar databasstorleken positivt.
* BCC-arkivering: standardparametrarna för BCC-arkivering har ändrats för att öka arkiveringshastigheten. [Läs mer](../../installation/using/email-archiving.md#parameters)
* Databasstrukturuppdatering: SQL-begäranden som genereras av guiden Uppdatera databasstruktur har förbättrats för snabbare körning.
* Garantier för operatoråtgärder: flera skyddsräcken har implementerats för att hindra operatorer från att utföra åtgärder som kan påverka plattformens integritet. Inbyggda scheman kan inte längre tas bort via gränssnittet. Arbetsflödets källa-XML kan inte längre redigeras av icke-adminanvändare.
* Två nya alternativ har gjorts tillgängliga: **XtkSecurity_Restrict_EditXML** (gör att du kan inaktivera utgåvan av leverantörens XML-kod) och **NmsOperation_OperationMgtDebug** (gör att du kan övervaka det tekniska arbetsflödet operationMgt). [Läs mer](../../installation/using/configuring-campaign-options.md)

**Andra ändringar**

* Push-meddelanden: vi har nu stöd för alternativet Tråd-ID för iOS push.
* Förbättrad hantering av index för långa namn, vilket kan orsaka problem efter uppgraderingen.
* Om publiceringsläget är inställt på **[!UICONTROL None]** i distributionsguiden loggas ett fel och analysen stoppas: &quot;Publiceringsläget är inställt på &#39;none&#39;: Det går inte att bädda in bilden. Bilderna visas inte på telefonen.&quot; (NEO-12208)
* Sändningshanteringen har förbättrats för transaktionsmeddelanden. När utsändningsloggar synkroniseras från körningsinstansen till kontrollinstansen uppdateras fältet @lastModified till systemets aktuella datum. Alternativet MC_Update_BlLastModified har lagts till för kontrollinstanser. True betyder att det aktuella datumet kommer att användas för kontrollinstansen (standardbeteende). Falskt innebär att vi använder körningsinstansens utsändningsdatum @lastModified. (NEO-12579)
* Index lades till i kupongtemporära tabeller för att optimera leveransen. (NEO-12437)
* I Analytics-integreringen är det nu tillåtet att hämta AAM segmentdata med tecknet %. (NEO-12025)
* 10 000 poster har tagits bort i heatmap-kartan för arbetsflöde för att åtgärda ett problem med saknade data. (NEO-12329)
* Open Office stöds inte och har nu tagits bort helt från programmet. Om du fortfarande använde den kan du gå över till Library Office eftersom det inte längre fungerar från och med 19.1.
* Nu kan du begränsa skrivåtkomst till Uppdatera dataaktivitet i arbetsflöde med hjälp av sysfilter-attribut. [Läs mer](../../configuration/using/filtering-schemas.md)

**Korrigeringar**

* Ett problem som gjorde att certifikatet inte kunde överföras för iOS mobila push-meddelanden har korrigerats.
* Potentiella återkommande serverkrascher för transaktionspush-meddelanden har korrigerats. Andra kraschproblem har åtgärdats.
* Ett problem som orsakade rapporteringsavvikelser mellan användaraktiviteter och spårningsrapporter för indikatorn för öppen leverans har korrigerats. (NEO-11742)
* Ett problem med IMS-inloggningen har korrigerats.
* Korrigerade ett problem som kan leda till att bilder saknas i en leverans när en bild läggs till från biblioteket. (NEO-11900)
* Korrigerade ett problem som kunde inträffa vid extrahering av erbjudandeinformation i en direktpostleverans. (NEO-11700)
* Ett problem som kunde påverka SMS-transaktionsmeddelandets prestanda har åtgärdats. (NEO-9812)
* Korrigerade en konsolkrasch som kunde inträffa när alternativet Definierad i en extern fil användes för huvudmålet för en leverans. (NEO-12349)
* Korrigerade ett fel vid analys av ett meddelande som riktade till mottagare för japanska (.JP)-domäner. (NEO-12246)
* Korrigerade ett visningsproblem vid användning av en värdefördelning med en 1:N-länk. (NEO-12212, NEO-11820)
* Korrigerade ett problem som kunde orsaka NmsMxDomain-fel i MTA-loggarna efter en efteruppgradering. (NEO-12752)
* Ett problem har korrigerats när alternativet Behåll alla ytterligare data från huvuduppsättningen användes i en arbetsflödesaktivitet för anrikning. (NEO-13291)
* Korrigerade ett Tomcat-kraschproblem när push-meddelanden skickades med HTTP2. (NEO-12701)
* Korrigerade ett problem med HTTPRequest-API som inte väntade på att alla återanrop skulle slutföras. (NEO-12628)
* Korrigerade ett problem med datorprocessen med spårningsindikatorer för transaktionsmeddelanden. (NEO-12529)
* Ett problem med användningen av teman i erbjudandehanteringen har korrigerats. (NEO-11804)
* Korrigerade ett prestandaproblem när push-meddelanden skickades. (NEO-11787)
* Ett problem har korrigerats vid förhandsgranskning av utgående XML- eller CSV-fil i offerthantering för direktreklam. (NEO-11290)
* Ett problem har korrigerats vid installation av **Hantera sociala nätverk** (Social Marketing). (NEO-12081)
* Korrigerade ett problem som hindrade dig från att ta bort ett webbprogram även om du hade rätt åtkomstbehörighet. (NEO-12072)
* Korrigerade ett problem som kunde göra att vissa värden skrevs över vid export och sedan import av ett objekt via XML. Alternativet XtkExport_IncludeDefaultValues har lagts till. Om du anger True (standardbeteende) exporteras alla värden. Om värdet är Falskt skrivs ändringarna över med standardvärdet. (NEO-11979)
* Ett problem som orsakade **[!UICONTROL Alert]** arbetsflödesaktivitet som ska misslyckas när en anrikningsaktivitet läggs till efter en fråga. (NEO-12132)
* Korrigerade ett fel i Oraclena där förskjutningar för pipeline (utlösare) inte hämtades från databasen och orsakade dubbletter. (NEO-12121)
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
* Ett problem som kunde orsaka fel i datorloggarna har korrigerats. (NEO-11539, NEO-8978)
* Ett problem som uppstod när du klickade på ikonen Historik i en sparad rapport korrigerades. (NEO-11620)
* Ett problem har korrigerats vid redigering av en pivottabell i en rapport. (NEO-12068)
