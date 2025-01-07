---
product: campaign
title: God praxis för arbetsflöden
description: Lär dig mer om arbetsflöden för kampanjer
feature: Workflows
exl-id: 39c57f61-2629-4214-91e4-cb97dc039deb
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1381'
ht-degree: 5%

---

# God praxis för arbetsflöden{#workflow-best-practices}



## Körning och prestanda {#execution-and-performance}

Nedan visas allmänna riktlinjer för hur du optimerar Campaign-prestanda, inklusive bästa praxis för dina arbetsflöden.

Felsökningsriktlinjer för arbetsflödeskörning finns också i [Campaign Classic v7 Production Guide](../../production/using/workflow-execution.md).

### Loggar {#logs}

JavaScript-metoden **[!UICONTROL logInfo()]** är en bra lösning för att felsöka ett arbetsflöde. Den är användbar men måste användas med försiktighet, särskilt för aktiviteter som ofta körs: den kan överlagra loggarna och avsevärt öka storleken på loggtabellen. Men du kan också behöva mer än **[!UICONTROL logInfo()]**.

Det finns ytterligare två lösningar:

* **Behåll resultatet av interimpopulationer mellan två exekveringar**

  Med det här alternativet behålls temporära tabeller mellan två körningar av ett arbetsflöde. Den är tillgänglig på fliken **[!UICONTROL General]** i arbetsflödesegenskaperna och kan användas för att övervaka data och kontrollera resultat i utvecklings- och testsyfte. Du kan använda det här alternativet i utvecklingsmiljöer, men aldrig använda det i produktionsmiljöer. Om du behåller tillfälliga tabeller kan databasens storlek öka avsevärt och så småningom kan storleksgränsen nås. Dessutom kommer säkerhetskopieringen att bli långsammare.

  Endast arbetsregister för den senaste körningen av arbetsflödet behålls. Arbetsregister från tidigare körningar rensas av arbetsflödet **[!UICONTROL cleanup]**, som körs dagligen.

  >[!CAUTION]
  >
  >Det här alternativet får aldrig kontrolleras i ett produktionsarbetsflöde. Det här alternativet används för att analysera resultaten och är utformat endast för teständamål och ska därför endast användas i utvecklings- eller staging-miljöer.

* **Logga SQL-frågor i journalen**

  På fliken **[!UICONTROL Execution]** i arbetsflödesegenskaperna loggas alla SQL-frågor som genererats av verktyget från de olika aktiviteterna. Det är ett bra sätt att se vad som faktiskt utförs av plattformen. Detta alternativ bör dock endast användas tillfälligt under utvecklingen och inte aktiveras i produktionen.

Rensa loggarna när de inte behövs längre. Arbetsflödeshistorik rensas inte automatiskt: alla meddelanden behålls som standard. Historiken kan rensas via menyn **[!UICONTROL File > Actions]** eller genom att klicka på knappen Åtgärder i verktygsfältet ovanför listan. Välj Rensa historik.
Mer information om hur du tömmer dina loggar finns i [dokumentationen](starting-a-workflow.md).

### Arbetsflödesplanering {#workflow-planning}

* Försök att bibehålla en stabil aktivitetsnivå under dagen och undvika toppar för att förhindra att instansen överbelastas. Det gör du genom att fördela arbetsflödets starttider jämnt över hela dagen.
* Schemalägg datainläsning över en natt för att minska resurskonflikter.
* Långa arbetsflöden kan eventuellt påverka server- och databasresurserna. Dela de längsta arbetsflödena för att minska bearbetningstiden.
* Om du vill minska den totala körtiden ersätter du tidskrävande aktiviteter med förenklade och snabbare aktiviteter.
* Undvik att köra fler än 20 arbetsflöden samtidigt. När alltför många arbetsflöden körs samtidigt kan systemet få slut på resurser och bli instabilt. Mer information om varför arbetsflödet kanske inte startar finns i den här [artikeln](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html).


