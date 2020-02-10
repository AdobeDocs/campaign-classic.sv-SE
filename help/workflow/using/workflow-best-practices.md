---
title: Bästa arbetsflöden
seo-title: Bästa arbetsflöden
description: Bästa arbetsflöden
seo-description: null
page-status-flag: never-activated
uuid: 56b04004-5d96-4169-9494-3d04284d5a3d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 3da951ef-5775-4593-8301-f143c71edc19
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4b4ec97e52a494dd88b2516650ae514294f00934

---


# Bästa arbetsflöden{#workflow-best-practices}

## Körning och prestanda {#execution-and-performance}

Nedan visas allmänna riktlinjer för hur du optimerar Campaign-prestanda, inklusive bästa praxis för dina arbetsflöden.

Felsökningsriktlinjer för arbetsflödeskörning finns också i [det här avsnittet](../../production/using/workflow-execution.md).

### Loggar {#logs}

JavaScript-metoden **[!UICONTROL logInfo()]** är en bra lösning för att felsöka ett arbetsflöde. Den är användbar men måste användas med försiktighet, särskilt för aktiviteter som ofta utförs: loggarna kan överbelastas och storleken på loggtabellen kan öka avsevärt. Men du kanske också behöver mer än **[!UICONTROL logInfo()]**.

Det finns ytterligare två lösningar:

* **Behåll resultatet från mellanliggande populationer mellan två avrättningar**

   Med det här alternativet behålls temporära tabeller mellan två körningar av ett arbetsflöde. Den är tillgänglig på fliken för arbetsflödesegenskaper och kan användas för utveckling och testning för att övervaka data och kontrollera resultat. **[!UICONTROL General]** Du kan använda det här alternativet i utvecklingsmiljöer, men aldrig använda det i produktionsmiljöer. Om du behåller tillfälliga tabeller kan databasens storlek öka avsevärt och så småningom kan storleksgränsen nås. Dessutom kommer säkerhetskopieringen att bli långsammare.

   Endast arbetsregister för den senaste körningen av arbetsflödet behålls. Arbetstabeller från tidigare körningar rensas av arbetsflödet, som körs dagligen. **[!UICONTROL cleanup]**

   >[!CAUTION]
   >
   >Det här alternativet får aldrig checkas in i ett produktionsarbetsflöde. Det här alternativet används för att analysera resultaten och är utformat endast för teständamål och ska därför endast användas i utvecklings- eller stagingmiljöer.

* **Logga SQL-frågor i journalen**

   Det här alternativet är tillgängligt på fliken **[!UICONTROL Execution]** för arbetsflödesegenskaper och loggar alla SQL-frågor som genererats av verktyget från de olika aktiviteterna. Det är ett bra sätt att se vad som faktiskt utförs av plattformen. Detta alternativ bör dock endast användas tillfälligt under utvecklingen och inte aktiveras i produktionen.

