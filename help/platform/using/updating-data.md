---
product: campaign
title: Uppdaterar data
description: Uppdaterar data
feature: Data Management
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: f7dfbc22-4ac3-4b61-927f-34ecc4e35154
source-git-commit: 8aceafa362b80f6e34edfd91a71551a58501a3d0
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 1%

---

# Uppdatera data{#updating-data}

>[!NOTE]
>
>Den här sidan gäller endast för operatorer som ansluter till Campaign med inbyggd autentisering.

De data som är länkade till en mottagares profil kan uppdateras manuellt eller automatiskt.

## Konfigurera en automatisk uppdatering {#setting-up-an-automatic-update}

En automatisk uppdatering kan konfigureras via ett arbetsflöde. Mer information om detta finns i [det här avsnittet](../../workflow/using/update-data.md).

## Utför en massuppdatering {#performing-a-mass-update}

Om du vill utföra manuella uppdateringar högerklickar du på de valda mottagarna för att använda snabbmenyn **[!UICONTROL Actions]** eller använder ikonen **[!UICONTROL Actions]** .

![](assets/s_ncs_user_action_icon.png)

Det finns två typer av uppdateringar: massuppdatering för en uppsättning mottagare och datasammanfogning mellan två profiler. För varje åtgärd kan du konfigurera uppdateringen med hjälp av en guide.

### Massuppdatering {#mass-update}

Använd **[!UICONTROL Action > Mass update of selected lines...]** för massuppdatering. Guiden hjälper dig att konfigurera och köra uppdateringen.

Det första steget i guiden är att ange vilka fält som ska uppdateras.

I den vänstra delen av guiden visas en lista med tillgängliga fält. Använd fältet **[!UICONTROL Find]** för att köra en sökning i dessa fält. Tryck på **Retur** för att bläddra i listan. Fältnamnen som matchar inmatningen visas i fet stil, vilket visas nedan.

Dubbelklicka på de fält som ska uppdateras för att visa dem i den högra delen av guiden.

![](assets/s_ncs_user_update_wizard01_1.png)

Om ett fel inträffar använder du knappen **[!UICONTROL Delete]** för att ta bort ett fält från listan med fält som ska uppdateras.

Välj eller ange de värden som ska användas för de profiler som ska uppdateras.

![](assets/s_ncs_user_update_wizard01_12.png)

Du kan klicka på **[!UICONTROL Distribution of values]** om du vill visa fördelningen av värden för det markerade fältet för mottagarna i den aktuella mappen (inte bara de mottagare som påverkas av uppdateringen).

![](assets/s_ncs_user_update_wizard01_2.png)

Du kan definiera filter för att visa värdefördelningen i det här fönstret eller ändra den aktuella mappen för att visa värdefördelningen i en annan mapp. Dessa är skrivskyddade åtgärder. De påverkar inte konfigurationen för den uppdatering som definieras.

![](assets/s_ncs_user_update_wizard01_3.png)

Stäng det här fönstret och klicka på **[!UICONTROL Next]** för att visa det andra uppdateringsguiden. I det här steget kan du starta uppdateringen genom att klicka på **[!UICONTROL Start]**.

![](assets/s_ncs_user_update_wizard01_4.png)

Information om uppdateringskörning visas i den övre delen av guiden.

Med **[!UICONTROL Stop]** kan du avbryta uppdateringen, men vissa poster kan ha uppdaterats, och om du stoppar processen avbryts inte uppdateringarna. Förloppsindikatorn visar hur långt åtgärden har kommit.

### Sammanfoga data {#merge-data}

Välj **[!UICONTROL Merge selected lines...]** om du vill starta sammanfogningen av två mottagarprofiler. Profilerna som ska sammanfogas måste vara markerade innan du väljer alternativet. Sammanfogningen konfigureras och startas med en guide.

I guiden visas de värden som ska hämtas för varje fält som har slutförts i en eller flera av källprofilerna. Om ett eller flera fält i de profiler som ska sammanfogas har olika värden visas de i avsnittet **[!UICONTROL List of conflicts]**. Du kan sedan välja standardprofil med alternativknapparna under listan, som i följande exempel:

![](assets/s_ncs_user_merge_wizard01_1.png)

Klicka på **[!UICONTROL Compute]** om du vill visa resultatet av ditt val.

![](assets/s_ncs_user_merge_wizard01_2.png)

Kontrollera **[!UICONTROL Result]**-kolumnerna i båda fönsteravsnitten och klicka på **[!UICONTROL Finish]** för att köra sammanfogningen.

## Exportera data {#exporting-data}

Innehållet i en lista kan exporteras. Så här konfigurerar och kör du exporten:

1. Välj de poster som ska exporteras.
1. Högerklicka och välj **[!UICONTROL Export...]**.

   ![](assets/s_ncs_user_export_list.png)

1. Markera sedan de data som ska extraheras. Som standard läggs alla kolumner som visas till i utdatakolumnerna.

   ![](assets/s_ncs_user_export_list_start.png)

   Mer information om hur du konfigurerar exportguiden finns i [det här avsnittet](../../platform/using/executing-export-jobs.md).

## Prenumerera på en tjänst {#subscribing-to-a-service}

I de flesta fall prenumererar mottagarna på ett nyhetsbrev via en dedikerad landningssida, vilket förklaras i [det här avsnittet](../../delivery/using/managing-subscriptions.md). Filtrerade mottagares profiler kan dock prenumerera på en tjänst (nyhetsbrev eller virala tjänster) manuellt. Så här gör du:

1. Markera de mottagare som du vill prenumerera på och högerklicka.
1. Välj **[!UICONTROL Actions > Subscribe selection to a service]**.

   ![](assets/s_ncs_user_selection_subscribe_service.png)

1. Välj önskad tjänst och klicka på **[!UICONTROL Next]**:

   ![](assets/s_ncs_user_selection_subscribe_service_2.png)

   >[!NOTE]
   >
   >Med den här redigeraren kan du skapa en ny tjänst: klicka på knappen **[!UICONTROL Create]**.

1. Du kan **[!UICONTROL Send a confirmation message]** till mottagare. Innehållet i det här meddelandet kan konfigureras i det prenumerationsscenario som är länkat till den valda tjänsten.
1. Klicka på knappen **[!UICONTROL Start]** för att köra prenumerationsprocessen.

   ![](assets/s_ncs_user_selection_subscribe_service_3.png)

I fönstrets övre del kan du övervaka körningsprocessen. Med knappen **[!UICONTROL Stop]** kan du stoppa processen. Mottagare som redan har bearbetats kommer dock att prenumereras.

Om du avmarkerar alternativet **[!UICONTROL Do not keep a trace of this job in the database]** kan du välja (eller skapa) körningsmappen där informationen om den här processen lagras.

Om du vill kontrollera processen går du till fliken **[!UICONTROL Subscriptions]** på profilerna för mottagarna som berörs av den här åtgärden, eller till fliken **[!UICONTROL Subscriptions]** som du kommer åt via noden **[!UICONTROL Profiles and Targets > Services and Subscriptions]**.

![](assets/s_ncs_user_selection_subscribe_service_4.png)

>[!NOTE]
>
>Mer information om hur du skapar och konfigurerar informationstjänster finns på [den här sidan](../../delivery/using/managing-subscriptions.md).
