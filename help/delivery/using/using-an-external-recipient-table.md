---
title: Använda en extern mottagartabell
seo-title: Använda en extern mottagartabell
description: Använda en extern mottagartabell
seo-description: null
page-status-flag: never-activated
uuid: a6147425-14f0-41e8-a47f-3e7072deafa7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 92c32b2d-d8bf-41ab-9349-ef4a15f10521
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Använda en extern mottagartabell{#using-an-external-recipient-table}

Om leveranstabellen är en extern tabell måste du göra ytterligare konfigurationer. Schemat måste utökas **[!UICONTROL nms:seedmember]** . En flik läggs till i startadresserna för att definiera fälten enligt nedan:

![](assets/s_ncs_user_seedlist_new_tab.png)

Om du vill lägga till dirigerade adresser till leveransen anger du lämpliga fält direkt på matchande flik eller importerar adressmallarna:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

Schematillägget **nms:seedMember** är [det här avsnittet](../../configuration/using/seed-addresses.md).
