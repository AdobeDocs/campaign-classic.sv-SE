---
solution: Campaign Classic
product: campaign
title: Leveranser av marknadsföringskampanjer
description: Läs mer om kampanjleveranser
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 1cde12d33551206da12e03a7e8deb198d427ab3a
workflow-type: tm+mt
source-wordcount: '2926'
ht-degree: 1%

---


# Leveranser av marknadsföringskampanjer {#marketing-campaign-deliveries}

Leveranser kan skapas via kampanjkontrollpanelen, ett kampanjarbetsflöde eller direkt via leveransöversikten.

När leveranser skapas från en kampanj länkas de till den här kampanjen och konsolideras på kampanjnivå.

![](assets/do-not-localize/how-to-video.png)[ Upptäck den här funktionen i en video](#create-email-video)

## Skapa leveranser {#creating-deliveries}

Om du vill skapa en leverans som är länkad till en kampanj klickar du på länken **[!UICONTROL Add a delivery]** på kontrollpanelen för kampanjer.

![](assets/campaign_op_add_delivery.png)

De föreslagna konfigurationerna passar för olika typer av leveranser: direktreklam, e-post, mobila kanaler. [Läs mer](../../delivery/using/steps-about-delivery-creation-steps.md).

## Välja målpopulationen {#selecting-the-target-population}

För varje leverans kan du definiera:

* Målgruppen - Läs mer i [Skapa målgruppen i ett arbetsflöde](#building-the-main-target-in-a-workflow) och [Välja målpopulationen](#selecting-the-target-population).
* En kontrollgrupp - Läs mer i [Definiera en kontrollgrupp](#defining-a-control-group).
* dirigerade adresser - Läs mer i [det här avsnittet](../../delivery/using/about-seed-addresses.md).

En del av den här informationen kan ärvas från [mallen](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

Om du vill skapa leveransmålet kan du definiera filtervillkor för mottagarna i databasen. Det här mottagarvalsläget visas i [det här avsnittet](../../delivery/using/steps-defining-the-target-population.md).

**Exempel: skicka meddelanden till en grupp**

Du kan importera en population till en lista och sedan ange den här listan som mål i leveranser.

1. Om du vill göra det redigerar du den aktuella leveransen och klickar på länken **[!UICONTROL To]** för att ändra målpopulationen.

1. Välj alternativet **[!UICONTROL Defined via the database]** på fliken **[!UICONTROL Main target]** och klicka på **[!UICONTROL Add]** för att välja mottagare.

![](assets/s_user_target_group_add.png)

1. Välj **[!UICONTROL A list of recipients]** och klicka på **[!UICONTROL Next]** för att markera den.

![](assets/s_user_target_group_next.png)

### Skapa målgruppen i ett arbetsflöde {#building-the-main-target-in-a-workflow}

Huvudmålet för en leverans kan också definieras i målarbetsflödet: I den grafiska miljön kan du skapa mål med hjälp av frågor, tester och operatorer: union, borttagning av dubbletter, delning osv. [Läs mer](../../workflow/using/architecture.md).

>[!IMPORTANT]
>
>Du kan inte skapa fler än 28 arbetsflöden i en kampanj. Tidigare är ytterligare arbetsflöden inte synliga i gränssnittet och kan generera fel.

#### Skapa arbetsflödet {#creating-a-targeting-workflow}

Målinriktning kan skapas med en kombination av filtreringsvillkor i en grafisk sekvens i ett arbetsflöde. Ni kan skapa populationer och underpopulationer som ska anpassas efter era behov. Om du vill visa arbetsflödesredigeraren klickar du på fliken **[!UICONTROL Targeting and workflows]** på kontrollpanelen för kampanjer.

![](assets/s_ncs_user_edit_op_wf_link.png)

Målpopulationen extraheras från Adobe Campaign-databasen via en eller flera frågor i ett arbetsflöde. Mer information om hur du skapar en fråga finns i [det här avsnittet](../../workflow/using/query.md).

Du kan starta frågor och dela populationer via rutor som Union, Intersection, Sharing, Exclusion osv.

Markera objekten i listorna till vänster om arbetsytan och länka dem för att skapa målet.

![](assets/s_ncs_user_edit_op_wf_tab_a.png)

I diagrammet länkar du upp de mål- och planeringsfrågor som krävs för målkonstruktion i diagrammet. Du kan utföra målinriktningen medan konstruktionen pågår för att kontrollera populationen som extraherats från databasen.

>[!NOTE]
>
>Exempel och procedur för att definiera frågor finns i [det här avsnittet](../../workflow/using/query.md).

I den vänstra delen av redigeraren finns ett bibliotek med grafiska objekt som representerar aktiviteter. Den första fliken innehåller målinriktningsaktiviteterna och den andra fliken innehåller flödeskontrollaktiviteterna, som används ibland för att samordna målinriktningsaktiviteter.

Körnings- och formateringsfunktionerna för målarbetsflödet är tillgängliga via verktygsfältet för diagramredigering.

![](assets/s_user_campaign_segmentation05.png)

>[!NOTE]
>
>Vilka aktiviteter som är tillgängliga för att skapa diagrammet och alla visnings- och layoutfunktioner finns i guiden [Automatisera med arbetsflöden](../../workflow/using/architecture.md).

Ni kan skapa flera arbetsflöden för målinriktning för en enskild kampanj. Så här lägger du till ett arbetsflöde:

1. Gå till den övre vänstra delen av arbetsflödets område, högerklicka och välj **[!UICONTROL Add]**. Du kan också använda knappen **[!UICONTROL New]** ovanför den här zonen.

   ![](assets/s_ncs_user_add_a_wf.png)

1. Välj mallen **[!UICONTROL New workflow]** och ge arbetsflödet ett namn.
1. Klicka på **[!UICONTROL OK]** för att bekräfta att arbetsflödet har skapats och skapa sedan diagrammet för arbetsflödet.

#### Kör arbetsflödet {#executing-a-workflow}

Målarbetsflöden kan startas manuellt med knappen **[!UICONTROL Start]** i verktygsfältet, förutsatt att du har rätt behörighet.

Målinriktningen kan programmeras för automatisk körning enligt ett schema (schemaläggare) eller en händelse (extern signal, filimport osv.).

Åtgärder som rör körning av målarbetsflödet (starta, stoppa, pausa, osv.) är **asynkrona** processer: kommandot sparas och börjar gälla så fort servern är tillgänglig för att använda det.

Med verktygsfältsikonerna kan du utföra åtgärder för arbetsflödet.

* Starta eller starta om

   * Med ikonen **[!UICONTROL Start]** kan du starta målarbetsflödet. När du klickar på den här ikonen aktiveras alla aktiviteter utan en indataövergång (förutom slutpunktshopp).

      ![](assets/s_user_segmentation_start.png)

      Servern tar hänsyn till begäran, vilket framgår av dess status:

      ![](assets/s_user_segmentation_start_status.png)

      Processens status ändras till **[!UICONTROL Started]**.

   * Du kan starta om arbetsflödet för målanpassning via motsvarande verktygsfältsikon. Det här kommandot kan vara användbart om ikonen **[!UICONTROL Start]** inte är tillgänglig, t.ex. när stoppning av målarbetsflöde pågår. I det här fallet klickar du på ikonen **[!UICONTROL Restart]** för att förutse omstarten. Servern tar hänsyn till begäran, vilket framgår av dess status:

      ![](assets/s_user_segmentation_restart_status.png)

      Processen anger sedan **[!UICONTROL Started]**-status.

* Stoppa eller pausa

   * Med verktygsfältsikonerna kan du stoppa eller pausa ett pågående målarbetsflöde.

      När du klickar på **[!UICONTROL Pause]** har åtgärder som pågår **[!UICONTROL are not]** pausats, men ingen annan aktivitet startas förrän nästa omstart.

      ![](assets/s_user_segmentation_pause.png)

      Servern tar hänsyn till kommandot, vilket visas i dess status:

      ![](assets/s_user_segmentation_pause_status.png)

      Du kan också pausa ett arbetsflöde för målinriktning automatiskt när körningen når en viss aktivitet. Om du vill göra det högerklickar du på aktiviteten som målarbetsflödet ska pausas från och väljer **[!UICONTROL Enable but do not execute]**.

      ![](assets/s_user_segmentation_donotexecute.png)

      Den här konfigurationen visas med en särskild ikon.

      ![](assets/s_user_segmentation_pause_activity.png)

      >[!NOTE]
      >
      >Det här alternativet är användbart under design- och testfaser av avancerade riktade kampanjer.

      Klicka på **[!UICONTROL Start]** för att återuppta körningen.

   * Klicka på ikonen **[!UICONTROL Stop]** för att stoppa den pågående körningen.

      ![](assets/s_user_segmentation_stop.png)

      Servern tar hänsyn till kommandot, vilket visas i dess status:

      ![](assets/s_user_segmentation_stop_status.png)
   Du kan också stoppa ett målarbetsflöde automatiskt när körningen når en aktivitet. Om du vill göra det högerklickar du på aktiviteten som målarbetsflödet ska stoppas från och väljer **[!UICONTROL Do not activate]**.

   ![](assets/s_user_segmentation_donotactivate.png)

   ![](assets/s_user_segmentation_unactivation.png)

   Den här konfigurationen visas med en särskild ikon.

   >[!NOTE]
   >
   >Det här alternativet är användbart under design- och testfaser av avancerade riktade kampanjer.

* Ovillkorligt stopp

   I Utforskaren väljer du **[!UICONTROL Administration > Production > Object created automatically > Campaign workflows]** för att få åtkomst till och agera på alla kampanjarbetsflöden.

   Du kan avbryta ditt arbetsflöde genom att klicka på ikonen **[!UICONTROL Actions]** och välja **[!UICONTROL Unconditional]** steg. Den här åtgärden avbryter kampanjarbetsflödet.

   ![](assets/s_user_segmentation_stop_unconditional.png)

### Definiera en kontrollgrupp {#defining-a-control-group}

En kontrollgrupp är en population som inte kommer att få leveransen. Det används för att spåra beteenden och kampanjeffekter efter leverans genom att göra en jämförelse med beteendet hos målpopulationen, som har fått leveransen.

Kontrollgruppen kan extraheras från huvudmålet och/eller komma från en viss grupp eller fråga.

#### Aktivera kontrollgruppen för en kampanj {#activating-the-control-group-for-a-campaign}

Du kan definiera en kontrollgrupp på kampanjnivå, och i så fall tillämpas kontrollgruppen på varje leverans av den aktuella kampanjen.

1. Redigera den aktuella kampanjen och klicka på fliken **[!UICONTROL Edit]**.
1. Klicka på **[!UICONTROL Advanced campaign settings]**.

   ![](assets/s_ncs_user_edit_op_target.png)

1. Välj alternativet **[!UICONTROL Enable and edit control group configuration]**.
1. Klicka på **[!UICONTROL Edit...]** för att konfigurera kontrollgruppen.

   ![](assets/s_ncs_user_edit_op_general_tab_exe_target.png)

Konfigurationsproceduren presenteras i [Extrahera kontrollgruppen från huvudmålet](#extracting-the-control-group-from-the-main-target) och [Lägga till en kontrollgrupp](#adding-a-population).

#### Aktivera kontrollgruppen för en leverans {#activating-the-control-group-for-a-delivery}

Du kan definiera en kontrollgrupp på leveransnivå. I så fall tillämpas kontrollgruppen på varje leverans av den aktuella kampanjen.

Som standard gäller den kontrollgruppskonfiguration som definieras på kampanjnivå för varje leverans av kampanjen. Du kan dock anpassa kontrollgruppen för en enskild leverans.

>[!NOTE]
>
>Om du har definierat en kontrollgrupp för en kampanj, och du även konfigurerar den för en leverans som är länkad till den här kampanjen, tillämpas bara den kontrollgrupp som har definierats för leveransen.

1. Redigera den aktuella leveransen och klicka sedan på länken **[!UICONTROL To]** i avsnittet **[!UICONTROL Email parameters]**.

   ![](assets/s_ncs_user_edit_op_target_del.png)

1. Klicka på fliken **[!UICONTROL Control group]** och välj sedan **[!UICONTROL Enable and edit control group configuration]**.
1. Klicka på **[!UICONTROL Edit...]** för att konfigurera kontrollgruppen.

Konfigurationsproceduren presenteras i [Extrahera kontrollgruppen från huvudmålet](#extracting-the-control-group-from-the-main-target) och [Lägga till en kontrollgrupp](#adding-a-population).

#### Extraherar kontrollgruppen från huvudmålet {#extracting-the-control-group-from-the-main-target}

Du kan extrahera mottagare från huvudmålet för leveransen. I det här fallet hämtas mottagarna från målet för leveransåtgärder som påverkas av den här konfigurationen. Extraheringen kan vara slumpmässig eller bero på att mottagarna har sorterats.

![](assets/s_ncs_user_extract_from_target_population.png)

Om du vill extrahera en kontrollgrupp aktiverar du kontrollgruppen för kampanjen eller leveransen och väljer något av följande alternativ: **[!UICONTROL Activate random sampling]** eller **[!UICONTROL Keep only the first records after sorting]**.

* **[!UICONTROL Activate random sampling]** : Med det här alternativet tillämpas slumpmässiga stickprov på mottagarna i målpopulationen. Om du sedan anger tröskelvärdet till 100 kommer kontrollgruppen att bestå av 100 mottagare som väljs slumpmässigt från målpopulationen. Det slumpmässiga urvalet beror på databasmotorn.
* **[!UICONTROL Keep only the first records after sorting]** : med det här alternativet kan du definiera en begränsning baserat på en eller flera sorteringsvillkor. Om du väljer fältet **[!UICONTROL Age]** som sorteringsvillkor och sedan definierar 100 som ett tröskelvärde, kommer kontrollgruppen att bestå av de 100 yngsta mottagarna. Det kan till exempel vara intressant att definiera en kontrollgrupp som innehåller mottagare som gör få inköp, eller mottagare som gör vanliga inköp, och att jämföra deras beteende med de kontaktade mottagarna.

Klicka på **[!UICONTROL Next]** för att definiera sorteringsordningen (om det behövs) och välj mottagarbegränsningsläget.

![](assets/s_ncs_user_edit_op_target_param.png)

Den här konfigurationen motsvarar en delningsaktivitet i arbetsflödet, vilket gör att du kan dela upp målet i delmängder. Kontrollgruppen är en av dessa deluppsättningar. Mer information finns i [det här avsnittet](../../workflow/using/architecture.md).

### Lägga till en kontrollgrupp {#adding-a-population}

Du kan definiera en ny population som ska användas som kontrollgrupp. Den här populationen kan komma från en grupp mottagare eller så kan du skapa den via en specifik fråga.

![](assets/s_ncs_user_add_to_target_population.png)

>[!NOTE]
>
>Adobe Campaign frågeredigerare presenteras i [det här avsnittet](../../workflow/using/query.md).

## Startar en leverans {#starting-a-delivery}

När alla godkännanden har beviljats är leveransen klar att startas. Leveransproceduren beror sedan på typen av leverans. Information om leveranser via e-post eller mobilkanal finns i [Starta en onlineleverans](#starting-an-online-delivery) och för leveranser via direktreklam finns i [Starta en offlineleverans](#starting-an-offline-delivery).

### Startar en onlineleverans {#starting-an-online-delivery}

När alla godkännandebegäranden har beviljats ändras leveransstatusen till **[!UICONTROL Pending confirmation]** och kan startas av en operator. I tillämpliga fall meddelas den Adobe Campaign-operatör (eller grupp av operatörer) som utsetts till granskare för att påbörja leveransen att en leverans är klar att påbörjas.

>[!NOTE]
>
>Om en viss operator eller grupp av operatorer har utsetts för att starta en leverans i leveransegenskaperna, kan du även tillåta den operator som ansvarar för leveransen att bekräfta sändningen. Aktivera alternativet **NMS_ActivateOwnerConfirmation** genom att ange **1** som värde. Alternativen hanteras från noden **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** i Adobe Campaign Utforskaren.
>  
>Om du vill inaktivera det här alternativet anger du **0** som värde. Bekräftelseprocessen som skickas fungerar sedan som standard: Endast den operator eller grupp av operatorer som är avsedda för sändning i leveransegenskaperna (eller en administratör) kan bekräfta och utföra sändningen.

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

Informationen visas också på kampanjkontrollpanelen. Med länken **[!UICONTROL Confirm delivery]** kan du påbörja leveransen.

![](assets/s_ncs_user_edit_del_to_start.png)

Med ett bekräftelsemeddelande kan du skydda den här åtgärden.

### Starta en offlineleverans {#starting-an-offline-delivery}

När alla godkännanden har beviljats ändras leveransstatusen till **[!UICONTROL Pending extraction]**. Extraheringsfilerna skapas med ett särskilt arbetsflöde som, i en standardkonfiguration, startar automatiskt när en direktleverans väntar på extrahering. När en process pågår visas den på kontrollpanelen och kan redigeras via länken.

>[!NOTE]
>
>De tekniska arbetsflödena för Campaign-paketet presenteras i [Lista över tekniska arbetsflöden](../../workflow/using/about-technical-workflows.md).

**Steg 1 - Godkännande av fil**

När extraheringsarbetsflödet har körts måste extraheringsfilen godkännas (förutsatt att godkännande av extraheringsfilen har valts i leveransinställningarna).

Mer information finns i [Godkänna en extraheringsfil](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file).

**Steg 2 - Godkännande av meddelandet till tjänsteleverantören**

* När extraheringsfilen har godkänts kan du generera ett bevis för routermeddelandet via e-post. Det här e-postmeddelandet är konstruerat utifrån en leveransmall. Det måste godkännas.

   >[!NOTE]
   >
   >Det här steget är bara tillgängligt om du har aktiverat sändning och godkännande av korrektur i godkännandefönstret.

![](assets/s_ncs_user_file_valid_select_BAT.png)


* Klicka på knappen **[!UICONTROL Send a proof]** för att skapa korrektur.

   Korrekturmålet måste definieras i förväg.

   Du kan skapa så många korrektur som behövs. Dessa nås via länken **[!UICONTROL Direct mail...]** för leveransinformationen.

   ![](assets/s_ncs_user_file_notif_submit_proof.png)

* Leveransstatusen ändras till **[!UICONTROL To submit]**. Klicka på knappen **[!UICONTROL Submit proofs]** för att starta godkännandeprocessen.

   ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* Leveransstatusen ändras till **[!UICONTROL Proof to validate]** och med en knapp kan du godkänna eller avvisa godkännande.

   ![](assets/s_ncs_user_file_notif_supplier_link.png)

   Du kan antingen godkänna eller avvisa det här godkännandet eller återgå till extraheringssteget.

   ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* Extraheringsfilen skickas till routern och leveransen är klar.

### Beräkning av kostnader och stockar {#calculation-of-costs-and-stocks}

Filextraheringen startar två åtgärder: budgetberäkning och lagerberäkning. Budgetposterna uppdateras.

* På fliken **[!UICONTROL Budget]** kan du hantera budgeten för kampanjen. Summan av kostnadsposterna visas i fältet **[!UICONTROL Calculates cost]** på kampanjens huvudflik och det program som den tillhör. Beloppen återspeglas också i kampanjbudgeten.

   Den verkliga kostnaden kommer så småningom att beräknas utifrån information som tillhandahålls av routern. Endast meddelanden som skickas faktureras.

* Stock definieras i noden **[!UICONTROL Administration > Campaign management > Stocks]** i trädet och kostnadsstrukturer i noden **[!UICONTROL Administration > Campaign management > Service providers]**.

   Lagerrader visas i lagersektionen. Om du vill definiera det ursprungliga lagret öppnar du en aktielinje. Lagret minskas varje gång en leverans sker. Du kan definiera en varningsnivå och meddelanden.

>[!NOTE]
>
>Mer information om kostnadsberäkningar och lagerhantering finns i [Leverantörer, stockar och budgetar](../../campaign/using/providers--stocks-and-budgets.md).

## Hantera associerade dokument {#managing-associated-documents}

Du kan koppla olika dokument till en kampanj: rapport, foto, webbsida, diagram osv. Dessa dokument kan vara i vilket format som helst (Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF osv.). Mer information om hur du länkar dokument med en kampanj finns i [Lägga till dokument](#adding-documents).

>[!IMPORTANT]
>
>Det här läget är reserverat för små dokument.

I en kampanj kan du även hänvisa till andra poster, t.ex. kampanjkuponger, specialerbjudanden för en viss gren eller butik. När dessa element ingår i en disposition kan de kopplas till en direktutskick. Se [Associera och strukturera resurser som är länkade via en leveransdisposition](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>Om du använder MRM kan du även hantera ett bibliotek med marknadsföringsresurser som är tillgängliga för flera deltagare för samarbete. Se [Hantera marknadsföringsresurser](../../campaign/using/managing-marketing-resources.md).

### Lägga till dokument {#adding-documents}

Dokument kan kopplas på kampanjnivå (sammanhangsberoende dokument) eller på programnivå (allmänna dokument).

Fliken **[!UICONTROL Documents]** innehåller:

* Listan över alla dokument som krävs för innehållet (mall, bilder osv.) som kan laddas ned lokalt av Adobe Campaign-operatörer med lämpliga rättigheter,
* Dokument som innehåller information för routern, om sådan finns.

Dokumenten länkas till programmet eller kampanjen via fliken **[!UICONTROL Edit > Documents]**.

![](assets/s_ncs_user_op_add_document.png)

Du kan också lägga till ett dokument i en kampanj via länken på kontrollpanelen.

![](assets/add_a_document_in_op.png)

Klicka på ikonen **[!UICONTROL Details]** för att visa innehållet i en fil och lägga till information:

![](assets/s_ncs_user_op_add_document_details.png)

På kontrollpanelen grupperas dokument som är kopplade till kampanjen i avsnittet **[!UICONTROL Document(s)]**, som i följande exempel:

![](assets/s_ncs_user_op_edit_document.png)

De kan också redigeras och ändras i den här vyn.

### Associera och strukturera resurser som är länkade via en leveransdisposition {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>Leveranskonturer används endast i samband med direktreklamkampanjer.

En leveransöversikt betecknar en strukturerad uppsättning element (dokument, filialer/butiker, kampanjkuponger osv.) som skapats i företaget och för en viss kampanj.

Dessa element är grupperade i leveranskonturer och en särskild leveransdisposition kommer att kopplas till en leverans. den kommer att refereras i extraheringsfilen som skickas till **tjänstleverantören** för att kopplas till leveransen. Du kan till exempel skapa en leveransdisposition som refererar till en gren och de marknadsföringsbroschyrer som används i den.

För en kampanj kan du strukturera externa element som ska kopplas till leveransen enligt vissa kriterier: närliggande filial, kampanjerbjudande, inbjudan till ett lokalt evenemang osv.

#### Skapa en kontur {#creating-an-outline}

Om du vill skapa en disposition klickar du på underfliken **[!UICONTROL Delivery outlines]** på fliken **[!UICONTROL Edit > Documents]** för den aktuella kampanjen.

>[!NOTE]
>
>Om den här fliken inte finns är den här funktionen inte tillgänglig för kampanjen. Se kampanjmallskonfigurationen.
>   
>Mer information finns i [Kampanjmallar](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

Klicka sedan på **[!UICONTROL Add a delivery outline]** och skapa en hierarki med konturer för kampanjen:

1. Högerklicka på trädets rot och välj **[!UICONTROL New > Delivery outlines]**.
1. Högerklicka på konturen som du just har skapat och välj **[!UICONTROL New > Item]** eller **[!UICONTROL New > Personalization fields]**.

![](assets/s_ncs_user_op_add_composition.png)

En disposition kan innehålla objekt och personaliseringsfält, resurser och erbjudanden:

* Objekten kan till exempel vara fysiska dokument som refereras och beskrivs här och bifogas till leveransen.
* Med personaliseringsfält kan du skapa personaliseringselement för leveranser i stället för mottagare. Det är därför möjligt att skapa värden som ska användas i leveranser för ett specifikt mål (välkomsterbjudande, rabatt osv.) De skapas i Adobe Campaign och importeras till dispositionen via länken **[!UICONTROL Import personalization fields...]**.

   ![](assets/s_ncs_user_op_add_composition_field.png)

   De kan också skapas direkt i dispositionen genom att klicka på ikonen **[!UICONTROL Add]** till höger om listzonen.

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* Resurserna är marknadsföringsresurser som genereras i kontrollpanelen för marknadsföringsresurser som nås via länken **[!UICONTROL Resources]** i **[!UICONTROL Campaigns]**-universum.

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >Mer information om marknadsföringsresurser finns i [Hantera marknadsföringsresurser](../../campaign/using/managing-marketing-resources.md).

#### Markera en kontur {#selecting-an-outline}

För varje leverans kan du välja den disposition som ska kopplas från det avsnitt som är reserverat för dispositionen, som i följande exempel:

![](assets/s_ncs_user_op_select_composition.png)

Den markerade dispositionen visas sedan i fönstrets nedre del. Den kan redigeras med ikonen till höger om fältet eller ändras med hjälp av listrutan:

![](assets/s_ncs_user_op_select_composition_b.png)

På fliken **[!UICONTROL Summary]** för leveransen visas även den här informationen:

![](assets/s_ncs_user_op_select_composition_c.png)

#### Extraheringsresultat {#extraction-result}

I den fil som extraheras och skickas till tjänsteleverantören, namnet på konturen och, i förekommande fall, dess egenskaper (kostnad, beskrivning osv.) läggs till i innehållet enligt informationen i exportmallen som är kopplad till tjänsteleverantören.

I följande exempel läggs etiketten, den uppskattade kostnaden och beskrivningen av dispositionen som är kopplad till leveransen till i extraheringsfilen.

![](assets/s_ncs_user_op_composition_in_export_template.png)

Exportmodellen måste vara kopplad till den tjänsteleverantör som valts för den aktuella leveransen. Se [Skapa tjänsteleverantörer och deras kostnadsstrukturer](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>Mer information om export finns i avsnittet [Komma igång](../../platform/using/get-started-data-import-export.md).

#### Självstudievideo {#create-email-video}

I den här videon förklaras hur du skapar en kampanj och ett e-postmeddelande i Adobe Campaign Classic.

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

Ytterligare Campaign Classic-instruktionsvideor finns [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).