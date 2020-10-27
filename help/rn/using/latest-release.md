---
title: Senaste versionen
description: Versionsinformation om senaste Campaign Classic
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: fe7ce92bde3405fed3429475cdd5681e5837876f
workflow-type: tm+mt
source-wordcount: '1820'
ht-degree: 3%

---


# Senaste versionen{#latest-release}

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i den **senaste versionen** av Campaign Classic Release Candidate.

Campaign Classic Gold Standard-versionen (senaste GA-versionen) [finns på den här sidan](../../rn/using/gold-standard.md).

## ![](assets/do-not-localize/blue_2.png) Version 20.3.1 - build 9228 {#release-20-3-1-build-9228}

_27 oktober 2020_

**Nyheter**

<table> 
<thead>
<tr> 
<th> <strong>Förbättringar av push-meddelanden i iOS</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>När ni integrerar mobilappen med Campaign måste ni säkra kommunikationen med Apple Push Notification service (APN:er). Du kan använda certifikatbaserad eller tokenbaserad autentisering.
</p>
<p>Dessa två autentiseringslägen är nu tillgängliga för iOS-mobilappar i Campaign Classic:
</p>
<ul> 
<li><p>Tokenbaserad autentisering (rekommenderas): det här autentiseringsläget baseras på en P8-fil. Autentiseringsläget är snabbare eftersom varje begäran till APN:er innehåller token. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns">Läs mer</a></p></li>
<li><p>Certifikatbaserad autentisering: det här autentiseringsläget baseras på en P12-fil. För varje program krävs ett separat certifikat. Det här certifikatet levereras av Apple via ditt utvecklarkonto. <a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns">Läs mer</a></p></li> 
</ul>
<p>Lär dig hur du väljer autentiseringsläge i Campaign i den <a href="../../delivery/using/configuring-the-mobile-application.md">detaljerade dokumentationen</a>.</p>
</td> 
</tr> 
</tbody> 
</table>

<table> 
<thead>
<tr> 
<th> <strong>Förbättringar av push-meddelanden i Android</strong><br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td> <p>Android-push-meddelanden har förbättrats med stöd för FCM HTTP v1 API för Android-push-kanalautentisering. </p>
<p>Med den nya API-versionen som stöds kan du nu skicka FCM-meddelanden som har utökade funktioner för push-meddelanden. <a href="https://firebase.google.com/docs/cloud-messaging/migrate-v1">Läs mer</a></p> 
<p>Lär dig hur du konfigurerar FCM HTTP v1 API för Android i Adobe Campaign i <a href="../../delivery/using/configuring-the-mobile-application-android.md">det här avsnittet</a> .</p>
</td> 
</tr> 
</tbody> 
</table>

**Säkerhetsförbättringar**

