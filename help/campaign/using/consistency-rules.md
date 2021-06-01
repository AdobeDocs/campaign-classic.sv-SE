---
product: campaign
title: Konsekvensregler
description: Konsekvensregler
audience: campaign
content-type: reference
topic-tags: campaign-optimization
exl-id: 757328fa-4698-4f85-a5fa-074b5152ec45
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 2%

---

# Konsekvensregler{#consistency-rules}

## Konsekvensregler {#about-consistency-rules}

Adobe Campaign garanterar enhetlig kommunikation tack vare en uppsättning regler som finns i kampanjtypologier. Syftet är att kontrollera de leveranser som skickas till mottagarna, t.ex. volym, art, relevans osv.

**Exempelvis kan** Capacityrules undvika att överbelasta den plattform som berörs av meddelandeleveransen. Specialerbjudanden som innehåller en nedladdningslänk får inte skickas till för många personer samtidigt för att undvika att servern blir mättad. Telefonkampanjer får inte överskrida uppringningscentralernas bearbetningskapacitet osv. Mer information finns i [Kontrollera kapacitet](#controlling-capacity).

## Kontrollera kapacitet {#controlling-capacity}

Innan du levererar meddelanden måste du se till att din organisation har kapacitet att bearbeta leveransen (fysisk infrastruktur), de svar som leveransen kan generera (inkommande meddelanden) och antalet samtal som ska göras till kontaktprenumeranter (bearbetningskapacitet för callcenter), till exempel.

För att göra detta måste du skapa **[!UICONTROL Capacity]**-typologiregler.

I följande exempel skapar vi en typologiregel för en lojalitetskampanj för en telefon. Vi begränsar antalet meddelanden till 20 per dag, dvs. den dagliga bearbetningskapaciteten för ett callcenter. När regeln tillämpas på två leveranser kan vi övervaka förbrukningen via loggar.

Så här utformar du en ny kapacitetsregel:

1. Klicka på **[!UICONTROL New]** under noden **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]**.
1. Välj en **[!UICONTROL Capacity]**-regeltyp.

   ![](assets/campaign_opt_create_capacity_01.png)

1. Skapa tillgänglighetsraderna på fliken **[!UICONTROL Capacity]**: i vårt exempel är detta tidsperioder under vilka samtal kan göras. Välj en period på 24 timmar och ange 150 i den initiala kvantiteten, vilket innebär att callcentret kan hantera 150 samtal per dag.

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >Tillgänglighetsraderna är endast avsedda som information. Om du behöver exkludera meddelanden när kapacitetsgränsen nås, se [det här avsnittet](#exclude-messages-when-capacity-limit-reached).

1. Koppla den här regeln till en typologi och referera sedan till typologin i leveransen för att tillämpa den här kapacitetsregeln. Mer information om detta finns i [det här avsnittet](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. Du kan övervaka förbrukningen från flikarna **[!UICONTROL Consumptions]** och **[!UICONTROL Capacity]**.

   När en regel används i en leverans ger kolumnerna **[!UICONTROL Consumed]** och **[!UICONTROL Remaining]** information om inläsningen, vilket visas nedan:

   ![](assets/campaign_opt_create_capacity_03.png)

   Mer information om detta finns i [det här avsnittet](#monitoring-consumption).

## Definiera maximal belastning {#defining-the-maximum-load}

För att definiera den maximala lasten måste du definiera tillgänglighetsrader. Det finns två alternativ: Du kan skapa en eller flera tillgänglighetsrader manuellt (se [Lägga till tillgänglighetsrader en efter en](#adding-availability-lines-one-by-one)) eller skapa tillgänglighetsintervall. Frekvensen för dessa tidsperioder kan automatiseras (se [Lägg till en uppsättning tillgänglighetsrader](#add-a-set-of-availability-lines)).

### Lägger till tillgänglighetsrader en i en {#adding-availability-lines-one-by-one}

Om du vill skapa en tillgänglighetslinje klickar du på knappen **[!UICONTROL Add]** och väljer **[!UICONTROL Add an availability line]**. Ange tillgänglighetsperioden och tillgänglig last.

![](assets/campaign_opt_create_capacity_02.png)

Lägg till så många rader som behövs för att anpassa bearbetningskapaciteten.

### Lägg till en uppsättning tillgänglighetsrader {#add-a-set-of-availability-lines}

Om du vill definiera tillgänglighetsperioder för en viss tid klickar du på knappen **[!UICONTROL Add]** och väljer alternativet **[!UICONTROL Add a set of availability lines]**. Ange en varaktighet för varje tidsperiod och antalet perioder som ska skapas.

Om du vill automatisera hur ofta sidan skapas klickar du på knappen **[!UICONTROL Change]** och definierar tidsplanering.

![](assets/campaign_opt_create_capacity_07.png)

Vi kan till exempel definiera ett schema för att skapa tillgänglighetsperioder för alla arbetsdagar med en hastighet på 10 samtal per timme mellan 09.00 och 17.00. Gör så här:

1. Välj typ av intervall och de dagar och timmar som den gäller:

   ![](assets/campaign_opt_create_capacity_08.png)

1. Ange giltighetsdatum:

   ![](assets/campaign_opt_create_capacity_09.png)

1. Kontrollera schemat innan du godkänner det:

   ![](assets/campaign_opt_create_capacity_10.png)

Arbetsflödet **[!UICONTROL Forecasting]** skapar automatiskt alla matchande rader.

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>Vi rekommenderar att du skapar tillgänglighetsrader via filimport. På den här fliken kan du visa och kontrollera förbrukningsrader.

## Uteslut meddelanden när kapacitetsgränsen är {#exclude-messages-when-capacity-limit-reached}

Tillgänglighetsraderna är endast avsedda som information. Markera alternativet **[!UICONTROL Exclude from the target messages in excess of capacity]** om du vill exkludera överflödiga meddelanden. Detta förhindrar att kapaciteten överskrids. För samma population som i föregående exempel får förbrukningen och den återstående kapaciteten inte överstiga den ursprungliga kvantiteten:

![](assets/campaign_opt_create_capacity_04.png)

Antalet meddelanden som ska bearbetas är jämnt fördelat över det definierade tillgänglighetsintervallet. Detta är särskilt relevant för callcenters eftersom deras högsta antal samtal per dag är begränsat. Vid e-postleveranser kan du med alternativet **[!UICONTROL Do not limit instantaneous delivery capacity]** ignorera det här tillgänglighetsintervallet och skicka e-postmeddelanden samtidigt.

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>Om det finns en överlagring väljs de sparade meddelandena enligt formeln som definieras i leveransegenskaperna.

![](assets/campaign_opt_create_capacity_06.png)

## Övervaka förbrukning {#monitoring-consumption}

Som standard är kapacitetsreglerna endast avsedda för indikationsändamål. Välj alternativet **[!UICONTROL Exclude messages in excess of capacity from the target]** om du vill förhindra att den definierade inläsningen överskrids. I det här fallet utesluts överflödiga meddelanden automatiskt från leveranser med denna typologiregel.

Om du vill övervaka förbrukning kan du visa de värden som visas i kolumnen **[!UICONTROL Consumed]** på fliken **[!UICONTROL Capacity]** i typologiregeln.

![](assets/campaign_opt_create_capacity_04.png)

Om du vill visa förbrukningsrader klickar du på fliken **[!UICONTROL Consumptions]** i regeln.
