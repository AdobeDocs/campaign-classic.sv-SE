---
product: campaign
title: Använd en extern mottagartabell
description: Använd en extern mottagartabell
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 18%

---

# Använd en extern mottagartabell{#using-an-external-recipient-table}

![](../../assets/common.svg)

Om leveranstabellen är en extern tabell måste du göra ytterligare konfigurationer. The **[!UICONTROL nms:seedmember]** schemat måste utökas. En flik läggs till i startadresserna för att definiera fälten enligt nedan:

![](assets/s_ncs_user_seedlist_new_tab.png)

Om du vill lägga till dirigerade adresser till leveransen anger du lämpliga fält direkt på matchande flik eller importerar adressmallarna:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

The **nms:seedMember** schematillägget är [det här avsnittet](../../configuration/using/seed-addresses.md).
