---
title: Utgåva
seo-title: Utgåva
description: Utgåva
seo-description: null
page-status-flag: never-activated
uuid: df9298fc-5f62-4afb-8118-ca7e3987e81f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
discoiquuid: 820be231-af76-44ce-8f4d-cd5eae1eb169
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 3%

---


# Utgåva{#edition}

Skärmen för att skapa och konfigurera konfigurationsdokument för navigeringshierarkin är tillgänglig via **[!UICONTROL Administration > Configuration > Navigation hierarchies]** noden:

![](assets/d_ncs_integration_navigation_arbo.png)

Konfigurationen av navigeringshierarkin är uppdelad i flera XML-dokument. Den har en liknande princip som schemautökningen: alla dokument sammanfogas för att generera ett enda dokument som innehåller hela konfigurationen. Dokumentet kan inte redigeras och visas på fliken Förhandsgranska.

Redigeringsfältet innehåller innehållet i XML-dokumentet:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Med redigeringskontrollen &quot;Namn&quot; kan du ange dokumentnyckeln som består av namnet och namnutrymmet. Attributen name och namespace för **`<navtree>`** elementet uppdateras automatiskt i schemats XML-redigeringsfält.

Förhandsgranskningen genererar automatiskt det sammanfogade dokumentet med den fullständiga konfigurationen:

![](assets/d_ncs_integration_navigation_preview.png)

