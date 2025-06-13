---
product: campaign
title: Hantera åtkomst till Campaign-mappar
description: Lär dig hur du ger åtkomst till Campaign-mappar och skapar vyer
badge: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Application Settings, Permissions
role: User, Admin
level: Beginner
exl-id: 0ba8a3d0-36d7-42f3-b281-0255e49b5fa3
hide: true
hidefromtoc: true
source-git-commit: b27b85b126e002c0ea8b5d71da1ed60e1e817980
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 2%

---

# Hantera åtkomst till mappar{#folder-access-management}



Varje mapp i Utforskarens navigeringsträd har behörighet att läsa, skriva och ta bort. För att få åtkomst till en fil måste en operator eller grupp av operatorer åtminstone ha läsåtkomst till den.

>[!NOTE]
>
>Mer information om behörigheter för mappar finns i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}.


## Mappar och vyer {#folders-and-views}

### Vad är en mapp? {#about-folders}

Mappar är noder i Adobe Campaign-trädet. De här noderna skapas genom att högerklicka på trädet via menyn **[!UICONTROL Add new folder]**. Som standard gör den första menyn att du kan lägga till den mapp som motsvarar den aktuella kontexten.

![](assets/s_ncs_user_add_folder_in_tree.png)

Du kan anpassa utforskarens navigeringsträd. Lär dig konfigurationssteg och bästa praxis [i det här avsnittet](adobe-campaign-workspace.md).

### Vad är en vy? {#about-views}

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

>[!IMPORTANT]
>
>Mappar som ligger utanför rutan ska inte markeras som vyer.


I exemplet nedan skapar vi nya mappar för att visa specifika data:

1. Skapa en ny typmapp för **[!UICONTROL Deliveries]** och ge den namnet **Leveranser i Frankrike**.
1. Högerklicka på mappen och välj **[!UICONTROL Properties...]**.

   ![Skärmbild med högerklick i egenskaperna](assets/s_ncs_user_add_folder_exple.png)

1. Välj **[!UICONTROL This folder is a view]** på fliken **[!UICONTROL Restriction]**. Därefter visas alla leveranser i databasen.

   ![Skärmvisning som visar den visningsruta som markeras](assets/s_ncs_user_add_folder_exple01.png)

1. Definiera leveransfiltervillkoren från frågeredigeraren i fönstrets mellersta del: kampanjerna som motsvarar det definierade filtret visas sedan.

   >[!NOTE]
   >
   >Frågeredigeraren visas i [det här avsnittet](../../platform/using/about-queries-in-campaign.md).

   Med följande filtervillkor:

![Skärmbild som visar de olika filtervillkoren](assets/s_ncs_user_add_folder_exple00.png)

Följande leveranser visas i vyn:

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>När [transaktionsmeddelanden](../../message-center/using/about-transactional-messaging.md) hanteras får mapparna **[!UICONTROL Real time events]** eller **[!UICONTROL Batch events]** inte anges som vyer för körningsinstanserna eftersom det kan leda till problem med åtkomst. Mer information om händelsesamling finns i [det här avsnittet](../../message-center/using/about-event-processing.md#event-collection).

<!--
## Permissions on a folder

### Edit permissions on a folder {#edit-permissions-on-a-folder}

To edit permissions on a specific folder of the tree, follow the steps below:

1. Right-click on the folder and select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_folder_properties.png)

1. Click the **[!UICONTROL Security]** tab to view authorizations on this folder.

   ![](assets/s_ncs_user_folder_properties_security.png)

### Modify permissions {#modify-permissions}

To modify permissions, you can:

* **Replace a group or an operator**. To do this, click one of the groups (or operators) with rights to the folder, and select a new group (or a new operator) from the drop-down list:

  ![](assets/s_ncs_user_folder_properties_security02.png)

* **Authorize a group or an operator**. To do this, click the **[!UICONTROL Add]** button and select the group or operator to which you want to assign authorizations for this folder.
* **Forbid a group or an operator**. To do this, click **[!UICONTROL Delete]** and select the group or operator from which you want to remove authorization for this folder.
* **Select the rights assigned to a group or an operator**. To do this, click the group or operator concerned, then select the access rights you want to grant and deselect the others.

  ![](assets/s_ncs_user_folder_properties_security03.png)

### Propagate permissions {#propagate-permissions}

You can propagate authorizations and access rights. To do this, select the **[!UICONTROL Propagate]** option in the folder properties.

The authorizations defined in this window will then be applied to all the sub-folders of the current node. You can then overload these authorizations for each of the sub-folders.

>[!NOTE]
>
>Clearing this option for a folder does not automatically clear it for the sub-folders. You must clear it explicitly for each of the sub-folders.

### Grant access to all operators {#grant-access-to-all-operators}

In the **[!UICONTROL Security]** tab, if the **[!UICONTROL System folder]** option is selected, all operators will have access to this data, regardless of their rights. If this option is cleared, you must explicitly add the operator (or their group) to the list of authorizations in order for them to have access.

![](assets/s_ncs_user_folder_properties_security03b.png)
-->