---
product: campaign
title: Integrera ett erbjudande via ett arbetsflöde
description: Integrera ett erbjudande via ett arbetsflöde
feature: Interaction, Offers, Workflows
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
exl-id: 33d318f3-1eb4-4c74-8c20-8b9f0442c7c3
source-git-commit: de9ff0b50d819038c97e8515ddb7d6cfeb4547a1
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 1%

---

# Integrera ett erbjudande via ett arbetsflöde{#integrating-an-offer-via-a-workflow}



Förutom själva leveransaktiviteten kan du definiera hur erbjudandena presenteras i flera arbetsflödesaktiviteter:

* Leveransbeskrivning
* Berikning
* Erbjudandemotor
* Erbjudanden per cell

## Leveransbeskrivning {#delivery-outline}

Med aktiviteten för leveransdisposition, som är tillgänglig i kampanjarbetsflödena, kan du presentera erbjudanden som refereras i en leveransdisposition från den pågående kampanjen.

1. Lägg till en dispositionsaktivitet för leverans i ett arbetsflöde innan du lägger till en leveransaktivitet.
1. I dispositionsaktiviteten för leverans anger du den disposition du vill använda.

   Mer information om hur du anger leveransdispositioner finns i guiden [Kampanj - MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Fyll i de tillgängliga fälten efter leverans.
1. Det finns två möjliga fall:

   * Om du vill ringa erbjudandemotorn markerar du kryssrutan **[!UICONTROL Restrict the number of propositions selected]**. Ange erbjudandeutrymme och antalet offerter som ska presenteras i leveransen.

     Anbudsvikterna och reglerna för rätt till uppgradering kommer att beaktas av erbjudandemotorn.

   * Om du inte markerar kryssrutan visas alla erbjudanden i leveransdispositionen utan att du behöver ringa till erbjudandemotorn.

   >[!NOTE]
   >
   >Förhandsgranskningen tar hänsyn till antalet erbjudanden som anges i leveransen. När du kör ett arbetsflöde är det numret som anges i leveransdispositionen som beaktas.

   ![](assets/int_compo_offre_wf1.png)

## Berikning {#enrichment}

Med anrikningsaktiviteten kan du lägga till erbjudanden eller länkar till erbjudanden för mottagare.

>[!NOTE]
>
>Mer information om anrikningsaktiviteten finns i den dedikerade dokumentationen i [handboken för arbetsflöden](../../workflow/using/enrichment.md).

Du kan till exempel förbättra data för en mottagarfråga före en leverans.

![](assets/int_enrichment_offer1.png)

Det finns två metoder för att ange erbjudandeförslag.

* Ange ett erbjudande eller ett erbjudande.
* Referera till en länk till ett erbjudande.

### Ange ett erbjudande eller ett samtal till erbjudandemotorn {#specifying-an-offer-or-a-call-to-the-offer-engine}

När du har konfigurerat frågan (se [Handboken för arbetsflöden](../../workflow/using/query.md)):

1. Lägg till och öppna en anrikningsaktivitet.
1. Välj **[!UICONTROL Add data]** på fliken **[!UICONTROL Enrichment]**.
1. Välj **[!UICONTROL An offer proposition]** i de datatyper som ska läggas till.

   ![](assets/int_enrichment_offer2.png)

1. Ange en identifierare och en etikett för det förslag som ska läggas till.
1. Ange erbjudandevalet. Det finns två möjliga alternativ:

   * **[!UICONTROL Search for the best offer in a category]** : Markera det här alternativet och ange parametrarna för uppringning av erbjudandemotor (erbjudandeutrymme, kategori eller tema, kontaktdatum, antal erbjudanden som ska behållas). Motorn beräknar automatiskt erbjudandena som ska läggas till enligt dessa parametrar. Vi rekommenderar att du fyller i antingen **[!UICONTROL Category]** eller **[!UICONTROL Theme]**-fältet i stället för båda samtidigt.

     ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]** : Markera det här alternativet och ange ett erbjudandeutrymme, ett specifikt erbjudande och ett kontaktdatum för att direkt konfigurera det erbjudande du vill lägga till, utan att anropa erbjudandemotorn.

     ![](assets/int_enrichment_offer4.png)

1. Konfigurera sedan en leveransaktivitet som motsvarar den valda kanalen. Mer information finns i avsnittet [Infoga ett erbjudande i ett leveransavsnitt](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery).

   >[!NOTE]
   >
   >Antalet tillgängliga offerter för förhandsgranskningen beror på konfigurationen som utförs i anrikningsaktiviteten snarare än eventuell konfiguration som utförs direkt i leveransen.

### Referera till en länk till ett erbjudande {#referencing-a-link-to-an-offer}

Du kan även referera till en länk till ett erbjudande i en anrikningsaktivitet.

Gör så här:

