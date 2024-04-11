---
product: campaign
title: Körningsinställningar
description: Körningsinställningar
feature: Interaction, Offers
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: e2dea4a0-9ed8-47b6-a16b-eeee653d2290
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# Körningsinställningar{#execution-settings}



När du skapar en simulering kan du ange körningsinställningar om det behövs. Med de här inställningarna kan du köra simuleringen under en tid med låg aktivitet beroende på dess prioritet, eller spela in SQL-frågor i loggen. Det här steget är valfritt.

Dessa inställningar kan ändras senare i dialogrutan **[!UICONTROL General]** i simuleringsfönstret.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** : låter dig schemalägga simuleringen baserat på vald prioritet (låg, medel eller hög) för att optimera Adobe Campaign prestanda.
* **[!UICONTROL Priority]** : det här är den nivå som används för simuleringen för att schemalägga den. När **[!UICONTROL Schedule execution for a time of low activity]** alternativet är markerat väljer kampanjbearbetningsarbetsflödet en tid med låg aktivitet för att starta kampanjen.
* **[!UICONTROL Log SQL queries in the journal]** : den här funktionen är endast avsedd för expertanvändare. Du kan lägga till en flik i loggen med SQL-frågor för att upptäcka eventuella felfunktioner om simuleringen avslutas med fel.
