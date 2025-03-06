---
product: campaign
title: Start och slut
description: Läs mer om Start- och slutarbetsflödesaktiviteter
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 56dfbaf3-93de-4ade-b4ad-9b54d239c7a5
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 4%

---

# Start och slut{#start-and-end}



Med aktiviteterna **[!UICONTROL Start]** och **[!UICONTROL End]** kan du markera början och slutet av ett arbetsflöde grafiskt. Dessa aktiviteter har ingen funktionell inverkan och är därför valfria.

* **[!UICONTROL Start]**

  Körningen av ett arbetsflöde börjar med aktiviteter utan en inkommande övergång och aktiviteter av typen Start.

  ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

  Du kan konfigurera aktiviteten **[!UICONTROL End]** så att den avbryter alla pågående uppgifter. Det gör du genom att dubbelklicka på aktiviteten för att visa dess egenskaper och markera lämpligt alternativ.

  ![](assets/s_user_segmentation_end.png)

  Data i arbetstabellen tas bort automatiskt när slutaktiviteten är aktiverad. Om det inte är nödvändigt och för att undvika onödiga inläsningar kan du välja att inaktivera övergången vid den senaste aktivitetsutdata. Om ingen process är schemalagd vid en utleverans avmarkerar du det relevanta alternativet enligt nedan:

  ![](assets/s_advuser_delivery_option_no_output.png)
