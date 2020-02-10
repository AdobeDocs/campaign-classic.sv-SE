---
title: Personaliseringsdata
seo-title: Personaliseringsdata
description: Personaliseringsdata
seo-description: null
page-status-flag: never-activated
uuid: d3d66216-502a-410b-b062-fb413eb9363f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 2cd8a320-37e8-410a-b71b-0c13c8e15482
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Personaliseringsdata{#personalization-data}

Det går att använda data i meddelandemallen för att testa anpassning av transaktionsmeddelanden. Den här funktionen används för att generera en förhandsgranskning eller skicka ett korrektur. Om du installerar modulen **Leverans** kan du med den här informationen visa en återgivning av meddelanden för olika leverantörer av Internetåtkomst (**inkorgsåtergivning**: Mer information finns i [det här avsnittet](../../delivery/using/about-deliverability.md)).

Syftet med dessa data är att testa dina meddelanden innan de levereras. Dessa meddelanden sammanfaller inte med faktiska data som ska bearbetas av meddelandecentret. XML-strukturen måste dock vara identisk med den för händelsen som lagras i körningsinstansen, vilket visas nedan.

![](assets/messagecenter_create_custo_006.png)

Med den här informationen kan du anpassa meddelandeinnehåll med personaliseringstaggar (mer information finns i [Skapa meddelandeinnehåll](../../message-center/using/creating-message-content.md)).

1. Klicka på **[!UICONTROL Seed addresses]** fliken i meddelandemallen.
1. I händelseinnehållet anger du testinformationen i XML-format.

   ![](assets/messagecenter_create_custo_001.png)