### Kör i motoralternativet {#execute-in-the-engine-option}

Kontrollera aldrig alternativet **[!UICONTROL Execute in the engine]** i fönstret **[!UICONTROL Workflow properties]**. När det här alternativet är aktiverat får arbetsflödet prioritet och alla andra arbetsflöden stoppas av arbetsflödesmotorn tills det är klart.

![](assets/wf-execute-in-engine.png)

## Egenskaper för arbetsflöde {#workflow-properties}

### Arbetsflödesmappar {#workflow-folders}

Adobe rekommenderar att du skapar arbetsflöden i en dedikerad mapp.

Om arbetsflödet påverkar hela plattformen (till exempel rensningsprocesser) kan du lägga till en undermapp i den inbyggda **[!UICONTROL Technical Workflows]**-mappen.

### Namnge arbetsflöde {#workflow-naming}

Eftersom det gör det enklare att hitta och felsöka dem om de inte fungerar på rätt sätt rekommenderar Adobe att du ger arbetsflödena egna namn och etiketter: fyll i arbetsflödets beskrivningsfält för att sammanfatta den process som ska utföras så att operatören kan förstå den utan problem.

Om arbetsflödet är en del av en process som innefattar flera arbetsflöden kan du vara explicit när du anger en etikett. Att använda siffror är ett bra sätt att ordna arbetsflödena (efter etikett).

Exempel:

* 001 - Importera - Importera mottagare
* 002 - Import - Importförsäljning
* 003 - Importera - Importera försäljningsinformation
* 010 - Exportera - Exportera leveransloggar
* 011 - Export - loggar för exportspårning

### Arbetsflödets allvarlighetsgrad {#workflow-severity}

Du kan konfigurera ett arbetsflödes svårighetsgrad i arbetsflödesegenskaperna på fliken **[!UICONTROL Execution]**:

* Normal
* Produktion
* Kritisk

Om du anger den här informationen när du skapar ett arbetsflöde blir det lättare att förstå hur allvarlig den konfigurerade processen är.

Det här alternativet har ingen funktionell inverkan på andra arbetsflöden än kampanjarbetsflöden.

Kampanjarbetsflöden (arbetsflöden som skapas som en del av en kampanj/åtgärd) med högre allvarlighetsgrad körs i första hand om kampanjen har många processer som ska köras samtidigt. Som standard kan bara 10 processer köras samtidigt i en kampanj, enligt alternativet NmsOperation_LimitConcurrency. Om en kampanj till exempel innehåller 25 arbetsflöden kommer arbetsflöden med högre allvarlighetsgrad att köras i den första poolen med 10 processer.

### Arbetsflödesövervakning {#workflow-monitoring}

Alla schemalagda arbetsflöden som körs i produktionsmiljöer bör övervakas för att varnas om ett fel uppstår.

I arbetsflödesegenskaperna väljer du en Supervisor-grupp, antingen standardgruppen **[!UICONTROL Workflow supervisors]** eller en anpassad grupp. Se till att minst en operator tillhör den här gruppen, med ett konfigurerat e-postmeddelande.

