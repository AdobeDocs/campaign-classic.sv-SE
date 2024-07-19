---
product: campaign
title: Använd en extern mottagartabell
description: Använd en extern mottagartabell
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Audiences
exl-id: b6aabc68-707d-4c6c-b008-277609166c6c
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 16%

---

# Använd en extern mottagartabell{#using-an-external-recipient-table}



Om leveranstabellen är en extern tabell måste du göra ytterligare konfigurationer. Schemat **[!UICONTROL nms:seedmember]** måste utökas. En flik läggs till i startadresserna för att definiera fälten enligt nedan:

![](assets/s_ncs_user_seedlist_new_tab.png)

Om du vill lägga till dirigerade adresser till leveransen anger du lämpliga fält direkt på matchande flik eller importerar adressmallarna:

![](assets/s_ncs_user_seedlist_add_new_tab.png)

Schematillägget **nms:seedMember** är [det här avsnittet](../../configuration/using/seed-addresses.md).
