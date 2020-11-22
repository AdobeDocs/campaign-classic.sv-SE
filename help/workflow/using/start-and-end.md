---
solution: Campaign Classic
product: campaign
title: Starta och sluta
description: Läs mer om Start- och slutarbetsflödesaktiviteter
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 4%

---


# Starta och sluta{#start-and-end}

Med hjälp av funktionerna **[!UICONTROL Start]** och **[!UICONTROL End]** kan du markera början och slutet av ett arbetsflöde grafiskt. Dessa aktiviteter har ingen funktionell inverkan och är därför valfria.

* **[!UICONTROL Start]**

   Körningen av ett arbetsflöde börjar med aktiviteter utan en inkommande övergång och aktiviteter av typen Start.

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

   Du kan konfigurera aktiviteten så att **[!UICONTROL End]** den avbryter alla pågående uppgifter. Det gör du genom att dubbelklicka på aktiviteten för att visa dess egenskaper och markera lämpligt alternativ.

   ![](assets/s_user_segmentation_end.png)

   Data i arbetstabellen tas bort automatiskt när slutaktiviteten är aktiverad. Om det inte är nödvändigt och för att undvika onödiga inläsningar kan du välja att inaktivera övergången vid den senaste aktivitetsutdata. Om ingen process är schemalagd vid en utleverans avmarkerar du det relevanta alternativet enligt nedan:

   ![](assets/s_advuser_delivery_option_no_output.png)

