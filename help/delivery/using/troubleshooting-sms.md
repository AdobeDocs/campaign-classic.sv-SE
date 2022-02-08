---
product: campaign
title: Felsöka SMS
description: Läs mer om felsökning av SMS-kanal
feature: SMS
exl-id: 841f0c2f-90ef-4db0-860a-75fc7c48804a
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '2744'
ht-degree: 0%

---

# Felsökning av SMS {#troubleshooting-sms}

![](../../assets/common.svg)

## Konflikt mellan olika externa konton {#external-account-conflict}

Om instansen har flera SMS-externa konton måste du kontrollera att problem inte orsakas av en konflikt mellan externa konton.

Adobe Campaign behandlar externa konton som icke-närstående enheter.

Om du har flera konton följer du den här proceduren för att isolera det externa konto som orsakar problem:

1. Inaktivera alla externa konton.
1. Aktivera ett externt konto.
1. Försök återskapa problemet.
1. Om det första problemet inte alltid uppstår gör du ett rimligt antal försök innan du sluter.
1. Om problemet inte uppstår med det kontot inaktiverar du det och startar om till steg 2 på nästa konto.

När du har markerat varje konto separat finns det två möjliga scenarier:

* **Problemet uppstod på ett eller flera konton**

   I så fall kan du tillämpa andra felsökningsprocedurer på varje konto separat. Det är bäst att inaktivera andra konton när du diagnostiserar ett konto för att minska nätverkstrafiken och antalet loggar.

* **Problemet uppstod inte när bara ett konto var aktivt vid något tillfälle**

   Du har en konflikt mellan konton. Som tidigare nämnts behandlar Adobe Campaign konton individuellt, men leverantören kan behandla dem som ett enda konto.

   * Du använder olika kombinationer av inloggning och lösenord för alla dina konton.
Du måste kontakta leverantören för att diagnostisera potentiella konflikter hos dem.

   * Vissa externa konton har samma kombination av inloggning och lösenord.
