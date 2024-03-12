---
product: campaign
title: Skicka med Enhanced MTA i Adobe Campaign Classic
description: Läs mer om omfattningen av och egenskaperna hos utskick av e-post med Adobe Campaign Enhanced MTA
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Email
role: User, Admin, Developer
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: bc6f5d569d0c8a5eba4499a854af370258ce83a2
workflow-type: tm+mt
source-wordcount: '1380'
ht-degree: 0%

---

# Skicka med Förbättrad MTA {#sending-with-enhanced-mta}

The **Adobe Campaign Enhanced MTA** (E-postöverföringsagent) tillhandahåller en uppgraderad sändningsinfrastruktur som möjliggör förbättrad leveransförmåga, renommé, genomströmning, rapportering, studshantering, IP-avkodning och hantering av anslutningsinställningar.

Den implementeras för att förbättra skalbarheten, öka leveransgenomströmningen och hjälpa till att skicka fler e-postmeddelanden snabbare. Detta uppnås med nya adaptiva leveransmetoder som ändrar e-postsändningsinställningarna i realtid baserat på feedback från Internetleverantörer.

>[!IMPORTANT]
>
>Adobe Campaign Enhanced MTA är endast tillgängligt för Campaign Classic som är värdbaserade eller hybridkunder. Campaign Classic på plats-installationer kan inte uppgraderas till att använda den förbättrade MTA-metoden.

