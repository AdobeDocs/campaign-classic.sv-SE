---
solution: Campaign Classic
product: campaign
title: Version 20.2
description: Version 20.2
feature: Overview
role: Business Practitioner
level: Beginner
exl-id: fcaab1aa-c8f9-4606-b0d8-eb481a38f588
translation-type: tm+mt
source-git-commit: 1c59afc7021af604559184cd0c21129af3759a8c
workflow-type: tm+mt
source-wordcount: '2970'
ht-degree: 87%

---

# Version 20.2{#release-20-2}

## ![](assets/do-not-localize/green_2.png) Version 20.2.5 – build 9188 {#release-20-2-5-build-9188}

_15 april 2021_

* Korrigerade en klientkonsolregression som orsakade bestående felmeddelanden på IMS-anslutningsskärmen. (NEO-34821)

**Endast konsoluppgraderingen är obligatorisk. Ingen serveruppgradering krävs.**

>[!NOTE]
>
> Anslut till [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/sv/campaign.html) för att hämta den nya versionen. Läs om hur du föreslår en konsoluppdatering för alla slutanvändare [på den här sidan](../../installation/using/client-console-availability-for-windows.md).

_31 mars 2021_

**Förbättringar**

* En förbättring har gjorts för att förhindra krascher vid ogiltiga tvålanrop. Detta kan få instansen att sluta fungera när du försöker köra specifika komplexa frågor. (NEO-28796, NEO-30553)
* Korrigerade en regression som förhindrade att SMS-leveranser med TLS skickades på grund av värdnamnsverifieringen. (NEO-29581)
* Korrigerade ett problem som förhindrade signerad spårning av länkar från att arbeta med vissa e-postklienter. (NEO-28414, NEO-29615)
* Korrigerade en spårnings-ID-sekvens när spårningstaggar för webApp användes, vilket kan orsaka konflikter med duplicerade ID:n. (NEO-27931)
* Ett problem som gjorde att pågående arbetsflöden stoppades av den dagliga omstarten av wfserver har åtgärdats. (NEO-30047)
* Korrigerade ett säkerhetsproblem med API-anrop från icke-adminanvändare när de försökte synkronisera mallar i Adobe Experience Manager. (NEO-32389, NEO-23487)
* Ett problem som gjorde att konsolen kraschade när en leveransdialogruta stängdes för en leverans som skapats med från en mall har åtgärdats. (NEO-31547)
* Ett problem som uppstod när en leverans skapades och sparades på fliken **Mål och arbetsflöde** i en kampanj har korrigerats: förhandsgranskningen misslyckas med följande fel. (NEO-29440)
* Korrigerade ett problem med att Tomcat 8.5 skickade ogiltiga svar som orsakade fel i transaktionsmeddelandeloggar. (NEO-30858)
* Ett regressionsproblem som orsakade minnesfel i extern trådhantering och påverkade prestanda har åtgärdats.
* Korrigerade ett problem som kunde göra att faktureringsarbetsflödet misslyckades när en anpassad målmappning användes. Primärnyckeln för det anpassade schemat lagras i kolumnen&quot;sourceId&quot; som bara tillåter heltalsvärden. Det tillåter nu både heltal och strängvärden. (NEO-25914, NEO-28146)
* Korrigerade en regression som förhindrade användning av vissa komponenter i konsolen, som datumväljaren och bildhantering i leveranser. (NEO-31453)

## ![](assets/do-not-localize/red_2.png) Version 20.2.4 – build 9187 {#release-20-2-4-build-9187}

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
> * Den här versionen inkluderar ett nytt anslutningsprotokoll: Om du ansluter till Campaign via Adobe Identity Service (IMS) är en uppgradering obligatorisk för både Campaign-servern och klientkonsolen för att kunna ansluta till Campaign efter **30 juni 2021**.
> * Den här versionen innehåller en [säkerhetskorrigering](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): Uppgraderingen är obligatorisk för att öka din miljösäkerhet.
> * Om du använder integreringen av Experience Cloud Triggers via oAuth-autentisering måste du gå över till Adobe I/O som beskrivs [på den här sidan](../../integrations/using/configuring-adobe-io.md). Det föråldrade autentiseringsläget med oAuth i Campaign upphör den **30 november 2021**.


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

