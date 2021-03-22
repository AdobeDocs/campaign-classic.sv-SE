---
solution: Campaign Classic
product: campaign
title: Version 20.1
description: Version 20.1
feature: Översikt
role: Yrkesverksam
level: Nybörjare
translation-type: tm+mt
source-git-commit: 96f5709b4c67d1979286cc1f71069a64435c5c70
workflow-type: tm+mt
source-wordcount: '1505'
ht-degree: 10%

---


# Version 20.1{#release-20-1}

## ![](assets/do-not-localize/limited_2.png) Version 20.1.4 – build 9126 {#release-20-1-4-build-9126}

_22 mars 2021_

* Korrigerade en regression som förhindrade användning av vissa komponenter i konsolen, som datumväljaren och bildupplösning i leveranser. (NEO-31453 och NEO-31454)

**Endast konsoluppgradering är obligatoriskt. Ingen serveruppgradering krävs.**

>[!NOTE]
>
> Anslut till [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) för att hämta den nya versionen. Lär dig hur du föreslår en konsoluppdatering för alla slutanvändare [på den här sidan](../../installation/using/client-console-availability-for-windows.md).

_23 december 2020_

>[!CAUTION]
>
> * Den här versionen innehåller ett nytt anslutningsprotokoll: Om du ansluter till Campaign via Adobe Identity Service (IMS) är uppgradering obligatoriskt för både Campaign-servern och klientkonsolen för att kunna ansluta till Campaign efter den 30 juni 2021 **.**
   >
   > 
* Den här versionen innehåller en [säkerhetskorrigering](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): uppgradering är obligatorisk för att öka din miljösäkerhet.


* Anslutningsprotokollet har uppdaterats för att följa den nya IMS-autentiseringsmekanismen.
* Korrigerade ett säkerhetsproblem för att förstärka skyddet mot problem med SSRF (Server Side Request Forgery). (NEO-27777)

## ![](assets/do-not-localize/red_2.png) Version 20.1.3 – build 9124{#release-20-1-3-build-9124}

_6 maj 2020_

* Ett problem med **filöverföringar** som hindrade SFTP-nyckelbaserad autentisering från att fungera i Debian 9 har korrigerats. (NEO-23183)

## ![](assets/do-not-localize/red_2.png) Version 20.1.2 – build 9123{#release-20-1-2-build-9123}

_13 mars 2020_

* Korrigerade ett problem som förhindrade versionshantering på Red Hat 7-servrar. (NEO-23332)

## ![](assets/do-not-localize/red_2.png) Version 20.1 – build 9122{#release-20-1-build-9122}

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
   <td> <p>Snowflake är ett helt hanterat moln data warehouse som bygger på både lagrings- och beräkningsnivå. Med denna nya kontakt kan Adobe Campaign nu utnyttja Snowflake kraft att utföra Big Data Segmentation. Den här kontakten är tillgänglig för alla kunder, inklusive via Adobe.</p>
    <p>Mer information finns i <a href="../../installation/using/configure-fda-snowflake.md">den detaljerade dokumentationen</a> och <a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/administrating/fda/big-data-segmentation-on-snowflake.html">självstudievideon</a>.</p>
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

