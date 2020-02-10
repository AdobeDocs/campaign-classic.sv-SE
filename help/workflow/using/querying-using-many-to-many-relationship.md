---
title: Frågar med hjälp av en många-till-många-relation
description: Lär dig hur du utför frågor med hjälp av en många-till-många-relation
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


# Frågar med hjälp av en många-till-många-relation {#querying-using-a-many-to-many-relationship}

I det här exemplet vill vi återställa mottagare som inte har kontaktats under de senaste 7 dagarna. Den här frågan gäller alla leveranser.

I det här exemplet visas även hur du konfigurerar ett filter som är relaterat till valet av ett samlingselement (eller en orange nod). Samlingselement är tillgängliga i **[!UICONTROL Field to select]** fönstret.

* Vilken tabell måste markeras?

   mottagartabellen (**nms:receive**)

* Fält som ska markeras för utdatakolumnen

   Primär nyckel, efternamn, förnamn och e-postadress

* Baserat på vilka kriterier är den information som filtreras

   Baserat på leveransloggarna för mottagare som går tillbaka 7 dagar före idag

Använd följande steg:

1. Öppna den allmänna frågeredigeraren och markera mottagartabellen **[!UICONTROL (nms:recipient)]**.
1. I **[!UICONTROL Data to extract]** fönstret väljer du **[!UICONTROL Primary key]**, **[!UICONTROL First name]** och **[!UICONTROL Last name]****[!UICONTROL Email]**.

   ![](assets/query_editor_nveau_33.png)

1. Sortera namnen i bokstavsordning i sorteringsfönstret.

   ![](assets/query_editor_nveau_34.png)

1. I **[!UICONTROL Data filtering]** fönstret väljer du **[!UICONTROL Filtering conditions]**.
1. I **[!UICONTROL Target element]** fönstret innebär filtreringsvillkoret för att extrahera profiler utan spårningslogg de senaste 7 dagarna två steg. Elementet som du måste markera är en många-till-många-länk.

   * Börja med att markera samlingselementet (den orangefärgade noden) för den första **[!UICONTROL Recipient delivery logs (broadlog)]** **[!UICONTROL Value]** kolumnen.

      ![](assets/query_editor_nveau_67.png)

      Välj **[!UICONTROL do not exist as]** operator. Du behöver inte välja ett andra värde på den här raden.

   * Innehållet i det andra filtervillkoret beror på det första. Här visas **[!UICONTROL Event date]** fältet direkt i **[!UICONTROL Recipient delivery logs]** tabellen eftersom det finns en länk till tabellen.

      ![](assets/query_editor_nveau_36.png)

      Markera **[!UICONTROL Event date]** med **[!UICONTROL greater than or equal to]** operatorn . Markera **[!UICONTROL DaysAgo (7)]** värdet. Det gör du genom att klicka **[!UICONTROL Edit expression]** i **[!UICONTROL Value]** fältet. I **[!UICONTROL Formula type]** fönstret väljer du **[!UICONTROL Process on dates]** och **[!UICONTROL Current date minus n days]** ger&quot;7&quot; som värde.

      ![](assets/query_editor_nveau_37.png)

      Filtervillkoret har konfigurerats.

      ![](assets/query_editor_nveau_38.png)

1. I **[!UICONTROL Data formatting]** fönstret växlar du efternamn till versaler. Klicka på **[!UICONTROL Last name]** raden i **[!UICONTROL Transformation]** kolumnen och välj **[!UICONTROL Switch to upper case]** i listrutan.

   ![](assets/query_editor_nveau_39.png)

1. Använd **[!UICONTROL Add a calculated field]** funktionen för att infoga en kolumn i dataförhandsvisningsfönstret.

   I det här exemplet lägger du till ett beräkningsfält med förnamn och efternamn på mottagarna i en enda kolumn. Klicka på **[!UICONTROL Add a calculated field]** funktionen. I **[!UICONTROL Export calculated field definition]** fönstret anger du en etikett och ett internt namn och väljer **[!UICONTROL JavaScript Expression]** typ. Ange sedan följande uttryck:

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   Klicka **[!UICONTROL OK]**. Fönstret är konfigurerat **[!UICONTROL Data formatting]** .

   Mer information om hur du lägger till beräkningsfält finns i det här avsnittet.

1. Resultatet visas i **[!UICONTROL Data preview]** fönstret. Mottagare som inte har kontaktats de senaste 7 dagarna visas i alfabetisk ordning. Namnen visas med stora bokstäver och kolumnen med för- och efternamn har skapats.

   ![](assets/query_editor_nveau_41.png)
