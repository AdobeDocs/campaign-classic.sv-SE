---
product: campaign
title: Kom igång med källor och destinationer
description: Läs mer om Adobe Experience Platform Sources and Destinations.
audience: integrations
content-type: reference
exl-id: 8cee52c7-ea56-4701-8ebb-eb18afffea51
source-git-commit: 89a18ae9ec57376d6ebec6c416c7562f960eb882
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 15%

---

# Arbeta med källor och destinationer {#rtcdp}

![](../../assets/v7-only.svg)

## Om Källor och mål

Med Adobe Experience Platform kan du dela data mellan Campaign Classic och Adobe Real-time Customer Data Platform (RTCDP). På så sätt kan ni inrikta er på Adobe Experience Platform målgrupper i era Campaign-arbetsflöden och sedan skicka tillbaka data till Adobe Real-time Customer Data Platform som hör till dessa målgrupper, som utskick, öppningar och klick.

* Med **Destinationer**, och importerade målgrupper från Adobe Experience Platform till Campaign Classic. På så sätt kan ni aktivera kända och okända data för era marknadsföringskampanjer.
* Med **Källor**, exportera data från Campaign Classic (t.ex. skickar, öppnar, klickar) till Adobe Experience Platform. På så sätt kan ni centralisera data som ni samlar in från olika källor till en enda plats och använda de insikter ni får av den för att göra mer.

>[!IMPORTANT]
>
>Tänk på lagringsgränserna för SFTP, lagringsgränserna för databaser och de aktiva profilgränserna enligt ditt Adobe Campaign-avtal när du utför den här integreringen.

En mer detaljerad översikt över Adobe Real-time Customer Data Platform, Destinationer och Källor finns på följande sidor:

* [Adobe Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html?lang=sv)
* [Dokumentation om mål](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.htmll?lang=sv)
* [Dokumentation om källor](https://experienceleague.adobe.com/docs/experience-platform/sources/home.htmll?lang=sv)

## Anslut Campaign Classic med Adobe Experience Platform

För att kunna dela data mellan Adobe Experience Platform och Campaign Classic måste du först ansluta Adobe Campaign som en **Mål** och ansluta din AWS S3- eller Azure-blobblagringsplats som en **Källa** i Adobe Experience Platform.

När du har konfigurerat anslutningarna kan du konfigurera en dataimport eller exportera till Campaign Classic med hjälp av arbetsflöden.

![](assets/rtcdp-schema.png)

Mer information om hur du konfigurerar dessa import- och exportprocesser finns i följande avsnitt:

* [Infoga Adobe Experience Platform-segment i Campaign](../../integrations/using/ingest-aep-data.md)
* [Exportera data från Campaign till Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
