---
solution: Campaign Classic
product: campaign
title: Publicera mall
description: Publicera mall
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 02dee9c4cc03784ccc20f147f816798248bd10f2
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 3%

---


# Ta bort publiceringen av mallen{#template-unpublication}

När en meddelandemall har publicerats på körningsinstanserna kan den avpubliceras. Mer information om mallpubliceringsprocessen finns i [det här avsnittet](../../message-center/using/template-publication.md).

* En publicerad mall kan fortfarande anropas om motsvarande händelse aktiveras: Om du inte längre använder en meddelandemall bör du avpublicera den. Detta för att undvika att skicka ett oönskat transaktionsmeddelande av misstag.

   Du publicerade till exempel en meddelandemall som du bara använder för julkampanjer. Du kanske vill avpublicera den när julperioden är slut och publicera den igen nästa år.

* Du kan inte heller ta bort en transaktionsmeddelandemall som har statusen **[!UICONTROL Published]**. Du måste avpublicera det först.

>[!NOTE]
>
>Den här funktionen är tillgänglig från och med Campaign 20.2.

Följ stegen nedan om du vill avpublicera en transaktionsmeddelandemall.

1. Gå till mappen **[!UICONTROL Message Center > Transactional message templates]** i trädet i kontrollinstansen.
1. Markera den mall som du vill avpublicera.
1. Klicka på **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Klicka på **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

Status för transaktionsmeddelandemallen ändras tillbaka från **[!UICONTROL Published]** till **[!UICONTROL Being edited]**.

När borttagningen är klar:

* Båda meddelandemallarna (som används för batch- och realtidshändelser) tas bort från varje körningsinstans.

   De visas inte längre i mappen **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** (se [det här avsnittet](../../message-center/using/template-publication.md)).

* När en mall har avpublicerats kan du ta bort den från kontrollinstansen.

   Det gör du genom att markera den i listan och klicka på knappen **[!UICONTROL Delete]** längst upp till höger på skärmen.