---
title: Hantera arbetsflöden
seo-title: Hantera arbetsflöden
description: Hantera arbetsflöden
seo-description: null
page-status-flag: never-activated
uuid: 8b6320c0-1aae-4acd-a698-03f9bebd916d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ee724240-c337-489d-a21b-5f3aec1f247a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Hantera arbetsflöden{#managing-workflows}

Som standard baseras dina nya arbetsflöden på en arbetsflödesmall som är förkonfigurerad och baserad på en mottagartabell (nms:mottagare). För att de ska kunna baseras automatiskt på den anpassade mottagartabellen som refereras i alternativet **Nms_DefaultRcpSchema** (se [Konfigurera gränssnittet](../../configuration/using/configuring-the-interface.md) ) måste du skapa en ny arbetsflödesmall.

Skapa en ny mall via **[!UICONTROL Resources > Templates > Workflow templates]** noden. I mallens egenskaper matchar de angivna dimensionerna tabellen med externa mottagare.

Genom att basera dina nya arbetsflöden på en nyligen skapad mall väljs den anpassade tabellen som standard för arbetsflödets globala mål- och filtreringsdimensioner.

Alla aktiviteter som används i arbetsflödet använder därför din anpassade tabell utan att någon ytterligare manuell konfiguration behövs.

Mer information om arbetsflöden finns i [det här avsnittet](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)

