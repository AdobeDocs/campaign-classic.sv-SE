---
product: campaign
title: Hantera arbetsflöden
description: Hantera arbetsflöden
feature: Workflows, Configuration
role: Data Engineer, Developer
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 5%

---

# Hantera arbetsflöden{#managing-workflows}



Som standard baseras dina nya arbetsflöden på en arbetsflödesmall som är förkonfigurerad och baserad på en mottagartabell (nms:mottagare). För att de ska kunna baseras automatiskt på den anpassade mottagartabellen som refereras i **Nms_DefaultRcpSchema** alternativ (se [Konfigurera gränssnittet](../../configuration/using/configuring-the-interface.md) måste du skapa en ny arbetsflödesmall.

Skapa en ny mall via **[!UICONTROL Resources > Templates > Workflow templates]** nod. I mallens egenskaper matchar de angivna dimensionerna tabellen med externa mottagare.

Genom att basera dina nya arbetsflöden på en nyligen skapad mall väljs den anpassade tabellen som standard för arbetsflödets globala mål- och filtreringsdimensioner.

Alla aktiviteter som används i arbetsflödet använder därför din anpassade tabell utan att någon ytterligare manuell konfiguration behövs.

Mer information om arbetsflöden finns i [det här avsnittet](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
