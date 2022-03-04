---
product: campaign
title: Utföra aggregerad databehandling
description: Lär dig hur du utför sammanställd datoranvändning i frågor
feature: Workflows
exl-id: 5b05788f-498b-4a84-bdde-2852900f0129
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 2%

---

# Utföra aggregerad databehandling {#performing-aggregate-computing}

![](../../assets/common.svg)

I det här exemplet vill vi räkna antalet mottagare som bor i London enligt kön.

* Vilken tabell måste markeras?

   Mottagartabellen (**nms:mottagare**)

* Vilka fält ska markeras i utdatakolumnen?

   Primärnyckel (med antal) och kön

* Vilka villkor baseras informationen på?

   Baserat på de mottagare som bor i London

Så här skapar du det här exemplet:

1. I **[!UICONTROL Data to extract]** definierar du ett antal för primärnyckeln (som i föregående exempel). Lägg till **[!UICONTROL Gender]** i utdatakolumnen. Kontrollera **[!UICONTROL Group]** i **[!UICONTROL Gender]** kolumn. På så sätt grupperas mottagarna efter kön.

   ![](assets/query_editor_nveau_27.png)

1. I **[!UICONTROL Sorting]** fönster, klicka **[!UICONTROL Next]**: ingen sortering behövs här.
1. Konfigurera datafiltrering. Här vill du begränsa urvalet till kontakter som bor i London.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >Värdena är skiftlägeskänsliga. Om värdet London anges i villkoret utan versal och om listan över mottagare innehåller ordet London med stor bokstav, misslyckas frågan.

1. I **[!UICONTROL Data formatting]** fönster, klicka **[!UICONTROL Next]**: ingen formatering krävs för det här exemplet.
1. I förhandsgranskningsfönstret klickar du på **[!UICONTROL Launch data preview]**.

   Det finns tre olika värden för varje sortering efter kön: **2** för hondjur, **1** för man och **0** när kön är okänd. I det här exemplet innehåller listan 10 kvinnor, 16 män och 2 personer vars kön inte är känd.

   ![](assets/query_editor_agregat_04.png)
