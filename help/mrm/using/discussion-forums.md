---
product: campaign
title: Diskussionsforum
description: Lär dig använda diskussionsforum för Campaign
feature: Resource Management
audience: campaign
content-type: reference
hide: true
hidefromtoc: true
topic-tags: tasks--resources-and-budgets
exl-id: 222853c5-c754-4c0b-8ee4-a64b2f8677a4
source-git-commit: 942edcf028207eab2ea583949ebc99ab61539ea0
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# Diskussionsforum{#discussion-forums}



Operatörer i Adobe Campaign kan använda diskussionsforum för att dela information. Följande element har ett eget forum: planer, program, kampanjer, resurser, simuleringar, aktier. Varje operator har också ett personligt forum. Alla diskussioner är offentliga, även på personliga forum.

Operatörer kan prenumerera på ett forum och få ett e-postmeddelande varje gång ett meddelande skickas.

## Gå till ett forum {#accessing-a-forum}

Gå till kontrollpanelen och klicka på länken **[!UICONTROL Forum]** i det övre högra hörnet om du vill besöka forumet för en kampanj, en operator osv. Den här länken ger dig även information om det totala antalet meddelanden i forumet.

![](assets/mrm_forum_access_link.png)

## Använd ett forum {#using-a-forum}

Meddelanden och deras svar visas i kronologisk ordning (från senaste till äldsta).

Om du vill visa innehållet i ett meddelande klickar du på meddelandehuvudet.

![](assets/mrm_forum_expand_msg.png)

**Starta en ny diskussion**

Om du vill starta en ny diskussion klickar du på knappen **[!UICONTROL Add a discussion]** i det övre högra hörnet. **[!UICONTROL Discussion forum]**-rutan visas (se nedan).

![](assets/mrm_forum_new_thread.png)

**Publicera ett meddelande till en befintlig diskussion**

Om du vill skicka ett meddelande till en befintlig diskussion öppnar du meddelandet som du vill svara på och klickar sedan på länken **[!UICONTROL Reply]** i det övre vänstra hörnet. **[!UICONTROL Discussion forum]**-rutan visas (se nedan).

![](assets/mrm_forum_answer_msg.png)

När du svarar på ett meddelande får den som publicerade det ursprungliga meddelandet ett meddelande.

**Skriv ett meddelande**

I rutan **[!UICONTROL Discussion forum]**:

1. Ange texten i fältet **[!UICONTROL Message]** och en diskussionsrubrik i fältet **[!UICONTROL Subject]**.

   ![](assets/mrm_forum_edit_msg.png)

1. Vid behov:

   * Använd fältet **[!UICONTROL Operator to notify]** om du vill att någon ska delta i diskussionen som inte prenumererar på forumet. Operatorn får ett e-postmeddelande för det här specifika meddelandet (de kommer inte att prenumerera på forumet). Om du vill meddela flera operatorer väljer du en grupp med operatorer.
   * Klicka på **[!UICONTROL Browse]** om du vill lägga till en bifogad fil i meddelandet. Den bifogade filen kommer också att inkluderas i e-postmeddelandet. Bifogade filer kan bara skickas individuellt: om du vill skicka flera filer måste du zippa dem.

1. Klicka på **[!UICONTROL Create the message]** för att publicera den på forumet.

>[!NOTE]
>
>När ett meddelande har skickats till forumet kan det inte längre ändras eller tas bort.

## Publicera på en operatörs personliga forum {#posting-to-the-personal-forum-of-an-operator}

Du kan skicka ett meddelande till en operatörs forum om ditt meddelande t.ex. inte gäller en viss kampanj, men du ändå vill hålla reda på konversationen i Adobe Campaign. Personliga forum är offentliga och alla operatörer kommer att se ditt meddelande. Operatören får ett meddelande varje gång någon publicerar på sitt personliga forum.

Så här kommer du åt en operatörs forum:

* Om du har behörighet att komma åt noden **[!UICONTROL Administration > Access management > Operators]** i utforskaren öppnar du instrumentpanelen för den önskade operatorn och klickar på länken **[!UICONTROL Forum]** i det övre högra hörnet.
* Om inte, leta reda på namnet på operatorn i Adobe Campaign (via ett meddelande som skickats till forumet av den här operatorn, en uppgift som tilldelats dem) och klicka på den för att komma åt deras instrumentpanel. Du kan också be administratören att skapa en vy över operatörsmappen.

## Prenumerera på ett forum {#subscribing-to-a-forum}

Genom att prenumerera på ett forum kan du följa diskussioner. Du får ett e-postmeddelande varje gång ett meddelande skickas till forumet. Det här e-postmeddelandet innehåller meddelandetexten och eventuella bilagor. Om du vill svara på ett meddelande klickar du i e-postmeddelandet och loggar sedan in på Adobe Campaign webbgränssnitt. När du prenumererar på ett forum visas den här informationen för alla.

* Om du vill prenumerera på ett forum klickar du på knappen **[!UICONTROL Follow discussions]** i det övre högra avsnittet ovanför listan med meddelanden.

  ![](assets/mrm_forum_subscribe.png)

  Avsnittet blir blått och visar att du prenumererar på forumet.

* Om du vill avbryta prenumerationen på ett forum klickar du på knappen **[!UICONTROL Unsubscribe]**.

  ![](assets/mrm_forum_unsubscribe.png)

* På din personliga instrumentpanel visas de forum som du prenumererar på. Klicka på länken **[!UICONTROL Subscription to discussion forums]** för att visa listan och klicka sedan på det objekt som är intressant för dig för att komma åt dess forum.

  ![](assets/platform_dashboard_operator_subscr_forums.png)

  Mer information om personliga instrumentpaneler finns i [det här avsnittet](../../platform/using/access-management-operators.md).

* Om du vill se vem som prenumererar på ett forum klickar du på länken **[!UICONTROL List of subscribers to this discussion forum]** ovanför listan med meddelanden.

  ![](assets/mrm_forum_subscribers.png)

## Kontrollera meddelandeleverans {#checking-notification-delivery}

Om operatorer som prenumererar på ett forum inte får meddelanden som förväntat:

* Kontrollera att e-postadresser anges i operatörens profiler.
* Gå till noden **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** och kontrollera att arbetsflödet för **[!UICONTROL Jobs in discussion forums]** har startats utan fel.
* Visa leveransloggarna:

   * Gå till **[!UICONTROL Campaigns > Navigation > Deliveries]** på startsidan för Adobe Campaign och öppna sedan leveransen av **[!UICONTROL Discussion forum notification]**.
   * Gå till **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** i Utforskaren och klicka sedan på **[!UICONTROL Discussion forum notifications]**.

  I rutan **[!UICONTROL Discussion forum notifications]** finns leveransloggarna på fliken **[!UICONTROL Edit > Delivery]**. Du kan även visa flikarna **[!UICONTROL Tracking > Log]** och **[!UICONTROL Exclusion causes]**.
