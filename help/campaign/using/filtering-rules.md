---
title: Filtreringsregler
seo-title: Filtreringsregler
description: Filtreringsregler
seo-description: null
page-status-flag: never-activated
uuid: 24238a99-1f0f-4d04-9807-557ec2a5ba16
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 0d50826e-2211-4c3b-8413-ca1453bba6c4
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e97183256ef6d3f2068dd0fbc8eb3c3f32e0bae0
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---


# Filtreringsregler{#filtering-rules}

Med filtreringsregler kan du definiera meddelanden som ska uteslutas baserat på kriterier som definierats i en fråga. Dessa regler är kopplade till en målinriktningsdimension.

Filtreringsregler kan länkas till andra typer av regler (kontroll, tryck osv.) i typologier eller grupperas i en dedikerad **filtreringstypologi** . Mer information finns i [Skapa och använda en filtertypologi](#creating-and-using-a-filtering-typology).

## Skapa en filtreringsregel {#creating-a-filtering-rule}

Du kan t.ex. filtrera nyhetsbrevets prenumeranter för att förhindra att kommunikationen skickas till mottagare som är minderåriga.

Så här definierar du filtret:

1. Skapa en **[!UICONTROL Filtering]** typologiregel som gäller för alla kommunikationskanaler.

   ![](assets/campaign_opt_create_filter_01.png)

1. Ändra standarddimensionen för målinriktning och välj prenumerationer (**nms:subscription**).

   ![](assets/campaign_opt_create_filter_02.png)

1. Skapa filtret med hjälp av **[!UICONTROL Edit the query from the targeting dimension...]** länken.

   ![](assets/campaign_opt_create_filter_03.png)

1. Länka den här regeln till en kampanjtypologi och spara den.

   ![](assets/campaign_opt_create_filter_04.png)

När den här regeln används i en leverans, exkluderas undertidsprenumeranter automatiskt. Ett specifikt meddelande indikerar regelprogram:

![](assets/campaign_opt_create_filter_05.png)

## Villkora en filtreringsregel {#conditioning-a-filtering-rule}

Du kan begränsa programfältet för filtreringsregeln baserat på den länkade leverans- eller leveransdispositionen.

Det gör du genom att gå till fliken **[!UICONTROL General]** i typologiregeln, välja den typ av begränsning som ska användas och skapa filtret enligt nedan:

![](assets/campaign_opt_create_filter_06.png)

I det här fallet gäller att även om regeln är länkad till alla leveranser, kommer den endast att tillämpas på dem som matchar kriterierna för det definierade filtret.

>[!NOTE]
>
>Typologier och filtreringsregler kan användas i ett arbetsflöde i **[!UICONTROL Delivery outline]** aktiviteten. For more on this, refer to [this section](../../workflow/using/delivery-outline.md).

## Skapa och använda en filtertypologi {#creating-and-using-a-filtering-typology}

Du kan skapa **[!UICONTROL Filtering]** typologier: de innehåller bara filtreringsregler.

![](assets/campaign_opt_create_typo_filtering.png)

Dessa specifika typologier kan länkas till en leverans när målet har valts: i leveransguiden klickar du på **[!UICONTROL To]** länken och sedan på **[!UICONTROL Exclusions]** fliken.

![](assets/campaign_opt_apply_typo_filtering.png)

Välj sedan den filtreringstyp som ska användas för leveransen. Om du vill göra det klickar du på **[!UICONTROL Add]** knappen och väljer de typologier som ska användas.

Du kan också länka filtreringsregler direkt via den här fliken utan att gruppera dem i en typologi. Använd fönstrets nedre del för att göra detta.

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>Endast typologier och filtreringsregler är tillgängliga i urvalsfönstret.
>
>Dessa konfigurationer kan definieras i leveransmallen som automatiskt tillämpas på alla nya leveranser som skapas med hjälp av mallen.


## Undantagsregler för standardleverans {#default-deliverability-exclusion-rules}

Två filtreringsregler är tillgängliga som standard: **[!UICONTROL Exclude addresses]** ( **[!UICONTROL addressExclusions]** ) och **[!UICONTROL Exclude domains]** ( **[!UICONTROL domainExclusions]** ). Under e-postanalysen jämför dessa regler mottagarnas e-postadresser med de förbjudna adresserna eller domännamnen i en krypterad global undertryckningslista som hanteras i leveransinstansen. Om det finns en matchning skickas inte meddelandet till den mottagaren.

Detta för att undvika att bli svartlistad på grund av skadlig aktivitet, särskilt användning av en svampfälla. Om en svällning till exempel används för att prenumerera via ett av dina webbformulär, skickas ett bekräftelsemeddelande via e-post till den svällningen, vilket gör att din adress automatiskt blir svartlistad.

>[!NOTE]
>
>Adresserna och domännamnen som finns i den globala undertryckningslistan är dolda. Endast antalet uteslutna mottagare anges i leveransanalysloggarna.

