---
solution: Campaign Classic
product: campaign
title: Personaliseringsdata
description: Personaliseringsdata
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 3%

---


# Personaliseringsdata{#personalization-data}

Det går att använda data i meddelandemallen för att testa anpassning av transaktionsmeddelanden. Den här funktionen används för att generera en förhandsgranskning eller skicka ett korrektur. Om du installerar modulen **Leverans** kan du med den här informationen visa en återgivning av meddelanden för olika leverantörer av Internetåtkomst (**inkorgsåtergivning**: Mer information finns i [det här avsnittet](../../delivery/using/inbox-rendering.md)).

Syftet med dessa data är att testa dina meddelanden innan de levereras. Dessa meddelanden sammanfaller inte med faktiska data som ska bearbetas av meddelandecentret. XML-strukturen måste dock vara identisk med den för händelsen som lagras i körningsinstansen, vilket visas nedan.

![](assets/messagecenter_create_custo_006.png)

Med den här informationen kan du anpassa meddelandeinnehåll med personaliseringstaggar (mer information finns i [Skapa meddelandeinnehåll](../../message-center/using/creating-message-content.md)).

1. Klicka på **[!UICONTROL Seed addresses]** fliken i meddelandemallen.
1. I händelseinnehållet anger du testinformationen i XML-format.

   ![](assets/messagecenter_create_custo_001.png)
