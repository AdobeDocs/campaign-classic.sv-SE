---
product: campaign
title: Arbetsflöde för leveranser över flera kanaler
description: Läs mer om arbetsflöden för flerkanalsleverans
feature: Workflows, Channels Activity
exl-id: dfd36d2c-44ff-49a9-80b4-09eaf3377072
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 3%

---

# Arbetsflöde för leveranser över flera kanaler{#cross-channel-delivery-workflow}



I det här användningsexemplet visas ett exempel med ett arbetsflöde för flerkanalsleverans. Det allmänna konceptet med flerkanalsleveranser presenteras i [det här avsnittet](cross-channel-deliveries.md).

Målet är att segmentera en målgrupp från mottagarna av databasen i olika grupper i syfte att skicka ett e-postmeddelande till en grupp och ett SMS-meddelande till en annan grupp.

De huvudsakliga implementeringsstegen för det här fallet är följande:

1. Skapa en **[!UICONTROL Query]** målgruppsaktiviteter.
1. Skapa en **[!UICONTROL Email delivery]** aktivitet som innehåller en länk till ett erbjudande.
1. Använda **[!UICONTROL Split]** aktivitet till:

   * Skicka ytterligare ett e-postmeddelande till mottagare som inte öppnade det första e-postmeddelandet.
   * Skicka ett SMS till mottagarna som öppnade e-postmeddelandet men inte klickade på länken till erbjudandet.
   * Lägg till mottagarna som öppnade e-postmeddelandet i databasen och klickade på länken.

![](assets/wkf_cross-channel_7.png)

## Steg 1: Målgruppsanpassning {#step-1--targeting-the-audience}

Om du vill definiera målet skapar du en fråga som identifierar mottagarna.

1. Skapa en kampanj. Mer information om detta finns i [det här avsnittet](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign).
1. I **[!UICONTROL Targeting and workflows]** fliken med kampanjen, lägg till en **Fråga** till ditt arbetsflöde. Mer information om hur du använder den här aktiviteten finns i [det här avsnittet](query.md).
1. Definiera de mottagare som ska ta emot leveranserna. Välj till exempel Guldmedlemmar som måldimension.
1. Lägg till filtervillkor i frågan. I det här exemplet väljer du mottagare som har en e-postadress och ett mobilnummer.

   ![](assets/wkf_cross-channel_3.png)

1. Spara ändringarna.

## Steg 2: Skapa ett e-postmeddelande med ett erbjudande {#step-2--creating-an-email-including-an-offer}

