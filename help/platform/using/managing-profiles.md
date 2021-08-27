---
product: campaign
title: Hantera profiler
description: Hantera profiler
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: e1d0556a-6f30-4863-9025-eb9c1b8b53d3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 2%

---

# Hantera profiler{#managing-profiles}

![](../../assets/common.svg)

## Mottagarträd {#recipient-tree}

Om du vill använda de avancerade funktionerna för mottagarhantering måste du redigera Adobe Campaign-trädet. Det gör du genom att klicka på knappen **[!UICONTROL Explorer]** i verktygsfältet.

Som standard lagras mottagarna i noden **[!UICONTROL Profiles and targets]** i Adobe Campaign-trädet. Från samma nod kan du skapa en eller flera mappar och undermappar för att lagra mottagarprofiler.

Varje nod sammanfaller med en mapp. Data från varje mapp måste anses vara partitionerade från varandra. Det innebär att hanteringen av dubbletter blir svårare för flera mottagarmappar.

>[!NOTE]
>
>Om du vill visa listan över alla mottagare i databasen måste du skapa en vy. Läs mer i [Mappar och vyer](../../platform/using/access-management-folders.md).

## Flytta mottagare {#moving-recipients}

Du kan markera en eller flera mottagare, dra dem från mottagarlistan och släppa dem i önskad mapp. Ett varningsmeddelande ber dig bekräfta den här åtgärden.

## Kopiera en mottagare {#copying-a-recipient}

Du kan kopiera en mottagare i samma mapp genom att högerklicka på önskad mottagare och välja **[!UICONTROL Copy]**.

## Ta bort mottagare {#deleting-recipients}

Om du vill ta bort mottagare flyttar du dem till en viss mapp och tömmer sedan innehållet i den här mappen. Vi rekommenderar **att du inte använder** alternativet **[!UICONTROL Delete]** i det här fallet.

Om du vill rensa en mapp använder du menyn **[!UICONTROL Actions > Purge folder]**, som du kommer åt genom att högerklicka på önskad mapp.

![](assets/s_ncs_user_purge_folder.png)

Klicka på **[!UICONTROL Start]** för att starta åtgärden. I fönstrets mellersta del visas förloppsstatusen enligt nedan:

![](assets/s_ncs_user_purge_folder_start.png)
