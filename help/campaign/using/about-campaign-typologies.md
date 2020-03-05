---
title: Om kampanjtypologier
seo-title: Om kampanjtypologier
description: Om kampanjtypologier
seo-description: null
page-status-flag: never-activated
uuid: ec89fb14-7e2f-4e9f-b7ab-3c2caf93a697
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 72c5151c-ce1e-425a-9aee-beefe9f21a67
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 44d8ba19f2e79d30229239312e6a5148d247fb28

---


# Om kampanjtypologier{#about-campaign-typologies}

Kampanjoptimering är Adobe Campaign-modulen som gör att ni kan styra, filtrera och övervaka utskick. För att undvika konflikter mellan kampanjer kan Adobe Campaign testa olika kombinationer genom att tillämpa särskilda begränsningsregler. Detta garanterar att de skickade meddelandena uppfyller kundernas behov och förväntningar och företagets kommunikationspolicy.

>[!NOTE]
>
>Beroende på vilket erbjudande du erbjuder kan Campaign Optimization inkluderas eller läggas till. Kontrollera licensavtalet.

## Typologiregler {#typology-rules}

Med Adobe Campaign kan ni utforma och tillämpa fyra typer av typologiregler:

1. **Filtreringsregler** som gör att du kan utesluta delar av målet baserat på villkor. Mer information finns i [Filtreringsregler](../../campaign/using/filtering-rules.md).
1. **Tryckregler** som gör att ni kan kontrollera reklamtrötthet. Mer information finns i [Tryckregler](../../campaign/using/pressure-rules.md).
1. **Kapacitetsregler** som gör att du kan begränsa lasterna för att garantera optimala bearbetningsförhållanden. Mer information finns i [Kontrollera kapacitet](../../campaign/using/consistency-rules.md#controlling-capacity).
1. **Styr** regler som gör att du kan kontrollera giltigheten för meddelanden innan de skickas. Mer information finns i [Kontrollregler](../../campaign/using/control-rules.md).

När typologireglerna har skapats grupperas de i kampanjtypologier som refereras i leveranser. Se [Använda typologier](#applying-typologies).

## Typologier {#typologies}

En kampanjtypologi kan innehålla flera [typologiregler](#typology-rules), men en leverans kan bara referera till en typologi.

På fliken **[!UICONTROL Rules]** kan du lägga till, ta bort eller visa de typologiregler som ska användas.

![](assets/campaign_opt_rules_tab.png)

## Använda typologier {#applying-typologies}

Steg för att skapa och tillämpa en typologi på leveranser listas nedan:

1. Skapa typologiregler.

   Typologiregler finns i **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** noden.

   Olika regler som är tillgängliga i Campaign beskrivs i följande avsnitt: regler [för](../../campaign/using/pressure-rules.md)försäljningstryck, [kapacitetsregler](../../campaign/using/consistency-rules.md#controlling-capacity), [kontrollregler](../../campaign/using/control-rules.md) och [filtreringsregler](../../campaign/using/filtering-rules.md).

1. Skapa en typologi och referera till reglerna som du skapade i den.

   Typologier nås via **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** -noden.

1. Konfigurera leveransen för att använda den typologi du skapade. For more on this, refer to [this section](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. Testa och kontrollera beteendet med kampanjsimuleringar. For more on campaign simulations, refer to [this section](../../campaign/using/campaign-simulations.md).

Vid färdigställande av leveransen utesluts mottagarna när kriteriet är uppfyllt. Du kan kontrollera loggar för att övervaka undantag. Exempel på användningsområden för typologiregler för tryck finns på [den här sidan](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules).

**Relaterat ämne**

* [Använd automatiska affärsregler på leveranser i alla kanaler](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)