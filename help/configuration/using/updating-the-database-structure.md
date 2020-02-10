---
title: Uppdaterar databasstrukturen
seo-title: Uppdaterar databasstrukturen
description: Uppdaterar databasstrukturen
seo-description: null
page-status-flag: never-activated
uuid: 084dcc7b-f890-4dff-a322-c9a8f1d614b8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: b82ae459-30b5-4a1c-91cc-5c7b8f128333
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Uppdaterar databasstrukturen{#updating-the-database-structure}

Om du vill använda ändringarna i scheman startar du guiden för databasuppdatering. Den här guiden är tillgänglig via **[!UICONTROL Tools > Advanced > Update database structure]** . Den kontrollerar om databasens fysiska struktur matchar dess logiska beskrivning och kör SQL-uppdateringsskripten.

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

