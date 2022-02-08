---
product: campaign
title: Utgåva
description: Utgåva
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Redigera navigeringsträdet i Campaign Explorer{#edition}

![](../../assets/v7-only.svg)

Skärmen för att skapa och konfigurera konfigurationsdokument för navigeringshierarkin är tillgänglig via **[!UICONTROL Administration > Configuration > Navigation hierarchies]** nod:

![](assets/d_ncs_integration_navigation_arbo.png)

Konfigurationen av navigeringshierarkin är uppdelad i flera XML-dokument. Den har en liknande princip som schemautökningen: alla dokument sammanfogas för att generera ett enda dokument som innehåller hela konfigurationen. Dokumentet kan inte redigeras och visas på fliken Förhandsgranska.

Redigeringsfältet innehåller innehållet i XML-dokumentet:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Med redigeringskontrollen &quot;Namn&quot; kan du ange dokumentnyckeln som består av namnet och namnutrymmet. Attributen name och namespace för **`<navtree>`** -elementet uppdateras automatiskt i schemats XML-redigeringsfält.

Förhandsgranskningen genererar automatiskt det sammanfogade dokumentet med den fullständiga konfigurationen:

![](assets/d_ncs_integration_navigation_preview.png)
