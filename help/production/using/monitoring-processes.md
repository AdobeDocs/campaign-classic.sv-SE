---
product: campaign
title: Övervaka processer
description: Lär dig övervaka Campaign-processer
feature: Monitoring
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1f5d8c7e-6f9b-46cd-a9b4-a3b48afb1794
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '3643'
ht-degree: 0%

---

# Övervaka processer{#monitoring-processes}


Programservern och omdirigeringsservern (**tracking**) kan övervakas manuellt eller automatiskt.

## Manuell övervakning {#manual-monitoring}

Gå till fliken **[!UICONTROL Monitoring]** och klicka på länken **[!UICONTROL Overview]** för att komma åt sidan för processövervakning i Adobe Campaign.

![](assets/d_ncs_monitoring.png)

På den sida som visas kan du visa den anslutna instansens tillstånd, dvs:

* Information om instansen: version, namn, databasmotor, installerade paket, serversystemsindikatorer.
* En förteckning över saknade processer och körningsinformation (startdatum, PID osv.).
* en översikt över arbetsflöden och leveranser.

Ytterligare sätt att övervaka Campaign-processer presenteras på [den här sidan](../../production/using/monitoring-guidelines.md).

### Loggjournal {#log-journal}

Om du vill visa loggjournalen som hör till en process klickar du på processen, till exempel **mta**, och väljer sedan **[!UICONTROL Open the log journal]** .

![](assets/d_ncs_monitoring2.png)

### Systemindikatorer {#system-indicators}

Bläddra till listan med systemindikatorer för att visa information om datorn, till exempel dess fysiska och virtuella minne, aktiva processer och tillgängliga diskutrymme. Indikatorer är olika för Linux och Windows. Gå till sidan **[!UICONTROL Instance Monitoring]** och klicka på länken **[!UICONTROL Display]** för att öppna listan med indikatorer.

#### Windows {#in-windows}

