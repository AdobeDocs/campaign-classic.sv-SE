---
product: campaign
title: Hantera profiler
description: Hantera profiler
feature: Profiles
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: e1d0556a-6f30-4863-9025-eb9c1b8b53d3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 2%

---

# Hantera profiler{#managing-profiles}



## Mottagarträd {#recipient-tree}

Om du vill använda de avancerade funktionerna för mottagarhantering måste du redigera Adobe Campaign-trädet. Klicka på **[!UICONTROL Explorer]** i verktygsfältet.

Som standard lagras mottagarna i **[!UICONTROL Profiles and targets]** noden i Adobe Campaign-trädet. Från samma nod kan du skapa en eller flera mappar och undermappar för att lagra mottagarprofiler.

Varje nod sammanfaller med en mapp. Data från varje mapp måste anses vara partitionerade från varandra. Det innebär att hanteringen av dubbletter blir svårare för flera mottagarmappar.

>[!NOTE]
>
>Om du vill visa listan över alla mottagare i databasen måste du skapa en vy. Läs mer i [Mappar och vyer](../../platform/using/access-management-folders.md).

## Flytta mottagare {#moving-recipients}

Du kan markera en eller flera mottagare, dra dem från mottagarlistan och släppa dem i önskad mapp. Ett varningsmeddelande ber dig bekräfta den här åtgärden.

## Kopiera en mottagare {#copying-a-recipient}

Du kan kopiera en mottagare i samma mapp genom att högerklicka på önskad mottagare och välja **[!UICONTROL Copy]**.

## Ta bort mottagare {#deleting-recipients}

Om du vill ta bort mottagare flyttar du dem till en viss mapp och tömmer sedan innehållet i den här mappen. Det är **rekommenderas att inte använda** den **[!UICONTROL Delete]** i det här fallet.

Om du vill rensa en mapp använder du **[!UICONTROL Actions > Purge folder]** -menyn, som du kommer åt genom att högerklicka på önskad mapp.

![](assets/s_ncs_user_purge_folder.png)

Klicka **[!UICONTROL Start]** för att starta åtgärden. I fönstrets mellersta del visas förloppsstatusen enligt nedan:

![](assets/s_ncs_user_purge_folder_start.png)
