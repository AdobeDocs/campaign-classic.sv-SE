---
solution: Campaign Classic
product: campaign
title: Utgåva
description: Utgåva
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 2%

---


# Utgåva{#edition}

Skärmen för att skapa och konfigurera konfigurationsdokument för navigeringshierarkin är tillgänglig via noden **[!UICONTROL Administration > Configuration > Navigation hierarchies]**:

![](assets/d_ncs_integration_navigation_arbo.png)

Konfigurationen av navigeringshierarkin är uppdelad i flera XML-dokument. Den har en liknande princip som schemautökningen: alla dokument sammanfogas för att generera ett enda dokument som innehåller hela konfigurationen. Dokumentet kan inte redigeras och visas på fliken Förhandsgranska.

Redigeringsfältet innehåller innehållet i XML-dokumentet:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Med redigeringskontrollen &quot;Namn&quot; kan du ange dokumentnyckeln som består av namnet och namnutrymmet. Attributen name och namespace för elementet **`<navtree>`** uppdateras automatiskt i schemats XML-redigeringsfält.

Förhandsgranskningen genererar automatiskt det sammanfogade dokumentet med den fullständiga konfigurationen:

![](assets/d_ncs_integration_navigation_preview.png)

