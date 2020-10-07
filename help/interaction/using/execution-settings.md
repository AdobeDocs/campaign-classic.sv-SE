---
title: Körningsinställningar
seo-title: Körningsinställningar
description: Körningsinställningar
seo-description: null
page-status-flag: never-activated
uuid: a6549091-0c33-4fe1-adde-de3b285dd456
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: simulating-offers
discoiquuid: 52b5d5a9-10dc-4601-8fe4-962a2334322b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 5%

---


# Körningsinställningar{#execution-settings}

När du skapar en simulering kan du ange körningsinställningar om det behövs. Med de här inställningarna kan du köra simuleringen under en tid med låg aktivitet beroende på dess prioritet, eller spela in SQL-frågor i loggen. Det här steget är valfritt.

Dessa inställningar kan ändras senare på fliken **[!UICONTROL General]** i simuleringsfönstret.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** : Med kan du schemalägga simuleringen baserat på vald prioritet (Låg, Medel eller Hög) för att optimera Adobe Campaign prestanda.
* **[!UICONTROL Priority]** : detta är den nivå som används för simuleringen för att schemalägga den. När alternativet är markerat väljer kampanjbearbetningsarbetsflödet en tid med låg aktivitet för att starta kampanjen. **[!UICONTROL Schedule execution for a time of low activity]**
* **[!UICONTROL Log SQL queries in the journal]** : den här funktionen är endast avsedd för expertanvändare. Du kan lägga till en flik i loggen med SQL-frågor för att upptäcka eventuella felfunktioner om simuleringen avslutas med fel.

