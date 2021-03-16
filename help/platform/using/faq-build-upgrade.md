---
solution: Campaign Classic
product: campaign
title: Vanliga frågor om uppgradering av bygge
description: Vanliga frågor om uppgraderingar av Campaign-versioner
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 4d5d14565726c5c6e7c4e2e8a82cfa8cef87be0f
workflow-type: tm+mt
source-wordcount: '2015'
ht-degree: 3%

---


# Vanliga frågor om uppgradering av bygge {#build-upgrade-faq}

Adobe Campaign uppdateras regelbundet. Om du känner till vår publicerade [versionsinformation](../../rn/using/rn-overview.md) är du antagligen medveten om att i genomsnitt 2/3 mindre versioner med nya funktioner släpps förbättringar och korrigeringar varje år. Dessutom släpper vi regelbundet mindre builder med kumulativa korrigeringar. Denna regelbundna uppdateringsfrekvens syftar till att få den senaste och bästa informationen i händerna, så att miljön är helt säker och så tydligt som möjligt förbättrar upplevelsen av vår produkt.

Det är viktigt att våra kunder kör den senaste versionen av Adobe Campaign. Det gör också att Adobe kan hjälpa till mycket effektivare om du stöter på problem - det tar ofta längre tid att identifiera, återge och åtgärda ett fel i en gammal version, för att inte tala om att vissa problem som du kanske stöter på redan har åtgärdats i en nyligen gjord version.

