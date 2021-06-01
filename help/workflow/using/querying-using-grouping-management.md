---
product: campaign
title: Fråga med grupperingshantering
description: Lär dig hur du utför frågor med hjälp av grupperingshantering
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 23bccb48-60ab-46c9-be26-2fa35243d61e
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---

# Fråga med grupperingshantering {#querying-using-grouping-management}

I det här exemplet vill vi köra en fråga för att hitta alla e-postdomäner som är riktade över 30 gånger under tidigare leveranser.

* Vilken tabell måste markeras?

   mottagartabellen (nms:mottagare)

* Fält som ska markeras i utdatakolumner?

   E-postdomän och primärnyckel (med antal)

* Datagruppering?

   Baserat på en e-postdomän med ett antal primärnycklar över 30. Den här åtgärden utförs med alternativet **[!UICONTROL Group by + Having]**. **[!UICONTROL Group by + Having]** I kan du gruppera data (&quot;gruppera efter&quot;) och göra en markering av grupperade data (&quot;ha&quot;).

Så här skapar du det här exemplet:

1. Öppna **[!UICONTROL Generic query editor]** och välj mottagartabellen (**nms:mottagare**).

   ![](assets/query_editor_02.png)

1. I fönstret **[!UICONTROL Data to extract]** väljer du fälten **[!UICONTROL Email domain]** och **[!UICONTROL Primary key]**. Kör ett antal i fältet **[!UICONTROL Primary key]**.

   Mer information om antalet primärnycklar finns i [det här avsnittet](../../platform/using/defining-filter-conditions.md#building-expressions).

1. Markera rutan **[!UICONTROL Handle groupings (GROUP BY + HAVING)]**.

   ![](assets/query_editor_nveau_29.png)

1. Sortera e-postdomäner i fallande ordning i fönstret **[!UICONTROL Sorting]**. Det gör du genom att kontrollera **[!UICONTROL Yes]** i kolumnen **[!UICONTROL Descending sort]**. Klicka på **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_70.png)

1. I **[!UICONTROL Data filtering]** väljer du **[!UICONTROL Filtering conditions]**. Gå till fönstret **[!UICONTROL Target elements]** och klicka på **[!UICONTROL Next]**.
1. I fönstret **[!UICONTROL Data grouping]** väljer du **[!UICONTROL Email domain]** genom att klicka på **[!UICONTROL Add]**.

   Det här fönstret för datagruppering visas bara om rutan **[!UICONTROL Handle groupings (GROUP BY + HAVING]**) är markerad.

   ![](assets/query_editor_blocklist_04.png)

1. I fönstret **[!UICONTROL Grouping condition]** anger du ett antal primärnycklar som är större än 30 eftersom vi bara vill att e-postdomäner som är avsedda mer än 30 gånger ska returneras som resultat.

   Fönstret visas när rutan **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** är markerad: Det är här grupperingsresultatet filtreras (HAVING).

   ![](assets/query_editor_blocklist_05.png)

1. Klicka på **[!UICONTROL Next]** i fönstret **[!UICONTROL Data formatting]**: ingen formatering behövs här.
1. Klicka på **[!UICONTROL Launch data preview]** i förhandsgranskningsfönstret: Här returneras tre olika e-postdomäner som är riktade över 30 gånger.

   ![](assets/query_editor_blocklist_06.png)
