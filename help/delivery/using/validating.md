---
title: Validerar
seo-title: Validerar
description: Validerar
seo-description: null
page-status-flag: never-activated
uuid: e3cd96ef-4f5d-4e17-9fec-5eaa4d835cb1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
discoiquuid: c363a7cf-81a5-4c02-a021-b822eeeadd03
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 70f51ba3937d0f20d9a488c61b52b7ec4396fa5e

---


# Validerar{#validating}

Globala koncept för validering av leverans visas i [det här avsnittet](../../delivery/using/steps-validating-the-delivery.md).

Utdatafilen för en direktpostleverans genereras under leveransanalysen. Filens innehåll beror på de markerade utdatakolumnerna (se [Extraheringsfil](../../delivery/using/defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>Analysfasen är detaljerad i [analysen av leveransen](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

Under analysfasen genereras filen, men informationen om mottagarna (dvs. leveransloggar) uppdateras inte. Du kan därför avbryta det här jobbet utan att köra några risker.

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
