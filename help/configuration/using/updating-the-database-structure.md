---
product: campaign
title: Uppdatera databasstrukturen
description: Uppdatera databasstrukturen
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
source-git-commit: 50a89f993523f3274e87ebac740d1c121082e18c
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 8%

---

# Uppdatera databasstrukturen{#updating-the-database-structure}



Om du vill använda ändringarna i scheman startar du guiden för databasuppdatering. Den här guiden är tillgänglig via **[!UICONTROL Tools > Advanced > Update database structure]** . Den kontrollerar om databasens fysiska struktur matchar dess logiska beskrivning och kör SQL-uppdateringsskripten.

![](assets/d_ncs_integration_schema_update.png)

Modulerna i databasen fylls i och aktiveras automatiskt.

![](assets/d_ncs_integration_schema_update_select.png)

The **[!UICONTROL Add stored procedures]** och **[!UICONTROL Import initialization data]** används för att starta de inledande SQL-skripten och de datapaket som körs när databasen skapas.

Du kan importera en uppsättning data från ett externt datapaket. Välj **[!UICONTROL Import a package]** och ange paketets XML-fil.

Följ stegen och visa SQL-skriptet för databasuppdatering:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Detta är i ett redigeringsfält och kan ändras för att ta bort eller lägga till SQL-kod.

Starta sedan databasuppdateringen:

![](assets/d_ncs_integration_schema_update3.png)
