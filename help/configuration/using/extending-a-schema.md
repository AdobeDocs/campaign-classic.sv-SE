---
product: campaign
title: Utöka ett schema
description: Lär dig hur du utökar ett schema
role: Data Engineer, Developer
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 4%

---

# Utöka ett schema{#extending-a-schema}

>[!IMPORTANT]
>
>Vissa inbyggda scheman får inte utökas: huvudsakligen de för vilka följande inställningar har definierats:\
>**dataSource=&quot;file&quot;** och **mappingType=&quot;xmlFile&quot;**.\
>Följande scheman får inte utökas: **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl:monitoring**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules**, **xtk:builder**, **xtk:connections**, **xtk:dbInit**, **xtk:funcList**, **xtk:fusion**, **xtk: jst**, **xtk:navtree**, **xtk:tk queryDef**, **xtk:resourceMenu**, **xtk:schema**, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:strings**.
>Denna lista är inte uttömmande.

Det finns två metoder för att utöka ett befintligt schema:

1. Ändra källschemat direkt.
1. Skapa ett annat schema med samma namn men ett annat namnutrymme. Fördelen är att du kan utöka en tabell utan att behöva ändra det ursprungliga schemat.

   Schemats rotelement måste innehålla attributet **extendedSchema** med namnet på schemat som ska utökas som dess värde.

   Ett tilläggsschema har inget eget schema: schemat som genereras från källschemat fylls i med fälten i tilläggsschemat.

   >[!IMPORTANT]
   >
   >Du får inte ändra de inbyggda schemana i programmet, utan i stället schemautbyggnadsmekanismen. I annat fall kommer ändrade scheman inte att uppdateras när du uppgraderar programmet. Detta kan leda till felfunktioner vid användning av Adobe Campaign.

   **Exempel**: tillägg för schemat **nms:mottagare**.

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

   Attributet **BeroendeSchemas** i schemats rotelement refererar till beroenden till tilläggsscheman.

   Attributet **tillhörTo** i fältet fyller i det schema där det deklareras.

>[!IMPORTANT]
>
>För att ändringarna ska kunna beaktas måste du generera om scheman. Mer information finns på [den här sidan](../../configuration/using/regenerating-schemas.md).\
>Om ändringarna påverkar databasens struktur måste du köra en uppdatering. Mer information finns på [den här sidan](../../configuration/using/updating-the-database-structure.md).
