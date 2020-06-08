---
title: Mallpublicering
seo-title: Mallpublicering
description: Mallpublicering
seo-description: null
page-status-flag: never-activated
uuid: f83dbe5f-762c-4c58-aeed-6ec289eb522f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 43908738-a71a-49be-ac00-175f57a0555c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 71aeeda3edafc64dbe696ce6f344b8b0ccdc43d1
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---


# Opublicerad mall{#template-unpublication}

När en meddelandemall har publicerats på körningsinstanserna kan den avpubliceras.

En publicerad mall kan fortfarande anropas. Om du inte längre använder en meddelandemall bör du därför avpublicera den. Detta för att undvika att skicka ett oönskat transaktionsmeddelande av misstag. Du publicerade till exempel en meddelandemall som du bara använder för julkampanjer. Du kanske vill avpublicera den när julperioden är slut och publicera den igen nästa år.

Du kan inte heller ta bort en transaktionsmeddelandemall som har **[!UICONTROL Published]** statusen. Du måste avpublicera det först.

Följ stegen nedan om du vill avpublicera en transaktionsmeddelandemall.

1. Gå till mappen för trädet i kontrollinstansen **[!UICONTROL Message Center > Transactional message templates]** .
1. Markera den mall som du vill avpublicera.
1. Klicka på **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Klicka på **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

Mallstatus för transaktionsmeddelanden ändras tillbaka från **[!UICONTROL Published]** till **[!UICONTROL Being edited]**.

När borttagningen är klar:

* Båda meddelandemallarna (som används för batch- och realtidshändelser) tas bort från varje körningsinstans. De visas inte längre i **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** mappen.

* När en mall har avpublicerats kan du ta bort den från kontrollinstansen om det behövs. Det gör du genom att markera den i listan och klicka på **[!UICONTROL Delete]** knappen längst upp till höger på skärmen.