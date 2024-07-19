---
product: campaign
title: Skapa och hantera listor
description: Lär dig skapa och hantera listor
feature: Profiles
role: User
level: Beginner
exl-id: 711b84cd-bac8-4f1a-9999-0124fbfc3a01
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 8%

---

# Skapa och hantera listor{#creating-and-managing-lists}



## Vad är en lista? {#about-lists-in-adobe-campaign}

En lista är en statisk uppsättning profiler som kan användas för leveransåtgärder eller uppdateras under importåtgärder eller under arbetsflödeskörning. En grupp som har extraherats från databasen via en fråga kan till exempel innehålla en lista.

Listor skapas och hanteras via länken **[!UICONTROL Lists]** på fliken **[!UICONTROL Profiles and targets]**.

![](assets/s_ncs_user_interface_group_link.png)

Det finns två typer av listor i Adobe Campaign:

* **[!UICONTROL Group]**-typ: **[!UICONTROL Group]**-typlistorna tillhör en **statisk**-lista med personer som har valts enligt specifika villkor. Listan är som en ögonblicksbild av en uppsättning profiler. Observera att den inte uppdateras automatiskt om profiler läggs till i databasen.

  Mer information om hur du skapar en **[!UICONTROL Group]**-typlista finns på den här [sidan](#creating-a-profile-list-from-a-group).

* **[!UICONTROL List]**-typ: Med typlistan **[!UICONTROL List]** kan du använda arbetsflöden för att skapa och hantera listor. De här listorna är specifika från dataimport som kan uppdateras via den dedikerade **[!UICONTROL List update]**-arbetsflödesaktiviteten.

  Till skillnad från typlistan **[!UICONTROL Group]** kan den här typlistan uppdateras automatiskt med en **[!UICONTROL Scheduler]**-aktivitet. Observera att ett exempel på hur du skapar **[!UICONTROL List]** typlistor finns på [den här sidan](../../workflow/using/list-update.md).

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#create-list-video)

## Skapa en profillista från en grupp {#creating-a-profile-list-from-a-group}

**[!UICONTROL Group]** typlistor som skapas via länken **[!UICONTROL Profiles and targets]** måste baseras på Adobe Campaign standardprofiltabell (nms:receive).

>[!NOTE]
>
>Om du vill skapa listor som innehåller andra typer av data måste du köra ett arbetsflöde. Om du till exempel använder en fråga i besökstabellen och sedan uppdaterar listan, kan du skapa en besökslista. Mer information om arbetsflöden finns i [det här avsnittet](../../workflow/using/about-workflows.md).

Så här skapar du en ny **[!UICONTROL Group]**-typlista:

1. Klicka på knappen **[!UICONTROL Create]** och välj **[!UICONTROL New list]**.

   ![](assets/s_ncs_user_new_group.png)

1. Ange informationen på fliken **[!UICONTROL Edit]** i fönstret där listan skapas.

   * Ange listnamnet i fältet **[!UICONTROL Label]** och ändra det interna namnet om det behövs.
   * Lägg till en beskrivning av den här listan.
   * Du kan ange ett förfallodatum: när det här datumet nås rensas listan och tas automatiskt bort.

     ![](assets/list_expiration_date.png)

1. Klicka på **[!UICONTROL Add]** på fliken **[!UICONTROL Content]** för att välja de profiler som tillhör listan.

   ![](assets/s_ncs_user_add_group.png)

1. Klicka på **[!UICONTROL Save]** om du vill spara listan. Sedan läggs den till i översikten över listor.

Du kan skapa nya profiler direkt från fönstret Lägg till profiler genom att klicka på **[!UICONTROL Create]**. Profilen läggs till i databasen.

![](assets/s_ncs_user_new_recipient_from_group.png)

Profillistan kan konfigureras precis som andra listor. Se [det här avsnittet](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## Länka data till en lista {#linking-data-to-a-list}

>[!NOTE]
>
>Det går bara att länka data till en lista med en **[!UICONTROL Group]**-typlista.

Profilerna för en uppsättning profiler kan filtreras och länkas till en lista. Leveransåtgärder kan sedan skickas till den här listan, till målprofiler. Så här grupperar du profiler:

1. Välj profiler och högerklicka.
1. Välj **[!UICONTROL Actions > Associate selection with a list...]**.

   ![](assets/s_ncs_user_add_selection_to_group.png)

1. Välj önskad lista eller skapa en ny lista med knappen **[!UICONTROL Create]** och klicka sedan på **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_add_selection_to_group_2.png)

1. Klicka på knappen **[!UICONTROL Start]**.

   ![](assets/s_ncs_user_add_selection_to_group_3.png)

Alternativet **[!UICONTROL Recreate the list]** tar bort det tidigare innehållet från listan. Det här läget är optimerat eftersom ingen fråga behövs för att kontrollera om profilerna redan är länkade till listan.

Om du avmarkerar alternativet **[!UICONTROL No trace of this job is saved in the database]** kan du välja (eller skapa) körningsmappen där den information som är länkad till den här processen lagras.

I fönstrets övre del kan du övervaka körningen. Med knappen **[!UICONTROL Stop]** kan du stoppa processen. Kontakter som redan har bearbetats länkas till listan.

Du kan övervaka processen via fliken **[!UICONTROL Lists]** för de profiler som berörs av den här åtgärden:

![](assets/s_ncs_user_add_selection_to_group_4.png)

Du kan även redigera listan via Adobe Campaign hemsida: klicka på menyn **[!UICONTROL Profiles and Targets > Lists]** och välj den aktuella listan. På fliken **[!UICONTROL Content]** visas de profiler som är länkade till den här listan.

![](assets/s_ncs_user_add_selection_to_group_5.png)

## Ta bort en profil från en lista {#removing-a-profile-from-a-list}

Om du vill ta bort en profil från en lista kan du:

* Redigera listan, markera profilen på fliken **[!UICONTROL Content]** och klicka sedan på ikonen **[!UICONTROL Delete]** .

  ![](assets/list_remove_a_recipient.png)

* Redigera profilen, klicka på fliken **[!UICONTROL List]** och sedan på ikonen **[!UICONTROL Delete]** .

  ![](assets/recipient_remove_a_list.png)

## Ta bort en lista med profiler {#deleting-a-list-of-profiles}

Du kan ta bort en eller flera listor från grupplistan i Adobe Campaign-trädet. Det gör du genom att redigera trädet via länken **[!UICONTROL Advanced > Explorer]** på Adobe Campaign hemsida. Markera gruppen/grupperna och högerklicka. Välj **[!UICONTROL Delete]**.  Ett varningsmeddelande ber dig bekräfta borttagningen.

>[!NOTE]
>
>När du tar bort en lista påverkas inte profilerna i listan, men data i deras profil uppdateras.

## Självstudievideo {#create-list-video}

### Skapa en lista med mottagare

En lista är en statisk uppsättning mottagare som kan användas för leveransåtgärder och som uppdateras i och med importer eller medan arbetsflödet körs. En lista över mottagare kallas även för en målgrupp.

Lär dig hur du skapar en målgrupp genom att konfigurera en lista med mottagare från Utforskaren.

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

### Så här skapar du en lista med mottagare i ett arbetsflöde {#create-list-in-a-wf-video}

Lär dig hur du skapar ett arbetsflöde för att rikta in dig på mottagare och hur du gör det återkommande innan du använder listan i ett e-postmål.

>[!VIDEO](https://video.tv.adobe.com/v/25603?quality=12)

Ytterligare Campaign Classic om instruktionsvideor finns [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
