---
product: campaign
title: Skapa händelsetyper
description: Lär dig hur du skapar händelsetyper som matchar transaktionsmeddelanden som du vill skicka i Adobe Campaign Classic
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 3%

---

# Skapa händelsetyper {#creating-event-types}



För att vara säker på att varje händelse kan ändras till ett personligt meddelande måste du först skapa **händelsetyper**.

När [skapa en meddelandemall](../../message-center/using/creating-the-message-template.md)väljer du den typ av händelse som matchar meddelandet som du vill skicka.

>[!IMPORTANT]
>
>Du måste skapa händelsetyper innan du kan använda dem i meddelandemallar.

Följ stegen nedan för att skapa händelsetyper som ska bearbetas av Adobe Campaign:

1. Logga in på **kontrollinstans**.

1. Gå till **[!UICONTROL Administration > Platform > Enumerations]** mapp i trädet.

1. Välj **[!UICONTROL Event type]** från listan.

1. Klicka **[!UICONTROL Add]** för att skapa ett uppräkningsvärde. Detta kan vara en orderbekräftelse, lösenordsändring, orderleveransändring osv.

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >Varje händelsetyp måste matcha ett värde i **[!UICONTROL Event type]** uppräkning.

1. När de specificerade listvärdena har skapats loggar du ut och tillbaka till instansen för att det ska gå att skapa.

>[!NOTE]
>
>Läs mer om specificerade listor i [Uppräkningshantering](../../platform/using/managing-enumerations.md).


