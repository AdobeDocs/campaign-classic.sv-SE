---
title: Skapa ett filter
description: Lär dig hur du skapar ett filter när du utför frågor
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# Skapa ett filter {#creating-a-filter}

De filter som är tillgängliga i Adobe Campaign definieras via filtervillkor som skapas i samma operativsystem som frågor.

>[!NOTE]
>
>Mer information om hur du skapar filter finns i [det här avsnittet](../../platform/using/filtering-options.md).

Noden innehåller **[!UICONTROL Administration > Configuration > Predefined filters]** alla filter som används i listorna och översikterna.

Operatorlistan kan till exempel filtreras efter **[!UICONTROL Active accounts]**:

![](assets/query_editor_filter_sample_1.png)

Det matchande filtret innehåller frågan om **[!UICONTROL Account disabled]** värdet för **[!UICONTROL Operators]** schemat:

![](assets/query_editor_filter_sample_2.png)

För samma lista kan du med **[!UICONTROL By login or label]** filtret filtrera data i listan baserat på det värde som anges i filterfältet:

![](assets/query_editor_filter_sample_3.png)

Den är byggd på följande sätt:

![](assets/query_editor_filter_sample_4.png)

Om du vill matcha filtreringsvillkoren måste operatörskontot kontrollera något av följande villkor:

* Etiketten innehåller de tecken som anges i inmatningsfältet,
* Operatornamnet innehåller de tecken som anges i indatafältet.
* Beskrivningsområdets innehåll innehåller de tecken som anges i inmatningsfältet.

>[!NOTE]
>
>Med funktionen kan du **[!UICONTROL Upper]** inaktivera skiftlägeskänslig funktion.

I kolumnen kan du **[!UICONTROL Taken into account if]** definiera programvillkoren för dessa filtervillkor. Här representerar tecknen **$(/tmp/@text)** innehållet i det inmatningsfält som är länkat till filtret:

![](assets/query_editor_filter_sample_5.png)

Här, **$(/tmp/@text)=&#39;byrå&#39;**

The **$(/tmp/@text)!=&#39;** uttryck tillämpar varje villkor när inmatningsfältet inte är tomt.
