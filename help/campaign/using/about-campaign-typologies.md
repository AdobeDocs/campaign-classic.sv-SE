---
solution: Campaign Classic
product: campaign
title: Om kampanjtypologier
description: Om kampanjtypologier
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 12%

---


# Om kampanjtypologier{#about-campaign-typologies}

Kampanjoptimering är Adobe Campaign-modulen som gör att ni kan styra, filtrera och övervaka leveransen. För att undvika konflikter mellan kampanjer kan Adobe Campaign testa olika kombinationer genom att tillämpa särskilda begränsningsregler. Detta garanterar att de skickade meddelandena uppfyller kundernas behov och förväntningar och företagets kommunikationspolicy.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#typologies-video)

>[!NOTE]
>
>Beroende på vilket erbjudande du erbjuder kan Campaign Optimization inkluderas eller läggas till. Kontrollera licensavtalet.

## Regler för typologi {#typology-rules}

Med Adobe Campaign kan du utforma och tillämpa fyra typologiregler:

* **Filtreringsregler** som gör att du kan utesluta delar av målet baserat på villkor. For more on this, refer to [Filtering rules](../../campaign/using/filtering-rules.md).
* **Tryckregler** som gör att ni kan kontrollera reklamtrötthet. For more on this, refer to [Pressure rules](../../campaign/using/pressure-rules.md).
* **Kapacitetsregler** som gör att du kan begränsa lasterna för att garantera optimala bearbetningsförhållanden. For more on this, refer to [Controlling capacity](../../campaign/using/consistency-rules.md#controlling-capacity).
* **Styr** regler som gör att du kan kontrollera giltigheten för meddelanden innan de skickas. For more on this, refer to [Control rules](../../campaign/using/control-rules.md).

När typologireglerna har skapats grupperas de i kampanjtypologier som refereras i leveranser. Se [Använda typologier](#applying-typologies).

## Typologier {#typologies}

En kampanjtypologi kan innehålla flera [typologiregler](#typology-rules), men en leverans kan bara referera till en typologi.

På fliken **[!UICONTROL Rules]** kan du lägga till, ta bort eller visa de typologiregler som ska användas.

![](assets/campaign_opt_rules_tab.png)

## Använda typologier {#applying-typologies}

Steg för att skapa och tillämpa en typologi på leveranser listas nedan:

1. Skapa typologiregler.

   Typologiregler finns i **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** noden.

   Olika regler som är tillgängliga i Campaign beskrivs i följande avsnitt: [regler](../../campaign/using/pressure-rules.md)för försäljningstryck, [kapacitetsregler](../../campaign/using/consistency-rules.md#controlling-capacity), [kontrollregler](../../campaign/using/control-rules.md) och [filtreringsregler](../../campaign/using/filtering-rules.md).

1. Skapa en typologi och referera till reglerna som du skapade i den.

   Typologier nås via **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** -noden.

1. Konfigurera leveransen för att använda den typologi du skapade. Mer information om detta finns i [det här avsnittet](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. Testa och kontrollera beteendet med kampanjsimuleringar. For more on campaign simulations, refer to [this section](../../campaign/using/campaign-simulations.md).

Vid färdigställande av leveransen utesluts mottagarna när kriteriet är uppfyllt. Du kan kontrollera loggar för att övervaka uteslutningar. Exempel på användningsområden för typologiregler för tryck finns på [den här sidan](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules).

## Självstudievideor {#typologies-video}

### Ställa in trötthetshantering med typologiregler

I den här videon förklaras hur du implementerar trötthetshantering i Adobe Campaign Classic genom att utnyttja typologiregler.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### Konfigurera trötthetshantering med fördefinierade filter

Trötthetshanteringen styr frekvens och antal meddelanden för att undvika att mottagare blir överdrivna. Om du inte har kampanjoptimeringsmodulen i din kampanjinstans kan du konfigurera ett fördefinierat filter som filtrerar målpopulationen efter antalet mottagna meddelanden. I den här videon förklaras hur du implementerar trötthetshantering i Adobe Campaign Classic med hjälp av filter.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

Fler Campaign Classic-instruktionsvideor finns [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html).

**Relaterat ämne**

* [Använd automatiska affärsregler på leveranser i alla kanaler](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)

* [Om kampanjtypologier](../../campaign/using/pressure-rules.md)

* [Hantera reklamtrötthet med tryckregler](https://docs.adobe.com/content/help/en/campaign-classic/using/orchestrating-campaigns/campaign-optimization/pressure-rules.html)