---
product: campaign
title: Protokoll och inställningar för SMS-koppling
description: Läs mer om SMS-anslutningen och hur du konfigurerar den
feature: SMS
exl-id: fded088a-11a2-4b87-a368-7b197334aca4
source-git-commit: 2c145829517a6961d502cc3e7b904547f8c71602
workflow-type: tm+mt
source-wordcount: '8460'
ht-degree: 0%

---

# Protokoll och inställningar för SMS-koppling {#sms-connector-protocol}

![](../../assets/common.svg)

>[!NOTE]
>
>I det här dokumentet refererar alla referenser till detaljer om protokollet, fältnamnen och värdena till [Specifikation för SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

## Översikt {#overview}

SMS kan vara begränsat till att skicka korta textmeddelanden utan formatering, men enkelheten gör det till en värdefull kommunikationskanal.

Det finns två sätt att skicka ett SMS:

* Skicka det manuellt från en telefon, det vanliga sättet att kommunicera direkt mellan människor.
* Skicka via internet, på samma sätt som Adobe Campaign skickar meddelanden. För detta behöver du en SMS-tjänsteleverantör som ansluter Internet till det mobila nätverket.
Adobe Campaign använder SMPP-protokollet för att skicka SMS till en tjänsteleverantör.

Det här dokumentet leder dig genom uppkopplingen mellan Adobe Campaign och en SMPP-leverantör.

SMPP-leverantörer kan ibland avvika från den officiella specifikationen, men SMS-kopplingen i Adobe Campaign erbjuder många alternativ för att anpassa sitt beteende så att det blir kompatibelt med de flesta leverantörer.

>[!IMPORTANT]
>
>Att konfigurera en anslutning till en ny provider kan kräva viss teknisk kompetens, kunskap om TCP, binär, hexadecimal representation och textkodning. Det kommer också att kräva ett aktivt samarbete med leverantören.

### SMS-typer {#sms-types}

När du skickar SMS via en SMS-leverantör kommer du att stöta på tre olika typer av SMS:

* **SMS MT (Mobile Terminated)**: ett SMS som Adobe Campaign skickar till mobiltelefoner via SMPP-leverantören.

* **SMS MO (Mobile Originated)**: ett SMS som skickas av en mobil till Adobe Campaign via SMPP-leverantören.

* **SMS SR (statusrapport), DR eller DLR (leveranskvitto)**: Ett returkvitto som skickas av mobilen till Adobe Campaign via SMPP-leverantören som anger att SMS:et har tagits emot. Adobe Campaign kan också få ett SR-meddelande som anger att meddelandet inte kunde levereras, ofta med en beskrivning av felet.

Du måste skilja mellan bekräftelser (RESP PDU, en del av SMPP-protokollet) och SR: SR är en typ av SMS som skickas via nätverket från början till slut, medan en bekräftelse bara är en bekräftelse på att en överföring har lyckats.

Både bekräftelser och SR kan utlösa fel, och om man skiljer mellan dem blir det lättare att felsöka.

### Information som medförs av ett sms {#information-sms}

Ett SMS innehåller mer information än text. Här följer en lista över vad du kan förvänta dig i ett SMS:

* Texten, som är begränsad till 140 byte, vilket innebär mellan 70 och 160 tecken beroende på kodningen. Se [SMS-textkodning](sms-protocol.md#sms-text-encoding) nedan om du vill ha mer information och begränsningar.

* En mottagaradress, ibland kallad `ADC` eller `MSISDN`. Det är numret på den mobil som kommer att ta emot SMS:et.

* En avsändaradress som kan anropas `oADC` eller ibland `sender id`. Det kan vara ett telefonnummer som används dag för dag, en kort kod som skickas via en leverantör eller ett namn. Namnet är en valfri funktion, i så fall kan du inte svara på SMS:et.

* En flagga som anger om meddelandet är ett flash-meddelande. Ett Flash-meddelande är ett popup-fönster som inte är sparat i minnet.

* En flagga som anger om ett SR förväntas eller inte.

* Ett giltighetsdatum efter vilket ingen nätverksutrustning får göra ett nytt försök.

* A `data_coding` som anger textens kodning.

## SMPP-protokoll {#smpp-protocol}

Adobe Campaign Classic stöder SMPP-protokollversion 3.4. Detta är ett utbrett protokoll som tillåter att SMS skickas till en leverantör (SMSC) och tar emot både SMS och kvitton. Mer information finns i [SMPP-dokumentation](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

Nätverksutrustningen på SMS-tjänstleverantörens sida kallas ofta SMSC.

### SMPP-anslutningar {#smpp-connections}

Adobe Campaign ansluter till SMS-tjänstleverantörens nätverksutrustning via TCP. SMPP-protokollet anger permanenta TCP-anslutningar från Adobe Campaign till providern. TCP-anslutningar initieras alltid av Adobe Campaign, även för att ta emot meddelanden.
SMPP öppnar 1 eller 2 TCP-anslutningar, beroende på läge. Alla anslutningar initieras alltid av Adobe Campaign.

SMPP-protokollet kan fungera i två lägen:

* **Sändare+mottagare (eller TX+RX)**: två separata TCP-anslutningar används för att överföra och ta emot meddelanden.
* **Mottagare (eller TRX)**: en enda TCP-anslutning används för att överföra och ta emot meddelanden.

>[!NOTE]
>
> Adobe Campaign Classic stöder endast TX+RX-läget. Denna begränsning beror på dess tekniska arkitektur.

### SMPP PDU {#smpp-pdu}

SMPP-överföringsenheter (&quot;paket&quot;) kallas PDU. A **PDU** innehåller ett kommando, en status, ett sekvensnummer och data.

Varje PDU måste bekräftas av en `SMPP RESP PDU` (synkront svar). Förfrågningar kan röras: avsändaren kan skicka många kommandon utan att vänta på `RESP`kallas dock fönstret för det antal begäranden som när som helst kan röras. `RESP PDU` kan anlända i vilken ordning som helst, oavsett ordningen på PDU:n för initieraren.

I den separerade **Sändare+mottagare** vilket läge som används beror på vilken typ av meddelande som skickas. Sändaranslutningen används för MT och mottagaranslutningen används för MO och SR. Begäranden och svar för varje typ av meddelande skickas via samma TCP-anslutning.

När du skickar ett MT-meddelande används till exempel sändaranslutningen och `RESP` som bekräftar att MT också skickas via sändningskanalen. När du tar emot ett flerlägesobjekt (eller ett SR) används mottagaranslutningen för att ta emot flerlägesobjektet och skicka `RESP` som bekräftar marknadschefen.

![](assets/do-not-localize/sms_protocol_1.png)

I Adobe Campaign Classic returneras ett ID från SMSC med `SUBMIT_SM_RESP` och `DELIVER_SM` steg. Identifieraren lagras i `providerId` fält för `nms::providerMsgId` tabell och är länkad till `broadLogId` och `deliveryId`. Denna matchningsåtgärd utförs av SMS-processen när den skriver till databasen.

Slutförd `SUBMIT_SM_RESP PDU` utlöser statusen för skickat meddelande i den sändande loggen när ett `DELIVER_SM (SR) PDU` utlöser statusen för mottaget meddelande.

### Säkerhetsaspekter {#security-aspects}

Själva protokollet är inte krypterat. De flesta leverantörer implementerar en variant av IP på tillåtelselista så att Adobe Campaign server-IP-adresserna måste deklareras till providern.

Adobe Campaign har stöd för att skicka inloggningar och lösenord under bindningsfasen. Det har även stöd för SMPP över TLS. Det bör noteras att certifikat krävs för att säkerheten ska vara god. Även om SMPP-kopplingen tillåter att certifikatkontroller kringgås, bör den bara användas för testning eftersom TLS utan certifikat ger en betydligt lägre säkerhetsnivå.

Kopplingen använder standardcertifikaten som tillhandahålls av systemet `openssl` bibliotek. Vanligtvis tillhandahålls det av `/etc/ssl/certs` på Debian. Den här katalogen tillhandahålls som standard av paketet&quot;ca-certificates&quot;, men det kan anpassas.

### Information i varje typ av PDU {#information-pdu}

Varje PDU har olika fält som innehåller olika information. Den här PDU:n finns i [Specifikation för SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

Varje avsnitt nedan beskriver både PDU:n och dess synkrona svar (`*_RESP PDU`). Alla PDU måste bekräftas med en motsvarande `RESP`är detta en obligatorisk del av specifikationen.

PDU:er kan ha valfria fält. Här beskrivs bara de vanligaste fälten. Se [Specifikation för SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) för mer information.

**BIND_TRANSMITTER / BIND_RECEIVER / BIND_TRANSCEIVER**

Denna PDU används för att initiera en anslutning till SMSC. **Sändare**, **Mottagare** och **Mottagare** ändrar endast den typ av SMS som får överföras via den här anslutningen:

| Läge | Typ av SMS tillåts |
|:-:|:-:|
| Sändare | MT |
| Mottagare | MO + SR |
| Mottagare | MT + MO + SR |

Anteckningsbara fält i en `BIND_* PDU`:

* **system_id**: Inloggning används för autentisering. Ange i det externa kontot.

* **lösenord**: Lösenord som används för autentisering. Ange i det externa kontot.

* **system_type**: Krävs för att anges till ett specifikt värde för vissa leverantörer. Ange i det externa kontot, som är tillgängligt i alla versioner. Skillnaden skiljer ofta mellan olika typer av kontrakt, kanaler, länder osv.

* **addr_ton** och **addr_npi**: Krävs av vissa leverantörer. Ange efter `Bind TON` och `Bind NPI` inställningar i det externa kontot.

* **adressintervall**: Krävs av vissa leverantörer. Oftast är detta en lista med kortkoder som är tillåtna för den här anslutningen. Ange i det externa kontot.

`BIND_*_RESP` har inget specifikt fält, det bekräftar om anslutningen lyckades eller inte.

#### UNBIND {#unbind}

Den här PDU:n måste skickas av systemet innan den kopplas från. Det måste vänta på matchningen `UNBIND_RESP` PDU innan anslutningen stängs.

Om SMSC konfigureras får anslutningen inte stängas, TCP-anslutningen styrs av Adobe Campaign-anslutningen.

#### SUBMIT_SM {#submit-sm}

Denna PDU skickar en MT till SMSC. Dess PDU för svar ger ID:t för MT.

Anteckningsbara fält i en `SUBMIT_SM` PDU:

* **service_type**: krävs av vissa leverantörer. Ange i leveransegenskaperna.

* **source_addr_ton** och **source_addr_npi**: anger vilken typ av källadress som skickas. Innehållet i dessa fält är standardiserat, men eftersom vissa leverantörer använder det på ett annat sätt bör du be leverantören om dess korrekta värde. Ange i det externa kontot.

* **source_addr**: källadressen/ADC för MT. Den visas på mobiltelefonen. Värdet i leveransen har företräde framför värdet på det externa kontot som anges i det externa kontot och leveransen.

* **dest_addr_ton** och **dest_addr_npi**: anger vilken typ av destinationsadress som överförs (t.ex. lokalt eller internationellt format). Innehållet i dessa fält är standardiserat, men eftersom vissa leverantörer använder det på ett annat sätt bör du be leverantören om dess korrekta värde. Ange i det externa kontot.

* **destination_addr**: mottagarens adress, telefonnummer eller MSISDN.

* **esm_class**: används för att avgöra om UDH används eller inte i textfältet. Aktiveras automatiskt av kopplingen för delad SMS om `message_payload` Läget används inte.

* **priority_flag**: prioriteten för det här meddelandet framför andra. Detta är kopplat till själva leveransprioriteten.

* **validity_period**: tidsstämpel efter vilken inga nya försök ska göras. Anges i själva leveransen.

* **registered_delivery**: anger om en SR begärs eller inte. Adobe Campaign anger alltid den här flaggan förutom för automatiska svar. För multipart-meddelanden är flaggan bara inställd för den första delen. Alla versioner har samma beteende.

* **data_coding**: används för att ange den kodning som används i textfältet. Se [SMS-textkodning](sms-protocol.md#sms-text-encoding) för mer information.

* **short_message**: texten i meddelandet. Om UDH används innehåller detta även UHD-huvudet.

Adobe Campaign har stöd för följande valfria fält:

* **dest_addr_subunit**: som används för att ange målet för SMS: flash-kort, mobilkort eller SIM-kort. Ange i leveransegenskaperna.

* **message_payload**: när det är aktiverat i det externa kontot skickas långa meddelanden i en enda PDU och texten skickas i det här fältet i stället för i `short_message` fält.

#### SUBMIT_SM_RESP {#submit-sm-resp}

Den här PDU:n kommer att innehålla ID:t för MT:n. Detta är användbart för att matcha det med inkommande SR.

>[!IMPORTANT]
>
>Många leverantörer skickar MT-ID:t hexadecimalt. Se till att du anger **ID-format i MT-bekräftelse** korrekt inställning i det externa kontot.

Vissa leverantörer skickar `SUBMIT_SM_RESP` efter att SR har skickats. För att ta hänsyn till detta väntar Adobe Campaign 30 sekunder innan det svarar **Ogiltigt meddelande-ID** till en SR med ett okänt ID.

#### DELIVER_SM {#delivery-sm}

Denna PDU skickas av SMSC till Adobe Campaign. Den innehåller antingen en enkel inloggning eller en SR.

De flesta fält har samma betydelse `SUBMIT_SM` motpart. Här är en lista med användbara fält:

* **source_addr**: MO/SR-källadress. Vanligtvis är det här ett telefonnummer.

* **destination_addr**: Kortkod som tog emot marknadsoperationen eller SR.

* **esm_class**: används för att avgöra om PDU:n är en MO eller en SR.

* **short_message**: texten i meddelandet. För SR innehåller detta data som beskrivs i tillägg B till SMPP-protokollspecifikationen. Se [SR-felhantering](sms-protocol.md#sr-error-management) för mer information.

Adobe Campaign kan läsa meddelande-ID i `receipted_message_id` valfritt fält med viss konfiguration.

#### DELIVER_SM_RESP {#deliver-sm-resp}

Denna PDU skickas av Adobe Campaign för att bekräfta SR och MO.

Adobe Campaign Classic godkänner SR och MO när de har infogats i databasen. Vissa bearbetningsfel kan inträffa även om de lyckas `DELIVER_SM_RESP` PDU har skickats. Den här begränsningen orsakas av Adobe Campaign Classic programvaruarkitektur.

#### INQUIRE_LINK {#enquire-links}

Denna PDU används bara för att kontrollera att anslutningen är aktiv. Dess frekvens bör fastställas efter leverantörens behov.

Standardvärdet på 60 sekunder bör matcha de flesta konfigurationer som angetts för det externa kontot.

#### INQUIRE_LINK_RESP {#enquire-links-resp}

Den här PDU:n bekräftar att anslutningen lever.

### Multipart SMS (long SMS) {#multipart}

>[!IMPORTANT]
>
> Adobe Campaign har endast stöd för multipart SMS eller lång SMS för att skicka. UDH och `message_payload` stöds inte för inkommande SMS (MO), vilket innebär att MO är begränsat till 160 tecken.

Multipart SMS, eller lång SMS, är SMS som skickas i flera delar. På grund av tekniska begränsningar i mobilnätverksprotokollet kan ett SMS inte vara större än 140 byte, annars måste det delas. Se [SMS-textkodning](sms-protocol.md#sms-text-encoding) om du vill veta mer om hur många tecken som får plats i ett SMS.

Varje del av ett långt meddelande är ett individuellt SMS. Dessa delar är oberoende av varandra på nätet och har monterats av den mottagande mobiltelefonen. För att hantera återförsök och anslutningsproblem skickar Adobe Campaign dessa delar i omvänd ordning och begär en SR endast i den första delen av meddelandet, den sista som skickas. Eftersom mobiltelefonen bara visar ett meddelande när den första delen tas emot, kommer nya försök med ytterligare delar inte att skapa dubbletter på mobiltelefonen.

Det maximala antalet SMS per meddelande kan anges per leverans med **Högsta antal SMS per meddelande** i **Leveransmall**. Meddelanden som överskrider den här gränsen misslyckas när ett SMS skickas med en för lång felorsak.

Det finns två sätt att skicka långt SMS:

* **UDH**: standardmetoden och det rekommenderade sättet att skicka långa meddelanden. I det här läget delar kopplingen upp meddelandet i flera `SUBMIT_SM PDU`har UDH-information. Det här protokollet används av mobiltelefoner själva. Detta innebär att Adobe Campaign har störst kontroll över meddelandegenereringen, vilket gör att man kan beräkna exakt hur många delar som skickades och hur de delades.

* **message_payload**: sättet att skicka hela det långa meddelandet i ett enda `SUBMIT_SM PDU`. Leverantören måste då dela upp den, vilket innebär att det är omöjligt för Adobe Campaign att veta exakt hur många delar som har skickats. Vissa leverantörer kräver det här läget, men vi rekommenderar att du bara använder det om de inte stöder UDH.

Se beskrivningen av `esm_class`, `short_message` och `message_payload` fälten i [SUBMIT_SM PDU](sms-protocol.md#information-pdu) för mer information om protokoll och format.

### Plattor och fönsterrutor {#throughput-capping}

De flesta leverantörer kräver en genomströmningsgräns för varje SMPP-anslutning. Detta kan uppnås genom att ange ett antal SMS i det externa kontot. Observera att genomströmningsbegränsning inträffar per anslutning. Den totala effektiva genomströmningen är gränsen per anslutning multiplicerad med det totala antalet anslutningar. Detta beskrivs i [Samtidiga anslutningar](sms-protocol.md#connection-settings) -avsnitt.

För att uppnå maximal genomströmning måste du finjustera det maximala sändningsfönstret. Det sändande fönstret är antalet `SUBMIT_SM PDU`som kan skickas utan att vänta på en `SUBMIT_SM_RESP`. Se [Inställning för fönstret skickas](sms-protocol.md#throughput-timeouts) för mer information.

### SR och felhantering (&quot;Bilaga B&quot;) {#sr-error-management}

SMPP-protokollet definierar synkrona standardfel i `RESP PDU`s, men den definierar inte felkoder för SR. Varje provider använder sina egna felkoder med sin innebörd.

En rekommendation ges i avsnittet i tillägg B i [SMPP-protokollspecifikation](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (sidan 167), men inte själva felkoderna.

Adobe Campaign sändningsmeddelandesystem har anpassats till felhanteringen och har använts för att korrekt tillhandahålla fel och deras allvarlighetsgrad (hårdhet, mjuk osv.).

Som nämnts ovan finns det två olika typer av fel:

* synkrona svar i `SUBMIT_SM_RESP` som inträffar omedelbart efter det att meddelandet skickades till SMSC
* kvitton som kan komma mycket senare när mobilen tog emot meddelandet eller när meddelandet nådde tidsgränsen. I så fall hittas felet i en SR.

När en SR tas emot kan status och fel hittas i `short_message` fält (exempel för implementeringar som överensstämmer med tillägg B). The `short_message` fältet i PDU:n kallas ofta **textfält** eftersom den innehåller text i MT. För SR innehåller den teknisk information plus ett delfält som heter **Text**. Dessa två fält är olika och `short_message` innehåller **Text** fält och annan information.

Adobe Campaign Classic-anslutningar (utom Extended SMPP) använder ett hårdkodat beteende som är beroende av den valda providern. Allmän SMPP skiljer bara mellan lyckade och misslyckade utan detaljer. Leveransloggen kan innehålla viss information som inte är garanterad.

#### SR-textfältformat {#sr-text-field-format}

Specifikationen rekommenderar att du använder det här formatet för SR-textfältet. Det är en lista med delfält, avgränsade med kolon, som avgränsar fältnamnet och dess värde. Fältnamn är inte skiftlägeskänsliga.

Exempel på ett SR-textfält som matchar rekommendationen i tillägg B:

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

ID-fältet är det ID som tas emot i `SUBMIT_SM_RESP PDU`, MT:s erkännande.

`sub` och `dlvrd` ska räkna ut mängden levererade delar och levererade meddelanden, men detta används inte av Adobe Campaign eftersom sändningssystemet ger bättre och mer integrerad information.

`submit date` och `done date` fält är indikativa tidsstämplar för när MT skickades och när SR skickades av mobilen. Förvänta dig problem med tidszoner eller till och med fel tidsstämplar från mobiler med felaktig datumuppsättning.

Statusfältet är viktigt eftersom det anger meddelandets status. Den enda viktiga statusen är `DELIVRD`, `UNDELIV` och `REJECTD`. The `DELIVRD` status anger att det lyckades, de andra två visar ett fel. Andra värden är möjliga, men de är vanligtvis mellanliggande meddelanden, t.ex. att MT nådde mobiltelefonen, men inte mobiltelefonen. Dessa mellanliggande meddelanden ignoreras av Adobe Campaign.

Felfältet innehåller den providerspecifika felkoden. Leverantören måste ge en tabell över möjliga felkoder tillsammans med deras betydelse för att kunna tolka det här värdet.

Slutligen innehåller textfältet vanligtvis början av texten i MT. Detta ignoreras av Adobe Campaign och vissa leverantörer skickar inte det för att undvika PII-läckage och bandbreddsförbrukning i nätverket. Den kan användas under felsökning för att identifiera SR-matchning av ett test MT enklare genom att läsa det här fältet.

### Exempel på SR-bearbetning i Adobe Campaign Classic Extended allmän SMPP {#sr-processing}

I det här exemplet visas fallet med en implementering som följer rekommendationerna i tillägg B, standardvärden i det externa kontot och ett godkänt SMS MT.

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Först `id extraction` regex används för att extrahera ID:t och stämma av det med motsvarande MT.

Sedan `status extraction` regex och `error code extraction` regex används för att extrahera dessa fält och läggs till i strängen.

Sändningsmeddelandet skapas med den här informationen och den ursprungliga oförändrade strängen läggs till som referens:

```
SR ExampleProvider DELIVRD 000|MESSAGE=id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Meddelandet normaliseras sedan och MESSAGE-delen tas bort för att kunna matcha flera meddelanden med samma stat- och felkoder.

```
SR ExampleProvider DELIVRD 000|#MESSAGE#
```

Om meddelandet inte redan har etablerats i sändningsmeddelandetabellen skapas en ny post med hela meddelandet som **firstText** och det normaliserade meddelandet. Sedan använder kopplingen framgångarna och `error` regex för att avgöra om åtgärden lyckades eller misslyckades:

* Om den matchar `success` regex, kommer det att betraktas som en framgång.

* Om den matchar `error` regex, meddelandet kvalificeras som ett fel.

* Om ingen av dessa två regex matchar, ignoreras SR. Det kan vara ett mellanliggande meddelande som inte hanteras av Adobe Campaign.

Som standard anges alla fel som mjuka fel. Det innebär att hårda fel måste tillhandahållas manuellt.

### SMS-textkodning {#sms-text-encoding}

Du borde **kontakta alltid SMSC-leverantören vid kodningsproblem**. Endast SMSC-leverantörerna har kunskap om den kodning de stöder och särskilda regler som kan gälla på grund av begränsningar i deras tekniska plattform.

SMS-meddelanden använder en speciell 7-bitars kodning, som ofta kallas GSM7-kodning.

I SMPP-protokollet kommer GSM7-text att utökas till 8 bitar per tecken för enklare felsökning. SMSC paketerar det i 7 bitar per tecken innan det skickas till mobilen. Det innebär att `short_message` SMS-fältet kan vara upp till 160 byte långt i SMPP-bildrutan, medan det är begränsat till 140 byte när det skickas via mobilnätet.

Om det uppstår kodningsproblem måste du kontrollera följande:

* Kontrollera att du vet vilka tecken som tillhör vilken kodning. GSM7 har inte fullt stöd för diakritiska tecken och accenter. Särskilt på franska, där é och è är en del av GSM7, men ê, â eller ï inte är det. Detsamma gäller spanska.

* C med cedilla (ç) förekommer endast i versaler i GSM7-alfabetet, men vissa telefoner återger det med gemener eller med&quot;smart&quot; stil. Den allmänna rekommendationen är att helt undvika det och ta bort röda hund eller växla till UCS-2.

* **Använd inte ASCII i SMS** såvida det inte uttryckligen begärs av SMSC-leverantören. Den här kodningen tar bort utrymme eftersom den har 8-bitars tecken och mindre täckning än GSM7. Denna kodning kan krävas för CDMA-nätverk som används i Nordamerika.

* Latin-1 stöds inte alltid. Kontrollera kompatibiliteten med SMSC-leverantören innan du försöker använda Latin-1.

* Tabeller för nationella språkskift stöds inte av Adobe Campaign-kopplingen. Du måste använda UCS-2 eller någon annan `data_coding` i stället.

* UCS-2 och UTF-16 blandas ofta med telefoner. Detta är ett problem när du använder känslolägesikoner och andra tecken som inte finns i UCS-2.

* De flesta telefoner saknar teckensnittstecken för alla UCS-2-tecken. Smarttelefoner har en tendens att kunna visa ovanliga tecken relativt enkelt, men i vissa fall har telefoner begränsat stöd för vad som är användbart på det inhemska språket i det land där de köptes. Om du vill använda känslolägesikoner eller ASCII-konst testar du det på en mängd olika telefoner innan du skickar iväg det. Adobe Campaign Preview simulerar inte tecken som saknas och visar symboler som finns i webbläsaren.

The `data_coding` -fältet anger vilken kodning som används. Ett stort problem är att värdet 0 innebär standard-SMSC-kodning i specifikationen, som vanligtvis hänvisar till GSM7. Kontrollera med SMSC-partnern vilken kodning som är kopplad till `data_coding` = 0 som endast stöds av Adobe Campaign. Övriga `data_coding` värdena tenderar att följa specifikationen, men det enda sättet att vara säker är att kontrollera med SMSC-leverantören.

Den största tillåtna storleken för ett meddelande beror på dess kodning. I tabellen sammanfattas all relevant information:

| Kodning | Vanlig data_coding | Meddelandestorlek (tecken) | Delstorlek för multipart-SMS | Tillgängliga tecken |
|:-:|:-:|:-:|:-:|:-:|
| GSM7 | 0 | 160 | 152 | Grundläggande GSM7-teckenuppsättning + tillägg (utökade tecken tar 2 tecken) |
| Latin-1 | 3 | 140 | 134 | ISO-8859-1 |
| UCS-2 <br>UTF-16 | 8 | 70 | 67 | Unicode (varierar från telefon till telefon) |

## SMPP:s externa kontoparametrar {#SMPP-parameters-external}

Varje implementering av SMPP-protokollet har många variationer. För att förbättra kompatibilitet och anpassningsbarhet finns det många inställningar som du kan använda för att ändra SMPP-anslutningens beteende. I det här avsnittet beskrivs alla parametrar och dess effekter på kopplingen.

### Allmänna parametrar och routning {#general-parameters-routing}

**Begränsa MTA-instanser för det här kontot**

Det går att ange en gräns för hur många MTA-instanser som tillåts ansluta till SMPP-providern. När det här alternativet är markerat kan du ange hur många MTA som högst får användas.

Det här alternativet ger bättre kontroll över antalet anslutningar, se [Samtidiga anslutningar](sms-protocol.md#connection-settings).

Om du anger ett värde som är högre än antalet MTA:er som körs, körs alla MTA:er som vanligt: det här alternativet är bara en gräns och kan inte ge ytterligare MTA.

Om du behöver kontrollera exakt antalet anslutningar, t.ex. leverantörskrav, bör du alltid ange det här alternativet även om den aktuella distributionen har rätt antal MTA:er som körs. Om ytterligare MTA läggs till därefter kommer anslutningsgränsen fortfarande att gälla.

### Anslutningsinställningar {#connection-settings}

#### SMSC-implementeringsnamn {#smsc-implementation-name}

Anger namnet på SMSC-implementeringen. Den ska anges med namnet på din leverantör. Kontakta administratören eller leveransgruppen om du vill veta vad du ska lägga till i det här fältet. Fältets roll beskrivs i [SR-felhantering](sms-protocol.md#sr-error-management) -avsnitt.

#### Server {#server}

DNS-namnet eller IP-adressen för servern som ska anslutas.

#### Port {#port}

Den TCP-port som anslutningen ska kopplas till.

#### Konto {#account}

Anslutningens inloggning. Godkänd i `system_id` BIND PDU-fält.

#### Lösenord {#password}

Lösenord för SMPP-anslutningen. Lösenordsfältet för BIND PDU har skickats.

#### Systemtyp {#system-type}

Värdet som skickas i `system_id` BIND PDU-fält. Vissa leverantörer behöver ett specifikt värde här.

#### Antal MTA-underordnade anslutningar {#number-mta-child}

I Adobe Campaign Classic definieras antalet anslutningar per underordnad MTA.

Adobe Campaign Classic Extended SMPP-kontakten kan styra antalet anslutningar per MTA-underordnad. För att styra den globala gränsen för anslutningar måste du begränsa antalet MTA-underordnade processer, vilket ofta innebär att du måste ha en dedikerad mellanleverantörsplattform för SMS.

För Adobe Campaign Classic kan det finnas ett annat antal mottagar- och sändaranslutningar:

* **Transmitteranslutningar = Antal MTA-underordnade anslutningar * antal MTA-underordnade processer * antal MTA-underprocesser </br> (om autosvar är inställt) + Antal underordnade MTA-anslutningar**

Som tidigare nämnts öppnar Adobe Campaign Classic SMS-processen fler sändaranslutningar om autosvar är aktiverat. Dessa extra anslutningar används för att skicka de automatiska svaren.

* **Mottagaranslutningar = Antal MTA-underordnade anslutningar**

Om du ställer in automatiska svar kommer SMS-processen att öppna sändare-/mottagarpar, vilket ökar antalet sändaranslutningar. Om du inte har konfigurerat något automatiskt svar öppnas bara mottagaranslutningar.

#### Aktivera TLS över SMPP {#enable-TLS}

Använd TLS för att ansluta till providern. Anslutningen kommer att krypteras. TLS-anslutningen hanteras av OpenSSL-biblioteket och allt som gäller OpenSSL kommer att vara sant för den här anslutningen.

#### Aktivera utförliga SMPP-spår i loggfilen {#enable-verbose-log-file}

Den här inställningen dumpar all SMPP-trafik i loggfiler. Det krävs ofta att du justerar parametrar under den inledande konfigurationen. Detta måste vara aktiverat vid felsökning av anslutningen och jämfört med den trafik som leverantören ser.

I Adobe Campaign Classic finns loggutdata i MTA-loggen för MT-relaterad trafik och i SMS-loggen för MO- och SR-relaterad trafik.

### Inställning för mottagaranslutning {#receiver-connection}

Det här avsnittet är bara synligt i separerad **sändare+mottagare** läge.

#### Använd olika parametrar för mottagaren {#receiver-parameters}

När rutan är avmarkerad används samma inställningar för sändare och mottagare.

När rutan är markerad finns inställningarna i **Anslutningsinställningar** -avsnittet gäller för sändare och inställningarna i **Mottagaranslutning** inställningarna gäller för mottagaren.

**Mottagarserver, port, konto, lösenord, systemtyp**

De här inställningarna gäller för mottagaren i läget sändare+mottagare. De fungerar som sändningsdelen, se ovan för mer information.

### SMPP-kanalinställningar {#smpp-channel-settings}

#### Tillåt teckenomläsning {#allow-character-transliteration}

Translitterering är processen att hitta tecken som är likvärdiga med dem som saknas. Det franska specialtecknet&quot;ê&quot; (e med cirkumflex) saknas till exempel i GSM-kodningen, men det kan ersättas med&quot;e&quot; utan att det försämrar läsbarheten.

När den här rutan är avmarkerad misslyckas textkodningen om strängen inte kan kodas exakt som den är.

När den här rutan är markerad försöker textkodningen att konvertera strängen till en ungefärlig version i stället för att misslyckas. Om vissa tecken inte har någon motsvarighet i målkodningen kommer textkodningen att misslyckas.

Se [Definiera en specifik mappning av kodningsinställningen](sms-protocol.md#SMSC-specifics) om du vill ha en mer allmän förklaring till kodningsprocessen.

#### Lagra inkommande MO i databasen {#incoming-mo-storing}

När det här alternativet är aktiverat lagras inkommande MO i databastabellen inSMS. Tabellen kan frågas med hjälp av frågeaktiviteten i vilket arbetsflöde som helst.

Adobe Campaign Classic lagrar alltid alla flerlägesobjekt i InSMS-databasen så det här alternativet är inte tillgängligt.

#### Aktivera KPI-uppdateringar i realtid under SR-bearbetning {#real-time-kpi}

När det här alternativet är aktiverat uppdateras KPI:er i realtid på huvudleveranssidan när fel-SR tas emot.

Nackdelen kan vara låg på grund av den databaskonflikt som genereras. Om det är inaktiverat uppdateras statistiken av **syncfromexec** arbetsflöde, körs var 20:e minut.

Adobe Campaign Classic har en helt annan mekanism för nyckeltal, så det här alternativet är inte tillgängligt.

#### Källnummer {#source-number}

Definierar standardkälladressen för meddelanden. Den här inställningen gäller endast om källnumret inte har angetts i leveransen.

Som standard skickas inte fältet för källnummer, så providern ersätter det för den korta koden.

Detta aktiverar funktionen för åsidosättning av avsändaradress/ADC.

#### Kort kod {#short-code}

Anger kontots kortnummer. Om flera korta koder används för det här kontot eller om den korta koden är okänd lämnar du det här fältet tomt.

Det kan vara praktiskt att ange kort kod för två funktioner:

* I förhandsvisningen visas den korta koden om inget källnummer anges. Det återspeglar det verkliga beteendet på mobiltelefonen.

* Inställningen blockeringslista för funktionen för automatiskt svar skickar bara till karantänen för en viss kort kod.

#### Käll-TON/NPI, mål-TON/NPI {#ton-npi}

TON (typ av nummer) och NPI (Numreringsplansindikator) beskrivs i avsnitt 5.2.5 i [Specifikation för SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (sidan 117). Dessa värden ska ställas in efter providerns behov.

De överförs som de är `source_addr_ton`, `source_addr_npi`, `dest_addr_ton` och `dest_addr_npi` fälten i `SUBMIT_SM PDU`.

#### Tjänsttyp {#service-type}

Det här fältet överförs som det är i `service_type` fält för `SUBMIT_SM PDU`. Ange detta efter leverantörens behov.

### Genomströmning och timeout {#throughput-timeouts}

Dessa inställningar styr alla timingaspekter av SMPP-kanalen. Vissa leverantörer kräver mycket exakt kontroll över meddelandehastighet, fönster och tidsinställningar för nya försök. Dessa inställningar bör anges till värden som matchar leverantörens kapacitet och villkoren som anges i deras kontrakt.

#### Skicka fönster {#sending-window}

Fönstret är antalet `SUBMIT_SM PDU`s som kan skickas utan att vänta på matchning `SUBMIT_SM_RESP`.

Exempel på en överföring med ett maximalt fönster på 4:

![](assets/do-not-localize/sms_protocol_2.png)

Fönstret hjälper till att öka genomströmningen när nätverkslänken har hög latens.  Fönstrets värde måste vara minst det antal SMS/s som multipliceras med länkens fördröjning i sekunder så att kopplingen aldrig väntar på en `SUBMIT_SM_RESP` innan du skickar nästa meddelande.
Om fönstret är för stort kan du skicka fler dubblettmeddelanden om det uppstår anslutningsproblem. Dessutom har de flesta leverantörer en mycket strikt begränsning för fönstret och vägrar att skicka meddelanden som överskrider gränsen.

Så här beräknar du den optimala skicka-fönsterformeln:

* Mät maximal fördröjning mellan `SUBMIT_SM` och `SUBMIT_SM_RESP`.

* Multiplicera detta värde i sekunder med maximal MT-genomströmning. Detta ger det optimala värdet för sändningsfönstret.

Exempel: Om du har 300 SMS/s angivet med maximal MT-genomströmning och det finns 100 ms fördröjning mellan `SUBMIT_SM` och `SUBMIT_SM_RESP` i genomsnitt är det optimala värdet `300×0.1 = 30`.

#### Maximal MT-genomströmning {#max-mt-throughput}

Maximalt antal MT per sekund och anslutning. Den här inställningen används strikt, MTA skickar aldrig meddelanden snabbare än den här gränsen. Det är användbart för leverantörer som kräver exakt begränsning.

Om du vill veta vilken total dataflödesgräns du har multiplicerar du talet med det totala antalet anslutningar enligt formeln ovan.

0 betyder ingen gräns, MTA skickar MT så snabbt som möjligt.

Det rekommenderas i allmänhet att denna inställning hålls under 1000, eftersom det är omöjligt att garantera en exakt dataström över detta antal om inte den slutliga arkitekturen är korrekt refererad och särskilt begärd SMPP-leverantör. Det kan vara bättre att öka antalet anslutningar så att de överstiger 1000 MT/s.

#### Tid före återanslutning {#time-reconnection}

När TCP-anslutningen bryts väntar anslutningen i så många sekunder innan ett anslutningsförsök görs.

#### MT:s förfalloperiod {#expiration-period}

Timeout mellan `SUBMIT_SM` och dess matchning `SUBMIT_SM_RESP`. Om `RESP` inte tas emot i tid, meddelandet betraktas som misslyckat och en global återförsöksprincip för MTA gäller.

#### Tidsgräns för bindning {#bind-timeout}

Timeout mellan TCP-anslutningsförsöket och `BIND_*_RESP` svara. När timeout uppstår stängs anslutningen av Adobe Campaign-anslutningen och den väntar på att anslutas igen innan den försöker igen.

#### fråge_länkperiod {#enquire-link-period}

`enquire_link` är en speciell typ av PDU som skickas för att hålla anslutningen vid liv. Perioden är i sekunder. Kampanjkopplingen skickar bara `enquire_link` när anslutningen är inaktiv för att spara bandbredd. Om inget RESP tas emot efter två gånger den här perioden betraktas anslutningen som död och en återanslutningsprocess utlöses.

### SMSC-specifikationer {#SMSC-specifics}

Dessa inställningar är avancerade inställningar som anpassar Adobe Campaign-anslutningen till de flesta SMPP-implementeringsegenskaper.

**Definiera en specifik mappning av kodningar**

Se [SMS-textkodning](sms-protocol.md#sms-text-encoding) om du vill ha mer information om textkodning.

Med den här inställningen kan du definiera en anpassad kodmappning, som skiljer sig från specifikationen. Du kan deklarera en lista med kodningar, tillsammans med deras `data_coding` värde.

MTA kommer att försöka koda med den första kodningen i listan. Om det inte fungerar kommer det att försöka använda nästa kodning i listan, osv. Om ingen kodning kan användas för att koda meddelandet inträffar ett fel. När kodningen har hittats skapar MTA `SUBMIT_SM PDU` med den kodade texten och `data_coding` fältuppsättningen med det värde som anges i tabellen.

Ordningen på objekten i tabellen är viktig: kodningar är försök uppifrån och ned. Du bör placera den billigaste eller mest rekommenderade kodningen högst upp i listan och sedan använda mer och mer kostsamma kodningar.

Observera att UCS-2 aldrig kommer att misslyckas eftersom det kan koda alla tecken som stöds i Adobe Campaign och att maxlängden för ett UCS-2 SMS är mycket mindre: Endast 70 tecken.

Du kan också använda den här inställningen för att tvinga en viss kodning att alltid användas genom att deklarera endast en rad i mappningstabellen.

Standardmappningen som används när kryssrutan inte är markerad motsvarar följande tabell:

| data_coding | Kodning |
|---|---|
| 0 | GSM |
| 9 | UCS-2 |

Detta innebär att MTA försöker koda meddelandet i GSM. Om det lyckas skickar det den med `data_coding` anges till 0.

Om meddelandet inte kan kodas i GSM kodas det i UCS-2 och ställs in `data_coding` till 8.

#### Aktivera message_payload {#enable-message-payload}

När det är avmarkerat delas lång SMS upp av MTA och skickas i flera `SUBMIT_SM PDU`är med UDH. Meddelandet kommer att disponeras om av mobiltelefonen efter UDH-data.

När det här alternativet är markerat skickas lång SMS i en SUBMIT_SM PDU, vilket placerar texten i det valfria fältet message_payload. Se [SMPP-specifikation](sms-protocol.md#ACS-SMPP-connector) om du vill ha mer information om detta.

Om den här funktionen är aktiverad kan Adobe Campaign inte räkna SMS-delar individuellt: alla meddelanden räknas som skickade i en del.

#### Skicka det fullständiga telefonnumret {#send-full-phone-number}

När den här kryssrutan inte är markerad skickas endast siffror i telefonnumret till leverantören (`destination_addr` fält för `SUBMIT_SM` fält). Detta är standardbeteendet eftersom den internationella nummerindikatorn, vanligtvis ett +-prefix, ersätts av TON- och NPI-fält i SMPP.

När kryssrutan är markerad skickas telefonnumret i befintligt skick, utan förbearbetning och potentiella mellanslag, + prefix eller nummertecken/hash/star-tecken.

Den här funktionen påverkar även funktionen för automatiskt svar på blockeringslista: När kryssrutan inte är markerad läggs ett +-prefix till telefonnummer som infogas i karantäntabellen för att kompensera för att +-prefixet tas bort från telefonnumret av själva SMPP-protokollet.

#### Hoppa över TLS-certifikatkontroll {#skip-tls}

När TLS är aktiverat hoppar du över alla certifikatkontroller.

När det här alternativet är markerat är anslutningen inte längre säker, utan bör inte aktiveras i produktionen.

Den kan vara användbar för felsökning och testning.

Du kan välja mellan tre olika värden för certifikatverifieringen:

* Fullständig certifieringskontroll (inklusive värdnamnet), standard.
* Hoppa över verifieringen av värdnamnet.
* Hoppa över certifikatverifieringen.

#### Bindning TON/NPI {#bind-ton-npi}

TON (typ av nummer) och NPI (Numreringsplansindikator) som beskrivs i avsnitt 5.2.5 i [Specifikation för SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (sidan 117). Dessa värden ska ställas in efter vad providern behöver.

De överförs som de är `addr_ton` och `addr_npi` fält i BIND PDU:n.

#### Adressintervall {#address-range}

Skickat som det är i fältet address_range i BIND PDU:n. Det här värdet ska ställas in efter vad providern behöver.

#### Ogiltigt antal ID-bekräftelser {#invalid-id}

Begränsar antalet **Meddelande-ID är ogiltigt** `DELIVER_SM_RESP` som kan skickas för en enskild SR.

**Detta bör endast användas för felsökningssyften som en lösning** och anges till 0 under normala förhållanden.

Exempel: När inställningen är 2:

* Providern skickar ett SR (`DELIVER_SM`) med ID &quot;1234&quot;.

* Det gick inte att hitta ID:t &quot;1234&quot; i databasen.

* Kopplingen räknar till 1 **Ogiltigt ID** fel för detta ID, så det skickar `DELIVER_SM_RESP` med felkoden&quot;Meddelande-ID ogiltigt&quot; (normalt beteende).

* Providern försöker på nytt samma SR med ID &quot;1234&quot;.

* Det gick fortfarande inte att hitta ID:t &quot;1234&quot; i databasen.

* Kopplingen räknar till 2 **Ogiltigt ID** fel för detta ID, så det skickar `DELIVER_SM_RESP` &quot;OK&quot;, även om det inte bearbetades korrekt.

* Den här funktionen är avsedd att tömma SR-buffertar på providersidan när ogiltiga SR-block är berättigade att meddelanden inte kan behandlas.

Om du ställer in det här fältet på 0 inaktiveras mekanismen där **Meddelande-ID är ogiltigt** returneras alltid, detta är normalt beteende.

Om du ställer in det här fältet på 1 kommer kopplingen alltid att svara &quot;OK&quot; även om ID:t är ogiltigt. Detta bör endast anges till 1 under övervakning, för felsökning och under kortast möjliga tid, t.ex. för att återhämta sig från ett problem på leverantörssidan.

#### Extraheringsregion för ID i SR {#regex-extraction}

SR-formatet används inte strikt av SMPP-protokollspecifikationen. Det är bara en rekommendation som beskrivs i [Tillägg B](sms-protocol.md#sr-error-management) (sidan 167) i specifikationen. Vissa SMPP-implementerare formaterar det här fältet annorlunda, så Adobe Campaign behöver ett sätt att extrahera rätt fält.

Som standard hämtas upp till 10 alfanumeriska tecken efter `id:`.

Regex måste ha exakt en hämtningsgrupp med en del inom parentes. Parenteser måste omge ID-delen. Regex-formatet är PCRE.

När du justerar den här inställningen måste du ta med så mycket kontext som möjligt för att undvika falska utlösare. Om det finns specifika prefix, till exempel `id:` i standarden, inkludera dem i regex. Använd också så mycket ordavgränsare (\b) som möjligt för att undvika att skriva in text mitt i ett ord.

Om det inte finns tillräckligt med sammanhang i regionen kan det medföra ett litet säkerhetsfel: det faktiska innehållet i meddelandet kan inkluderas i meddelandet. Om du bara matchar ett specifikt ID-format utan kontext, t.ex. ett UUID, kan det bero på att det faktiska textinnehållet parsas, t.ex. ett UUID som är inbäddat i textfältet, i stället för ID:t.

#### Regex används för att fastställa status för lyckat/fel {#regex-applied}

När meddelanden med en okänd kombination av stat/fel-fält påträffas, används dessa regex i statusfältet för att avgöra om SR lyckades eller inte. SR med statusvärden som inte matchar någon av dessa regexter ignoreras.

Som standard används de startvärden som börjar med `DELIV`, t.ex. `DELIVRD` i [Tillägg B](sms-protocol.md#sr-error-management), kommer att anses ha levererats och alla statusvärden som matchar fel, t.ex. `REJECTED`, `UNDELIV`, betraktas som fel.

#### ID-format i MT-bekräftelse {#id-format-mt}

Detta anger formatet på det ID som returneras i `message_id` fält för `SUBMIT_SM_RESP PDU`.

* **Ändra inte**: ID:t lagras som det är i databasen, som ASCII-kodad text. Ingen förbearbetning eller filtrering sker.

* **Decimaltal**: ID:t förväntas vara ett decimaltal i ASCII-format. Radavstånd och inledande nollor tas bort när den här inställningen används.

* **Hexadecimalt tal**: ID:t förväntas vara ett hexadecimalt tal i ASCII-format, utan inledande 0x eller avslutande h. ID:t konverteras sedan till ett decimaltal innan det lagras i databasen.

* **Hexadecimal sträng**: ID:t förväntas vara en ASCII-kodad text som i sin tur är en sträng med byte kodade som hexadecimala. I PDU:n hittar du t.ex. `0x34 0x31 0x34 0x32 0x34 0x33`, som motsvarar ASCII &quot;414243&quot;. Strängen avkodas sedan som en hexadecimal sträng med byte och du får &quot;ABC&quot; som ett resultat: Du kommer att lagra ID:t &quot;ABC&quot; i databasen.

#### ID-format i SR {#id-format-sr}

Detta anger formatet för det ID som fångats av `Extraction` region för ID i SR. Värden har samma innebörd och samma beteende som formatet i MT ovan.

**SR ID eller felkod i valfritt fält**

>[!NOTE]
>
>Endast tillgängligt i Adobe Campaign Classic Extended SMPP Connector.

Om du markerar det här alternativet läggs innehållet i valfria fält till i texten som bearbetas av regexterna ovan. Texten kommer att ha formatet `0xTAG:VALUE`, `0xTAG` är det fyrsiffriga hexadecimala värdet av taggen i versaler, t.ex. `0x002E`.

Du kanske vill hämta ID:t i `receipted_message_id` fält. Aktivera den här kryssrutan och följande text läggs till i statusen:

```
0x001E:05e3299e-8d37-49d0-97c6-8e4fe60c7739
```

I det här exemplet är 0x001E taggen för det valfria fältet och UUID är fältets värde.

Om du vill hämta det här värdet kan du nu ange följande region i Extraheringsregex för ID:t i fältet för SR:

```
\b0x001E:([0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12})\b
```

>[!IMPORTANT]
>
>Du kan bara fånga valfria fält som har textvärden (ASCII/UTF-8). Binära fält kan inte hämtas på ett tillförlitligt sätt med det aktuella regex-systemet.

**SR-id eller felkod i textfält**

Om du markerar det här alternativet visas **Text** fältet kommer att behållas under bearbetningen av statustexten för SR.

Detta är användbart om providern placerar viktiga data i det här fältet som ID eller status. Vanligtvis kan det här fältet tas bort eftersom det kan innehålla text som inte är ASCII-kodad och stör regex-bearbetningen.

Om du aktiverar det här alternativet kan ett mycket litet säkerhetsfel uppstå om `Extraction` Regex för ID:t i fältet SR är inte tillräckligt specifik. Innehållet i **Text** kan tolkas som ett ID och en angripare kan använda det för att mata in förfalskade ID:n, vilket kan leda till en situation där tjänsten inte kan användas delvis.

**Service ID-tagg**

Tillåter att en anpassad TLV läggs till. Det här fältet anger taggdelen. Värdet kan anpassas per leverans i **Service- eller program-ID** värdet i de avancerade parametrarna för leveransen.

Med den här inställningen kan du bara lägga till ett TLV-alternativ per meddelande.

### Automatiskt svar skickat till MO {#automatic-reply}

>[!IMPORTANT]
>
>I Adobe Campaign Classic och i en hybridarkitektur kräver tillämpning av autosvar för den utökade SMPP-anslutningen att du lägger till skrivåtkomst för mellanoperatorn på **Externt konto** mapp.

Med den här funktionen kan du snabbt svara på text till MO och hantera kortkod som skickas till blockeringslista.

The **Nyckelord** och **Kort kod** kolumner definierar villkor som utlöser det automatiska svaret. Om båda fälten matchar skickas MO och den ytterligare åtgärden utlöses. Om du vill ange ett jokertecken lämnar du fältet tomt. Nyckelordet matchar det första alfanumeriska ordet i MO-texten, och interpunktion och radavstånd ignoreras. Det betyder att **Nyckelord** fältet får inte innehålla blanksteg och måste vara ett enda ord.

The **Nyckelord** inställning är ett prefix. Om du till exempel anger &quot;AD&quot; kommer det att matcha &quot;AD&quot;, &quot;ADAPT&quot; och &quot;ADOBE&quot;. Om du har flera nyckelord med ett gemensamt prefix måste du vara uppmärksam på ordningen eftersom nyckelorden bearbetas uppifrån och ned.

The **Svara** kolumn är den text som ska besvaras. Det finns ingen tillgänglig personalisering i det här fältet. Om du lämnar det här fältet tomt kommer inget meddelande att skickas, men den ytterligare åtgärden kommer att utlösas ändå.

The **Ytterligare åtgärd** kolumn innehåller en extra åtgärd när båda **Nyckelord** och **Kort kod** match, empty short code match all short codes. Du kan skicka till karantän eller ta bort från karantän, ange inget svar på texten. Om du anger en **Ytterligare åtgärd** men lämna **Svara** fältet är tomt kommer åtgärden att utföras, men inget svar kommer att skickas. Karantän används bara för den angivna korta koden eller för alla korta koder om fältet lämnas tomt.

>[!IMPORTANT]
>
>Inställningen Skicka fullständigt telefonnummer påverkar beteendet för karantänmekanismen för automatiska svar: Om du inte markerar alternativet för att skicka fullständigt telefonnummer kommer det telefonnummer som sätts i karantän att föregås av ett plustecken (&quot;+&quot;) så att det blir kompatibelt med det internationella telefonnummerformatet.

Alla poster i tabellen bearbetas i den angivna ordningen tills en regel matchar. Om flera regler matchar en flerfunktionsregel tillämpas bara den översta regeln.

## Mallparametrar för SMS-leverans {#sms-delivery-template-parameters}

Vissa parametrar kan anges per leveransmall.

### Från fält {#from-field}

Det här fältet är valfritt. Det tillåter åsidosättande av avsändaradress (oADC). Innehållet i det här fältet placeras i `source_addr` fält för `SUBMIT_SM PDU`.

Fältet är begränsat till 21 tecken av SMPP-specifikationen, men vissa leverantörer kan tillåta längre värden. Observera också att mycket strikta begränsningar kan tillämpas i vissa länder, till exempel längd, innehåll och tillåtna tecken.

### Leveransparametrar {#delivery-parameters}

#### Högsta antal SMS per meddelande {#maximum-sms}

Den här inställningen fungerar bara om **Meddelandenyttolast** inställningen är inaktiverad. Om meddelandet kräver mer SMS än det här värdet utlöses ett fel.

SMS-protokollet begränsar SMS till 255 delar, men vissa mobiltelefoner har problem med att sätta ihop långa meddelanden med mer än 10 delar eller så beror gränsen på den exakta modellen. Vi rekommenderar att du inte går över 5 delar per meddelande.

På grund av hur personaliserade meddelanden fungerar i Adobe Campaign kan meddelandena variera i storlek. Att ha ett stort antal långa meddelanden kan öka sändningskostnaderna.

#### Överföringsläge {#transmission-mode}

Det här fältet anger vilken typ av SMS du vill överföra: normala meddelanden eller flash-meddelanden som lagras på mobilen eller SIM-kortet.

Den här inställningen överförs i `dest_addr_subunit` valfritt fält i `SUBMIT_SM PDU`.

* **Ospecificerad** skickar inget valfritt fält i PDU:n.

* **Flash** anger värdet till 1. Det skickar ett flash-meddelande som visas på mobilen och inte lagras i minnet.

* **Normal** anger värdet till 0. Det skickar ett normalt meddelande.

* **Spara på mobilen** anger värdet till 2. Den instruerar telefonen att lagra SMS:et i det interna minnet.

* **Spara vid terminal** anger värdet till 3. Telefonen uppmanas att lagra SMS:et på SIM-kortet.

#### Giltighetsperiod {#validity-period}

Giltighetsperioden överförs i `validity_period` fält för `SUBMIT_SM PDU`. Datumet formateras alltid som ett absolut UTC-tidsformat, datumfältet avslutas med &quot;00+&quot;.

## Utökad allmän SMPP-anslutning {#acc-extended-connector}

![](assets/do-not-localize/sms_protocol_4.png)

Pilar representerar dataflöden.

När leveransdelar skickas visar MTA-barnen MTA. Antalet underordnade MTA-processer är dynamiskt och beror på en konfiguration i serverConf.xml. Varje MTA-underordnad instansierar kopplingen `CSmppConnectorWorker` som ansluter till SMPP-providern. Anslutningar hålls aktiva så länge som MTA-barnet hålls vid liv, som även kan konfigureras i serverConf.xml.

SMS-processen behandlar endast SR, den ansluter till providern och låter anslutningen vara öppen. Processen återansluter var 10:e minut för att läsa in nya inställningar, vilket är en normal åtgärd.

### Matchande MT-, SR- och broadcast-poster {#matching-mt}

Ett mellanliggande register `nmsProviderMsgId` används för att lagra MT- och SR-data temporärt innan de implementeras asynkront i utsändningsloggen.

`nmsProviderMsgId` tabellen har tre grupper med kolumner:

* Kolumner som uppdateras när en MT skickas och bekräftas: `iBroadLogId`, `iDeliveryId`

* Kolumner som uppdateras när en SR tas emot: `iMsgId`, `iStatus`

* Kolumner som alltid uppdateras: `tsCreated`, `sProviderId`

När både MT och SR är klara bör du ha fullständiga rader, med både sändningsinformation och statusinformation.

Här, `iMsgId` är länkad till `nmsBroadLogMsg` tabellen, vilket anger det fullständiga status-/felmeddelandet.

SMS-processen söker efter hela rader varje minut och bearbetar dem sedan asynkront:

* Hela raden läses.
* SMS-processen beräknar namnet på utsändningstabellen baserat på leveransmappningen.
* SMS-processen uppdaterar utsändningstabellen med meddelande-ID och status.

**Genomströmning och parallella anslutningar**

Varje MTA-underordnad skapar en konfigurerbar mängd anslutningar, så om du begränsar antalet MTA-underordnade kommer antalet anslutningar att begränsas. Eftersom korrelationen mellan de underordnade MTA-processerna och trafiken är korrelerad kan detta styras något, men ändå lite oförutsägbart.

## Innan du publicerar {#checklist}

Den här checklistan innehåller en lista med saker som du bör kontrollera innan du publicerar. En ofullständig konfiguration kan leda till många problem.

### Kontrollera om det finns externa kontokonflikter {#external-account-conflict}

Kontrollera att du inte har gamla SMS-externa konton. Om du lämnar testkontot inaktiverat riskerar du att det återaktiveras i produktionssystemet och skapar potentiella konflikter.

Om du har flera konton på samma Adobe Campaign-instans som ansluter till samma leverantör, kontaktar du leverantören för att se till att de verkligen särskiljer anslutningar mellan dessa konton. Om du har flera konton med samma inloggning krävs extra konfiguration.

### Aktivera utförliga SMPP-spår under kontroller {#enable-verbose}

Du bör alltid aktivera utförliga SMPP-spår under kontroller.
Även om du inte kan kontrollera loggarna själv är det enklare för [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) för att hjälpa dig.

### Testa ditt SMS {#test}

* **Skicka SMS med alla slags tecken**
Om du behöver skicka SMS med tecken som inte är GSM eller ASCII kan du försöka skicka meddelanden med så många olika tecken som möjligt. Om du ställer in en anpassad teckenmappningstabell skickar du minst ett SMS för alla möjliga 
`data_coding` värden.

* **Kontrollera att SR har bearbetats korrekt**
SMS:et ska markeras som mottaget i leveransloggen. Leveransloggen bör slutföras och se ut så här: Kontrollera att du har ändrat leveransleverantörens namn. Leveransloggen får aldrig innehålla    `SR yourProvider stat=DELIVRD err=000|#MESSAGE`
Kontrollera att du har ändrat leveransleverantörens namn. Leveransloggen får aldrig innehålla **SR allmänt** i produktionsmiljöer.

* **Kontrollera att flerlägesobjekt har bearbetats**
Om du behöver bearbeta MO (automatiska svar, lagra MO i databasen osv.) försök att göra några tester. Skicka några SMS för alla automatiska svarsnyckelord och kontrollera om svaret är tillräckligt snabbt, inte mer än några sekunder.
Kontrollera i loggen att Adobe Campaign svarar med ett lyckat resultat 
`DELIVER_SM_RESP` (command_status=0).

### Kontrollera PDU:er {#check-pdus}

Även om meddelandena ser bra ut är det viktigt att kontrollera att PDU:er är korrekt formaterade.

Detta steg är nödvändigt vid anslutning till en leverantör som inte var ansluten till Adobe Campaign tidigare.

#### BIND {#bind}

Kontrollera att `BIND_* PDUs` skickas korrekt. Det viktigaste att kontrollera är att providern alltid returnerar lyckad `BIND_*_RESP PDUs` (command_status = 0).

Kontrollera att det inte finns för många `BIND_* PDU`s. Om det finns för många av dem kan det tyda på att anslutningen är instabil. Se [Problem med instabila anslutningar](sms-protocol.md#issues-unstable-connection) för mer information.

#### INQUIRE_LINK {#enquire-link-pdus}

Kontrollera att `ENQUIRE_LINK PDU`Utbyts regelbundet när anslutningen är inaktiv.

**SUBMIT_SM / DELIVER_SM**

Skicka ett meddelande och sök sedan i loggarna efter dess motsvarande `SUBMIT_SM`, `SUBMIT_SM_RESP`, `DELIVER_SM` och `DELIVER_SM_RESP PDU`s.

Med `SUBMIT_SM PDU`:

* Kontrollera att `data_coding` är korrekt, 0 som standard.
* Kontrollera att `short_message` är korrekt kodad. Försök att avkoda den med en hexadecimal konverterare som stöder flera kodningar.

Med `SUBMIT_SM_RESP PDU`:

* Kontrollera att den lyckades, command_status = 0.
* Kontrollera att brödtexten innehåller ett korrekt formaterat ID följt av byte &#39;0&#39;.

Med `DELIVER_SM PDU`:

* Avkoda den hexadecimala `short_message` fält.
* Kontrollera med ett regex-kontrollverktyg att det område som definieras i `Extraction` region för ID:t i SR returnerar exakt en hämtningsgrupp och att den hämtar hela ID:t i meddelandet.
* Kontrollera att det extraherade ID:t matchar det som finns i `SUBMIT_SM_RESP`.
* Kontrollera att regex definieras i `Extraction` statusregion i SR returnerar innehållet i statusfältet.
* Kontrollera att regex definieras i `Extraction` regex för felet i SR returnerar felfältets innehåll.

Med `DELIVER_SM_RESP PDU`:

* Kontrollera att det skickades snabbt efter att du fått `DELIVER_SM PDU`, vanligtvis mindre än 1 sekund.
* Kontrollera att den lyckades, command_status = 0.

### Kontrollera med din leverantör {#provider}

Även om ditt SMS fungerar som det ska kan du kontakta leverantören och se om allt är i ordning.

### Inaktivera utförliga SMPP-spår {#disable-verbose}

När alla kontroller är slutförda är det sista du behöver **Inaktivera utförliga SMPP-spår** för att inte generera för många loggar. Du kan återaktivera dem för felsökning även i produktionssystem.
