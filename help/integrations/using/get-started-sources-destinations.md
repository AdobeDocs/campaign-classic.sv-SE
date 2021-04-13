---
solution: Campaign Classic
product: campaign
title: Kom igång med källor och mål
description: Läs mer om Adobe Experience Platform Sources and Destinations.
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: b4da54c122e75a175f6f586a05955b3dfed00c1e
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---


# Kom igång med källor och mål {#rtcdp}

## Om Källor och mål

Med Adobe Experience Platform kan ni dela data mellan Campaign Classic och Adobe kunddataplattform i realtid (RTCDP). På så sätt kan ni inrikta er på Adobe Experience Platform målgrupper i era Campaign-arbetsflöden och sedan skicka tillbaka data från kunddataplattformen i Adobe i realtid som relaterar till dessa målgrupper, som att skicka, öppna och klicka.

* Med **Destinationer** kan ni importera målgrupper från Adobe Experience Platform till Campaign Classic. På så sätt kan ni aktivera kända och okända data för era marknadsföringskampanjer.
* Med **Källor** exporterar du data från Campaign Classic (t.ex. skickar, öppnar, klickar) till Adobe Experience Platform. På så sätt kan ni centralisera data som ni samlar in från olika källor till en enda plats och använda de insikter ni får av den för att göra mer.

>[!IMPORTANT]
>
>Tänk på lagringsgränserna för SFTP, lagringsgränserna för databaser och de aktiva profilgränserna enligt ditt Adobe Campaign-avtal när du utför den här integreringen.

En mer detaljerad översikt över Adobe kunddataplattform, destinationer och källor i realtid finns på följande sidor:

* [Adobe kunddataplattform i realtid](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html)
* [Destinationsdokumentation](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html)
* [Källdokumentation](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html)

## Anslut Campaign Classic med Adobe Experience Platform

För att kunna dela data mellan Adobe Experience Platform och Campaign Classic måste du först ansluta Adobe Campaign som **mål** och ansluta din AWS S3- eller Azure-blobblagringsplats som **källa** i Adobe Experience Platform.

När du har konfigurerat anslutningarna kan du konfigurera en dataimport eller exportera till Campaign Classic med hjälp av arbetsflöden.

![](assets/rtcdp-schema.png)

Mer information om hur du konfigurerar dessa import- och exportprocesser finns i följande avsnitt:

* [Infoga Adobe Experience Platform-segment i Campaign](../../integrations/using/ingest-aep-data.md)
* [Exportera data från Campaign till Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