* **[!UICONTROL Pending events queued]**: indikator som är specifik för **Meddelandecenter**. [Läs mer](../../message-center/using/additional-configurations.md#monitoring-thresholds)

* **[!UICONTROL Memory]**: information om det fysiska minnet (RAM).

  **[!UICONTROL Current value]**: aktuell minnesförbrukning.

  **[!UICONTROL Max Value]**: Total mängd installerat minne.

  **[!UICONTROL Available]**: Mängd tillgängligt minne.

  **[!UICONTROL Warning]**: den här indikatorn visas när minnesförbrukningen når 80 % av den totala mängden.

  **[!UICONTROL Alert]**: den här indikatorn visas när minnesförbrukningen når 90 % av den totala mängden.

  När indikatorerna **[!UICONTROL Warning]** och **[!UICONTROL Alert]** visas kan du lösa problemet genom att lägga till RAM-minne på den dator där Adobe Campaign-servern är installerad. Du kan också välja att installera Adobe Campaign-servern på en dedikerad dator.

* **[!UICONTROL Swap Memory]**: Information om det virtuella minnet som matchar en växlingsfil: ett område på hårddisken som används som om det vore RAM.

  **[!UICONTROL Current value]**: faktisk minnesförbrukning.

  **[!UICONTROL Max Value]**: Total mängd minne.

  **[!UICONTROL Available]**: Mängd tillgängligt minne.

  **[!UICONTROL Warning]**: den här indikatorn visas när minnesförbrukningen når 80 % av den totala mängden.

  **[!UICONTROL Alert]**: den här indikatorn visas när minnesförbrukningen når 90 % av den totala mängden.

  När indikatorerna **[!UICONTROL Warning]** och **[!UICONTROL Alert]** visas kan du lösa problemet genom att öka storleken på utbytesfilen i de avancerade Windows-inställningarna.

* **[!UICONTROL Disk XXX]**: information om datorläsare.

  **[!UICONTROL Current value]**: diskutrymme som faktiskt används.

  **[!UICONTROL Max Value]**: total diskkapacitet.

  **[!UICONTROL Available]**: ledigt diskutrymme.

  **[!UICONTROL Used]**: procentandel av disken som används.

  **[!UICONTROL Warning]**: den här indikatorn visas när det tillgängliga diskutrymmet når 80 % av den totala kapaciteten.

  **[!UICONTROL Alert]**: den här indikatorn visas när det tillgängliga diskutrymmet når 90 % av den totala kapaciteten.

* **[!UICONTROL Number of processes too old]**: information om Adobe Campaign-processer som har varit aktiva i mer än en dag.

  **[!UICONTROL Current value]**: antal aktiva processer.

  **[!UICONTROL Max Value]**: maximalt antal auktoriserade processer (1).

  **[!UICONTROL Alert]**: den här indikatorn visas om antalet processer är lika med 1.

  När indikatorn **[!UICONTROL Alert]** visas kan det bero på att den aktuella processen har låsts av SQL-databasmotorn eller att den har fastnat i en oändlig slinga. Processen **watchdog** som tillhandahålls av Adobe Campaign startar automatiskt om alla processer varje dag och gör att du kan lösa det här problemet. Du kan också stoppa den berörda processen själv för att tvinga fram en omstart.

#### Linux {#in-linux}

![](assets/production_system_indicators_linux_001.png)

* **[!UICONTROL Pending events queued]**: indikator som är specifik för **Meddelandecenter**. Mer information finns i [det här avsnittet](../../message-center/using/additional-configurations.md#monitoring-thresholds).

* **[!UICONTROL Load average (1/5/15 minutes)]**: information om belastningen, dvs. processorns användningshastighet för processer som körs på datorn under de senaste minuterna, fem minuter eller femton minuter

  **[!UICONTROL Current value]**: faktisk inläsning av datorn.

  **[!UICONTROL Max value]**: maximal användningsbelastning för processerna på datorn

  **[!UICONTROL Warning]**: den här indikatorn visas när inläsningen når 80 % av det högsta tillåtna värdet under den senaste minuten, fem minuter eller femton minuter.

  **[!UICONTROL Alert]**: den här indikatorn visas när inläsningen når 90 % av det högsta tillåtna värdet för den sista minuten, fem minuter eller femton minuter.

* **[!UICONTROL Memory]** information om det fysiska minnet (RAM).

  **[!UICONTROL Current value]**: faktisk minnesförbrukning.

  **[!UICONTROL Max Value]**: Total mängd installerat minne.

  **[!UICONTROL Available]**: Mängd tillgängligt minne.

  **[!UICONTROL Warning]**: den här indikatorn visas när minnesförbrukningen når 80 % av den totala mängden.

  **[!UICONTROL Alert]**: den här indikatorn visas när minnesförbrukningen når 90 % av den totala mängden.

  När indikatorerna **[!UICONTROL Warning]** och **[!UICONTROL Alert]** visas kan du lösa problemet genom att lägga till RAM-minne på den dator där Adobe Campaign-servern är installerad. Du kan också välja att installera Adobe Campaign-servern på en dedikerad dator.

* **[!UICONTROL Swap Memory]**: Information om det virtuella minnet som matchar en växlingsfil: ett område på hårddisken som används som om det vore RAM.

  **[!UICONTROL Current value]**: faktisk minnesförbrukning.

  **[!UICONTROL Max Value]**: Total mängd minne.

  **[!UICONTROL Available]**: Mängd tillgängligt minne.

  **[!UICONTROL Warning]**: den här indikatorn visas när minnesförbrukningen når 80 % av den totala mängden.

  **[!UICONTROL Alert]**: den här indikatorn visas när minnesförbrukningen når 90 % av den totala mängden.

  När indikatorerna **[!UICONTROL Warning]** och **[!UICONTROL Alert]** visas kan du lösa problemet genom att öka storleken på utbytesfilen.

* **[!UICONTROL Core Files]**: information om de filer som genererats efter krasch i en Adobe Campaign-process. Med de här filerna kan du diagnostisera orsaken till kraschen.

  **[!UICONTROL Current Value]**: antal befintliga filer.

  **[!UICONTROL Max Value]**: maximalt antal tillåtna filer (1).

  **[!UICONTROL Warning]**: den här indikatorn visas när antalet filer blir 1.

  **[!UICONTROL Alert]**: den här indikatorn visas när antalet filer är lika med 1.

  När en process saknas på grund av en krasch visas den i rött i listan över processer och startas om automatiskt av den **watchdog** -process som tillhandahålls av Adobe Campaign.

* **[!UICONTROL Number of shared memory segments]**: information om de minnessegment som delas av alla Adobe Campaign-processer.

  **[!UICONTROL Current value]**: antal minnessegment som används för närvarande.

  **[!UICONTROL Max Value]**: maximalt antal tillåtna minnessegment (2).

  **[!UICONTROL Warning]**: den här indikatorn visas när antalet minnessegment når 1.

  **[!UICONTROL Alert]**: den här indikatorn visas när antalet minnessegment når 2.

* **[!UICONTROL Number of processes too old]**: information om processer som har varit aktiva i över en dag.

  **[!UICONTROL Current value]**: antal aktiva processer.

  **[!UICONTROL Max Value]**: maximalt antal auktoriserade processer.

  **[!UICONTROL Warning]**: den här indikatorn visas när antalet processer når 80 % av det tillåtna tröskelvärdet.

  **[!UICONTROL Alert]**: den här indikatorn visas när antalet processer når 90 % av det tillåtna tröskelvärdet.

* **[!UICONTROL File Handles]**: information om filbeskrivningarna, dvs. antalet filer som öppnas per process.

  **[!UICONTROL Current value]**: aktuellt antal filbeskrivare.

  **[!UICONTROL Max Value]**: maximalt antal filbeskrivare som tillåts av operativsystemet.

  **[!UICONTROL Warning]**: den här indikatorn visas när antalet auktoriserade filbeskrivare når 80 %-tröskelvärdet.

  **[!UICONTROL Alert]**: den här indikatorn visas när antalet auktoriserade filbeskrivare når tröskelvärdet på 90 %.

* **[!UICONTROL Processes]**: information om datorprocesserna.

  **[!UICONTROL Current value]**: antal aktiva processer.

  **[!UICONTROL Max Value]**: maximalt antal auktoriserade processer.

  **[!UICONTROL Active Processes]**: antal aktiva processer.

  **[!UICONTROL Inactive Processes]**: antal inaktiva processer.

  **[!UICONTROL Warning]**: den här indikatorn visas när antalet auktoriserade processer når 80 %-tröskelvärdet.

  **[!UICONTROL Alert]**: den här indikatorn visas när antalet auktoriserade processer når tröskelvärdet på 90 %.

* **[!UICONTROL Zombie Processes]**: information om processer som har stoppats men fortfarande har en process-ID (PID) och som fortfarande är synlig i processtabellen.

  **[!UICONTROL Current value]**: antal zoomprocesser som för närvarande är aktiva.

  **[!UICONTROL Max Value]**: maximalt antal auktoriserade zombieprocesser (2).

  **[!UICONTROL Warning]**: den här indikatorn visas när antalet zoomprocesser närmar sig 2.

  **[!UICONTROL Alert]**: den här indikatorn visas när antalet zombieprocesser når 2.

#### Anpassa indikatorer {#customized-indicators}

Med Adobe Campaign kan du anpassa indikatorerna enligt nedan:

1. Skapa en **.sh**-fil och ge den namnet **[!UICONTROL cust_indicators.sh]** .
1. Lägg till anpassade indikatorer i den här filen. Exempel:

   ```
   #!/bin/bash 
   echo "<indicator name='Zombie Processes'>  
   <current label='Current Value' value='0' display=''/>  
   <warning value='2'/>  <alert value='2'/>  
   <max label='Max Value' value='2'/>
   </indicator>"
   ```

   eller

   ```
   #!/bin/bash 
   echo "<indicator name='Availability'>  
   <current label='Last update of data' display='2012-09-03 10:00'/>  
   <current label='Availability last month' display='100.00%'/>  
   <current label='Availability this month' display='100.00%'/> 
   <current label='Recent downtime periods' display='2012-07-04 11:10:00 - 11:19:59'/>
   </indicator>"
   ```

1. Spara filen i mappen **[!UICONTROL usr/local/neolane/nl6]**.

Filen anropas av Adobe Campaign.

## SMTP-rapporter {#smtp-reports}

Rapporterna om övervakning av SMTP-leveranser är integrerade i Adobe Campaign. De kan nås via konsolen eller via webben.

Dessa rapporter visar SMTP-leveransstatistik och SMTP-fel per domän. Operatorn måste ha **administratörsbehörighet** för att få åtkomst till dem.

De grupperas under **Övervakning** > SMTP-övervakning.

![](assets/smtp_reports_access.png)

>[!IMPORTANT]
>
>* Information om SMTP-övervakning är bara tillgänglig om e-postkanalen har aktiverats.
>* **[!UICONTROL SMTP sending statistics]** erbjuds bara om statistikservern har startats på instansen.
>

### Sändningsstatistik för SMTP {#smtp-sending-statistics}

Med rapporten **[!UICONTROL SMTP sending statistics]** kan du styra serveraktiviteten. Den visar en syntes av varje dator.

![](assets/smtp_stats_report.png)

Listan över indikatorer för den här rapporten visas under diagrammet.

1. Totalt antal skickade meddelanden.
1. Representerar in-/utmeddelanden:

   * Blå linje: meddelanden som är klara för att skickas och som anlänt till Shaper, dvs. sista steget innan SMTP skickas (sammanfaller med inkommande data).

   * Grön linje: meddelanden har skickats (sammanfaller med utgående data).

   * Röd linje: meddelanden som överges av Shaper, returnerades till **mta** (sammanfaller med data som underkänns vid den här återställningen).

   Dessa värden uttrycks i antal meddelanden per timme.

1. Representerar två köer i Shaper:

   * Blå kurva: kön med aktiva meddelanden. Dessa meddelanden skickas så snart som möjligt.

   * Kaki-kurva: kön med fördröjda överföringar. Dessa meddelanden kan inte returneras för tillfället på grund av begränsning eller på grund av att det inte finns någon anslutning till målet. Försök görs var femte, tionde, tionde, 20:e, 40:e, 2:a minut, osv. för den definierade **MaxAgeSec**-tiden innan den överges.

1. Diagrammet visar en detalj av övergivna meddelanden (röd kurva i det andra diagrammet): visar andelen meddelanden som överges utan återförsök (mauve) jämfört med meddelanden vars sändning misslyckades (röd). På så sätt kan du visa andelen meddelanden som inte har bearbetats inom den angivna perioden på grund av begränsningar i statistikservern (strypning) eller på grund av att fjärrservern inte är tillgänglig.
1. SMTP-anslutningar öppnas eller öppnas.
1. Uppskattning av antalet **mtachild**.

>[!NOTE]
>
>Den här rapporten är relaterad till statusen för komponenten Email Traffic Shaper.

### SMTP-fel per domän {#smtp-errors-per-domain}

Med den här rapporten kan du visa leveransfel, under en angiven period, uppdelade efter domän.

>[!NOTE]
>
>Alternativen **minConnectionsToLog**, **minErrorsToLog** och **minMessagesToLog** i filen **serverConf.xml** definierar de tröskelvärden över vilka anslutningsstatistik ska beaktas.

![](assets/smtp_error_report.png)

Förteckningen över indikatorer för denna rapport visas under tabellen.

* Kolumnen **Domän** innehåller namnet på den domän som meddelandena skickas till (eller det riktiga domännamnet, t.ex. yahoo.com för yahoo.fr),
* Kolumnen **Sammanhang** visar antalet SMTP-anslutningar som är öppna för den här domänen,
* Kolumnen **Skickat** motsvarar antalet meddelanden som skickas till den här domänen.
* Kolumnen **Volym** visar mängden meddelanden som har försökt att skickas till den här domänen (ungefärligt värde).
* Kolumnen **Fel** visar en volymindikator för fel i den här domänen under perioden.
* Kolumnen **Senaste svar** visar det senaste SMTP-svarsmeddelandet som tagits emot för den här domänen.
* I kolumnen **Datum** visas datumet för det senaste SMTP-svaret som tagits emot för den här domänen.

>[!NOTE]
>
>Värdena som visas i kolumnerna **Sammanhang**, **Skickat** och **Volym** beräknas med hänsyn till den period som valts i fältet **[!UICONTROL Period]**.

Klicka på ett domännamn för att visa felen.

De kategoriseras av PublicId: den här identifieraren motsvarar en IP-adress som delas av flera Adobe Campaign-datorer bakom en router. Statistikservern använder den här identifieraren för att memorera anslutningen och leveransstatistiken mellan den här startpunkten och målservern.

![](assets/smtp_error_report_details.png)

I fältet **[!UICONTROL Owner of domain]** kan du gruppera olika domännamn under samma etikett. I den inledande rapportvyn kopplas alla MX-domännamn till den här ägaren.

Klicka på en PublicId-identifierare för att visa mer information.

![](assets/smtp_error_report_subdetails.png)

>[!NOTE]
>
>Procentandelen fel representeras av två diagram. Den första är en vågrät förloppsindikator på en svart bakgrund. Det andra diagrammet är kronologiskt. Den markerade perioden delas in i tolv tidsintervall, som alla representeras av en lodrät förloppsindikator. I båda representationerna är stapeln svart om inget fel har identifierats. Färgen på stapeln beror på hur många procent fel som har inträffat (gult, orange och slutligen rött). Färggrått innebär att ingen signifikant datavolym har hittats. Du kan visa den exakta procentandelen fel genom att placera markören i diagrammet.

>[!NOTE]
>
>Mer information om SMTP-fel och hur du hanterar dem i Adobe Campaign finns i [det här avsnittet](../../installation/using/email-deliverability.md).

## Faktureringsrapport {#billing-report}

Det tekniska arbetsflödet **[!UICONTROL Billing]** skickar systemaktivitetsrapporten till faktureringsoperatorn via e-post. Den aktiveras som standard den 25:e varje månad på marknadsinstansen.

Det tekniska arbetsflödet finns i en undermapp till följande nod: **Administration** > **Produktion** > **Tekniska arbetsflöden**.

![](assets/billing.png)

När arbetsflödet har startats var 25:e månad får din faktureringsoperatör följande rapport i sin inkorg.

![](assets/billing_2.png)

Följande mätvärden finns för att spåra dina leveranser:

* **[!UICONTROL Start date]** : Startdatum för leveransen. Observera att det kan vara tidigare än rapportens &quot;från&quot;-datum.
* **[!UICONTROL Label]** : Etikett på leveransen. Leveranser som har färre än 100 meddelanden att skicka anses vara för små och aggregeras därför efter startdatum. I så fall visas antalet aggregat i etiketten, t.ex. [Sammanläggning av 3 små leveranser].
* **[!UICONTROL Total volume]** : Total volym byte som överförts för leveransen.
* **[!UICONTROL Avg volume]** : Genomsnittlig volym överförda byte. Detta är resultatet av följande formel **(total volym/meddelanden)**, som är beräkningsgrunden för måttet **[!UICONTROL Multiplier]**.
* **[!UICONTROL Messages]** : Antal skickade meddelanden. Detta inkluderar både meddelanden som har skickats och försök igen (efter att ett studsmeddelande har tagits emot från den kontaktade servern).
* **[!UICONTROL Multiplier (x)]** : Värdet för multiplikatorn dras från meddelandets genomsnittliga volym.
* **[!UICONTROL Count]** : Resultat av multiplikationen av meddelandena och multiplikatorn.

## Automatisk övervakning {#automatic-monitoring}

Adobe Campaign erbjuder flera automatiska övervakningsmetoder som visas nedan.

### Kommandorad {#command-line}

Kommando

**nlserver monitor**

Här kan du visa en lista med indikatorer för Adobe Campaign-modulerna och systemet.

Det genererar utdata i ett enkelt bearbetat XML-format.

Det här kommandot kan också köras med parametern **-missing** som listar de processer som saknas i den här instansen när konfigurationsfilerna anger att de ska köras.

```sql
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
mta@prod
stat@prod
wfserver@prod
```

### Information som publiceras av servern {#information-published-by-the-server}

#### /r/test {#r-test}

Sidan **http(s)://`<application>`/r/test** används för att testa omdirigeringsservern. Vi rekommenderar att du använder samma metod för att testa frontservrarna som används för spårning. Den här sidan kan också användas för att testa en lastdispatcher.

Här visas en rad som den här i XML-format:

```
<redir status='OK' date='YYYY-MM-DD HH:MM:SS.112Z' build='XXXX' host='<hostname>' localHost='<servername>'/>
```

**Frekvens**: Det här testet använder ingen inläsning och kan därför köras mycket ofta (t.ex. en gång i sekunden).

#### /nl/jsp/ping.jsp {#nl-jsp-ping-jsp}

Den här **http(ar)://`<Application server url>`/nl/jsp/ping.jsp**-sidan fungerar på samma sätt som nätverkets motsvarighet: den testar en fullständig fråga som går igenom apache/tomcat/web module/database och överför till klienten. Om allt fungerar som det ska returneras&quot;OK&quot;. Vi rekommenderar att du kör det här testet på datorer med tillgång till databaser (t.ex. matriser och enkäter).

**Användning**: En sessionstoken som är associerad med en operatorinloggning måste skickas som ett argument för att fjärrinloggning ska kunna ske (se tipset i [Automatisk övervakning via Adobe Campaign-skript](#automatic-monitoring-via-adobe-campaign-scripts)).

Exempel:

![](assets/ncs_monitoring_ping.png)

Operatornamnet och inloggningen måste tidigare konfigureras i Adobe Campaign klientkonsol med databasbehörighet.

![](assets/ncs_operators_rights_01.png)

**Frekvens**: Detta är ett test som använder mycket liten bandbredd. Den kan därför köras ganska ofta, men inte mer än en gång per minut.

#### /nl/jsp/monitor.jsp {#nl-jsp-monitor-jsp}

Detta är ett test för att kontrollera att en operatör kan komma åt Adobe Campaign-servern via en webbsida, samma webbsida som den som nås via klientkonsolmenyerna. Du kan ringa upp den här sidan från dina övervakningsverktyg (Tivoli, Nagios, etc.).

![](assets/ncs_monitoring_web.png)

**Användning**: En sessionstoken som är associerad med en användarinloggning, som gör att du kan ansluta till instansen, måste användas som ett argument (se tipset i [Automatisk övervakning via Adobe Campaign-skript](#automatic-monitoring-via-adobe-campaign-scripts)).

Operatorn och inloggningen måste konfigureras tidigare i Adobe Campaign klientkonsol med rätt databasbehörighet och databasbegränsningar.

**Frekvens**: Detta är ett fullständigt servertest och behöver inte köras ofta (det kan till exempel utföras en gång var tionde minut).

#### /nl/jsp/soaprouter.jsp {#nl-jsp-soaprouter-jsp}

Detta **jsp** representerar startpunkten för Adobe Campaign API:er. Den kan därför ge detaljerad övervakning av ansökan. Den kan också användas för att övervaka Adobe Campaign webbtjänster. Det används i våra övervakningsskript, men observera att det endast är för avancerade användare.

### Övervakning baserad på distributionstyper {#monitoring-based-on-deployment-types}

Adobe Campaign aktiverar olika distributionskonfigurationer (mer information finns i [det här avsnittet](../../installation/using/hosting-models.md)). I det här avsnittet beskrivs de olika automatiska övervakningstekniker som ska användas beroende på vilken typ av installation du har.

<table> 
 <thead> 
  <tr> 
   <th> Distributionstyp </th> 
   <th> Övervakning </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Fristående </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> och <span class="uicontrol">/nl/jsp/monitor.jsp</span> på Adobe Campaign-servern</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Standard </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> och <span class="uicontrol">/nl/jsp/ping.jsp</span> på frontservrarna</p> </li> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> på programservern</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Enterprise </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/r/test</span> och <span class="uicontrol">/nl/jsp/ping.jsp</span> på frontservrarna</p> </li> 
     <li><p> <span class="uicontrol">/r/test</span> och <span class="uicontrol">/nl/jsp/monitor.jsp</span> på programservern</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> Mid-sourcing </td> 
   <td> 
    <ul> 
     <li><p> <span class="uicontrol">/nl/jsp/monitor.jsp</span> på programservern</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Automatisk övervakning via Adobe Campaign-skript {#automatic-monitoring-via-adobe-campaign-scripts}

Adobe Campaign kan tillhandahålla ett instansövervakningsverktyg (netreport) som gör att du kan skicka en rapport via e-post om de identifierade avvikelserna.

![](assets/pro_netreport.png)

>[!IMPORTANT]
>
>Det här verktyget kan användas för att övervaka dina instanser, men stöds inte av Adobe Campaign. Kontakta er Campaign-administratör om du vill ha mer information.

### Obligatoriska element {#required-elements}

Följande förinstallationsanvisningar krävs för automatisk övervakning:

* Du måste ha filerna **netreport.tgz** (Linux-installation) eller **netreport.zip** (Windows-installation),
* Vi rekommenderar att du inte installerar övervakning på den dator som ska övervakas,
* Den måste vara installerad på en dator med JRE eller JDK.
* i Linux måste datorn som ska övervakas ha paketet **bc**. Mer information om detta finns i [det här avsnittet](../../installation/using/installing-packages-with-linux.md#distribution-based-on-rpm--packages).

### Installationsprocedur {#installation-procedure}

Installationsproceduren är följande:

1. I konsolen skapar du en ny operator om det behövs (övervakningsanvändaren finns redan), men tilldelar inga rättigheter.
1. Kör arkivextrahering.
1. Läs filen **Viktigt**.
1. Uppdatera konfigurationsfilen **netconf.xml**.
1. Uppdatera filen **netreport.bat** (Windows) eller **netreport.sh** (Linux).

### Konfigurera filen netconf.xml {#configuring-the-netconf-xml-file}

XML-konfigurationsfilen innehåller följande element:

* [Elementet &#39;Egenskaper&#39;](#properties--element)
* [Instance-element](#instance--element)
* [Värdelement](#host--element)
* [Underelement](#sub-elements)

Här är ett konfigurationsexempel:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<netconf>
  <properties mailServer="mail.adobe.net" mailFrom="mail@adobe.com" recipientList="recipient@adobe.com">
    <nightMode start="00:00 am" end="07:00 am"/>
    <buildRange minimum="7829" maximum="8180"/>
    <buildRange minimum="8300" maximum="8400"/>
    <sla/>
  </properties>

  <instance name="dev" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devrd.domain.com" alias="devrd" sessiontoken="monitoring" criticalLevel="1" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="false" isSecure="false"/>
                                <redir url="/r/test"/>
                                <http url="/nl/jsp/ping.jsp"/>
                </host>
                <host name="devtrk.domain.com" alias="devtrk" sessiontoken="monitoring" criticalLevel="0" filter="wkf;new">
                                <ncs instance="devrd" url="/nl/jsp/soaprouter.jsp" includeDead="true" isSecure="false"/>
                </host>
  </instance>
  <host name="dev-test" alias="dev-test" sessiontoken="monitoring" criticalLevel="2">
                <ncs instance="dev" url="/nl/jsp/soaprouter.jsp" includeDead="false"/>
  </host>
</netconf>
```

>[!NOTE]
>
>Du kan ange olika konfigurationer genom att lägga till ett suffix till filen **netconf.xml**, till exempel **netconf-dev.xml**, **netconf-prod.xml** osv. Ange sedan den konfiguration som ska användas för att köra netreport i filerna **netreport.bat** eller **netreport.sh** genom att till exempel lägga till **$JAVA_HOME/bin/java netreport dev** eller **@%JAVA_HOME%binjava netreport prod** .

>[!IMPORTANT]
>
>För att operatorn **monitoring** ska fungera måste datorn som netreport körs på finnas i en säkerhetszon i läget **sessionTokenOnly**. Om ingen betrodd IP-mask har angetts för den här operatorn måste säkerhetszonen också vara i läget **allowEmptyPassword** och **allowUserPassword** .

#### Elementet &#39;Egenskaper&#39; {#properties--element}

Det här elementet används för att fylla i konfigurationen av e-postmeddelanden, dvs.

* **mailServer**: SMTP-server som används för att skicka e-post (t.ex. smtp.domain.net).
* **mailFrom**: rapportavsändarens e-postadress (t.ex.: monitoring@domain.net).
* **receiveList**: listan med e-postadresser för att övervaka mottagare. Adresser måste avgränsas med kommatecken (inga blanksteg).
* Läget **night** (valfritt) används för att undvika att skicka e-post mellan den angivna tidsperioden. I stället konsolideras data och ett e-postmeddelande om nattens aktivitet skickas efter sluttiden (7:00 som standard).
* Med underelementet **buildRange** (valfritt) kan du ange ett lägsta och högsta build-nummer. Ett fel genereras för alla datorer vars build-nummer inte faller inom detta intervall

  ```
  <buildRange minimum="0000" maximum="9999"/>
  ```

* Du kan lägga till ett **`<sla>`**-underelement (valfritt) i elementet **properties**. En loggfil genereras varje gång netreport körs. Namnet på filen innehåller konfigurationsnamnet samt datum och tid, till exempel **dev_06_12_13_16_47_05.tmp**. Filen innehåller följande information: instansnamn, datornamn, allvarlighetsgrad, (0 till 3, från minst kritisk till mest kritisk), datum (tidsstämpelformat), förfluten tid (i millisekunder) mellan frågan och svaret, vilken tjänst som används (http, ncs, ncsex, redir). Den här informationen avgränsas av tabellmärken och radbrytningar i slutet av varje tjänst.

>[!NOTE]
>
>Attributet **persistHtmlFile** med värdet &quot;true&quot; för elementet **`<property>`** används för att registrera den senaste övervakningsstatusen i filen **netreport.md**. Filen sparas i installationskatalogen.

#### Instance-element {#instance--element}

Med det här elementet kan du gruppera om flera datorer (värdar) till samma instans. Instansnamnen visas i den första delen av övervakningsmeddelandet. Du kan klicka på namnet på en instans för att få information om varje dator.

```
instance name="instance-name" recipientList="mail@mail.com,mail2@mail.com">
                <host name="devcamp.domain.com" ...>
                       ...
                </host>
                <host name="devtrack.domain.com" ...>
                       ...
                </host>
</instance
```

* **name**: instansnamn som visas i den första delen av e-postmeddelandet.
* **receiveList** (valfritt): gör att du kan skicka en övervakningsrapport om en viss instans via e-post.

#### Värdelement {#host--element}

Detta element konfigurerar övervakningen av en viss server på värden, dvs.

* **namn**: namnet på datorn som ska övervakas.
* **alias** (valfritt): namnet på den övervakade datorn så som den kommer att visas i rapporten.
* **sessionToken**: tillhandahåller inloggningsautentisering via en auktoriserad sessionstoken.

  Om du vill konfigurera sessionstoken väljer du operatorn **övervakning** i Adobe Campaign-konsolen. På fliken **Åtkomstbehörighet** anger du IP-adresserna till datorerna som har behörighet att övervaka den här instansen. Du kan sedan ansluta till övervakningssidan från dessa datorer med hjälp av identifieraren **monitoring** och utan att behöva ange ett lösenord.

  ![](assets/ncs_operators_rights_02.png)

* **criticalLevel** (valfritt): gör att du kan sortera fel som ska visas efter allvarlighetsgrad. Möjliga värden är &#39;0&#39; (alla nivåer visas), &#39;1&#39; (endast stora och kritiska fel visas) och &#39;2&#39; (endast kritiska fel visas). Om det här attributet inte anges visas alla felnivåer.
* **filter** (valfritt): gör att du kan utesluta vissa arbetsflödesfel, till exempel **filter=&quot;wkf;wkf1&quot;**. Arbetsflödesetiketter måste separeras med semikolon.

#### Underelement {#sub-elements}

* **tcp**: kontrollerar om servern är upp eller ned. Du måste ange ett portnummer.
* **http**: kontrollerar att webbservern finns (programservern fungerar).
* **ncs**: kontrollerar processerna för instansen som anges i instansattributet (arbetsflödesfel, minnesanvändning osv.). Attributet **included** (mandatory) ger dig möjlighet att visa döda processer (&#39;true&#39; eller &#39;false&#39;-värden).
* **redir**: kontrollerar spårningen.

I de flesta fall kan endast underelementen **ncs** och **redir** behållas.

I alla fall kan vissa noder överlagras i underelementen (t.ex. noden **port=75** för att överlagra porten som används för http-, ncs- eller redir-anslutningen):

```
<ncs instance="clap40" url="/nl/jsp/soaprouter.jsp" includeDead="false" port="80"/>
```

I underelementen **ncs**, **redir** och **http** kan du lägga till attributet **isSecure** (valfritt) för att välja om du vill använda https-protokollet (&#39;true&#39; eller &#39;false&#39;). Om attributet inte anges används http-protokollet.

### Konfigurera filen netreport.bat eller netreport.sh {#configuring-the-netreport-bat-or-netreport-sh--file}

Om du vill konfigurera den redigerar du den här filen och anger vilken katalog som JRE eller JDK är installerad i.

### Startar övervakning {#launching-monitoring}

Kör filen **netreport.bat** eller **netreport.sh** med regelbundna intervall via ett skript för att starta övervakning. En rapport skickas efter den första körningen och sedan endast om statusen ändras.

### Testövervakning {#testing-monitoring}

Testa övervakningen genom att köra filen **netreport.bat** eller **netreport.sh**.

Ett e-postmeddelande skickas till mottagarna som anges i **mottagarlistan** i filen **netconf.xml**.
