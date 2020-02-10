---
title: Köra ett arbetsflöde
seo-title: Köra ett arbetsflöde
description: Köra ett arbetsflöde
seo-description: null
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4b4ec97e52a494dd88b2516650ae514294f00934

---


# Köra ett arbetsflöde{#executing-a-workflow}

Felsökningsriktlinjer för arbetsflödeskörning finns i [det här avsnittet](../../production/using/workflow-execution.md).

## Starta ett arbetsflöde {#starting-a-workflow}

Ett arbetsflöde startas alltid manuellt. När den startas kan den dock förbli inaktiv beroende på den information som anges via en schemaläggare (se [Schemaläggaren](../../workflow/using/scheduler.md)) eller aktivitetsplanering.

Åtgärder för att målinrikta arbetsflödeskörning (starta, stoppa, pausa osv.) är **asynkrona** processer: beställningen registreras och träder i kraft så snart servern är tillgänglig för att använda den.

Med verktygsfältet kan du starta och spåra arbetsflödets körning.

Listan med alternativ på **[!UICONTROL Actions]** menyn och högerklicksmenyn finns nedan.

### Verktygsfältet Åtgärder {#actions-toolbar}

Verktygsfältsknapparna beskrivs i det här [avsnittet](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). Knappen **[!UICONTROL Actions]** ger dig tillgång till ytterligare körningsalternativ för att arbeta med valda arbetsflöden. Du kan också använda **[!UICONTROL File > Actions]** menyn eller högerklicka på ett arbetsflöde och välja **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   Med den här åtgärden kan du starta körningen av ett arbetsflöde: ett arbetsflöde som är **Färdigt**, **Redigeras** eller **Pausas** ändrar status till **Startat**. Arbetsflödesmotorn hanterar sedan körningen av det här arbetsflödet. Om arbetsflödet pausades återupptas det, annars startas arbetsflödet från början och de inledande aktiviteterna aktiveras.

   Starten är en asynkron process: Begäran sparas och behandlas så snart som möjligt av en arbetsflödesserver.

* **[!UICONTROL Pause]**

   Den här åtgärden anger arbetsflödets status till **Pausad**. Inga aktiviteter aktiveras förrän arbetsflödet återupptas. pågående åtgärder är dock inte pausade.

* **[!UICONTROL Stop]**

   Den här åtgärden stoppar ett arbetsflöde som körs. Status för instansen är inställd på **Slutförd**. Pågående åtgärder stoppas om det är möjligt. Import och SQL-frågor avbryts omedelbart.

   Stoppning är en asynkron process. Begäran registreras och arbetsflödesservern eller servrarna avbryter pågående åtgärder. Det kan därför ta tid att stoppa en arbetsflödesinstans, särskilt om arbetsflödet körs på flera servrar, där var och en måste ta kontroll för att avbryta de pågående åtgärderna.

* **[!UICONTROL Restart]**

   Den här åtgärden avbryter och startar sedan om arbetsflödet. I de flesta fall går det att starta om snabbare. Det är också användbart att automatisera omstarten när stoppet tar en viss tid: Detta beror på att &quot;Stoppa&quot;-kommandot inte är tillgängligt när arbetsflödet stoppas.

   Åtgärderna är också tillgängliga via körningsikonerna i verktygsfältet. **[!UICONTROL Start / Pause / Stop / Restart]** Mer information finns i det här [avsnittet](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **[!UICONTROL Purge history]**

   Med den här åtgärden kan du rensa arbetsflödeshistoriken. Mer information finns i [Rensa loggarna](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

   Med det här alternativet kan du starta arbetsflödet i simuleringsläge i stället för i realläge. Det innebär att när du aktiverar det här läget utförs endast aktiviteter som inte påverkar databasen eller filsystemet (t.ex. **[!UICONTROL Query]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]** osv.). Verksamhet som har en effekt (t.ex. **[!UICONTROL Export]**, **[!UICONTROL Import]** osv.) samt de som kommer efter dem (i samma gren) inte utförs.

* **[!UICONTROL Execute pending tasks now]**

   Med den här åtgärden kan du starta alla väntande uppgifter så snart som möjligt. Om du vill starta en viss uppgift högerklickar du på aktiviteten och väljer **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Unconditional stop]**

   Det här alternativet ändrar arbetsflödets status till **[!UICONTROL Finished]**. Denna åtgärd bör endast användas som en sista utväg om den normala stoppprocessen misslyckas efter flera minuter. Använd bara det ovillkorliga stoppet om du är säker på att inga verkliga arbetsflödesjobb pågår.

   >[!CAUTION]
   >
   >Det här alternativet är reserverat för expertanvändare.

