---
solution: Campaign Classic
product: campaign
title: Version 20.3
description: Version 20.3
audience: rns
content-type: reference
topic-tags: campaign-release-notes, latest-release-notes
translation-type: tm+mt
source-git-commit: 97546a5a49880c5af51754fb5d7b02359f3d556c
workflow-type: tm+mt
source-wordcount: '1941'
ht-degree: 99%

---


# Version 20.3{#release-20-3}

## ![](assets/do-not-localize/blue_2.png) Version 20.3.3 – build 9234 {#release-20-3-3-build-9234}

_11 januari 2021_

* Korrigerade ett säkerhetsproblem för att förstärka skyddet mot problem med SSRF (Server Side Request Forgery). (NEO-27777)
* Korrigerade ett regressionsproblem relaterat till genereringsprocessen av leveransloggar som kunde få MTA-processen att krascha.

## ![](assets/do-not-localize/red_2.png) Version 20.3.1 – build 9228 {#release-20-3-1-build-9228}

_27 oktober 2020_

>[!CAUTION]
>
> * Den här versionen inkluderar ett nytt anslutningsprotokoll: om du ansluter till Campaign via Adobe Identity Service (IMS) är en uppgradering obligatorisk för både Campaign-servern och klientkonsolen för att kunna ansluta till Campaign efter **31 mars 2021**.
> * Den här versionen innehåller en [säkerhetskorrigering](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): uppgradering är obligatorisk för att öka din miljösäkerhet.
> * Om du använder integreringen av Experience Cloud Triggers via oAuth-autentisering måste du gå över till Adobe I/O såsom beskrivs [på den här sidan](../../integrations/using/configuring-adobe-io.md). Äldre oAuth-autentiseringsmodeller upphör **30 april 2021**.


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
   * Anslutningsprotokollet har uppdaterats för att följa den nya IMS-autentiseringsmekanismen. Att uppgradera servern och klientkonsolen är obligatoriskt för att kunna ansluta efter 31 mars 2021.
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
