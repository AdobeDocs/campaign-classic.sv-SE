---
solution: Campaign Classic
product: campaign
title: Hantera åtkomst till Campaign-mappar
description: Lär dig hur du ger åtkomst till Campaign-mappar och skapar vyer
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 0%

---


# Hantera åtkomst till mappar{#folder-access-management}

Varje mapp i trädet har behörighet att läsa, skriva och ta bort. För att få åtkomst till en fil måste en operator eller grupp av operatorer åtminstone ha läsåtkomst till den.

## Behörigheter för en mapp

### Redigera behörigheter i en mapp {#edit-permissions-on-a-folder}

Följ stegen nedan om du vill redigera behörigheter i en viss mapp i trädet:

1. Högerklicka på mappen och välj **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_folder_properties.png)

1. Klicka på fliken **[!UICONTROL Security]** för att visa behörigheter för den här mappen.

   ![](assets/s_ncs_user_folder_properties_security.png)

### Ändra behörigheter {#modify-permissions}

Om du vill ändra behörigheter kan du:

* **Ersätta en grupp eller en operator**. Det gör du genom att klicka på en av grupperna (eller operatorerna) med rättigheter till mappen och välja en ny grupp (eller en ny operator) i listrutan:

   ![](assets/s_ncs_user_folder_properties_security02.png)

* **Auktorisera en grupp eller en operator**. Det gör du genom att klicka på knappen **[!UICONTROL Add]** och markera gruppen eller operatorn som du vill tilldela behörigheter för den här mappen.
* **Förbjud en grupp eller en operator**. Om du vill göra det klickar du på **[!UICONTROL Delete]** och väljer gruppen eller operatorn som du vill ta bort behörigheten för den här mappen från.
* **Välj de rättigheter som tilldelats en grupp eller en operator**. Det gör du genom att klicka på gruppen eller operatorn i fråga och sedan markera de åtkomsträttigheter som du vill ge och avmarkera de andra.

   ![](assets/s_ncs_user_folder_properties_security03.png)

### Sprid behörigheter {#propagate-permissions}

Du kan sprida auktoriseringar och åtkomsträttigheter. Det gör du genom att välja alternativet **[!UICONTROL Propagate]** i mappegenskaperna.

Behörigheterna som definieras i det här fönstret kommer sedan att tillämpas på alla undermappar i den aktuella noden. Du kan sedan överlagra dessa behörigheter för var och en av undermapparna.

>[!NOTE]
>
>Om du rensar det här alternativet för en mapp tas det inte bort automatiskt för undermapparna. Du måste rensa det explicit för var och en av undermapparna.

### Bevilja åtkomst för alla operatorer {#grant-access-to-all-operators}

Om alternativet **[!UICONTROL System folder]** är markerat på fliken **[!UICONTROL Security]** har alla operatorer åtkomst till dessa data, oavsett deras rättigheter. Om det här alternativet är avmarkerat måste du uttryckligen lägga till operatorn (eller deras grupp) i listan över auktoriseringar för att de ska ha åtkomst.

![](assets/s_ncs_user_folder_properties_security03b.png)

## Mappar och vyer {#folders-and-views}

### Om mappar {#about-folders}

Mappar är noder i Adobe Campaign-trädet. Dessa noder skapas genom att högerklicka på trädet via menyn **[!UICONTROL Add new folder]**. Som standard gör den första menyn att du kan lägga till den mapp som motsvarar den aktuella kontexten.

![](assets/s_ncs_user_add_folder_in_tree.png)

Du kan ge dessa mappar behörigheter som i alla andra mappar i trädet. Se [Hantering av mappåtkomst](#folder-access-management).

### Om vyer {#about-views}

Dessutom kan du skapa vyer för att begränsa tillgången till data och ordna innehållet i trädet så att det passar dina behov. Du kan sedan tilldela behörighet till vyerna.

En vy är en mapp som visar poster som lagras fysiskt i en eller flera andra mappar av samma typ. Om du till exempel skapar en Campaign-mapp som är en vy, visas alla kampanjer som finns i databasen som standard, oavsett ursprung. Dessa data kan sedan filtreras.

När du konverterar en mapp till en vy visas alla data som motsvarar mapptypen i databasen i vyn, oavsett i vilken mapp den sparas. Du kan sedan filtrera den för att begränsa vilka data som visas.

>[!IMPORTANT]
>
>Vyerna innehåller data och ger åtkomst till dem, men data lagras inte fysiskt i visningsmappen. Operatorn måste ha rätt behörighet för den önskade åtgärden i datakällmapparna (minst läsåtkomst).
>
>Om du vill ge åtkomst till en vy utan att ge åtkomst till dess källmapp, ger du bara inte läsåtkomst till den överordnade noden i källmappen.

För att skilja vyer från mappar visas namnet på varje vy i en annan färg (mörk cyan).

![](assets/s_ncs_user_view_name_color.png)

### Lägga till mappar och skapa vyer {#adding-folders-and-creating-views}

I exemplet nedan skapar vi nya mappar för att visa specifika data:

1. Skapa en ny typmapp för **[!UICONTROL Deliveries]** och ge den namnet **Leveranser, Frankrike**.
1. Högerklicka på den här mappen och välj **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_add_folder_exple.png)

1. Välj **[!UICONTROL This folder is a view]** på fliken **[!UICONTROL Restriction]**. Därefter visas alla leveranser i databasen.

   ![](assets/s_ncs_user_add_folder_exple01.png)

1. Definiera villkor för leveransfilter från frågeredigeraren i fönstrets mellersta del: kampanjer som motsvarar det definierade filtret visas sedan.

   >[!NOTE]
   >
   >Frågeredigeraren visas i [det här avsnittet](../../platform/using/about-queries-in-campaign.md).

   Med följande filtervillkor:

![](assets/s_ncs_user_add_folder_exple00.png)

Följande leveranser visas i vyn:

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>När du hanterar [transaktionsmeddelanden](../../message-center/using/about-transactional-messaging.md)-händelser får mapparna **[!UICONTROL Real time events]** eller **[!UICONTROL Batch events]** inte anges som vyer för körningsinstanserna, eftersom det kan leda till åtkomstproblem. Mer information om händelsesamling finns i [det här avsnittet](../../message-center/using/event-collection.md).