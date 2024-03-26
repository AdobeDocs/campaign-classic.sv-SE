---
product: campaign
title: Om kampanjtypologier
description: Om kampanjtypologier
role: User, Data Engineer
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Typology Rules, Campaigns
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 14%

---

# Om kampanjtypologier{#about-campaign-typologies}

Kampanjoptimering är Adobe Campaign-modulen som gör att ni kan styra, filtrera och övervaka leveransen. För att undvika konflikter mellan kampanjer kan Adobe Campaign testa olika kombinationer genom att tillämpa särskilda begränsningsregler. Detta garanterar att de skickade meddelandena uppfyller kundernas behov och förväntningar och företagets kommunikationspolicy.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#typologies-video)

>[!NOTE]
>
>Beroende på vilket erbjudande du erbjuder kan Campaign Optimization inkluderas eller läggas till. Kontrollera licensavtalet.

## Typologiregler {#typology-rules}

Med Adobe Campaign kan du utforma och tillämpa fyra typologiregler:

* **Filtrering** regler som gör att du kan utesluta delar av målet baserat på kriterier. Mer information finns i [Filtreringsregler](filtering-rules.md).
* **Tryck** regler som gör att ni kan kontrollera reklamtrötthet. Mer information finns i [Tryckregler](pressure-rules.md).
* **Kapacitet** regler som gör att du kan begränsa lasterna för att garantera optimala bearbetningsförhållanden. Mer information finns i [Kontrollera kapacitet](consistency-rules.md#controlling-capacity).
* **Kontroll** regler som gör att du kan kontrollera giltigheten för meddelanden innan de skickas. Mer information finns i [Kontrollregler](control-rules.md).

När typologireglerna har skapats grupperas de i kampanjtypologier som refereras i leveranser. Se [Använda typologier](#applying-typologies).

## Typologier {#typologies}

En kampanjtypologi kan innehålla flera [typologiregler](#typology-rules), men en leverans kan bara referera till en typologi.

The **[!UICONTROL Rules]** kan du lägga till, ta bort eller visa de typologiregler som ska användas.

![](assets/campaign_opt_rules_tab.png)

## Använda typologier {#applying-typologies}

Steg för att skapa och tillämpa en typologi på dina leveranser listas nedan:

1. Skapa typologiregler.

   Typologiregler finns i **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** nod.

   Olika regler som är tillgängliga i Campaign beskrivs i följande avsnitt: [regler för försäljningstryck](pressure-rules.md), [kapacitetsregler](consistency-rules.md#controlling-capacity), [kontrollregler](control-rules.md) och [filtreringsregler](filtering-rules.md).

1. Skapa en typologi och referera till reglerna som du skapade i den.

   Typologier nås via **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** nod.

1. Konfigurera leveransen för att använda den typologi du skapade. Mer information om detta finns i [det här avsnittet](applying-rules.md#applying-a-typology-to-a-delivery).
1. Testa och kontrollera beteendet med kampanjsimuleringar. Mer information om kampanjsimuleringar finns i [det här avsnittet](campaign-simulations.md).

Vid färdigställande av leveransen utesluts mottagarna när kriteriet är uppfyllt. Du kan kontrollera loggar för att övervaka undantag. Exempel på användningsområden för regler för trycktypologi finns i [den här sidan](pressure-rules.md#use-cases-on-pressure-rules).

## Självstudievideor {#typologies-video}

### Ställa in trötthetshantering med typologiregler

I den här videon förklaras hur du implementerar trötthetshantering i Adobe Campaign genom att utnyttja typologiregler.

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### Ställa in trötthetshantering med fördefinierade filter

Trötthetshanteringen styr frekvens och antal meddelanden för att undvika överbelastning av mottagaren. Om du inte har kampanjoptimeringsmodulen i din kampanjinstans kan du konfigurera ett fördefinierat filter som filtrerar målpopulationen efter antalet meddelanden som tas emot I den här videon förklaras hur du implementerar trötthetshantering i Adobe Campaign Classic med hjälp av filter.

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

Det finns ytterligare utbildningsvideor för Campaign [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).

**Relaterat ämne**

* [Kom igång med typologier och trötthetshantering](pressure-rules.md)

