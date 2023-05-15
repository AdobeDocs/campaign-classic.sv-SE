---
product: campaign
title: God praxis för datamodell
description: Lär dig hur du arbetar med datamodellen Campaign Classic
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Data Model
exl-id: 9c59b89c-3542-4a17-a46f-3a1e58de0748
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '3988'
ht-degree: 0%

---

# God praxis för datamodell{#data-model-best-practices}

I det här dokumentet beskrivs viktiga rekommendationer när du utformar din Adobe Campaign-datamodell.

Om du vill få en bättre förståelse för de inbyggda tabellerna i Campaign och deras interaktion kan du läsa [det här avsnittet](../../configuration/using/about-data-model.md) -avsnitt.

Läs [den här dokumentationen](../../configuration/using/about-schema-reference.md) för att komma igång med Campaign-scheman. Lär dig hur du konfigurerar tilläggsscheman för att utöka den konceptuella datamodellen för Adobe Campaign-databasen i [det här dokumentet](../../configuration/using/about-schema-edition.md).

## Översikt {#overview}

Adobe Campaign-systemet är extremt flexibelt och kan byggas ut utöver den ursprungliga implementeringen. Men även om möjligheterna är oändliga är det viktigt att fatta kloka beslut och bygga starka grunder för att börja utforma din datamodell.

Det här dokumentet innehåller vanliga användningsexempel och metodtips om hur du kan skapa rätt Adobe Campaign-verktyg.

## Datamodellarkitektur {#data-model-architecture}

Adobe Campaign är ett kraftfullt kanalövergripande kampanjhanteringssystem som kan hjälpa er att anpassa era online- och offlinestrategier för att skapa personaliserade kundupplevelser.

### Kundfokuserat tillvägagångssätt {#customer-centric-approach}

De flesta e-postleverantörer kommunicerar med kunderna via en listcentrerad strategi, men Adobe Campaign förlitar sig på en relationsdatabas för att få en bredare bild av kunderna och deras attribut.

Detta kundcentrerade tillvägagångssätt visas i tabellen nedan. The **Mottagare** tabellen i grått är den viktigaste kundtabellen som allt byggs kring:

![](assets/customer-centric-data-model.png)

Om du vill få åtkomst till beskrivningen av varje tabell går du till **[!UICONTROL Admin > Configuration > Data schemas]**, välj en resurs i listan och klicka på **[!UICONTROL Documentation]** -fliken.

Adobe Campaign standarddatamodell presenteras i [det här dokumentet](../../configuration/using/data-model-description.md).

