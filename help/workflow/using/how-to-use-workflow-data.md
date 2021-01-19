---
solution: Campaign Classic
product: campaign
title: Så använder du arbetsflödesdata
description: Lär dig hur du använder arbetsflödesdata
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 1901db70fde2b7b3c2789154bd93160012cd4c29
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 2%

---


# Så använder du arbetsflödesdata{#how-to-use-workflow-data}

## Uppdaterar databasen {#updating-the-database}

Alla insamlade data kan användas för att uppdatera databasen eller i leveranser. Du kan till exempel utöka möjligheterna att personalisera innehåll i meddelanden (ange antalet kontrakt i meddelandet, ange den genomsnittliga kundvagnen under det senaste året, osv.) eller målgruppsanpassning (skicka ett meddelande till kontraktsparter, rikta in de 1 000 bästa abonnenterna på onlinetjänster osv.). Dessa data kan också exporteras eller arkiveras i en lista.

### Listor och direkta uppdateringar {#lists-and-direct-updates}

Data från Adobe Campaign-databasen och de befintliga listorna kan uppdateras med hjälp av två dedikerade aktiviteter:

* Med aktiviteten **[!UICONTROL List update]** kan du lagra arbetstabeller i en datalist.

   Du kan välja en befintlig lista eller skapa den. I det här fallet beräknas namnet och eventuellt postmappen.

   ![](assets/s_user_create_list.png)

   Se [Listuppdatering](../../workflow/using/list-update.md).

* Aktiviteten **[!UICONTROL Update data]** utför en massuppdatering av fälten i databasen.

   Mer information finns i [Uppdatera data](../../workflow/using/update-data.md).

### Hantering av prenumeration/avprenumeration {#subscription-unsubscription-management}

Om du vill veta mer om att prenumerera på och avsluta prenumerationer på en informationstjänst via ett arbetsflöde kan du läsa [Prenumerationstjänster](../../workflow/using/subscription-services.md).

## Skicka via ett arbetsflöde {#sending-via-a-workflow}

### Leveransaktivitet {#delivery-activity}

Leveransaktiviteten anges i [Delivery](../../workflow/using/delivery.md).

### Förbättra och målinrikta leveranser {#enriching-and-targeting-deliveries}

Leveranser kan bearbeta data från arbetsflöden för att anpassa innehåll eller inom ramen för valet av målpopulation.

Inom ramen för direktutskick kan du t.ex. inkludera ytterligare data som hämtats från dataändringar som utförts i arbetsflödet i extraheringsfilen:

![](assets/s_advuser_add_data_postal_mail.png)

Förutom de vanliga personaliseringsfälten kan du lägga till anpassningsfält från arbetsflödesfaser till leveransinnehållet. De ytterligare data som definieras i arbetsflödesaktiviteterna kan behållas och göras tillgängliga i leveransguiden, vilket visas i exemplet nedan, för att definiera namnet på utdatafilen inom ramen för direktmeddelandeleverans:

![](assets/s_advuser_using_additional_data.png)

Data i arbetsflödestabellen identifieras med sitt namn: den alltid består av länken **targetData**. Mer information finns i [Måldata](../../workflow/using/data-life-cycle.md#target-data).

Inom ramen för e-postleverans kan personaliseringsfält även använda data från måltillägg som har utförts i arbetsflödesfaserna för målanpassning, vilket visas i exemplet nedan:

![](assets/s_advuser_add_data_email.png)

Om en segmentkod anges i en målaktivitet läggs den till i en specifik kolumn i arbetsflödestabellen och erbjuds tillsammans med anpassningsfälten. Om du vill visa alla anpassningsfält klickar du på länken **[!UICONTROL Target extension > Other...]** som är tillgänglig via personaliseringsknappen.

![](assets/s_advuser_segment_code_select.png)
