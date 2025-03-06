---
product: campaign
title: Bygg ett arbetsflöde
description: Lär dig skapa ett arbetsflöde
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 8ba20ccd-b03f-4c4f-87c1-a21e80d8e4be
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1624'
ht-degree: 0%

---

# Bygg ett arbetsflöde {#building-a-workflow}



I det här avsnittet beskrivs de viktigaste principerna och de bästa metoderna för att skapa ett arbetsflöde i Campaign.

* Skapa ett arbetsflöde, se [Skapa ett nytt arbetsflöde](#creating-a-new-workflow)
* Utforma arbetsflödesdiagrammet, se [Lägga till och länka aktiviteter](#adding-and-linking-activities)
* Åtkomstparametrar och aktivitetsegenskaper, se [Konfigurera aktiviteter](#configuring-activities)
* Designa arbetsflöden för målinriktning, se [Målarbetsflöden](#targeting-workflows)
* Använd arbetsflöden för att köra en kampanj, se [Kampanjarbetsflöden](#campaign-workflows)
* Få åtkomst till och skapa tekniska arbetsflöden, se [Tekniska arbetsflöden](#technical-workflows)
* Använd mallar för att skapa arbetsflöden, se [Arbetsflödesmallar](#workflow-templates)

## Skapa ett nytt arbetsflöde {#creating-a-new-workflow}

Öppna en arbetsflödesmapp från **[!UICONTROL Explorer]**. Som standard kan du använda **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.

Klicka på knappen **[!UICONTROL New]** ovanför listan med arbetsflöden.

![](assets/create_a_wf_icon.png)

Du kan också använda knappen **[!UICONTROL Create]** i arbetsflödesöversikten (**[!UICONTROL Monitoring]** > länken **[!UICONTROL Workflow]**).

![](assets/create_a_wf.png)

Ange en etikett och klicka på **[!UICONTROL Save]**.

>[!NOTE]
>
>När du ändrar det interna namnet på en arbetsflödesaktivitet eller själva arbetsflödet måste du spara arbetsflödet innan du stänger det, så att det nya interna namnet beaktas korrekt.

## Lägg till och länka aktiviteter {#adding-and-linking-activities}

Du måste nu definiera de olika aktiviteterna och länka samman dem i diagrammet. I det här skedet av konfigurationen kan vi se diagrametiketten och arbetsflödesstatusen (Redigering pågår). Fönstrets nedre del används endast för att redigera diagrammet. Den innehåller ett verktygsfält, en palett med aktiviteter (till vänster) och själva diagrammet (till höger).

![](assets/new-workflow-2.png)

>[!NOTE]
>
>Om paletten inte visas klickar du på den första knappen i verktygsfältet för att visa den.

Aktiviteter grupperas efter kategori på palettens olika flikar. Tillgängliga flikar och aktiviteter kan variera beroende på arbetsflödestyp (teknik, målgruppsanpassning eller kampanjarbetsflöde).

* Den första fliken innehåller målgrupps- och datahanteringsaktiviteter. Dessa aktiviteter beskrivs i [Målaktiviteter](about-targeting-activities.md).
* På den andra fliken finns schemaläggningsaktiviteter, som huvudsakligen används för att samordna andra aktiviteter. De här aktiviteterna beskrivs i [Flödeskontrollaktiviteter](about-flow-control-activities.md).
* Den tredje fliken innehåller verktyg och åtgärder som kan användas i arbetsflödet. De här aktiviteterna beskrivs i [Åtgärdsaktiviteter](about-action-activities.md).
* Den fjärde fliken innehåller aktiviteter som är beroende av en viss händelse, till exempel att ett e-postmeddelande tas emot eller att en fil tas emot på en server. De här aktiviteterna beskrivs i [Händelseaktiviteter](about-event-activities.md).

Skapa diagrammet

1. Lägg till en aktivitet genom att markera den på paletten och flytta den till diagrammet med dra-och-släpp-funktionen.

   Lägg till en **Start**-aktivitet och sedan en **Delivery**-aktivitet i diagrammet.

   ![](assets/new-workflow-3.png)

1. Länka samman aktiviteterna genom att dra aktivitetsövergången **Start** och släppa den på aktiviteten **Leverans**.

   ![](assets/new-workflow-4.png)

   Du kan automatiskt länka en aktivitet till den föregående genom att placera den nya aktiviteten i slutet av övergången.

1. Lägg till de aktiviteter du behöver och länka ihop dem enligt bilden nedan.

   ![](assets/new-workflow-5.png)

>[!CAUTION]
>
>Du kan kopiera och klistra in aktiviteter i samma arbetsflöde. Vi rekommenderar dock inte att du kopierar inklistringsaktiviteter i olika arbetsflöden. Vissa inställningar som är kopplade till aktiviteter som Leveranser och Schemaläggare kan leda till konflikter och fel när målarbetsflödet körs. Vi rekommenderar i stället att du **duplicerar** arbetsflöden. Mer information finns i [Duplicera arbetsflöden](#duplicating-workflows).

Du kan ändra visning och layout för diagrammet med följande element:

* **Använd verktygsfältet**

  Verktygsfältet för diagramredigering ger dig tillgång till arbetsflödets layout- och körningsfunktioner.

  ![](assets/s_user_segmentation_wizard_10.png)

  På så sätt kan du anpassa layouten för redigeringsverktyget: hur paletten visas och översikten, storleken och justeringen av grafiska objekt.

  ![](assets/s_user_segmentation_toolbar.png)

  Ikoner för förlopp och visning av loggar beskrivs i följande avsnitt:

   * [Visa förlopp](../../workflow/using/monitoring-workflow-execution.md#displaying-progress)
   * [Visa loggar](../../workflow/using/monitoring-workflow-execution.md#displaying-logs)

* **Objektjustering**

  Om du vill justera ikoner markerar du dem och klickar på ikonen **[!UICONTROL Align vertically]** eller **[!UICONTROL Align horizontally]** .

  Använd nyckeln **CTRL** för att markera flera spridda aktiviteter eller för att avmarkera en eller flera aktiviteter. Klicka på diagrambakgrunden för att avmarkera allt.

* **Bildhantering**

  Du kan anpassa bakgrundsbilden för diagrammet samt de som hör till de olika aktiviteterna. Se [Ändra aktivitetsbilder](managing-activity-images.md).

## Konfigurera aktiviteter {#configuring-activities}

Dubbelklicka på en aktivitet för att konfigurera den eller högerklicka och välj **[!UICONTROL Open...]**.

>[!NOTE]
>
>Kampanjarbetsflödesaktiviteter beskrivs i [det här avsnittet](about-activities.md).

Den första fliken innehåller den grundläggande konfigurationen. Fliken **[!UICONTROL Advanced]** innehåller ytterligare parametrar, som används särskilt för att definiera beteenden när ett fel påträffas, ange körningstid för en aktivitet och för att ange ett initieringsskript.

För att få en bättre förståelse för aktiviteterna och för att arbetsflödet ska bli mer lättläst kan du ange kommentarer i aktiviteterna: dessa visas automatiskt när operatorer rullar över aktiviteten.

![](assets/example1-comment.png)

## Målarbetsflöden {#targeting-workflows}

Med målarbetsflöden kan du skapa flera leveransmål. Du kan skapa frågor, definiera fackföreningar eller undantag baserat på specifika villkor, lägga till schemaläggning tack vare arbetsflödesaktiviteter. Resultatet av den här målsättningen kan automatiskt överföras till en lista som kan fungera som mål för leveransåtgärder

Förutom dessa aktiviteter kan du med alternativen för datahantering hantera data och komma åt avancerade funktioner för att tillgodose komplexa målgruppsproblem. Mer information finns i [Datahantering](targeting-data.md#data-management).

Alla dessa aktiviteter finns på den första arbetsflödesfliken.

>[!NOTE]
>
>Målinriktade aktiviteter beskrivs i [det här avsnittet](about-activities.md).

Målarbetsflöden kan skapas och redigeras via noden **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** i Adobe Campaign-trädet eller via hemsidans **[!UICONTROL Profiles and Targets > Targeting workflows]**-meny.

![](assets/target_wf.png)

Målarbetsflöden inom ramen för en kampanj lagras med alla kampanjarbetsflöden.

### Viktiga steg för att skapa ett målarbetsflöde {#implementation-steps-}

Steg för att skapa ett arbetsflöde för målinriktning finns i följande avsnitt:

1. **Identifiera**-data i databasen - Se [Skapa frågor](targeting-data.md#creating-queries)
1. **Förbered**-data för leverans - Se [Förbättra och ändra data](targeting-data.md#enriching-and-modifying-data)
1. **Använd**-data för att utföra uppdateringar eller inom en leverans - Se [Uppdatera databasen](how-to-use-workflow-data.md#updating-the-database)

Resultaten av alla berikningar och all hantering som utförs under målgruppsanpassningen lagras och är tillgängliga i personaliseringsfält, särskilt för användning när personaliserade meddelanden skapas. Mer information finns i [Måldata](data-life-cycle.md#target-data)

### Målinriktning och filtrering {#targeting-and-filtering-dimensions}

Vid datasegmenteringsåtgärder mappas målnyckeln till en filtreringsdimension. Med målinriktningsdimensionen kan du definiera målgruppen för operationen: mottagare, mottagare, operatör, prenumeranter osv. Med filtreringsdimensionen kan du välja populationen baserat på vissa kriterier: avtalsägare, nyhetsbrevets prenumeranter osv.

Om du till exempel vill välja klienter som har haft en livförsäkring i över 5 år, väljer du följande måldimension: **Klienter** och följande filtreringsdimension: **Kontraktsinnehavare**. Du kan sedan definiera filtervillkoren i frågeaktiviteten

Under måldimensionens urvalsfas finns endast kompatibla filtreringsdimensioner i gränssnittet.

Dessa två dimensioner måste vara relaterade. Innehållet i listan **[!UICONTROL Filtering dimension]** beror alltså på måldimensionen som anges i det första fältet.

För mottagare (**mottagare**) är följande filtreringsdimensioner tillgängliga:

![](assets/query_filter_target_dimensions_1.png)

I **Webbprogram** kommer listan att innehålla följande filtreringsdimensioner:

![](assets/query_filter_target_dimensions_2.png)

## Kampanjarbetsflöden {#campaign-workflows}

För varje kampanj kan du skapa arbetsflöden som ska köras från fliken **[!UICONTROL Targeting and workflows]**. Dessa arbetsflöden är specifika för kampanjen.

![](assets/wf-in-op-edit-delivery-tab.png)

Fliken innehåller samma aktiviteter som för alla arbetsflöden. [Läs mer](#implementation-steps-)

Förutom att rikta kampanjer kan ni med kampanjarbetsflöden skapa och konfigurera leveranser helt för alla tillgängliga kanaler. När leveransen har skapats i arbetsflödet är den tillgänglig från kontrollpanelen för kampanjen. [Läs mer](../../campaign/using/marketing-campaign-deliveries.md)

Alla kampanjarbetsflöden är centraliserade under noden **[!UICONTROL Administration > Production > Objects created automatically > Campaign workflows]**.

![](assets/campaigns_wf.png)

Kampanjarbetsflöden och implementeringsexempel finns på [den här sidan](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

## Tekniska arbetsflöden {#technical-workflows}

Tekniska arbetsflöden medföljer Adobe Campaign. De är åtgärder eller jobb som schemalagts för periodisk körning på servern. De gör att du kan utföra underhåll i databasen, vidarebefordra spårningsinformation om leveranser och konfigurera provisoriska processer för leveranser. Tekniska arbetsflöden konfigureras via noden **[!UICONTROL Administration > Production > Technical workflows]**.

![](assets/navtree.png)

Inbyggda mallar finns för att skapa tekniska arbetsflöden. De kan konfigureras så att de passar dina behov.

Undermappen **[!UICONTROL Campaign process]** centraliserar de arbetsflöden som krävs för att köra processer inom kampanjer: aktivitetsmeddelande, lagerhantering, kostnadsberäkning osv.

>[!NOTE]
>
>En lista över tekniska arbetsflöden som installeras med varje modul finns i ett [dedikerat avsnitt](about-technical-workflows.md).

Du kan skapa andra tekniska arbetsflöden i noden **[!UICONTROL Administration > Production > Technical workflows]** i trädstrukturen. Den här processen är dock reserverad för expertanvändare.

De aktiviteter som erbjuds är desamma som för arbetsflöden med målinriktning. [Läs mer](#implementation-steps-)

## Arbetsflödesmallar {#workflow-templates}

Arbetsflödesmallar innehåller den övergripande konfigurationen av egenskaper och eventuellt ett antal aktiviteter som sammanfogats i ett diagram. Den här konfigurationen kan återanvändas för att skapa nya arbetsflöden som innehåller ett visst antal förkonfigurerade element

Du kan skapa nya arbetsflödesmallar som baseras på befintliga mallar eller ändra ett arbetsflöde direkt till en mall.

Arbetsflödesmallar lagras i noden **[!UICONTROL Resources > Templates > Workflow templates]** i Adobe Campaign-trädet.

![](assets/s_advuser_wf_template_tree.png)

Förutom de vanliga arbetsflödesegenskaperna kan du med mallegenskaperna ange körningsfilen för arbetsflöden som skapas baserat på den här mallen.

![](assets/s_advuser_wf_template_properties.png)

## Duplicera arbetsflöden {#duplicating-workflows}

Du kan duplicera olika typer av arbetsflöden. När du har duplicerat arbetsflödet överförs inte ändringarna till kopian av arbetsflödet.

>[!CAUTION]
>
>Kopiera och klistra in är tillgängligt i arbetsflöden, men vi rekommenderar att du använder **Duplicera**. När en aktivitet har kopierats behålls hela dess konfiguration. För leveransaktiviteter (e-post, SMS, push-meddelanden..) kopieras även det leveransobjekt som är kopplat till aktiviteten, vilket kan orsaka krasch.

1. Högerklicka på ett arbetsflöde.
1. Klicka på **Duplicera**.

   ![](assets/duplicate-workflows.png)

1. Ändra arbetsflödesetiketten i arbetsflödesfönstret.
1. Klicka på **Spara**.

Dubblettfunktionen är inte direkt tillgänglig i kampanjvyn.

Men du kan skapa en vy som visar alla arbetsflöden i instansen. I den här vyn kan du duplicera arbetsflöden med **Duplicera till**.

**Skapa en vy**

1. I **Utforskaren** går du till den mapp du behöver för att skapa vyn i.
1. Högerklicka och gå till **Lägg till en ny mapp** > **Process**, välj **Arbetsflöden**.

   ![](assets/add-new-folder-workflows.png)

Den nya mappen **Arbetsflöden** skapas.

1. Högerklicka och välj **Egenskaper**.
1. I **Begränsning** kontrollerar du att mappen är en vy **och klickar på** Spara **.**

   ![](assets/folder-is-a-view.png)

Mappen innehåller nu alla arbetsflöden för din instans.

**Duplicera ett kampanjarbetsflöde**

1. Välj ett kampanjarbetsflöde i arbetsflödesvyn.
1. Högerklicka på **Duplicera till**.
   ![](assets/duplicate-to-right-click.png)
1. Ändra etiketten.
1. Klicka på **Spara**.

Du kan se det duplicerade arbetsflödet i arbetsflödesvyn.
