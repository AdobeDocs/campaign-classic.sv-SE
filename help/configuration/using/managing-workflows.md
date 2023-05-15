---
product: campaign
title: Hantera arbetsflöden
description: Hantera arbetsflöden
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 4%

---

# Hantera arbetsflöden{#managing-workflows}



Som standard baseras dina nya arbetsflöden på en arbetsflödesmall som är förkonfigurerad och baserad på en mottagartabell (nms:mottagare). För att de ska kunna baseras automatiskt på den anpassade mottagartabellen som refereras i **Nms_DefaultRcpSchema** alternativ (se [Konfigurera gränssnittet](../../configuration/using/configuring-the-interface.md) måste du skapa en ny arbetsflödesmall.

Skapa en ny mall via **[!UICONTROL Resources > Templates > Workflow templates]** nod. I mallens egenskaper matchar de angivna dimensionerna tabellen med externa mottagare.

Genom att basera dina nya arbetsflöden på en nyligen skapad mall väljs den anpassade tabellen som standard för arbetsflödets globala mål- och filtreringsdimensioner.

Alla aktiviteter som används i arbetsflödet använder därför din anpassade tabell utan att någon ytterligare manuell konfiguration behövs.

Mer information om arbetsflöden finns i [det här avsnittet](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