Vi startade därför [Gold Standard](https://helpx.adobe.com/se/campaign/kb/gold-standard.html)-programmet för att samarbeta med våra kunder för att proaktivt och regelbundet uppgradera deras miljöer.

## Vad är en bygguppgradering?

En bygguppgradering är när Adobe Campaign Classic uppdateras till det senaste säkra versionsnumret, men ändå ligger kvar på samma huvud-/delnivå. Till exempel: Campaign Classic v7 build 9026 to Campaign v7 build 9032.

Läs mer [i det här avsnittet](../../rn/using/rn-overview.md).

## Vilken är den senaste versionen av Adobe Campaign Classic?

Den senaste versionen av Campaign Classic, med nya funktioner och dokumentation, finns i den senaste [versionsinformationen](../../rn/using/latest-release.md).

## Hur vet jag vilken version jag har?

Kontrollera din version från **[!UICONTROL Help > About...]**-menyn i Adobe Campaign Client Console. Rutan **[!UICONTROL About]** innehåller detaljerad information om versionen och bygget som du kör för både konsolen och servern.

Läs mer [i det här avsnittet](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Vad betyder byggstatusen?

Från och med Campaign Classic 19.2 associeras en status med varje bygge.

Läs mer [i det här avsnittet](../../rn/using/rn-overview.md).

## Är en bygguppgradering samma sak som en versionsuppgradering?

Nej. En versionsuppgradering är en stegvis uppdatering i en viss större version, medan en versionsuppgradering är en förändring från en större version till en annan. Uppgraderingar är enkla eftersom de vanligtvis inte innebär några större förändringar av arkitektur, teknik eller datamodell.

Versionsuppgraderingar å andra sidan har ofta betydande tekniska ändringar och, beroende på hur detaljerad konfigurationen är för en viss kund, kan kräva betydande konfigurationsändringar och/eller partiell omimplementering.

Med serverinformationen från skärmbilden i föregående avsnitt kan du till exempel:

* En bygguppgradering innebär att man går från build 6880 till valfri version som är större än 6880. Exempel: v6.1.1 build 8222 to v6.1.1 build 8666

* En versionsuppgradering innebär att man måste gå från version 6.0.2 till en version som är större än 6.0.2.  Till exempel: v6.0.1 build 2222 to v6.1.1 build 8666

## Ska jag säkerhetskopiera mina data före dessa uppdateringar?

Adobe gör en säkerhetskopia av ditt system innan några ändringar görs. Men om det finns viktiga anpassningsarbeten i ditt icke-produktionssystem (utvecklings- eller testservrar) rekommenderar vi att du exporterar dessa som ett paket före en uppgradering.

![](assets/do-not-localize/how-to-video.png) Om du vill ha mer information  [tittar du på videon](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html) så här.

## När kommer uppgraderingarna att äga rum?

Kunderna erbjuds ett datumintervall att välja mellan. Ändringar i produktionssystemet utförs inte på helger.

Du kan uppgradera från måndag till torsdag och fredag används endast för icke-produktionstillfällen.

## Hur lång tid tar uppgraderingen?

Hur lång tid det tar att utföra en bygguppgradering beror på flera faktorer:

* Storleken på den databas som ska säkerhetskopieras eller återställas (större databaser kräver mer tid att uppgradera)
* Miljöernas storlek (många av våra kunder har flera olika servrar som var och en hanterar specifika funktioner, där större miljöer kräver mer tid att uppgradera)
* Systemets komplexitet (vissa system har mer beroende tjänster och anslutningar för verifiering, vilket kräver verifiering av stabiliteten och prestandan hos sådana system)

Uppgradering är en tvåstegsprocess:

1. Förberedelse av systemet för uppgradering - Med tanke på just din miljö leder den här fasen i princip till en fullständig uppgradering i en icke-produktionsmiljö. När den uppgraderade miljön har speglats ur teknisk och funktionell synpunkt kan fas 2 inträffa. Denna första fas kan, beroende på de ovan nämnda faktorerna, ta från några dagar till några veckor.

1. Själva uppgraderingen - produktionsmiljön har uppgraderats. Denna fas utförs vanligtvis på några timmar. I mycket komplexa miljöer bör man förvänta sig längre driftstopp. Om något går fel definieras en återställningsstrategi som kan utföras.

Mer information finns i [det här dokumentet](https://helpx.adobe.com/se/campaign/kb/acc-build-upgrade.html).

## Vilka resurser behövs för uppgraderingen?

Bygguppgraderingsprocessen kräver följande resurser:

* Adobe Architect - För värdbaserade eller molnbaserade meddelanden/hybridarkitekturer måste arkitekten koordinera med kundtjänst.
* Projektledare - värd: värdteamet samarbetar med kundtjänstteamet och kunden för att samordna uppgraderingstiden för alla instanser.
* Adobe Campaign Administrator - Hosted: värdteamet utför uppgraderingen.
* Adobe Campaign operator\marknadsföringsanvändare - Operatorn kör tester på instanser av utveckling, test och produktion.

## Hur kan jag förbereda mig för uppgraderingen?

Exportera material som är viktigt och som måste bevaras i dina utvecklings- och staging-system. [Se videon](https://helpx.adobe.com/campaign/classic/how-to/generate-packages-in-acv6.html) för mer information.

Uppdatera dina kunskaper om viktiga arbetsflöden och leveranser som utvecklats i dina körningsböcker (eller av ditt konsultteam/partner) genom att läsa dokumentationen som skickas till ditt team när implementeringen är klar.

Identifiera låga volymer eller låga trafiktider som skulle vara idealiska för underhållsperioder eftersom de ger lägsta möjliga inverkan på verksamheten.

Läs igenom vår [checklista för bygguppgradering nedan](#check-list) och dina testplaner och se till att resurser som kan utföra dessa tester är tillgängliga inom 24-48 timmar. när en uppgradering har slutförts.

Mer information finns i [det här dokumentet](https://helpx.adobe.com/campaign/kb/acc-build-upgrade.html).

## Kan uppgraderingar göras dygnet runt eller på kontorstid utanför kontorstid?

Uppgraderingar kan göras utanför kontorstid. Vi rekommenderar alltid att du uppgraderar miljön när du arbetar offline, när inga användare är anslutna till instansen.

## Vilka är kostnaderna för en bygguppgradering?

Det kostar inget att installera bygguppgraderingen för kunder som har värdtjänster. Om det finns anpassad utveckling i systemet måste kunden identifiera resurser som behövs för att testa utvecklingen efter uppgraderingen och för att korrigera eventuella problem som kan uppstå med den anpassade utvecklingen.

## Kommer du att få åtkomst till instansen under uppgraderingsprocessen?

Nej. Servern stängs av under en uppgradering för att säkerställa att dataintegriteten bevaras när produkten uppgraderas. När allt är klart startas det om och alla tjänster återupptas.

## Kommer e-postmeddelandena att fortsätta att skickas från Message Center under uppgraderingsprocessen?

När uppgraderingen görs för Message Center (RT) skickas inga e-postmeddelanden från instansen. Observera att alla processer som stoppas när ett Campaign-system stängs av automatiskt återupptas när systemet startas om. Detta inkluderar aktiva eller schemalagda leveranser, spårning och mätberäkningar för tidigare skickade leveranser.

## Kommer arbetsflödena att fortsätta att köras och skicka leveranserna?

Nej. Under bygguppgraderingen stoppas både arbetsflödes- och e-posttjänster. Det innebär att arbetsflöden inte körs och att leveranser inte skickas. De återupptas när systemet har startats om. Adobe rekommenderar dock starkt att alla kritiska arbetsflöden för sökvägar kontrolleras efter en uppgradering för att säkerställa att de körs och är felfria.

## Fungerar mina spårningslänkar fortfarande under uppgraderingen?

Det går att spåra länkar under uppgraderingen. Det går inte att skicka nya e-postmeddelanden under uppgraderingen, men spårningslänkar som ingår i redan skickade e-postmeddelanden kan användas.

## Måste jag vara tillgänglig under uppgraderingsprocessen?

Ja. Kunderna bör förse Adobe med en kontaktpunkt som är tillgänglig under eller omedelbart efter uppgraderingen av produktionsinstansen.  Adobe kommer att kontakta den här personen via e-post såvida inte andra arrangemang har gjorts. Detta kommer att säkerställa en smidig övergång och omedelbar validering av kritiska uppgifter. Adobe kontaktar kunden när uppgraderingen är klar för bekräftelse.

## Behöver jag uppdatera klientkonsolen?

Ja. Klientkonsolen måste finnas på samma version som serverinstansen. När uppgraderingen är klar bör din klientkonsol uppmana dig att uppgradera till den senaste versionen för att säkerställa att den är i linje med serverbygget.

## Vad är återställningsplanen? Bevaras säkerhetskopior av mina data?

Återställningsplanen är att återställa systemet med den senaste tillgängliga säkerhetskopian. Säkerhetskopior lagras i 7 dagar för datacenterkunder och i 14 dagar för kunder som använder Amazon Web Service (AWS).

## Hur lång tid tar det att återställa?

Det beror på databasens säkerhetskopieringsstorlek. Genomsnittlig tid det tar är 4 timmar att slutföra.

## Vilka typer av tester utförs på mitt system efter uppgraderingen?

Se [checklistan för uppgraderingen nedan](#check-list).

## Vilken typ av test måste jag utföra efter min uppgradering?

Utvecklings- och scenmiljöer uppgraderas antingen i följd eller tillsammans, men det krävs en signering innan produktionsinstansen uppgraderas. På så sätt kan varje kund utföra grundliga tester innan de signerar om produktionsändringar.

Se listan [bocka för uppgradering nedan](#check-list). Kunderna bör köra liknande tester liksom andra som de kan behöva för miljön.

## Hur ofta måste jag göra en bygguppgradering?

För att säkerställa optimala prestanda, tillgänglighet och säkerhet för systemet kommer Adobe att samarbeta med kunder för att säkerställa att systemen uppgraderas minst en gång per år.

## Kommer det att bli någon avstängning med en bygguppgradering?

Ja. Servern stängs av under en uppgradering för att säkerställa att dataintegriteten bevaras när produkten uppgraderas. När allt är klart startas det om och alla tjänster återupptas.

## Vem ska jag kontakta för att öppna uppgraderingsbiljetten?

Om du får problem efter en uppgraderingsversion kontaktar du [Adobe kundtjänst](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Kundtjänst schemalägger byggdatum och öppnar biljetter relaterade till uppgraderingar.

Läs mer i [Hjälp- och supportalternativ för Campaign Classic](https://helpx.adobe.com/se/campaign/kb/ac-support.html)

## Build upgrade checklist {#check-list}

### Checklista för efteruppgradering av molnmeddelandeserver

1. Skicka en testleverans
   1. Validera leveransloggarna och det relaterade arbetsflödet
   1. Verifiera att spårningsloggarna har uppdaterats
   1. Validera spegelsida och spårningslänkar
1. Bekräfta att alla tekniska arbetsflöden är i startläge
1. Kontrollera att alla processer också är aktiva

### Checklista för uppgradering av marknadsföringsserver efter uppgradering

* Kan du logga in på servern? Kontrollera att Campaign Client Console fungerar utan några fel-/varningspopup-fönster.
* Se till att använda samma konsolversion som byggversionen efter uppgraderingen.
* Har du några webbprogram som infogar data i Campaign-databasen? I så fall kör du dem och
verifiera att de kan infoga nya poster via API.
* Kan du skicka ut ett test-e-postmeddelande? Skapa ny leverans med en känd mall och skicka den till
en testmottagare, verifiera personalisering, ta bort länkar, spegla sida allt arbete.
* Körs alla era arbetsflöden för kritiska sökvägar? Kontrollera arbetsflöden, öppna arbetsflödesjournal, verifiera
att det inte finns några fel.
* Är alla dina mappar tillgängliga, synliga och tillgängliga? Bläddra bland olika mappar och kontrollera.
allt innehåll visas och visas.
* Kommer leveranserna igenom med rätt tidszon?

   * Verifiera skapandedatum och ändringsdatum med tidsstämpeln och tidszonen
   * Verifiera att körningen av schemaläggaren fungerar i ett arbetsflöde vid den angivna tiden
   * Hämta en lista över arbetsflöden som är i PAUSED- och FAILED-läge. Starta och övervaka dem
   * Kör AB-testning för ett scenario
   * Testa push-meddelanden tillsammans med deras spårningsfunktioner för djupa länkar
   * Testa att skicka SMS
   * Om du har någon extern FDA ansluten, testar du om data skickas på båda sätten
   * Om du använder integreringar som Adobe Campaign-Adobe Experience Manager eller Adobe Campaign-Adobe Analytics bör du testa om de fortfarande fungerar som tidigare

**Se även**

* [Utföra en uppgradering av din build](../../production/using/build-upgrade.md)
* [Versionsinformation för Campaign Classic](../../rn/using/rn-overview.md)
* [Hjälp- och supportalternativ för Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html)
* [Gold Standard](https://helpx.adobe.com/campaign/kb/gold-standard.html)