---
product: campaign
title: Infoga Adobe Experience Platform-segment i Campaign
description: Lär er hur ni kan få ut Adobe Experience Platform-målgrupper till Campaign Classic
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 6db8a653-b649-402c-8814-24826edadba7
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Infoga Adobe Experience Platform-segment i Campaign {#destinations}



Om du vill importera Adobe Experience Platform-målgrupper till Campaign och använda dem i dina arbetsflöden måste du först ansluta Adobe Campaign som Adobe Experience Platform **mål** och konfigurera det med segmentet som ska exporteras.

När målet har konfigurerats exporteras data till din lagringsplats och du måste skapa ett dedikerat arbetsflöde i Campaign Classic för att kunna importera det.

## Anslut Adobe Campaign som mål

Konfigurera en anslutning till Adobe Campaign på Adobe Experience-plattformen genom att välja en lagringsplats för de exporterade segmenten. I det här steget kan du även välja vilka segment som ska exporteras och ange ytterligare XDM-fält som ska inkluderas.

Mer information finns i [Måldokumentationen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=sv-SE).

När målet har konfigurerats skapar Adobe Experience Platform en tabbavgränsad tabbavgränsad txt- eller CSV-fil på den angivna lagringsplatsen. Den här åtgärden schemaläggs och utförs en gång per 24 timmar.

Du kan nu konfigurera ett arbetsflöde för Campaign Classic så att du kan importera segmentet till Campaign.

## Skapa ett importarbetsflöde i Campaign Classic

När Campaign Classicen har konfigurerats som mål måste du skapa ett dedikerat arbetsflöde för att importera filen som har exporterats av Adobe Experience Platform.

För att göra detta måste du lägga till och konfigurera en **[!UICONTROL File transfer]**-aktivitet. Mer information om hur du konfigurerar den här aktiviteten finns i [det här avsnittet](../../workflow/using/file-transfer.md).

![](assets/rtcdp-file-transfer.png)

Du kan sedan skapa arbetsflödet utifrån dina behov (uppdatera databasen med segmentdata, skicka en flerkanalsleverans till segmentet osv.)

Som ett exempel hämtar arbetsflödet nedan filen från din lagringsplats dagligen och uppdaterar sedan Campaign-databasen med segmentdata.

![](assets/rtcdp-workflow.png)
