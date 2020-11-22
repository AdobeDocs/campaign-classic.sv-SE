---
solution: Campaign Classic
product: campaign
title: Validera
description: Validera
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---


# Validera{#validating}

Globala koncept för validering av leverans visas i [det här avsnittet](../../delivery/using/steps-validating-the-delivery.md).

Utdatafilen för en direktpostleverans genereras under leveransanalysen. Filens innehåll beror på de markerade utdatakolumnerna (se [Extraheringsfil](../../delivery/using/defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>Analysfasen är detaljerad i [analysen av leveransen](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

Under analysfasen genereras filen, men information om mottagare (dvs. leveransloggar) uppdateras inte. Du kan därför avbryta det här jobbet utan att köra några risker.

Kontrollera resultatet av analysen och innehållet i utdatafilen innan du klickar på **[!UICONTROL Confirm delivery]**. Med ett bekräftelsemeddelande kan du starta leveransen.

Skicka-bekräftelsen startar dataextraheringen i den angivna filen.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

Du kan sedan stänga guiden och titta på leveransloggarna via **[!UICONTROL Delivery]** fliken, som du når via leveransinformationen.

Du kan konfigurera hämtningsläget för leveransloggar på fliken **[!UICONTROL Analysis]** för leveransegenskaperna.

Det finns två lägen:

* **[!UICONTROL Messages are considered sent after validation]** (standardläge): i det här funktionsläget uppdateras alla utsändningsloggar när operatorn bekräftar sändningen (deras status går från Väntande leverans till Skickat) och leveransen ställs automatiskt in på **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : I det här läget kan du uppdatera utsändningsloggarna via en extern fil som skickas av tjänsteleverantören. I det här fallet måste ett arbetsflöde för att bearbeta informationen användas för att uppdatera sändningsstatusen.

   >[!NOTE]
   >
   >I det här fallet måste även leveransens status ändras till **[!UICONTROL Finished]** av användaren så snart som utsändningsloggarna uppdateras.
