---
product: campaign
title: Skapa ett filter
description: Lär dig hur du skapar ett filter när du utför frågor
feature: Query Editor, Workflows
exl-id: 297ea1e1-39ef-4b99-aaaa-9e88611fb1bf
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---

# Skapa ett filter {#creating-a-filter}



De filter som är tillgängliga i Adobe Campaign definieras via filtervillkor som skapas i samma operativsystem som frågor.

>[!NOTE]
>
>Mer information om hur du skapar filter finns i [det här avsnittet](../../platform/using/filtering-options.md).

The **[!UICONTROL Administration > Configuration > Predefined filters]** noden innehåller alla filter som används i listorna och översikterna.

Operatorlistan kan till exempel filtreras efter **[!UICONTROL Active accounts]**:

![](assets/query_editor_filter_sample_1.png)

Det matchande filtret innehåller frågan på **[!UICONTROL Account disabled]** värdet på **[!UICONTROL Operators]** schema:

![](assets/query_editor_filter_sample_2.png)

För samma lista **[!UICONTROL By login or label]** Med -filter kan du filtrera data i listan baserat på det värde som anges i filterfältet:

![](assets/query_editor_filter_sample_3.png)

Den är uppbyggd på följande sätt:

![](assets/query_editor_filter_sample_4.png)

Om du vill matcha filtreringsvillkoren måste operatörskontot kontrollera något av följande villkor:

* Etiketten innehåller de tecken som anges i inmatningsfältet,
* Operatornamnet innehåller de tecken som anges i indatafältet.
* Beskrivningsområdets innehåll innehåller de tecken som anges i inmatningsfältet.

>[!NOTE]
>
>The **[!UICONTROL Upper]** kan du inaktivera skiftlägeskänslig funktion.

The **[!UICONTROL Taken into account if]** kan du definiera programvillkoren för dessa filtervillkor. Här är **$(/tmp/@text)** tecken representerar innehållet i det inmatningsfält som är länkat till filtret:

![](assets/query_editor_filter_sample_5.png)

Här, **$(/tmp/@text)=&#39;agent&#39;**

The **$(/tmp/@text)!=&#39;** -uttrycket använder varje villkor när indatafältet inte är tomt.
