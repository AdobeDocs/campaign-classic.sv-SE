---
title: Guiden Nytt fält
seo-title: Guiden Nytt fält
description: Guiden Nytt fält
seo-description: null
page-status-flag: never-activated
uuid: 2c8d35db-042a-47cf-a7a6-3bb63bf40d94
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6da65fb5-18a1-41a0-96d8-588e383f944b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Guiden Nytt fält{#new-field-wizard}

Med en guide som är tillgänglig via **[!UICONTROL Tools > Advanced > Add new fields]** kan du lägga till ett eller flera fält i en tabell i databasen.

När du validerar guiden uppdateras tilläggsschemat för den tabell som ska utökas och SQL-skriptet startas för att ändra databasens fysiska struktur.

Den här assistenten har fördelen att det går snabbt att lägga till ett fält utan att du behöver känna till strukturen i ett dataschema.

Den största nackdelen är begränsningen av data och de egenskaper som ska utökas.

Guiderna innehåller följande steg:

1. På den första sidan kan du ange namnet på schemat som ska utökas och namnområdet för tilläggsschemat där ändringarna ska sparas:

   ![](assets/d_ncs_integration_schema_addfield.png)

1. På nästa sida kan du ange egenskaperna för det fält som ska läggas till.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. Bekräfta ändringarna genom att klicka på **[!UICONTROL Finish]** .

En tilläggsfil som i vårt exempel kallas&quot;cus:mottagare&quot; skapas automatiskt och motsvarande SQL-skript körs:

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>Som standard deklareras de tillagda fälten med **egenskapsanvändaren** (med värdet &quot;true&quot;). Detta gör att du kan visa och redigera fältet i indataformuläret för det utökade schemat med hjälp av en kontroll av typen &quot;treeEdit&quot; (se Indataformulär).

