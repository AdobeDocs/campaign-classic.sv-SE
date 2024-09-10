---
product: campaign
title: Uppdatera databasstrukturen
description: Uppdatera databasstrukturen
feature: Configuration
role: Data Engineer, Developer
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 8%

---

# Uppdatera databasstrukturen{#updating-the-database-structure}



Om du vill använda ändringarna i scheman startar du databasuppdateringsassistenten. Den här assistenten är tillgänglig via **[!UICONTROL Tools > Advanced > Update database structure]**. Den kontrollerar om databasens fysiska struktur matchar dess logiska beskrivning och kör SQL-uppdateringsskripten.

![](assets/d_ncs_integration_schema_update.png)

Modulerna i databasen fylls i och aktiveras automatiskt.

![](assets/d_ncs_integration_schema_update_select.png)

Alternativen **[!UICONTROL Add stored procedures]** och **[!UICONTROL Import initialization data]** används för att starta de inledande SQL-skripten och de datapaket som körs när databasen skapas.

Du kan importera en uppsättning data från ett externt datapaket. Det gör du genom att markera **[!UICONTROL Import a package]** och ange paketets XML-fil.

Följ stegen och visa SQL-skriptet för databasuppdatering:

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>Detta är i ett redigeringsfält och kan ändras för att ta bort eller lägga till SQL-kod.

Starta sedan databasuppdateringen:

![](assets/d_ncs_integration_schema_update3.png)
