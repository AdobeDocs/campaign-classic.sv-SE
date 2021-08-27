---
product: campaign
title: Verifierar leveransen
description: Verifierar leveransen
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
exl-id: c2f4d8d0-f0fe-4d1a-92fd-91edaf9729f3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1663'
ht-degree: 5%

---

# Validera leveransen {#validating-the-delivery}

![](../../assets/common.svg)

När en leverans har skapats och konfigurerats måste du validera den innan du skickar den till huvudmålet.

Så här gör du:

1. **Analysera leveransen**: Med det här steget kan du förbereda meddelanden som ska levereras. [Läs mer](#analyzing-the-delivery).

   Reglerna som används under analysen visas i [det här avsnittet](#validation-process-with-typologies). De tillgängliga valideringslägena beskrivs i avsnittet [Ändra godkännandeläge](#changing-the-approval-mode).

1. **Skicka korrektur**: I det här steget kan du styra innehåll, URL-adresser, personalisering osv. Läs mer i [Skicka ett korrektur](steps-validating-the-delivery.md#sending-a-proof) och [Definiera ett specifikt korrekturmål](steps-defining-the-target-population.md#defining-a-specific-proof-target).

>[!IMPORTANT]
>
>De två stegen ovan MÅSTE utföras efter varje ändring av meddelandeinnehållet.

## Analysera leveransen {#analyzing-the-delivery}

Analysen är den fas då målpopulationen beräknas och leveransinnehållet färdigställs. När leveransen är klar kan den skickas.

### Starta analysen {#launching-the-analysis}

1. Klicka på **[!UICONTROL Send]** om du vill starta leveransanalysen.
1. Välj **[!UICONTROL Deliver as soon as possible]**.

   ![](assets/s_ncs_user_email_del_send.png)

1. Klicka på **[!UICONTROL Analyze]** om du vill starta analysen manuellt.

   Förloppsindikatorn visar analysförloppet.

   ![](assets/s_ncs_user_email_del_analyze_progress.png)

   >[!NOTE]
   >
   >Valideringsreglerna som används vid analysen beskrivs i avsnittet [Valideringsprocess med typologier](steps-validating-the-delivery.md#validation-process-with-typologies).

1. Du kan när som helst stoppa analysen genom att klicka på **[!UICONTROL Stop]**.

   ![](assets/s_ncs_user_wizard_email01_16.png)

   Inga meddelanden skickas under förberedelsefasen. Du kan därför påbörja eller avbryta analysen utan risk.

   >[!IMPORTANT]
   >
   >Vid körning fryser analysen leveransen (eller korrekturet). Alla ändringar av leveransen (eller beviset) måste följas av en annan analys innan de blir tillämpliga.

1. Vänta tills analysen är klar.

   När analysen är klar anger fönstrets övre del om leveransförberedelserna är slutförda eller om några fel har inträffat. Alla valideringssteg, varningar och fel visas. Färgade ikoner visar meddelandetypen:
   * Den blå ikonen visar ett informativt meddelande.
   * Den gula ikonen indikerar ett icke-kritiskt bearbetningsfel.
   * Den röda ikonen anger ett kritiskt fel som förhindrar leverans.

   ![](assets/s_ncs_user_email_del_analyze_error.png)

1. Klicka på **[!UICONTROL Close]** för att korrigera eventuella fel.

1. När du har gjort ändringarna startar du om analysen genom att klicka på **[!UICONTROL Analyze]**.

När du har kontrollerat resultatet av analysen kan du klicka på **[!UICONTROL Confirm delivery]** för att skicka meddelandet till det angivna målet. Med ett bekräftelsemeddelande kan du starta leveransen.

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>Klicka på länken **[!UICONTROL Change the main delivery target]** om antalet meddelanden som ska skickas inte matchar din konfiguration. På så sätt kan du ändra definitionen av målpopulationen och starta om analysen.

### Analysinställningar {#analysis-parameters}

På fliken **[!UICONTROL Analysis]** i leveransegenskaperna kan du definiera en uppsättning information om hur meddelanden ska förberedas under analysfasen.

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

På den här fliken finns följande alternativ:

* **[!UICONTROL Label and code of the delivery]** : Alternativen i detta avsnitt används för att beräkna värdena för dessa fält under leveransanalysfasen. Fältet **[!UICONTROL Compute the execution folder during the delivery analysis]** beräknar namnet på mappen som kommer att innehålla den här leveransåtgärden under analysfasen.
* **[!UICONTROL Approval mode]** : I det här fältet kan du definiera manuell eller automatisk leverans när analysen är klar. Valideringslägena visas i avsnittet [Ändra godkännandeläge](#changing-the-approval-mode).
* **[!UICONTROL Prepare the delivery parts in the database]** : Med det här alternativet kan du förbättra resultatet för leveransanalysen. Mer information finns i [det här avsnittet](#improving-delivery-analysis).
* **[!UICONTROL Prepare the personalization data with a workflow]** : Med det här alternativet kan du förbereda personaliseringsdata i leveransen i ett automatiskt arbetsflöde, vilket kan göra att du kan uppnå en avsevärd prestandaökning för personalisering. Mer information finns i [Optimera personalisering](personalization-fields.md#optimizing-personalization).
* **[!UICONTROL Start job in a detached process]** : Med det här alternativet kan du påbörja leveransanalysen i en separat process. Analysfunktionen använder som standard Adobe Campaign programserverprocess (webbserver). Om du väljer det här alternativet ser du till att analysen slutförs även om ett programserverfel inträffar.
* **[!UICONTROL Log SQL queries generated during the analysis in the journal]** : Med det här alternativet läggs SQL-frågeloggarna till i leveransjournalen under analysfasen.
* **[!UICONTROL Ignore personalization scripts during sending]** : Med det här alternativet kan du kringgå tolkningen av JavaScript-direktiv som finns i HTML-innehåll. De visas som i det levererade innehållet. Dessa direktiv introduceras med taggen **&lt;%=**).

### Förbättra resultatet av leveransanalysen {#improving-delivery-analysis}

Om du vill påskynda leveransförberedelsen kan du kontrollera **[!UICONTROL Prepare the delivery parts in the database]**-alternativet innan du startar analysen.

När det här alternativet är aktiverat utförs leveransförberedelsen direkt i databasen, vilket avsevärt kan snabba upp analysen.

För närvarande är det här alternativet endast tillgängligt när följande villkor är uppfyllda:
* Leveransen måste vara ett e-postmeddelande. De andra kanalerna stöds inte för tillfället.
* Du får inte använda medelstor eller extern routning, endast bulkleveransroutningstyp. Du kan kontrollera routningen som används på fliken **[!UICONTROL General]** i **[!UICONTROL Delivery properties]**.
* Du kan inte ange en målgrupp som kommer från en extern fil som mål. För en enskild leverans klickar du på länken **[!UICONTROL To]** i **[!UICONTROL Email parameters]** och kontrollerar att alternativet **[!UICONTROL Defined in the database]** är markerat. Kontrollera att mottagarna är **[!UICONTROL Specified by the inbound event(s)]** på fliken **[!UICONTROL Delivery]** för en leverans som används i ett arbetsflöde.
* Du måste använda en PostgreSQL-databas.

### Konfigurera analysprioriteten {#analysis-priority-}

När leveransen är en del av en kampanj finns det ytterligare ett alternativ på fliken **[!UICONTROL Advanced]**. På så sätt kan du ordna bearbetningsordningen för leveranser i samma kampanj.

Innan leveransen skickas analyseras varje leverans. Analysens längd beror på leveransens extraheringsfil. Ju större filstorlek, desto längre tid tar analysen och följande leveranser väntar.

Med alternativen för **[!UICONTROL Message preparation by the scheduler]** kan du prioritera leveransanalysen i ett kampanjarbetsflöde.

![](assets/delivery_analysis_priority.png)

Om en leverans är för stor är det bättre att tilldela den en låg prioritet för att undvika att analysen av andra arbetsflödesleveranser går långsammare.

>[!NOTE]
>
>Om du vill vara säker på att de större leveransanalyserna inte fördröjer arbetsflödena kan du schemalägga deras körningar genom att trycka på **[!UICONTROL Schedule execution for a time of low activity]**.

## Skicka ett bevis {#sending-a-proof}

För att upptäcka eventuella fel i meddelandekonfigurationen rekommenderar Adobe att du skapar en leveransvalideringscykel. Se till att innehållet godkänns så ofta som det behövs genom att skicka korrekturer till testmottagare. Ett korrektur ska skickas varje gång en ändring görs för att godkänna innehållet.

>[!NOTE]
>
>* Tillgängliga valideringslägen beskrivs i [Ändra godkännandeläge](steps-validating-the-delivery.md#changing-the-approval-mode).
>* Korrekturmålets konfiguration förklaras i [Definiera ett specifikt korrekturmål](steps-defining-the-target-population.md#defining-a-specific-proof-target).

>


Följ stegen nedan för att skicka ett bevis:

1. Kontrollera att korrekturmålet har konfigurerats enligt beskrivningen i [Definiera ett specifikt korrekturmål](steps-defining-the-target-population.md#defining-a-specific-proof-target).
1. Klicka på **[!UICONTROL Send a proof]** i det övre fältet i leveransguiden.

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. Starta meddelandeanalys. Se [Analysera leveransen](steps-validating-the-delivery.md#analyzing-the-delivery).
1. Du kan nu skicka leveransen (se [Skicka leveransen](steps-sending-the-delivery.md)).

   När leveransen är skickad visas korrekturet i leveranslistan och skapas och numreras automatiskt. Den kan redigeras om du vill komma åt dess innehåll och egenskaper. Se denna [sida](about-delivery-monitoring.md) för mer information om detta.

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >Om flera format har skapats för leveransen (HTML och Text) kan du välja formatet för de meddelanden som ska skickas till korrekturmottagarna i fönstrets nedre del.

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

Du kanske vill ändra innehållet i leveransen som ett resultat av kommentarer som gjorts av den valideringsgrupp som tar emot korrekturet. När du har gjort ändringarna måste du starta om analysen och sedan skicka ett nytt bevis. Varje nytt korrektur numreras och loggas i leveransjournalen.

När leveransen har analyserats kan du visa de olika korrektur som skickats via underfliken **[!UICONTROL Proofs]** i loggen (**[!UICONTROL Audit]**-fliken).

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

Du måste skicka så många korrektur som behövs tills innehållet i leveransen är klart. Efter det kan du skicka leveransen till huvudmålet och stänga valideringscykeln.

På fliken **[!UICONTROL Advanced]** i leveransegenskaperna kan du definiera egenskaperna för korrekturet. Vid behov kan du åsidosätta reglerna för uteslutning av mottagare.

![](assets/s_ncs_user_wizard_email01_145.png)

Följande alternativ är tillgängliga:

* Det första alternativet gör att du kan behålla korrekturet dubblerar.
* Med båda av följande alternativ kan du hålla mottagare som är på blockeringslista och adresser i karantän. Se beskrivningen av dessa alternativ för huvudmålet i [Anpassa undantagsinställningar](steps-defining-the-target-population.md#customizing-exclusion-settings). Till skillnad från målet för en leverans, där dessa adresser exkluderas som standard, behålls de som standard som mål för ett korrektur.
* Med alternativet **[!UICONTROL Keep the delivery code for the proof]** kan du ge korrekturet samma leveranskod som den som har definierats för den leverans som det hör till. Den här koden anges i det första steget i leveransguiden.
* Som standard anges korrekturens ämne med &quot;Korrekturnr&quot;, där # är korrekturets nummer. Du kan ändra det här prefixet i fältet **[!UICONTROL Label prefix]**.

## Valideringsprocess med typologier {#validation-process-with-typologies}

Innan du skickar meddelanden bör du analysera kampanjen för att godkänna dess innehåll och konfiguration. Kontrollreglerna som tillämpas under analysfasen definieras i en **typologi**. Som standard täcker analysen följande punkter för e-post:

* Godkänna objektet
* Godkänna URL:er och bilder
* Godkänna URL-etiketterna
* Godkänn länken för avprenumeration
* Kontrollera storleken på korrektur
* Kontrollera giltighetsperioden
* Kontrollera schemaläggning av vågor

Typologin som ska användas för varje leverans väljs på fliken **[!UICONTROL Typologies]** i leveransparametrarna.

Du kan visa och redigera godkännandereglerna, deras innehåll, deras körningsordning och deras fullständiga beskrivning via noden **[!UICONTROL Administration > Campaign execution > Typology management > Typology rules]**.

Du kan skapa nya regler och definiera nya typologier från den här noden. Dessa uppgifter är dock reserverade för expertanvändare som kan JavaScript.

Mer information om typologiregler finns på [den här sidan](../../campaign-opt/using/about-campaign-typologies.md).

Om du vill redigera den aktuella typologin klickar du på ikonen **[!UICONTROL Edit link]** till höger om fältet **[!UICONTROL Typology]**.

![](assets/s_ncs_user_email_del_typo_tab.png)

Fliken **[!UICONTROL Rule]** innehåller en lista med de typologiregler som ska användas. Markera en regel och klicka på ikonen **[!UICONTROL Detail...]** för att visa dess konfiguration:

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>**[!UICONTROL Arbitration]** typologier används inom ramen för hantering av försäljningstryck. Mer information om detta finns i [det här avsnittet](../../mrm/using/about-marketing-resource-management.md).

## Ändra godkännandeläge {#changing-the-approval-mode}

På fliken **[!UICONTROL Analysis]** för leveransegenskaper kan du välja valideringsläge. Om varningar genereras under analysen (t.ex. om vissa tecken framhävs i leveransämnet osv.) kan du konfigurera leveransen för att definiera om den fortfarande ska köras eller inte. Som standard måste användaren bekräfta att meddelanden skickas i slutet av analysfasen: detta är **manuell** validering.

Välj ett annat godkännandeläge i listrutan i lämpligt fält.

![](assets/s_ncs_user_email_del_validation_mode.png)

Följande godkännandelägen är tillgängliga:

* **[!UICONTROL Manual]**: I slutet av analysfasen måste användaren bekräfta leveransen för att kunna börja skicka. Det gör du genom att klicka på knappen **[!UICONTROL Start]** för att starta leveransen.
* **[!UICONTROL Semi-automatic]**: Skicka börjar automatiskt om analysfasen inte genererar några varningsmeddelanden.
* **[!UICONTROL Automatic]**: Sändningen börjar automatiskt i slutet av analysfasen, oavsett resultatet.
