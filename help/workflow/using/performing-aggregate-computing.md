---
title: Utföra aggregerad databearbetning
description: Lär dig hur du utför sammanställd datoranvändning i frågor
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


# Utföra aggregerad databearbetning {#performing-aggregate-computing}

I det här exemplet vill vi räkna antalet mottagare som bor i London enligt kön.

* Vilken tabell måste markeras?

   mottagartabellen (**nms:receive**)

* Vilka fält ska markeras i utdatakolumnen?

   Primärnyckel (med antal) och kön

* Vilka villkor baseras informationen på?

   Baserat på de mottagare som bor i London

Så här skapar du det här exemplet:

1. I **[!UICONTROL Data to extract]** definierar du ett antal för primärnyckeln (som i föregående exempel). Lägg till **[!UICONTROL Gender]** fältet i utdatakolumnen. Markera **[!UICONTROL Group]** alternativet i **[!UICONTROL Gender]** kolumnen. På så sätt grupperas mottagarna efter kön.

   ![](assets/query_editor_nveau_27.png)

1. I **[!UICONTROL Sorting]** fönstret klickar du på **[!UICONTROL Next]**: ingen sortering behövs här.
1. Konfigurera datafiltrering. Här vill du begränsa urvalet till kontakter som bor i London.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >Värdena är skiftlägeskänsliga. Om värdet London anges i villkoret utan versal och om listan över mottagare innehåller ordet London med stor bokstav, misslyckas frågan.

1. I **[!UICONTROL Data formatting]** fönstret klickar du på **[!UICONTROL Next]**: ingen formatering krävs för det här exemplet.
1. Klicka på i förhandsgranskningsfönstret **[!UICONTROL Launch data preview]**.

   Det finns tre olika värden för varje sortering efter kön: **2** för hondjur, **1** för hanar och **0** när kön är okänd. I det här exemplet innehåller listan 10 kvinnor, 16 män och 2 personer vars kön inte är känd.

   ![](assets/query_editor_agregat_04.png)
