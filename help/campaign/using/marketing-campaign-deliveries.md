---
product: campaign
title: Leveranser av marknadsföringskampanjer
description: Läs mer om kampanjleveranser
role: User
feature: Campaigns, Resource Management, Cross Channel Orchestration
hide: true
hidefromtoc: true
exl-id: 1dd3c080-444d-45f8-9562-d2d01a9d2860
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '1491'
ht-degree: 0%

---

# Leveranser av marknadsföringskampanjer {#marketing-campaign-deliveries}

Leveranser kan skapas via kampanjkontrollpanelen, ett kampanjarbetsflöde eller direkt via leveransöversikten.

När leveranser skapas från en kampanj länkas de till den här kampanjen och konsolideras på kampanjnivå.

![](assets/do-not-localize/how-to-video.png)[Upptäck den här funktionen i videon](#create-email-video)

## Skapa leveranser {#creating-deliveries}

Om du vill skapa en leverans som är länkad till en kampanj klickar du på länken **[!UICONTROL Add a delivery]** på kontrollpanelen för kampanjer.

![](assets/campaign_op_add_delivery.png)

De föreslagna konfigurationerna passar för de olika typerna av leverans: direktreklam, e-post, mobilkanaler. Läs mer i [Campaign v8-dokumentationen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html){target="_blank"}.

## Starta en leverans {#starting-a-delivery}

När alla godkännanden har beviljats är leveransen klar att startas. Leveransproceduren beror sedan på typen av leverans. Information om leveranser via e-post eller mobilkanal finns i [Starta en onlineleverans](#starting-an-online-delivery) och för leveranser via direktreklam, se [Starta en offlineleverans](#starting-an-offline-delivery).

### Starta en onlineleverans {#starting-an-online-delivery}

När alla godkännandebegäranden har beviljats ändras leveransstatusen till **[!UICONTROL Pending confirmation]** och kan startas av en operator. I tillämpliga fall meddelas den Adobe Campaign-operatör (eller grupp av operatörer) som utsetts till granskare för att påbörja leveransen att en leverans är klar att påbörjas.

>[!NOTE]
>
>Om en viss operator eller grupp av operatorer har utsetts för att starta en leverans i leveransegenskaperna, kan du även tillåta den operator som ansvarar för leveransen att bekräfta sändningen. Aktivera alternativet **NMS_ActivateOwnerConfirmation** genom att ange **1** som värde. Alternativen hanteras från noden **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** i Adobe Campaign Utforskaren.
>  
>Om du vill inaktivera det här alternativet anger du **0** som värde. Bekräftelseprocessen för att skicka kommer då att fungera som standard: endast den operator eller grupp av operatorer som har angetts för sändning i leveransegenskaperna (eller en administratör) kommer att kunna bekräfta och utföra sändningen.

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

Informationen visas också på kampanjkontrollpanelen. Med länken **[!UICONTROL Confirm delivery]** kan du påbörja leveransen.

![](assets/s_ncs_user_edit_del_to_start.png)

Med ett bekräftelsemeddelande kan du skydda den här åtgärden.

### Starta en offlineleverans {#starting-an-offline-delivery}

När alla godkännanden har beviljats ändras leveransstatusen till **[!UICONTROL Pending extraction]**. Extraheringsfilerna skapas med ett särskilt arbetsflöde som, i en standardkonfiguration, startar automatiskt när en direktleverans väntar på extrahering. När en process pågår visas den på kontrollpanelen och kan redigeras via länken.

>[!NOTE]
>
>De tekniska arbetsflödena för Campaign-paketet visas i [Lista över tekniska arbetsflöden](../../workflow/using/about-technical-workflows.md).

**Steg 1 - Godkännande av fil**

När extraheringsarbetsflödet har körts måste extraheringsfilen godkännas (förutsatt att godkännande av extraheringsfilen har valts i leveransinställningarna).

Mer information finns i [Godkänn en extraheringsfil](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file).

**Steg 2 - Godkännande av meddelandet till tjänstleverantören**

* När extraheringsfilen har godkänts kan du generera ett korrektur av routerns e-postmeddelande. Det här e-postmeddelandet är konstruerat baserat på en leveransmall. Det måste godkännas.

  >[!NOTE]
  >
  >Det här steget är bara tillgängligt om du har aktiverat sändning och godkännande av korrektur i godkännandefönstret.

![](assets/s_ncs_user_file_valid_select_BAT.png)


* Klicka på knappen **[!UICONTROL Send a proof]** för att skapa korrektur.

  Korrekturmålet måste definieras i förväg.

  Du kan skapa så många korrektur som behövs. Dessa nås via länken **[!UICONTROL Direct mail...]** i leveransinformationen.

  ![](assets/s_ncs_user_file_notif_submit_proof.png)

* Leveransstatusen ändras till **[!UICONTROL To submit]**. Klicka på knappen **[!UICONTROL Submit proofs]** för att starta godkännandeprocessen.

  ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* Leveransstatusen ändras till **[!UICONTROL Proof to validate]** och med en knapp kan du acceptera eller avvisa godkännande.

  ![](assets/s_ncs_user_file_notif_supplier_link.png)

  Du kan antingen godkänna eller avvisa det här godkännandet eller återgå till extraheringssteget.

  ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* Extraheringsfilen skickas till routern och leveransen är klar.

### Beräkning av kostnader och lager {#calculation-of-costs-and-stocks}

Filextraheringen startar två åtgärder: budgetberäkning och lagerberäkning. Budgetposterna uppdateras.

* På fliken **[!UICONTROL Budget]** kan du hantera budgeten för kampanjen. Summan av kostnadsposterna visas i fältet **[!UICONTROL Calculates cost]** på kampanjens huvudflik och det program som den tillhör. Beloppen återspeglas också i kampanjbudgeten.

  Den verkliga kostnaden kommer till slut att beräknas utifrån information som tillhandahålls av routern. Endast meddelanden som skickas faktureras.

* Stock definieras i noden **[!UICONTROL Administration > Campaign management > Stocks]** i trädet och kostnadsstrukturer i noden **[!UICONTROL Administration > Campaign management > Service providers]**.

  Lagerrader visas i lagersektionen. Om du vill definiera det ursprungliga lagret öppnar du en aktielinje. Lagret minskas varje gång en leverans sker. Du kan definiera en varningsnivå och meddelanden.

>[!NOTE]
>
>Mer information om kostnadsberäkningar och lagerhantering finns i [Leverantörer, stockar och budgetar](../../campaign/using/providers-stocks-and-budgets.md).

## Hantera associerade dokument {#managing-associated-documents}

Du kan associera olika dokument med en kampanj: rapport, foto, webbsida, diagram osv. Dessa dokument kan vara i vilket format som helst (Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF osv.). Lär dig hur du länkar dokument med en kampanj [i det här avsnittet](../../campaign/using/marketing-campaign-assets.md).

>[!IMPORTANT]
>
>Det här läget är reserverat för små dokument.

I en kampanj kan du även hänvisa till andra poster, t.ex. kampanjkuponger, specialerbjudanden för en viss gren eller butik. När dessa element ingår i en disposition kan de kopplas till en direktutskick. [Läs mer](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>Om du använder MRM kan du även hantera ett bibliotek med marknadsföringsresurser som är tillgängliga för flera deltagare för samarbete. Se [Hantera marknadsföringsresurser](../../mrm/using/managing-marketing-resources.md).

### Lägga till dokument {#adding-documents}

Dokument kan kopplas på kampanjnivå (sammanhangsberoende dokument) eller på programnivå (allmänna dokument).

Fliken **[!UICONTROL Documents]** innehåller:

* En förteckning över alla dokument som krävs för innehållet (mall, bilder osv.) och som kan laddas ned lokalt av Adobe Campaign-operatörer med lämpliga rättigheter.
* Dokument som innehåller information för routern, om sådan finns.

Dokumenten är länkade till programmet eller kampanjen via fliken **[!UICONTROL Edit > Documents]**.

![](assets/s_ncs_user_op_add_document.png)

Du kan också lägga till ett dokument i en kampanj via länken på kontrollpanelen.

![](assets/add_a_document_in_op.png)

Klicka på ikonen **[!UICONTROL Details]** om du vill visa innehållet i en fil och lägga till information:

![](assets/s_ncs_user_op_add_document_details.png)

I kontrollpanelen grupperas dokument som är kopplade till kampanjen i avsnittet **[!UICONTROL Document(s)]**, som i följande exempel:

![](assets/s_ncs_user_op_edit_document.png)

De kan också redigeras och ändras i den här vyn.

### Associera och strukturera resurser som är länkade via en leveransöversikt {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>Leveranskonturer används endast för direktreklamkampanjer.

En leveransöversikt anger en strukturerad uppsättning element (dokument, filialer/butiker, kampanjkuponger osv.) som har skapats i företaget och för en viss kampanj.

Dessa element grupperas i leveranskonturer och en viss leveransdisposition kopplas till en leverans. Den refereras till i extraheringsfilen som skickas till **tjänstleverantören** för att kunna kopplas till leveransen. Du kan till exempel skapa en leveransdisposition som refererar till en gren och de marknadsföringsbroschyrer som används i den.

För en kampanj kan du strukturera externa element som ska kopplas till leveransen enligt vissa kriterier: relaterad gren, kampanjerbjudande, inbjudan till en lokal händelse osv.

#### Skapa en disposition {#creating-an-outline}

Om du vill skapa en disposition klickar du på underfliken **[!UICONTROL Delivery outlines]** på fliken **[!UICONTROL Edit > Documents]** i den aktuella kampanjen.

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

* Resurserna är marknadsföringsresurser som genereras i kontrollpanelen för marknadsföringsresurser som nås via länken **[!UICONTROL Resources]** på fliken **[!UICONTROL Campaigns]**.

  ![](assets/s_ncs_user_mkg_resource_ovv.png)

  >[!NOTE]
  >
  >Mer information om marknadsföringsresurser finns i [Hantera marknadsföringsresurser](../../mrm/using/managing-marketing-resources.md).

#### Markera en kontur {#selecting-an-outline}

För varje leverans kan du välja den disposition som ska kopplas från det avsnitt som är reserverat för extraheringsdispositionen, som i följande exempel:

![](assets/s_ncs_user_op_select_composition.png)

Den markerade dispositionen visas sedan i fönstrets nedre del. Du kan redigera den med ikonen till höger om fältet eller ändra den med hjälp av listrutan:

![](assets/s_ncs_user_op_select_composition_b.png)

På fliken **[!UICONTROL Summary]** i leveransen visas även den här informationen:

![](assets/s_ncs_user_op_select_composition_c.png)

#### Extraheringsresultat {#extraction-result}

I den fil som extraheras och skickas till tjänsteleverantören läggs namnet på dispositionen och, i tillämpliga fall, dess egenskaper (kostnad, beskrivning osv.) till i innehållet enligt informationen i den exportmall som är associerad med tjänsteleverantören.

I följande exempel läggs etiketten, den uppskattade kostnaden och beskrivningen av dispositionen som är kopplad till leveransen till i extraheringsfilen.

![](assets/s_ncs_user_op_composition_in_export_template.png)

Exportmodellen måste vara kopplad till den tjänsteleverantör som valts för den aktuella leveransen. Se [Skapa tjänsteleverantörer och deras kostnadsstrukturer](../../campaign/using/providers-stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>Mer information om export finns i avsnittet [Komma igång](../../platform/using/get-started-data-import-export.md).

#### Självstudievideo {#create-email-video}

I den här videon förklaras hur du skapar en kampanj och ett e-postmeddelande i Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

Ytterligare utbildningsvideor för Campaign är tillgängliga [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
