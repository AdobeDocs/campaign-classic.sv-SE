---
product: campaign
title: Förstå leveransfel
description: Lär dig mer om leveransfel
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2614'
ht-degree: 14%

---

# Förstå leveransfel{#understanding-delivery-failures}

![](../../assets/common.svg)

## Om leveransfel {#about-delivery-failures}

När ett meddelande (e-post, SMS, push-meddelanden) inte kan skickas till en profil skickar fjärrservern automatiskt ett felmeddelande som hämtas av Adobe Campaign-plattformen och är kvalificerat för att avgöra om e-postadressen eller telefonnumret ska placeras i karantän eller inte. Se [E-posthantering](#bounce-mail-management).

>[!NOTE]
>
>**E-postfelmeddelanden** (eller &quot;studsningar&quot;) kvalificeras av Enhanced MTA (synkrona studsningar) eller av inMail-processen (asynkrona studsningar).
>
>**SMS**-felmeddelanden (eller &quot;SR&quot; för &quot;Statusrapport&quot;) kvalificeras av MTA-processen.

När ett meddelande har skickats kan du i leveransloggarna visa leveransstatus för varje profil och tillhörande feltyp och orsak.

Meddelanden kan också uteslutas under färdigställandet av leveransen om en adress sätts i karantän eller om en profil finns på blockeringslista. Exkluderade meddelanden visas på kontrollpanelen för leverans.

**Relaterade ämnen:**

* [Leveransloggar och historik](delivery-dashboard.md#delivery-logs-and-history)
* [Misslyckad status](delivery-performances.md#failed-status)
* [Typ av leveransfel och orsaker](#delivery-failure-types-and-reasons)

## Typ av leveransfel och orsaker {#delivery-failure-types-and-reasons}

Det finns tre typer av fel när ett meddelande misslyckas. Varje feltyp avgör om en adress skickas till karantän. Mer information finns i [Villkor för att skicka en adress till karantän](understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

* **Hård**: Ett &quot;hårt&quot; fel indikerar en ogiltig adress. Detta inbegriper ett felmeddelande som uttryckligen anger att adressen är ogiltig, till exempel: &quot;Okänd användare&quot;.
* **Mjuk**: Detta kan vara ett tillfälligt fel eller ett fel som inte gick att kategorisera, till exempel: &quot;Ogiltig domän&quot; eller &quot;Postlådan är full&quot;.
* **Ignorerad**: Det här är ett fel som är tillfälligt, till exempel &quot;Frånvarande&quot;, eller ett tekniskt fel, till exempel om avsändartypen är &quot;e-postadministratör&quot;.

Möjliga orsaker till leveransfel är:

<table> 
 <tbody> 
  <tr> 
   <td> Feletikett </td> 
   <td> Feltyp </td> 
   <td> Tekniskt värde </td> 
   <td> Beskrivning </td> 
  </tr> 
  <tr> 
   <td> Kontot är inaktiverat </td> 
   <td> Mjuk/hård </td> 
   <td> 4 </td> 
   <td> Kontot som är länkat till adressen är inte längre aktivt. När IAP (Internet Access Provider) upptäcker en lång inaktivitetsperiod kan den stänga användarens konto. Det går då inte att skicka till användarens adress. Om kontot är tillfälligt inaktiverat på grund av sex månaders inaktivitet och fortfarande kan aktiveras, tilldelas statusen Med fel och kontot provas igen tills felräknaren når 5. Om felmeddelandet talar om att kontot är permanent inaktiverat ställs det in direkt på Karantän.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adress i karantän </td> 
   <td> Hård </td> 
   <td> 9 </td> 
   <td> Adressen placerades i karantän.<br /> </td> 
  </tr> 
  <tr> 
   <td> Adressen har inte angetts </td> 
   <td> Hård </td> 
   <td> 7 </td> 
   <td> Ingen adress har angetts för mottagaren.<br /> </td> 
  </tr> 
  <tr> 
   <td> Felaktig adress </td> 
   <td> Ignorerad </td> 
   <td> 14 </td> 
   <td> Kvalitetsklassificeringen för den här adressen är för låg.<br /> </td> 
  </tr> 
  <tr> 
   <td> Blocklist adress </td> 
   <td> Hård </td> 
   <td> 8 </td> 
   <td> Adressen lades till i blockeringslista vid tidpunkten för sändningen. Den här statusen används för att importera data från externa listor och externa system till listan över Adobe Campaign-karantän.<br /> </td> 
  </tr> 
  <tr> 
   <td> Kontrolladress </td> 
   <td> Ignorerad </td> 
   <td> 127 </td> 
   <td> Mottagarens adress är en del av kontrollgruppen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dubbel </td> 
   <td> Ignorerad </td> 
   <td> 10 </td> 
   <td> Mottagarens adress fanns redan i den här leveransen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Felet ignorerades </td> 
   <td> Ignorerad </td> 
   <td> 25 </td> 
   <td> Adressen är på tillåtelselista. Felet ignoreras därför och ett e-postmeddelande skickas.<br /> </td> 
  </tr> 
  <tr> 
   <td> Uteslutet efter skiljedom </td> 
   <td> Ignorerad </td> 
   <td> 12 </td> 
   <td> Mottagaren uteslöts av en kampanjtypologiregel av typen"medling".<br /> </td> 
  </tr> 
  <tr> 
   <td> Exkluderad av en SQL-regel </td> 
   <td> Ignorerad </td> 
   <td> 11 </td> 
   <td> Mottagaren uteslöts av en kampanjtypologiregel av typen SQL.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ogiltig domän </td> 
   <td> Mjuk </td> 
   <td> 2 </td> 
   <td> Domänen för e-postadressen är felaktig eller finns inte längre. Den här profilen används igen tills felantalet är 5. Därefter sätts postens status till Karantän och inga nya försök görs.<br /> </td> 
  </tr> 
  <tr> 
   <td> Postlådan är full </td> 
   <td> Mjuk </td> 
   <td> 5 </td> 
   <td> Den här användarens postlåda är full och kan inte ta emot fler meddelanden. Den här profilen används igen tills felantalet är 5. Därefter sätts postens status till Karantän och inga nya försök görs.<br /> Den här typen av fel hanteras av en rensningsprocess. Adressen har en giltig status efter 30 dagar.<br /> Varning: För att adressen ska tas bort automatiskt från listan över adresser i karantän måste det tekniska arbetsflödet för databassorensning startas.<br /> </td> 
  </tr> 
  <tr> 
   <td> Inte ansluten </td> 
   <td> Ignorerad </td> 
   <td> 6 </td> 
   <td> Mottagarens mobiltelefon är avstängd eller inte ansluten till nätverket när meddelandet skickas.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ej definierad </td> 
   <td> Ej definierad </td> 
   <td> 0 </td> 
   <td> Adressen kvalificeras eftersom felet inte har ökats ännu. Den här typen av fel inträffar när ett nytt felmeddelande skickas av servern: Det kan vara ett isolerat fel, men om det inträffar igen ökar felräknaren, som varnar de tekniska teamen. De kan sedan göra en meddelandeanalys och kvalificera felet via <span class="uicontrol">Administration</span> / <span class="uicontrol">Kampanjhantering</span> / <span class="uicontrol">Hantering av ej slutprodukter</span> i trädstrukturen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ej berättigade till erbjudandena </td> 
   <td> Ignorerad </td> 
   <td> 16 </td> 
   <td> Mottagaren var inte berättigad till erbjudandena i leveransen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Avvisad </td> 
   <td> Mjuk/hård </td> 
   <td> 20 </td> 
   <td> Adressen har placerats i karantän på grund av säkerhetsfeedback som en skräppostrapport. Enligt felet görs ett nytt försök att ange adressen tills felräknaren når 5 eller skickas direkt till karantän.<br /> </td> 
  </tr> 
  <tr> 
   <td> Målet är begränsat </td> 
   <td> Ignorerad </td> 
   <td> 17 </td> 
   <td> Den maximala leveransstorleken har uppnåtts för mottagaren.<br /> </td> 
  </tr> 
  <tr> 
   <td> Okvalificerad adress </td> 
   <td> Ignorerad </td> 
   <td> 15 </td> 
   <td> Postadressen har inte kvalificerats.<br /> </td> 
  </tr> 
  <tr> 
   <td> Onåbar </td> 
   <td> Mjuk/hård </td> 
   <td> 3 </td> 
   <td> Ett fel har uppstått i meddelandeleveranskedjan. Det kan vara en incident på SMTP-relä, en domän som inte går att nå för tillfället, osv. Enligt felet görs ett nytt försök att ange adressen tills felräknaren når 5 eller skickas direkt till karantän.<br /> </td> 
  </tr> 
  <tr> 
   <td> Okänd användare </td> 
   <td> Hård </td> 
   <td> 1 </td> 
   <td> Adressen finns inte. Inga fler leveransförsök kommer att göras för den här profilen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Försök igen efter ett tillfälligt leveransfel {#retries-after-a-delivery-temporary-failure}

Om ett meddelande misslyckas på grund av en **Mjuk** eller **Ignorerad** fel som är tillfälliga, försök utförs igen under leveransens varaktighet.

>[!NOTE]
>
>Tillfälligt olevererade meddelanden kan bara relateras till en **Mjuk** eller **Ignorerad** fel, men inte ett **Hård** fel (se [Typ av leveransfel och orsaker](#delivery-failure-types-and-reasons)).

>[!IMPORTANT]
>
>För värdbaserade eller hybridinstallationer, om du har uppgraderat till [Förbättrad MTA](sending-with-enhanced-mta.md)används inte längre inställningarna för nya försök i leveransen av Campaign. Mjuka avhoppsförsök och hur lång tid det tar mellan dem bestäms av den förbättrade MTA-metoden baserat på typ och allvarlighetsgrad för de avhoppssvar som kommer tillbaka från meddelandets e-postdomän.

För anläggningsinstallationer och värdbaserade/hybridinstallationer som använder det äldre Campaign MTA går du till de avancerade parametrarna för leverans- eller leveransmallen och anger önskad varaktighet i motsvarande fält för att ändra varaktigheten för en leverans. Se [Definiera giltighetsperiod](steps-sending-the-delivery.md#defining-validity-period).

Standardkonfigurationen tillåter fem försök med en timmes intervall, följt av ett nytt försök per dag i fyra dagar. Antalet försök kan ändras globalt (kontakta den tekniska administratören på Adobe) eller för varje leverans- eller leveransmall (se [Konfigurerar återförsök](steps-sending-the-delivery.md#configuring-retries)).

## Synkrona och asynkrona fel {#synchronous-and-asynchronous-errors}

Ett meddelande kan misslyckas omedelbart (synkront fel), eller senare, efter att det har skickats (asynkront fel).

* Synkront fel: Om fjärre-postservern som kontaktades av Adobe Campaign-leveransservern omedelbart returnerade ett felmeddelande, får leveransen inte skickas till profilens server. Adobe Campaign kvalificerar varje fel för att avgöra om e-postadresserna i fråga ska sättas i karantän eller inte. Se [Kvalifikation av studsmeddelanden](#bounce-mail-qualification).
* Asynkront fel: Ett studsmeddelande eller en SR skickades senare av den mottagande servern. Det här e-postmeddelandet läses in i en teknisk postlåda som programmet använder för att etikettera meddelanden med ett fel. Asynkrona fel kan uppstå upp till en vecka efter att en leverans har skickats.

   >[!NOTE]
   >
   >Konfiguration av studspostlådan finns i [det här avsnittet](../../installation/using/deploying-an-instance.md#managing-bounced-emails).

   The [feedback-slinga](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops) fungerar som studsmeddelanden. När en användare kvalificerar ett e-postmeddelande som skräppost kan du konfigurera e-postregler i Adobe Campaign så att alla leveranser till den här användaren blockeras. Meddelanden som skickas till användare som har kvalificerat ett e-postmeddelande som skräppost omdirigeras automatiskt till en e-postruta som har skapats för detta ändamål. Dessa användares adresser är till blockeringslista, även om de inte klickade på länken för att ta bort prenumerationen. Adresserna finns i blockeringslista i (**NmsAddress**) karantänregister och inte i (**NmsRecipient**) mottagartabell.

   >[!NOTE]
   >
   >Klagomålshanteringen beskrivs närmare i [Leveranshantering](about-deliverability.md) -avsnitt.

## E-posthantering {#bounce-mail-management}

På Adobe Campaign-plattformen kan du hantera e-postleveransfel via studsfunktionen.

När ett e-postmeddelande inte kan levereras till en mottagare, returnerar fjärrmeddelandeservern automatiskt ett felmeddelande (studsmeddelanden) till en teknisk inkorg som är utformad för detta.

För lokala installationer och värdbaserade/hybridinstallationer som använder det äldre Campaign MTA samlas felmeddelanden in av Adobe Campaign-plattformen och kvalificeras av InMail-processen för att berika listan över regler för e-posthantering.

>[!IMPORTANT]
>
>För värdbaserade eller hybridinstallationer, om du har uppgraderat till [Förbättrad MTA](sending-with-enhanced-mta.md)används inte längre de flesta regler för e-posthantering. Mer information finns i [det här avsnittet](#email-management-rules).

### Kvalifikation av studsmeddelanden {#bounce-mail-qualification}

>[!IMPORTANT]
>
>För värdbaserade eller hybridinstallationer, om du har uppgraderat till [Förbättrad MTA](sending-with-enhanced-mta.md):
>
>* Studentkvalifikationer i **[!UICONTROL Delivery log qualification]** tabellen används inte längre för **synkron** felmeddelanden vid leveransfel. Den förbättrade MTA-metoden avgör studstyp och kvalifikationer och skickar tillbaka informationen till Campaign.
>
>* **** Asynkrona studsningar är fortfarande kvalificerade inMail-processen enligt **[!UICONTROL Inbound email]**-reglerna. Mer information finns i [Regler för e-posthantering](#email-management-rules).
>
>* För instanser som använder den förbättrade MTA-metoden **utan webhooks/EFS**, **[!UICONTROL Inbound email]** regler kommer också att användas för att bearbeta synkrona studsmeddelanden från Förbättrat MTA, med samma e-postadress som för asynkrona studsmeddelanden.


För lokala installationer och värdbaserade/hybridinstallationer som använder den äldre Campaign MTA får Adobe Campaign-leveransservern ett felmeddelande från meddelandeservern eller fjärr-DNS-servern när leveransen av ett e-postmeddelande misslyckas. Listan med fel består av strängar i meddelandet som returneras av fjärrservern. Feltyper och orsaker tilldelas till varje felmeddelande.

Den här listan är tillgänglig via **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** nod. Det innehåller alla regler som Adobe Campaign använder för att kvalificera leveransfel. Den är inte uttömmande och uppdateras regelbundet av Adobe Campaign och kan även hanteras av användaren.

![](assets/tech_quarant_rules_qualif.png)

Meddelandet som returnerades av fjärrservern vid den första förekomsten av den här feltypen visas i **[!UICONTROL First text]** kolumn i **[!UICONTROL Delivery log qualification]** tabell. Om den här kolumnen inte visas klickar du på **[!UICONTROL Configure list]** längst ned till höger i listan för att markera den.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign filtrerar det här meddelandet för att ta bort variabelinnehållet (t.ex. ID:n, datum, e-postadresser, telefonnummer osv.) och visar det filtrerade resultatet i **[!UICONTROL Text]** kolumn. Variablerna ersätts med **`#xxx#`**, förutom adresser som ersätts med **`*`**.

Med den här processen kan du sammanföra alla fel av samma typ och undvika flera poster för liknande fel i tabellen för leveransloggskvalificering.

>[!NOTE]
>
>The **[!UICONTROL Number of occurrences]** visas antalet förekomster av meddelandet i listan. Den är begränsad till 100 000 förekomster. Du kan redigera fältet om du till exempel vill återställa det.

Studsade e-postmeddelanden kan ha följande kvalificeringsstatus:

* **[!UICONTROL To qualify]** : studsposten inte kunde kvalificeras. Kvalificering måste tilldelas slutkundsteamet för att garantera effektiv plattformsleverans. Så länge den inte är kvalificerad används studentposten inte för att utöka listan över regler för e-posthantering.
* **[!UICONTROL Keep]** : studsmeddelandet är kvalificerat och kommer att användas av **Uppdatera för leverans** arbetsflöde som ska jämföras med befintliga regler för e-posthantering och berika listan.
* **[!UICONTROL Ignore]** : studsmeddelandet ignoreras av Campaign MTA, vilket innebär att den här studsen aldrig kommer att leda till att mottagarens adress sätts i karantän. Den används inte av **Uppdatera för leverans** arbetsflödet och det skickas inte till klientinstanser.

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>Om en Internet-leverantör skulle råka ut för ett avbrott markeras e-post som skickas via Campaign felaktigt som studsar. För att korrigera detta måste du uppdatera studskompetens. Mer information finns på [den här sidan](update-bounce-qualification.md).

### Regler för e-posthantering {#email-management-rules}

>[!IMPORTANT]
>
>För värdbaserade eller hybridinstallationer, om du har uppgraderat till [Förbättrad MTA](sending-with-enhanced-mta.md)används inte längre de flesta regler för e-posthantering. Mer information finns i avsnitten nedan.

E-postregler nås via **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** nod. Regler för e-posthantering visas i fönstrets nedre del.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>Standardparametrarna för plattformen konfigureras i distributionsguiden. Mer information finns i [det här avsnittet](../../installation/using/deploying-an-instance.md).

Standardreglerna är följande.

>[!IMPORTANT]
>
>* Leveransservern (MTA) måste startas om om om parametrarna har ändrats.
>* Ändringen eller skapandet av hanteringsregler är endast till för expertanvändare.


#### Inkommande e-post {#inbound-email}

>[!IMPORTANT]
>
>För värdbaserade eller hybridinstallationer, om du har uppgraderat till [Förbättrad MTA](sending-with-enhanced-mta.md)och om instansen har **Webhooks/EFS** funktionalitet, **[!UICONTROL Inbound email]** regler används inte längre för synkrona felmeddelanden vid leveransfel. Mer information finns i [det här avsnittet](#bounce-mail-qualification).

För lokala installationer och värdbaserade/hybridinstallationer som använder det äldre Campaign MTA innehåller dessa regler en lista över teckensträngar som kan returneras av fjärrservrar och som gör att du kan kvalificera felet (**Hård**, **Mjuk** eller **Ignorerad**).

När ett e-postmeddelande misslyckas returnerar fjärrservern ett studsmeddelande till den adress som anges i plattformsparametrarna. Adobe Campaign jämför innehållet i varje studentpost med strängarna i listan över regler och tilldelar det sedan till en av de tre [feltyper](#delivery-failure-types-and-reasons).

>[!NOTE]
>
>Användaren kan skapa egna regler. När du importerar ett paket och uppdaterar data via **Uppdatera för leverans** arbetsflöde skrivs de regler som användaren har skapat över.

Mer information om studentkvalifikationer finns i [det här avsnittet](#bounce-mail-qualification).

#### Domänhantering {#domain-management}

>[!IMPORTANT]
>
>För värdbaserade eller hybridinstallationer, om du har uppgraderat till [Förbättrad MTA](sending-with-enhanced-mta.md), **[!UICONTROL Domain management]** regler används inte längre. **DKIM-signering (DomainKeys Identified Mail)** för e-postautentisering görs av den utökade MTA:n för alla meddelanden med alla domäner. Det signerar inte med **Avsändar-ID**, **DomainKeys** eller **S/MIME** om inte annat anges på den förbättrade MTA-nivån.

För lokala installationer och värdbaserade/hybridinstallationer som använder den äldre Campaign MTA-metoden, använder Adobe Campaign meddelandeserver en enda **Domänhantering** regel för alla domäner.

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* Du kan välja om du vill aktivera vissa identifieringsstandarder och krypteringsnycklar eller inte för att kontrollera domännamnet, till exempel **Avsändarens ID**, **DomainKeys**, **DKIM** och **S/MIME**.
* The **SMTP-relä** Med parametrar kan du konfigurera IP-adressen och porten för en reläserver för en viss domän. Mer information finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#smtp-relay).

Om dina meddelanden visas i Outlook med **[!UICONTROL on behalf of]** i avsändarens adress, kontrollera att du inte signerar dina e-postmeddelanden med **Avsändarens ID**, som är den inaktuella autentiseringsstandarden för e-postautentisering från Microsoft. Om **[!UICONTROL Sender ID]** är aktiverat, avmarkera motsvarande ruta och kontakta [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Leveransen påverkas inte.

#### MX-hantering {#mx-management}

>[!IMPORTANT]
>
>För värdbaserade eller hybridinstallationer, om du har uppgraderat till [Förbättrad MTA](sending-with-enhanced-mta.md), **[!UICONTROL MX management]** regler för leveransflöde används inte längre. Den utökade MTA-servern använder sina egna MX-regler som gör att den kan anpassa din genomströmning efter domän baserat på ditt eget historiska e-postrykte och på realtidsfeedback som kommer från de domäner där du skickar e-post.

För anläggningsinstallationer och värdbaserade/hybridinstallationer som använder det äldre kampanjavtalet MTA:

* MX-hanteringsreglerna används för att reglera flödet av utgående e-post för en viss domän. De samplar studsmeddelandena och blockerar sändningarna där så är lämpligt.

* Adobe Campaign meddelandeserver tillämpar regler som är specifika för domänerna och sedan reglerna för det allmänna fallet som representeras av en asterisk i listan med regler.

* Om du vill konfigurera MX-hanteringsregler anger du bara ett tröskelvärde och väljer vissa SMTP-parametrar. A **tröskelvärde** är en gräns som beräknas som ett felprocentvärde över vilket alla meddelanden till en viss domän blockeras. I det allmänna fallet, för minst 300 meddelanden, blockeras sändning av e-postmeddelanden under tre timmar om felprocenten når 90 %.

Mer information om MX-hantering finns i [det här avsnittet](../../installation/using/email-deliverability.md#mx-configuration).
