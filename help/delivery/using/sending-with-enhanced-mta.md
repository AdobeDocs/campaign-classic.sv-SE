---
solution: Campaign Classic
product: campaign
title: Skicka med förbättrad MTA i Adobe Campaign Classic
description: Läs mer om omfattningen av och detaljerna med att skicka e-post med Adobe Campaign Enhanced MTA.
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 72fdac4afba6c786cfbd31f4a916b0539ad833e3
workflow-type: tm+mt
source-wordcount: '1398'
ht-degree: 2%

---


# Skicka med den förbättrade MTA {#sending-with-enhanced-mta}

Med **Adobe Campaign Enhanced MTA** (Mail Transfer Agent) får du en uppgraderad sändningsinfrastruktur som möjliggör förbättrad leveransförmåga, renommé, dataflöde, rapportering, studshantering, IP-rampkonfigurering och hantering av anslutningsinställningar.

Den implementeras för att förbättra skalbarheten, öka leveransflödet och hjälpa till att skicka fler e-postmeddelanden snabbare. Detta uppnås med nya adaptiva leveransmetoder som ändrar e-postsändningsinställningarna i realtid baserat på feedback från Internetleverantörer.

>[!IMPORTANT]
>
>Adobe Campaign Enhanced MTA är endast tillgängligt för kunder med värdtjänster eller hybridkunder i Campaign Classic. Anläggningar på plats i Campaign Classic kan inte uppgraderas till att använda den förbättrade MTA-metoden.

