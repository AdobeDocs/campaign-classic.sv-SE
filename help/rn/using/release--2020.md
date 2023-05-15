---
product: campaign
title: 2020-versioner
description: Läs mer om Campaign Classic 2020-versioner
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Overview
role: User
level: Beginner
hidefromtoc: true
exl-id: e2eb7e04-faaa-4df0-913d-471c291eeb03
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '6601'
ht-degree: 73%

---

# 2020-versioner{#release-2020}




## Version 20.3{#release-20-3}

### ![](assets/do-not-localize/red_2.png) Version 20.3.3 – build 9234 {#release-20-3-3-build-9234}

_11 januari 2021_

* Korrigerade ett säkerhetsproblem för att förstärka skyddet mot problem med SSRF (Server Side Request Forgery). (NEO-27777)
* Korrigerade ett regressionsproblem relaterat till genereringsprocessen av leveransloggar som kunde få MTA-processen att krascha.

### ![](assets/do-not-localize/red_2.png) Version 20.3.1 – build 9228 {#release-20-3-1-build-9228}

_27 oktober 2020_

>[!CAUTION]
>
> * Den här versionen inkluderar ett nytt anslutningsprotokoll: Om du ansluter till Campaign via Adobe Identity Service (IMS) är en uppgradering obligatorisk för både Campaign-servern och klientkonsolen för att kunna ansluta till Campaign efter **30 juni 2021**. [Läs mer](../../technotes/using/ims-updates.md)
> * Den här versionen innehåller en [säkerhetskorrigering](https://helpx.adobe.com/se/security/products/campaign/apsb21-04.html): Uppgraderingen är obligatorisk för att öka din miljösäkerhet.
> * Om du använder integreringen av Experience Cloud Triggers via oAuth-autentisering måste du gå över till Adobe I/O som beskrivs [på den här sidan](../../integrations/using/configuring-adobe-io.md). Det inaktuella autentiseringsläget oAuth med Campaign [har tagits bort](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) i **september 2021**. Värdmiljöer drar nytta av en förlängning till **23 februari 2022**. Kontakta Adobe kundtjänst för support på plats eller som hybridkund till februari 2022. Du måste ange [AppID:et för OAuth-applikationen](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) till Adobe.


**Nyheter**

<table> 
<thead>
<tr> 
<th> <strong>Förbättringar på push-meddelanden i iOS</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>När du integrerar mobilappen i Campaign måste du säkra kommunikationen med Apple Push Notification service (APN:er). Du kan använda certifikatbaserad eller tokenbaserad autentisering.
</p>
<p>Dessa två autentiseringsmetoder finns nu tillgängliga för iOS-mobilappar i Campaign Classic:
</p>
<ul> 
<li><p>Tokenbaserad autentisering (rekommenderas): den här autentiseringsmetoden baseras på en .p8-fil. Den här autentiseringsmetoden är snabbare eftersom varje begäran till APN:er innehåller rätt token. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">Läs mer</a></p></li>
<li><p>Certifikatbaserad autentisering: den här autentiseringsmetoden baseras på en .p12-fil. För varje app krävs ett separat certifikat. Det här certifikatet levereras av Apple via ditt utvecklarkonto. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">Läs mer</a></p></li> 
</ul>
<p>Läs om hur du väljer autentiseringsmetod i Campaign i den <a href="../../delivery/using/configuring-the-mobile-application.md">detaljerade dokumentationen</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Förbättringar på push-meddelanden i Android</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p><a href="../../delivery/using/configuring-the-mobile-application-android.md#creating-notification-message">Push-meddelanden i Android har förbättrats med stöd för FCM HTTP v1 API för push-kanalautentisering i Android.</a> </p>
<p>Med den nya API-versionen som stöds kan du nu skicka FCM-meddelanden som erbjuder förbättrade funktioner för push-meddelanden. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">Läs mer</a></p> 
<p>Läs <a href="../../delivery/using/configuring-the-mobile-application-android.md">det här avsnittet</a> om hur du konfigurerar FCM HTTP v1 API för Android i Adobe Campaign.</p>
</td> 
</tr> 
</tbody> 
</table>

**Säkerhetsförbättringar**

* Säker inläsning av bibliotek: för att skydda dig mot DLL preloading-angrepp läser Campaign nu endast in Windows DLL-filer från Windows standardiserade DLL-sökväg när Campaign Client (nlclient) läses in. [Läs mer](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
* Korrigerade ett säkerhetsproblem för att förstärka skyddet mot SSRF-angrepp (Server Side Request Forgery). (NEO-25661)
* Korrigerade ett problem som uppstod vid hantering av GDPR-förfrågningar om användarens information som förhindrade att poster togs bort från anpassade tabeller med en relation på andra nivån till mottagartabellen. (NEO-25967)
* Korrigerade ett säkerhetsproblem med API-anrop från icke-adminanvändare när de försökte synkronisera mallar i Adobe Experience Manager. (NEO-23487)

**Kompatibilitetsuppdateringar**

Campaign har nu stöd för följande system:
* iOS 14
* PostgreSQL 12
* CentOS/RedHat 8
* MSSQL2019

Läs mer i [kompatibilitetsmatrisen för Campaign](../../rn/using/compatibility-matrix.md).

**Inaktuella funktioner**

Följande funktioner är nu inaktuella i 20.3:

* Demdex-domänen som användes för att importera och exportera målgrupper till Adobe Experience Cloud är inaktuell. Om du använder demdex-domänen för dina externa import-/exportkonton måste du anpassa implementeringen därefter. [Läs mer](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* Integreringsautentisering för utlösare som ursprungligen baserades på oAUTH-autentiseringsinställningar för åtkomst till pipelines har nu ändrats och flyttats till Adobe I/O. [Läs mer](../../integrations/using/configuring-adobe-io.md)

Läs mer på sidan [Funktioner som är inaktuella eller har tagits bort](../../rn/using/deprecated-features.md).

**Förbättringar**

* Flera förbättringar har gjorts i **klientkonsolen**:
   * Anslutningsprotokollet har uppdaterats för att följa den nya IMS-autentiseringsmekanismen. Uppgradering av server- och klientkonsol är obligatoriskt för anslutning efter 30 juni 2021.
   * För att förhindra inkompatibilitet med vissa begränsningar i grupprincipobjekt (GPO) för internetsäkerhet har inloggningsskärmen på klientkonsolen i Campaign ersatts av ett inbyggt standardformulär för Windows.
   * Korrigerade ett problem vid kopiera/klistra in aktiviteter i ett arbetsflöde med 64 bitars klientkonsol. (NEO-27635)
   * På menyn **Om** har information lagts till för att skilja på 64 bitars och 32 bitars konsoler.
* Arbetsflödesidentifieraren visas nu i loggarna när du återupptar ett arbetsflöde vilket gör det lättare att identifiera vilket arbetsflöde som återupptogs.
* En ny permanent cookie har införts: nllastdelid. Denna cookie (inte samma som UUID230) lagrar deliveryId. När sessionscookien saknas hämtas utsändningsinformation från det deliveryId som finns i denna cookie.
Den här ändringen korrigerar ett problem som uppstod när webbläsarsessionen var över: sessionscookien som innehåller deliveryId och broadlogId togs bort. Utan deliveryId gick det inte att hitta utsändningsinformation och informationen i spårningstabellen saknades om det fanns en permanent spårning (senaste leverans).
Läs mer om cookies i [det här avsnittet](../../platform/using/privacy-and-recommendations.md#cookies).
* Förbättrad prestanda för leverans av stora volymer med en leveransbarhetsserver genom att starta om MTA-processen innan leveransen skickas.

**Andra ändringar**

* När du använder en relativ sökväg för SFTP läggs inte längre `~/`-tecken till automatiskt. Vid behov kan du manuellt lägga till `~/`-tecken i sökvägen men Adobe rekommenderar att du använder en **absolut sökväg**.
* Windows NT-autentisering har tagits bort från de tillgängliga autentiseringsmetoderna när en ny databas konfigureras med en Microsoft SQL-server. [Läs mer](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* Arbetsflödet för databasrensning har optimerats för Teradata för att förbättra prestandan. (NEO-19959)
* Förbättrade felmeddelandet som visades när en bild infogades från Adobe Target och klientnamnet var tomt i det externa kontot.
* I leveransegenskaper har alternativet **[!UICONTROL Archive emails]** bytt namn till **[!UICONTROL Email BCC]**.
* selectAll-frågor med ogiltiga noder avvisas nu för att förbättra tillförlitligheten. Om du behöver inaktivera kontrollen och återgå till det tidigare beteendet kan du ställa in XtkSecurity_Disable_QueryCheck på 0.
* Det negativa ID-intervallstödet har lagts till för nmsBroadlogId-sekvensen. Den här versionen justerar min_value för nmsBroadlogId-sekvensen så att det negativa intervallet inkluderas. Om du har ett strikt användningsfall som inte tillåter negativa ID:n, ska du återställa sekvensens min_value till 1.

**Tekniska utvecklingar**

Tomcat har uppdaterats från version 7 (7.0.103) till version 8 (8.5.57).

Katalogen `tomcat-7` ersätts med en `tomcat-8`-katalog.

I Windows har nu _iis_neolane_setup.vbs_ och _apache_neolane.conf_ installerats i katalogen `conf` (i stället för i `tomcat-7/conf` som tidigare).

I Linux finns nu _apache_neolane.conf_ installerat i katalogen `conf`.

**Felkorrigeringar**

* Korrigerade ett problem som kunde förhindra att leveransstatistik beräknades om.
* Korrigerade ett problem som visade ett felmeddelande när en CSV-fil laddades upp med Campaign Classic build 9080 som var ansluten till en server med en äldre build. (NEO-23218)
* Korrigerade ett problem som kunde visa ett felmeddelande när Microsoft Dynamics CRM-guiden konfigurerades för ett externt konto. Detta berodde på ett kompatibilitetsproblem med den senaste API-versionen i MS Dynamics CRM. (NEO-24528)
* Korrigerade ett problem som förhindrade dig från att exportera poster av typen look up (dvs. data som består av poster med främmande nycklar kopplade till andra tabeller) från Campaign Classic till Microsoft Dynamics med CRM-kopplingen. (NEO-23864)
* Korrigerade ett problem som kunde förhindra att Microsoft Dynamics-data hämtades om alternativet **Automatiskt index** var aktiverat i CRM-kopplingen. (NEO-25981)
* Korrigerade ett problem med IMS-autentisering som kunde lämna anslutningar öppna även om de avslutades. Avslutade anslutningar stängs nu automatiskt så fort de avslutas för att undvika att anslutningar ackumuleras och systemresurser används. (NEO-25996)
* Korrigerade ett problem som inte visade något felmeddelande när synkroniseringen av innehåll i Adobe Experience Manager misslyckades med en leverans på grund av en felkonfiguration av det externa kontot (felaktigt konto eller lösenord). Ett meddelande visas nu i händelse av fel vilket gör det lättare att identifiera problemet. (NEO-25586)
* Korrigerade ett problem som uppstod när åtgärdstypen **Uppdatera** valdes i aktiviteten **Uppdatera data**. Om de data som skulle uppdateras var felaktiga blev arbetsflödet fel och misslyckades. Om data är felaktiga misslyckas inte arbetsflödet och posterna lagras i en utgående övergång för **Avvisningar**. (NEO-23794)
* Korrigerade ett problem som kunde förhindra arbetsflöden med delarbetsflöden från att fungera. (NEO-24036)
* Korrigerade ett problem som uppstod när man redigerade en beskrivning av en kampanjmall som hindrade knappen **Spara** från att visas när symboler såsom japanska tecken kopierades och klistrades in. (NEO-27071)
* Korrigerade ett problem som kunde förhindra dig från att ändra spårningsservern i guiden instanskonfiguration.
* Korrigerade ett problem som förhindrade att beskrivningen av en kampanj eller kampanjmall sparades när användaren klickade utanför fönstret innan denne klickade på knappen **Spara**. (NEO-27449)
* Korrigerade ett problem som kunde förhindra det tekniska arbetsflödet **Antal aktiva faktureringsprofiler** (billingActiveContactCount) från att fungera. Detta kunde inträffa om en länk hade utförts på ett beräknat fält i ett schematillägg. Stora mängder data skapades vilket kunde leda till att databasen fick slut på temporärt utrymme. (NEO-24062)
* Korrigerande ett problem med aktiviteten **inläsning av data (fil)** vilket kunde hindra dig från att importera japanska tecken från .txt- och .csv-filer om de var placerade i slutet av filen. (NEO-24957)
* Korrigerande ett problem med kontinuerliga leveranser som kunde förhindra att fälten **Analys startad** och **Analys slutförd** fylldes i korrekt. (NEO-20755)
* Korrigerade ett problem som kunde visa ett felmeddelande när SMS-meddelanden skulle förhandsgranskas efter en fråga i ett annat schema än **mottagaren** (nms:recipient). (NEO-27517)
* Korrigerade ett problem vid användning av Snowflake FDA-kopplingen. En användare med Snowflake FDA-namngivna åtkomsträttigheter kunde inte köra en fråga i ett Snowflake-schema. Ett fel av typen ”Lösenordet hittades inte” visades i loggarna. (NEO-23851)
* Korrigerade ett problem vid användning av en FDA-koppling som inträffade när det länkade FDA-schemanamnet var en delsträng av ett elementnamn i det aktuella schemat. Detta inträffade till exempel om FDA-schemat var ”cust” och ett av elementen i mottagarschemat var ”customer”. När kolumnen i ”customer”-elementet hämtades och en kolumn från FDA-schemat &quot;cust&quot; lades till saknades värdet för den lokala kolumnen. (NEO-20193)
* Korrigerade ett problem i arbetsflöden när poster hämtades från en extern databas och infogades i databasen i Campaign. (NEO-26359)
* Korrigerade ett problem i det tekniska arbetsflödet **Uppdatera händelsestatus**. För att matcha storleken på inkommande motsvarande fält i aktiviteten **Leveransstatistik** ändrades storleken på tre målfält i aktiviteten **Uppdatera leveransstatus** från 32 till 64 bitar. (NEO-11557) Läs mer om arbetsflödet **Uppdatera händelsestatus** i [det här avsnittet](../../workflow/using/about-technical-workflows.md).
* Korrigerade ett problem i rapporten **Meddelandecentrets händelsehistorik** som orsakade skriptfel när filter tillämpades och gjorde det omöjligt att filtrera per ett datumintervall. (NEO-23365)
* Korrigerade ett störningsproblem mellan de tekniska arbetsflödena **Kampanjjobb** (operationMgt) och **Förhandsgranskning** (forecasting). Detta inträffade när schemalagda leveranser förblev i statusen ”Klar för mål” eller ”Klar för leverans”. (NEO-20819)
* Korrigerade ett XML-tolkningsproblem när XML-identifieraren inte fanns i mdata-fältet i xtkOperator. Detta orsakade fel efter uppgraderingen. (NEO-26113)
* Korrigerade ett problem vid användning av aktiviteten **filöverföring** som var länkad till ett externt Azure-konto och som hade krypterats i SSL där anslutningen gjordes med HTTP i stället för med HTTPS. (NEO-26720)
* Korrigerade ett problem för MSSQL-databasen där ett fel kunde uppstå med proceduren up_updatestats under rensningsarbetsflödet.
* Korrigerade en krasch som inträffade när webbprocessen stängdes av om interaktionsbegäranden fortfarande bearbetades. (NEO-26447)
* Korrigerade ett problem där funktionen **NoNull** i Oracle DB inte längre fungerade efter uppgradering 9032. (NEO-26488)
* Korrigerade ett problem där spårningsarbetsflödet misslyckades efter uppgradering 9171 om LINEV2-paketet installerades utan Message Center-paketet.
* Korrigerade ett skalbarhetsproblem som förhindrade att anslutningspoolen utökades till det önskade antalet anslutningar eftersom databasens anslutningssträng för attributet ”APP” fick ett ogiltigt värde. (NEO-25105)
* Korrigerade ett problem med proxykonfigurationen som förhindrade dig från att logga in på Adobe Campaign efter den senaste Windows 10-uppdateringen. (NEO-27813)
* Korrigerade ett problem som gjorde oönskade URL:er synliga i de levererade e-postmeddelandena efter import av HTML-mallar med spårningslänkar. (NEO-25909)
* Korrigerade ett problem som gjorde att servern kraschade när måldata visades som tillhörde resterna från en **delad** aktivitet i ett arbetsflöde.
* Korrigerade ett problem med serverkraschar genom att förhindra minnesfel när uttrycksanalysen rensades. (NEO-26856)
* Korrigerade ett problem i anrikningsaktiviteten där icke-adminanvändare definierade instansvariabler. (NEO-25653)
* Korrigerade en regression som kunde blockera arbetsflödesdataexporten till en FDA-databas (Teradata, Snowflake).

## Version 20.2{#release-20-2}

### ![](assets/do-not-localize/limited_2.png) Version 20.2.5 – build 9188 {#release-20-2-5-build-9188}

_15 april 2021_

* Korrigerade en klientkonsolregression som orsakade bestående felmeddelanden på IMS-anslutningsskärmen. (NEO-34821)

**Endast konsoluppgraderingen är obligatorisk. Ingen serveruppgradering krävs.**

>[!NOTE]
>
> Anslut till [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) för att hämta den nya versionen. Läs om hur du föreslår en konsoluppdatering för alla slutanvändare [på den här sidan](../../installation/using/client-console-availability-for-windows.md).

_31 mars 2021_

**Förbättringar**

* En förbättring har gjorts för att förhindra krascher vid ogiltiga tvålanrop. Detta kan få instansen att sluta fungera när du försöker köra specifika komplexa frågor. (NEO-28796, NEO-30553)
* Korrigerade en regression som förhindrade att SMS-leveranser med TLS skickades på grund av värdnamnsverifieringen. (NEO-29581)
* Korrigerade ett problem som förhindrade signerad spårning av länkar från att arbeta med vissa e-postklienter. (NEO-28414, NEO-29615)
* Korrigerade en spårnings-ID-sekvens när spårningstaggar för webApp användes, vilket kan orsaka konflikter med duplicerade ID:n. (NEO-27931)
* Ett problem som gjorde att pågående arbetsflöden stoppades av den dagliga omstarten av wfserver har åtgärdats. (NEO-30047)
* Korrigerade ett säkerhetsproblem med API-anrop från icke-adminanvändare när de försökte synkronisera mallar i Adobe Experience Manager. (NEO-32389, NEO-23487)
* Ett problem som gjorde att konsolen kraschade när en leveransdialogruta stängdes för en leverans som skapats med från en mall har åtgärdats. (NEO-31547)
* Ett problem som uppstod när en leverans skapades och sparades i **Målgruppsanpassning och arbetsflöde** fliken för en kampanj: förhandsgranskningen misslyckas med följande fel. (NEO-29440)
* Korrigerade ett problem med att Tomcat 8.5 skickade ogiltiga svar som orsakade fel i transaktionsmeddelandeloggar. (NEO-30858)
* Ett regressionsproblem som orsakade minnesfel i extern trådhantering och påverkade prestanda har åtgärdats.
* Korrigerade ett problem som kunde göra att faktureringsarbetsflödet misslyckades när en anpassad målmappning användes. Primärnyckeln för det anpassade schemat lagras i kolumnen&quot;sourceId&quot; som bara tillåter heltalsvärden. Det tillåter nu både heltal och strängvärden. (NEO-25914, NEO-28146)
* Korrigerade en regression som förhindrade användning av vissa komponenter i konsolen, som datumväljaren och bildhantering i leveranser. (NEO-31453)

### ![](assets/do-not-localize/red_2.png) Version 20.2.4 – build 9187 {#release-20-2-4-build-9187}

_15 april 2021_

* Korrigerade en klientkonsolregression som orsakade bestående felmeddelanden på IMS-anslutningsskärmen. (NEO-34821)
* Korrigerade en regression som förhindrade användning av vissa komponenter i konsolen, som datumväljaren och bildhantering i leveranser. (NEO-31453, NEO-31454)

**Endast konsoluppgraderingen är obligatorisk. Ingen serveruppgradering krävs.**

>[!NOTE]
>
> Anslut till [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) för att hämta den nya versionen. Läs om hur du föreslår en konsoluppdatering för alla slutanvändare [på den här sidan](../../installation/using/client-console-availability-for-windows.md).

_22 december 2020_

>[!CAUTION]
>
> * Den här versionen inkluderar ett nytt anslutningsprotokoll: Om du ansluter till Campaign via Adobe Identity Service (IMS) är en uppgradering obligatorisk för både Campaign-servern och klientkonsolen för att kunna ansluta till Campaign efter **30 juni 2021**.  [Läs mer](../../technotes/using/ims-updates.md)
> * Den här versionen innehåller en [säkerhetskorrigering](https://helpx.adobe.com/se/security/products/campaign/apsb21-04.html): Uppgraderingen är obligatorisk för att öka din miljösäkerhet.
> * Om du använder integreringen av Experience Cloud Triggers via oAuth-autentisering måste du gå över till Adobe I/O som beskrivs [på den här sidan](../../integrations/using/configuring-adobe-io.md). Det inaktuella autentiseringsläget oAuth med Campaign [har tagits bort](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) i **september 2021**. Värdmiljöer drar nytta av en förlängning till **23 februari 2022**. Kontakta Adobe kundtjänst för support på plats eller som hybridkund till februari 2022. Du måste ange [AppID:et för OAuth-applikationen](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) till Adobe.


**Förbättringar**

* Anslutningsprotokollet har uppdaterats för att följa den nya IMS-autentiseringsmekanismen.
* Integreringsautentisering med utlösare som ursprungligen baserades på AUTH-autentiseringsinställningar för åtkomst till pipeline har ändrats och flyttats till Adobe I/O. [Läs mer](../../integrations/using/configuring-adobe-io.md)
* Då [support för det äldre binära protokollet i iOS APN:er har upphört](https://developer.apple.com/news/?id=c88acm2b) uppdateras alla instanser som använder det här protokollet till HTTP/2-protokollet under efteruppgraderingen.
* Korrigerade ett säkerhetsproblem för att förstärka skyddet mot problem med SSRF (Server Side Request Forgery). (NEO-27777)
* Ett problem som orsakade inaktivering av SMPP-anslutningen efter ett anslutningsfel har korrigerats, vilket förhindrar att andra SMS-leveranser skickas och leder till prestandaproblem. (NEO-28609)
* Korrigerade ett problem med serverkraschar genom att förhindra minnesfel när uttrycksanalysen rensades. (NEO-26856)
* Korrigerade ett problem som gjorde att servern kraschade när måldata visades som tillhörde resterna från en **delad** aktivitet i ett arbetsflöde.
* Korrigerade ett problem som kunde visa ett felmeddelande när SMS-meddelanden skulle förhandsgranskas efter en fråga i ett annat schema än **mottagaren** (nms:recipient). (NEO-27517)
* Korrigerade ett problem när en HTTPS-anslutningsbegäran med portnumret som uttryckligen definierats i värdnamnet gjordes. Anropet misslyckades med ett certifikatfel. (NEO-29146)
* Korrigerade ett problem i hanteringen av POSIX-trådar som genererade stora kärndumpfiler på marknadsinstansen. (NEO-28117, NEO-29281)
* Korrigerade problem som kan få webbprocessen att krascha vid förberedelse av leveranser eller vid förhandsgranskning av återkommande leveranser. (NEO-27790, NEO-27517)
* Korrigerade ett problem som orsakade att leveranser eller korrektur som skickades misslyckades när de utlöstes av en icke-adminoperator. (NEO-28597)

![](assets/do-not-localize/cp-icon.png) **Ny version av kontrollpanelen i oktober** med domänkonfiguration som använder CNAME och nya funktioner för databasövervakning. [Läs mer](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=sv).

### ![](assets/do-not-localize/red_2.png) Version 20.2.3 – build 9182 {#release-20-2-3-build-9182}

_11 september 2020_

* Korrigerade en regression som gjorde att leveransförberedelser blockerades på grund av en felfunktion på leveransdelen, vilket ledde till överbelastning av minnet. (NEO-27346)
* Korrigerade ett problem med en efteruppgradering som stängde av Apache och webbservern innan webbapplikationens publicering. (NEO-27155)
* Korrigerade en regression i mallhanteringen i HTML som ledde till att URL:er blev synliga på grund av en feltolkning av flikarna. (NEO-25909)
* Korrigerade ett problem med arbetsflödet för databasrensning som kunde sluta fungera på grund av en ohanterad datakälla. (NEO-23160 och NEO-23364)
* Arbetsflödet för rensning tömmer nu utgångna listor med grupper om 100 i stället för en i taget.
* Korrigerade en regression som förhindrade dig från att ändra det interna namnet på ett externt konto. (NEO-27323)
* Korrigerade en regression under efteruppgraderingen som orsakade en felaktig start av lserver (felloggar).
* Uppdateringshanteringen för delat minne har förbättrats. De ytterligare steg som krävdes i 20.2 behövs inte längre.

### ![](assets/do-not-localize/red_2.png) Version 20.2.2 – build 9180 {#release-20-2-2-build-9180}

_22 juli 2020_

* Korrigerade ett problem som hindrade spårning från att fungera när signaturfunktionen var inaktiverad. (NEO-26411)
* Korrigerade ett problem som medförde att osignerade länkar från anpassade domäner blockerades när de borde tillåtas. (NEO-25210)
* Korrigerade ett problem som kunde hindra dig från att öppna/klicka på spårnings-URL:er när du använde vissa äldre versioner av Outlook. (NEO-25688)
* Korrigerade ett problem som ledde till att spegelsidans URL:er definierades på ett felaktigt sätt i e-postleveranser (på grund av felaktig ASCII-teckenkontroll). (NEO-26084)
* Korrigerade ett problem med att hantera kodning av URL:er i tjänsten som förebygger nätfiske. (NEO-25283)
* Korrigerade ett problem som förhindrade spårning av URL:er, som använder fragment i personaliseringsparametrar (ankartaggar med pundtecken), från att fungera. (NEO-25774)
* Korrigerade ett problem med spårning när särskilda anpassade spårningsformler användes. (NEO-25277)
* Korrigerade ett problem som hindrade spårningen av ”meddelandeklickningar” från att fungera (iOS- och Android-push-meddelanden). (NEO-25965)
* Korrigerade en regression som påverkade beräknade fält i ett arbetsflöde och orsakade att arbetsflödet slutade fungera. (NEO-25194)
* Korrigerade en regression som förhindrade att webbspårnings-URL:er kunde skapas på direkten. (NEO-20999)
* Korrigerade ett regressionsproblem med färdiga leveransrapporter som verkade vara förkortade när de exporterades till PDF. (NEO-25757)
* Korrigerade ett problem där distributionsguiden kraschade.
* Korrigerade ett problem som kunde förhindra att arbetsflödet för erbjudandeavisering fungerar korrekt efter en efteruppgradering.
* iOS HTTP2-kopplingen har förbättrats (tredjepartsuppdateringar och felhantering). (NEO-25904 och NEO-25903)
* Listan jarsToSkip i catalina.properties har uppdaterats för att ta bort referensen till en jar-fil som inte längre används (iOS-meddelanden).
* Korrigerade ett problem som blockerade leveransförberedelser efter en efteruppgradering.
* Efter bytet till mekanismen för nytt sekvens-ID publiceras alla webbapplikationer som uppdaterar mottagartabellen på nytt, under efteruppgraderingen.
* Korrigerade en potentiell XSS-sårbarhet i leveransinnehåll. (NEO-17987 och NEO-26073)

![](assets/do-not-localize/cp-icon.png) **Den senaste versionen av kontrollpanelen från juni** med övervakning av aktiva profiler, granskning av deldomänens levererbarhet och hantering av GPG-nycklar. [Läs mer](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=sv).

### ![](assets/do-not-localize/red_2.png) Version 20.2.1 – build 9178 {#release-20-2-1-build-9178}

_8 juni 2020_

**Nyheter**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Stöd för uttryckssymboler</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>När du utformar ett meddelande i Campaign kan du nu enkelt infoga uttryckssymboler i meddelandetexten med en dedikerad knapp. De kan också läggas till i e-postmeddelandets ämnesrad. Du kan anpassa listan med tillgängliga uttryckssymboler i gränssnittet.</p>
    <p>Se den <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">detaljerade dokumentationen</a> för mer information om hur du lägger till uttryckssymboler. Läs mer om hur man anpassar listan med uttryckssymboler <a href="../../delivery/using/customizing-emoticon-list.md">i det här avsnittet</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure Synapse FDA-koppling</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Du kan ansluta din instans i Campaign till den externa Azure Synapse-databasen. Denna anslutning hanteras via ett nytt externt konto.</p>
    <p>Azure Synapse är bara tillgängligt för hybridmiljöer och lokala miljöer. Mer information finns i den <a href="../../installation/using/configure-fda-synapse.md">detaljerade dokumentationen</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Integritetslagar för Thailand och Brasilien</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Thailands lag om skydd av personuppgifter (PDPA) är den nya integritetslagen som harmoniserar och moderniserar kraven på skydd av personuppgifter i Thailand. </p>
   <p>Brasiliens Lei Geral de Proteção de Dados (LGPD) börjar gälla från och med början av 2021 för alla företag som samlar in eller behandlar personuppgifter i Brasilien.</p>
   <p>Dessa bestämmelser gäller för Adobe Campaign-kunder som innehar uppgifter för registrerade personer som bor i dessa länder. Förutom de sekretessfunktioner som redan finns i Campaign (inklusive medgivandehantering, datalagringsinställningar och användarroller) tar vi tillfället i akt att inkludera ytterligare funktioner för att underlätta beredskapen för PDPA och LGPD:</p>
   <ul> 
     <li><p>Rätt till åtkomst och rätt att ta bort: vi tar vara på de funktioner som redan finns för GDPR och CCPA. <a href="https://helpx.adobe.com/se/campaign/kb/acc-privacy.html">Läs mer</a></p></li> 
     <li> <p>När du skapar en förfrågan om användarens information med gränssnittet i Campaign eller API:et väljer du nu <strong>regeltypen</strong>: PDPA, LGPD, GDPR eller CCPA. <a href="https://helpx.adobe.com/se/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">Läs mer</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Säkerhetsförbättringar**

* Förbättrad säkerhet för spårning av länkar i e-postmeddelanden är aktiverad som standard för alla kunder. Det finns ytterligare en förbättrad säkerhetsfunktion som kan aktiveras genom att kontakta kundtjänst. Mer information om funktionen och stegen för icke-värdbaserade kunder som vill aktivera den finns i [checklistan över säkerhet och sekretess](https://helpx.adobe.com/se/campaign/kb/acc-security.html). (NEO-24232)

* För att optimera säkerheten har MD5-hash-algoritmen som används för att generera filnamn förstärkts med sha256 för offentlig filöverföring. (NEO-17044)

* För att förstärka säkerheten mot XSS-angrepp inaktiveras skript på klientsidan när en spegelsida körs. (NEO-17987)

* Ett problem som hindrade det tekniska arbetsflödet **borttagning av förfrågningar om användares information** från att ta bort avstämningsdata har åtgärdats. (NEO-25168 och NEO-21004)

* Ett problem med **filöverföringar** som hindrade SFTP-nyckelbaserad autentisering från att fungera i Debian 9 har korrigerats. (NEO-23183)

**Kompatibilitetsförbättringar**

Campaign har nu stöd för följande system:
* Operativsystem: Debian 10
* RDBMS: Oracle 18c och Oracle 19c
* FDA: Azure Synapse Analytics

Läs mer i [kompatibilitetsmatrisen i Campaign](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html).

**Förbättringar**

* Transaktionsmeddelanden har förbättrats för en bättre användarupplevelse. En mall för transaktionsmeddelanden kan nu avpubliceras. Detta tar bort den från körningsinstanserna. [Läs mer](../../message-center/using/publishing-message-templates.md#template-unpublication).

* Det finns nya alternativ för att ange begränsningar när e-postmeddelanden skickas och de innehåller bilder eller bilagor. Dessa skydd kan undvika prestandaproblem, vilket är särskilt användbart för transaktionsmeddelanden. [Läs mer](../../installation/using/configuring-campaign-options.md#delivery)

* Det nya alternativet **Förbereda leveransdelarna i databasen** gör det möjligt att utföra leveransförberedelser direkt i databasen, vilket kan avsevärt snabba upp analysen. Det här alternativet är bara tillgängligt för särskilda konfigurationer. [Läs mer](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* Prestandan gällande [aktiviteten i CRM-kopplingen](../../workflow/using/crm-connector.md) för Microsoft Dynamics har förbättrats. (NEO-13303 och NEO-12710)

* Versionen för delat minne har uppgraderats.

   >[!WARNING]
   >
   >Denna förbättring kräver ytterligare ett steg efter uppgraderingen. Se avsnittet **Tekniska utvecklingar** nedan.

* Arbetsflödet för rensning har förbättrats. Överblivna arbetstabeller för alla borttagna arbetsflöden tas nu även bort automatiskt av arbetsflödet för rensning. [Läs mer](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Certifikat för mobila applikationer i iOS med iOS HTTP2-kopplingen valideras nu innan push-meddelanden skickas, vilket förhindrar att leveranser misslyckas på grund av utgångna certifikat.

* Hanteringen av HTTP-proxyanslutningar har förbättrats. [Läs mer](../../installation/using/file-res-management.md).

* Nytt alternativ i arbetsflödesaktiviteterna **[!UICONTROL Javascript Code]** och **[!UICONTROL Advanced Javascript Code]** för att stoppa körningen efter en gräns. Standardvärdet är 1 timme. [Läs mer](../../workflow/using/sql-code-and-javascript-code.md#javascript-code).

**Andra ändringar**

* Äldre SMS-kopplingar är nu inaktuella. Se till [sidan Inaktuella funktioner](../../rn/using/deprecated-features.md).

* Du kan inte längre använda ditt eget Litmus-konto för att etablera och använda Inkorgsåtergivning i Adobe Campaign. [Läs mer](../../delivery/using/inbox-rendering.md).

* Färgen på visningsnamnen har ändrats från mörkblått till mörk cyan för att göra det lättare att skilja vyer från mappar. [Läs mer](../../platform/using/access-management-folders.md)

* Campaign Classic kan nu anslutas till Microsoft Dynamics CRM-konton i Storbritannien, Indien och Kanada. Detta gäller driftsättningstyperna Office 365 och lokalt (Dynamics 2015).

* Campaign utför nu en TLS-verifiering för att kontrollera att värdnamnet för servern matchar värdnamnet i det angivna certifikatet.

* Tabellen Leverans- och spårningsstatistik visar nu en post per leverans för SMS-kanalen i stället för en post per leveransmottagare.

* Ett felmeddelande har lagts till i loggfilen för att varna användare när den nedladdade filen är större än diskutrymmet.

* Följande funktioner är nu tillgängliga för Snowflake-kopplingen: MonthsAgo, DaysAgoInt, ToDateTime och YearsAgo.

**Tekniska utvecklingar**

Den nya versionen uppdaterar delat minne och kräver ytterligare steg för att utföra uppgraderingen. Som administratör i Campaign måste du ta bort minnessegment. Dessa steg är obligatoriska eftersom gamla segment förhindrar att nlserver/nlsrvmod startar.

I Windows krävs en omstart av systemet.

I Debian/CentOs krävs delad minnesborttagning. Gör följande:

Innan uppgraderingen måste du utföra följande:

1. Stoppa tjänsten Apache2 (http2 i CentOS) om den körs.
1. Stoppa tjänsten nlserver (nlserver6 för äldre versioner) om den körs.

Efter uppgraderingen:

1. Ta bort det delade minnet med kommandot **ipcrm** om versionen är äldre än den aktuella versionen.
1. Starta tjänsten nlserver om den kördes.
1. Starta tjänsten Apache2 om den kördes.

Följande är kommandoraderna för Debian:

```
/etc/init.d/nlserver* stop
/etc/init.d/apache2 stop

for i in `ipcs -s | awk '/www-data/
{print $2}'`; do (ipcrm -s $i); done

for i in `ipcs -m | awk '/www-data/ {print $2}
'`; do (ipcrm shm $i); done

for i in `ipcs -m | awk '/neolane/
{print $2}'`; do (ipcrm shm $i); done

for i in `ipcs -s | awk '/neolane/ {print $2}
'`; do (ipcrm -s $i); done

/etc/init.d/apache2 restart
/etc/init.d/nlserver* start
```

Ett exempel för Linux finns på den här [sidan](../../configuration/using/additional-parameters.md#redirection-server-configuration).

**Felkorrigeringar**

* Korrigerade en mindre regression i loggfilerna för arbetsflödet för rensning.
* Korrigerade ett problem i arbetsflödets **inläsningsaktivitet (SOAP)** vid tolkning av WSDL-filer.
* Korrigerade ett problem som orsakade ett fel vid uppgradering av ett antal arbetsflöden med en **undersökningsaktivitet** för att effektivt bearbeta ett stort antal arbetsflöden.
* Korrigerade ett intermittent anslutningsproblem under bearbetningen av inMail-meddelanden från Enhanced MTA. (NEO-20380)
* Korrigerade ett problem som förhindrade att procentvärdena för aktiva klick visades korrekt när bilder visades med en bredd på 100 % i HTML-koden. (NEO-23203)
* Korrigerade ett problem som förhindrade att leveransens villkorliga innehåll visades fullständigt i rapporten med aktiva klick. (NEO-18729)
* Korrigerade ett problem som hoppade över steget med målgruppens godkännande när ett arbetsflöde återupptogs för att skicka en återkommande leverans. (NEO-18166)
* Korrigerade ett problem som förhindrade knappen **Starta om förberedelsemeddelandet** från att återuppta leveransen efter att ett fel i arbetsflödet hade åtgärdats. (NEO-13488)
* Korrigerade ett problem som kunde få leveranser att misslyckas i läget mid-sourcing under uppstartsfasen där målgruppen inkluderade mottagare med japanska e-postformat. (NEO-23846)
* Korrigerade ett problem med konvertering av tidszoner med Snowflake-koppling (NEO-20105)
* Korrigerade ett problem med externa konton som använder FTP över SSL. (NEO-20498)
* Korrigerade ett problem som kunde förhindra att bilder visades i Line-leveranser. (NEO-23207)
* Korrigerade ett problem som orsakade ett fel när ett erbjudande publicerades. (NEO-23312)
* Korrigerade ett problem med push-meddelanden som gjorde att testanslutningar fungerade i mobila applikationer även när certifikatet hade upphört att gälla. (NEO-22991)
* Korrigerade ett problem som kunde påverka push-meddelanden när de skickades med hög frekvens. (NEO-20516)
* Korrigerade ett problem som gjorde att spårningsdata inkluderade dubbletter trots att spårningsloggarna inte gjorde det. (NEO-20040)
* Korrigerade ett problem som orsakade att dubbla transaktionsmeddelanden skickades efter att ett kommunikationsfel för spårningsservern hade korrigerats. (NEO-23640)
* Korrigerade ett problem som raderade kodning av parametervärde vid omdirigering från en spårnings-URL (inverkan på japanska tecken). (NEO-25637)
* Korrigerade ett problem som kunde förhindra att en fråga fungerade när flyttal jämfördes. (NEO-23243)
* Korrigerade ett problem som kunde förhindra att innehållet i kolumnen **Ändrad av** visades efter att ett arbetsflöde startades om. (NEO-23035)
* Korrigerade ett problem som gjorde att det tekniska arbetsflödet för spårning inte fungerade vid nedladdning av loggar från en andra behållare. (NEO-23159)
* Korrigerade ett problem som kunde få arbetsflöden att inte fungera när en **Berikandeaktivitet** kördes. (NEO-17338)
* En kontroll har lagts till i fältet **Dubbletter att behålla** i arbetsflödesaktiviteten **Avduplicering** för att förhindra att noll eller negativa värden anges.
* **Guiden för Scheduler** har tagits bort från de återkommande kampanjerna för att undvika omnämnande av timmar och minuter. Endast datum beaktas.
* Korrigerade ett problem med ytterligare lagringsfält när leveranser skapades via alternativet **Beräknad av ett skript** i **skriptet** arbetsflödesaktivitet. (NEO-20609)
* Korrigerade ett problem som förhindrade att spökarbetsflöden togs bort i databasrensningen.
* Korrigerade ett problem som gjorde att det tekniska arbetsflödet för **fakturering (aktiva profiler)** inte fungerade. (NEO-19777)
* Korrigerade ett regressionsproblem vid användning av ACS Connector-funktionen som förhindrade anslutningen till en instans i Campaign Standard (felaktig hantering av FOH/FOH2-anslutningen). (NEO-23433)
* Korrigerade ett problem som gjorde att du inte kunde skapa ett schematillägg för en primärnyckel med flera kolumner med en Hadoop-tabell. (NEO-17390)
* Korrigerade ett problem i **inläsningsaktiviteten (SOAP)** som kunde förhindra att WSDL-filer lästes in från en URL. (NEO-16924)
* Korrigerade ett problem som förhindrade dig från att utföra ett **ovillkorligt stopp** via konsolen när flera aktiva arbetsflödesservrar lästes in. (NEO-19556)
* Korrigerade en regression som fick arbetsflödet för rensning att krascha.
* Korrigerade ett problem som kunde inträffa när en mall publicerades på en körningsinstans.
* Korrigerade ett problem som kunde förhindra att det tekniska arbetsflödet collectPrivacyRequests kördes. (NEO-20513 och NEO-25169)
* Korrigerade problem som kunde inträffa vid försök att ansluta till Audience Manager efter uppgradering till build 9080. (NEO-20511 och NEO-25167)
* Korrigerade ett problem som kunde uppstå vid export av rapporter i PDF- eller XLS-format. (NEO-20982, NEO-23493 och NEO-23348)
* Korrigerade ett problem som kunde visa en leverans två gånger i leveranslistan efter att den hade skickats.
* Korrigerade ett problem med leveransförberedelser som kunde inträffa när routningskonfigurationen var inställd på att skicka leveransen via mid-sourcing.
* Korrigerade ett problem som kunde visa ett felmeddelande när du klickade på en webbapplikationslänk i ett Line-meddelande.
* Korrigerade ett problem som tog bort aktivitetshistoriken för **Inkrementell fråga** efter att ha kört arbetsflödet för rensning.
* Ett problem har korrigerats när ett externt konto med mid-sourcing skapades där alternativet NmsMidSourcing_LastBroadLog_&lt;InternalName> saknades.
* Korrigerade ett regressionsproblem i databasanslutningen som orsakade att webbservern hela tiden startades om på grund av ett problem med databaskodningen. Detta kan leda till överkonsumtion. (NEO-23264)


## Version 20.1{#release-20-1}

### ![](assets/do-not-localize/limited_2.png) Version 20.1.4 – build 9126 {#release-20-1-4-build-9126}

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

### ![](assets/do-not-localize/red_2.png) Version 20.1.3 – build 9124{#release-20-1-3-build-9124}

_6 maj 2020_

* Ett problem med **filöverföringar** som hindrade SFTP-nyckelbaserad autentisering från att fungera i Debian 9 har korrigerats. (NEO-23183)

### ![](assets/do-not-localize/red_2.png) Version 20.1.2 – build 9123{#release-20-1-2-build-9123}

_13 mars 2020_

* Korrigerade ett problem som förhindrade versionshantering på Red Hat 7-servrar. (NEO-23332)

### ![](assets/do-not-localize/red_2.png) Version 20.1 – build 9122{#release-20-1-build-9122}

_17 februari 2020_

**Nyheter**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Snowflake FDA Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Snowflake är ett helt hanterat moln data warehouse som bygger på både lagrings- och beräkningsnivå. Med denna nya kontakt kan Adobe Campaign nu utnyttja Snowflake förmåga att utföra Big Data Segmentation. Den här kontakten är tillgänglig för alla kunder, inklusive via Adobe.</p>
    <p>Mer information finns i <a href="../../installation/using/configure-fda-snowflake.md">detaljerad dokumentation</a> och <a href="https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">video med självstudiekurser</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Förbättringar av hadoopets FDA Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Hadoopet FDA Connector har förbättrats med stöd för både Hadoop 3.0 och Cloudera.</p>
    <p>Mer information finns i den <a href="../../installation/using/configure-fda-hadoop.md">detaljerade dokumentationen</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

**Säkerhetsförbättringar**

* Förbättrad säkerhet i rapportkonfigurationen som skyddar mot clickjacking. Detta gäller nya rapporter. För gamla rapporter måste du publicera om dem för att ändringarna ska gälla. (NEO-13282)

* Åtgärda ett litet minnesproblem i cryptString. (NEO-20071)

* Förbättrad JSP-övervakare för att åtgärda intern IP-exponering. (NEO-16821)

* Ett problem där stackspårningsinformation kunde visas för icke-adminanvändare har korrigerats. (NEO-12388)

* Förbättrad hantering av cachelagrade data från tidigare sessioner. (NEO-17039)

* Korrigerade ett problem som förhindrade filen logins.log från att registrera lyckade inloggningsförsök via IMS. (NEO-11004)

**Förbättringar**

* iOS 13 stöds nu med HTTP2-anslutningen.

* Förbättrad karantänhantering och rensning av tabeller som används av funktionen för push-meddelanden (nms:address och nms:appSubscriptionRcp). För iOS (endast HTTP2-anslutning) hanteras nu inaktiverade tokens på samma sätt som för Android. Inaktiveringsflaggan har nu angetts i tabellen NmsAppSubscriptionRcp. [Läs mer](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* Ett nytt alternativ har lagts till i **JavaScript-kod** och **Avancerad JavaScript-kod** arbetsflödesaktiviteter för att definiera en timeout-period. Detta förhindrar att JavaScript-körningsfasen körs för länge. Om tidsgränsen överskrids stoppas arbetsflödet. Standardtidsgränsen är 1 timme. [Läs mer](../../workflow/using/sql-code-and-javascript-code.md)

* Leveransanalysen stoppas nu när ingen matchande tillhörighet hittas på mittkällservern, med motsvarande felmeddelande.

* Databasredundans för Postgres stöds nu: när databasservern kraschar och startas om kopplas Campaign nu automatiskt tillbaka till den.

* The **Påbörja väntande** vyn har lagts till i noden Administration > Granskning > Arbetsflödesstatus. Detta gör att du kan övervaka alla arbetsflöden på instansen som väntar på att startas av **operationMgt** -processen. Den här vyn levereras med paketet med marknadsföringskampanjer. [Läs mer](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Andra ändringar**

* I Linux används nu en systemenhet för start av servertjänsten i stället för skriptet /etc/init.d/nlserver6. Migreringen till det nya startschemat utförs automatiskt när du installerar 20.1-paketet. /etc/init.d/nlserver6 finns fortfarande men för interaktion med nlserver-tjänsten (start, omstart, stopp osv.) rekommenderar vi att du använder systemctl-kommandot direkt.

* De mest använda anpassade tabellerna har flyttats från **xtkNewId** till dedikerade sekvenser.

* Förbättrade frågeprestanda som kan påverkas av onödiga databasanslutningar.

* Förbättrade prestanda för guiden Databasuppdatering för att göra färre SQL-satser för att optimera svarstiden.

* Hanteringen av databasposter har förbättrats.

* Anslutningspoolens tillförlitlighet har förbättrats, vilket kan förhindra att oväntade anslutningsfel inträffar för ofta.

* Verifieringsreglerna för e-postadresser som skickar en adress till karantän om ett mjukt fel uppstår har förbättrats. [Läs mer](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* För Debian använder Campaign nu system PCRE-bibliotek när de blir tillgängliga.

* Campaign tillåter nu användning av ett nyare ODBC-systembibliotek.

* En timeout har lagts till i LINE-serverleten när en anslutning öppnas för att läsa in en rik bild. Om det tar för lång tid att läsa in bilden avbryts anslutningen för att undvika flaskhalsar.

**Korrigeringar**

* Ett krypteringsfel för kontonycklar har korrigerats när Hadoopet används.

* Korrigerade ett regressionsproblem på grund av implementeringen av SSL-certifieringen som gjorde att användaranslutningen misslyckades på Windows-servern. (NEO-20629)

* Ett problem med den inkrementella frågeaktiviteten vid negativa arbetsflödes-ID:n har korrigerats. (NEO-19779)

* Korrigerade ett kodningsproblem när frågor kördes via Netezza FDA-anslutningen. (NEO-19594)

* Ett problem som orsakade ett fel när metoden POST i **Web Download** händelseaktivitet i arbetsflöde.

* Ett problem med generering av erbjudandeförslag har korrigerats. (NEO-18176)

* Korrigerade ett sidfotsvisningsproblem när webbformulärmallen för hämtning användes.

* Ett problem som orsakade att URL:er i innehållet i kontinuerliga leveranser tolkades har åtgärdats. (NEO-16910)

* Ett problem med **Starta** och **End** fält som inte beräknas när en ny kampanj skapas.

* Ett problem med **Filhämtning** arbetsflödesaktivitet när en URL används.

* Ett problem har korrigerats vid förhandsgranskning av en importerad lista i en frågeaktivitet i en rapport. (NEO-13119)

* Ett problem som visade en föråldrad bild vid val av **Powered by Campaign** personaliseringsblock i e-postredigeraren.

* Nätverkskommunikationen mellan klienten och servern har förbättrats.

* Ett problem har korrigerats när för många arbetsflöden skapades i samma kampanj. Nu kan du inte skapa fler än 28 arbetsflöden. En varning visas.

* Ett problem som uppstod när **En markering med kolumner** avstämningsalternativ i **Union** arbetsflödesaktivitet.

* Korrigerade ett kraschproblem i konsolen som kan inträffa när en skadad anrikningslista används i ett arbetsflöde. (NEO-18096)

* Åtgärdade olika kraschproblem i konsolen som kan uppstå i arbetsflöden (NEO-18010, NEO-18032)

* Ett problem som gjorde att en **Extern signal** arbetsflödesaktivitet även när den inaktiverades. (NEO-17524)

* Ett problem har korrigerats när ett nytt schema skapades.

* Korrigerade ett spårningsproblem när SMS-meddelanden skickades. (NEO-19595)

* Korrigerade ett problem som visade felaktigt målgruppsnummer i leveransindikatorer.

* Korrigerade ett problem som visade felaktiga procentvärden när en beskrivande rapport genererades via en arbetsflödesaktivitet. (NEO-14314)

* Korrigerade ett problem som gjorde att leveransgenomströmningsrapporten visade olika nummer när tidsvyparametern användes. (NEO-11783)

* Ett problem som förhindrade att spårningsindikatorerna för transaktionsmeddelanden uppdaterades i arbetsflödet för spårning har åtgärdats. (NEO-17770)

* Korrigerade ett regressionsproblem som gjorde att webbprocessen kraschade och startades om när ett erbjudande begärdes via SOAP. (NEO-19482)

* Korrigerade ett problem som förhindrade överföring av data till offentliga resurser om överföringskatalogen var en delad fjärrplats. (NEO-19361)

* Ett problem som orsakade **Importera målgrupper från Adobe Experience Cloud** det tekniska arbetsflödet misslyckas ständigt. (NEO-18463)

* Korrigerade ett problem som förhindrade att leveranser skickades när mallar som importerats från Experience Manager användes. (NEO-17540)

* Korrigerade ett fel som uppstod efter uppgraderingen till build 9032 och förhindrade instansen från att ansluta till FTP-servern via SSL-protokollet. (NEO-20498)

* Ett problem som uppstod när en stor mängd data skulle tas bort, infogas eller uppdateras med **Uppdatera data** i ett arbetsflöde med ett FDA-schema som måldimension. (NEO-13280)

* Ett problem som förhindrade att e-post skickades när det fanns Javascript-kod utanför innehållstaggen för HTML har åtgärdats. (NEO-18628)

* Korrigerade ett fel som uppstod när spegelsidan skulle visas från leveransloggarna för ett skickat meddelande. (NEO-17976)

* Ett problem som förhindrade **Länk till spegelsida** Personaliseringsblocket visas inte i **Textinnehåll** tabb efter klickning **Importera HTML** i en leverans. (NEO-17568)

* Felmeddelandet som visas när du klickar på en länk till en spegelsida som har gått ut har klargjorts. (NEO-17340)

* Ett problem som gjorde att vissa knappar inte kunde användas i **Datadistribution** skärmen.

* Ett problem som uppstod när en leveransaktivitet schemalades i en instans med Asien/Kolkata som tidszon har åtgärdats. (NEO-20001)

* Ett fel visas nu när en leverans har ett tillhörighetskonfigurationsproblem.

* Ett problem som visade ett felaktigt versionstaggnummer i **Om** -menyn.

* Korrigerade ett problem som uppstod när routningskontot skulle uppdateras från egenskaperna för en återkommande leverans i ett arbetsflöde. (NEO-18684)

* Korrigerade ett fel som uppstod vid anslutning till instansen via omdirigeringsmodulen, vilket förhindrade att anslutningen rensades korrekt när den stängdes.