![](assets/do-not-localize/cp-icon.png) **Ny version av kontrollpanelen i oktober** med domänkonfiguration som använder CNAME och nya funktioner för databasövervakning. [Läs mer](https://docs.adobe.com/content/help/sv-SE/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/red_2.png) Version 20.2.3 – build 9182 {#release-20-2-3-build-9182}

_11 september 2020_

* Korrigerade en regression som gjorde att leveransförberedelser blockerades på grund av en felfunktion på leveransdelen, vilket ledde till överbelastning av minnet. (NEO-27346)
* Korrigerade ett problem med en efteruppgradering som stängde av Apache och webbservern innan webbapplikationens publicering. (NEO-27155)
* Korrigerade en regression i HTML-mallhantering som ledde till att URL:er för spårning blev synliga på grund av en felaktig tolkning av flikar. (NEO-25909)
* Korrigerade ett problem med arbetsflödet för databasrensning som kunde sluta fungera på grund av en ohanterad datakälla. (NEO-23160 och NEO-23364)
* Arbetsflödet för rensning tömmer nu utgångna listor med grupper om 100 i stället för en i taget.
* Korrigerade en regression som förhindrade dig från att ändra det interna namnet på ett externt konto. (NEO-27323)
* Korrigerade en regression under efteruppgraderingen som orsakade en felaktig start av lserver (felloggar).
* Uppdateringshanteringen för delat minne har förbättrats. De ytterligare steg som krävdes i 20.2 behövs inte längre.

## ![](assets/do-not-localize/red_2.png) Version 20.2.2 – build 9180 {#release-20-2-2-build-9180}

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
* Efter bytet till [mekanismen för nytt sekvens-ID](https://helpx.adobe.com/se/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence) publiceras alla webbapplikationer som uppdaterar mottagartabellen på nytt, under efteruppgraderingen.
* Korrigerade en potentiell XSS-sårbarhet i leveransinnehåll. (NEO-17987 och NEO-26073)

![](assets/do-not-localize/cp-icon.png) **Den senaste versionen av kontrollpanelen från juni** med övervakning av aktiva profiler, granskning av deldomänens levererbarhet och hantering av GPG-nycklar. [Läs mer](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html).

## ![](assets/do-not-localize/red_2.png) Version 20.2.1 - build 9178 {#release-20-2-1-build-9178}

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

* Transaktionsmeddelanden har förbättrats för en bättre användarupplevelse. En mall för transaktionsmeddelanden kan nu avpubliceras. Detta tar bort den från körningsinstanserna. [Läs mer](../../message-center/using/template-unpublication.md).

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
* Korrigerade ett problem som kunde inträffa när du försökte ansluta till Audience Manager efter att ha uppgraderat till build 9080. (NEO-20511 och NEO-25167)
* Korrigerade ett problem som kunde uppstå vid export av rapporter i PDF- eller XLS-format. (NEO-20982, NEO-23493 och NEO-23348)
* Korrigerade ett problem som kunde visa en leverans två gånger i leveranslistan efter att den hade skickats.
* Korrigerade ett problem med leveransförberedelser som kunde inträffa när routningskonfigurationen var inställd på att skicka leveransen via mid-sourcing.
* Korrigerade ett problem som kunde visa ett felmeddelande när du klickade på en webbapplikationslänk i ett Line-meddelande.
* Korrigerade ett problem som tog bort aktivitetshistoriken för **Inkrementell fråga** efter att ha kört arbetsflödet för rensning.
* Ett problem har korrigerats när ett externt konto med mid-sourcing skapades där alternativet NmsMidSourcing_LastBroadLog_&lt;InternalName> saknades.
* Korrigerade ett regressionsproblem i databasanslutningen som orsakade att webbservern hela tiden startades om på grund av ett problem med databaskodningen. Detta kan leda till överkonsumtion. (NEO-23264)
