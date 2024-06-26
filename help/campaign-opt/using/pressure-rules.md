---
product: campaign
title: Tryckregler
description: Lär dig arbeta med tryckregler i Adobe Campaign
role: User, Data Engineer
feature: Fatigue Management, Typology Rules, Campaigns
exl-id: c23212f2-fdf8-4820-b389-546f7c84db27
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '3336'
ht-degree: 4%

---

# Tryckregler{#pressure-rules}

## Om reklamtrötthet {#about-marketing-fatigue}

Genom att implementera tryckhantering kan ni undvika att överbelasta databaspopulationen, vilket också kallas utmattning för marknadsföring. För att göra detta kan du definiera ett maximalt antal meddelanden per mottagare. Ni kan också tillämpa skiljedomsregler mellan kampanjer för att skicka det bästa meddelandet till målgruppen.

**Tryck** regler, för att hantera reklamtrötthet, till exempel för att begränsa antalet brev som ska skickas till en population till två, för att välja den kommunikation som bäst motsvarar en grupp abonnenters intressen, för att undvika att skicka ett SMS till en missnöjd kund, osv.

Kampanjer väljs ut baserat på definierade trösklar och meddelandevikt.

* Ett tröskelvärde är det högsta antalet leveranser som tillåts för en viss mottagare under en viss period. Den kan vara inställd eller variabel. Den anges eller beräknas i typologiregelinställningarna. Se [Maximalt antal meddelanden](#maximum-number-of-messages).
* Med leveransvikter kan ni identifiera leveranser med högsta prioritet inom ramen för tryckhantering. Meddelanden med högst vikt har prioritet. Se [Meddelandevikt](#message-weight).

Skiljeförfarandet består i att se till att schemalagda kampanjer, vars vikt är större än den pågående kampanjen, inte leder till alltför stor profilbegäran: i så fall utesluts profilen från leveransen.

Skiljekriterierna (meddelandets vikt och/eller tröskelvärde) kan variera beroende på två typer av information:

* mottagarinställning, som är deklarativ information: nyhetsbrevsprenumerationer, mottagarstatus (kund eller potentiell kund),
* mottagarens beteende: inköp, besökta länkar osv.

Skiljedomsregeln för att definiera godtagbara meddelanden tillämpas under analysfasen. För varje mottagare och för den berörda perioden skickas meddelandet om följande formel är sann: **(antal skickade meddelanden) + (antal meddelanden med större vikt) &lt; tröskelvärde**.

Annars blir mottagaren **[!UICONTROL Excluded by arbitration]**. Mer information finns i [Uteslutning efter skiljedom](#exclusion-after-arbitration).

## Skapa en tryckregel {#creating-a-pressure-rule}

Börja med att skapa kampanjtypologier och definiera länkade typologiregler (**Tryck** regler).

Så här skapar och konfigurerar du en **[!UICONTROL Pressure]**-typologiregel:

1. Klicka på knappen **[!UICONTROL New]** -ikonen ovanför listan.

   ![](assets/campaign_opt_create_a_rule_01.png)

1. I **[!UICONTROL General]** den nya regelns flik väljer du en **Tryck** skriv regeln och ange ett namn och en beskrivning för den.

   ![](assets/campaign_opt_create_a_rule_02.png)

1. Ändra körningsordningen om det behövs. När flera typologiregler används som **[!UICONTROL Typology]** de lägre ordnade reglerna tillämpas först. Mer information finns i [Körningsordning](applying-rules.md#execution-order).
1. I **[!UICONTROL Calculation parameters]** definierar du en frekvens om du vill spara målgruppsanpassning efter nästa dagliga omskiljningskörning. Mer information finns i [Justera beräkningsfrekvens](applying-rules.md#adjusting-calculation-frequency).
1. Klicka på **[!UICONTROL Pressure]** och välj den kalenderperiod under vilken typologiregeln gäller.

   ![](assets/campaign_opt_create_a_rule_03.png)

   Regeln kommer att tillämpas på leveranser vars kontaktdatum är inkluderat i den berörda perioden.

   >[!NOTE]
   >
   >Schemalagda leveranser beaktas endast om **[!UICONTROL Take the deliveries into account in the provisional calendar]** är markerat. Mer information finns i [Ange period](#setting-the-period).
   >

1. Definiera metoden för att beräkna det högsta antalet meddelanden.

   Tröskelvärdet är det högsta antal meddelanden som kan skickas till en mottagare under den aktuella perioden.

   Som standard är tröskelvärdet konstant och du måste ange ett maximalt antal meddelanden som tillåts av regeln.

   ![](assets/campaign_opt_create_a_rule_03b.png)

   Om du vill definiera ett variabeltröskelvärde väljer du **[!UICONTROL Depends on the recipient]** värdet i **[!UICONTROL Type of threshold]** och använder ikonen till höger för att öppna uttrycksredigeraren.

   ![](assets/campaign_opt_create_a_rule_04.png)

   Mer information finns i [Maximalt antal meddelanden](#maximum-number-of-messages).

1. Ange metod för beräkning av leveransvikt.

   Varje leverans har en vikt, dvs. ett värde som representerar dess prioritetsnivå: detta möjliggör medling mellan kampanjer. Vikten beräknas med hjälp av den formel som definieras i typologiregeln och/eller i dess egenskaper. Mer information finns i [Meddelandevikt](#message-weight).

1. Som standard tas alla meddelanden med i beräkningen av tröskelvärdet. The **[!UICONTROL Restriction]** kan du filtrera de meddelanden som berörs av typologiregeln:

   * I det övre avsnittet på den här fliken kan du begränsa vilka mottagare som påverkas.
   * I det nedre avsnittet på den här fliken kan du filtrera de meddelanden som ska räknas.

     I följande exempel har bara mottagare sparats i **NewContacts** -mappen beaktas och leveranser som börjar med **Nyhetsbrev** är bekymrade.

   ![](assets/campaign_opt_create_a_rule_05.png)

1. The **[!UICONTROL Typologies]** kan du visa de kampanjtyper som tillämpar den här regeln eller länka regeln till en eller flera befintliga typologier. Mer information finns i [Använda typologier](about-campaign-typologies.md#applying-typologies).

## Definiera tröskelvärden och vikter {#defining-thresholds-and-weights}

### Maximalt antal meddelanden {#maximum-number-of-messages}

Varje tryckregel definierar ett tröskelvärde, dvs. det maximala antalet meddelanden som kan skickas till en mottagare under en viss tidsperiod. När denna tröskel har uppnåtts kan inga fler leveranser göras förrän efter den beaktade perioden. Med den här processen kan du automatiskt utesluta en mottagare från en leverans om ett meddelande överskrider det angivna tröskelvärdet och på så sätt undvika överdriven begäran.

Tröskelvärden kan antingen vara konstanta eller beräknas med en formel med variabler. Detta innebär att tröskelvärdena för en viss period kan variera från en mottagare till en annan, eller till och med för samma mottagare.

![](assets/campaign_opt_create_a_rule_threshold.png)

>[!CAUTION]
>
>Inmatning **0** som ett tröskelvärde förhindrar alla leveranser till målpopulationen under skadeundersökningsperioden.

**Exempel:**

Du kan indexera antalet auktoriserade meddelanden beroende på vilket segment mottagaren tillhör. Det innebär att en mottagare som tillhör webbsegmentet kan få fler meddelanden än andra mottagare. An **[!UICONTROL Iif (@origin='Web', 5, 3)]** typformel tillåter leverans av 5 meddelanden till mottagare och 3 för andra segment. Konfigurationen blir följande:

![](assets/campaign_opt_pressure_sample.png)

Om du vill definiera tröskelvärdet kan du använda en dimension som är länkad till måldimensionen: t.ex. för att inkludera meddelanden som levereras till mottagarprofilerna som lagras i besökstabellen (mer information i besökstabellen finns i [det här avsnittet](../../surveys/using/use-case-creating-a-refer-a-friend-form.md)) eller för att undvika att skicka mer än ett meddelande per vecka till samma hushåll (som kan hänvisa till flera e-postadresser) som identifieras i en dimension som är länkad till mottagarnas.

Om du vill göra det väljer du **[!UICONTROL Count messages on a linked dimension]** väljer du sedan besökaren eller kontakttabellen.

### Meddelandevikt {#message-weight}

Varje leverans har en vikt som motsvarar dess prioritetsnivå. Som standard är vikten för en leverans inställd på 5. Med tryckregler kan du definiera vikten på de leveranser som de ska tillämpas på.

Vikter kan antingen anges eller beräknas med en formel som passar mottagarna. Du kan till exempel definiera vikten för en leverans baserat på mottagarens intressen.

>[!CAUTION]
>
>Vikten som definieras i en typologiregel kan överlastas individuellt för varje leverans, i **[!UICONTROL Properties]** -fliken. Klicka på **[!UICONTROL Typology]** för att välja kampanjtyp och, om det behövs, ange vilken vikt som ska användas.\
>Vikten som deklarerats i en A-typologiregel används dock inte för att beräkna en B-typologiregel: den här vikten gäller endast leveranser som använder A-regeln.

**Exempel:**

I följande exempel vill vi länka vikten på nyhetsbrev på musik till mottagarnas benägenhetspoäng. Så här gör du:

1. Skapa ett nytt fält för att lagra poängvärden för mottagarnas benägenhet. Fältet, **@Musik** i det här fallet kommer att berikas med svar på undersökningar och online-undersökningar, insamlade spårningsdata osv.
1. Skapa en typologiregel för att beräkna meddelandevikten baserat på det här fältet.

   ![](assets/campaign_opt_pressure_weight_sample.png)

1. Använd den här regeln för meddelanden med följande ämne: nyhetsbrev, specialerbjudanden osv. Vikten av dessa leveranser, och därmed deras prioritet, beror på varje mottagares benägenhetspoäng.

## Ange perioden {#setting-the-period}

Tryckregler definieras i **n**-dagars löpande perioder.

Perioden är konfigurerad i **[!UICONTROL Pressure]** -fliken för regeln. Du kan ange antalet dagar och vid behov välja vilken typ av gruppering som ska användas (dag, vecka, månad, kvartal osv.).

Med grupperingstypen kan du utöka **[!UICONTROL Period considered]** till hela dagen, kalenderveckan, kalendermånaden eller kalenderåret för datum för perioden.

En tryckregel som definierar ett tröskelvärde på 2 meddelanden per vecka, med en gruppering för varje kalendermånad, förhindrar till exempel att fler än 2 meddelanden levereras inom samma vecka OCH inom samma kalendermånad. Varning! Om perioden överlappar två månader kommer beräkningströskeln att ta hänsyn till leveranser från dessa två kalendermånader och kan därför förhindra alla nya leveranser under den andra månaden.

Observera att som standard beaktas endast leveranser som redan har skickats vid beräkningen av tröskelvärdet. I Campaign Classic v7 markerar du **[!UICONTROL Take the deliveries into account in the provisional calendar]** om du även vill ta hänsyn till planerade leveranser för den aktuella perioden. I detta fall fördubblas skadeundersökningsperioden för att möjliggöra integrering av såväl framtida leveranser som tidigare leveranser.

Om du vill begränsa antalet leveranser som beaktas till en tvåveckorsperiod kan du antingen:

1. Retur **15d** i **[!UICONTROL Concerned period]** Fält: Leveranser som har skickats upp till två veckor före leveransdatumet och som regeln tillämpas på ska beaktas vid beräkningen.

eller

1. Retur **7d** i **[!UICONTROL Period considered]** fält OCH kontrollera **[!UICONTROL Take the deliveries into account in the provisional calendar]** alternativ: leveranser som skickas upp till 7 dagar före leveransdatumet och som schemaläggs upp till 7 dagar efter leveransdatumet då regeln tillämpas kommer att tas med i beräkningen.

Periodens startdatum beror på hur databasen är konfigurerad.

Om du t.ex. tillämpar en 15-dagars tryckregel utan gruppering för en leverans som är daterad 12/11, kommer leveranser att tas med i beräkningen mellan 11/27 och 12/12. Om tryckregeln tar hänsyn till leveranserna i den preliminära kalendern, kommer alla leveranser som planeras mellan 11/27 och 12/27 att beaktas. Slutligen, om du konfigurerar en gruppering per kalendermånad i regeln, kommer alla leveranser i november och december att beaktas vid beräkningen av tröskelvärdet (från 11/1 till 12/31).


**Vanliga fall**

För att säkerställa att leveranser för den aktuella kalenderveckan inte tas med i beräkningen, och inte heller risken att ta hänsyn till leveranser från föregående vecka för beräkningströskeln, anger du **[!UICONTROL Period considered]** kl. 0 och välj Gruppering per kalendervecka som **[!UICONTROL Period type]**.

När en period är större än 0 (till exempel 1) kan beräkningströskeln ta hänsyn till föregående dags leveranser. Om föregående dag motsvarar föregående kalendervecka och den valda periodtypen är Gruppering per kalendervecka, kommer därför alla föregående vecka att tas med i beräkningen.

**Exempel:**

Vi vill skapa en tryckregel som begränsar begäran till tre meddelanden per tvåveckorsperiod, med en gruppering efter kalendermånaden.

![](assets/campaign_opt_pressure_period_sample_1a.png)

Låt oss ta sex nyhetsbrev med samma vikt, som är schemalagda till 05/30, 06/3, 06/8, 06/12, 06/22 och 06/30.

![](assets/campaign_opt_pressure_period_sample_0.png)

Leveranserna som planeras till den 12 och 30 juni kommer inte att skickas: leveranströskeln 06/12 skulle överstiga tröskelvärdet på 3 meddelanden per tvåveckorsperiod och den 30:e leveransen skulle överstiga tröskelvärdet för auktoriserad kommunikation per kalendermånad.

![](assets/campaign_opt_pressure_period_sample_1.png)

Alla mottagare av dessa leveranser undantas genom skiljedomsförfarande under analysfasen:

![](assets/campaign_opt_pressure_period_sample_2.png)

För samma regel gäller att om du grupperar leveranser per kvartal, ska mottagarna av **nyhetsbrev nr 5** kommer också att uteslutas, och det kommer inte att skickas.

Om ingen gruppering är markerad är det bara **nyhetsbrev nr 4** kommer inte att skickas eftersom det var schemalagt för samma tvåveckorsperiod som de tre första nyhetsbreven.

>[!NOTE]
>
>När du ändrar definitionen för en typologiregel kan du skapa en **Simulering** kontrollera hur leveranserna påverkar de leveranser de används för och övervaka hur leveranserna påverkar varandra. Mer information finns i [Kampanjsimuleringar](campaign-simulations.md).

## Uteslutning efter skiljedom {#exclusion-after-arbitration}

Skiljeförfarandet tillämpas varje kväll på nytt via **[!UICONTROL Forecasting]** tekniskt arbetsflöde och **[!UICONTROL Campaign jobs]** arbetsflöde.

The **[!UICONTROL Forecasting]** arbetsflödet förberäknar data för den aktuella perioden (från startdatumet till dagens datum), vilket gör att typologiregler kan tillämpas under analysen. Den beräknar också om räknare för uteslutning för skiljedom varje kväll.

För varje mottagare kontrollerar Adobe Campaign därför att antalet meddelanden som ska skickas inte överstiger tröskelvärdet, med hänsyn tagen till antalet meddelanden som redan har skickats under den berörda perioden. Informationen är **indikator**, eftersom alla beräkningar uppdateras vid leveranstillfället.

Om det här antalet överskrider tröskelvärdet tillämpas de skiljeregler som definierats i kampanjtypologin och mottagarna utesluts från kampanjer med lägre vikt.

![](assets/campaign_opt_pressure_exclusion.png)

>[!NOTE]
>
>Om flera leveranser har samma poängtal skickas kampanjen för det tidigaste datumet.

## Användningsfall för tryckregler {#use-cases-on-pressure-rules}

### Anpassa tröskelvärdet baserat på kriterium {#adapting-the-threshold-based-on-criterion}

Vi vill skapa en typologiregel för att förhindra att fler än fyra meddelanden per vecka skickas till kunder och två meddelanden per vecka till potentiella kunder.

Identifiera kunder och potentiella kunder med **[!UICONTROL Status]** -fält, som innehåller 0 för potentiella kunder och 1 för kunder.

Så här skapar du regeln:

1. Skapa ett nytt **Tryck** typologiregel.
1. Redigera **[!UICONTROL Pressure]** -flik: i **[!UICONTROL Maximum number of messages]** ska vi skapa en formel för att beräkna tröskeln beroende på varje mottagare. Välj **[!UICONTROL Depends on the recipient]** värdet i **[!UICONTROL Threshold type]** fält och klicka sedan på **[!UICONTROL Edit expression]** till höger om **[!UICONTROL Formula]** fält.

   Klicka på **[!UICONTROL Advanced parameters]** för att definiera beräkningsformeln.

   ![](assets/campaign_opt_pressure_sample_1_1.png)

1. Välj **[!UICONTROL Edit the formula using an expression]** och klicka **[!UICONTROL Next]**.

   ![](assets/campaign_opt_pressure_sample_1_2.png)

1. Dubbelklicka på **Iif** funktionen i **[!UICONTROL Others]** nod.

   Välj sedan mottagare **Status** i **[!UICONTROL Available fields]** -avsnitt.

   ![](assets/campaign_opt_pressure_sample_1_3.png)

   Ange följande formel: **Iif(@status=0,2,4)**

   ![](assets/campaign_opt_pressure_sample_1_4.png)

   Med den här formeln kan du tilldela värdet 2 om statusen är lika med 0 och värdet 4 för alla andra statusvärden.

   Klicka **[!UICONTROL Finish]** för att godkänna formeln.

1. Ange den period under vilken regeln gäller: 7 dagar i det här fallet, för att räkna antalet meddelanden per vecka.

   ![](assets/campaign_opt_pressure_sample_1_5.png)

1. Spara regeln för att godkänna skapandet.

Länka nu den regel du just har skapat till en typologi för att använda den på leveranser. Så här gör du:

1. Skapa en kampanjtypologi.
1. Gå till **[!UICONTROL Rules]** klickar du på **[!UICONTROL Add]** och välj den regel du nyss skapade.

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. Spara typologin: läggs den till i listan över befintliga typologier.

Om du vill använda den här typologin i dina leveranser väljer du den i leveransegenskaperna i dialogrutan **[!UICONTROL Typology]** enligt nedan:

![](assets/campaign_opt_pressure_sample_1_7.png)

>[!NOTE]
>
>Typologin kan definieras i leveransmallen som automatiskt ska tillämpas på alla leveranser som skapas med den här mallen.

Vid leveransanalys utesluts leveransmottagarna vid behov från leveransen, beroende på hur många leveranser de redan har skickat. Om du vill visa informationen kan du:

* Visa analysresultatet:

  ![](assets/campaign_opt_pressure_sample_1_8.png)

* Redigera leveransen och klicka på **[!UICONTROL Delivery]** -fliken och **[!UICONTROL Exclusions]** underflik:

  ![](assets/campaign_opt_pressure_sample_1_9.png)

* Klicka på **[!UICONTROL Audit]** -fliken och sedan **[!UICONTROL Causes of exclusions]** underflik för att visa antalet undantag och de tillämpade typologireglerna:

  ![](assets/campaign_opt_pressure_sample_1_10.png)

### Beräkna leveransvikten baserat på beteende {#calculating-the-delivery-weight-based-on-behavior}

Du kan definiera tryckregler baserat på mottagarnas beteende, vilket innebär att vikten på en leverans kan anpassas till kriterier som varierar mellan olika mottagare. Du kan till exempel bestämma dig för att skicka ett meddelande beroende på om en mottagare besökt din webbplats eller inte, klickat i ett visst avsnitt av det senaste nyhetsbrevet, prenumererat på en informationstjänst eller till och med baserat på svar på en undersökning, ett onlinespel osv.

I följande exempel vill vi skapa en leverans med vikten 5. Vikten har berikats med benägenhetspoäng baserat på mottagarnas beteende: kunder som redan beställt från den här webbplatsen får poängen 5, medan kunder som aldrig beställt online får poängen 4.

Om du vill utföra den här typen av konfiguration måste du använda en formel för att definiera meddelandets vikt. Information om benägenhetspoäng och enkätsvar måste finnas tillgänglig i datamodellen. I vårt exempel **Propensitet** fältet har lagts till.

Använd följande konfigurationssteg:

1. Skapa ett nytt **Tryck** typologiregel.
1. Redigera **[!UICONTROL Pressure]** -fliken. Vi vill skapa en tröskelformel som baseras på varje enskild mottagare: klicka på **[!UICONTROL Edit expression]** ikonen till höger om **[!UICONTROL Weight formula]** fält.

   ![](assets/campaign_opt_pressure_sample_2_1.png)

1. Som standard är värdet **5** visas i den övre delen av uttrycksredigeraren. Vi vill lägga till benägenhetspoängen för varje mottagare i den här vikten: placera markören till höger om 5, ange **+** tecken och markera **Propensitet** fält.

   ![](assets/campaign_opt_pressure_sample_2_2.png)

1. Lägg sedan till ett högre värde för mottagare som redan har gjort ett köp. För dem måste vikten på leveransen ökas med 5, medan för andra bara 4.

   ![](assets/campaign_opt_pressure_sample_2_3.png)

1. Klicka **[!UICONTROL Finish]** om du vill spara den här regeln.
1. Länka regeln till en kampanjtypologi och referera till den här typologin i en leverans för att godkänna den.

### Skicka endast de högst viktade meddelandena {#sending-only-the-highest-weighted-messages}

Du vill inte skicka mer än två meddelanden inom samma vecka, med en gräns på två meddelanden per dag, till var och en av dina mottagare, och du vill bara att meddelanden med högre vikt ska levereras.

För att göra detta måste du schemalägga flera leveranser med olika vikter för samma mottagare och tillämpa en tryckregel som utesluter leveranser med lägre vikter.

Först konfigurerar du tryckregeln.

1. Skapa en tryckregel. Mer information finns i [Skapa en tryckregel](#creating-a-pressure-rule).
1. I **[!UICONTROL General]** väljer du **[!UICONTROL Re-apply the rule at the start of personalization]** alternativ.

   ![](assets/campaign_opt_pressure_example_5.png)

   Det här alternativet åsidosätter det värde som definieras i **[!UICONTROL Frequency]** och tillämpar automatiskt regeln under personaliseringsfasen. Mer information finns i [Justera beräkningsfrekvens](applying-rules.md#adjusting-calculation-frequency).

1. I **[!UICONTROL Pressure]** flik, välja **[!UICONTROL 7d]** som **[!UICONTROL Period considered]** och **[!UICONTROL Grouping per day]** som **[!UICONTROL Period type]**.
1. Välj **[!UICONTROL Take the deliveries into account in the provisional calendar]** möjlighet att inkludera planerade leveranser.

   ![](assets/campaign_opt_pressure_example_1.png)

   Leveranser som skickas upp till 7 dagar före leveransdatumet och som schemalagts upp till 7 dagar efter leveransdatumet kommer att tas med i beräkningen. Mer information finns i [Ange perioden](#setting-the-period).

1. I **[!UICONTROL Typologies]** länka regeln till en kampanjtypologi.
1. Spara ändringarna.

Skapa och konfigurera nu ett arbetsflöde för varje leverans som du vill att tryckregeln ska tillämpas på.

1. Skapa en kampanj. Mer information om detta finns i [det här avsnittet](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign).
1. I **[!UICONTROL Targeting and workflows]** fliken med kampanjen, lägg till en **Fråga** till ditt arbetsflöde. Mer information om hur du använder den här aktiviteten finns i [det här avsnittet](../../workflow/using/query.md).
1. Lägg till en **[!UICONTROL Email delivery]** till arbetsflödet och öppna det. Mer information om hur du använder den här aktiviteten finns i [det här avsnittet](../../workflow/using/delivery.md).
1. Gå till **[!UICONTROL Approvals]** -fliken i **[!UICONTROL Delivery properties]** och inaktivera alla godkännanden.

   ![](assets/campaign_opt_pressure_example_2.png)

1. I **[!UICONTROL Typology]** -fliken i **[!UICONTROL Delivery properties]** refererar du till kampanjens typologi för att tillämpa regeln. Definiera en vikt för leveransen.

   ![](assets/campaign_opt_pressure_example_3.png)

1. Klicka på **[!UICONTROL Scheduling]** och markera **[!UICONTROL Schedule delivery (automatic execution when the scheduled date is reached)]**. I det här exemplet väljer du **[!UICONTROL Use a calculation formula]** alternativ.
1. Ange extraheringsdatumet till 10 minuter (aktuellt datum + 10 minuter).
1. Ange kontaktdatumet till nästa dag (aktuellt datum + 1 dag).

   ![](assets/campaign_opt_pressure_example_4.png)

   För att undantagen för tryckregler ska kunna implementeras måste du ange datum och tid för extraheringen innan kontaktdatum och -tid samt innan nattskiljedomsförfarandet tillämpas på nytt. Mer information finns i [Uteslutning efter skiljedom](#exclusion-after-arbitration).

1. Avmarkera **[!UICONTROL Confirm the delivery before sending]** och spara ändringarna.
1. Fortsätt på samma sätt för varje leverans som du vill skicka. Se till att du anger önskad vikt för varje leverans.
1. Kör relevanta arbetsflöden för att förbereda och skicka leveranserna.

När det nattliga skiljeförfarandet tillämpas kommer leveranser med de lägre vikterna för samma mottagare att uteslutas. Endast leveranser med den högsta vikten kommer att övervägas för sändning. Mer information finns i [Meddelandevikt](#message-weight).

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
   <td> 13:00<br /> </td> 
   <td> 08:00 (nästa dag)<br /> </td> 
   <td> 2:00<br /> </td> 
   <td> Nightly<br /> </td> 
   <td> Exkluderad<br /> </td> 
   <td> Exkluderad<br /> </td> 
  </tr> 
  <tr> 
   <td> Leverans 2<br /> </td> 
   <td> Handikappade<br /> </td> 
   <td> 10<br /> </td> 
   <td> 16:00<br /> </td> 
   <td> 09:00 (nästa dag)<br /> </td> 
   <td> 2:00<br /> </td> 
   <td> Nightly<br /> </td> 
   <td> Skickat<br /> </td> 
   <td> 09:00 (nästa dag)<br /> </td> 
  </tr> 
 </tbody> 
</table>

Efter det att extraktionsdatumet har passerats för de två leveranserna, tillämpas det nattliga skiljeförfarandet på nytt före kontaktdatumen för båda leveranserna. På så sätt kan du hitta alla leveranser som redan har skickats (mottagare för vilka en leverans har bearbetats, registrerats via de breda loggarna) eller som har schemalagts för att skickas (mottagare som är berättigade att ta emot en leverans, som registrerats via prognosloggarna).

När alla skickade och potentiella leveranser har listats för den period som anges i tryckregeln sorterar Adobe Campaign dem efter vikt, med den högsta viktningen först. När det tröskelvärde som anges i tryckregeln nås (om det inte finns fler än två e-postmeddelanden inom samma vecka), utesluts mottagarna från leveransen.
