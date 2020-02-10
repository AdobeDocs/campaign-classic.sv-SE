---
title: Diskussionsforum
seo-title: Diskussionsforum
description: Diskussionsforum
seo-description: null
page-status-flag: never-activated
uuid: 6253bb32-c71d-45ac-bc03-027131ae95a5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
discoiquuid: 88eb17b6-5206-4064-9cd9-b4645a85c609
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Diskussionsforum{#discussion-forums}

Adobe Campaign-operatorer kan använda diskussionsforum för att dela information. Följande element har ett eget forum: planer, program, kampanjer, resurser, simuleringar, aktier. Varje operator har också ett personligt forum. Alla diskussioner är offentliga, även på personliga forum.

Operatörer kan prenumerera på ett forum och få ett e-postmeddelande varje gång ett meddelande skickas.

## Åtkomst till ett forum {#accessing-a-forum}

Om du vill besöka ett forum för en kampanj, en operatör osv., går du till kontrollpanelen och klickar på **[!UICONTROL Forum]** länken i det övre högra hörnet. Den här länken ger dig även det totala antalet meddelanden i forumet.

![](assets/mrm_forum_access_link.png)

## Använda ett forum {#using-a-forum}

Meddelanden och deras svar visas i kronologisk ordning (från senaste till äldsta).

Om du vill visa innehållet i ett meddelande klickar du på meddelandehuvudet.

![](assets/mrm_forum_expand_msg.png)

**Starta en ny diskussion**

Om du vill starta en ny diskussion klickar du på **[!UICONTROL Add a discussion]** knappen i det övre högra hörnet. Kartongen visas **[!UICONTROL Discussion forum]** (se nedan).

![](assets/mrm_forum_new_thread.png)

**Publicera ett meddelande till en befintlig diskussion**

Om du vill skicka ett meddelande till en befintlig diskussion öppnar du meddelandet som du vill svara på och klickar sedan på **[!UICONTROL Reply]** länken i det övre vänstra hörnet. Kartongen visas **[!UICONTROL Discussion forum]** (se nedan).

![](assets/mrm_forum_answer_msg.png)

När du svarar på ett meddelande får den som publicerade det ursprungliga meddelandet ett meddelande.

**Skriva ett meddelande**

I **[!UICONTROL Discussion forum]** kartongen:

1. Skriv texten i **[!UICONTROL Message]** fältet och en diskussionsrubrik i **[!UICONTROL Subject]** fältet.

   ![](assets/mrm_forum_edit_msg.png)

1. Vid behov:

   * Använd **[!UICONTROL Operator to notify]** fältet om du vill att någon ska delta i diskussionen som inte prenumererar på forumet. Operatorn får ett e-postmeddelande för det här specifika meddelandet (de kommer inte att prenumerera på forumet). Om du vill meddela flera operatorer väljer du en grupp med operatorer.
   * Om du vill lägga till en bifogad fil i meddelandet klickar du på **[!UICONTROL Browse]**. Den bifogade filen kommer också att inkluderas i e-postmeddelandet. Bifogade filer får endast skickas individuellt: om du vill skicka flera filer måste du zippa upp dem.

1. Klicka **[!UICONTROL Create the message]** för att publicera den på forumet.

>[!NOTE]
>
>När ett meddelande har skickats till forumet kan det inte längre ändras eller tas bort.

## Publicering på en operatörs personliga forum {#posting-to-the-personal-forum-of-an-operator}

Du kan publicera ett meddelande på forumet för en operatör om ditt meddelande t.ex. inte gäller en viss kampanj, men du ändå vill hålla reda på konversationen i Adobe Campaign. Personliga forum är offentliga och alla operatörer kommer att se ditt meddelande. Operatören får ett meddelande varje gång någon publicerar på sitt personliga forum.

Så här kommer du åt en operatörs forum:

* Om du har de rättigheter som krävs för att få åtkomst till **[!UICONTROL Administration > Access management > Operators]** noden i utforskaren öppnar du kontrollpanelen för den önskade operatorn och klickar på **[!UICONTROL Forum]** länken i det övre högra hörnet.
* Om inte, leta reda på namnet på operatorn i Adobe Campaign (via ett meddelande som skickats till forumet av den här operatorn, en uppgift som tilldelats honom) och klicka på den för att komma åt deras instrumentpanel. Du kan också be administratören att skapa en vy över operatörsmappen.

## Prenumerera på ett forum {#subscribing-to-a-forum}

Genom att prenumerera på ett forum kan du följa diskussioner. Du får ett e-postmeddelande varje gång ett meddelande skickas till forumet. Det här e-postmeddelandet innehåller meddelandetexten och eventuella bilagor. Om du vill svara på ett meddelande klickar du i e-postmeddelandet och loggar sedan in på webbgränssnittet i Adobe Campaign. När du prenumererar på ett forum visas den här informationen för alla.

* Om du vill prenumerera på ett forum klickar du på **[!UICONTROL Follow discussions]** knappen i det övre högra avsnittet ovanför listan med meddelanden.

   ![](assets/mrm_forum_subscribe.png)

   Avsnittet blir blått och visar att du prenumererar på forumet.

* Klicka på **[!UICONTROL Unsubscribe]** knappen om du vill avbryta prenumerationen på ett forum.

   ![](assets/mrm_forum_unsubscribe.png)

* På din personliga instrumentpanel visas de forum som du prenumererar på. Klicka på **[!UICONTROL Subscription to discussion forums]** länken för att visa listan och klicka sedan på det objekt som du vill ska få åtkomst till dess forum.

   ![](assets/platform_dashboard_operator_subscr_forums.png)

   Mer information om personliga instrumentpaneler finns i [det här avsnittet](../../platform/using/access-management.md#operators).

* Om du vill se vem som prenumererar på ett forum klickar du på **[!UICONTROL List of subscribers to this discussion forum]** länken ovanför listan med meddelanden.

   ![](assets/mrm_forum_subscribers.png)

## Kontrollerar meddelandeleverans {#checking-notification-delivery}

Om operatorer som prenumererar på ett forum inte får meddelanden som förväntat:

* Kontrollera att e-postadresser anges i operatörens profiler.
* Gå till **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** noden och kontrollera att **[!UICONTROL Jobs in discussion forums]** arbetsflödet har startats och är felfritt.
* Visa leveransloggarna:

   * På startsidan för Adobe Campaign går du till **[!UICONTROL Campaigns > Navigation > Deliveries]** och öppnar sedan **[!UICONTROL Discussion forum notification]** leveransen.
   * Gå till Utforskaren **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** och klicka sedan **[!UICONTROL Discussion forum notifications]**.
   I **[!UICONTROL Discussion forum notifications]** rutan finns leveransloggarna på **[!UICONTROL Edit > Delivery]** fliken. Du kan även visa **[!UICONTROL Tracking > Log]** och **[!UICONTROL Exclusion causes]** flikarna.