* Säker inläsning av bibliotek: För att skydda sig mot DLL-förinläsningsattacker läser Campaign nu in Windows DLL-filer endast från Windows standardsystem-DLL-sökvägen när Campaign Client (nlclient) läses in. [Läs mer](https://support.microsoft.com/en-us/help/2389418/secure-loading-of-libraries-to-prevent-dll-preloading-attacks) (NEO-24147)
* Korrigerade ett säkerhetsproblem för att förstärka skyddet mot SSRF-attacker (Server Side Request Forgery). (NEO-25661)
* Korrigerade ett fel som uppstod vid hantering av GDPR-sekretessbegäranden som förhindrade att poster togs bort från anpassade tabeller med en relation på andra nivån till mottagartabellen. (NEO-25967)
* Ett säkerhetsproblem har korrigerats med API-anrop från icke-adminanvändare vid försök att synkronisera Adobe Experience Manager-mallar. (NEO-23487)

**Kompatibilitetsuppdateringar**

Campaign har nu stöd för följande system:
* iOS 14
* PostgreSQL 12
* CentOS / RedHat 8
* MSSQL2019

Learn more in the [Campaign Compatibility matrix](../../rn/using/compatibility-matrix.md).

**Inaktuella funktioner**

Följande funktioner har tagits bort i 20.3:

* Den demodomän som används för att importera och exportera målgrupper till Adobe Experience Cloud är föråldrad. Om du använder demodomänen för dina externa import-/exportkonton måste du anpassa implementeringen därefter. [Läs mer](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)
* Integreringsautentisering med utlösare som ursprungligen baserades på AUTH-autentiseringsinställningar för åtkomst till pipeline har nu ändrats och flyttats till Adobe I/O. [Läs mer](../../integrations/using/about-triggers.md)

Läs mer på sidan [Funktioner som](../../rn/using/deprecated-features.md)tagits bort eller tagits bort.

**Förbättringar**

* Flera förbättringar har gjorts i **klientkonsolen**:
   * För att förhindra inkompatibilitet med vissa begränsningar i grupprincipobjektregler för Internetsäkerhet har inloggningsskärmen för klientkonsolen i Campaign ersatts av ett inbyggt standardformulär för Windows.
   * Ett problem har korrigerats vid kopiering/inklistring i ett arbetsflöde med 64-bitars klientkonsol. (NEO-27635)
   * På menyn **Om** har information lagts till för att skilja 64- och 32-bitars konsoler åt.
* Arbetsflödesidentifieraren visas nu i loggarna när du återupptar ett arbetsflöde, vilket gör det lättare att identifiera vilket arbetsflöde som återupptogs.
* En ny permanent cookie har införts: nllastdelid. Denna cookie (annan än UUID230) lagrar deliveryId. När sessionscookie saknas hämtas utsändningsinformation från det deliveryId som finns i denna cookie.
Den här ändringen åtgärdar ett fel som uppstod när webbläsarsessionen var över: sessionscookien som innehåller deliveryId och broadlogId har tagits bort. Utan deliveryId gick det inte att hitta utsändningsinformation och spårningstabellinformationen skulle saknas om det fanns en permanent spårning (senaste leverans).
Läs mer om cookies i [det här avsnittet](../../platform/using/privacy-and-recommendations.md#cookies).
* Förbättrade prestanda för leverans av stora volymer med leveransserver genom att starta om MTA-processen innan leverans skickas.

**Andra ändringar**

* När du använder relativ sökväg för SFTP läggs inte längre `~/` tecken automatiskt till. Vid behov kan du lägga till `~/` tecken i sökvägen manuellt, men Adobe rekommenderar att du använder en **absolut sökväg**.
* Windows NT-autentisering har tagits bort från de tillgängliga autentiseringsmetoderna när en ny databas konfigureras med en Microsoft SQL Server. [Läs mer](../../installation/using/creating-and-configuring-the-database.md#step-1---selecting-the-database-engine)
* Arbetsflödet för databasrensning har optimerats för Teradata för att förbättra prestandan. (NEO-19959)
* Förbättrade felmeddelandet som visades när en bild infogades från Adobe Target och innehavarnamnet var tomt i det externa kontot.
* I leveransegenskaper har **[!UICONTROL Archive emails]** alternativet bytt namn **[!UICONTROL Email BCC]**.
* Markera Alla frågor med ogiltiga noder avvisas nu för att förbättra tillförlitligheten. Om du behöver inaktivera kontrollen och återgå till det tidigare beteendet kan du ställa in XtkSecurity_Disable_QueryCheck på 0.

**Tekniska utvecklingar**

Tomcat har uppdaterats från version 7 (7.0.103) till version 8 (8.5.57).

Katalogen `tomcat-7` ersätts med en `tomcat-8` katalog.

I Windows _installeras iis_neolane_setup.vbs_ och _apache_neolane.conf_ nu i `conf` katalogen (i stället för `tomcat-7/conf` tidigare).

I Linux är _apache_neolane.conf_ nu installerat i `conf` katalogen.

**Felkorrigeringar**

* Korrigerade ett problem som kunde förhindra att leveransstatistik beräknades om.
* Korrigerade ett fel som visade ett felmeddelande när en CSV-fil överfördes med Campaign Classic 9080-bygge som är ansluten till en server med en äldre version. (NEO-23218)
* Korrigerade ett problem som kunde visa ett felmeddelande när Microsoft Dynamics CRM-guiden konfigurerades för ett externt konto. Detta berodde på ett kompatibilitetsproblem med den senaste API-versionen för MS Dynamics CRM. (NEO-24528)
* Korrigerade ett problem som förhindrade dig från att exportera poster av typen lookup (dvs. data som består av poster med sekundärnyckel kopplade till andra tabeller) från Campaign Classic till Microsoft Dynamics med CRM-kopplingen. (NEO-23864)
* Ett problem som kunde förhindra att Microsoft Dynamics-data hämtades om alternativet **Automatiskt index** aktiverades i CRM-anslutningen har åtgärdats. (NEO-25981)
* Korrigerade ett problem med IMS-autentisering som kunde lämna anslutningar öppna även om de avslutades. Avbrutna anslutningar stängs nu automatiskt så fort de avslutas för att undvika att anslutningar och systemresurser ackumuleras. (NEO-25996)
* Korrigerade ett problem som inte visade något felmeddelande när synkroniseringen av Adobe Experience Manager-innehåll misslyckades för en leverans på grund av en felkonfiguration av det externa kontot (felaktigt konto eller lösenord). Ett meddelande visas nu i händelse av fel, vilket gör det lättare att identifiera problemet. (NEO-25586)
* Ett problem som uppstod när **Update** -åtgärdstypen valdes i aktiviteten **Update data** har åtgärdats. Om de data som ska uppdateras var felaktiga, skulle arbetsflödet vara fel och misslyckas. Om data är felaktiga kommer arbetsflödet inte att misslyckas och posterna lagras i en utgående övergång för **Avvisningar** . (NEO-23794)
* Ett problem som kunde förhindra arbetsflöden med delarbetsflöden har korrigerats. (NEO-24036)
* Ett problem har korrigerats vid redigering av en kampanjmallsbeskrivning som hindrade knappen **Spara** från att visas när symboler som t.ex. japanska tecken kopieras och klistras in. (NEO-27071)
* Korrigerade ett problem som kunde förhindra dig från att ändra spårningsservern i instanskonfigurationsguiden.
* Korrigerade ett problem som förhindrade att beskrivningen av en kampanj- eller kampanjmall sparades när användaren klickade utanför fönstret innan användaren klickade på knappen **Spara** . (NEO-27449)
* Ett problem som kunde förhindra det tekniska arbetsflödet **Antal aktiva faktureringsprofiler** (billingActiveContactCount) har åtgärdats. Detta kan inträffa om en länk har utförts på ett beräknat fält i ett schematillägg. En stor mängd data skapades, vilket kan leda till att databasen får slut på temporärt utrymme. (NEO-24062)
* Ett problem med aktiviteten för inläsning av **data (fil)** har korrigerats, vilket kan hindra dig från att importera japanska tecken från txt- och csv-filer om de var placerade i slutet av filen. (NEO-24957)
* Ett problem med kontinuerliga leveranser som kunde förhindra att fälten **Startanalys** och **Analys slutförd** fylldes i korrekt har åtgärdats. (NEO-20755)
* Korrigerade ett problem som kunde visa ett felmeddelande när SMS-meddelanden skulle förhandsgranskas efter en fråga i ett annat schema än **mottagaren** (nms:mottagare). (NEO-27517)
* Ett problem har korrigerats vid användning av Snowflake FDA-anslutningen. En användare med Snowflake FDA-åtkomstnamnsrättigheter kunde inte köra en fråga i ett Snowflake-schema. Ett fel av typen &quot;Lösenordet hittades inte&quot; visades i loggarna. (NEO-23851)
* Korrigerade ett fel vid användning av en FDA-anslutning som inträffade när det länkade FDA-schemanamnet var en delsträng av ett elementnamn i det aktuella schemat. Detta inträffade till exempel om FDA-schemat var &quot;cust&quot; och ett av elementen i mottagarschemat var &quot;customer&quot;. När kolumnen i kundelementet hämtades och en kolumn från FDA-schemat &quot;cust&quot; lades till, saknades värdet för den lokala kolumnen. (NEO-20193)
* Korrigerade ett problem i arbetsflöden när poster hämtades från en extern databas och infogades i Campaign-databasen. (NEO-26359)
* Ett problem i det tekniska arbetsflödet för **Update-händelsestatus** har korrigerats: För att matcha storleken på inkommande motsvarande fält i aktiviteten **Leveransstatistik** ändrades storleken på tre målfält i aktiviteten **Uppdatera leveransstatus** från 32 till 64 bitar. (NEO-11557) Läs mer om arbetsflödet för status **för** uppdateringshändelser i [det här avsnittet](../../workflow/using/message-center--execution-.md).
* Korrigerade ett fel i händelserapporten för **meddelandecentret** som orsakade skriptfel när filter tillämpades och gjorde filtret till ett datumintervall omöjligt. (NEO-23365)
* Korrigerade ett störningsproblem mellan de tekniska arbetsflödena för **kampanjjobb** (operationMgt) och **Preview** (prognostisering). Detta inträffade när schemalagda leveranser förblev i statusen&quot;Klart för mål&quot; eller&quot;Klart för leverans&quot;. (NEO-20819)
* Korrigerade ett XML-tolkningsproblem när XML-identifieraren inte fanns i datafältet i xtkOperator. Det orsakade fel efter uppgraderingen. (NEO-26113)
* Ett problem har korrigerats vid användning av **filöverföringsaktiviteten** som är länkad till ett externt Azure-konto som krypterats i SSL, där anslutningen gjordes med HTTP i stället för med HTTPS. (NEO-26720)
* Korrigerade ett problem för MSSQL-databasen där ett fel kunde uppstå med proceduren up_updatestats under rensningsarbetsflödet.
* Korrigerade en krasch som inträffade när webbprocessen stängdes av om interaktionsbegäranden fortfarande bearbetades. (NEO-26447)
* Ett problem har korrigerats där funktionen **NoNull** i Oracle DB inte längre fungerade efter uppgradering 9032. (NEO-26488)
* Korrigerade ett problem där spårningsarbetsflödet misslyckades efter uppgradering 9171 om LINEV2-paketet installerades utan Message Center-paketet.
* Korrigerade ett skalbarhetsproblem som förhindrade att anslutningspoolen utökades till det önskade antalet anslutningar eftersom databasanslutningssträngen för attributet APP slutade att få ett ogiltigt värde. (NEO-25105)
* Ett fel på proxykonfigurationsnivån som förhindrade dig från att logga in på Adobe Campaign efter den senaste Windows 10-uppdateringen har åtgärdats. (NEO-27813)
* Korrigerade ett problem som gjorde oönskade URL:er synliga i de levererade e-postmeddelandena efter import av HTML-mallar med spårningslänkar. (NEO-25909)
* Korrigerade ett problem som gjorde att servern kraschade när måldata för resten visades från en **delad** aktivitet i ett arbetsflöde.
* Korrigerade ett serverkraschproblem genom att förhindra minnesfel när uttrycksparsern rensades. (NEO-26856)
* Korrigerade ett problem i anrikningsaktiviteten där icke-adminanvändare definierade instansvariabler. (NEO-25653)