Innan du börjar skapa ett arbetsflöde måste du definiera arbetsflödesansvariga. De meddelas via e-post om fel uppstår. Mer information finns i [Hantera fel](monitoring-workflow-execution.md#managing-errors).

Kontrollera regelbundet fliken **[!UICONTROL Monitoring]** för att visa den övergripande statusen för de aktiva arbetsflödena. Mer information finns i [Instansövervakning](monitoring-workflow-execution.md#instance-supervision).

Med Workflow HeatMap kan Adobe Campaign plattformsadministratörer övervaka inläsningen av instansen och planera arbetsflödena utifrån detta. Mer information finns i [Arbetsflödesövervakning](heatmap.md).

## Använda aktiviteter {#using-activities}

>[!CAUTION]
>
>Du kan kopiera och klistra in aktiviteter i samma arbetsflöde. Vi rekommenderar dock inte att du kopierar inklistringsaktiviteter i olika arbetsflöden. Vissa inställningar som är kopplade till aktiviteter som Leveranser och Schemaläggare kan leda till konflikter och fel när målarbetsflödet körs. Vi rekommenderar i stället att du **duplicerar** arbetsflöden. Mer information finns i [Duplicera arbetsflöden](building-a-workflow.md#duplicating-workflows).

### Namn på aktiviteten {#name-of-the-activity}

När du utvecklar ditt arbetsflöde får alla aktiviteter ett namn, liksom alla Adobe Campaign-objekt. När namnet genereras av verktyget rekommenderar vi att du byter namn på det med ett explicit namn när du konfigurerar det. Risken med att göra det senare är att det kan avbryta arbetsflödet med aktiviteter med hjälp av namnet på en annan tidigare aktivitet. Det skulle därför vara svårt att uppdatera namnen efteråt.

Aktivitetsnamnet finns på fliken **[!UICONTROL Advanced]**. Ge dem inte namnen **[!UICONTROL query]**, **[!UICONTROL query1]**, **[!UICONTROL query11]**, men ge dem explicita namn som **[!UICONTROL querySubscribedRecipients]**. Det här namnet visas i journalen, och om tillämpligt i SQL-loggarna, och det hjälper till att felsöka arbetsflödet när det konfigureras.

### Första och sista aktiviteten {#first-and-last-activities}

* Starta alltid arbetsflödet med en **[!UICONTROL Start]**-aktivitet eller en **[!UICONTROL Scheduler]**-aktivitet. När det är relevant kan du även använda en **[!UICONTROL External signal]**-aktivitet.
* När du skapar ditt arbetsflöde ska du bara använda en **[!UICONTROL Scheduler]**-aktivitet per gren. Om samma gren i ett arbetsflöde har flera schemaläggare (länkade till varandra), multipliceras antalet uppgifter som ska utföras exponentiellt, vilket skulle innebära att databasen överbelastas avsevärt. Den här regeln gäller även för alla aktiviteter med en **[!UICONTROL Scheduling & History]**-flik. Läs mer om [Schemaläggning](scheduler.md).

  ![](assets/wf-scheduler.png)

* Använd **[!UICONTROL End]** aktiviteter för varje arbetsflöde. På så sätt kan Adobe Campaign frigöra temporärt utrymme som används för beräkningar i arbetsflöden. Mer information finns i: [Start och slut](start-and-end.md).

### Javascript inom en aktivitet {#javascript-within-an-activity}

Du kanske vill lägga till JavaScript när du initierar en arbetsflödesaktivitet. Detta kan göras på aktivitetens **[!UICONTROL Advanced]**-flik.

För att underlätta spärrning av arbetsflödet rekommenderar vi att du använder dubbla streck i början och slutet av aktivitetsetiketten enligt följande: — Min etikett —.

### Signal {#signal}

Oftast vet du inte varifrån signalen anropas. För att undvika det här problemet kan du använda fältet **[!UICONTROL Comment]** på fliken **[!UICONTROL Advanced]** i signalaktiviteten för att dokumentera den förväntade källan för en signal för den här aktiviteten.

![](assets/workflow-signal-bp.png)

## Uppdatering av arbetsflöde {#workflow-update}

Ett produktionsarbetsflöde får inte uppdateras direkt. Om inte processen består av att skapa en kampanj med mallarbetsflöden, bör processerna först testas i en utvecklingsmiljö. Efter den här valideringen kan arbetsflödet distribueras och startas i produktionen.

Utför alla tester i utvecklings- eller testmiljöer, inte i produktionsmiljöer. Prestanda kan inte säkerställas i sådana fall.

Arkiverade arbetsflöden kan finnas på utvecklings- eller testplattformar i en arkiverad mapp, men produktionsmiljön bör vara så ren som möjligt. Gamla arbetsflöden bör tas bort från produktionsmiljön om de är inaktiva.
