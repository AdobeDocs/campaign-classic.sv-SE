---
product: campaign
title: Diskussionsforum
description: Lär dig använda diskussionsforum för Campaign
feature: Resource Management
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
exl-id: 222853c5-c754-4c0b-8ee4-a64b2f8677a4
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# Diskussionsforum{#discussion-forums}



Operatörer i Adobe Campaign kan använda diskussionsforum för att dela information. Följande element har ett eget forum: planer, program, kampanjer, resurser, simuleringar, aktier. Varje operator har också ett personligt forum. Alla diskussioner är offentliga, även på personliga forum.

Operatörer kan prenumerera på ett forum och få ett e-postmeddelande varje gång ett meddelande skickas.

## Gå till ett forum {#accessing-a-forum}

Gå till kontrollpanelen och klicka på **[!UICONTROL Forum]** i det övre högra hörnet. Den här länken ger dig även information om det totala antalet meddelanden i forumet.

![](assets/mrm_forum_access_link.png)

## Använd ett forum {#using-a-forum}

Meddelanden och deras svar visas i kronologisk ordning (från senaste till äldsta).

Om du vill visa innehållet i ett meddelande klickar du på meddelandehuvudet.

![](assets/mrm_forum_expand_msg.png)

**Starta en ny diskussion**

Om du vill starta en ny diskussion klickar du på **[!UICONTROL Add a discussion]** längst upp till höger. The **[!UICONTROL Discussion forum]** öppnas (se nedan).

![](assets/mrm_forum_new_thread.png)

**Publicera ett meddelande till en befintlig diskussion**

Om du vill skicka ett meddelande till en befintlig diskussion öppnar du meddelandet som du vill svara på och klickar sedan på knappen **[!UICONTROL Reply]** i det övre vänstra hörnet. The **[!UICONTROL Discussion forum]** öppnas (se nedan).

![](assets/mrm_forum_answer_msg.png)

När du svarar på ett meddelande får den som publicerade det ursprungliga meddelandet ett meddelande.

**Skriv ett meddelande**

I **[!UICONTROL Discussion forum]** box:

1. Ange texten i dialogrutan **[!UICONTROL Message]** -fält och en diskussionsrubrik i **[!UICONTROL Subject]** fält.

   ![](assets/mrm_forum_edit_msg.png)

1. Vid behov:

   * Använd dialogrutan **[!UICONTROL Operator to notify]** fält. Operatorn får ett e-postmeddelande för det här specifika meddelandet (de kommer inte att prenumerera på forumet). Om du vill meddela flera operatorer väljer du en grupp med operatorer.
   * Om du vill lägga till en bifogad fil i meddelandet klickar du på **[!UICONTROL Browse]**. Den bifogade filen kommer också att inkluderas i e-postmeddelandet. Bifogade filer kan bara skickas individuellt: om du vill skicka flera filer måste du zippa dem.

1. Klicka **[!UICONTROL Create the message]** för att lägga ut det på forumet.

>[!NOTE]
>
>När ett meddelande har skickats till forumet kan det inte längre ändras eller tas bort.

## Publicera på en operatörs personliga forum {#posting-to-the-personal-forum-of-an-operator}

Du kan skicka ett meddelande till en operatörs forum om ditt meddelande t.ex. inte gäller en viss kampanj, men du ändå vill hålla reda på konversationen i Adobe Campaign. Personliga forum är offentliga och alla operatörer kommer att se ditt meddelande. Operatören får ett meddelande varje gång någon publicerar på sitt personliga forum.

Så här kommer du åt en operatörs forum:

* Om du har de rättigheter som krävs för att få åtkomst till **[!UICONTROL Administration > Access management > Operators]** noden i Utforskaren, öppnar kontrollpanelen för den önskade operatorn och klickar på **[!UICONTROL Forum]** i det övre högra hörnet.
* Om inte, leta reda på namnet på operatorn i Adobe Campaign (via ett meddelande som skickats till forumet av den här operatorn, en uppgift som tilldelats dem) och klicka på den för att komma åt deras instrumentpanel. Du kan också be administratören att skapa en vy över operatörsmappen.

## Prenumerera på ett forum {#subscribing-to-a-forum}

Genom att prenumerera på ett forum kan du följa diskussioner. Du får ett e-postmeddelande varje gång ett meddelande skickas till forumet. Det här e-postmeddelandet innehåller meddelandetexten och eventuella bilagor. Om du vill svara på ett meddelande klickar du i e-postmeddelandet och loggar sedan in på Adobe Campaign webbgränssnitt. När du prenumererar på ett forum visas den här informationen för alla.

* Klicka på **[!UICONTROL Follow discussions]** i det övre högra avsnittet ovanför listan med meddelanden.

  ![](assets/mrm_forum_subscribe.png)

  Avsnittet blir blått och visar att du prenumererar på forumet.

* Om du vill avbryta prenumerationen klickar du på **[!UICONTROL Unsubscribe]** -knappen.

  ![](assets/mrm_forum_unsubscribe.png)

* På din personliga instrumentpanel visas de forum som du prenumererar på. Klicka på **[!UICONTROL Subscription to discussion forums]** för att visa listan och sedan klicka på det objekt som intresserar dig för att komma åt dess forum.

  ![](assets/platform_dashboard_operator_subscr_forums.png)

  Mer information om personliga instrumentpaneler finns i [det här avsnittet](../../platform/using/access-management-operators.md).

* Klicka på knappen **[!UICONTROL List of subscribers to this discussion forum]** -länken ovanför listan med meddelanden.

  ![](assets/mrm_forum_subscribers.png)

## Kontrollera meddelandeleverans {#checking-notification-delivery}

Om operatorer som prenumererar på ett forum inte får meddelanden som förväntat:

* Kontrollera att e-postadresser anges i operatörens profiler.
* Gå till **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** och kontrollera att **[!UICONTROL Jobs in discussion forums]** arbetsflödet har startats och är felfritt.
* Visa leveransloggarna:

   * På Adobe Campaign hemsida går du till **[!UICONTROL Campaigns > Navigation > Deliveries]** och sedan öppna **[!UICONTROL Discussion forum notification]** leverans.
   * Gå till Utforskaren **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** och sedan klicka **[!UICONTROL Discussion forum notifications]**.

  I **[!UICONTROL Discussion forum notifications]** finns leveransloggarna i **[!UICONTROL Edit > Delivery]** -fliken. Du kan även visa **[!UICONTROL Tracking > Log]** och **[!UICONTROL Exclusion causes]** -tabbar.
