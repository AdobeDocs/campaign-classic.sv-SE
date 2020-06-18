---
title: Implementering
seo-title: Implementering
description: Implementering
seo-description: null
page-status-flag: never-activated
uuid: 883bad1c-c35b-4c48-9dca-c0cb947facb6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 853f26ad-d373-49a5-952e-4197ffc3d904
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 537cbdec1ec88da1c759f6ca8eafe383c55a61d3
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 0%

---


# Förbättra leveransen genom återengagemang{#re-engagement}

Vid implementering av leverans är några av de bästa sätten att försöka upprätthålla en sund prenumerantbas och förbättra leveransen genom strategier för återengagemang.

* Att upprätthålla en sund prenumerationsbas är en av de viktigaste aspekterna för att säkerställa bra och enhetlig leverans. Många leveransproblem kan uppstå till följd av dålig datahantering och dåligt underhåll.
* Ett av de vanligaste problemen som marknadsförare står inför idag är inaktiv prenumerationsaktivitet (kallas även låg eller utebliven interaktion) som kan påverka e-postleveransen negativt och få avkastning.

>[!NOTE]
>
>Om du vill ha mer information om strategier för återengagemang i kampanjer och Adobes leveranstjänster kan du kontakta din leveranskonsult eller prata med din Adobe-säljare.

## Hur visar internetleverantörer icke-engagemangsaktiviteter? {#how-do-isps-view-non-engagement-activity-}

I åratal har internetleverantörer använt feedback från sina användare för att bestämma var de ska skicka meddelanden, eller om de alls ska leverera dem. Användarengagemanget består av både positiv och negativ feedback och internetleverantörer övervakar båda kontinuerligt. Att inte engagera sig är kanske en av de viktigaste aktörerna i ett negativt engagemang. Ur ett leveransperspektiv kan ni också sänka det totala anseendet för er IP-adress och domäner genom att kontinuerligt skicka kampanjer till användare som inte visar något engagemang.

Internetleverantörer som AOL, Gmail, Microsoft och Yahoo! visa icke-engagemang som oönskad e-post och börja dirigera om meddelanden till skräppostmappen. Dessutom äger dessa prenumeranter inte längre e-postkontot och detta kan användas som en&quot;återvunnen&quot; skräppostsvällning. Det innebär att adressen var ogiltig en tid och att alla meddelanden avvisades. Om prenumeranthanteringssystemet inte tar bort adressater som &quot;studsar hårt&quot; är det troligt att skräppostsvällningar skickas som leder till betydande leveransproblem.

## Hur ska du närma dig inaktivitet? {#how-should-you-approach-inactivity-}

Som tur är kan kunder som använder Adobe Campaign-plattformen visa inaktivitet i sin instans genom att granska öppna och klicka på data enligt segmentet. Eftersom ett uteblivet engagemang kan hindra leveransen kan det vara en första idé att bara ta bort prenumeranter från databasen. Detta kan dock i vissa fall visa sig vara ett felaktigt alternativ. Därför är en strategi för återengagemang (som också kallas återupptagning) den bästa rekommendationen att behålla de abonnenter som är intresserade av att få e-post och gradvis fasa ut dem som inte längre uppvisar någon aktivitet.

## Fungerar verkligen återengagemangskampanjer? {#do-re-engagement-campaigns-really-work-}

Enligt en studie av Return Path resulterade återengagemangskampanjer i en öppen frekvens på 12 % jämfört med ett genomsnitt på 14 % för normala kampanjer. Även om bara 24 % av prenumeranterna hade läst kampanjen om återengagemang, läste ungefär 45 % av dem de följande meddelandena.

![](assets/deliverability_implementation_1.png)

## Hur skapar ni en återengagemangskampanj? {#how-do-you-create-a-re-engagement-campaign-}

### Fas 1 {#phase-1}

* Det första steget är att identifiera prenumeranter som har mycket lite till ingen öppnings- eller klickaktivitet och segmentera gruppen utifrån en bestämd tidsram. Regeln är att granska prenumeranter som inte har öppnat eller klickat på ett e-postmeddelande inom de senaste 90 dagarna. Detta varierar dock beroende på verksamhetens art (till exempel säsongsbunden sändning).
* En annan sak att tänka på när man definierar tidsramar är att internetleverantörer och blocklistföretag ser engagemang som varsomhelst mellan 1,5 och 1,8 år. Dessutom kan beteendeaktiviteter som inköp och webbplatsaktivitet eller andra kontaktpunkter, som inställningar under registreringsfasen eller den första kontaktpunkten, förekomma.

### Fas 2 {#phase-2}

* När ett segment har definierats är nästa steg att skapa en återengagemangskampanj som fångar upp abonnenten enligt de mätvärden som har identifierats. Genom att skapa en ämnesrad ökar abonnentens intresse. Enligt en Return Path-studie genererar ämnesrader och innehåll där det står&quot;We missing you&quot; högre svarsfrekvens än&quot;We want you back&quot;.
* Man kan också erbjuda ett incitament att återengagera sig i e-postmeddelandet. När du överväger erbjudanden med rabatt är det bäst att använda dollarbelopp jämfört med procentandelar. Return Path föreslår också detta eftersom det ger högre svarsfrekvens. Slutligen är det också användbart att utföra A/B-delade tester för att granska respons och svarsfrekvens.

### Fas 3 {#phase-3}

Nästa steg är att fastställa frekvensen för återengagemangskampanjen. Till skillnad från bekräftelsemeddelanden är återengagemangskampanjer avsedda att vinna tillbaka abonnenten med en serie e-postmeddelanden över tiden. I följande exempel visas ett exempel på frekvensen.

![](assets/deliverability_implementation_2.png)

Prenumeranter som interagerar med kampanjen genom att följa öppnings- eller klickaktiviteten läggs tillbaka i den engagerade listan över prenumeranter.

### Fas 4 {#phase-4}

* Nästa fas är att identifiera abonnenter som ständigt inte uppvisar någon aktivitet och gradvis minska antalet utskick av e-post till dem under en tidsperiod. Om det inte finns någon aktivitet under det senaste året är det bra att spärra prenumeranternas e-postprenumeration. Även om de inte har visat något intresse för e-postinnehållet finns det alltid en sista möjlighet att få dem att återaktivera sin prenumeration genom att skicka en engångskampanj för återbekräftelse.
* Återbekräftelsekampanjer är ett bra sätt att fråga prenumeranter som är inaktiva länge om de vill stanna kvar i prenumerationslistan. När du skapar kampanjen är det bättre att lägga till en&quot;klicka här&quot;-länk så att de kan bekräfta åtgärden och verifiera deras adress. På så sätt kan funktionsmakrot registreras i databasen. Nedan visas ett exempel på en e-postbekräftelse:

   ![](assets/deliverability_implementation_3.png)

   När abonnenten har vidtagit en åtgärd kan en landningssida med en bekräftelse på att han eller hon har gjort en ny prenumeration visas. Nedan visas ett exempel på landningssidan:

   ![](assets/deliverability_implementation_4.png)
