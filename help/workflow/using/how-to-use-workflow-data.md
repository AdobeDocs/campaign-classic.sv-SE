---
title: Så här använder du arbetsflödesdata
seo-title: Så här använder du arbetsflödesdata
description: Så här använder du arbetsflödesdata
seo-description: null
page-status-flag: never-activated
uuid: ed03f14b-1b53-426e-9213-22cb2f3deb19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: ec3844ca-8d80-4ddc-b08c-f18a6919bb28
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Så här använder du arbetsflödesdata{#how-to-use-workflow-data}

## Uppdaterar databasen {#updating-the-database}

Alla insamlade data kan användas för att uppdatera databasen eller i leveranser. Du kan till exempel utöka möjligheterna att personalisera innehåll i meddelanden (ange antalet kontrakt i meddelandet, ange den genomsnittliga kundvagnen under det senaste året, osv.) eller målgruppsanpassning (skicka ett meddelande till kontraktsparter, rikta in de 1 000 bästa abonnenterna på onlinetjänster osv.). Dessa data kan också exporteras eller arkiveras i en lista.

### Listor och direkta uppdateringar {#lists-and-direct-updates}

Data från Adobe Campaign-databasen och befintliga listor kan uppdateras med två dedikerade aktiviteter:

* Med hjälp av den här **[!UICONTROL List update]** aktiviteten kan du lagra arbetstabeller i en datalist.

   Du kan välja en befintlig lista eller skapa den. I det här fallet beräknas namnet och eventuellt postmappen.

   ![](assets/s_user_create_list.png)

   Se [Listuppdatering](../../workflow/using/list-update.md).

* Aktiviteten **[!UICONTROL Update data]** utför en massuppdatering av fälten i databasen.

   Mer information finns i [Uppdatera data](../../workflow/using/update-data.md).

### Prenumerations-/prenumerationshantering {#subscription-unsubscription-management}

Om du vill veta mer om hur du prenumererar och avbeställer från en informationstjänst via ett arbetsflöde kan du läsa [Prenumerationstjänster](../../workflow/using/subscription-services.md).

## Skicka via ett arbetsflöde {#sending-via-a-workflow}

### Leveransaktivitet {#delivery-activity}

Leveransaktiviteten beskrivs i [Leverans](../../workflow/using/delivery.md).

### Förbättra och målinrikta leveranser {#enriching-and-targeting-deliveries}

Leveranser kan bearbeta data från arbetsflöden för att anpassa innehåll eller inom ramen för valet av målpopulation.

Inom ramen för direktutskick kan du t.ex. inkludera ytterligare data som hämtats från dataändringar som utförts i arbetsflödet i extraheringsfilen:

![](assets/s_advuser_add_data_postal_mail.png)

Förutom de vanliga personaliseringsfälten kan du lägga till anpassningsfält från arbetsflödesfaser till leveransinnehållet. De ytterligare data som definieras i arbetsflödesaktiviteterna kan behållas och göras tillgängliga i leveransguiden, vilket visas i exemplet nedan, för att definiera namnet på utdatafilen inom ramen för direktmeddelandeleverans:

![](assets/s_advuser_using_additional_data.png)

Data i arbetsflödestabellen identifieras med sitt namn: den alltid består av länken **targetData** . Mer information finns i [Måldata](../../workflow/using/executing-a-workflow.md#target-data).

Inom ramen för e-postleverans kan personaliseringsfält även använda data från måltillägg som har utförts i arbetsflödesfaserna för målanpassning, vilket visas i exemplet nedan:

![](assets/s_advuser_add_data_email.png)

Om en segmentkod anges i en målaktivitet läggs den till i en specifik kolumn i arbetsflödestabellen och erbjuds tillsammans med anpassningsfälten. Om du vill visa alla anpassningsfält klickar du på den **[!UICONTROL Target extension > Other...]** länk som du kan nå via personaliseringsknappen.

![](assets/s_advuser_segment_code_select.png)

## Exportera data {#exporting-data}

### Zippa eller kryptera en fil {#zipping-or-encrypting-a-file}

Med Adobe Campaign kan du exportera komprimerade eller krypterade filer. När du definierar en export genom en **[!UICONTROL Data extraction (file)]** aktivitet kan du definiera en efterbearbetning för att komprimera eller kryptera filen.

Så här kan du göra:

* Om Adobe har Adobe som värd för din installation av Adobe Campaign: skicka en begäran till [supporten](https://support.neolane.net) om att få de nödvändiga verktygen installerade på servern.
* Om ni har Adobe Campaign lokalt: installera verktyget som du vill använda (till exempel: GPG, GZIP) och nödvändiga nycklar (krypteringsnyckel) på programservern.

Du kan sedan använda kommandon eller kod som:

```
function encryptFile(file) {  
  var systemCommand = “gpg --encrypt --recipient  recipientToEncryptTo ” + file;  
  var result = execCommand(systemCommand, true); 
}
```

När du importerar en fil kan du även packa upp eller dekryptera den. Se [Zippa upp eller dekryptera en fil före bearbetning](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing).
