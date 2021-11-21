---
product: campaign
title: Validera
description: Validera
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---

# Validera{#validating}

![](../../assets/common.svg)

Global concepts when validating a delivery are presented in [this section](steps-validating-the-delivery.md).

Utdatafilen för en direktpostleverans genereras under leveransanalysen. The file&#39;s content depends on the selected output columns (refer to [Extraction file](defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>Analysfasen är detaljerad i [Analyserar leveransen](steps-validating-the-delivery.md#analyzing-the-delivery).

Under analysfasen genereras filen, men informationen om mottagarna (dvs. leveransloggar) uppdateras inte. Du kan därför avbryta det här jobbet utan att köra några risker.

Check the result of the analysis and the content of the output file before clicking **[!UICONTROL Confirm delivery]**. Med ett bekräftelsemeddelande kan du starta leveransen.

Skicka-bekräftelsen startar dataextraheringen i den angivna filen.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

Du kan sedan stänga guiden och titta på leveransloggarna via **[!UICONTROL Delivery]** -fliken, som du kommer åt via leveransinformationen.

You can configure the delivery logs retrieval mode from the **[!UICONTROL Analysis]** tab of the delivery properties.

Det finns två lägen:

* **[!UICONTROL Messages are considered sent after validation]** (standardläge): i det här funktionsläget uppdateras alla utsändningsloggar när operatorn bekräftar sändningen (deras status går från Väntande leverans till Skickat) och leveransen ställs automatiskt in på **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : I det här läget kan du uppdatera utsändningsloggarna via en extern fil som skickas av tjänsteleverantören. In this case, a workflow to process this information needs to be used in order to update the broadlog status.

   >[!NOTE]
   >
   >In this case, the delivery&#39;s status also needs to be changed to **[!UICONTROL Finished]** by the user as soon as the broadlogs are updated.