* **[!UICONTROL Save as template]**

   Den här åtgärden skapar en ny arbetsflödesmall baserad på det valda arbetsflödet. Du måste ange mappen där den ska sparas (i **[!UICONTROL Folder]** fältet).

   Alternativen **[!UICONTROL Mass update of selected lines]** och **[!UICONTROL Merge selected lines]** är allmänna plattformsalternativ som är tillgängliga på alla **[!UICONTROL Actions]** menyer. Mer information finns i det här [avsnittet](../../platform/using/updating-data.md).

### Högerklicka på menyn {#right-click-menu}

När du har valt en eller flera arbetsflödesaktiviteter kan du högerklicka för att agera på ditt val.

![](assets/contextual_menu.png)

Följande alternativ är tillgängliga på högerklicksmenyn:

**[!UICONTROL Open]**: Med det här alternativet kan du komma åt aktivitetsegenskaperna.

**[!UICONTROL Display logs:]** Med det här alternativet kan du visa loggen för uppgiftskörning för den valda aktiviteten. Se [Visa loggar](../../workflow/using/monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** Med den här åtgärden kan du starta väntande uppgifter så snart som möjligt.

**[!UICONTROL Workflow restart from a task:]** Med det här alternativet kan du starta om arbetsflödet med de resultat som tidigare lagrats för den här aktiviteten.

**[!UICONTROL Cut/Copy/Paste/Delete:]** Med dessa alternativ kan du klippa ut, kopiera, klistra in och ta bort aktiviteter.

**[!UICONTROL Copy as bitmap:]** Med det här alternativet kan du ta en skärmbild av alla aktiviteter.

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** Dessa alternativ är också tillgängliga på fliken **[!UICONTROL Advanced]** för aktivitetsegenskaperna. De beskrivs i [Körning](../../workflow/using/advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** Med kan du spara eller avbryta ändringar som gjorts i ett arbetsflöde.

>[!NOTE]
>
>Du kan markera en grupp aktiviteter och använda något av dessa kommandon på dem.

Menyn för högerklickning finns också i det här [avsnittet](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).

## Arbetsflödets livscykel {#workflow-life-cycle}

Arbetsflödescykeln består av tre huvudsteg.

* **Redigeras**

   Detta är den inledande designfasen: När ett nytt arbetsflöde skapas är dess status&quot;Redigeras&quot;. Arbetsflödet hanteras ännu inte av servern och kan ändras utan risk.

* **Startat**

   När den inledande designfasen är klar kan arbetsflödet startas. I den här fasen hanteras instansen av servern och de enskilda åtgärderna körs. Arbetsflödet kan fortfarande ändras med vissa försiktighetsåtgärder.

* **Slutförd**

   Ett arbetsflöde är&quot;Slutfört&quot; när det inte längre finns några pågående uppgifter eller när en operator uttryckligen har stoppat instansen.

Aktiviteterna **Start** och **Leverans** beskrivs till exempel medan aktiviteten **Godkännande** blinkar i arbetsflödet nedan.

![](assets/new-workflow-6.png)

Detta innebär att de två första aktiviteterna har slutförts och att godkännande pågår, dvs. det har skapats men ännu inte slutförts.

Tecknen **574 -OK** som visas ovanför övergången efter **leveransaktiviteten** innebär att leveransförberedelsen har 574 mottagare som mål och att åtgärden har slutförts. Den här informationen, som läggs till i övergångarna när de körs, beräknas av aktiviteterna som bearbetar data.

Arbetsflödet startas och väntar på att en operator som tillhör gruppen som anges i **godkännandeaktiviteten** ska fatta ett beslut. Operatörer som tillhör gruppen och som har en e-postadress eller ett mobiltelefonnummer meddelas.

Operatorhantering beskrivs i det här [avsnittet](../../platform/using/access-management.md).

Mer information om hur du övervakar arbetsflöden finns i [det här avsnittet](../../workflow/using/monitoring-workflow-execution.md).

## Datalivscykel {#data-life-cycle}

### Arbetsregister {#work-table}

I arbetsflöden lagras data som transporteras från en aktivitet till en annan i en temporär arbetstabell.

Dessa data kan visas och analyseras genom att högerklicka på lämplig övergång.

![](assets/wf-right-click-analyze.png)

Välj den relevanta menyn för att göra detta:

* Visa målet

   På den här menyn visas tillgängliga data om målpopulationen samt arbetstabellens struktur (**[!UICONTROL Schema]** flik).

   ![](assets/wf-right-click-display.png)

   Mer information finns i [Arbetstabeller och arbetsflödesschema](../../workflow/using/monitoring-workflow-execution.md#worktables-and-workflow-schema).

* Analysera målet

   På den här menyn kan du komma åt guiden för beskrivande analys där du kan ta fram statistik och rapporter om övergångsdata.

   Mer information finns i det här [avsnittet](../../reporting/using/using-the-descriptive-analysis-wizard.md).

Måldata rensas när arbetsflödet körs. Endast den sista arbetstabellen är tillgänglig. Du kan konfigurera arbetsflödet så att alla arbetsregister förblir tillgängliga: markera alternativet i arbetsflödesegenskaperna. **[!UICONTROL Keep the result of interim populations between two executions]**

Vi rekommenderar dock att du undviker att aktivera det här alternativet om det finns stora mängder data.

![](assets/wf-purge-data-option.png)

### Måldata {#target-data}

De data som lagras i arbetsflödets arbetstabell är tillgängliga i personaliseringsfälten.

På så sätt kan du använda data som samlats in via en lista eller baserat på svar på en enkät i en leverans. Använd följande syntax:

```
%= targetData.FIELD %
```

**[!UICONTROL Target extension]** (targetData)-typografiska element är inte tillgängliga för riktade arbetsflöden. Leveransmålet måste byggas in i arbetsflödet och anges i leveransens ingående övergång.

Om du vill skapa leveranskorrektur måste korrekturmålet byggas baserat på **[!UICONTROL Address substitution]** läget så att personaliseringsdata kan anges. Mer information finns i det här [avsnittet](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof).

I följande exempel ska vi samla in en lista med information om kunderna som ska användas i ett personaliserat e-postmeddelande.

Använd följande steg:

1. Skapa ett arbetsflöde för att samla in information, stämma av den med data som redan finns i databasen och starta sedan en leverans.

   ![](assets/wf-targetdata-sample-1.png)

   I vårt exempel är filinnehållet följande:

   ```
   Music,First name,Last name,Account,CD/DVD,Card
   Pop,David,BLAIR,4323,CD,0
   Rock,Daniel,ARCARI,3222,DVD,1
   Disco,Uma,ALTON,0488,DVD,0
   Jazz,Paul,BOLES,6475,CD,1
   Jazz,David,BOUKHARI,0841,DVD,1
   [...]
   ```

   Så här läser du in filen:

   ![](assets/wf-targetdata-sample-2.png)

1. Konfigurera **[!UICONTROL Enrichment]** typaktiviteten för att stämma av insamlade data med data som redan finns i Adobe Campaign-databasen.

   Här är avstämningsnyckeln kontonumret:

   ![](assets/wf-targetdata-sample-3.png)

1. Konfigurera sedan **[!UICONTROL Delivery]**: skapas baserat på en mall och mottagarna anges av den inkommande övergången.

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >Endast data i övergången får användas för att anpassa leveransen. **anpassningsfält av typen targetData** är bara tillgängliga för den inkommande populationen av **[!UICONTROL Delivery]** aktiviteten.

1. Använd de fält som samlats in i arbetsflödet i leveransmallen.

   Det gör du genom att infoga **[!UICONTROL Target extension]** typanpassningsfält.

   ![](assets/wf-targetdata-sample-5.png)

   Här vill vi infoga kundens favoritmusikgenre och medietyp (CD eller DVD) enligt den fil som samlas in i arbetsflödet.

   Dessutom kommer vi att lägga till en kupong för förmånskortinnehavare, dvs. mottagare för vilka &#39;kortet&#39; är lika med 1.

   ![](assets/wf-targetdata-sample-6.png)

   **[!UICONTROL Target extension]** Data av typen targetData infogas i leveranser med samma egenskaper som alla personaliseringsfält. De kan också användas i ämnet, länketiketterna eller själva länkarna.

   Meddelanden adresserade till insamlade mottagare kommer att innehålla följande data:

   ![](assets/wf-targetdata-sample-7.png)

## Definiera godkännanden {#defining-approvals}

Godkännanden gör det möjligt för operatorer att fatta beslut som styr ett arbetsflöde eller att bekräfta att det fortsätter att köras.

Ett meddelande skickas till en grupp operatorer och arbetsflödet väntar på ett svar innan det återupptas. Arbetsflödet har inte stoppats och andra åtgärder kan utföras. Det kan till exempel finnas flera väntande samtidiga godkännanden.

Ett godkännande kan innehålla flera alternativ som operatorn kan välja. Det är dock möjligt att begränsa antalet val till ett för att skicka en uppgift som ska utföras till en operator, till exempel utföra målinriktning. Operatorn kan sedan svara när uppgiften har utförts (processen återupptas sedan). I följande exempel visas dessa typer av godkännanden:

![](assets/validation-1.png)

I operationer baseras alla faser som kräver godkännande på samma princip.

![](assets/validation-1-in-op.png)

Exempel på godkännanden finns i det här [avsnittet](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

En operator kan svara på ett av två sätt: validera med webbsidan som är länkad i e-postmeddelandet eller via konsolen.

>[!NOTE]
>
>När svaret har sparats kan det inte ändras.

### Skicka e-post {#sending-emails}

Det går att få ett meddelande om godkännande som innehåller en länk till en webbsida där det går att svara. Om måloperatorn ska få ett e-postmeddelande om godkännande måste operatörens e-postadress vara fullständig. Om så inte är fallet måste operatören använda konsolen för att svara

Operatorhantering beskrivs i det här [avsnittet](../../platform/using/access-management.md).

E-postmeddelanden om godkännande skickas kontinuerligt. Standardleveransmallen är **[!UICONTROL notifyAssignee]**: Den sparas i **[!UICONTROL Administration > Campaign management > Technical delivery templates]** mappen. Scenariot kan anpassas och vi rekommenderar att du skapar en kopia och ändrar mallar för varje aktivitet.

Leveranser som skapas med den här mallen lagras i **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** mappen.

### Godkännande via konsolen {#approval-via-the-console}

I åtgärder visas element som ska godkännas på kontrollpanelen för kampanjer.

För tekniska arbetsflöden kan de uppgifter som användaren kan godkänna nås från trädstrukturen i **[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]** mappen.

![](assets/validation-node.png)

### Grupper {#groups}

Ett godkännande tilldelas en grupp operatorer, en enstaka operator eller en uppsättning operatorer som väljs via ett filtreringsvillkor.

1. För den enklaste formen av godkännande slutförs uppgiften så snart en operator svarar. Alla andra operatorer som försöker svara får ett meddelande om att någon redan har gjort det.
1. För flera godkännanden, se [Flera godkännanden](#multiple-approval).

Operatörsgrupperna för godkännanden bör utses som roller eller funktioner i stället för namngivna personer. En&quot;Kampanjbudgetgrupp&quot; är till exempel att föredra framför&quot;Harry&#39;s Group&quot;. Vi rekommenderar att du har minst två personer i en grupp som kan godkänna en uppgift. På så sätt kan den andre svara om någon inte är närvarande.

### Förfallodatum {#expirations}

Förfallodatum är specifika övergångar som används i olika typer av aktiviteter, och särskilt vid godkännanden. En förfallotid kan användas för att utlösa en åtgärd efter en viss tidsrymd i avsaknad av ett svar eller för att fortsätta arbetsflödet (och tilldela ett godkännande till en annan grupp, till exempel).

På den andra fliken i egenskaperna för aktivitetsgodkännande kan du definiera en eller flera förfallotider. Du kan definiera flera olika förfallotyper.

![](assets/expiration.png)

Om du vill lägga till en ny förfallotid klickar du på **[!UICONTROL Add]**. En övergång läggs till för varje förfallodatum som skapas. Du kan:

* ändra de typiska parametrarna direkt genom att klicka på en cell i listan (eller genom att trycka på F2),
* eller redigera uttrycket genom att klicka på **[!UICONTROL Detail...]** knappen.

>[!NOTE]
>
>Det är inte nödvändigt att ange en ordning för förfallodatumen eftersom de bearbetas i kronologisk ordning.

Alternativet **[!UICONTROL Do not terminate the task]** låter godkännandet vara aktivt när fördröjningen överskrids. I det här läget kan du hantera påminnelser medan du låter godkännandet vara aktivt: -operatorer kan fortfarande svara. Det här alternativet är inaktiverat som standard, vilket innebär att uppgiften anses vara slutförd när den upphör att gälla och att operatorerna kanske inte längre svarar.

Du kan skapa fyra typer av förfallodatum:

* **Fördröjning efter att aktiviteten har startats**: Utgångsdatumet beräknas genom att en angiven tidsperiod läggs till det datum då godkännandet aktiveras.
* **Fördröjning efter ett visst datum**: Förfallotiden beräknas genom att lägga till en tidslängd till ett datum som du anger.
* **Fördröjning före ett visst datum**: Förfallodatumet beräknas genom att en tidslängd subtraheras från ett datum som du anger.
* **Förfallotid beräknat av skript**: Förfallotiden beräknas med JavaScript.

   I följande exempel beräknas en förfallotid 24 timmar innan det datum då en leverans påbörjas (identifieras av **vars.deliveryId**):

   ```
   var delivery = nms.delivery.get(vars.deliveryId)
   var expiration = delivery.scheduling.contactDate
   var oneDay = 1000*60*60*24
   expiration.setTime(expiration.getTime() - oneDay)
   return expiration
   ```

### Flera godkännanden {#multiple-approval}

Flera godkännanden är en mekanism som gör det möjligt för alla godkännandeoperatörer att svara. En övergång aktiveras för varje svar.

Flera godkännanden är användbara för röstnings- eller undersökningsmetoder. Du kan räkna svar och bearbeta resultatet efter en viss period genom att lägga till en deadline.

### Nödvändiga rättigheter {#required-rights}

Operatörerna i en grupp måste minst ha följande rättigheter för att kunna besvara en begäran om godkännande:

* Skriva behörigheter för arbetsflöde.
* Läsa- och skrivbehörigheter för mappen som innehåller de uppgifter som ska godkännas.

Gruppen Workflow execution har dessa rättigheter. En operator som lagts till i den här gruppen har behörighet att svara på en godkännandebegäran.

## Arkitektur {#architecture}

Arbetsflöden hanteras av en specifik modul. Den här modulen kan startas på flera servrar för att dela bearbetningsbelastningen.

![](assets/architecture.png)

* Processen &#39;Workflow Instance Runner&#39; (runwf) kör alla åtgärder i en viss arbetsflödesinstans. När det inte finns några uppgifter att utföra just nu blir den&quot;passiv&quot;, det vill säga sparar dess status i databasen och sedan stoppas.
* Modulen Arbetsflödesserver (wfserver) övervakar aktuella arbetsflödesinstanser. När det finns en uppgift att utföra skapar den här modulen en process för att aktivera (eller återaktivera) motsvarande instans.

När en operator utför en åtgärd i ett arbetsflöde (start, stopp, paus osv.), utförs åtgärden inte direkt av modulen nlserver, utan placeras i en kö för att bearbetas av arbetsflödesmodulen.
