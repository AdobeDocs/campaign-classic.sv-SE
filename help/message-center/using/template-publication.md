---
solution: Campaign Classic
product: campaign
title: Publicera mall
description: Publicering av mall för transaktionsmeddelanden
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 2%

---


# Publicera mall{#template-publication}

När meddelandemallen som skapats på kontrollinstansen är klar kan du publicera den på alla körningsinstanser. Med Publication kan du automatiskt skapa två meddelandemallar i körningsinstansen som gör att du kan skicka meddelanden som är länkade till realtids- och grupphändelser.

>[!IMPORTANT]
>
>Kom ihåg att publicera mallen när du gör ändringar i den för att ändringarna ska börja gälla vid leverans av transaktionsmeddelanden.

>[!NOTE]
>
>När du publicerar transaktionsmeddelandemallar publiceras typologiregler automatiskt på körningsinstanserna.

1. Gå till mappen **[!UICONTROL Message Center > Transactional message templates]** i trädet i kontrollinstansen.
1. Välj den mall som du vill publicera i dina körningsinstanser.
1. Klicka på **[!UICONTROL Publish]**.

   ![](assets/messagecenter_publish_model_008.png)

När publiceringen är klar skapas båda meddelandemallarna som ska användas för batch- och realtidshändelser i trädet för produktionsinstansen i mappen **[!UICONTROL Administration > Production > Message Center Execution> Default > Transactional message templates]**.

![](assets/messagecenter_deployed_model_001.png)

>[!NOTE]
>
>Om du ersätter ett befintligt fält i transaktionsmeddelandemallen, t.ex. avsändaradressen, med ett tomt värde, kommer motsvarande fält i körningsinstansen/instanserna inte att uppdateras när transaktionsmeddelandet publiceras igen. Det innehåller fortfarande det föregående värdet. Om du lägger till ett värde som inte är tomt uppdateras motsvarande fält som vanligt efter nästa publicering.
