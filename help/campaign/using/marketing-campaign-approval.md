---
title: Godkänna marknadsföringskampanjer
seo-title: Godkänna marknadsföringskampanjer
description: Godkänna marknadsföringskampanjer
seo-description: null
page-status-flag: never-activated
uuid: 842b501f-7d65-4450-b7ab-aff3942fb96f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: 8d076211-10a6-4a98-b0d2-29dad154158c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---

# Godkänna marknadsföringskampanjer {#approving-marketing-campaigns}

## Godkännandeprocess {#approval-process}

Varje steg i en leverans kan godkännas för att säkerställa full övervakning och kontroll av kampanjens olika processer: målgruppsanpassning, innehåll, budget, extrahering och utskick av ett bevis.

>[!NOTE]
>
>Du måste kontrollera att granskarna har behörighet att godkänna. Kontrollera också att deras säkerhetszon är korrekt definierad.

E-postmeddelanden skickas till de Adobe Campaign-operatörer som är utsedda granskare för att informera dem om en begäran om godkännande.

Godkännandeförfarandet presenteras i [Kontroll och godkännande av leveranser](#checking-and-approving-deliveries).

>[!NOTE]
>
>Endast leveransägaren kan påbörja en leverans. För att en annan operator (eller operatörsgrupp) ska kunna starta en leverans måste du lägga till dem som granskare i **[!UICONTROL Delivery start:]** fältet.\
>Se även [Välja granskare](#selecting-reviewers).

### Verksamhetsprincip {#operating-principle-}

Standardmeddelandet för budgetgodkännande blir till exempel följande:

![](assets/s_user_validation_link_in_mail.png)

Granskningsoperatörerna kan sedan välja om det aktuella steget ska godkännas eller inte.

![](assets/s_user_validation_page_confirm.png)

När operatorn har godkänt sitt val vidarebefordras godkännande eller avvisning av jobbet till kontrollpanelen för leverans.

![](assets/s_user_validation_link_in_op_board.png)

Informationen finns också i kampanjens godkännandeloggar (via **[!UICONTROL Edit > Tracking > Approvals]** fliken):

![](assets/s_user_validation_log_in_op_edit_tab.png)

Dessa meddelanden skickas till de operatorer som påverkas av varje process som har aktiverats för godkännande.

Godkännanden kan aktiveras för kampanjmallen, för varje enskild kampanj eller för en leverans.

Alla jobb som kräver godkännande markeras i kampanjmallen ( **[!UICONTROL Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** flik), liksom de operatorer som ansvarar för godkännandet (de får meddelanden om inte det här alternativet är aktiverat). Mer information finns i [Godkännandeprocesser](#approving-processes).

De här inställningarna kan åsidosättas för varje kampanj som skapas med den här mallen och individuellt för varje kampanjleverans: klicka på **[!UICONTROL Properties]** knappen och sedan på **[!UICONTROL Approvals]** fliken.

I följande exempel kommer leveransinnehållet inte att kräva godkännande:

![](assets/s_user_validation_select_process_from_del.png)

### Välja granskare {#selecting-reviewers}

För varje typ av godkännande väljs de operatörer eller operatörsgrupper som ansvarar för godkännandet i den nedrullningsbara listan i leveransen. Ytterligare operatorer kan läggas till via **[!UICONTROL Edit...]** länken. I det här fönstret kan du även redigera deadline för godkännande.

![](assets/s_user_validation_add_operator.png)

Om ingen granskare anges ansvarar kampanjhanteraren för godkännande och får meddelanden. Kampanjhanteraren anges på fliken **[!UICONTROL Edit > Properties]** i kampanjen:

![](assets/s_user_op_manager_field.png)

>[!NOTE]
>
>Alla andra Adobe Campaign-operatorer med **[!UICONTROL Administrator]** rättigheter kan också godkänna jobb, men de får inga meddelanden.\
>Som standard kan kampanjledaren inte genomföra godkännandet eller starta leveranserna om godkännandeoperatorer har definierats. Du kan ändra det här beteendet och auktorisera kampanjhanteraren att godkänna/starta leveranser genom att skapa alternativet **NmsCampaign_Activate_OwnerConfirmation** med **1** som värde.

### Godkännandelägen {#approval-modes}

#### Godkännande via kontrollpanelen {#approval-via-the-dashboard}

Om du vill godkänna ett jobb via konsolen eller webbgränssnittet klickar du på lämplig länk på kontrollpanelen för kampanjer. Jobb kan också godkännas via leveransspårning eller via kontrollpanelen för leverans.

![](assets/s_user_validation_from_console.png)

Kontrollera den information som ska godkännas, välj om du vill godkänna eller inte och ange en kommentar om det behövs. Klicka **[!UICONTROL Ok]** för att spara.

>[!NOTE]
>
>Om en process redan har godkänts av en annan operator är godkännandelänken inte tillgänglig.

#### Godkännande via meddelanden {#approval-via-notification-messages}

Klicka på länken i meddelandet (se [Meddelanden](#notifications)). Du ombeds att identifiera dig, som visas nedan:

![](assets/s_user_validation__log_in.png)

Markera **[!UICONTROL Accept]** eller **[!UICONTROL Reject]** skriv en kommentar om det behövs.

![](assets/s_user_validation_save_target_validation.png)

Klicka **[!UICONTROL Validate]**.

>[!NOTE]
>
>Om varningar utlöstes under processen visas en varning i meddelandet.

#### Godkännandespårning {#approval-tracking}

Informationen finns på flera ställen:

* I loggen för kampanjgodkännande finns **[!UICONTROL Approvals]** en underflik på **[!UICONTROL Edit > Tracking]** fliken:

   ![](assets/s_user_validation_log_from_op.png)

* I kampanjleveransloggen **[!UICONTROL Deliveries]** underfliken på **[!UICONTROL Edit > Tracking]** fliken:

   ![](assets/s_user_validation_log_from_delivery_list.png)

* Godkännandestatusen för varje leverans kan visas genom att klicka på **[!UICONTROL Hide/show log]** alternativet på **[!UICONTROL Summary]** fliken.

   ![](assets/s_user_validation_log_delivery.png)

* Den här informationen kan även nås via fliken **[!UICONTROL Tracking > Approvals]** för varje leverans:

   ![](assets/s_user_validation_log_from_exe_tab.png)

>[!NOTE]
>
>När en operator har godkänt eller avvisat ett jobb kan de andra granskarna inte längre agera på godkännandet.

#### Automatiskt och manuellt godkännande {#automatic-and-manual-approval}

När du skapar ett arbetsflöde för målinriktning, om godkännandet är automatiskt (standardläge), visas länken för godkännande eller ett meddelande skickas så snart ett godkännande krävs.

Om du vill välja godkännandeläge (manuellt eller automatiskt) klickar du på fliken **[!UICONTROL Edit > Properties]** i kampanj- eller kampanjmallen, klickar **[!UICONTROL Advanced campaign settings...]** och slutligen på **[!UICONTROL Approvals]** fliken.

![](assets/s_user_validation_select_mode.png)

>[!NOTE]
>
>Det valda godkännandeläget gäller alla leveranser av kampanjen.

När ett arbetsflöde med målinriktning skapas kan du med manuellt godkännande undvika att skapa godkännandelänkar eller skicka meddelanden automatiskt. Kampanjkontrollpanelen erbjuder sedan en **[!UICONTROL Submit targeting for approval]** länk för att starta godkännandeprocessen manuellt.

Med ett bekräftelsemeddelande kan du auktorisera godkännanden för de jobb som valts för den här leveransen.

Godkännandeknapparna visas sedan på kontrollpanelen för kampanjer (för den här leveransen), på kontrollpanelen för leveranser och i leveransspårningen. Om meddelanden är aktiverade skickas de parallellt.

Med den här metoden kan du aktivera godkännanden utan att skicka falska meddelanden till granskarna.

### Meddelanden {#notifications}

Meddelanden är specifika e-postmeddelanden som skickas till granskarna för att informera dem om att en process väntar på godkännande. När operatorn klickar på länken i meddelandet visas en autentiseringssida, och efter inloggningen kan operatorn visa informationen och godkänna eller avvisa jobbet. En kommentar kan också anges i godkännandefönstret.

Innehållet i e-postmeddelanden kan personaliseras. Se [Meddelandeinnehåll](#notification-content).

#### Aktivera/inaktivera meddelanden {#enabling-disabling-notification}

Som standard skickas aviseringsmeddelanden om godkännandet av det relaterade jobbet är aktiverat i kampanjmallen, kampanjen eller leveransen. Meddelanden kan dock inaktiveras för att endast auktorisera godkännanden från konsolen.

Det gör du genom att redigera godkännandefönstret för kampanj- eller kampanjmallen ( **[!UICONTROL Edit > Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** flik) och välja **[!UICONTROL Do not enable notification sending]**.

![](assets/s_user_validation_notif_desactivate.png)

#### Meddelandeinnehåll {#notification-content}

Meddelandeinnehåll definieras i en specifik mall: **[!UICONTROL Notification of validations for the marketing campaign]**. Den här mallen sparas i mappen **[!UICONTROL Administration > Campaign management > Technical delivery templates]** i Adobe Campaign-trädet.

## Kontrollera och godkänna leveranser {#checking-and-approving-deliveries}

Med Adobe Campaign kan ni skapa godkännandeprocesser för de viktigaste stegen i marknadsföringskampanjen i samverkansbaserat läge.

För direktutskick kan Adobe Campaign-operatorer visa extraheringsfilen innan den skickas till routern, och om det behövs kan de ändra formatet och starta om extraheringen. Se [Godkänna en extraheringsfil](#approving-an-extraction-file).

För varje kampanj kan du godkänna leveransmålet, innehållet (se [Godkänna innehåll](#approving-content)) och kostnaderna. De Adobe Campaign-operatörer som ansvarar för godkännandet kan meddelas via e-post och godkänna eller avvisa godkännanden från konsolen eller via en webbanslutning. Se [Godkännandeprocesser](#approving-processes).

När dessa valideringsfaser är klara kan leveransen startas. Se [Påbörja leverans](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery).

>[!NOTE]
>
>Mer information om godkännandelägen och spårning finns i [Godkännandeprocess](#approval-process).

### Godkännandeprocesser {#approving-processes}

De faser som kräver godkännande visas på kampanjkontrollpanelen (via konsolen i webbgränssnittet). De visas också i leveransspårningstabellen och på leveransinstrumentpanelen.

Nu är kampanjens status **[!UICONTROL To validate]**.

>[!NOTE]
>
>* Om du vill välja vilka processer som ska godkännas ändrar du kampanjmallen. Mer information finns i [Campaign-mallar](../../campaign/using/marketing-campaign-templates.md#campaign-templates).
   >
   >
* Se även avsnittet om [godkännandeprocessen](#approval-process).



![](assets/s_ncs_user_edit_del_to_validate.png)

>[!NOTE]
>
>Om ett fel som är länkat till ett konfigurationsproblem uppstår under meddelandeförberedelsen i ett målarbetsflöde visas länken på kontrollpanelen. **[!UICONTROL Restart message preparation]** Åtgärda felet och klicka på den här länken för att starta om meddelandeförberedelsen samtidigt som målfasen kringgås.

![](assets/s_user_validation_relaunch_message_preparation.png)

För varje leverans i kampanjen kan du godkänna följande processer:

* **Målgruppsanpassning, innehåll och budget**

   När **[!UICONTROL Enable target approval]**, **[!UICONTROL Enable content approval]** eller **[!UICONTROL Enable budget approval]** alternativ väljs i inställningsfönstret för jobbgodkännande visas de relevanta länkarna på kontrollpanelen för kampanjer för de aktuella leveranserna.

   >[!NOTE]
   >
   >Budgetgodkännande är bara tillgängligt om målgodkännande är aktiverat i fönstret för godkännandeinställningar. Länken för budgetgodkännande visas bara när målet har analyserats. Länken visas också tillsammans med länken för målgodkännande.

   Om **[!UICONTROL Assign content editing]** eller **[!UICONTROL External content approval]** alternativen är markerade i fönstret för godkännandeinställningar visas länkarna **[!UICONTROL Available content]** och **[!UICONTROL External content approval]** på kontrollpanelen.

   Med godkännande av innehåll får du åtkomst till de skickade korrekturen.

* **Godkännande av utdrag (direktutskick)**

   När **[!UICONTROL Enable extraction approval]** är markerat i fönstret för godkännandeinställningar måste den extraherade filen godkännas innan routern kan meddelas.

   En **[!UICONTROL Approve content]** länk finns tillgänglig på kampanjinstrumentpanelen enligt nedan:

   ![](assets/s_ncs_user_edit_file_valid.png)

   Extraheringsfiler kan förhandsgranskas via rutan för godkännande och sedan accepteras eller avvisas.

   ![](assets/s_ncs_user_edit_file_valid_preview_file.png)

   >[!NOTE]
   >
   >Förhandsgranskningen av extraheringsfilen gäller endast ett dataexempel. Hela utdatafilen läses inte in.

* **Godkänner associerade leveranser**

   Alternativet **[!UICONTROL Enable individual approval of each associated delivery]** används för en huvudleverans som är kopplad till sekundära leveranser. Som standard är det här alternativet inte markerat så att ett övergripande godkännande av huvudleveransen kan utföras. Om du väljer det här alternativet måste varje leverans godkännas individuellt.

   ![](assets/s_ncs_user_task_valid_associate.png)

#### Välja processer som ska godkännas {#choosing-the-processes-to-be-approved}

Godkännandefaserna definieras med den mall som är associerad med kampanjen. Du måste välja vilka element som ska godkännas från mallen och ange vilka Adobe Campaign-operatorer som ska ansvara för godkännandena. Mer information finns i [Campaign-mallar](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

>[!NOTE]
>
>Godkännandekonfigurationen för kampanjen eller kampanjmallen kommer att tillämpas på alla framtida leveranser som är länkade till den här kampanjen. Konfigurationsändringar kommer inte att tillämpas på tidigare leveranser.

Den här informationen kan åsidosättas för varje kampanj och varje leverans.

För en kampanj klickar du på **[!UICONTROL Edit > Properties]** fliken, sedan på **[!UICONTROL Advanced campaign settings...]** länken och slutligen på **[!UICONTROL Approvals]** underfliken för att komma åt sidan för godkännandekonfiguration.

Du kan markera och avmarkera de processer som ska godkännas och utse Adobe Campaign-operatörer som ansvarar för godkännandet. Det kan vara enskilda operatorer, en grupp operatorer eller en lista med operatorer.

Om du vill välja en lista med operatorer klickar du på länken till höger om det fält som anger den första granskaren och lägger till så många operatorer som behövs, vilket visas nedan: **[!UICONTROL Edit...]**

![](assets/s_user_validation_add_operator.png)

>[!NOTE]
>
>* Om en lista över granskare definieras, godkänns ett jobb så snart en granskare har godkänt det. Länken för godkännande finns inte längre på kontrollpanelen. Om en annan granskare klickar på länken för godkännande i meddelandet när meddelanden har skickats, får de ett meddelande om att en annan operator redan har godkänt jobbet.
>* Du kan definiera ett godkännandeschema för kampanjen i den nedre delen av granskningsfönstret. Som standard har granskarna tre dagar på sig att godkänna en process från och med överföringsdatumet. Det är möjligt att konfigurera en påminnelse som automatiskt skickas till de berörda operatörerna före godkännandedeadline.
>* Du kan lägga till påminnelser från det här avsnittet.
>



![](assets/s_ncs_user_edit_op_valid_calendar.png)

För varje leverans klickar du på **[!UICONTROL Audit]** knappen och på **[!UICONTROL Approvals]** fliken för att visa och redigera godkännandedatum och automatiska påminnelser.

![](assets/s_ncs_user_edit_del_valid.png)

>[!NOTE]
>
>Den här fliken är tillgänglig när innehållsgodkännandeprocessen har startats.

### Godkänna innehåll {#approving-content}

>[!CAUTION]
>
>För att godkänna ett innehåll är en korrekturcykel obligatorisk. Med korrektur kan du godkänna visningen av information, personaliseringsdata och kontrollera att länkar fungerar. Mer information om hur du skapar ett korrektur och dess livscykel finns i avsnittet [Skicka meddelanden](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof) .
>
>De funktioner för godkännande av innehåll som beskrivs nedan är avsedda att läggas till i provleveransen.

Det går att konfigurera en innehållsgodkännandecykel. Det gör du genom att välja **[!UICONTROL Enable content approval]** alternativet i fönstret för godkännandeinställningar. Huvudstegen i innehållsgodkännandecykeln är:

1. När en ny leverans har skapats klickar kampanjhanteraren på **[!UICONTROL Submit content]** länken på kampanjkontrollpanelen för att starta innehållsgodkännandecykeln.

   ![](assets/s_ncs_user_validation_submit_content_validation.png)

   >[!NOTE]
   >
   >Om **[!UICONTROL Enable the sending of proofs]** alternativen (för e-postleveranser) eller **[!UICONTROL Enable the sending and approval of proofs]** (för direktreklam) har valts i fönstret för godkännandeinställningar skickas korrektur automatiskt.

1. Ett e-postmeddelande skickas till den person som ansvarar för innehållet, som kan välja om det ska godkännas eller inte:

   * via e-postmeddelandet:

      ![](assets/s_ncs_user_del_content_valid_bat_notif.png)

      >[!NOTE]
      >
      >E-postmeddelandet innehåller en länk till de korrektur som redan har skickats, och eventuellt till en återgivning av meddelandet för de olika webbmejlen, om alternativet **Leverans** är aktiverat för den här instansen.

   * via konsolen eller webbgränssnittet, leveransspårning, kontrollpanelen för leverans eller kontrollpanelen för kampanjer:

      ![](assets/s_ncs_user_validation_content_bat_op.png)

      >[!NOTE]
      >
      >På den här kampanjkontrollpanelen kan du visa en lista över de korrektur som har skickats genom att klicka på **[!UICONTROL Inbox rendering...]** länken. Om du vill visa innehållet klickar du på **[!UICONTROL Detail]** ikonen till höger om listan.

      ![](assets/s_ncs_user_validation_content_BAT_details.png)

1. Ett e-postmeddelande skickas till den person som ansvarar för kampanjen som informerar dem om huruvida innehållet har godkänts eller inte.

   >[!NOTE]
   >
   >Den person som ansvarar för kampanjen kan när som helst starta om innehållsgodkännandecykeln. Det gör du genom att klicka på länken på **[!UICONTROL Content status]** raden i kampanjinstrumentpanelen (på leveransnivå) och sedan klicka på **[!UICONTROL Reset content approval to submit it again]**.

   ![](assets/s_user_validation_relaunch_content_validation.png)

#### Tilldela redigering av innehåll {#assign-content-editing}

Med det här alternativet kan du definiera någon som ansvarar för redigering av innehåll, till exempel en webbmaster. Om **[!UICONTROL Assign content editing]** alternativet är markerat i fönstret för godkännandeinställningar läggs flera godkännandesteg till mellan det att meddelandet skapas och levereras till den person som ansvarar för innehållet:

1. När du har skapat en ny leverans klickar den person som ansvarar för kampanjen på **[!UICONTROL Submit content editing]** länken på kontrollpanelen för kampanjer för att starta redigeringscykeln för innehållet.

   ![](assets/s_ncs_user_validation_submit_content_edition.png)

1. Den person som ansvarar för redigering av innehåll får ett e-postmeddelande om att innehållet är tillgängligt.

   ![](assets/s_ncs_user_validation_submit_content_notif.png)

1. De kan sedan logga in på konsolen, öppna leveransen och redigera den med en förenklad guide för att ändra motiv, HTML och textinnehåll samt skicka korrektur.

   ![](assets/s_user_validation_content_edition.png)

   >[!NOTE]
   >
   >Om **[!UICONTROL Enable the sending of proofs]** alternativen (för e-postleveranser) eller **[!UICONTROL Enable the sending and approval of proofs]** (för direktreklam) har valts i fönstret för godkännandeinställningar skickas korrektur automatiskt.

1. När den person som ansvarar för redigeringen av innehållet är klar med alla ändringar av leveransinnehållet kan han eller hon göra innehållet tillgängligt.

   För att göra detta kan de

   * klicka på **[!UICONTROL Available content]** länken via Adobe Campaign-konsolen.

      ![](assets/s_ncs_user_validation_submit_content_available.png)

   * klicka på länken i meddelandet och godkänn sedan innehållstillgängligheten.

      ![](assets/s_ncs_user_validation_submit_content_available2.png)

      Operatören kan lägga till en kommentar innan innehållet skickas till den person som ansvarar för kampanjen.

      ![](assets/s_ncs_user_validation_submit_content_available3.png)

      I meddelandet kan granskaren godkänna eller avvisa innehållet.

      ![](assets/s_ncs_user_validation_submit_content_available4.png)

#### Godkännande av externt innehåll {#external-content-approval}

Med det här alternativet kan du definiera en extern operatör som ansvarar för att godkänna leveransåtergivning, som enhetlig varumärkeskommunikation, priser osv. När **[!UICONTROL External content approval]** alternativet väljs i fönstret för godkännandeinställningar läggs flera godkännandesteg till mellan innehållsgodkännande och leverans av meddelandet till den person som ansvarar för kampanjen:

1. Den externa innehållshanteraren får ett e-postmeddelande om att innehållet har godkänts och begär externt godkännande.
1. E-postmeddelandet innehåller länkar till skickade korrektur, som gör att du kan visa leveransåtergivning, och en knapp för att godkänna eller avvisa leveransinnehållet.

   >[!NOTE]
   >
   >Länkarna är bara tillgängliga om ett eller flera korrektur har skickats. I annat fall är leveransåtergivning bara tillgängligt via konsolen eller webbgränssnittet.

   ![](assets/s_user_validation_external_content.png)

### Godkänna en extraheringsfil {#approving-an-extraction-file}

För offlineleveranser genererar Adobe Campaign en extraheringsfil som, beroende på hur den är konfigurerad, skickas till routern. Dess innehåll beror på vilken exportmall som används.

När innehållet, målsättningen och budgeten har godkänts ändras leveransen till **[!UICONTROL Extraction pending]** tills extraheringsarbetsflödet för kampanjerna har startats.

![](assets/s_ncs_user_waiting_file_extraction.png)

Extraheringsfilen skapas på extraheringsbegärandedatumet och leveransstatusen ändras till **[!UICONTROL File to approve]**.

![](assets/s_ncs_user_file_extract_to_valid.png)

Du kan visa innehållet i den extraherade filen (genom att klicka på filens namn), godkänna den eller, om det behövs, ändra formatet och starta extraheringen igen med hjälp av länkarna på kontrollpanelen.

När filen har godkänts kan du skicka e-postmeddelandet till routern. Mer information finns i [Starta en offlineleverans](../../campaign/using/marketing-campaign-deliveries.md#starting-an-offline-delivery).
