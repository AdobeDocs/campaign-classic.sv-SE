---
product: campaign
title: Infoga Adobe Experience Platform-segment i Campaign
description: Lär dig hur du importerar Adobe Experience Platform-målgrupper till Campaign Classic
feature: Platform Integration
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: integrations
content-type: reference
exl-id: 6db8a653-b649-402c-8814-24826edadba7
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Infoga Adobe Experience Platform-segment i Campaign {#destinations}



Om ni vill få in Adobe Experience Platform-målgrupper i Campaign och använda dem i era arbetsflöden måste ni först koppla samman Adobe Campaign som Adobe Experience Platform **Mål** och konfigurera det med segmentet som ska exporteras.

När målet har konfigurerats exporteras data till lagringsplatsen och du måste skapa ett dedikerat arbetsflöde i Campaign Classic för att kunna importera det.

## Anslut Adobe Campaign som mål

Konfigurera en anslutning till Adobe Campaign på Adobe Experience-plattformen genom att välja en lagringsplats för de exporterade segmenten. I det här steget kan du även välja vilka segment som ska exporteras och ange ytterligare XDM-fält som ska inkluderas.

Mer information finns i [Destinationsdokumentation](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

När målet har konfigurerats skapar Adobe Experience Platform en tabbavgränsad tabbavgränsad txt- eller CSV-fil på den angivna lagringsplatsen. Den här åtgärden schemaläggs och utförs en gång per 24 timmar.

Nu kan du konfigurera ett arbetsflöde i Campaign Classic för att importera segmentet till Campaign.

## Skapa ett importarbetsflöde i Campaign Classic

När Campaign Classic har konfigurerats som mål måste du skapa ett dedikerat arbetsflöde för att importera filen som har exporterats av Adobe Experience Platform.

Om du vill göra det måste du lägga till och konfigurera en **[!UICONTROL File transfer]** aktivitet. Mer information om hur du konfigurerar den här aktiviteten finns i [det här avsnittet](../../workflow/using/file-transfer.md).

![](assets/rtcdp-file-transfer.png)

Du kan sedan skapa arbetsflödet utifrån dina behov (uppdatera databasen med segmentdata, skicka en flerkanalsleverans till segmentet osv.)

Som ett exempel hämtar arbetsflödet nedan filen från din lagringsplats dagligen och uppdaterar sedan Campaign-databasen med segmentdata.

![](assets/rtcdp-workflow.png)