>[!NOTE]
>
>Adobe Campaign Classic gör det möjligt att skapa en anpassad kundtabell. I de flesta fall rekommenderas dock att man använder [Mottagarregister](../../configuration/using/about-data-model.md#default-recipient-table) som redan har färdiga tabeller och funktioner.

### Data för Adobe Campaign {#data-for-campaign}

Vilka data ska skickas till Adobe Campaign? Det är viktigt att kunna avgöra vilka data som krävs för era marknadsföringsaktiviteter.

>[!NOTE]
>
>Adobe Campaign är varken ett data warehouse eller ett rapportverktyg. Därför ska du inte importera alla möjliga kunder och tillhörande information till Adobe Campaign, eller importera data som bara ska användas för att skapa rapporter.

Om du vill avgöra om ett attribut behövs eller inte i Adobe Campaign, frågar du dig själv om det hamnar i någon av följande kategorier:

* Attribut som används för **segmentering**
* Attribut som används för **datahanteringsprocesser** (t.ex. aggregerad beräkning)
* Attribut som används för **personalisering**

Om du inte hamnar i något av dessa behöver du troligen inte det här attributet i Adobe Campaign.

### Val av datatyper {#data-types}

Följ de bästa metoderna nedan för att konfigurera data i Adobe Campaign för att säkerställa att din systemarkitektur och prestanda är bra.

* En stor tabell ska i de flesta fall ha numeriska fält och innehålla länkar till referenstabeller (när du arbetar med värdelista).
* The **expr** Med -attribut kan du definiera ett schemaattribut som ett beräknat fält i stället för ett fysiskt uppsättningsvärde i en tabell. Detta gör att du kan komma åt information i ett annat format (till exempel ålder och födelsedatum) utan att behöva lagra båda värdena. Detta är ett bra sätt att undvika att duplicera fält. I mottagartabellen används till exempel ett uttryck för domänen, som redan finns i e-postfältet.
* När uttrycksberäkningen är komplex bör du dock inte använda **expr** attribut som on-the-fly-beräkning kan påverka hur dina frågor fungerar.
* The **XML** text är ett bra sätt att undvika att skapa för många fält. Men det tar också upp diskutrymme när en CLOB-kolumn används i databasen. Det kan även leda till komplexa SQL-frågor och kan påverka prestanda.
* Längden på en **string** -fältet ska alltid definieras med kolumnen. Som standard är maxlängden i Adobe Campaign 255, men Adobe rekommenderar att du håller fältet kortare om du redan vet att storleken inte kommer att överskrida en kortare längd.
* Det går bra att ha ett fält som är kortare i Adobe Campaign än i källsystemet om du är säker på att storleken i källsystemet var för stor och inte skulle nås. Detta kan betyda en kortare sträng eller ett mindre heltal i Adobe Campaign.

### Val av fält {#choice-of-fields}

Ett fält måste lagras i en tabell om det har ett syfte att målinrikta eller personalisera. Det innebär att om ett fält inte används för att skicka ett anpassat e-postmeddelande eller används som ett kriterium i en fråga tar det upp diskutrymme medan det är oanvändbart.

För hybridinstanser och lokala instanser täcker FDA (Federated Data Access, en valfri funktion som ger åtkomst till externa data) behovet av att lägga till ett fält&quot;direkt&quot; under en kampanjprocess. Du behöver inte importera allt om du har FDA. Mer information finns i [Om åtkomst till federerade data](../../installation/using/about-fda.md).

### Val av nycklar {#choice-of-keys}

Förutom **autopk** som definieras som standard i de flesta tabeller bör du överväga att lägga till några logiska nycklar eller affärsnycklar (kontonummer, klientnummer osv.). Den kan användas senare för import/avstämning eller datapaket. Mer information finns i [Identifierare](#identifiers).

Effektiva nycklar är viktiga för prestanda. Numeriska datatyper bör alltid vara att föredra som nycklar för tabeller.

För SQLServer-databasen kan du använda &quot;grupperat index&quot; om prestanda behövs. Eftersom Adobe inte hanterar detta måste du skapa det i SQL.

### Dedikerade tabellutrymmen {#dedicated-tablespaces}

Med tabellutrymmesattributet i schemat kan du ange ett dedikerat tabellutrymme för en tabell.

Med installationsguiden kan du lagra objekt efter typ (data, tillfällig och indexerad).

Dedikerade tabellutrymmen är bättre för partitionering, säkerhetsregler och ger smidig och flexibel administration, bättre optimering och prestanda.

## Identifierare {#identifiers}

Adobe Campaign-resurser har tre identifierare och det går att lägga till ytterligare en identifierare.

I följande tabell beskrivs dessa identifierare och deras syfte.

| Identifierare | Beskrivning | Bästa praxis |
|--- |--- |--- |
| ID | <ul><li>ID är den fysiska primärnyckeln för en Adobe Campaign-tabell. För färdiga tabeller är det ett genererat 32-bitarsnummer från en sekvens</li><li>Den här identifieraren är vanligtvis unik för en viss Adobe Campaign-instans. </li><li>Ett automatiskt genererat ID kan vara synligt i en schemadefinition. Sök i *autopk=&quot;true&quot;* -attribut.</li></ul> | <ul><li>Automatiskt genererade identifierare bör inte användas som referens i ett arbetsflöde eller i en paketdefinition.</li><li>Man bör inte anta att ID:t alltid blir ett ökande tal.</li><li>ID:t i en körklar tabell är ett 32-bitars tal och den här typen bör inte ändras. Numret hämtas från en sekvens som beskrivs i avsnittet med samma namn.</li></ul> |
| Namn (eller internt namn) | <ul><li>Den här informationen är en unik identifierare för en post i en tabell. Värdet kan uppdateras manuellt, vanligtvis med ett genererat namn.</li><li>Den här identifieraren behåller sitt värde när den distribueras i en annan instans av Adobe Campaign och får inte vara tom.</li></ul> | <ul><li>Byt namn på den post som genererats av Adobe Campaign om objektet ska distribueras från en miljö till en annan.</li><li>När ett objekt har ett namnutrymmesattribut (*schema* till exempel) kommer det här gemensamma namnutrymmet att utnyttjas för alla anpassade objekt som skapas. Vissa reserverade namnutrymmen bör inte användas: *nms*, *xtk*, *nl*, *ncl*, *crm*, *xxl*.</li><li>När ett objekt inte har något namnutrymme (*arbetsflöde* eller *leverans* till exempel) skulle det här namnutrymmesbegreppet läggas till som ett prefix för ett internt namnobjekt: *namespaceMyObjectName*.</li><li>Använd inte specialtecken som blanksteg&quot;, semikolon &quot;:&quot; eller bindestreck &quot;-&quot;. Alla dessa tecken ersätts med understrecket&quot;_&quot; (tillåtet tecken). &quot;abc-def&quot; och &quot;abc:def&quot; skulle till exempel lagras som &quot;abc_def&quot; och skrivas över varandra.</li></ul> |
| Etikett | <ul><li>Etiketten är affärsidentifieraren för ett objekt eller en post i Adobe Campaign.</li><li>Det här objektet tillåter mellanslag och specialtecken.</li><li>Det garanterar inte att ett register är unikt.</li></ul> | <ul><li>Vi rekommenderar att du bestämmer en struktur för objektetiketterna.</li><li>Detta är den mest användarvänliga lösningen för att identifiera en post eller ett objekt för en Adobe Campaign-användare.</li></ul> |

## Anpassade interna nycklar {#custom-internal-keys}

Primärnycklar krävs för alla tabeller som skapas i Adobe Campaign.

De flesta organisationer importerar poster från externa system. Även om den fysiska nyckeln för mottagartabellen är attributet &quot;id&quot;, är det möjligt att fastställa en anpassad nyckel dessutom.

Denna anpassade nyckel är den faktiska primärnyckeln för posten i det externa system som matar Adobe Campaign.

När en körklar tabell har både en autopk och en intern nyckel, ställs den interna nyckeln in som ett unikt index i den fysiska databastabellen.

När du skapar en anpassad tabell finns det två alternativ:
* En kombination av autogenererad nyckel (id) och intern nyckel (anpassad). Det här alternativet är intressant om systemnyckeln är en sammansatt nyckel eller inte ett heltal. Heltal ger högre prestanda i stora tabeller och att de kopplas ihop med andra tabeller.
* Använda primärnyckeln som extern systemprimärnyckel. Den här lösningen är vanligtvis att föredra eftersom den förenklar import och export av data, med en konsekvent nyckel mellan olika system. Automatisk opk ska inaktiveras om nyckeln heter&quot;id&quot; och förväntas fyllas med externa värden (inte autogenererade).

>[!IMPORTANT]
>
>En autopk ska inte användas som referens i arbetsflöden.

## Sekvenser {#sequences}

Adobe Campaign primärnyckel är ett automatiskt genererat ID för alla färdiga tabeller och kan vara samma för anpassade tabeller. Mer information finns i [det här avsnittet](#identifiers).

Det här värdet hämtas från det som kallas **sekvens**, som är ett databasobjekt som används för att generera en nummersekvens.

Det finns två typer av sekvenser:
* **Delad**: fler än en tabell skulle välja sitt ID från samma sekvens. Det innebär att om ett ID &#39;X&#39; används av en tabell, så har ingen annan tabell som delar samma sekvens en post med ID &#39;X&#39;. **XtkNewId** är standardsekvensen som är tillgänglig i Adobe Campaign.
* **Dedikerad**: bara en tabell plockar sina ID:n från sekvensen. Sekvensnamnet innehåller vanligtvis tabellnamnet.

>[!IMPORTANT]
>
>Sekvensen är ett 32-bitars heltalsvärde med ett begränsat maximalt antal tillgängliga värden: 2,14 miljarder. När det maximala värdet har uppnåtts återgår sekvensen till 0 för att återvinna ID:n.
>
>Om gamla data inte har rensats blir resultatet ett brott mot en unik nyckel, vilket blir en blockerare för plattformens hälsa och användning. Adobe Campaign skulle inte kunna skicka ut meddelanden (när det påverkar leveransloggtabellen) och resultatet skulle påverkas mycket.

Därför skulle en kund som skickar 6 miljarder e-postmeddelanden årligen med en kvarhållningsperiod på 180 dagar för sina loggar få slut på ID:n på 4 månader. Om du vill förhindra en sådan utmaning måste du se till att du har rensningsinställningar för volymerna. Mer information finns i [det här avsnittet](#data-retention).

När en anpassad tabell skapas i Adobe Campaign med en primärnyckel som autoPK, bör en anpassad dedikerad sekvens systematiskt kopplas till den tabellen.

Som standard har en anpassad sekvens värden mellan +1 000 och +2,1BB. Tekniskt sett är det möjligt att få ett fullständigt urval av 4BB genom att aktivera negativa ID:n. Detta bör användas med försiktighet och ett ID kommer att förloras vid övergång från negativa till positiva tal: posten 0 ignoreras vanligtvis av Adobe Campaign i genererade SQL-frågor.

Om du vill ha mer information om sekvensöverstrålning kan du titta på [den här videon](https://helpx.adobe.com/customer-care-office-hours/campaign/sequences-exhaustion-campaign-classic.html).

## Index {#indexes}

Index är viktiga för prestandan. När du deklarerar en nyckel i schemat skapas ett index automatiskt i nyckelfälten i Adobe. Du kan också deklarera fler index för frågor som inte använder nyckeln.

Adobe rekommenderar att du definierar ytterligare index eftersom det kan förbättra prestandan.

Tänk dock på följande:

* Indexanvändningen är bunden till ditt åtkomstmönster. Optimering av indexering är ofta en viktig del i databasdesignen och måste hanteras av experter. Att lägga till index är ofta ett iterativt arbetsflöde som är kopplat till databasunderhåll. Det görs med tiden, steg för steg, för att åtgärda prestandaproblem när det händer.
* Index ökar den totala tabellstorleken (för att lagra själva indexet).
* Genom att lägga till index i kolumner kan du förbättra prestanda för dataläsåtkomst (SELECT), men det kan minska prestanda för dataskrivåtkomst (UPDATE).
* Eftersom detta påverkar prestandan under infogningen av data bör indexens storlek och antal begränsas.
* Lägg inte till index när det inte är nödvändigt. Kontrollera att det är obligatoriskt och det ökar den övergripande prestandan för dina frågor (testa och lär).
* I allmänhet är ett index effektivt om du vet att dina frågor inte återför mer än 10 % av posterna.
* Välj noggrant de index som behöver definieras.
* Ta inte bort interna index från färdiga tabeller.

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you’ve completed this important import, it is possible to enable the index(es).-->

### Exempel

Det kan bli mycket komplicerat att hantera index, och det är därför viktigt att förstå hur de fungerar. För att illustrera denna komplexitet kan vi ta ett grundläggande exempel, som att söka efter mottagare genom att filtrera på förnamn och efternamn. Så här gör du:
1. Gå till mappen som visar alla mottagare i databasen. Mer information finns i [Hantera profiler](../../platform/using/managing-profiles.md).
1. Högerklicka på **[!UICONTROL First name]** fält.
1. Välj **[!UICONTROL Filter on this field]**.

   ![](assets/data-model-index-example.png)

1. Upprepa den här åtgärden för **[!UICONTROL Last name]** fält.

De två motsvarande filtren läggs till ovanpå skärmen.

![](assets/data-model-index-search.png)

Nu kan du använda sökfiltrering på **[!UICONTROL First name]** och **[!UICONTROL Last name]** fält enligt de olika filtervillkoren.

Nu kan du lägga till index för att snabba upp sökningen efter dessa filter. Men vilka index ska användas?

>[!NOTE]
>
>Det här exemplet gäller värdbaserade kunder som använder en PostgreSQL-databas.

Tabellen nedan visar i vilka fall de tre index som beskrivs nedan används eller inte enligt det åtkomstmönster som visas i den första kolumnen.

| Sökvillkor | Index 1 (förnamn + efternamn) | Index 2 (endast förnamn) | Index 3 (endast efternamn) | Kommentarer |
|--- |--- |--- |--- |--- |
| Förnamnet är lika med &quot;Johnny&quot; | Används | Används | Används inte | Eftersom förnamnet finns på första plats i index 1 används det ändå: efternamnet behöver inte innehålla något villkor. |
| Förnamnet är lika med&quot;Johnny&quot; OCH efternamnet är lika med&quot;Smith&quot; | Används | Används inte | Används inte | Eftersom båda attributen söks igenom i samma fråga, används bara det index som kombinerar båda attributen. |
| Efternamnet är lika med &quot;Smith&quot; | Används inte | Används inte | Används | Attributens ordning i indexet beaktas. Om du inte matchar den här ordningen kanske inte indexet används. |
| Förnamnet börjar med &quot;Joh&quot; | Används | Används | Används inte | &quot;Vänster sökning&quot; aktiverar index. |
| Förnamnet slutar med &quot;nny&quot; | Används inte | Används inte | Används inte | &quot;Rätt sökning&quot; inaktiverar index och en fullständig sökning utförs. Vissa specifika indextyper kan hantera det här användningsfallet, men de är inte tillgängliga som standard i Adobe Campaign. |
| Förnamnet innehåller &quot;John&quot; | Används inte | Används inte | Används inte | Det här är en kombination av&quot;vänster&quot; och&quot;höger&quot;-sökningar. På grund av det senare inaktiveras index och en fullständig sökning utförs. |
| Förnamnet är lika med&quot;john&quot; | Används inte | Används inte | Används inte | Index är skiftlägeskänsliga. Om du vill göra det icke-skiftlägeskänsligt bör du skapa ett specifikt index som innehåller en SQL-funktion som &quot;upper(firstName)&quot;. Du bör göra samma sak med andra dataomformningar, till exempel &quot;unaccent(first name)&quot;. |

## Länkar och kardinalitet {#links-and-cardinality}

### Länkar {#links}

Se upp för den&quot;egna&quot; integriteten i stora tabeller. Om du tar bort poster som har breda tabeller i &quot;egen&quot; integritet kan instansen stoppas. Tabellen är låst och borttagningarna görs en i taget. Därför är det bäst att använda&quot;neutral&quot; integritet i underordnade tabeller som har stora volymer.

Att deklarera en länk som en extern koppling är inte bra för prestandan. Posten med noll-id emulerar den externa kopplingsfunktionen. Du behöver inte deklarera externa kopplingar om autopk används i länken.

Även om det är möjligt att ansluta en tabell i ett arbetsflöde rekommenderar Adobe att du definierar gemensamma länkar mellan resurser direkt i datastrukturdefinitionen.

Länken ska definieras i enlighet med de data som finns i tabellerna. En felaktig definition kan påverka data som hämtas via länkar, t.ex. oväntat duplicering av poster.

Namnge länken konsekvent med tabellnamnet: länknamnet bör hjälpa till att förstå vad den distinkta tabellen är.

Namnge inte en länk med ID som suffix. Ge det till exempel namnet&quot;transaktion&quot; i stället för&quot;transaktionId&quot;.

Som standard skapar Adobe Campaign en länk med den externa tabellens primärnyckel. För större tydlighet är det bättre att uttryckligen definiera kopplingen i länkdefinitionen.

Ett index läggs till i de attribut som används i en länk.

Länkarna som skapades av och ändrades senast av finns i många tabeller. Det går att inaktivera indexet genom att använda attributet noDbIndex på länken, om den här informationen inte används av företaget.

### Kardinalitet {#cardinality}

När du utformar en länk måste du se till att målposten är unik när en 1-1-relation har deklarerats. Annars kan join returnera flera poster när bara en förväntas. Detta resulterar i fel under leveransförberedelsen när frågan returnerar fler rader än förväntat. Ange länknamnet till samma namn som målschemat.

Definiera en länk med en kardinalitet (1-N) i schemat på (1) sidan. Relationen mottagare (1) - (N)-transaktion ska till exempel definieras i transaktionsschemat.

Observera att en länks omvända kardinalitet är (N) som standard. Det går att definiera en länk (1-1) genom att lägga till attributet revCardinality=&#39;single&#39; till länkdefinitionen.

Om den omvända länken inte ska vara synlig för användaren kan du dölja den med länkdefinitionen revLink=&#39;_INGEN_&#39;. Ett bra exempel för detta är att definiera en länk från mottagaren till den senast slutförda transaktionen. Du behöver bara se länken från mottagaren till den sista transaktionen och ingen omvänd länk krävs för att kunna visas från transaktionsregistret.

Länkar som utför en extern koppling (1-0..1) bör användas med försiktighet eftersom det påverkar systemets prestanda.

## Datalagring - rensning och rensning {#data-retention}

Adobe Campaign är varken ett data warehouse eller ett rapportverktyg. För att Adobe Campaign-lösningen ska fungera väl bör databastillväxten därför förbli under kontroll. För att uppnå detta kan det vara bra att följa några av de bästa metoderna nedan.

Som standard har Adobe Campaign leverans- och spårningsloggar en kvarhållningstid på 180 dagar. En rensningsprocess körs för att ta bort alla äldre loggar.

* Om du vill att loggarna ska sparas längre bör detta beslut fattas med stor noggrannhet beroende på databasstorleken och mängden meddelanden som skickas. Som påminnelse är Adobe Campaign-sekvensen ett 32-bitars heltal.
* Vi rekommenderar att du inte har mer än 1 miljard poster samtidigt i dessa tabeller (cirka 50 % av de 2,14 miljarder ID som finns) för att begränsa riskerna med att använda alla tillgängliga ID:n. Detta kräver att vissa kunder minskar kvarhållningstiden till mindre än 180 dagar.

Läs mer om datalagring i [Riktlinjer för kampanjsekretess och -säkerhet](../../platform/using/privacy-and-recommendations.md).

Läs mer om rensningsarbetsflödet för Campaign Data base [i det här avsnittet](../../production/using/database-cleanup-workflow.md).

>[!IMPORTANT]
>
>Anpassade tabeller rensas inte med standardrensningsprocessen. Även om detta kanske inte är nödvändigt den första dagen, glöm inte att skapa en rensningsprocess för dina anpassade tabeller eftersom detta kan leda till prestandaproblem.

Det finns några lösningar som minimerar behovet av arkivering i Adobe Campaign:
* Exportera data i en data warehouse utanför Adobe Campaign.
* Generera aggregerade värden som använder mindre utrymme samtidigt som de är tillräckliga för er marknadsföringspraxis. Du behöver t.ex. inte den fullständiga kundtransaktionshistoriken i Adobe Campaign för att hålla reda på de senaste köpen.

Du kan deklarera attributet &quot;deleteStatus&quot; i ett schema. Det är effektivare att markera posten som borttagen och sedan skjuta upp borttagningen i rensningsaktiviteten.

## Prestanda {#performance}

Följ de bästa metoderna nedan för att få bättre prestanda när som helst.

### Allmänna rekommendationer {#general-recommendations}

* Undvik åtgärder som &quot;CONTAINS&quot; i frågor. Om du vet vad som förväntas och vill filtreras efter använder du samma villkor med &quot;EQUAL TO&quot; eller andra specifika filteroperatorer.
* Undvik koppling till icke-indexerade fält när du skapar data i arbetsflöden.
* Försök att se till att processer som import och export går utanför kontorstid.
* Se till att det finns ett schema för alla dagliga aktiviteter och att schemat följs.
* Om en eller flera av de dagliga processerna misslyckas och om det är obligatoriskt att köra den samma dag, ska du se till att det inte finns några processkonflikter som körs när den manuella processen startar, eftersom detta kan påverka systemets prestanda.
* Kontrollera att ingen av de dagliga kampanjerna körs under importprocessen eller när någon manuell process körs.
* Använd en eller flera referenstabeller i stället för att duplicera ett fält i varje rad. När du använder nyckel/värde-par bör du välja en numerisk nyckel.
* En kort sträng kan fortfarande användas. Om referenstabeller redan finns på plats i ett externt system, kommer dataintegreringen med Adobe Campaign att underlättas om du återanvänder samma.

### En-till-många-relationer {#one-to-many-relationships}

* Datadesign påverkar användbarhet och funktionalitet. Om du utformar din datamodell med många 1:N-relationer blir det svårare för användarna att skapa meningsfull logik i programmet. En-till-många-filterlogik kan vara svår för icke-tekniska marknadsförare att konstruera och förstå på ett korrekt sätt.
* Det är bra att ha alla viktiga fält i en tabell eftersom det gör det enklare för användarna att skapa frågor. Ibland kan det också vara bra för prestanda att duplicera vissa fält mellan tabeller om det kan undvika en koppling.
* Vissa inbyggda funktioner kan inte referera till 1:N-relationer, t.ex. offertviktningsformel och Leveranser.

## Stora tabeller {#large-tables}

Adobe Campaign förlitar sig på databasmotorer från tredje part. Beroende på vilken provider som används kan optimering av prestanda för större tabeller kräva en viss design.

Nedan följer några vanliga metodtips som bör följas när du utformar din datamodell med stora tabeller och komplexa kopplingar.

* När du använder ytterligare anpassade mottagartabeller måste du ha en dedikerad loggtabell för varje leveransmappning.
* Minska antalet kolumner, särskilt genom att identifiera de som inte används.
* Optimera datamodellens relationer genom att undvika komplexa kopplingar, till exempel kopplingar på flera villkor och/eller flera kolumner.
* Använd alltid numeriska data i stället för teckensträngar för kopplingsnycklar.
* Minska så mycket du kan av djupet för loggbevarande. Om du behöver mer detaljerad historik kan du sammanställa beräkningar och/eller hantera anpassade loggtabeller för att lagra större historik.

### Tabellstorlek {#size-of-tables}

Tabellstorleken är en kombination av antalet poster och antalet kolumner per post. Båda kan påverka prestanda för frågor.

* A **liten storlek** tabellen liknar tabellen Delivery.
* A **medelstor storlek** tabellen är densamma som storleken på mottagartabellen. Det finns en post per kund.
* A **stor** tabellen påminner om den allmänna loggtabellen. Det finns många poster per kund.
Om din databas till exempel innehåller 10 miljoner mottagare innehåller den stora loggtabellen cirka 100 till 200 miljoner meddelanden och leveranstabellen innehåller några tusen poster.

I PostgreSQL får en rad inte överskrida 8 kB för att undvika [TOST](https://wiki.postgresql.org/wiki/TOAST) mekanism. Försök därför att så mycket som möjligt minska antalet kolumner och storleken på varje rad för att behålla optimala prestanda för systemet (minne och processor).

Antalet rader påverkar även prestandan. Adobe Campaign-databasen är inte utformad för att lagra historiska data som inte aktivt används för målinriktning eller personalisering - det här är en operativ databas.

Om du vill förhindra prestandaproblem som har att göra med det stora antalet rader sparar du bara de nödvändiga posterna i databasen. Alla andra poster bör exporteras till tredje part data warehouse och tas bort från Adobe Campaign databas.

Här följer några tips om tabellstorlek:

* Designa stora tabeller med färre fält och mer numeriska data.
* Använd inte en stor kolumntyp (t.ex.: Int64) för att lagra små tal som booleska värden.
* Ta bort oanvända kolumner från tabelldefinitionen.
* Spara inte historiska eller inaktiva data i Adobe Campaign-databasen (export och rensning).

Här är ett exempel:

![](assets/transaction-table-example.png)

I det här exemplet:
* The *Transaktion* och *Transaktionsobjekt* tabeller är stora: över 10 miljoner.
* The *Produkt* och *Butik* tabeller är mindre: mindre än 10 000.
* Produktetiketten och referensen har placerats i *Produkt* tabell.
* The *Transaktionsobjekt* tabellen har bara en länk till *Produkt* tabell, som är numerisk.
