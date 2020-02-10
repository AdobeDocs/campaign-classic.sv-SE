---
title: Utöka ett schema
seo-title: Utöka ett schema
description: Utöka ett schema
seo-description: null
page-status-flag: never-activated
uuid: 1767b9de-1d72-4ece-aeec-87f83862d81c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 1c9af980-4e6b-44dc-af61-dd284863ec7d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# Utöka ett schema{#extending-a-schema}

>[!CAUTION]
>
>Vissa inbyggda scheman får inte utökas: huvudsakligen de för vilka följande inställningar har definierats:\
>**dataSource=&quot;file&quot;** och **mappingType=&quot;xmlFile&quot;**.\
>Följande scheman får inte utökas: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema********************************************,¥ncm:publishing¥nl:surveillance¥,nms:calendar✔nms:remote Tracking, nms:userAgentRules,¥xtk:builder, xtk:connections,¥xtk:dbInit,¥xtk:funcList,xtk:fusion¥,¥xtk: jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, ****************xtk:scriptContext¥,¥xtk:sessionUnder,¥xtk:sqlSchemaUnder, Underxtk:strings¥.
>Denna lista är inte uttömmande.

Det finns två metoder för att utöka ett befintligt schema:

1. Ändra källschemat direkt.
1. Skapa ett annat schema med samma namn men ett annat namnutrymme. Fördelen är att du kan utöka en tabell utan att behöva ändra det ursprungliga schemat.

   Schemats rotelement måste innehålla attributet **extendedSchema** med namnet på schemat som ska utökas som dess värde.

   Ett tilläggsschema har inte ett eget schema: schemat som genereras från källschemat fylls i med fälten i tilläggsschemat.

   >[!CAUTION]
   >
   >Du får inte ändra de inbyggda schemana i programmet, utan i stället schemautbyggnadsmekanismen. I annat fall kommer ändrade scheman inte att uppdateras vid tidpunkten för framtida uppgraderingar av programmet. Detta kan leda till fel i användningen av Adobe Campaign.

   **Exempel**: tillägg för **nms:mottagarschemat** .

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

   Attributet **relativeSchemas** i schemats rotelement refererar till beroenden till tilläggsscheman.

   Attributet **tillhörTo** i fältet fyller i det schema där det deklareras.

>[!CAUTION]
>
>För att ändringarna ska kunna beaktas måste du generera om scheman. Mer information finns i avsnittet [Återskapa scheman](../../configuration/using/regenerating-schemas.md) .\
>Om ändringarna påverkar databasens struktur måste du köra en uppdatering. Mer information finns i avsnittet [Uppdatera databasstrukturen](../../configuration/using/updating-the-database-structure.md) .

