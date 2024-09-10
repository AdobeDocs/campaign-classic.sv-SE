---
product: campaign
title: Validera
description: Validera
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Direct Mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 1%

---

# Validera{#validating}



Globala koncept vid validering av en leverans visas i [det här avsnittet](steps-validating-the-delivery.md).

Utdatafilen för en direktpostleverans genereras under leveransanalysen. Filens innehåll beror på de markerade utdatakolumnerna (se [Extraktionsfil](defining-the-direct-mail-content.md#extraction-file)).

>[!NOTE]
>
>Analysfasen är detaljerad i [Analysera leveransen](steps-validating-the-delivery.md#analyzing-the-delivery).

Under analysfasen genereras filen, men informationen om mottagarna (dvs. leveransloggar) uppdateras inte. Du kan därför avbryta det här jobbet utan att köra några risker.

Kontrollera resultatet av analysen och innehållet i utdatafilen innan du klickar på **[!UICONTROL Confirm delivery]**. Med ett bekräftelsemeddelande kan du starta leveransen.

Skicka-bekräftelsen startar dataextraheringen i den angivna filen.

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

Du kan sedan stänga assistenten och titta på leveransloggarna via fliken **[!UICONTROL Delivery]** som du kommer åt via leveransinformationen.

Du kan konfigurera hämtningsläget för leveransloggar på fliken **[!UICONTROL Analysis]** i leveransegenskaperna.

Det finns två lägen:

* **[!UICONTROL Messages are considered sent after validation]** (standardläge): i det här funktionsläget uppdateras alla utsändningsloggar när operatorn bekräftar sändningen (deras status går från Väntande leverans till Skickat) och leveransen ställs automatiskt in på **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** : I det här läget kan du uppdatera utsändningsloggarna via en extern fil som skickas av tjänsteleverantören. I det här fallet måste ett arbetsflöde för att bearbeta informationen användas för att uppdatera sändningsstatusen.

  >[!NOTE]
  >
  >I det här fallet måste leveransens status också ändras till **[!UICONTROL Finished]** av användaren så snart som utsändningsloggarna uppdateras.