1. Välj **[!UICONTROL Add data]** på aktivitetens **[!UICONTROL Enrichment]**-flik.
1. Välj **[!UICONTROL A link]** i fönstret där du väljer vilken typ av data som ska läggas till.
1. Välj den typ av länk som du vill etablera samt dess mål. I det här fallet är målet erbjudandeschemat.

   ![](assets/int_enrichment_link1.png)

1. Ange kopplingen mellan inkommande tabelldata i anrikningsaktiviteten (här mottagartabellen) och erbjudandetabellen. Du kan till exempel länka en erbjudandekod till en mottagare.

   ![](assets/int_enrichment_link2.png)

1. Konfigurera sedan en leveransaktivitet som motsvarar den valda kanalen. Mer information finns i avsnittet [Infoga ett erbjudande i ett leveransavsnitt](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery).

   >[!NOTE]
   >
   >Antalet tillgängliga offerter för förhandsgranskningen beror på konfigurationen som utförs i leveransen.

### Rankning och vikter för erbjudanden {#storing-offer-rankings-and-weights}

När en **enrichment** -aktivitet används för att leverera erbjudanden lagras deras rankningar och deras vikter som standard inte i förslagstabellen.

>[!NOTE]
>
>Kom ihåg: Den här informationen lagras som standard i aktiviteten **[!UICONTROL Offer engine]**.

Du kan dock lagra den här informationen på följande sätt:

1. Skapa ett anrop till erbjudandemotorn i en anrikningsaktivitet som placerats efter en fråga och före en leveransaktivitet. Se avsnittet [Ange ett erbjudande eller ett anrop till erbjudandemotorn](../../interaction/using/integrating-an-offer-via-a-workflow.md#specifying-an-offer-or-a-call-to-the-offer-engine).
1. Välj **[!UICONTROL Edit additional data...]** i aktivitetens huvudfönster.

   ![](assets/ita_enrichment_rankweight_1.png)

1. Lägg till **[!UICONTROL @rank]**-kolumnerna för rankningen och **[!UICONTROL @weight]** för erbjudandevikten.

   ![](assets/ita_enrichment_rankweight_2.png)

1. Bekräfta tillägget och spara arbetsflödet.

Leveransen lagrar automatiskt rangordningen och vikten av erbjudandena. Den här informationen visas på leveransfliken **[!UICONTROL Offers]**.

## Erbjudandemotor {#offer-engine}

Med aktiviteten **[!UICONTROL Offer engine]** kan du även ange ett anrop till erbjudandemotorn före leveransen.

Denna aktivitet fungerar enligt samma princip som anrikningsaktiviteten med ett motoranrop genom att anrika den inkommande populationsinformationen med ett erbjudande som beräknas av motorn, före leverans.

![](assets/int_offerengine_activity2.png)

När du har konfigurerat frågan (se [Handboken för arbetsflöden](../../workflow/using/query.md)):

1. Lägg till och öppna en **[!UICONTROL Offer engine]**-aktivitet.
1. Fyll i de olika tillgängliga fälten för att ange anrop till motoriska parametrar (erbjudandeutrymme, kategori eller tema, kontaktdatum, antal erbjudanden som ska behållas). Motorn beräknar automatiskt erbjudandena som ska läggas till enligt dessa parametrar.

   >[!NOTE]
   >
   >Varning! Om du använder den här aktiviteten lagras endast de offertförslag som används i leveransen.

   ![](assets/int_offerengine_activity1.png)

1. Konfigurera sedan en leveransaktivitet som motsvarar den valda kanalen. Mer information finns i avsnittet [Infoga ett erbjudande i ett leveransavsnitt](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery).

## Erbjudanden per cell {#offers-by-cell}

Med aktiviteten **[!UICONTROL Offers by cell]** kan du distribuera den inkommande populationen (från en fråga till exempel) till flera segment och ange ett erbjudande som ska visas för vart och ett av dessa segment.

Gör så här:

1. Lägg till aktiviteten **[!UICONTROL Offers by cell]** när du har angett målpopulationen och öppna den sedan.
1. På fliken **[!UICONTROL General]** väljer du det erbjudandeutrymme som du vill visa erbjudandena på.
1. På fliken **[!UICONTROL Cells]** anger du de olika delmängderna med knappen **[!UICONTROL Add]**:

   * Ange delmängdsfyllningen med de tillgängliga filtrerings- och begränsningsreglerna.
   * Välj sedan det erbjudande som du vill presentera för undergruppen. De erbjudanden som är tillgängliga är sådana som är berättigade i den erbjudandemiljö som valdes i föregående steg.

     ![](assets/int_offer_per_cell1.png)

1. Konfigurera sedan en leveransaktivitet som motsvarar den valda kanalen. Mer information finns i avsnittet [Infoga ett erbjudande i ett leveransavsnitt](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery).
