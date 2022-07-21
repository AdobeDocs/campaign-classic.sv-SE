---
product: campaign
title: Så använder du arbetsflödesdata
description: Lär dig hur du använder arbetsflödesdata
feature: Workflows, Data Management
exl-id: 5354d608-2fea-45f9-a0aa-11c7e965ab04
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 2%

---

# Så använder du arbetsflödesdata{#how-to-use-workflow-data}

![](../../assets/v7-only.svg)

## Uppdaterar databasen {#updating-the-database}

Alla insamlade data kan användas för att uppdatera databasen eller i leveranser. Du kan till exempel utöka möjligheterna att personalisera innehåll i meddelanden (ange antalet kontrakt i meddelandet, ange den genomsnittliga kundvagnen under det senaste året, osv.) eller målgruppsanpassning (skicka ett meddelande till kontraktsparter, rikta in de 1 000 bästa abonnenterna på onlinetjänster osv.). Dessa data kan också exporteras eller arkiveras i en lista.

### Listor och direkta uppdateringar {#lists-and-direct-updates}

Data från Adobe Campaign-databasen och de befintliga listorna kan uppdateras med hjälp av två dedikerade aktiviteter:

* The **[!UICONTROL List update]** kan du lagra arbetsdokument i en datalist.

   Du kan välja en befintlig lista eller skapa den. I det här fallet beräknas namnet och eventuellt postmappen.

   ![](assets/s_user_create_list.png)

   Se [Listuppdatering](list-update.md).

* The **[!UICONTROL Update data]** aktiviteten utför en massuppdatering av fälten i databasen.

   Mer information finns i [Uppdatera data](update-data.md).

### Prenumerations-/prenumerationshantering {#subscription-unsubscription-management}

Om du vill veta mer om att prenumerera på och avsluta prenumerationer på en informationstjänst via ett arbetsflöde kan du läsa [Prenumerationstjänster](subscription-services.md).

## Skicka via ett arbetsflöde {#sending-via-a-workflow}

### Leveransaktivitet {#delivery-activity}

Leveransaktiviteten beskrivs i [Leverans](delivery.md).

### Förbättra och målinrikta leveranser {#enriching-and-targeting-deliveries}

Leveranser kan bearbeta data från arbetsflöden för att anpassa innehåll eller inom ramen för valet av målpopulation.

Inom ramen för direktutskick kan du t.ex. inkludera ytterligare data som hämtats från dataändringar som utförts i arbetsflödet i extraheringsfilen:

![](assets/s_advuser_add_data_postal_mail.png)

Förutom de vanliga personaliseringsfälten kan du lägga till anpassningsfält från arbetsflödesfaser till leveransinnehållet. De ytterligare data som definieras i arbetsflödesaktiviteterna kan behållas och göras tillgängliga i leveransguiden, vilket visas i exemplet nedan, för att definiera namnet på utdatafilen inom ramen för direktmeddelandeleverans:

![](assets/s_advuser_using_additional_data.png)

Data i arbetsflödestabellen identifieras med sitt namn: den alltid består av **targetData** länk. Mer information finns i [Måldata](data-life-cycle.md#target-data).

Inom ramen för e-postleverans kan personaliseringsfält även använda data från måltillägg som har utförts i arbetsflödesfaserna för målanpassning, vilket visas i exemplet nedan:

![](assets/s_advuser_add_data_email.png)

Om en segmentkod anges i en målaktivitet läggs den till i en specifik kolumn i arbetsflödestabellen och erbjuds tillsammans med anpassningsfälten. Om du vill visa alla anpassningsfält klickar du på **[!UICONTROL Target extension > Other...]** via personaliseringsknappen.

![](assets/s_advuser_segment_code_select.png)
