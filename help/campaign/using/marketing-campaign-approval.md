---
product: campaign
title: Konfigurera och hantera godkännandeprocessen
description: Lär dig hantera godkännanden av marknadsföringskampanjer
language: en
role: User
feature: Approvals, Campaigns
hide: true
hidefromtoc: true
exl-id: 8cbb2445-f5e4-4a25-ba7e-56e39ca9d3ce
source-git-commit: df014d3f3029a61176e5117e27f3d2e8228fc407
workflow-type: tm+mt
source-wordcount: '2665'
ht-degree: 0%

---


# Konfigurera och hantera godkännandeprocessen {#approving-marketing-campaigns}

Varje steg i en leverans kan godkännas för att säkerställa full övervakning och kontroll av kampanjprocesserna. Dessa omfattar målinriktning, innehåll, budget, extrahering och utskick av ett bevis.

Meddelanden skickas till [!DNL Adobe Campaign]-operatorer som är utsedda granskare för att informera dem om en godkännandebegäran. Kontrollera att granskarna har **behörighet** att godkänna och att deras säkerhetszon är korrekt definierad. [Läs mer om hur du väljer granskare](#selecting-reviewers).

Godkännandeproceduren presenteras i [Översikt över godkännandeproceduren](#checking-and-approving-deliveries).

>[!NOTE]
>
>Endast leveransägaren kan påbörja en leverans. För att en annan operator (eller operatorgrupp) ska kunna starta en leverans måste du lägga till dem som granskare i fältet **[!UICONTROL Delivery start:]**.\
>[Läs mer om hur du väljer granskare](#selecting-reviewers).

## Verksamhetsprincip {#operating-principle-}

Standardmeddelandet för budgetgodkännande är till exempel följande:

![E-postmeddelande om godkännande med valideringslänk](assets/s_user_validation_link_in_mail.png)

Granskningsoperatorerna kan sedan välja att godkänna budgeten eller inte.

![Bekräftelsesida för godkännande med alternativ för godkännande eller avvisning](assets/s_user_validation_page_confirm.png)

När operatorn validerar vidarebefordras godkännande eller avvisning av jobbet till kontrollpanelen för leverans.

![Kampanjinstrumentpanelen med godkännandelänk för ett jobb](assets/s_user_validation_link_in_op_board.png)

Informationen finns också i kampanjens godkännandeloggar. Loggarna nås via fliken **[!UICONTROL Edit > Tracking > Approvals]**.

![Fliken Kampanjredigering med godkännandelogg](assets/s_user_validation_log_in_op_edit_tab.png)

Dessa meddelanden skickas till de operatorer som påverkas av varje process som har aktiverats för godkännande.

Godkännanden kan aktiveras för kampanjmallen, för varje enskild kampanj eller för en leverans.

Alla jobb som kräver godkännande markeras i kampanjmallen ( **[!UICONTROL Properties]** > **[!UICONTROL Advanced campaign settings...]** > fliken **[!UICONTROL Approvals]**). Operatorerna som ansvarar för godkännandet väljs också där och får meddelanden om inte det här alternativet är inaktiverat. Mer information finns i [stegen för att godkänna en leverans](#approving-processes).

Dessa inställningar kan åsidosättas för varje kampanj som skapas med den här mallen och individuellt för varje kampanjleverans: klicka på knappen **[!UICONTROL Properties]** och sedan på fliken **[!UICONTROL Approvals]**.

I följande exempel kommer leveransinnehållet inte att kräva godkännande:

![Inställningar för leveransgodkännande med processval](assets/s_user_validation_select_process_from_del.png)

## Välj granskare {#selecting-reviewers}

För varje typ av godkännande väljs de operatörer eller operatörsgrupper som ansvarar för godkännandet i den nedrullningsbara listan i leveransen. Fler operatorer kan läggas till via länken **[!UICONTROL Edit...]**. I det här fönstret kan du även redigera deadline för godkännande.

![Lägg till granskningsdialogruta för godkännandeoperatorer](assets/s_user_validation_add_operator.png)

Om ingen granskare anges ansvarar kampanjhanteraren för godkännande och får meddelanden. Kampanjhanteraren anges på fliken **[!UICONTROL Edit > Properties]** i kampanjen:

![Kampanjegenskaper som visar hanteringsfält](assets/s_user_op_manager_field.png)

>[!NOTE]
>
>Alla andra [!DNL Adobe Campaign]-operatorer med **[!UICONTROL Administrator]**-behörighet kan också godkänna jobb, men de får inga meddelanden.\
>Som standard kan kampanjledaren inte genomföra godkännandet eller starta leveranserna om godkännandeoperatorer har definierats. Du kan ändra det här beteendet och auktorisera kampanjhanteraren att godkänna/starta leveranser genom att skapa alternativet **NmsCampaign_Activate_OwnerConfirmation** med **1** som ett värde.

## Godkännandelägen {#approval-modes}

### Godkännande via kontrollpanelen {#approval-via-the-dashboard}

Om du vill godkänna ett jobb via konsolen eller webbgränssnittet klickar du på lämplig länk på kontrollpanelen för kampanjer. Jobb kan också godkännas via leveransspårning eller via kontrollpanelen för leverans.

![Godkännandeåtgärder för kampanjinstrumentpanelen i konsolen](assets/s_user_validation_from_console.png)

Kontrollera den information som ska godkännas, välj om du vill godkänna eller inte och ange en kommentar om det behövs. Klicka på **[!UICONTROL Ok]** om du vill spara.

>[!NOTE]
>
>Om en process redan har godkänts av en annan operator är godkännandelänken inte tillgänglig.

### Godkännande via meddelanden {#approval-via-notification-messages}

Klicka på länken som finns i meddelandet (se [Meddelanden](#notifications)). Du måste logga in enligt nedan:

![Inloggningssida för godkännande för meddelandelänken](assets/s_user_validation__log_in.png)

Välj **[!UICONTROL Accept]** eller **[!UICONTROL Reject]** och ange en kommentar om det behövs.

![Godkännandesida med acceptera eller avvisa och kommentera](assets/s_user_validation_save_target_validation.png)

Klicka på **[!UICONTROL Validate]**.

>[!NOTE]
>
>Om varningar utlöstes under processen visas en varning i meddelandet.

### Godkännandespårning {#approval-tracking}

Informationen finns på flera ställen:

* I loggen för kampanjgodkännande finns underfliken **[!UICONTROL Approvals]** på fliken **[!UICONTROL Edit > Tracking]**:

  ![Logglista för kampanjgodkännande](assets/s_user_validation_log_from_op.png)

* I kampanjleveransloggen, **[!UICONTROL Deliveries]**-underfliken på fliken **[!UICONTROL Edit > Tracking]**:

  ![Leveranslogglista med godkännandestatus](assets/s_user_validation_log_from_delivery_list.png)

* Godkännandestatusen för varje leverans kan visas genom att klicka på alternativet **[!UICONTROL Hide/show log]** på fliken **[!UICONTROL Summary]**.

  ![Leveranssammanfattning som visar godkännandelogg](assets/s_user_validation_log_delivery.png)

* Den här informationen kan också nås via fliken **[!UICONTROL Tracking > Approvals]** för varje leverans:

  ![Fliken Godkännanden för leveransspårning](assets/s_user_validation_log_from_exe_tab.png)

>[!NOTE]
>
>När en operator har godkänt eller avvisat ett jobb kan de andra granskarna inte längre agera på godkännandet.

### Automatiskt och manuellt godkännande {#automatic-and-manual-approval}

När du skapar ett arbetsflöde för målinriktning, om godkännandet är automatiskt (standardläge), visar [!DNL Adobe Campaign] godkännandelänken eller skickar ett meddelande så snart ett godkännande krävs.

Om du vill välja godkännandeläge (manuellt eller automatiskt) klickar du på fliken **[!UICONTROL Edit > Properties]** i kampanj- eller kampanjmallen, klickar sedan på **[!UICONTROL Advanced campaign settings...]** och slutligen på fliken **[!UICONTROL Approvals]**.

![Godkännandeinställningar med manuellt och automatiskt läge](assets/s_user_validation_select_mode.png)

>[!NOTE]
>
>Det valda godkännandeläget gäller alla leveranser av kampanjen.

När ett arbetsflöde med målinriktning skapas kan du med manuellt godkännande undvika att skapa godkännandelänkar eller skicka meddelanden automatiskt. Kampanjinstrumentpanelen erbjuder sedan en **[!UICONTROL Submit targeting for approval]**-länk för att starta godkännandeprocessen manuellt.

Med ett bekräftelsemeddelande kan du auktorisera godkännanden för de jobb som valts för den här leveransen.

Godkännandeknapparna visas sedan på kontrollpanelen för kampanjer (för den här leveransen), på kontrollpanelen för leveranser och i leveransspårningen. Om meddelanden är aktiverade skickas de parallellt.

Med den här metoden kan du aktivera godkännanden utan att skicka falska meddelanden till granskarna.

## Meddelanden {#notifications}

Meddelanden är specifika e-postmeddelanden som skickas till granskarna för att informera dem om att en process väntar på godkännande. När operatorn klickar på länken i meddelandet visas en autentiseringssida, och efter inloggningen kan operatorn visa informationen och godkänna eller avvisa jobbet. En kommentar kan också anges i godkännandefönstret.

Innehållet i e-postmeddelanden kan personaliseras. Se [Meddelandeinnehåll](#notification-content).

### Aktivera/inaktivera meddelande {#enabling-disabling-notification}

Som standard skickas aviseringsmeddelanden om godkännandet av det relaterade jobbet är aktiverat i kampanjmallen, kampanjen eller leveransen. Meddelanden kan dock inaktiveras för att endast auktorisera godkännanden från konsolen.

Det gör du genom att redigera godkännandefönstret för kampanj- eller kampanjmallen ( **[!UICONTROL Edit > Properties]** > **[!UICONTROL Advanced campaign settings...]** > fliken **[!UICONTROL Approvals]**) och välja **[!UICONTROL Do not enable notification sending]**.

![Godkännandeinställningar med inaktiverade meddelanden](assets/s_user_validation_notif_desactivate.png)

### Meddelandeinnehåll {#notification-content}

Meddelandeinnehåll definieras i en specifik mall: **[!UICONTROL Notification of validations for the marketing campaign]**. Den här mallen sparas i mappen **[!UICONTROL Administration > Campaign management > Technical delivery templates]** i trädet [!DNL Adobe Campaign].

## Granska och godkänn leveranser {#checking-and-approving-deliveries}

Med [!DNL Adobe Campaign] kan du konfigurera godkännandeprocesser för huvudstegen i marknadsföringskampanjen i samarbetsläge.

För direktutskick av e-post kan [!DNL Adobe Campaign]-operatorer visa extraheringsfilen innan den skickas till routern, och om det behövs kan de ändra formatet och starta om extraheringen. Se [Godkänn en extraheringsfil](#approving-an-extraction-file).

För varje kampanj kan du godkänna leveransmålet, innehållet (se [Godkänn innehåll](#approving-content)) och kostnaderna. [!DNL Adobe Campaign]-operatorer som ansvarar för godkännande kan meddelas via e-post och kan acceptera eller avvisa godkännande från konsolen eller via en webbanslutning. Se [Steg för att godkänna en leverans](#approving-processes).

När dessa valideringsfaser är klara kan leveransen startas. [Läs mer om hur du påbörjar en leverans](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery).

### Steg för att godkänna en leverans {#approving-processes}

De faser som kräver godkännande visas på kampanjkontrollpanelen (via konsolen i webbgränssnittet). De visas också i leveransspårningstabellen och på leveransinstrumentpanelen.

Nu är kampanjens status **[!UICONTROL To validate]**.

>[!NOTE]
>
>Om du vill välja de processer som kräver ett godkännande ändrar du kampanjmallen. Mer information finns i [Kampanjmallar](../../campaign/using/marketing-campaign-templates.md#campaign-templates).
>

![Kampanjinstrumentpanelen med leveransstatus Att validera](assets/s_ncs_user_edit_del_to_validate.png)

>[!NOTE]
>
>Om ett fel som är länkat till ett konfigurationsproblem uppstår under meddelandeförberedelsen i ett målarbetsflöde visas länken **[!UICONTROL Restart message preparation]** på instrumentpanelen. Åtgärda felet och klicka på den här länken för att starta om meddelandeförberedelsen samtidigt som målfasen kringgås.

![Instrumentpanelslänk för att starta om meddelandeförberedelsen](assets/s_user_validation_relaunch_message_preparation.png)

För varje leverans i kampanjen kan du godkänna följande processer:

* **Målinriktning, innehåll och budget**

  När alternativen **[!UICONTROL Enable target approval]**, **[!UICONTROL Enable content approval]** eller **[!UICONTROL Enable budget approval]** har valts i inställningsfönstret för jobbgodkännande visas de relevanta länkarna i kontrollpanelen för kampanjen för de aktuella leveranserna.

  >[!NOTE]
  >
  >Budgetgodkännande är bara tillgängligt om målgodkännande är aktiverat i fönstret för godkännandeinställningar. Länken för budgetgodkännande visas bara när målet har analyserats. Länken visas också tillsammans med länken för målgodkännande.

  Om alternativen **[!UICONTROL Assign content editing]** eller **[!UICONTROL External content approval]** väljs i fönstret för godkännandeinställningar visas länkarna **[!UICONTROL Available content]** och **[!UICONTROL External content approval]** på kontrollpanelen.

  Med godkännande av innehåll får du åtkomst till de skickade korrekturen.

* **Godkännande av extrahering (direktutskick)**

  När **[!UICONTROL Enable extraction approval]** har valts i fönstret för godkännandeinställningar måste den extraherade filen godkännas innan routern kan meddelas.

  En **[!UICONTROL Approve content]**-länk är tillgänglig på kampanjinstrumentpanelen enligt nedan:

  ![Kontrollpanel för godkännande med länken Godkänn innehåll](assets/s_ncs_user_edit_file_valid.png)

  Extraheringsfiler kan förhandsgranskas via rutan för godkännande och sedan accepteras eller avvisas.

  ![Förhandsgranskning av extraheringsfil i godkännandedialogrutan](assets/s_ncs_user_edit_file_valid_preview_file.png)

  >[!NOTE]
  >
  >Förhandsgranskningen av extraheringsfilen gäller endast ett dataexempel. Hela utdatafilen läses inte in.

* **Godkänner associerade leveranser**

  Alternativet **[!UICONTROL Enable individual approval of each associated delivery]** används för en huvudleverans som är associerad med sekundära leveranser. Som standard är det här alternativet inte markerat så att ett övergripande godkännande av huvudleveransen kan utföras. Om du väljer det här alternativet måste varje leverans godkännas individuellt.

  ![Alternativ för att aktivera enskilt godkännande av associerade leveranser](assets/s_ncs_user_task_valid_associate.png)

### Välj godkända processer {#choosing-the-processes-to-be-approved}

Godkännandefaserna definieras med den mall som är associerad med kampanjen. Du måste välja de element som ska godkännas från mallen och ange de [!DNL Adobe Campaign]-operatorer som ansvarar för godkännandena. Mer information om kampanjmallar finns i [kampanjmallar](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

>[!NOTE]
>
>Godkännandekonfigurationen för kampanjen (eller kampanjmallen) gäller för alla framtida leveranser som är länkade till den här kampanjen. Konfigurationsändringar kommer inte att tillämpas på tidigare leveranser.

Den här informationen kan åsidosättas för varje kampanj och varje leverans.

För en kampanj klickar du på fliken **[!UICONTROL Edit > Properties]**, sedan på länken **[!UICONTROL Advanced campaign settings...]** och slutligen på underfliken **[!UICONTROL Approvals]** för att komma åt sidan för godkännandekonfiguration.

Du kan markera och avmarkera de processer som ska godkännas och utse [!DNL Adobe Campaign]-operatorer som ansvarar för godkännandet. Det kan vara enskilda operatorer, en grupp operatorer eller en lista med operatorer.

Om du vill välja en lista med operatorer klickar du på länken **[!UICONTROL Edit...]** till höger om fältet som anger den första granskaren och lägger till så många operatorer som behövs, enligt följande:

![Lägg till granskningsdialogruta för godkännandeoperatorer](assets/s_user_validation_add_operator.png)

>[!NOTE]
>
>* Om en lista över granskare definieras, godkänns ett jobb när en granskare har godkänt det. Länken för godkännande finns inte längre på kontrollpanelen. Om en annan granskare klickar på länken för godkännande i meddelandet när meddelanden har skickats, får de ett meddelande om att en annan operator redan har godkänt jobbet.
>* Du kan definiera ett godkännandeschema för kampanjen i den nedre delen av granskningsfönstret. Som standard har granskarna tre dagar på sig att godkänna en process från och med överföringsdatumet. Det är möjligt att konfigurera en påminnelse som automatiskt skickas till de berörda operatörerna före godkännandedeadline.
>* Du kan lägga till påminnelser från det här avsnittet.
>

![Inställningar för godkännandekalender och påminnelse](assets/s_ncs_user_edit_op_valid_calendar.png)

Klicka på knappen **[!UICONTROL Audit]** och fliken **[!UICONTROL Approvals]** för att visa och redigera godkännandedatum och automatiska påminnelser för varje leverans.

![Fliken Leveransgodkännanden med datum och påminnelser](assets/s_ncs_user_edit_del_valid.png)

>[!NOTE]
>
>Den här fliken är tillgänglig när innehållsgodkännandeprocessen har startats.

### Godkänn ett innehåll {#approving-content}

>[!CAUTION]
>
>För att godkänna ett innehåll är en korrekturcykel obligatorisk. Med korrektur kan du godkänna visningen av information, personaliseringsdata och kontrollera att länkar fungerar. Lär dig hur du skapar ett korrektur i [skapa ett bevis](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).
>
>De funktioner för godkännande av innehåll som beskrivs nedan avser leveransbeviset.

Det går att konfigurera en innehållsgodkännandecykel. Det gör du genom att välja alternativet **[!UICONTROL Enable content approval]** i fönstret för godkännandeinställningar. Huvudstegen i innehållsgodkännandecykeln är:

1. När en ny leverans har skapats klickar kampanjhanteraren på länken **[!UICONTROL Submit content]** på kontrollpanelen för kampanjer för att starta innehållsgodkännandecykeln.

   ![Kampanjinstrumentpanelslänk för att skicka innehåll för godkännande](assets/s_ncs_user_validation_submit_content_validation.png)

   >[!NOTE]
   >
   >Om alternativen **[!UICONTROL Enable the sending of proofs]** (för e-postleveranser) eller **[!UICONTROL Enable the sending and approval of proofs]** (för direktmeddelandeleveranser) har valts i fönstret för godkännandeinställningar skickas korrektur automatiskt.

1. Ett e-postmeddelande skickas till den person som ansvarar för innehållet, som kan välja om det ska godkännas eller inte:

   * via e-postmeddelandet:

     ![E-postmeddelande om godkännande av innehåll för korrektur](assets/s_ncs_user_del_content_valid_bat_notif.png)

     >[!NOTE]
     >
     >E-postmeddelandet innehåller en länk till de korrektur som redan har skickats, och eventuellt till en återgivning av meddelandet för de olika webbreklementen om alternativet **Slutprodukt** är aktiverat för den här instansen.

   * via konsolen eller webbgränssnittet, leveransspårning, kontrollpanelen för leverans eller kontrollpanelen för kampanjer:

     ![Leveransspårning med innehållskorrekturlista](assets/s_ncs_user_validation_content_bat_op.png)

     >[!NOTE]
     >
     >På den här kampanjinstrumentpanelen kan du visa en lista med korrektur som har skickats genom att klicka på länken **[!UICONTROL Inbox rendering...]**. Klicka på ikonen **[!UICONTROL Detail]** till höger om listan för att visa innehållet.

     ![Vyn Korrekturinformation för godkännande av innehåll](assets/s_ncs_user_validation_content_BAT_details.png)

1. Ett e-postmeddelande skickas till den person som är ansvarig för kampanjen som informerar dem om huruvida innehållet har godkänts eller inte.

   >[!NOTE]
   >
   >Den person som ansvarar för kampanjen kan när som helst starta om innehållsgodkännandecykeln. Det gör du genom att klicka på länken på raden **[!UICONTROL Content status]** på kontrollpanelen för kampanjer (på leveransnivå) och sedan klicka på **[!UICONTROL Reset content approval to submit it again]**.

   ![Kampanjinstrumentpanelslänk för att starta om innehållsgodkännande](assets/s_user_validation_relaunch_content_validation.png)

#### Tilldela redigering av innehåll {#assign-content-editing}

Med det här alternativet kan du definiera någon som ansvarar för redigering av innehåll, till exempel en webbmaster. Om alternativet **[!UICONTROL Assign content editing]** är markerat i fönstret för godkännandeinställningar läggs flera godkännandesteg till mellan att leveransen skapas och att e-postmeddelandet levereras till den person som ansvarar för innehållet:

1. När en ny leverans har skapats klickar den person som är ansvarig för kampanjen på länken **[!UICONTROL Submit content editing]** på kontrollpanelen för kampanjer för att starta redigeringscykeln för innehållet.

   ![Kampanjinstrumentpanelslänk för att skicka innehållsredigering](assets/s_ncs_user_validation_submit_content_edition.png)

1. Den person som ansvarar för redigering av innehåll får ett e-postmeddelande om att innehållet är tillgängligt.

   ![Meddelande om redigering av innehåll](assets/s_ncs_user_validation_submit_content_notif.png)

1. De kan sedan logga in på konsolen, öppna leveransen och redigera den med en förenklad assistent för att ändra motivet, HTML och textinnehållet samt skicka korrektur.

   ![Förenklad assistent för redigering av leveransinnehåll](assets/s_user_validation_content_edition.png)

   >[!NOTE]
   >
   >Om alternativen **[!UICONTROL Enable the sending of proofs]** (för e-postleveranser) eller **[!UICONTROL Enable the sending and approval of proofs]** (för direktmeddelandeleveranser) har valts i fönstret för godkännandeinställningar skickas korrektur automatiskt.

1. När den person som ansvarar för redigeringen av innehållet är klar med alla ändringar av leveransinnehållet kan han eller hon göra innehållet tillgängligt.

   För att göra detta kan de

   * klicka på länken **[!UICONTROL Available content]** via konsolen [!DNL Adobe Campaign].

     ![Konsollänk för att göra innehåll tillgängligt](assets/s_ncs_user_validation_submit_content_available.png)

   * klicka på länken i meddelandet och godkänn sedan innehållstillgängligheten.

     ![Meddelandelänk för att godkänna innehållstillgänglighet](assets/s_ncs_user_validation_submit_content_available2.png)

     Operatören kan lägga till en kommentar innan innehållet skickas till den person som ansvarar för kampanjen.

     ![Kommentarsfält innan innehållstillgänglighet skickas](assets/s_ncs_user_validation_submit_content_available3.png)

     I meddelandet kan granskaren godkänna eller avvisa innehållet.

     ![Godkännandesvar för innehållstillgänglighet](assets/s_ncs_user_validation_submit_content_available4.png)

#### Godkännande av externt innehåll {#external-content-approval}

Med det här alternativet kan du definiera en extern operatör som ansvarar för att godkänna leveransåtergivning, som enhetlig varumärkeskommunikation, priser osv. När alternativet **[!UICONTROL External content approval]** har valts i fönstret för godkännandeinställningar läggs flera godkännandesteg till mellan innehållsgodkännandet och leveransen av meddelandet till den person som ansvarar för kampanjen:

1. Den externa innehållshanteraren får ett e-postmeddelande om att innehållet har godkänts och begär externt godkännande.
1. E-postmeddelandet innehåller länkar till skickade korrektur, som gör att du kan visa leveransåtergivning, och en knapp för att godkänna eller avvisa leveransinnehållet.

   >[!NOTE]
   >
   >De här länkarna är bara tillgängliga om ett eller flera korrektur har skickats. I annat fall är leveransåtergivning bara tillgängligt via konsolen eller webbgränssnittet.

   ![E-post för godkännande av externt innehåll med korrekturlänkar](assets/s_user_validation_external_content.png)

### Godkänn en extraheringsfil {#approving-an-extraction-file}

För offlineleveranser genererar [!DNL Adobe Campaign] en extraheringsfil som, beroende på hur den är konfigurerad, skickas till routern. Dess innehåll beror på vilken exportmall som används.

När innehåll, mål och budget har godkänts ändras leveransen till **[!UICONTROL Extraction pending]** tills extraheringsarbetsflödet för kampanjerna startas.

![Leveransstatus som visar väntande extrahering](assets/s_ncs_user_waiting_file_extraction.png)

På extraheringsbegärandedatumet skapas extraheringsfilen och leveransstatusen ändras till **[!UICONTROL File to approve]**.

![Leveransstatus visar fil som ska godkännas](assets/s_ncs_user_file_extract_to_valid.png)

Du kan visa innehållet i den extraherade filen (genom att klicka på filens namn), godkänna den eller, om det behövs, ändra formatet och starta extraheringen igen med hjälp av länkarna på kontrollpanelen.

När filen har godkänts kan du skicka e-postmeddelandet till routern. Mer information finns i [Starta en offlineleverans](../../campaign/using/marketing-campaign-deliveries.md#starting-an-offline-delivery).
