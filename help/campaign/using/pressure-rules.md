---
title: Tryckregler
seo-title: Tryckregler
description: Tryckregler
seo-description: null
page-status-flag: never-activated
uuid: 653d8336-8765-4938-88c1-a96cd76c3b7e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 3710768e-ab7f-40a4-9c48-830695adc990
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Tryckregler{#pressure-rules}

## Om reklamtrötthet {#about-marketing-fatigue}

Genom att implementera tryckhantering kan ni undvika att överbelasta databaspopulationen, vilket också kallas utmattning för marknadsföring. För att göra detta kan du definiera ett maximalt antal meddelanden per mottagare. Ni kan också tillämpa skiljedomsregler mellan kampanjer för att skicka det bästa meddelandet till målgruppen.

**Tryckregler** , t.ex. för att hantera reklamtrötthet, för att begränsa antalet brev som ska skickas till en population till två, för att välja den kommunikation som bäst motsvarar en grupp abonnenters intressen, för att undvika att skicka ett SMS till en missnöjd kund, osv.

Kampanjer väljs ut baserat på definierade trösklar och meddelandevikt.

* Ett tröskelvärde är det högsta antalet leveranser som tillåts för en viss mottagare under en viss period. Den kan vara inställd eller variabel. Den anges eller beräknas i typologiregelinställningarna. Se [Maximalt antal meddelanden](#maximum-number-of-messages).
* Med leveransvikter kan ni identifiera leveranser med högsta prioritet inom ramen för tryckhantering. Meddelanden med högst vikt har prioritet. Se [Meddelandevikt](#message-weight).

Skiljeförfarandet består i att se till att schemalagda kampanjer, vars vikt är större än den pågående kampanjen, inte leder till alltför stor profilbegäran: om så är fallet, utesluts profilen från leveransen.

Skiljekriterierna (meddelandets vikt och/eller tröskelvärde) kan variera beroende på två typer av information:

* mottagarens inställning, som är deklarativ information: prenumerationer på nyhetsbrev, mottagarstatus (kund eller potentiell kund),
* mottagarens beteende: inköp, besökta länkar osv.

Skiljedomsregeln för att definiera godtagbara meddelanden tillämpas under analysfasen. För varje mottagare och för den berörda perioden skickas meddelandet om följande formel är sann: **(antal skickade meddelanden) + (antal meddelanden med större vikt) &lt; tröskelvärde**.

Annars blir mottagaren **[!UICONTROL Excluded by arbitration]**. Mer information finns i [Uteslutning efter skiljedom](#exclusion-after-arbitration).

## Skapa en tryckregel {#creating-a-pressure-rule}

Om du vill skapa skiljeväggar mellan kampanjer med Adobe Campaign börjar du med att skapa kampanjtypologier och definiera länkade typologiregler (**tryckregler** ).

Så här skapar och konfigurerar du en **[!UICONTROL Pressure]** typologiregel:

1. Klicka på **[!UICONTROL New]** ikonen ovanför listan i listan över kampanjtypologiregler.

   ![](assets/campaign_opt_create_a_rule_01.png)

1. Markera en regel av typen **[!UICONTROL General]** Tryck **** på fliken för den nya regeln och ange ett namn och en beskrivning för den.

   ![](assets/campaign_opt_create_a_rule_02.png)

1. Ändra körningsordningen om det behövs. När flera typologiregler används som en **[!UICONTROL Typology]** uppsättning tillämpas de lägre ordnade reglerna först. Mer information finns i [Körningsordning](../../campaign/using/applying-rules.md#execution-order).
1. I avsnittet anger du en frekvens om du vill spara målgruppsanpassning efter nästa dagliga omskiljningskörning. **[!UICONTROL Calculation parameters]** Mer information finns i [Justera beräkningsfrekvens](../../campaign/using/applying-rules.md#adjusting-calculation-frequency).
1. Klicka på **[!UICONTROL Pressure]** fliken och välj den kalenderperiod som typologiregeln gäller för.

   ![](assets/campaign_opt_create_a_rule_03.png)

   Regeln kommer att tillämpas på leveranser vars kontaktdatum är inkluderat i den berörda perioden.

   >[!NOTE]
   >
   >Schemalagda leveranser beaktas endast om du väljer **[!UICONTROL Take the deliveries into account in the provisional calendar]** alternativet. Mer information finns i [Ange perioden](#setting-the-period).

1. Definiera metoden för att beräkna det högsta antalet meddelanden.

   Tröskelvärdet är det högsta antal meddelanden som kan skickas till en mottagare under den aktuella perioden.

   Som standard är tröskelvärdet konstant och du måste ange ett maximalt antal meddelanden som tillåts av regeln.

   ![](assets/campaign_opt_create_a_rule_03b.png)

   Om du vill definiera ett variabeltröskelvärde markerar du **[!UICONTROL Depends on the recipient]** värdet i **[!UICONTROL Type of threshold]** fältet och använder ikonen till höger för att öppna uttrycksredigeraren.

   ![](assets/campaign_opt_create_a_rule_04.png)

   Mer information finns i [Maximalt antal meddelanden](#maximum-number-of-messages).

1. Ange metod för beräkning av leveransvikt.

   Varje leverans har en vikt, dvs. ett värde som representerar dess prioritetsnivå: Detta möjliggör skiljeförfaranden mellan kampanjer. Vikten beräknas med hjälp av den formel som definieras i typologiregeln och/eller i dess egenskaper. Mer information finns i [Meddelandevikt](#message-weight).

1. Som standard tas alla meddelanden med i beräkningen av tröskelvärdet. På fliken **[!UICONTROL Restriction]** kan du filtrera de meddelanden som berörs av typologiregeln:

   * I det övre avsnittet på den här fliken kan du begränsa vilka mottagare som påverkas.
   * I det nedre avsnittet på den här fliken kan du filtrera de meddelanden som ska räknas.

      I följande exempel beaktas endast mottagare som sparats i mappen **NewContacts** och leveranser som börjar med **Newsletter** .
   ![](assets/campaign_opt_create_a_rule_05.png)

1. På fliken **[!UICONTROL Typologies]** kan du visa de kampanjtyper som tillämpar den här regeln eller länka regeln till en eller flera befintliga typologier. Mer information finns i [Använda typologier](../../campaign/using/about-campaign-typologies.md#applying-typologies).

## Definiera tröskelvärden och vikter {#defining-thresholds-and-weights}

### Maximalt antal meddelanden {#maximum-number-of-messages}

Varje tryckregel definierar ett tröskelvärde, dvs. det maximala antalet meddelanden som kan skickas till en mottagare under en viss tidsperiod. När denna tröskel har uppnåtts kan inga fler leveranser göras förrän efter utgången av skadeundersökningsperioden. Med den här processen kan du automatiskt utesluta en mottagare från en leverans om ett meddelande överskrider det angivna tröskelvärdet och på så sätt undvika överdriven begäran.

Tröskelvärden kan antingen vara konstanta eller beräknas med en formel med variabler. Detta innebär att tröskelvärdena för en viss period kan variera från en mottagare till en annan, eller till och med för samma mottagare.

![](assets/campaign_opt_create_a_rule_threshold.png)

>[!CAUTION]
>
>Om **0** anges som ett tröskelvärde förhindras alla leveranser till målpopulationen under skadeundersökningsperioden.

**Exempel:**

Du kan indexera antalet auktoriserade meddelanden beroende på vilket segment mottagaren tillhör. Det innebär att en mottagare som tillhör webbsegmentet kan få fler meddelanden än andra mottagare. En **[!UICONTROL Iif (@origin='Web', 5, 3)]** typformel tillåter leverans av 5 meddelanden till mottagare och 3 för andra segment. Konfigurationen blir följande:

![](assets/campaign_opt_pressure_sample.png)

Om du vill definiera tröskelvärdet kan du använda en dimension som är länkad till måldimensionen: om du till exempel vill inkludera meddelanden som levereras till mottagarprofiler som lagras i besökstabellen (för mer information i besökstabellen, se [detta avsnitt](../../web/using/use-case--creating-a-refer-a-friend-form.md)) eller för att undvika att skicka mer än ett meddelande per vecka till samma hushåll (som kan hänvisa till flera e-postadresser) som identifieras i en dimension som är länkad till mottagarnas.

Om du vill göra det markerar du **[!UICONTROL Count messages on a linked dimension]** alternativet och väljer sedan besökaren eller kontakttabellen.

### Meddelandevikt {#message-weight}

Varje leverans har en vikt som motsvarar dess prioritetsnivå. Som standard är vikten för en leverans inställd på 5. Med tryckregler kan du definiera vikten på de leveranser som de ska tillämpas på.

Vikter kan antingen anges eller beräknas med en formel som passar mottagarna. Du kan till exempel definiera vikten för en leverans baserat på mottagarens intressen.

>[!CAUTION]
>
>Vikten som definieras i en typologiregel kan överladdas individuellt för varje leverans på **[!UICONTROL Properties]** fliken. Klicka på **[!UICONTROL Typology]** fliken för att välja kampanjtyp och ange vilken vikt som ska användas om det behövs.\
>Vikten som deklarerats i en A-typologiregel används dock inte för att beräkna en B-typologiregel: den här vikten gäller endast leveranser som använder A-regeln.

**Exempel:**

I följande exempel vill vi länka vikten på nyhetsbrev på musik till mottagarnas benägenhetspoäng. Så här gör du:

1. Skapa ett nytt fält för att lagra poängvärden för mottagarnas benägenhet. Fältet, **@Music** i det här fallet, kommer att berikas med svar på enkäter och online-enkäter, insamlade spårningsdata osv.
1. Skapa en typologiregel för att beräkna meddelandevikten baserat på det här fältet.

   ![](assets/campaign_opt_pressure_weight_sample.png)

1. Använd den här regeln för meddelanden med följande ämne: nyhetsbrev, specialerbjudanden osv. Vikten av dessa leveranser, och därmed deras prioritet, beror på varje mottagares benägenhetspoäng.

## Ange period {#setting-the-period}

Tryckregler definieras i **vardagar**.

Perioden konfigureras på regelns **[!UICONTROL Pressure]** flik. Du kan ange antalet dagar och vid behov välja vilken typ av gruppering som ska användas (dag, vecka, månad, kvartal osv.).

Med grupperingstypen kan du utöka **[!UICONTROL Period considered]** fältet till hela dagen, kalenderveckan, kalendermånaden eller kalenderåret för datum för perioden.

En tryckregel som definierar ett tröskelvärde på 2 meddelanden per vecka, med en gruppering för varje kalendermånad, förhindrar till exempel att fler än 2 meddelanden levereras inom samma vecka OCH inom samma kalendermånad. Varning! Om perioden överlappar två månader kommer beräkningströskeln att ta hänsyn till leveranser från dessa två kalendermånader och kan därför förhindra alla nya leveranser under den andra månaden.

>[!NOTE]
>
>Som standard beaktas endast leveranser som redan har skickats vid beräkning av tröskelvärdet. Markera alternativet **[!UICONTROL Take the deliveries into account in the provisional calendar]** om du även vill ta hänsyn till planerade leveranser för den aktuella perioden. I detta fall fördubblas skadeundersökningsperioden för att möjliggöra integrering av såväl framtida leveranser som tidigare leveranser.\
>Om du vill begränsa antalet leveranser som beaktas till en tvåveckorsperiod kan du antingen:
>
>* Ange **15d** i **[!UICONTROL Concerned period]** fältet: Leveranser som skickats upp till två veckor före leveransdagen och som regeln tillämpas på ska beaktas vid beräkningen.
>
>  
eller
>
>* Ange **7d** i **[!UICONTROL Period considered]** fältet OCH kontrollera **[!UICONTROL Take the deliveries into account in the provisional calendar]**\
   >alternativ: leveranser som skickas upp till 7 dagar före leveransdatumet och som schemalagts upp till 7 dagar efter leveransdatumet då regeln tillämpas kommer att beaktas vid beräkningen.
>
>
Periodens startdatum beror på hur databasen är konfigurerad.

Om du t.ex. tillämpar en 15-dagars tryckregel utan gruppering för en leverans som är daterad 12/11, kommer leveranser att tas med i beräkningen mellan 11/27 och 12/12. Om tryckregeln tar hänsyn till leveranserna i den preliminära kalendern, kommer alla leveranser som planeras mellan 11/27 och 12/27 att beaktas. Slutligen, om du konfigurerar en gruppering per kalendermånad i regeln, kommer alla leveranser i november och december att beaktas vid beräkningen av tröskelvärdet (från 11/1 till 12/31).

>[!CAUTION]
>
>**Vanliga fall**
>Om du vill vara säker på att leveranser för den aktuella kalenderveckan inte tas med i beräkningen, och inte ta hänsyn till de leveranser som kommer från föregående vecka för beräkningströskeln, anger du **[!UICONTROL Period considered]** &quot;0&quot; och väljer&quot;Gruppering per kalendervecka&quot; som **[!UICONTROL Period type]**.
> 
>När en period är större än 0 (till exempel 1) kan beräkningströskeln ta hänsyn till föregående dags leveranser. Om föregående dag motsvarar föregående kalendervecka och den valda periodtypen är Gruppering per kalendervecka, kommer därför alla föregående vecka att tas med i beräkningen.

**Exempel:**

Vi vill skapa en tryckregel som begränsar begäran till tre meddelanden per tvåveckorsperiod, med en gruppering efter kalendermånaden.

![](assets/campaign_opt_pressure_period_sample_1a.png)

Låt oss ta sex nyhetsbrev med samma vikt, som är schemalagda till 05/30, 06/3, 06/8, 06/12, 06/22 och 06/30.

![](assets/campaign_opt_pressure_period_sample_0.png)

De leveranser som planeras till den 12 och 30 juni kommer inte att skickas: Leveransen 06/12 skulle överstiga tröskelvärdet på 3 meddelanden per 2-veckorsperiod och den 30:e leveransen skulle överstiga tröskelvärdet för auktoriserad kommunikation per kalendermånad.

![](assets/campaign_opt_pressure_period_sample_1.png)

Alla mottagare av dessa leveranser undantas genom skiljedomsförfarande under analysfasen:

![](assets/campaign_opt_pressure_period_sample_2.png)

Om du grupperar leveranser per kvartal kommer även mottagarna av **nyhetsbrevet nr 5** att exkluderas, och det kommer inte att skickas.

Om ingen gruppering är markerad skickas inte bara **nyhetsbrevet nr.4** , eftersom det var schemalagt för samma tvåveckorsperiod som de tre första nyhetsbreven.

>[!NOTE]
>
>När du ändrar definitionen för en typologiregel kan du skapa en **simulering** som styr hur den påverkar de leveranser den används på och övervaka hur leveranserna påverkar varandra. Mer information finns i [Kampanjsimuleringar](../../campaign/using/campaign-simulations.md).

## Uteslutning efter skiljedom {#exclusion-after-arbitration}

Skiljeförfarandet tillämpas varje kväll via det **[!UICONTROL Forecasting]** tekniska arbetsflödet och **[!UICONTROL Campaign jobs]** arbetsflödet.

Arbetsflödet förberäknar data för den aktuella perioden (från startdatumet till det aktuella datumet), vilket gör att typologiregler kan användas under analysen. **[!UICONTROL Forecasting]** Den beräknar också om räknare för uteslutning för skiljedom varje kväll.

För varje mottagare kontrollerar Adobe Campaign att antalet meddelanden som ska skickas inte överstiger tröskelvärdet, med hänsyn tagen till antalet meddelanden som redan skickats under den aktuella perioden. Den här informationen är en **indikator** eftersom alla beräkningar uppdateras vid leveranstillfället.

Om det här antalet överskrider tröskelvärdet tillämpas de skiljeregler som definierats i kampanjtypologin och mottagarna utesluts från kampanjer med lägre vikt.

![](assets/campaign_opt_pressure_exclusion.png)

>[!NOTE]
>
>Om flera leveranser har samma poängtal skickas kampanjen för det tidigaste datumet.

## Användningsfall för tryckregler {#use-cases-on-pressure-rules}

### Anpassning av tröskelvärdet baserat på kriterium {#adapting-the-threshold-based-on-criterion}

Vi vill skapa en typologiregel för att förhindra att fler än fyra meddelanden per vecka skickas till kunder och två meddelanden per vecka till potentiella kunder.

Om du vill identifiera kunder och potentiella kunder använder du **[!UICONTROL Status]** fältet, som innehåller 0 för potentiella kunder och 1 för kunder.

Så här skapar du regeln:

1. Skapa en ny typologiregel för **trycktyp** .
1. Redigera **[!UICONTROL Pressure]** fliken: i **[!UICONTROL Maximum number of messages]** avsnittet vill vi skapa en formel för att beräkna tröskelvärdet beroende på varje mottagare. Markera **[!UICONTROL Depends on the recipient]** värdet i **[!UICONTROL Threshold type]** fältet och klicka sedan **[!UICONTROL Edit expression]** till höger om **[!UICONTROL Formula]** fältet.

   Klicka på **[!UICONTROL Advanced parameters]** knappen för att definiera beräkningsformeln.

   ![](assets/campaign_opt_pressure_sample_1_1.png)

1. Markera **[!UICONTROL Edit the formula using an expression]** alternativet och klicka på **[!UICONTROL Next]**.

   ![](assets/campaign_opt_pressure_sample_1_2.png)

1. Dubbelklicka på funktionen **Iif** i **[!UICONTROL Others]** noden i listan över funktioner.

   Välj sedan mottagarnas **status** i **[!UICONTROL Available fields]** avsnittet.

   ![](assets/campaign_opt_pressure_sample_1_3.png)

   Ange följande formel: **Iif(@status=0,2,4)**

   ![](assets/campaign_opt_pressure_sample_1_4.png)

   Med den här formeln kan du tilldela värdet 2 om statusen är lika med 0 och värdet 4 för alla andra statusvärden.

   Klicka **[!UICONTROL Finish]** för att godkänna formeln.

1. Ange den period under vilken regeln gäller: 7 dagar i det här fallet för att räkna antalet meddelanden per vecka.

   ![](assets/campaign_opt_pressure_sample_1_5.png)

1. Spara regeln för att godkänna skapandet.

Länka nu den regel du just har skapat till en typologi för att använda den på leveranser. Så här gör du:

1. Skapa en kampanjtypologi.
1. Gå till fliken **[!UICONTROL Rules]** , klicka på **[!UICONTROL Add]** knappen och välj den regel du just har skapat.

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. Spara typologin: läggs det till i listan över befintliga typologier.

Om du vill använda den här typologin i dina leveranser markerar du den i leveransegenskaperna på **[!UICONTROL Typology]** fliken enligt nedan:

![](assets/campaign_opt_pressure_sample_1_7.png)

>[!NOTE]
>
>Typologin kan definieras i leveransmallen som automatiskt ska tillämpas på alla leveranser som skapas med den här mallen.

Vid leveransanalys utesluts leveransmottagarna vid behov från leveransen, beroende på hur många leveranser de redan har skickat. Om du vill visa den här informationen kan du:

* Visa analysresultatet:

   ![](assets/campaign_opt_pressure_sample_1_8.png)

* Redigera leveransen och klicka på **[!UICONTROL Delivery]** fliken och **[!UICONTROL Exclusions]** underfliken:

   ![](assets/campaign_opt_pressure_sample_1_9.png)

* Klicka på **[!UICONTROL Audit]** fliken och sedan på **[!UICONTROL Causes of exclusions]** underfliken för att visa antalet undantag och de typologiregler som används:

   ![](assets/campaign_opt_pressure_sample_1_10.png)

### Beräkna leveransvikt baserat på beteende {#calculating-the-delivery-weight-based-on-behavior}

Du kan definiera tryckregler baserat på mottagarens beteende: Det innebär att en leverans kan anpassas till kriterier som varierar mellan olika mottagare. Du kan till exempel bestämma dig för att skicka ett meddelande beroende på om en mottagare besökt din webbplats eller inte, klickat i ett visst avsnitt av det senaste nyhetsbrevet, prenumererat på en informationstjänst eller till och med baserat på svar på en undersökning, ett onlinespel osv.

I följande exempel vill vi skapa en leverans med vikten 5. Den här vikten har berikats med benägenhetspoäng baserat på mottagarens beteende: kunder som redan beställt från denna webbplats får 5 poäng, medan kunder som aldrig beställt online får 4 poäng.

Om du vill utföra den här typen av konfiguration måste du använda en formel för att definiera meddelandets vikt. Information om benägenhetspoäng och enkätsvar måste finnas tillgänglig i datamodellen. I vårt exempel har fältet **Propensitet** lagts till.

Använd följande konfigurationssteg:

1. Skapa en ny typologiregel för **trycktyp** .
1. Redigera **[!UICONTROL Pressure]** fliken. Vi vill skapa en tröskelformel som baseras på varje enskild mottagare: klicka på **[!UICONTROL Edit expression]** ikonen till höger om **[!UICONTROL Weight formula]** fältet.

   ![](assets/campaign_opt_pressure_sample_2_1.png)

1. Som standard visas värde **5** i den övre delen av uttrycksredigeraren. Vi vill lägga till benägenhetspoängen för varje mottagare i den här vikten: placera markören till höger om 5, ange tecknet **+** och markera fältet **Propensitet** .

   ![](assets/campaign_opt_pressure_sample_2_2.png)

1. Lägg sedan till ett högre värde för mottagare som redan har gjort ett köp. För dem måste vikten på leveransen ökas med 5, medan för andra bara 4.

   ![](assets/campaign_opt_pressure_sample_2_3.png)

1. Klicka **[!UICONTROL Finish]** för att spara den här regeln.
1. Länka regeln till en kampanjtypologi och referera till den här typologin i en leverans för att godkänna den.

### Skicka endast de högsta viktade meddelandena {#sending-only-the-highest-weighted-messages}

Du vill inte skicka mer än två meddelanden inom samma vecka, med en gräns på två meddelanden per dag, till var och en av dina mottagare, och du vill bara att meddelanden med högre vikt ska levereras.

För att göra detta måste du schemalägga flera leveranser med olika vikter för samma mottagare och tillämpa en tryckregel som utesluter leveranser med lägre vikter.

Konfigurera först tryckregeln.

1. Skapa en tryckregel. Mer information finns i [Skapa en tryckregel](#creating-a-pressure-rule).
1. Välj **[!UICONTROL General]** alternativet på **[!UICONTROL Re-apply the rule at the start of personalization]** fliken.

   ![](assets/campaign_opt_pressure_example_5.png)

   Det här alternativet åsidosätter det värde som definieras i **[!UICONTROL Frequency]** fältet och tillämpar automatiskt regeln under personaliseringsfasen. Mer information finns i [Justera beräkningsfrekvens](../../campaign/using/applying-rules.md#adjusting-calculation-frequency).

1. På **[!UICONTROL Pressure]** fliken väljer du **[!UICONTROL 7d]** som **[!UICONTROL Period considered]** och **[!UICONTROL Grouping per day]** som **[!UICONTROL Period type]**.
1. Välj alternativet **[!UICONTROL Take the deliveries into account in the provisional calendar]** för att inkludera schemalagda leveranser.

   ![](assets/campaign_opt_pressure_example_1.png)

   Leveranser som skickas upp till 7 dagar före leveransdatumet och som schemalagts upp till 7 dagar efter leveransdatumet kommer att tas med i beräkningen. Mer information finns i [Ange perioden](#setting-the-period).

1. Länka regeln till en kampanjtypologi på fliken **[!UICONTROL Typologies]** .
1. Spara ändringarna.

Skapa och konfigurera nu ett arbetsflöde för varje leverans som du vill att tryckregeln ska tillämpas på.

1. Skapa en kampanj. Mer information finns i [det här avsnittet](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign).
1. Lägg till en **[!UICONTROL Targeting and workflows]** Query **-aktivitet i arbetsflödet på fliken** i kampanjen. Mer information om hur du använder den här aktiviteten finns i [det här avsnittet](../../workflow/using/query.md).
1. Lägg till en **[!UICONTROL Email delivery]** aktivitet i arbetsflödet och öppna den. Mer information om hur du använder den här aktiviteten finns i [det här avsnittet](../../workflow/using/delivery.md).
1. Gå till fliken **[!UICONTROL Approvals]** i **[!UICONTROL Delivery properties]** och inaktivera alla godkännanden.

   ![](assets/campaign_opt_pressure_example_2.png)

1. På fliken **[!UICONTROL Typology]** i **[!UICONTROL Delivery properties]** refererar du till den kampanjtypologi som regeln ska tillämpas på. Definiera en vikt för leveransen.

   ![](assets/campaign_opt_pressure_example_3.png)

1. Klicka på **[!UICONTROL Scheduling]** och välj **[!UICONTROL Schedule delivery (automatic execution when the scheduled date is reached)]** i leveransfönstret. I det här exemplet väljer du **[!UICONTROL Use a calculation formula]** alternativet.
1. Ange extraheringsdatumet till 10 minuter (aktuellt datum + 10 minuter).
1. Ange kontaktdatumet till nästa dag (aktuellt datum + 1 dag).

   ![](assets/campaign_opt_pressure_example_4.png)

   För att undantagen för tryckregler ska kunna implementeras måste du ange datum och tid för extraheringen innan kontaktdatum och -tid samt innan nattskiljedomsförfarandet tillämpas på nytt. Mer information finns i [Uteslutning efter skiljedom](#exclusion-after-arbitration).

1. Avmarkera **[!UICONTROL Confirm the delivery before sending]** alternativet och spara ändringarna.
1. Fortsätt på samma sätt för varje leverans som du vill skicka. Se till att du anger önskad vikt för varje leverans.
1. Kör de relevanta arbetsflödena för att förbereda och skicka leveranserna.

När det nattliga skiljeförfarandet tillämpas kommer leveranser med de lägre vikterna för samma mottagare att uteslutas. Endast de leveranser som har högst vikt kommer att skickas. Mer information finns i [Meddelandevikt](#message-weight).

Med tanke på att ett e-postmeddelande redan har skickats till de berörda mottagarna tidigare under veckan visar tabellen nedan ett exempel på konfigurationer som kan användas för ytterligare två leveranser.

<table> 
 <thead> 
  <tr> 
   <th> Leverans<br /> </th> 
   <th> Godkännanden<br /> </th> 
   <th> Bredd<br /> </th> 
   <th> Extraheringsdatum/-tid<br /> </th> 
   <th> Kontaktdatum<br /> </th> 
   <th> Startdatum/-tid för leverans<br /> </th> 
   <th> Körningsdatum/tid för skiljedomsarbetsflöde<br /> </th> 
   <th> Leveransstatus<br /> </th> 
   <th> Skickad leverans (datum/tid)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Leverans 1<br /> </td> 
   <td> Handikappade<br /> </td> 
   <td> 5<br /> </td> 
   <td> 3pm<br /> </td> 
   <td> 08:00 (nästa dag)<br /> </td> 
   <td> 2pm<br /> </td> 
   <td> Nightly<br /> </td> 
   <td> Exkluderad<br /> </td> 
   <td> Exkluderad<br /> </td> 
  </tr> 
  <tr> 
   <td> Leverans 2<br /> </td> 
   <td> Handikappade<br /> </td> 
   <td> 10<br /> </td> 
   <td> 4pm<br /> </td> 
   <td> 09:00 (nästa dag)<br /> </td> 
   <td> 2pm<br /> </td> 
   <td> Nightly<br /> </td> 
   <td> Skickat<br /> </td> 
   <td> 09:00 (nästa dag)<br /> </td> 
  </tr> 
 </tbody> 
</table>

Efter det att extraktionsdatumet har passerats för de två leveranserna, tillämpas det nattliga skiljeförfarandet på nytt före kontaktdatumen för båda leveranserna. På så sätt kan du hitta alla leveranser som redan har skickats (mottagare för vilka en leverans har bearbetats, registrerats via de breda loggarna) eller som har schemalagts för att skickas (mottagare som är berättigade att ta emot en leverans, som registrerats via prognosloggarna).

När alla skickade och potentiella leveranser har listats för den period som definierats i tryckregeln sorterar Adobe Campaign dem efter vikt, med den högsta viktningen först. När det tröskelvärde som anges i tryckregeln nås (om det inte finns fler än två e-postmeddelanden inom samma vecka), utesluts mottagarna från leveransen.
