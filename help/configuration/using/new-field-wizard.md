---
product: campaign
title: Ny fältassistent
description: Ny fältassistent
feature: Schema Extension
role: Data Engineer, Developer
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: ec774cc10a69a694b3c2bf5a6f662afd12a1435a
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Ny fältassistent{#new-field-wizard}


Med en assistent som är tillgänglig via **[!UICONTROL Tools > Advanced > Add new fields]** kan du lägga till ett eller flera fält i en tabell i databasen.

När assistenten valideras uppdateras tilläggsschemat för den tabell som ska utökas och SQL-skriptet startas för att ändra databasens fysiska struktur.

Den här assistenten har fördelen att det går snabbt att lägga till ett fält utan att du behöver känna till strukturen i ett dataschema.

Den största nackdelen är begränsningen av data och de egenskaper som ska utökas.

Assistentskärmarna innehåller följande steg:

1. På den första sidan kan du ange namnet på schemat som ska utökas och namnområdet för tilläggsschemat där ändringarna ska sparas:

   ![](assets/d_ncs_integration_schema_addfield.png)

1. På nästa sida kan du ange egenskaperna för det fält som ska läggas till.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. Bekräfta ändringarna genom att klicka på knappen **[!UICONTROL Finish]**.

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
>Som standard deklareras tillagda fält med egenskapen **user** (med värdet &quot;true&quot;). Detta gör att du kan visa och redigera fältet i indataformuläret för det utökade schemat med hjälp av en kontroll av typen &quot;treeEdit&quot; (se Indataformulär).