Om du har etablerats en Campaign Classic-instans efter september 2018 använder du Förbättrad MTA. Alla andra Campaign Classic hittar du på [Frågor och svar](#enhanced-mta-faq) nedan.

Den förbättrade MTA-implementeringen kan påverka vissa av de befintliga Campaign-funktionerna. Mer information finns i [Förbättrade MTA-egenskaper](#enhanced-mta-impacts).

>[!NOTE]
>
>Om du är slutanvändare av Adobe Campaign och vill veta om din instans har uppgraderats till Förbättrat MTA, kontaktar du den interna Campaign-administratören.

## Vanliga frågor och svar {#enhanced-mta-faq}

### Användning och fördelar

**Vad är det förbättrade MTA-avtalet?**

Adobe Campaign kan nu uppgraderas till att använda en ny MTA (Mail Transfer Agent) som kör SparkPosts kommersiella e-postmeddelande MTA som kallas **Momentum**.

Momentum är en innovativ MTA-teknik med höga prestanda som inkluderar smartare studshantering och en automatiserad leveransoptimeringsfunktion som hjälper avsändare att uppnå och upprätthålla optimala leveransfrekvenser för inkorgen. <!--More than 37% of the world's business email is sent using SparkPost's MTA technology.-->

**Vilka är fördelarna?**

* Adobe Campaign-kunder som använder Enhanced MTA har sett en <!--300%-->en kraftig ökning av den totala genomströmningshastigheten och <!--90%+-->markant minskning av mjuka studsar.
* Den förbättrade MTA-modellen använder den senaste MTA-tekniken för att ge dig optimala hastigheter för e-postleveransen.
* Genom att direkt och automatiskt anpassa den till den feedback den får säkerställer den också exaktare och intelligentare e-postleverans med realtidsdata.

**Kan jag använda Adobe Campaign MTA och Enhanced MTA samtidigt?**

Nej. Det är bara den förbättrade MTA som kan användas för e-postleveranser när din instans har uppgraderats.

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we've implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you're not already using it, we'll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### Uppgradera till förbättrad MTA

**Vad krävs för att uppgradera till Enhanced MTA?**

Om du har etablerats en Campaign Classic-instans efter september 2018 krävs ingen åtgärd eftersom du redan använder den förbättrade MTA-filen.

För alla andra värdbaserade eller delvis värdbaserade (hybridkunder) kommer Adobe Campaign-teamet att nå ut för att samordna ett migreringsdatum och komma med information om de steg som krävs för migreringen.

>[!IMPORTANT]
>
>Den förbättrade MTA-metoden är inte tillgänglig för lokala installationer.

**Hur uppgraderar jag min instans till Förbättrat MTA?**

Hela processen för dina värdinstanser kräver några minuters driftstopp. Adobe kommer att övervaka e-postflödet och -leveransen i upp till 24 timmar efter uppgraderingen för att bedöma om e-postleveranserna påverkas.

Om problem upptäcks kan Adobe snabbt och tillfälligt återställa instansen till Adobe Campaign MTA.

För närvarande påverkar Förbättrad MTA bara e-postkanalen. Dina push-meddelanden och SMS-leveranser fortsätter att använda den interna Campaign MTA-metoden och påverkas inte på något sätt av uppgraderingen.

**Måste jag gå igenom IP-uppvärmning igen efter att jag uppgraderat till det förbättrade MTA-avtalet?**

Nej. Uppgraderingen kräver inte att du byter till nya IP-adresser, så du kan fortsätta använda dina befintliga, värmade e-postadresser.

**Kommer en uppgradering till den förbättrade MTA-versionen att påverka pågående kampanjer eller leveranser?**

För kunder som använder Adobe Campaign transaktionsmeddelandefunktioner köas alla API-anrop för att utlösa ett e-postmeddelande under det mycket korta driftstoppet för uppgraderingen och kommer att provas när uppgraderingen är klar.

## Förbättrade MTA-egenskaper {#enhanced-mta-impacts}

### Nya MX-regler

MX-hanteringens leveransdataflödesregler används inte längre. Den utökade MTA har egna MX-regler som gör att den kan anpassa din genomströmning efter domän baserat på ditt eget historiska e-postrykte och på realtidsfeedback från de domäner där du skickar e-post.

Mer information om MX-konfiguration finns i [det här avsnittet](../../installation/using/email-deliverability.md#mx-configuration).

### Studentkvalificering

Studentkvalifikationerna i Campaign **[!UICONTROL Delivery log qualification]** tabellen används inte längre för **synkron** felmeddelanden vid leveransfel. Den förbättrade MTA-metoden avgör studstyp och kvalifikationer och skickar tillbaka informationen till Campaign.

>[!NOTE]
>
>Det förbättrade MTA-uttrycket kvalificerar SMTP-studsen och skickar tillbaka den till Campaign i form av en studskod mappad till en Campaign-studsorsak och -kvalificering.

Mer information om studskvalifikationer finns i [det här avsnittet](understanding-delivery-failures.md#bounce-mail-qualification).

### Leverans

En leverans kan inte stoppas när den har överförts till det förbättrade MTA-avtalet - även om den visas med **[!UICONTROL Stopped]** status i Campaign.

### Leveranskapacitet

Dataflödesdiagrammet för Campaign Delivery visar inte längre dataflödet för dina e-postmottagare. I det diagrammet visas nu dataöverföringshastigheten för vidarebefordran av meddelanden från Campaign till det förbättrade MTA-avtalet.

Mer information om leveransflöde finns i [det här avsnittet](../../reporting/using/global-reports.md#delivery-throughput).

### Försök igen

Inställningarna för nya försök i leveransen används inte längre av Campaign. Mjuka avhoppsförsök och hur lång tid det tar mellan dem bestäms av den förbättrade MTA-metoden baserat på typ och allvarlighetsgrad för de avhoppssvar som kommer tillbaka från meddelandets e-postdomän.

Mer information om återförsök finns i [det här avsnittet](steps-sending-the-delivery.md#configuring-retries).

### Giltighetsperiod

Inställningen för giltighetsperiod i kampanjleveranserna kommer endast att användas av den förbättrade MTA-metoden om den är inställd på **3,5 dagar eller mindre**. Om du definierar ett värde som är högre än 3,5 dagar i Campaign beaktas det inte.

Om giltighetsperioden till exempel är inställd på standardvärdet 5 dagar i Campaign kommer meddelanden med mjuk studsning att hamna i den förbättrade MTA-återförsökskön och provas igen i upp till 3,5 dagar från den dag då meddelandet nådde den förbättrade MTA-gränsen. I så fall används inte det värde som angetts i Campaign.

När ett meddelande har varit i den förbättrade MTA-kön i 3,5 dagar och inte kunnat levereras, kommer det att gå ut och statusen uppdateras från **[!UICONTROL Sent]** till **[!UICONTROL Failed]** i leveransloggarna.

Mer information om giltighetsperioden finns i [det här avsnittet](steps-sending-the-delivery.md#defining-validity-period).

### DKIM-signering

DKIM (DomainKeys Identified Mail) signering av e-postautentisering görs av den utökade MTA:n. DKIM-signering av den interna Campaign MTA-filen kommer att stängas av i domänhanteringstabellen som en del av den förbättrade MTA-uppgraderingen.
Mer information om DKIM finns i [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### Rapport om lyckade leveranser

I **[!UICONTROL Summary]** vy för e-postleverans [kontrollpanel](delivery-dashboard.md), **[!UICONTROL Success]** från 100 % och sedan gradvis sjunker under hela leveransen [giltighetsperiod](steps-sending-the-delivery.md#defining-validity-period), när de mjuka och hårda studenterna rapporteras tillbaka från det förbättrade MTA-avtalet till Campaign.

Alla meddelanden visas som **[!UICONTROL Sent]** i [skicka loggar](delivery-dashboard.md#delivery-logs-and-history) så snart de har vidarebefordrats från Campaign till det förbättrade MTA-avtalet. De är kvar i denna status såvida inte eller till [studsa](understanding-delivery-failures.md#delivery-failure-types-and-reasons) för det meddelandet kommuniceras tillbaka från Förbättrat MTA till Campaign.

När hårda studsmeddelanden rapporteras tillbaka från Förbättrat MTA ändras deras status från **[!UICONTROL Sent]** till **[!UICONTROL Failed]** och **[!UICONTROL Success]** procentandelen minskas därefter.

När meddelanden med mjuk studsning rapporteras tillbaka från Förbättrad MTA visas de fortfarande som **[!UICONTROL Sent]** och **[!UICONTROL Success]** procentandelen har ännu inte uppdaterats. Mjuka studsmeddelanden visas sedan [omförsök](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) under hela leveransperioden

* Om ett nytt försök lyckas före giltighetsperiodens slut förblir meddelandets status som **[!UICONTROL Sent]** och **[!UICONTROL Success]** procentandelen förblir oförändrad.

* I annat fall ändras statusen till **[!UICONTROL Failed]** och **[!UICONTROL Success]** procentandelen minskas därefter.

Du bör därför vänta tills giltighetsperiodens slut för att se den slutliga **[!UICONTROL Success]** och det slutliga antalet **[!UICONTROL Sent]** och **[!UICONTROL Failed]** meddelanden.

Tabellen nedan visar de olika stegen i sändningsprocessen med motsvarande KPI:er och sändning av loggstatus.

| Steg i sändningsprocessen | KPI-sammanfattning | Loggstatus skickas |
|--- |--- |--- |
| Meddelandet har vidarebefordrats från Campaign till det förbättrade MTA-meddelandet | **[!UICONTROL Success]** procent börjar vid 100 % | Skickat |
| Hårdstudsmeddelanden rapporteras tillbaka från Förbättrad MTA | **[!UICONTROL Success]** procentandelen minskas därefter | Misslyckades |
| Mjuka studsmeddelanden rapporteras tillbaka från Förbättrat MTA | Ingen ändring i **[!UICONTROL Success]** procent | Skickat |
| Mjuka studsmeddelanden - återförsök har slutförts | Ingen ändring i **[!UICONTROL Success]** procent | Skickat | **[!UICONTROL Success]** procentandelen ökas därefter | Skickat |
| Mjukt studsande meddelanden återförsök misslyckas | **[!UICONTROL Success]** procentandelen minskas därefter | Misslyckades |

