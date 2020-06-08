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
source-git-commit: 1486e897a125520c51661db3030c62ab380fb173
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Mallpublicering{#template-publication}

När meddelandemallen som skapats på kontrollinstansen är klar kan du publicera den på alla körningsinstanser. Med Publication kan du automatiskt skapa två meddelandemallar i körningsinstansen som gör att du kan skicka meddelanden som är länkade till realtids- och grupphändelser.

>[!IMPORTANT]
>
>Kom ihåg att publicera mallen när du gör ändringar i den för att ändringarna ska börja gälla vid leverans av transaktionsmeddelanden.

>[!NOTE]
>
>När du publicerar transaktionsmeddelandemallar publiceras typologiregler automatiskt på körningsinstanserna.

1. Gå till mappen för trädet i kontrollinstansen **[!UICONTROL Message Center > Transactional message templates]** .
1. Välj den mall som du vill publicera i dina körningsinstanser.
1. Klicka på **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

När publiceringen är klar skapas båda meddelandemallarna som ska användas för batch- och realtidshändelser i trädet för produktionsinstansen i **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]** mappen.

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>Om du ersätter ett befintligt fält i transaktionsmeddelandemallen, t.ex. avsändaradressen, med ett tomt värde, kommer motsvarande fält i körningsinstansen/instanserna inte att uppdateras när transaktionsmeddelandet publiceras igen. Det innehåller fortfarande det föregående värdet. Om du lägger till ett värde som inte är tomt uppdateras motsvarande fält som vanligt efter nästa publicering.
