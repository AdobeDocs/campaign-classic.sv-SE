---
product: campaign
title: Skapa ett filter
description: Lär dig hur du skapar ett filter när du utför frågor
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 297ea1e1-39ef-4b99-aaaa-9e88611fb1bf
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 2%

---

# Skapa ett filter {#creating-a-filter}

![](../../assets/common.svg)

De filter som är tillgängliga i Adobe Campaign definieras via filtervillkor som skapas i samma operativsystem som frågor.

>[!NOTE]
>
>Mer information om hur du skapar filter finns i [det här avsnittet](../../platform/using/filtering-options.md).

Noden **[!UICONTROL Administration > Configuration > Predefined filters]** innehåller alla filter som används i listorna och översikterna.

Operatorlistan kan till exempel filtreras med **[!UICONTROL Active accounts]**:

![](assets/query_editor_filter_sample_1.png)

Det matchande filtret innehåller frågan för **[!UICONTROL Account disabled]**-värdet för **[!UICONTROL Operators]**-schemat:

![](assets/query_editor_filter_sample_2.png)

För samma lista kan du med filtret **[!UICONTROL By login or label]** filtrera data i listan baserat på det värde som anges i filterfältet:

![](assets/query_editor_filter_sample_3.png)

Den är byggd på följande sätt:

![](assets/query_editor_filter_sample_4.png)

Om du vill matcha filtreringsvillkoren måste operatörskontot kontrollera något av följande villkor:

* Etiketten innehåller de tecken som anges i inmatningsfältet,
* Operatornamnet innehåller de tecken som anges i indatafältet.
* Beskrivningsområdets innehåll innehåller de tecken som anges i inmatningsfältet.

>[!NOTE]
>
>Med funktionen **[!UICONTROL Upper]** kan du inaktivera den skiftlägeskänsliga funktionen.

Med **[!UICONTROL Taken into account if]**-kolumnen kan du definiera programvillkoren för dessa filtervillkor. Här representerar **$(/tmp/@text)**-tecknen innehållet i det inmatningsfält som är länkat till filtret:

![](assets/query_editor_filter_sample_5.png)

Här, **$(/tmp/@text)=&#39;byrå&#39;**

**$(/tmp/@text)!=&#39;**-uttryck tillämpar varje villkor när inmatningsfältet inte är tomt.