1. Skapa en **[!UICONTROL Email delivery]** och dubbelklicka på den i arbetsflödet för att redigera den. Mer information om hur du skapar e-postmeddelanden finns i [det här avsnittet](../../delivery/using/about-email-channel.md).
1. Designa meddelandet och infoga en länk med ett erbjudande i innehållet.

   ![](assets/wkf_cross-channel_1.png)

   Mer information om hur du integrerar ett erbjudande i ett meddelande finns i [det här avsnittet](../../interaction/using/integrating-an-offer-via-the-wizard.md#delivering-with-a-call-to-the-offer-engine).

1. Spara ändringarna.
1. Högerklicka på **[!UICONTROL Email delivery]** för att öppna den.
1. Välj **[!UICONTROL Generate an outbound transition]** för att återställa populationen och spårningsloggarna.

   ![](assets/wkf_cross-channel_2.png)

   På så sätt kan du använda den här informationen för att skicka ytterligare leveranser beroende på mottagarnas beteenden när du tar emot det första e-postmeddelandet.

1. Lägg till en **[!UICONTROL Wait]** om du vill att mottagarna ska kunna öppna e-postmeddelandet i några dagar.

   ![](assets/wkf_cross-channel_4.png)

## Steg 3: Segmentera målgruppen {#step-3--segmenting-the-resulting-audience}

När målet har identifierats och första leveransen har skapats måste du segmentera målet i olika populationer med filtervillkoren.

1. Lägg till en **Dela** till arbetsflödet och öppna det. Mer information om hur du använder den här aktiviteten finns i [det här avsnittet](split.md).
1. Skapa tre segment från populationen som beräknas uppströms i frågan.

   ![](assets/wkf_cross-channel_6.png)

1. För den första delmängden väljer du **[!UICONTROL Add a filtering condition on the inbound population]** och klicka **[!UICONTROL Edit]**.

   ![](assets/wkf_cross-channel_8.png)

1. Välj **[!UICONTROL Recipients of a delivery]** som begränsningsfilter och klicka på **[!UICONTROL Next]**.

   ![](assets/wkf_cross-channel_9.png)

1. Välj **[!UICONTROL Recipients who have not opened or clicked (email)]** från **[!UICONTROL Behavior]** nedrullningsbar lista och välj e-postmeddelandet med det erbjudande du vill skicka från leveranslistan. Klicka på **[!UICONTROL Finish]**.

   ![](assets/wkf_cross-channel_10.png)

1. Fortsätt på samma sätt för den andra delmängden och välj **[!UICONTROL Recipients who have not clicked (email)]** från **[!UICONTROL Behavior]** nedrullningsbar lista.

   ![](assets/wkf_cross-channel_11.png)

1. För den tredje delmängden, efter att du har valt **[!UICONTROL Add a filtering condition on the inbound population]** och klicka **[!UICONTROL Edit]** väljer du **[!UICONTROL Use a specific filtering dimension]** alternativ.
1. Välj **[!UICONTROL Recipient tracking log]** från **[!UICONTROL Filtering dimension]** nedrullningsbar lista, markera **[!UICONTROL Filtering conditions]** från **[!UICONTROL List of restriction filters]** och klicka **[!UICONTROL Next]**.

   ![](assets/wkf_cross-channel_12.png)

1. Välj filtervillkoren enligt följande:

   ![](assets/wkf_cross-channel_13.png)

1. Klicka **[!UICONTROL Finish]** för att spara ändringarna.

## Steg 4: Slutför arbetsflödet {#step-4--finalizing-the-workflow}

1. Lägg till relevanta aktiviteter i arbetsflödet efter de tre deluppsättningarna som är resultatet av **[!UICONTROL Split]** aktivitet:

   * Lägg till en **[!UICONTROL Email delivery]** för att skicka ett påminnelsemejl till den första delmängden.
   * Lägg till en **[!UICONTROL Mobile delivery]** aktivitet för att skicka ett SMS-meddelande till den andra delmängden.
   * Lägg till en **[!UICONTROL List update]** för att lägga till motsvarande mottagare i databasen.

1. Dubbelklicka på leveransaktiviteterna i arbetsflödet för att redigera dem. Mer information om hur du skapar e-postmeddelanden och ett SMS finns i [E-postkanal](../../delivery/using/about-email-channel.md) och [SMS-kanal](../../delivery/using/sms-channel.md).
1. Dubbelklicka på **[!UICONTROL List update]** aktivitet och välj **[!UICONTROL Generate an outbound transition]** alternativ.

   Du kan sedan exportera de resulterande mottagarna från Adobe Campaign till Adobe Experience Cloud. Du kan till exempel använda målgruppen i Adobe Target genom att lägga till en **[!UICONTROL Update shared audience]** till arbetsflödet. Mer information finns i [Exportera en målgrupp](../../integrations/using/importing-and-exporting-audiences.md#exporting-an-audience).

1. Klicka på **Starta** i åtgärdsfältet för att köra arbetsflödet.

Den befolkning som **Fråga** aktiviteten segmenteras för att ta emot ett e-postmeddelande eller ett SMS-meddelande enligt mottagarnas beteenden. Den återstående populationen läggs till i databasen med **[!UICONTROL List update]** aktivitet.
