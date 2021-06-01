---
product: campaign
title: Använda en extern mottagartabell
description: Använda en extern mottagartabell
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 18%

---

# Använda en extern mottagartabell{#using-an-external-recipient-table}

Om leveranstabellen är en extern tabell måste du göra ytterligare konfigurationer. Schemat **[!UICONTROL nms:seedmember]** måste utökas. En flik läggs till i startadresserna för att definiera fälten enligt nedan:

![](assets/s_ncs_user_seedlist_new_tab.png)

Om du vill lägga till dirigerade adresser till leveransen anger du lämpliga fält direkt på matchande flik eller importerar adressmallarna:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

Schematillägget **nms:seedMember** är [det här avsnittet](../../configuration/using/seed-addresses.md).
