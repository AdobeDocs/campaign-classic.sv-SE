---
product: campaign
title: Mallar för marknadsföringskampanjer
description: Mallar för marknadsföringskampanjer
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Campaigns, Templates
exl-id: d272d4b9-f1b2-4fb2-9ed9-91a4aea7eca3
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 0%

---

# Skapa och konfigurera kampanjmallar {#campaign-templates}

Alla marknadsföringskampanjer bygger på en mall som lagrar de viktigaste egenskaperna och funktionerna. Kampanjmallar är centraliserade i **[!UICONTROL Resources > Templates > Campaign templates]** nod. En standardmall anges som standard. Du kan skapa en ny kampanj med hjälp av alla tillgängliga moduler (dokument, uppgifter, dirigerade adresser osv.), men vilka moduler som erbjuds beror på dina rättigheter och konfigurationen av din Adobe Campaign-plattform.

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>Trädet visas när du klickar på **[!UICONTROL Explorer]** på startsidan.

En inbyggd mall tillhandahålls för att skapa en kampanj för vilken ingen specifik konfiguration har definierats. Du kan skapa och konfigurera kampanjmallar och sedan skapa kampanjer utifrån dessa mallar.

![](assets/do-not-localize/how-to-video.png) Mer information om hur du skapar kampanjer finns i [den här videon](../../campaign/using/marketing-campaign-deliveries.md#create-email-video).

## Skapa en kampanjmall {#creating-or-duplicating-a-campaign-template}

Så här skapar du en kampanjmall:

1. Öppna kampanj **Utforskaren**.
1. I **Resurser > Mallar > Campaign-mallar**, klicka **Nytt** i verktygsfältet ovanför listan med mallar.

   ![](assets/create_campaign_template_1.png)

1. Ange etiketten för den nya kampanjmallen.
1. Klicka **Spara** och öppna mallen igen.
1. I **Redigera** -fliken anger du **Internt namn** och andra värden, om det behövs.
1. Välj **Avancerade kampanjinställningar** för att lägga till ett arbetsflöde i kampanjmallen.

   ![](assets/create_campaign_template_2.png)

1. Ändra **Målgruppsanpassning och arbetsflöden** värde till **Ja**.

   ![](assets/create_campaign_template_3.png)

1. I **Målgruppsanpassning och arbetsflöden** flik, klicka **Lägg till ett arbetsflöde..**.

   ![](assets/create_campaign_template_4.png)

1. Slutför **Etikett** fält och klicka **OK**.
1. Skapa ett arbetsflöde som passar dina behov.
1. Klicka **Spara**. Mallen kan nu användas i en kampanj.

Du kan också **duplicera** standardmallen för återanvändning och anpassning av dess konfiguration.

På de olika flikarna och underflikarna i kampanjmallen kan du komma åt inställningarna som beskrivs i [Allmän konfiguration](#general-configuration).

![](assets/s_ncs_user_new_op_template_duplicate.png)

## Välj moduler {#select-modules}

The **[!UICONTROL Advanced campaign settings...]** kan du aktivera och inaktivera jobb för kampanjer som är baserade på den här mallen. Välj de funktioner som du vill aktivera i kampanjer som skapas baserat på den här mallen.

![](assets/s_ncs_user_op_template_tab1.3.png)

Om en funktion inte har valts, de element som rör processen (menyer, ikoner, alternativ, flikar, underflikar osv.) visas inte i mallens gränssnitt eller i kampanjer som är baserade på den här mallen. Flikarna till vänster om kampanjinformationen sammanfaller vanligtvis med de processer som valts i mallen. Om **Utgifter och mål** är inte markerat, motsvarar **[!UICONTROL Budget]** -fliken visas inte i kampanjer som baseras på den här mallen.

Dessutom läggs genvägar till konfigurationsfönstren till på kontrollpanelen för kampanjer. När en funktion är aktiverad får en direktlänk åtkomst till den från kontrollpanelen för kampanjer.

Med konfigurationen nedan:

![](assets/s_ncs_user_op_template_tab1.4.png)

Följande länkar visas på kontrollpanelen för kampanjer ( **[!UICONTROL Add a task]** länk saknas):

![](assets/s_ncs_user_op_template_tab1.3ex.png)

Bara följande flikar visas:

![](assets/s_ncs_user_op_template_tab1.4ex.png)

Men med den här typen av konfiguration:

![](assets/s_ncs_user_op_template_tab2.2ex.png)

Följande länkar och flikar visas:

![](assets/s_ncs_user_op_template_tab2.3ex.png)

## Modultyper {#typology-of-enabled-modules}

* **Kontrollgrupp**

   När den här modulen är markerad läggs en extra flik till i de avancerade inställningarna för mallen och kampanjerna som är baserade på den här mallen. Konfigurationen kan definieras via mallen eller individuellt för varje kampanj. Läs mer om kontrollgrupper i [det här avsnittet](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

   ![](assets/s_ncs_user_op_template_activate_1.png)

* **Fröadresser**

   När den här modulen är markerad läggs en extra flik till i de avancerade inställningarna för mallen och kampanjerna som är baserade på den här mallen. Konfigurationen kan definieras via mallen eller individuellt för varje kampanj. Läs mer om dirigerade adresser i [det här avsnittet](../../delivery/using/about-seed-addresses.md).

   ![](assets/s_ncs_user_op_template_activate_2.png)

* **Dokument**

   När den här modulen är markerad läggs en extra flik till i **[!UICONTROL Edition]** -fliken i mallen och de kampanjer som är baserade på den här mallen. Bifogade dokument kan läggas till från mallen eller individuellt för varje kampanj. Läs mer om dokument i [det här avsnittet](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents).

   ![](assets/s_ncs_user_op_template_activate_3.png)

* **Kontur**

   När den här modulen är markerad **[!UICONTROL Delivery outlines]** underfliken läggs till i **[!UICONTROL Documents]** för att definiera leveransdispositioner för kampanjen. Läs mer om leveransdispositioner i [det här avsnittet](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

   ![](assets/s_ncs_user_op_template_activate_4.png)

* **Målgruppsanpassning och arbetsflöden**

   När du väljer **[!UICONTROL Targeting and workflows]** -modulen läggs en flik till så att du kan skapa ett eller flera arbetsflöden för kampanjer baserat på den här mallen. Arbetsflöden kan också konfigureras individuellt för varje kampanj baserat på den här mallen.Läs mer om kampanjarbetsflöden i [det här avsnittet](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

   ![](assets/s_ncs_user_op_template_activate_5.png)

   När den här modulen är aktiverad läggs en flik till i de avancerade inställningarna för kampanjen för att definiera processkörningssekvensen.

   ![](assets/s_ncs_user_op_template_activate_5a.png)

* **Godkännande**

   Om du väljer **[!UICONTROL Approval]** kan du välja vilka processer som ska godkännas och vilka operatörer som ansvarar för godkännandena. Läs mer om godkännanden i [det här avsnittet](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

   ![](assets/s_ncs_user_op_template_activate_5b.png)

   Du kan välja om du vill aktivera processgodkännande via **[!UICONTROL Approvals]** -fliken i avsnittet för mallar med avancerade inställningar. Jobb som har valts för godkännande måste godkännas för att meddelandeleverans ska kunna auktoriseras.

   Du måste associera en granskaroperator eller grupp av operatorer för varje aktiverat godkännande.

* **Utgifter och mål**

   När den här modulen är markerad **[!UICONTROL Budget]** -fliken läggs till i informationen om mallen och kampanjer som baseras på den här mallen, så att den associerade budgeten kan väljas.

   ![](assets/s_ncs_user_op_template_activate_7.png)

## Egenskaper och körning {#general-configuration}

### Mallegenskaper {#template-properties}

![](assets/s_ncs_user_op_new_template.png)

När du skapar en kampanjmall måste du ange följande information:

* Ange **label** av mallen: Den här etiketten tilldelas som standard till alla kampanjer som skapas via den här mallen.
* Välj kampanj **natur** i listrutan. De värden som är tillgängliga i den här listan är de som har sparats i **[!UICONTROL natureOp]** uppräkning.

   >[!NOTE]
   >
   >Mer information om uppräkningar finns i [Komma igång](../../platform/using/managing-enumerations.md) -avsnitt.

* Välj **kampanjtyp**: unika, återkommande eller periodiska. Som standard används kampanjmallar för unika kampanjer. Återkommande och periodiska kampanjer beskrivs i [det här avsnittet](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns).
* Ange kampanjens varaktighet, dvs. antalet dagar som kampanjen ska äga rum. När du skapar en kampanj som baseras på den här mallen fylls start- och slutdatumet för kampanjen i automatiskt.

   Om kampanjen är återkommande måste du ange kampanjens start- och slutdatum direkt i mallen.

* Ange **relaterat program** av mallen: kampanjer som är baserade på den här mallen länkas till det valda programmet.

### Parametrar för mallkörning {#template-execution-parameters}

The **[!UICONTROL Advanced campaign settings...]** kan du konfigurera de avancerade alternativen för mallen för bearbetning av leveransmålet (kontrollgrupp, dirigeringsadresser osv.) och konfigurationen av kampanjmätning och arbetsflödeskörning.

![](assets/s_ncs_user_op_template_tab1.2.png)

## Spåra kampanjkörning{#campaign-reverse-scheduling}

Du kan skapa ett schema för en kampanj och spåra resultat, till exempel för att förbereda ett händelseschema för ett visst datum. Med kampanjmallar kan du nu beräkna startdatumet för en aktivitet baserat på slutdatumet för en kampanj.

Gå till dialogrutan Uppgiftskonfiguration **[!UICONTROL Implementation schedule]** området och kontrollera **[!UICONTROL The start date is calculated based on the campaign end date]** box. (Här är &quot;startdatum&quot; startdatum för aktiviteten). Gå till **[!UICONTROL Start]** och ange ett intervall: aktiviteten startar så här långt före kampanjens slutdatum. Om du anger en period som är längre än kampanjen är inställd på att vara sista, börjar aktiviteten före kampanjen.

![](assets/mrm_task_in_template_start_date.png)

När du skapar en kampanj med den här mallen beräknas startdatumet för aktiviteten automatiskt. Du kan dock ändra den senare.
