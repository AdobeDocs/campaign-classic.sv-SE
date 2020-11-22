---
solution: Campaign Classic
product: campaign
title: Använda en extern mottagartabell
description: Använda en extern mottagartabell
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 18%

---


# Använda en extern mottagartabell{#using-an-external-recipient-table}

Om leveranstabellen är en extern tabell måste du göra ytterligare konfigurationer. Schemat måste utökas **[!UICONTROL nms:seedmember]** . En flik läggs till i startadresserna för att definiera fälten enligt nedan:

![](assets/s_ncs_user_seedlist_new_tab.png)

Om du vill lägga till dirigerade adresser till leveransen anger du lämpliga fält direkt på matchande flik eller importerar adressmallarna:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

Schematillägget **nms:seedMember** är [det här avsnittet](../../configuration/using/seed-addresses.md).