* Förbättrad karantänhantering och rensning av tabeller som används av funktionen för push-meddelanden (nms:address och nms:appSubscriptionRcp). I iOS (endast HTTP2-anslutning) hanteras nu inaktiverade tokens på samma sätt som för Android. Inaktiveringsflaggan har nu angetts i tabellen NmsAppSubscriptionRcp. [Läs mer](../../production/using/database-cleanup-workflow.md#subscription-cleanup--nmac-)

* Ett nytt alternativ har lagts till i **JavaScript-koden** och **avancerad JavaScript-kod**-arbetsflödesaktiviteter för att definiera en timeout-period. Detta förhindrar att javascript-körningsfasen körs för länge. Om tidsgränsen överskrids stoppas arbetsflödet. Standardtidsgränsen är 1 timme. [Läs mer](../../workflow/using/sql-code-and-javascript-code.md)

* Leveransanalysen stoppas nu när ingen matchande tillhörighet hittas på mittkällservern, med motsvarande felmeddelande.

* Databasredundans för Postgres stöds nu: när databasservern kraschar och startas om kopplas Campaign nu automatiskt tillbaka till den.

* Vyn **Starta väntande** har lagts till i noden Administration > Granskning > Arbetsflödesstatus. Detta gör att du kan övervaka alla arbetsflöden på instansen som väntar på att startas av processen **operationMgt**. Den här vyn levereras med paketet med marknadsföringskampanjer. [Läs mer](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

**Andra ändringar**

* I Linux används nu en systemenhet för start av servertjänsten i stället för skriptet /etc/init.d/nlserver6. Migreringen till det nya startschemat utförs automatiskt när du installerar 20.1-paketet. /etc/init.d/nlserver6 finns fortfarande men för interaktion med nlserver-tjänsten (start, omstart, stopp osv.) rekommenderar vi att du använder systemctl-kommandot direkt.

* De vanligaste anpassade tabellerna har flyttats från **xtkNewId**-sekvensen till dedikerade sekvenser. [Läs mer](https://helpx.adobe.com/se/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)

* Förbättrade frågeprestanda som kan påverkas av onödiga databasanslutningar.

* Förbättrade prestanda för guiden Databasuppdatering för att göra färre SQL-satser för att optimera svarstiden.

* Hanteringen av databasposter har förbättrats.

* Anslutningspoolens tillförlitlighet har förbättrats, vilket kan förhindra att oväntade anslutningsfel inträffar för ofta.

* Verifieringsreglerna för e-postadresser som skickar en adress till karantän om ett mjukt fel uppstår har förbättrats. [Läs mer](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

* För Debian använder Campaign nu system PCRE-bibliotek när de blir tillgängliga.

* Campaign tillåter nu användning av ett nyare ODBC-systembibliotek.

* En timeout har lagts till i LINE-serverleten när en anslutning öppnas för att läsa in en rik bild. Om det tar för lång tid att läsa in bilden avbryts anslutningen för att undvika flaskhalsar.

**Felkorrigeringar**

* Ett krypteringsfel för kontonycklar har korrigerats när Hadoopet används.

* Korrigerade ett regressionsproblem på grund av implementeringen av SSL-certifieringen som gjorde att användaranslutningen misslyckades på Windows-servern. (NEO-20629)

* Ett problem med den inkrementella frågeaktiviteten vid negativa arbetsflödes-ID:n har korrigerats. (NEO-19779)

* Korrigerade ett kodningsproblem när frågor kördes via Netezza FDA-anslutningen. (NEO-19594)

* Ett problem som orsakade ett fel när metoden POST användes i aktiviteten **Webbhämtning** arbetsflödeshändelse har korrigerats.

* Ett problem med generering av erbjudandeförslag har korrigerats. (NEO-18176)

* Korrigerade ett sidfotsvisningsproblem när webbformulärmallen för hämtning användes.

* Ett problem som orsakade att URL:er i innehållet i kontinuerliga leveranser tolkades har åtgärdats. (NEO-16910)

* Ett problem har korrigerats med fälten **Start** och **End** som inte beräknades när en ny kampanj skapades.

* Korrigerade ett problem med arbetsflödesaktiviteten **Filhämtning** när en URL användes.

* Ett problem har korrigerats vid förhandsgranskning av en importerad lista i en frågeaktivitet i en rapport. (NEO-13119)

* Korrigerade ett fel som visade en föråldrad bild när du valde **Powered by Campaign**-anpassningsblocket i e-postredigeraren.

* Nätverkskommunikationen mellan klienten och servern har förbättrats.

* Ett problem har korrigerats när för många arbetsflöden skapades i samma kampanj. Nu kan du inte skapa fler än 28 arbetsflöden. En varning visas.

* Ett problem har korrigerats vid användning av **Ett urval kolumner** avstämningsalternativ i en **unionsarbetsflödesaktivitet**.

* Korrigerade ett kraschproblem i konsolen som kan inträffa när en skadad anrikningslista används i ett arbetsflöde. (NEO-18096)

* Åtgärdade olika kraschproblem i konsolen som kan uppstå i arbetsflöden (NEO-18010, NEO-18032)

* Korrigerade ett problem som medgav körning av en **extern signal**-arbetsflödesaktivitet även när den inaktiverades. (NEO-17524)

* Ett problem har korrigerats när ett nytt schema skapades.

* Korrigerade ett spårningsproblem när SMS-meddelanden skickades. (NEO-19595)

* Korrigerade ett problem som visade felaktigt målgruppsnummer i leveransindikatorer.

* Korrigerade ett problem som visade felaktiga procentvärden när en beskrivande rapport genererades via en arbetsflödesaktivitet. (NEO-14314)

* Korrigerade ett problem som gjorde att leveransgenomströmningsrapporten visade olika nummer när tidsvyparametern användes. (NEO-11783)

* Ett problem som förhindrade att spårningsindikatorerna för transaktionsmeddelanden uppdaterades i arbetsflödet för spårning har åtgärdats. (NEO-17770)

* Korrigerade ett regressionsproblem som gjorde att webbprocessen kraschade och startades om när ett erbjudande begärdes via SOAP. (NEO-19482)

* Korrigerade ett problem som förhindrade överföring av data till offentliga resurser om överföringskatalogen var en delad fjärrplats. (NEO-19361)

* Ett problem som orsakade att **det tekniska arbetsflödet för att importera målgrupper från Adobe Experience Cloud** inte fungerade korrekt har åtgärdats. (NEO-18463)

* Korrigerade ett problem som förhindrade att leveranser skickades när mallar som importerats från Experience Manager användes. (NEO-17540)

* Korrigerade ett fel som uppstod efter uppgraderingen till build 9032 och förhindrade instansen från att ansluta till FTP-servern via SSL-protokollet. (NEO-20498)

* Ett problem som uppstod när en stor mängd data skulle tas bort, infogas eller uppdateras med aktiviteten **Uppdatera data** i ett arbetsflöde med ett FDA-schema som måldimension har åtgärdats. (NEO-13280)

* Korrigerade ett problem som förhindrade att e-post skickades när det fanns Javascript-kod utanför HTML-innehållstaggen. (NEO-18628)

* Korrigerade ett fel som uppstod när spegelsidan skulle visas från leveransloggarna för ett skickat meddelande. (NEO-17976)

* Ett problem som gjorde att **länken till sidan**-anpassningsblocket inte kunde visas på fliken **Textinnehåll** efter att du klickat på **Importera HTML** i en leverans har åtgärdats. (NEO-17568)

* Felmeddelandet som visas när du klickar på en länk till en spegelsida som har gått ut har klargjorts. (NEO-17340)

* Ett problem som gjorde att vissa knappar inte kunde användas i **skärmen för att skapa**-data har åtgärdats.

* Ett problem som uppstod när en leveransaktivitet schemalades i en instans med Asien/Kolkata som tidszon har åtgärdats. (NEO-20001)

* Ett fel visas nu när en leverans har ett tillhörighetskonfigurationsproblem.

* Ett problem som visade ett felaktigt versionstaggnummer på menyn **Om** har korrigerats.

* Korrigerade ett problem som uppstod när routningskontot skulle uppdateras från egenskaperna för en återkommande leverans i ett arbetsflöde. (NEO-18684)

* Korrigerade ett fel som uppstod vid anslutning till instansen via omdirigeringsmodulen, vilket förhindrade att anslutningen rensades korrekt när den stängdes.