Om du har etablerats en Campaign Classic-instans efter september 2018 använder du Förbättrad MTA. För alla andra Campaign Classic-kunder, se [Vanliga frågor](#enhanced-mta-faq) nedan.

Den förbättrade MTA-implementeringen kan påverka vissa av de befintliga Campaign-funktionerna. Mer information finns i [Förbättrade MTA-specifikationer](#enhanced-mta-impacts).

## Frågor och svar {#enhanced-mta-faq}

### Användning och fördelar

**Vad är det förbättrade MTA-avtalet?**

Adobe Campaign kan nu uppgraderas till att använda en ny MTA (Mail Transfer Agent) som kör SparkPosts kommersiella e-post MTA med namnet **Momentum**.

Momentum är en innovativ MTA-teknik med höga prestanda som inkluderar smartare studshantering och en automatiserad leveransoptimeringsfunktion som hjälper avsändare att uppnå och upprätthålla optimala leveransfrekvenser för inkorgen. <!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**Vilka är fördelarna?**

* Adobe Campaign-kunder som använder Förbättrad MTA har sett en <!--300%-->kraftig ökning av den totala genomströmningshastigheten och en <!--90%+-->avsevärd minskning av mjuka studsar.
* Den förbättrade MTA-modellen använder den senaste MTA-tekniken för att ge dig optimala hastigheter för e-postleveransen.
* Genom att direkt och automatiskt anpassa den till den feedback den får säkerställer den också exaktare och intelligentare e-postleverans med realtidsdata.

**Kan jag använda Adobe Campaign MTA och Enhanced MTA samtidigt?**

Nej. Det är bara den förbättrade MTA som kan användas för e-postleveranser när din instans har uppgraderats.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Uppgradera till förbättrad MTA

**Vad krävs för att uppgradera till Enhanced MTA?**

Om du har etablerats en Campaign Classic-instans efter september 2018 krävs ingen åtgärd eftersom du redan använder den förbättrade MTA-metoden.

För alla andra kunder som är värdbaserade eller delvis värdbaserade (hybridkunder) kommer Adobe Campaign-teamet att nå ut för att koordinera ett migreringsdatum och komma med information om lämpliga åtgärder för migrering.

>[!IMPORTANT]
>
>Den förbättrade MTA-metoden är inte tillgänglig för lokala installationer.

**Hur uppgraderar jag min instans till Förbättrat MTA?**

Hela processen för dina värdinstanser kräver några minuters driftstopp. Adobe kommer att övervaka e-postflödet och leveransen i upp till 24 timmar efter uppgraderingen för att bedöma om e-postleveranserna påverkas.

Om problem upptäcks kan Adobe snabbt och tillfälligt återställa instansen till Adobe Campaign MTA.

För närvarande påverkar Förbättrad MTA bara e-postkanalen. Dina push-meddelanden och SMS-leveranser fortsätter att använda den interna Campaign MTA-metoden och påverkas inte på något sätt av uppgraderingen.

**Måste jag gå igenom IP-uppvärmning igen efter att jag uppgraderat till det förbättrade MTA-avtalet?**

Nej. Uppgraderingen kräver inte att du byter till nya IP-adresser, så du kan fortsätta använda dina befintliga, värmade e-postadresser.

**Kommer en uppgradering till den förbättrade MTA-versionen att påverka pågående kampanjer eller leveranser?**

Eventuella leveranser som förberetts innan din instans uppgraderades för att använda det förbättrade MTA måste förbereds på nytt för att den nya MTA-metoden ska kunna användas korrekt.

För kunder som använder Adobe Campaign transaktionsmeddelandefunktioner köas alla API-anrop för att utlösa ett e-postmeddelande under det mycket korta driftstoppet för uppgraderingen och kommer att provas när uppgraderingen är klar.

## Förbättrade MTA-specifikationer {#enhanced-mta-impacts}

### Förbättrade MTA-rubriker

De senaste Campaign Classic-instanserna innehåller kod som lägger till de obligatoriska Enhanced MTA-rubrikerna i alla meddelanden. Om du använder Adobe Campaign 19.1 (build 9032) eller senare och om så inte är fallet, måste du lägga till parametern &quot;useMomentum=true&quot; i konfigurationen för marknadsföringsinstansen (i filen [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta)).

Om du använder en äldre instans som inte innehåller den här koden måste en ny typologiregel med namnet **[!UICONTROL Typology Rule for Enhanced MTAs]** läggas till i alla befintliga typologier i Campaign-instansen.
Den här regeln läggs till av ett **[!UICONTROL Typology]**-paket som installeras som en del av uppgraderingen till det förbättrade MTA-paketet.

>[!IMPORTANT]
>
>Om du ser den här typologiregeln i din typologi ska du inte ta bort eller ändra den på något sätt. Annars kan e-postleveransen påverkas negativt.

Det här **[!UICONTROL Typology]**-paketet måste installeras på Adobe Campaign marknadsinstans.

Om du är en hybridklient kommer Adobe Campaign-teamet att ge dig anvisningar om hur du installerar **[!UICONTROL Typology]**-paketet på din marknadsinstans som en del av uppgraderingen till Enhanced MTA. Kontakta er kontoansvarige för att få de fullständiga instruktionerna.

>[!IMPORTANT]
>
>Instruktioner från Adobe Campaign-teamet om hur du installerar **[!UICONTROL Typology]**-paketet bör följas noggrant. Annars kan du råka ut för större problem med dina IP-adresser som används för att skicka e-post.

Mer information om typologier finns i [det här avsnittet](../../campaign/using/about-campaign-typologies.md).

### Nya MX-regler

MX-hanteringens leveransdataflödesregler används inte längre. Den utökade MTA har egna MX-regler som gör att den kan anpassa din genomströmning efter domän baserat på ditt eget historiska e-postrykte och på realtidsfeedback från de domäner där du skickar e-post.

Mer information om MX-konfiguration finns i [det här avsnittet](../../installation/using/email-deliverability.md#mx-configuration).

### Studentkvalificering

Studskompetensen i tabellen Campaign **[!UICONTROL Delivery log qualification]** används inte längre för **synkrona** felmeddelanden om leveransfel. Den förbättrade MTA-metoden avgör studstyp och kvalifikationer och skickar tillbaka informationen till Campaign.

>[!NOTE]
>
>Det förbättrade MTA-uttrycket kvalificerar SMTP-studsen och skickar tillbaka den till Campaign i form av en studskod mappad till en Campaign-studsorsak och -kvalificering.

Mer information om studskompetens finns i [det här avsnittet](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification).

### Skickad status med Förbättrad MTA

I vyn **[!UICONTROL Summary]** för en e-postleverans [dashboard](../../delivery/using/delivery-dashboard.md) är procentandelen **[!UICONTROL Success]** 100 % och går sedan successivt ned under leveransens [giltighetsperiod](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period), allt eftersom de mjuka och hårda studenterna rapporteras från det förbättrade MTA till Campaign.

Alla meddelanden visas som **[!UICONTROL Sent]** i de [avsändande loggarna](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history) så snart de har vidarebefordrats från Campaign till det utökade MTA-numret. De har den statusen såvida inte eller tills ett [studs](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons) för det meddelandet kommuniceras tillbaka från det förbättrade MTA till Campaign.

När hårda studsmeddelanden rapporteras tillbaka från det förbättrade MTA:et ändras deras status från **[!UICONTROL Sent]** till **[!UICONTROL Failed]** och procentandelen **[!UICONTROL Success]** minskas därefter.

När meddelanden med mjuk studsning rapporteras tillbaka från Förbättrat MTA visas de fortfarande som **[!UICONTROL Sent]** och procentandelen **[!UICONTROL Success]** har ännu inte uppdaterats. Mjuka studsmeddelanden skickas sedan [på nytt](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) under leveransens giltighetsperiod:

* Om ett nytt försök lyckas innan giltighetsperioden är slut förblir meddelandestatusen **[!UICONTROL Sent]** och procentandelen **[!UICONTROL Success]** oförändrad.

* I annat fall ändras statusen till **[!UICONTROL Failed]** och procentandelen **[!UICONTROL Success]** minskas därefter.

Du bör därför vänta tills giltighetsperiodens slut för att se det sista **[!UICONTROL Success]** procentvärdet och det slutliga antalet meddelanden som faktiskt är **[!UICONTROL Sent]** och **[!UICONTROL Failed]**.

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

## Leveransflöde

Dataflödesdiagrammet för Campaign Delivery visar inte längre dataflödet för dina e-postmottagare. I det diagrammet visas nu dataöverföringshastigheten för vidarebefordran av meddelanden från Campaign till det förbättrade MTA-avtalet.

Mer information om leveransflöde finns i [det här avsnittet](../../reporting/using/global-reports.md#delivery-throughput).

### Giltighetsperiod

Inställningen för giltighetsperiod i dina Campaign-leveranser kommer endast att användas av den förbättrade MTA-metoden om den är inställd på **3,5 dagar eller mindre**. Om du definierar ett värde som är högre än 3,5 dagar i Campaign beaktas det inte.

Om giltighetsperioden till exempel är inställd på standardvärdet 5 dagar i Campaign kommer meddelanden med mjuk studsning att hamna i den förbättrade MTA-återförsökskön och provas igen i upp till 3,5 dagar från den dag då meddelandet nådde den förbättrade MTA-gränsen. I så fall används inte det värde som angetts i Campaign.

När ett meddelande har varit i Enhanced MTA-kön i 3,5 dagar och inte kunnat levereras, kommer det att löpa ut och status uppdateras från **[!UICONTROL Sent]** till **[!UICONTROL Failed]** i leveransloggarna.

Mer information om giltighetsperioden finns i [det här avsnittet](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period).

## DKIM-signering

DKIM (DomainKeys Identified Mail) signering av e-postautentisering görs av den utökade MTA:n. DKIM-signering av den interna Campaign MTA-filen kommer att stängas av i domänhanteringstabellen som en del av den förbättrade MTA-uppgraderingen.
Mer information om DKIM finns i [det här avsnittet](../../delivery/using/technical-recommendations.md#dkim).