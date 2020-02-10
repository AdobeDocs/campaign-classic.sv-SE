---
title: Lägga till ett beräkningsfält av uppräkningstyp
description: Lär dig hur du lägger till ett beräkningsfält av typen Uppräkning
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


# Lägga till ett beräkningsfält av uppräkningstyp {#adding-an-enumeration-type-calculated-field}

Här vill vi skapa en fråga med ett beräkningsfält av **[!UICONTROL Enumerations]** typen. Det här fältet genererar ytterligare en kolumn i förhandsgranskningsfönstret för data. Den här kolumnen anger de numeriska värden som returneras som resultat för varje mottagare (0, 1 och 2). Varje värde i den nya kolumnen tilldelas ett kön: &quot;Man&quot; för &quot;1&quot;, &quot;kvinna&quot; för &quot;2&quot; eller &quot;Inte angivet&quot; om värdet är lika med &quot;0&quot;.

* Vilken tabell måste markeras?

   mottagartabellen (nms:mottagare)

* Fält som ska markeras i utdatakolumnen?

   Efternamn, förnamn, kön

* Vilka villkor som informationen ska filtreras baserat på?

   Mottagarspråket

Använd följande steg:

1. Öppna den allmänna frågeredigeraren och välj mottagartabellen (**[!UICONTROL nms:recipient]**).
1. I **[!UICONTROL Data to extract]** fönstret väljer du **[!UICONTROL Last name]**, **[!UICONTROL First name]** och **[!UICONTROL Gender]**.

   ![](assets/query_editor_nveau_73.png)

1. I **[!UICONTROL Sorting]** fönstret klickar du på **[!UICONTROL Next]**: ingen sortering behövs för det här exemplet.
1. I **[!UICONTROL Data filtering]** väljer du **[!UICONTROL Filtering conditions]**.
1. I **[!UICONTROL Target element]** fönstret anger du ett filtervillkor för att samla in mottagare som talar engelska.

   ![](assets/query_editor_nveau_74.png)

1. Klicka på i **[!UICONTROL Data formatting]** fönstret **[!UICONTROL Add a calculated field]**.

   ![](assets/query_editor_nveau_75.png)

1. Gå till **[!UICONTROL Type]** fönstret och **[!UICONTROL Export calculated field definition]** välj **[!UICONTROL Enumerations]**.

   Definiera den kolumn som det nya beräkningsfältet ska referera till. Det gör du genom att markera **[!UICONTROL Gender]** kolumnen i den nedrullningsbara menyn i **[!UICONTROL Source column]** fältet: målvärdena sammanfaller med **[!UICONTROL Gender]** kolumnen.

   ![](assets/query_editor_nveau_76.png)

   Definiera **käll** - och **målvärden** : målvärdet gör frågeresultatet lättare att läsa. Frågan ska returnera mottagarens kön och resultatet blir antingen 0, 1 eller 2.

   För varje &quot;käll-mål&quot;-rad som ska anges klickar du **[!UICONTROL Add]** i **[!UICONTROL List of enumeration values]**:

   * I **[!UICONTROL Source]** kolumnen anger du källvärdet för varje kön (0,1,2) på en ny rad.
   * Ange värdena i **[!UICONTROL Destination]** kolumnen: &quot;Ej angivet&quot; för rad &quot;0&quot;, &quot;Man&quot; för rad &quot;1&quot; och &quot;Kvinna&quot; för rad &quot;2&quot;.
   Markera **[!UICONTROL Keep the source value]** funktionen.

   Klicka **[!UICONTROL OK]** för att godkänna beräkningsfältet.

   ![](assets/query_editor_nveau_77.png)

1. Klicka på i **[!UICONTROL Data formatting]** fönstret **[!UICONTROL Next]**.
1. I förhandsgranskningsfönstret, **[!UICONTROL start the preview of the data]**.

   Den extra kolumnen definierar kön för 0, 1 och 2:

   * 0 för &quot;Ej angivet&quot;
   * 1 för &quot;Male&quot;
   * 2 för &quot;Kvinna&quot;
   ![](assets/query_editor_nveau_78.png)

   Om du t.ex. inte anger kön &quot;2&quot; i **[!UICONTROL List of enumeration values]** och **[!UICONTROL Generate a warning and continue]** funktionen för **[!UICONTROL In other cases]** fältet är markerad visas en varningslogg. Den här loggen anger att kön &quot;2&quot; (kvinna) inte har angetts. Den visas i fältet **[!UICONTROL Logs generated during export]** i förhandsgranskningsfönstret.

   ![](assets/query_editor_nveau_79.png)

   Låt oss ta ett exempel till och säga att uppräkningsvärdet &quot;2&quot; inte anges. Markera **[!UICONTROL Generate an error and reject the line]** funktionen: alla mottagare av kön&quot;2&quot; kommer att orsaka avvikelser och annan information på raden (för- och efternamn, osv.) exporteras inte. En fellogg visas i fältet **[!UICONTROL Logs generated during export]** i förhandsgranskningsfönstret. Den här loggen anger att uppräkningsvärdet &quot;2&quot; inte har angetts.

   ![](assets/query_editor_nveau_80.png)
