---
product: campaign
title: Publicera meddelandemallar
description: Läs om publicering och borttagning av publicering av transaktionsmeddelandemallar i Adobe Campaign Classic
feature: Transactional Messaging, Message Center, Templates
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 1d55f42b-64bf-4b1f-a317-c1f7456aa5b3
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 2%

---

# Publicera meddelandemallar {#publishing-template-messages}



## Publicera mall {#template-publication}

När [meddelandemall](../../message-center/using/creating-the-message-template.md) som skapats i kontrollinstansen är klar och när du har [testad](../../message-center/using/testing-message-templates.md) kan du publicera den. Den här processen kommer även att publicera den på alla körningsinstanser.

Med Publikationen kan du automatiskt skapa **två meddelandemallar** på körningsinstanserna, som gör att du kan skicka meddelanden som är länkade till **realtidshändelser** och **batchhändelser**.

>[!NOTE]
>
>När du publicerar transaktionsmeddelandemallar publiceras också typologiregler automatiskt på körningsinstanserna.

>[!IMPORTANT]
>
>När du gör några ändringar i en mall måste du publicera den igen för att ändringarna ska gälla vid leverans av transaktionsmeddelanden.

1. På kontrollinstansen går du till **[!UICONTROL Message Center > Transactional message templates]** mapp i trädet.
1. Välj den mall som du vill publicera i dina körningsinstanser.
1. Klicka på **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

När publiceringen är klar skapas båda meddelandemallarna som ska användas för batch- och realtidshändelser i trädet för produktionsinstansen i **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** mapp.

![](assets/messagecenter_deployed_model_001.png)

När en mall har publicerats, om motsvarande händelse aktiveras, kommer körningsinstansen att ta emot händelsen, länka den till transaktionsmallen och skicka motsvarande transaktionsmeddelande till varje mottagare. Mer information finns i [Händelsebearbetning](../../message-center/using/about-event-processing.md).

>[!NOTE]
>
>Om du ersätter ett befintligt fält i transaktionsmeddelandemallen, t.ex. avsändaradressen, med ett tomt värde, kommer motsvarande fält i körningsinstansen/instanserna inte att uppdateras när transaktionsmeddelandet publiceras igen. Det innehåller fortfarande det föregående värdet.
>
>Om du lägger till ett värde som inte är tomt uppdateras motsvarande fält som vanligt efter nästa publicering.

## Ta bort publiceringen av en mall {#template-unpublication}

När en meddelandemall har publicerats på körningsinstanserna kan den avpubliceras. Mer information om mallpubliceringsprocessen finns i [det här avsnittet](#template-publication).

* En publicerad mall kan fortfarande anropas om motsvarande händelse aktiveras: om du inte längre använder en meddelandemall bör du avpublicera den. Detta för att undvika att skicka ett oönskat transaktionsmeddelande av misstag.

  Du publicerade till exempel en meddelandemall som du bara använder för julkampanjer. Du kanske vill avpublicera den när julperioden är slut och publicera den igen nästa år.

* Du kan inte heller ta bort en transaktionsmeddelandemall som har **[!UICONTROL Published]** status. Du måste avpublicera det först.

>[!NOTE]
>
>Den här funktionen är tillgänglig från och med Campaign 20.2.

Följ stegen nedan om du vill avpublicera en transaktionsmeddelandemall.

1. På kontrollinstansen går du till **[!UICONTROL Message Center > Transactional message templates]** mapp i trädet.
1. Markera den mall som du vill avpublicera.
1. Klicka på **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Klicka på **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

Mallstatusen för transaktionsmeddelanden ändras tillbaka från **[!UICONTROL Published]** till **[!UICONTROL Being edited]**.

När borttagningen är klar:

* Båda meddelandemallarna (som används för batch- och realtidshändelser) tas bort från varje körningsinstans.

  De visas inte längre i **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** mapp (se [det här avsnittet](#template-publication)).

* När en mall har avpublicerats kan du ta bort den från kontrollinstansen.

  Om du vill göra det markerar du den i listan och klickar på **[!UICONTROL Delete]** överst till höger på skärmen.