Leverantören kan inte avgöra vilket externt konto som `BIND PDU` kommer från, så de behandlar alla anslutningar från flera konton som ett enda. De kan ha cirkulerat MO och SR slumpmässigt över de två kontona, vilket kan orsaka problem.
Om providern stöder flera korta koder för samma kombination av inloggning och lösenord måste du fråga var den korta koden ska placeras i `BIND PDU`. Observera att den här informationen måste placeras inuti `BIND PDU`och inte i `SUBMIT_SM`, sedan `BIND PDU` är den enda plats där du kan dirigera MO korrekt.
Se [Information i varje typ av PDU](sms-protocol.md#information-pdu) om du vill veta vilket fält som är tillgängligt i `BIND PDU`, vanligtvis lägger du till den korta koden i `address_range`, men det kräver särskild support från leverantören. Kontakta dem för att få veta hur de förväntar sig att skicka flera korta koder oberoende av varandra.
Adobe Campaign stöder hantering av flera korta koder på samma externa konto.

## Problem med externt konto i allmänhet {#external-account-issues}

* Undersök om kopplingen nyligen har ändrats och av vem (markera Externa konton som en grupp).

   ```
   select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
   
   (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
   
   (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
   
   N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
   
   from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
   ```

* Undersök (i /postupgrade directory) om systemet har uppgraderats och när
* Undersök om några paket som påverkar SMS kan ha uppgraderats nyligen (/var/log/dpkg.log).

## Problem med hosting (hosted){#issue-mid-sourcing}

* Om problemet inträffar i en miljö med medelhög källkod måste du se till att leveransloggarna och de breda loggarna skapas och uppdateras på servern med mellanlagring. Om så inte är fallet är detta inte ett SMS-problem.

* Om allt fungerar på mittservern och SMS-meddelanden skickas korrekt, men marknadsinstansen inte uppdateras korrekt, kan du få ett problem med mellansynkronisering.

## Problem vid anslutning till providern {#issue-provider}

* Om `BIND PDU` returnerar ett värde som inte är noll `command_status` ber du leverantören om mer information.

* Kontrollera att nätverket är korrekt konfigurerat så att TCP-anslutningen kan göras till providern.

* Be leverantören kontrollera att de har lagt till IP-adresserna till tillåtelselista i Adobe Campaign-instansen.

* Kontrollera **Externt konto** inställningar. Fråga leverantören vilket värde fälten har.

* Om anslutningen lyckas men inte fungerar kontrollerar du [Problem med instabila anslutningar](troubleshooting-sms.md#issues-unstable-connection) -avsnitt.

* Om det är svårt att diagnostisera anslutningsproblem kan nätverksinhämtningen ge information. Se till att nätverksinhämtningen körs samtidigt medan problemet uppstår så att det kan analyseras effektivt. Du bör också notera exakt när problemet uppstår.

## Problem med instabil anslutning {#issues-unstable-connection}

En anslutning anses vara instabil om något av följande inträffar:

* Anslutningen varar i mindre än 1 timme. Adobe Campaign Classic sändaranslutningar är ett undantag på grund av hur Adobe Campaign Classic MTA fungerar.

* Leverantören skickar `UNBIND PDU`s.

* `enquire_link` timeout, antingen på Adobe Campaign eller på leverantörssidan. Du kanske ser `ENQUIRE_LINK_RESP` med en felkod som inte är noll i så fall.

* Det finns mycket `BIND PDU`s. Det får inte finnas mer än ett fåtal under en dag, beroende på antalet anslutningar. Mer än 1 BIND PDU per timme ska vara varningar.

Så här åtgärdar du problem med anslutningsstabilitet:

* Instabila anslutningar är sällan rotorsaken, det beror ofta på ett annat problem som utlöser en frånkoppling. Att hitta rotorsaken är prioriteten.

* Aktivera utförliga SMPP-spår. De måste se vad som händer när anslutningen startas om.

* Om providern skickar `BIND PDU`Något kan vara fel. Fråga leverantören varför `UNBING` skickas.

* Ibland är det enda sättet att se hur anslutningen stängs att ta en nätverksinhämtning.

* Om providern stänger anslutningarna genom att skicka antingen en `TCP FIN` eller en `TCP RST packet`frågar du leverantören mer information.

* Om providern stänger anslutningen efter att ha skickat ett rent fel, till exempel `DELIVER_SM_RESP` med en felkod måste de åtgärda sin koppling, annars förhindras att andra typer av meddelanden överförs och utlösa MTA-begränsning. Detta är särskilt viktigt i sändningsläge där stängning av anslutningen påverkar både MT och SR.

## Problem vid sändning av MT (vanlig SMS skickad till en slutanvändare){#issue-MT}

* Kontrollera att anslutningen är stabil. En SMPP-anslutning bör vara kontinuerligt uppkopplad i minst en timme, med undantag för sändare på Adobe Campaign Classic. Se avsnittet [Problem med instabila anslutningar](sms-protocol.md#issues-unstable-connection).

* Om du startar om MTA så att sändning av MT fungerar igen under en liten tidsperiod, har du antagligen strypning på grund av en instabil anslutning. Se avsnittet [Problem med instabila anslutningar](troubleshooting-sms.md#issues-unstable-connection).

* Kontrollera att den breda loggen finns och att den har rätt status med rätt datum. Annars kan det vara ett leveransproblem.

* Kontrollera att MTA faktiskt behandlar meddelandet. Om så inte är fallet är det kanske inte ett SMS-problem.

* Kontrollera att SMS-anslutningen är bunden till providerns utrustning. Be leverantören om feedback för att säkerställa att alla system kommunicerar på rätt sätt. Se `BIND_TRANSMITTER` och `BIND_TRANSCEIVER PDU`s om du vill ha information om bindningsprocessen. Du kan behöva aktivera SMPP-spår för korrekt felsökning.

* När SMPP-spårningarna är aktiverade kontrollerar du att `SUBMIT_SM PDU` innehåller rätt information.

* Kontrollera att providern svarar med en `SUBMIT_SM_RESP PDU` med ett OK-värde (kod 0). Kontrollera att PDU:n kommer med rimlig fördröjning: om något längre än en sekund måste diskuteras med leverantören, kommer det vanligtvis på mindre än 100 ms.

* Om alla dessa steg fungerar kan du vara säker på att problemet ligger hos leverantören. De måste göra felsökningen på sin plattform.

* Om det fungerar men flödet inte är konsekvent kan du försöka justera sändande fönster och sänka MT-flödet. Du måste arbeta med leverantören för att justera det. Adobe Campaign kan skicka meddelanden mycket snabbt så att det kan uppstå prestandaproblem på leverantörens utrustning.

## MT dupliceras (samma SMS skickas flera gånger i rad){#duplicated-MT}

Dubbletter orsakas ofta av återförsök. Det är normalt att ha dubbletter när du försöker göra om meddelanden. Försök i stället att ta bort grundorsaken till nya försök.

* Om dubbletter skickas med exakt 60 sekunders mellanrum är det antagligen ett problem på leverantörssidan, de skickar inte någon `SUBMIT_SM_RESP` snabbt nog.

* Om du ser många `BIND/UNBIND`har du en instabil anslutning. Se[Problem med instabila anslutningar](troubleshooting-sms.md#issues-unstable-connection) för lösningar innan du försöker lösa problem med dubblettmeddelanden.

Minska antalet dubbletter när ett nytt försök görs:

* Sänk sändningsfönstret. Sändande fönster ska vara tillräckligt stort för att täcka `SUBMIT_SM_RESP` latens. Dess värde representerar det maximala antalet meddelanden som kan dupliceras om ett fel inträffar när fönstret är fullt.

## Utfärda vid behandling av SR (leveranskvitton) {#issue-process-SR}

* Du måste ha aktiverat SMPP-spår för att kunna utföra någon typ av SR-felsökning.

* Kontrollera att `DELIVER_SM PDU` kommer från leverantören och är välformad.

* Kontrollera att Adobe Campaign svarar med framgång `DELIVER_SM_RESP PDU` i tid. På Adobe Campaign Classic garanterar detta att SR har införts i `providerMsgId` tabell för uppskjuten behandling av SMS-processen.

Om `DELIVER_SM PDU` bekräftas inte och du bör kontrollera följande:

* Kontrollera regex för id-extrahering och felbearbetning i **Externt konto**. Du kan behöva validera dem mot innehållet i `DELIVER_SM PDU`.

* Kontrollera att fel har etablerats korrekt i `broadLogMsg` tabell.

Om `DELIVER_SM PDU` har bekräftats av Adobe Campaign Classic utökade SMPP-anslutning, men broadLog uppdateras inte korrekt, kontrollera ID-avstämningsprocessen som beskrivs i avsnittet [Matchande MT-, SR- och broadcast-poster](sms-protocol.md#matching-mt).

Om du har korrigerat allt men vissa ogiltiga SR fortfarande finns i providerns buffertar kan du hoppa över dem genom att använda alternativet&quot;Ogiltigt antal ID-bekräftelser&quot;. Detta ska användas med försiktighet och återställas till 0 så fort som möjligt efter att buffertarna har tömts.

## Problem vid bearbetning av MO (och svartlistning/autosvar){#issue-process-MO}

* Aktivera SMPP-spår under tester. Om du inte aktiverar TLS bör du göra en nätverksinhämtning när du felsöker MO för att kontrollera att PDU:er innehåller rätt information och är korrekt formaterade.

* När du hämtar nätverkstrafik eller analyserar SMPP-spår, se till att du fångar in hela konversationen med MO och dess MT-svar om ett svar har konfigurerats.

* Om flerlägesobjektet (`DELIVER_SM PDU`) visas inte i spårningarna, problemet ligger på leverantörssidan. De måste felsöka på sin plattform.

* Om `DELIVER_SM PDU` visas kontrollerar du att Adobe Campaign har godkänt det `DELIVER_SM_RESP PDU` (kod 0). Denna RESP garanterar att all bearbetningslogik har använts av Adobe Campaign (autosvar och tillåt/blocklist). Om så inte är fallet söker du efter ett felmeddelande i SMS-processloggarna.

* Om automatiska svar är aktiverade kontrollerar du att `SUBMIT_SM` har skickats till providern. Annars kommer det garanterat att hitta ett felmeddelande i SMS-processloggarna.

* Om `SUBMIT_SM MT PDU` som innehåller svaret finns i spårningarna, men SMS:et inte kommer till mobiltelefonen, måste du kontakta leverantören för att få hjälp med felsökningen.

## Problem vid färdigställande av leveransen, med undantag för mottagare i karantän (i karantän enligt funktionen för autosvar) {#issue-delivery-preparation}

* Kontrollera att telefonnummerformatet är exakt detsamma i karantäntabellen och i leveransloggen. Om så inte är fallet, se [section](sms-protocol.md#automatic-reply) om du har problem med plusprefixet för det internationella telefonnummerformatet.

* Kontrollera korta koder. Undantag kan inträffa om den korta koden för mottagaren antingen är densamma som den är definierad i det externa kontot eller om den är tom (tom = valfri kortkod). Om bara en kort kod används för hela Adobe Campaign-instansen är det enklare att lämna alla **kort kod** fält är tomma.

## Kodningsproblem {#encoding-issues}

**Steg 1: Kontakta leverantören**

Kontakta dem och se vad som är fel med dem. De bör kunna tala om för dig om problemet ligger på deras sida eller på Adobe Campaign sida. Om problemet är i Adobe Campaign bör de kunna tala om exakt vilket fält som är felaktigt.

**Steg 2: Ta reda på vad meddelandet innehåller**

Unicode tillåter många varianter för likartade tecken och Adobe Campaign kan inte hantera alla.

Den vanligaste källan till problem är en kopiera-klistra in från en ordbehandlare, som ändrar vanliga tecken till typografiskt korrekta versioner: blanksteg ändrade till fasta blanksteg, dubbla citattecken ändrade till inledande och avslutande citattecken, minustecken ändrade till olika typer av bindestreck osv.

Kopiera inte och klistra in meddelandet när du testar. Skriv det alltid direkt i gränssnittet.

Med hexadecimala tecken kan du se skillnaden mellan liknande tecken. En gemener L, en versal I, O, 0, alla olika typer av citattecken, icke-latinska kodningar eller till och med olika typer av blanksteg kan alla se likadana ut eller kanske inte visas alls.

Om du vill konvertera Unicode till hexadecimal kan du använda onlineverktyg som [Unicode-kodskonverterare](https://r12a.github.io/app-conversion/) webbplats. Skriv texten och kontrollera att det inte finns någon PII-fil, t.ex. telefonnummer, och klicka **Konvertera**. De hexadecimala värdena visas längst ned (UTF-32-zon).

När biljetter om kodningsproblem öppnas, oavsett om det gäller leverantören eller [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)innehåller alltid en hexadecimal version av det du skriver och det du ser.

**Steg 3: Ta reda på vad du ska skicka**

Bestäm vilken kodning du förväntar dig ska användas och sök online efter teckentabellen. Kontrollera att de tecken du vill skicka är tillgängliga på målkodsidan. Kontrollera att `data_coding` fältet är korrekt och matchar vad du och leverantören förväntar sig.

**Steg 4: Ta reda på vad du skickade**

Du behöver felsökningsutdata för anslutningen för att se exakt vilka byte du skickar till providern. Kodningsproblem visas i `SUBMIT_SM PDU`s, så var noga med att fånga dem. Skicka distinkta meddelanden som är enkla att hitta i loggen.

Skicka olika typer av specialtecken vid testning. GSM7-kodning har till exempel utökade tecken som är mycket tydliga i hexadecimal form, och de är enkla att hitta eftersom de inte visas i någon annan kodning.

## Element som ska inkluderas vid kommunikation om ett SMS-problem {#element-include}

När du behöver hjälp med ett SMS-problem, oavsett om det gäller att öppna en supportanmälan till Adobe Campaign, SMS-leverantören eller någon sorts kommunikation om problemet, måste du inkludera följande information för att vara säker på att den är korrekt kvalificerad. Rätt kvalificerade problem är avgörande för att lösa problem snabbare.

* **Aktivera utförliga SMPP-meddelanden** när problemet uppstår. De flesta SMS-problem är omöjliga att lösa utan detta.

* Om problemet är relaterat till SMS-trafik ska du kontakta leverantören först. Deras plattform är bäst lämpad för effektiv diagnos av SMS-trafikproblem i realtid.

* Ta med en kort men faktisk beskrivning av problemet.

* Ta med en beskrivning av det förväntade resultatet.

* Inkludera feedback från leverantören.

* Inkludera relevanta loggar och/eller nätverksinhämtningar. Se till att du återskapar problemet under hämtningen när du gör hämtningar.

* Om du inkluderar loggar, kalkeringar eller klipp bör du identifiera exakt var i filen problemet finns.

* Om du refererar till meddelanden, PDU:er eller loggar måste du tydligt ange deras tidsstämpel för att göra dem lättare att hitta.

* Försök återskapa problemet i en testmiljö. Om du är osäker på en inställning kan du testa den i testmiljön och kontrollera resultatet med SMPP-spår. Det är oftast bättre att rapportera problem som replikeras i testmiljöer än att rapportera direkt i produktionsmiljöer.

* Inkludera alla ändringar eller förbättringar som gjorts på plattformen. Ta även med eventuella ändringar som leverantören kan ha gjort på sin sida.

### Nätverksinspelning {#network-capture}

Nätverksinspelning behövs inte alltid, vanligen räcker det med omfattande SMPP-meddelanden. Här följer några riktlinjer som hjälper dig att avgöra om en nätverksinhämtning behövs:

* Anslutningsproblem, men de detaljerade meddelandena visar inga `BIND_RESP PDU`.

* Oförklarliga frånkopplingar utan felmeddelande, det vanliga beteendet för kopplingen när den upptäcker ett protokollfel på låg nivå.

* Providern klagar över avbindnings-/frånkopplingsprocessen.

* Kodningsproblem i valfria TLV-fält.

* Trafiken misstänks vara blandad mellan olika anslutningar.

I alla andra situationer kan du försöka analysera detaljerade SMPP-meddelanden först och begära en nätverksregistrering enbart om information saknas i de detaljerade loggarna.

I vissa fall behövs ingen hämtning av nätverkstrafik. Här är de vanligaste situationerna:

* TLS aktiverat: TLS-trafik krypteras per definition så den kan inte fångas in.

* Prestandaproblem: Loggar innehåller all information som behövs för att spåra prestandaproblem.

* Timingproblem (`retry timing`, `enquire_link` period, flödeskappning osv.)

* SR-parsning och -bearbetning: utförliga loggar ger mycket mer sammanhang och en bättre presentation.

* MO-behandling (automatiska svar, karantän).

* Fel som inte involverar faktisk SMPP-trafik: Förberedelse av leverans, API-problem för Message Center, arbetsflödesproblem osv.

## Aktivera SMPP-spår {#enabling-smpp-traces}

Den nya kopplingen har stöd för utökad loggning via spår: SMPP. Spår skrivs ut i MTA-loggen, inte i standardutdata.

**Aktivera per externt konto (föredragen metod)**

1. I **Externt konto**, kontrollera **Aktivera utförliga SMPP-spår i loggfilen**.
1. Vänta i 10 minuter så att servern kan läsa in externa konton igen.

Det borde vara aktivt nu.

**Aktivera i konfiguration**

I `config-instance.xml` anger du följande parametrar:

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## Kontrollera antalet öppna anslutningar i en behållare {#open-connections}

Om du vill kontrollera antalet öppna anslutningar i en behållare kan du använda det här kommandot:

```
(for pid in $(ss -neopts  | sed -n ‘s/^.*:3600[ \t].*users:(([0-9A-Za-z”]*,pid=\([0-9]*\),.*$/\1/p’ | sort ); do  cat /proc/$pid/cmdline; echo  ” $pid” ;done;) | uniq --count
```

Här visas antalet anslutningar som är öppna för en viss port. Här använder vi port 3600.

Resultatet ska vara följande:

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

4 öppna anslutningar för SMS-processen och 2 per huvudunderordnad med 5 underordnade.
