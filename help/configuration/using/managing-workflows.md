---
product: campaign
title: Hantera arbetsflöden
description: Hantera arbetsflöden
feature: Workflows, Configuration
role: Data Engineer, Developer
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 4%

---

# Hantera arbetsflöden{#managing-workflows}



Som standard baseras dina nya arbetsflöden på en arbetsflödesmall som är förkonfigurerad och baserad på en mottagartabell (nms:mottagare). För att de ska kunna baseras automatiskt på den anpassade mottagartabellen som refereras i alternativet **Nms_DefaultRcpSchema** (se [Konfigurera gränssnittet](../../configuration/using/configuring-the-interface.md)) måste du skapa en ny arbetsflödesmall.

Skapa en ny mall via noden **[!UICONTROL Resources > Templates > Workflow templates]**. I mallens egenskaper matchar de angivna dimensionerna tabellen med externa mottagare.

Genom att basera dina nya arbetsflöden på en nyligen skapad mall väljs den anpassade tabellen som standard för arbetsflödets globala mål- och filtreringsdimensioner.

Alla aktiviteter som används i arbetsflödet använder därför din anpassade tabell utan att någon ytterligare manuell konfiguration behövs.

Mer information om arbetsflöden finns i [det här avsnittet](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
