---
product: campaign
title: Utöka ett schema
description: Lär dig hur du utökar ett schema
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 5%

---

# Utöka ett schema{#extending-a-schema}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
>Vissa inbyggda scheman får inte utökas: huvudsakligen de för vilka följande inställningar har definierats:\
>**dataSource=&quot;file&quot;** och  **mappingType=&quot;xmlFile&quot;**.\
>Följande scheman får inte utökas: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, &lt;a 10/>ncm:publishing **,** nl:monitoring **,** nms:calendar **,** nms:remoteTracking **,** nms:userAgentRules **,** xtk:builder **,** xtk:connections **,** xtk:dbInit **,** xtk:funcList&lt;a2 7/>, **xtk:fusion**, **xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema&lt;a 39/>,** xtk:scriptContext **,** xtk:session **,** xtk:sqlSchema **,** xtk:strings&lt;a4 7/>.********
>Denna lista är inte uttömmande.

Det finns två metoder för att utöka ett befintligt schema:

1. Ändra källschemat direkt.
1. Skapa ett annat schema med samma namn men ett annat namnutrymme. Fördelen är att du kan utöka en tabell utan att behöva ändra det ursprungliga schemat.

   Schemats rotelement måste innehålla attributet **extendedSchema** med namnet på schemat som ska utökas som dess värde.

   Ett tilläggsschema har inte ett eget schema: schemat som genereras från källschemat fylls i med fälten i tilläggsschemat.

   >[!IMPORTANT]
   >
   >Du får inte ändra de inbyggda schemana i programmet, utan i stället schemautbyggnadsmekanismen. I annat fall kommer ändrade scheman inte att uppdateras vid tidpunkten för framtida uppgraderingar av programmet. Detta kan leda till felfunktioner vid användning av Adobe Campaign.

   **Exempel**: tillägg för  **nms:** mottagarschema.

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   Det utökade schemat **nms:receive** fylls i med fältet ifyllt i tilläggsschemat:

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   Attributet **relativeSchemas** i schemats rotelement refererar till beroendena på tilläggsscheman.

   Attributet **tillhörTo** i fältet fyller i det schema där det deklareras.

>[!IMPORTANT]
>
>För att ändringarna ska kunna beaktas måste du generera om scheman. Mer information finns i avsnittet [Återskapa scheman](../../configuration/using/regenerating-schemas.md).\
>Om ändringarna påverkar databasens struktur måste du köra en uppdatering. Mer information om detta hittar du i avsnittet [Uppdatera databasstrukturen](../../configuration/using/updating-the-database-structure.md) .
