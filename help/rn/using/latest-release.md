---
title: Senaste versionen
description: Senaste versionen
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
source-git-commit: e3e8802aae0d10befcf9eef1ccf720f82c460038
workflow-type: tm+mt
source-wordcount: '1739'
ht-degree: 0%

---


# Senaste versionen{#latest-release}

[Uppgradering](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html) | [Kontrollpanelsversioner](https://docs.adobe.com/content/help/en/control-panel/using/release-notes.html) | [Dokumentationsuppdateringar](../../rn/using/documentation-updates.md) | [Tidigare versioner](../../rn/using/release--20-1.md) | [Föråldrade funktioner](../../rn/using/deprecated-features.md)

<table> 
 <tbody> 
  <tr> 
   <td><img src="assets/do-not-localize/green3.png"/><strong>Allmän tillgänglighet</strong></td>
   <td><img src="assets/do-not-localize/blue3.png"/><strong>Releasedatan</strong></td> 
   <td><img src="assets/do-not-localize/orange3.png"/><strong>Inte längre tillgänglig</strong></td> 
   <td><img src="assets/do-not-localize/red3.png"/><strong>Föråldrat</strong></td> 
  </tr> 
   <tr> 
   <td>Senaste stabila bygge tillgänglig. Bygg validerat i produktion.<br> </td>
   <td>Bygg validerat av Adobe. Väntar på korrektur av produktionen.<br> </td>
   <td>Nyare bygge tillgänglig med felkorrigeringar. Uppdatering krävs.<br> </td>
   <td>Innehåller kända regressioner. Uppdatering är obligatorisk.<br> </td>
  </tr> 
 </tbody> 
</table>

Den **sista stabila versionen** är 9032 (3a9dc9c). Klicka [här](../../rn/using/release--19-1.md#release-19-1-4-build-9032)

## ![](assets/do-not-localize/blue_2.png) Version 20.2.1 - build 9178 {#release-20-2-1-build-9178}

_8 juni 2020_

**Vad är nytt?**

<table> 
 <thead> 
  <tr> 
   <th> <strong>Stöd för uttryckssymboler</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>När du utformar ett meddelande i Campaign kan du nu enkelt infoga uttryckssymboler i meddelandetexten med en dedikerad knapp. De kan också läggas till i e-postens ämnesrad. Du kan anpassa listan med tillgängliga uttryckssymboler i gränssnittet.</p>
    <p>Mer information om hur du lägger till uttryckssymboler finns i den <a href="../../delivery/using/defining-the-email-content.md#inserting-emoticons">detaljerade dokumentationen</a>. Lär dig hur du anpassar uttryckslistan <a href="../../delivery/using/customizing-emoticon-list.md">i det här avsnittet</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Azure Synapse FDA Connector</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Nu kan du ansluta din Campaign-instans till din externa Azure Synapse-databas. Anslutningen hanteras via ett nytt externt konto.</p>
    <p>Azure Synapse är bara tillgängligt för hybridmiljöer och lokala miljöer. Mer information finns i den <a href="../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse">detaljerade dokumentationen</a>.</p>
   </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Sekretesslagar för Thailand och Brasilien</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Thailand’s Personal Data Protection Act (PDPA) är den nya integritetslagen som harmoniserar och moderniserar dataskyddskraven för Thailand. </p>
   <p>Brasiliens Lei Geral de Proteção de Dados (LGPD) börjar gälla från och med 16 augusti för alla företag som samlar in eller behandlar personuppgifter i Brasilien.</p>
   <p>Dessa regler gäller Adobe Campaign-kunder som lagrar data för registrerade i dessa länder. Förutom de sekretessfunktioner som redan finns i Campaign (inklusive samtyckeshantering, datalagringsinställningar och användarroller) tar vi tillfället i akt att inkludera ytterligare funktioner för att underlätta din beredskap för PDPA och LGPD:</p>
   <ul> 
     <li><p>Rätt till åtkomst och rätt att ta bort: vi utnyttjar de funktioner som tillkommit för GDPR och CCPA. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">Läs mer</a></p></li> 
     <li> <p>När du skapar en sekretessbegäran med Campaign-gränssnittet eller API:t väljer du nu <strong>regeltypen</strong> : PDPA, LGPD, GDPR, CCPA. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ManagingPrivacyRequests">Läs mer</a>.</p></li>
    </ul>
   </td> 
  </tr> 
 </tbody> 
</table>

**Säkerhetsförbättringar**

* Förbättrad säkerhet för spårning av länkar i e-postmeddelanden är aktiverat som standard för alla kunder. Det finns ytterligare en förbättrad säkerhetsfunktion som du kan aktivera genom att kontakta Kundtjänst. Mer information om funktionen och stegen för icke-värdbaserade kunder för att aktivera den finns i checklistan [för](https://helpx.adobe.com/campaign/kb/acc-security.html)säkerhet och sekretess. (NEO-24232)

* För att optimera säkerheten har den MD5-hash-algoritm som används för att generera filnamn förstärkts med sha256 för filöverföring. (NEO-17044)

* För att förstärka säkerheten mot XSS-attacker inaktiveras klientskript när en spegelsida körs. (NEO-17987)

* Ett problem som hindrade det tekniska arbetsflödet för rensning av **sekretessbegäran** från att ta bort avstämningsdata har åtgärdats. (NEO-25168, NEO-21004)

* Ett problem med **filöverföringsaktiviteten** som hindrade SFTP-nyckelbaserad autentisering från att fungera i Debian 9 har korrigerats. (NEO-23183)

**Kompatibilitetsförbättringar**

Följande system stöds nu i Campaign:
* Operativsystem: Debian 10
* RDBMS: Oracle 18c och Oracle 19c
* FDA: Azure Synapse Analytics

Läs mer i [Matrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)Kampanjkompatibilitet.

**Förbättringar**

* Transaktionsmeddelanden har förbättrats för en bättre användarupplevelse. Du kan nu avpublicera en transaktionsmeddelandemall som tar bort den från körningsinstanserna. [Läs mer](../../message-center/using/template-unpublication.md).

* Det finns nya alternativ för att ange begränsningar när du skickar e-postmeddelanden som innehåller bilder eller bilagor. Dessa skyddsräcken kan undvika prestandaproblem, vilket är särskilt användbart för transaktionsmeddelanden. [Läs mer](../../installation/using/configuring-campaign-options.md#delivery)

* Med det nya alternativet **Förbered leveransdelarna i databasen** kan leveransförberedelser utföras direkt i databasen, vilket avsevärt kan snabba upp analysen. Det här alternativet är bara tillgängligt för särskilda konfigurationer. [Läs mer](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis). (NEO-23886)

* Prestandan för [CRM Connector-aktiviteten](../../workflow/using/crm-connector.md) för Microsoft Dynamics har förbättrats. (NEO-13303, NEO-12710)

* Versionen för delat minne har ökats.

   >[!WARNING]
   >
   >Denna förbättring kräver ytterligare ett steg efter uppgraderingen. Se avsnittet **Technical Evolutions** nedan.

* Rensningsarbetsflödet har förbättrats. Överblivna arbetstabeller för alla borttagna arbetsflöden tas nu även bort automatiskt i rensningsarbetsflödet. [Läs mer](../../production/using/database-cleanup-workflow.md#cleanup-of-workflow-instances).

* Certifikat för iOS-mobilprogram med iOS HTTP2-anslutning valideras nu innan push-meddelanden skickas, vilket förhindrar att leveranser misslyckas på grund av utgångna certifikat.

* Hanteringen av HTTP-proxyanslutningar har förbättrats. [Läs mer](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration).

**Andra ändringar**

* Äldre SMS-anslutningar är nu föråldrade. Gå till sidan [](../../rn/using/deprecated-features.md)Borttagna funktioner.

* Du kan inte längre använda ditt eget Litmus-konto för att etablera och använda Inkorgsåtergivning i Adobe Campaign. [Läs mer](../../delivery/using/inbox-rendering.md).

* Färgen på visningsnamnen har ändrats från mörkblått till mörkblått cyan för att det ska bli lättare att skilja vyer från mappar. [Läs mer](../../platform/using/access-management.md#about-views)

* Campaign Classic kan nu anslutas till Microsoft Dynamics CRM-konton som finns i regionerna UK, Indien och Kanada. Detta gäller distributionstyperna Office 365 och On Premise (Dynamics 2015).

* Campaign utför nu en TLS-verifiering för att kontrollera att värdnamnet för servern matchar värdnamnet i det angivna certifikatet.

* Tabellen Leverans- och spårningsstatistik visar nu en post per leverans för SMS-kanalen i stället för en post per leveransmottagare.

* Ett felmeddelande har lagts till i loggfilen för att varna användare när den hämtade filen är större än diskutrymmet.

* Följande funktioner är nu tillgängliga för Snowflake-kopplingen: MonthsAgo, DaysAgoInt, ToDateTime, YearsAgo.

**Teknisk utveckling**

Den här nya versionen uppdaterar delat minne och kräver ytterligare steg för att utföra uppgraderingen. Som kampanjadministratör måste du ta bort minnessegment. Dessa steg är obligatoriska eftersom gamla segment förhindrar att nlserver/nlsrvmod startar.

I Windows krävs en omstart av systemet.

På Debian/CentOs krävs delad minnesborttagning. Så här gör du:

Innan du uppgraderar måste du göra följande:

1. Stoppa Apache2-tjänsten (http2 i CentOS) om den körs.
1. Stoppa servertjänsten (nlserver6 för äldre versioner) om den körs.

Efter uppgraderingen:

1. Ta bort det delade minnet med **kommandot ipcrm** om versionen är äldre än den aktuella versionen.
1. Starta nlserver-tjänsten om den körs.
1. Starta Apache2-tjänsten om den körs.

Här är kommandoraden för Debian:

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

**Patchar**

* Korrigerade en mindre regression i rensningsarbetsflödets loggar.
* Korrigerade ett problem i arbetsflödets **inläsningsaktivitet (SOAP)** vid parsning av WSDL-filer.
* Korrigerade ett problem som orsakade ett fel vid uppgradering av ett antal arbetsflöden med en **undersökningsaktivitet** för effektiv bearbetning av ett stort antal arbetsflöden.
* Korrigerade ett intermittent anslutningsproblem under bearbetningen av inMail-meddelanden från Förbättrad MTA. (NEO-20380)
* Korrigerade ett problem som förhindrade att procentvärdena för aktiva klick visades korrekt när bilder visades med en bredd på 100 % i HTML-koden. (NEO-23203)
* Korrigerade ett problem som förhindrade att leveransens villkorliga innehåll visades fullständigt i rapporten med aktiva klick. (NEO-18729)
* Korrigerade ett problem som hoppade över målgodkännandesteget när ett arbetsflöde återupptogs för att skicka en återkommande leverans. (NEO-18166)
* Ett problem som gjorde att **förberedelseknappen** för omstartsmeddelandet inte kunde återuppta leveransen efter att ett fel i arbetsflödet hade åtgärdats har åtgärdats. (NEO-13488)
* Korrigerade ett problem som kunde få leveranser att misslyckas i läget mitt i källkoden under uppfartsfasen, där mottagare med japanska e-postformat ingick i målfasen. (NEO-23846)
* Korrigerade ett problem med tidszonskonvertering med Snowflake Connector (NEO-20105)
* Ett problem med externa konton som använder FTP över SSL har korrigerats. (NEO-20498)
* Korrigerade ett problem som kunde förhindra att bilder visas i radleveranser. (NEO-23207)
* Korrigerade ett problem som orsakade ett fel när ett erbjudande publicerades. (NEO-23312)
* Korrigerade ett problem med push-meddelanden som gjorde att testanslutningar fungerade i mobilprogram, även när certifikatet hade upphört att gälla. (NEO-22991)
* Korrigerade ett problem som kunde påverka push-meddelanden när de skickades med hög frekvens. (NEO-20516)
* Ett problem som gjorde att spårningsdata inkluderade dubbletter trots att spårningsloggarna inte gjorde det har åtgärdats. (NEO-20040)
* Korrigerade ett problem som orsakade att dubbla transaktionsmeddelanden skickades efter att ett kommunikationsfel för spårningsservern korrigerats. (NEO-23640)
* Ett problem som tog bort kodningsparametervärdet vid omdirigering från en spårnings-URL har korrigerats. (NEO-25637)
* Korrigerade ett problem som kunde förhindra att en fråga fungerar när flyttal jämfördes. (NEO-23243)
* Korrigerade ett problem som kunde förhindra att innehållet **Ändrad av** kolumn visas efter att ett arbetsflöde startades om. (NEO-23035)
* Korrigerade ett problem som gjorde att det tekniska arbetsflödet för spårning misslyckades vid hämtning av loggar från en andra behållare. (NEO-23159)
* Korrigerade ett problem som kunde få arbetsflöden att misslyckas när en **anrikningsaktivitet** kördes. (NEO-17338)
* En kontroll har lagts till i **Dubbletter för att behålla** fältet i arbetsflödesaktiviteten **Deduplicering** för att förhindra att null- eller negativa värden anges.
* Guiden **** Schemaläggaren har tagits bort från de återkommande kampanjerna för att undvika omnämnande av timmar och minuter. Endast datum beaktas.
* Korrigerade ett problem med ytterligare lagringsfält när leveranser skapades via alternativet **Beräknad av ett skript** i **skriptarbetsflödesaktiviteten** . (NEO-20609)
* Korrigerade ett problem som förhindrade att spökarbetsflöden togs bort i databasrensningsaktiviteterna.
* Korrigerade ett problem som gjorde att det tekniska arbetsflödet för **fakturering (aktiva profiler)** misslyckades. (NEO-19777)
* Ett problem har korrigerats vid testning av anslutningen för det externa acsDefaultAccount-kontot. (NEO-23433)
* Ett problem som gjorde att du inte kunde skapa ett schematillägg för en primärnyckel med flera kolumner med en Hadoop-tabell har åtgärdats. (NEO-17390)
* Ett problem i **inläsningsaktiviteten (SOAP)** som kunde förhindra att WSDL-filer lästes in från en URL har åtgärdats. (NEO-16924)
* Korrigerade ett problem som förhindrade dig från att utföra ett **ovillkorligt stopp** via konsolen när flera aktiva arbetsflödesservrar lästes in. (NEO-19556)
* Korrigerade en regression som fick rensningsarbetsflödet att krascha.
* Korrigerade ett problem som kunde inträffa när en mall publicerades på en körningsinstans.
* Ett problem som kunde förhindra det tekniska arbetsflödet collectPrivacyRequests har åtgärdats. (NEO-20513, NEO-25169)
* Korrigerade problem som kan inträffa när du försöker ansluta till Audience Manager efter att ha uppgraderat till build 9080. (NEO-20511, NEO-25167)
* Problem som kan uppstå vid export av rapporter i PDF- eller XLS-format har åtgärdats. (NEO-20982, NEO-23493, NEO-23348)
* Korrigerade ett problem som kunde visa en leverans två gånger i leveranslistan efter att den skickades.
* Ett problem med leveransförberedelser som kunde inträffa när routningskonfigurationen var inställd på att skicka leveransen via mellanlagring har åtgärdats.
* Korrigerade ett problem som kunde visa ett felmeddelande när du klickade på en webbprogramlänk i ett radmeddelande.
* Korrigerade ett problem som kunde förhindra Microsoft Dynamics CRM från att hämta alla entiteter. (NEO-24528)
* Korrigerade ett problem som tog bort historiken för aktiviteten **Inkrementell fråga** efter att ha kört rensningsarbetsflödet.
* Ett problem har korrigerats när ett externt konto med mellanleverantörer skapades där alternativet NmsMidSourcing_LastBroadLog_&lt;InternalName> saknades