Rensa loggarna när de inte behövs längre. Arbetsflödeshistorik rensas inte automatiskt: alla meddelanden behålls som standard. Du kan rensa historiken via **[!UICONTROL File > Actions]** menyn eller genom att klicka på knappen Åtgärder i verktygsfältet ovanför listan. Välj Rensa historik.
Mer information om hur du tömmer dina loggar finns i den här [dokumentationen](../../workflow/using/executing-a-workflow.md#actions-toolbar).

### Arbetsflödesplanering {#workflow-planning}

* Försök att bibehålla en stabil aktivitetsnivå under dagen och undvika toppar för att förhindra att instansen överbelastas. Det gör du genom att fördela arbetsflödets starttider jämnt över hela dagen.
* Schemalägg datainläsning över en natt för att minska resurskonflikter.
* Långa arbetsflöden kan eventuellt påverka server- och databasresurserna. Dela de längsta arbetsflödena för att minska bearbetningstiden.
* Om du vill minska den totala körtiden ersätter du tidskrävande aktiviteter med förenklade och snabbare aktiviteter.
* Undvik att köra fler än 20 arbetsflöden samtidigt. När alltför många arbetsflöden körs samtidigt kan systemet få slut på resurser och bli instabilt. Mer information om varför arbetsflödet kanske inte startar finns i den här [artikeln](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html).

### Arbetsflödeskörning {#workflow-execution}

Det är en god vana att inte schemalägga ett arbetsflöde så att det körs mer än var 15:e minut eftersom det kan påverka den totala systemprestandan och skapa block i databasen.

Undvik att lämna arbetsflödena i pausat läge. Om du skapar ett tillfälligt arbetsflöde måste du se till att det kan slutföras korrekt och inte vara i ett **[!UICONTROL paused]** läge. Om den pausas innebär det att du måste behålla de temporära tabellerna och på så sätt öka storleken på databasen. Tilldela arbetsflödesgranskare under Arbetsflödesegenskaper för att skicka en avisering när ett arbetsflöde misslyckas eller pausas av systemet.

Så här undviker du att arbetsflöden är i pausat läge:

* Kontrollera dina arbetsflöden regelbundet för att se om det inte finns några oväntade fel.
* Håll arbetsflödena så enkla som möjligt, t.ex. genom att dela upp stora arbetsflöden i flera olika arbetsflöden. Du kan använda **[!UICONTROL External signal]** aktiviteter som utlöser deras körning baserat på andra arbetsflödenas körning.
* Undvik inaktiverade aktiviteter med arbetsflöden som lämnar trådarna öppna och leder till många tillfälliga tabeller som kan ta mycket plats. Behåll inte aktiviteter i **[!UICONTROL Do not enable]** eller **[!UICONTROL Enable but do not execute]** lägen i dina arbetsflöden.

Stoppa även oanvända arbetsflöden. Arbetsflöden som fortsätter att köras behåller anslutningar till databasen.

Använd endast ovillkorlig stop i de sällsynta fallen. Använd inte den här åtgärden regelbundet. Utan att utföra en ren stängning av anslutningar som genereras av arbetsflöden till databasen påverkar prestanda.

### Kör i motoralternativet {#execute-in-the-engine-option}

I **[!UICONTROL Workflow properties]** fönstret markerar du aldrig **[!UICONTROL Execute in the engine]** alternativet. När det här alternativet är aktiverat får arbetsflödet prioritet och alla andra arbetsflöden stoppas av arbetsflödesmotorn tills det är klart.

![](assets/wf-execute-in-engine.png)

## Egenskaper för arbetsflöde {#workflow-properties}

### Arbetsflödesmappar {#workflow-folders}

Adobe rekommenderar att du skapar arbetsflöden i en dedikerad mapp.

Om arbetsflödet påverkar hela plattformen (till exempel rensningsprocesser) kan du lägga till en undermapp i den inbyggda **[!UICONTROL Technical Workflows]** mappen.

### Namnge arbetsflöde {#workflow-naming}

Eftersom det gör det enklare att hitta och felsöka dem om de inte fungerar på rätt sätt rekommenderar Adobe att du ger arbetsflödena egna namn och etiketter: fylla i arbetsflödets beskrivningsfält för att sammanfatta den process som ska utföras så att operatorn lätt kan förstå den.

Om arbetsflödet är en del av en process som innefattar flera arbetsflöden kan du vara tydlig när du anger en etikett; Att använda siffror är ett bra sätt att ordna arbetsflödena (med Label).

Till exempel:

* 001 - Importera - Importera mottagare
* 002 - Import - Importförsäljning
* 003 - Importera - Importera försäljningsinformation
* 010 - Exportera - Exportera leveransloggar
* 011 - Export - loggar för exportspårning

### Arbetsflödets allvarlighetsgrad {#workflow-severity}

Du kan konfigurera ett arbetsflödes svårighetsgrad i arbetsflödesegenskaperna på **[!UICONTROL Execution]** fliken:

* Normal
* Produktion
*  Kritisk

Om du anger den här informationen när du skapar ett arbetsflöde blir det lättare att förstå hur allvarlig den konfigurerade processen är.

Det här alternativet har ingen funktionell inverkan på andra arbetsflöden än kampanjarbetsflöden.

Kampanjarbetsflöden (arbetsflöden som skapas som en del av en kampanj/åtgärd) med högre allvarlighetsgrad körs i första hand om kampanjen har många processer som ska köras samtidigt. Som standard kan bara 10 processer köras samtidigt i en kampanj, enligt alternativet NmsOperation_LimitConcurrency. Om en kampanj till exempel innehåller 25 arbetsflöden kommer arbetsflöden med högre allvarlighetsgrad att köras i den första poolen med 10 processer.

### Arbetsflödesövervakning {#workflow-monitoring}

Alla schemalagda arbetsflöden som körs i produktionsmiljöer bör övervakas för att varnas om ett fel uppstår.

I arbetsflödesegenskaperna väljer du en Supervisor-grupp, antingen standardgruppen **[!UICONTROL Workflow supervisors]** eller en anpassad grupp. Se till att minst en operator tillhör den här gruppen, med en e-postkonfiguration.

Innan du börjar skapa ett arbetsflöde måste du definiera arbetsflödesansvariga. De meddelas via e-post om fel uppstår. Mer information finns i [Hantera fel](../../workflow/using/monitoring-workflow-execution.md#managing-errors).

Kontrollera regelbundet **[!UICONTROL Monitoring]** universum för att se den övergripande statusen för de aktiva arbetsflödena. Mer information finns i [Instansövervakning](../../workflow/using/monitoring-workflow-execution.md#instance-supervision).

Workflow HeatMap gör att Adobe Campaign-plattformens administratörer kan övervaka belastningen på instansen och planera arbetsflödena i enlighet med detta. Mer information finns i [Arbetsflödesövervakning](../../workflow/using/heatmap.md).

## Använda aktiviteter {#using-activities}

>[!CAUTION]
>
>Du kan kopiera och klistra in aktiviteter i samma arbetsflöde. Vi rekommenderar dock inte att du kopierar inklistringsaktiviteter i olika arbetsflöden. Vissa inställningar som är kopplade till aktiviteter som Leveranser och Schemaläggare kan leda till konflikter och fel när målarbetsflödet körs. Vi rekommenderar i stället att du **duplicerar** arbetsflöden. Mer information finns i [Duplicera arbetsflöden](../../workflow/using/building-a-workflow.md#duplicating-workflows).

### Namn på aktiviteten {#name-of-the-activity}

När du utvecklar ditt arbetsflöde får alla aktiviteter ett namn, liksom alla Adobe Campaign-objekt. När namnet genereras av verktyget rekommenderar vi att du byter namn på det med ett explicit namn när du konfigurerar det. Risken med att göra det senare är att det kan avbryta arbetsflödet med aktiviteter med hjälp av namnet på en annan tidigare aktivitet. Det skulle därför vara svårt att uppdatera namnen efteråt.

Aktivitetsnamnet finns på **[!UICONTROL Advanced]** fliken. Ge dem inte namn **[!UICONTROL query]**, **[!UICONTROL query1]** utan ge dem explicita namn som **[!UICONTROL query11]****[!UICONTROL querySubscribedRecipients]**. Det här namnet visas i journalen, och om tillämpligt i SQL-loggarna, och det hjälper till att felsöka arbetsflödet när det konfigureras.

### Första och sista aktiviteten {#first-and-last-activities}

* Starta alltid arbetsflödet med en **[!UICONTROL Start]** aktivitet eller en **[!UICONTROL Scheduler]** aktivitet. När det är relevant kan du även använda en **[!UICONTROL External signal]** aktivitet.
* När du skapar ditt arbetsflöde ska du bara använda en aktivitet per gren **[!UICONTROL Scheduler]** . Om samma gren i ett arbetsflöde har flera schemaläggare (länkade till varandra), multipliceras antalet uppgifter som ska utföras exponentiellt, vilket skulle innebära att databasen överbelastas avsevärt. Den här regeln gäller även för alla aktiviteter med en **[!UICONTROL Scheduling & History]** flik. Läs mer om [schemaläggning](../../workflow/using/scheduler.md).

   ![](assets/wf-scheduler.png)

* Använd **[!UICONTROL End]** aktiviteter för alla arbetsflöden. På så sätt kan Adobe Campaign frigöra temporärt utrymme som används för beräkningar i arbetsflöden. Mer information finns i: [Start och slut](../../workflow/using/start-and-end.md).

### Javascript inom en aktivitet {#javascript-within-an-activity}

Du kanske vill lägga till JavaScript när du initierar en arbetsflödesaktivitet. Detta kan du göra på aktivitetens flik **[!UICONTROL Advanced]** .

Om du vill göra det enklare att spåra arbetsflödet rekommenderar vi att du använder dubbla streck i början och slutet av aktivitetsetiketten enligt följande: — Min etikett —.

### Signal {#signal}

Oftast vet du inte varifrån signalen anropas. För att undvika det här problemet kan du använda fältet **[!UICONTROL Comment]** på fliken **[!UICONTROL Advanced]** i signalaktiviteten för att dokumentera det förväntade ursprunget för en signal för den här aktiviteten.

![](assets/workflow-signal-bp.png)

## Uppdatering av arbetsflöde {#workflow-update}

Ett produktionsarbetsflöde får inte uppdateras direkt. Om inte processen består av att skapa en kampanj med mallarbetsflöden, bör processerna först testas i en utvecklingsmiljö. Efter den här valideringen kan arbetsflödet distribueras och startas i produktionen.

Utför alla tester i utvecklings- eller stagingmiljöer, inte i produktionsmiljöer. Prestanda kan inte säkerställas i sådana fall.

Arkiverade arbetsflöden kan finnas på utvecklings- eller testplattformar i en arkiverad mapp, men produktionsmiljön bör vara så ren som möjligt. Gamla arbetsflöden bör tas bort från produktionsmiljön om de är inaktiva.
