---
title: Starta och sluta
description: Läs mer om Start- och slutarbetsflödesaktiviteter
page-status-flag: never-activated
uuid: ec0c818c-c307-4f50-908c-507bce0ea27b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 8b239d5e-2317-42c8-9fee-7d40bea624da
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
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

