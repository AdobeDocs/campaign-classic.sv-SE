---
product: campaign
title: Redigera navigeringsträdet i Campaign Explorer
description: Redigera navigeringsträdet i Campaign Explorer
feature: Application Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---


# Redigera navigeringsträdet i Campaign Explorer{#edition}

Skärmen för att skapa och konfigurera konfigurationsdokument för navigeringshierarkin är tillgänglig via **[!UICONTROL Administration > Configuration > Navigation hierarchies]** nod:

![](assets/d_ncs_integration_navigation_arbo.png)

Konfigurationen av navigeringshierarkin är uppdelad i flera XML-dokument. Den fungerar enligt en princip som liknar schematillägg: alla dokument sammanfogas för att generera ett enda dokument som innehåller hela konfigurationen. Dokumentet kan inte redigeras och visas på fliken Förhandsgranska.

Redigeringsfältet innehåller innehållet i XML-dokumentet:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Med redigeringskontrollen &quot;Namn&quot; kan du ange dokumentnyckeln som består av namnet och namnutrymmet. Attributen name och namespace för **`<navtree>`** -elementet uppdateras automatiskt i schemats XML-redigeringsfält.

Förhandsgranskningen genererar automatiskt det sammanfogade dokumentet med den fullständiga konfigurationen:

![](assets/d_ncs_integration_navigation_preview.png)
