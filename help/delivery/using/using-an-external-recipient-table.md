---
product: campaign
title: Använd en extern mottagartabell
description: Använd en extern mottagartabell
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 16%

---

# Använd en extern mottagartabell{#using-an-external-recipient-table}



Om leveranstabellen är en extern tabell måste du göra ytterligare konfigurationer. The **[!UICONTROL nms:seedmember]** schemat måste utökas. En flik läggs till i startadresserna för att definiera fälten enligt nedan:

![](assets/s_ncs_user_seedlist_new_tab.png)

Om du vill lägga till dirigerade adresser till leveransen anger du lämpliga fält direkt på matchande flik eller importerar adressmallarna:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

The **nms:seedMember** schematillägget är [det här avsnittet](../../configuration/using/seed-addresses.md).
