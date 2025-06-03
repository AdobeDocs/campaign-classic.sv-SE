---
product: campaign
title: Hantera profiler
description: Hantera profiler
feature: Profiles
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: e1d0556a-6f30-4863-9025-eb9c1b8b53d3
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 1%

---

# Hantera profiler{#managing-profiles}



## Mottagarträd {#recipient-tree}

Om du vill använda de avancerade funktionerna för mottagarhantering måste du redigera Adobe Campaign-trädet. Det gör du genom att klicka på knappen **[!UICONTROL Explorer]** i verktygsfältet.

Som standard lagras mottagare i noden **[!UICONTROL Profiles and targets]** i Adobe Campaign-trädet. Från samma nod kan du skapa en eller flera mappar och undermappar för att lagra mottagarprofiler.

Varje nod sammanfaller med en mapp. Data från varje mapp måste anses vara partitionerade från varandra. Det innebär att hanteringen av dubbletter blir svårare för flera mottagarmappar.

>[!NOTE]
>
> * Om du vill visa listan över alla mottagare i databasen måste du skapa en vy. Läs mer i [Mappar och vyer](../../platform/using/access-management-folders.md).
> * Mer information om hur du hanterar dina profiler finns i [Campaign v8-dokumentationen](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/config/configuration/folders-and-views){target=_blank}.


<!--
## Move recipients {#moving-recipients}

You can select one or more recipients, drag them from the recipient list, and drop them in the desired folder. A warning message asks you to confirm this action.

## Copy a recipient {#copying-a-recipient}

You can copy a recipient in the same folder by right-clicking the desired recipient and selecting **[!UICONTROL Copy]**.

## Delete recipients {#deleting-recipients}

To delete recipients, move them to a specific folder and then purge the content of this folder. It is **strongly recommended not to use** the **[!UICONTROL Delete]** option in this case.

To purge a folder, use the **[!UICONTROL Actions > Purge folder]** menu, accessed by right-clicking the desired folder.

![](assets/s_ncs_user_purge_folder.png)

Click **[!UICONTROL Start]** to launch the operation. The middle section of the window displays the progress status, as shown below:

![](assets/s_ncs_user_purge_folder_start.png)
-->