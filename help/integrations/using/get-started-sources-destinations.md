---
product: campaign
title: Kom igång med källor och destinationer
description: Läs mer om Adobe Experience Platform Sources and Destinations
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 8cee52c7-ea56-4701-8ebb-eb18afffea51
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 10%

---

# Arbeta med källor och destinationer {#rtcdp}



## Om Källor och mål

Med Adobe Experience Platform kan du dela data mellan Campaign Classic och Adobe Real-time Customer Data Platform (RTCDP). På så sätt kan ni inrikta er på Adobe Experience Platform målgrupper i era Campaign-arbetsflöden och sedan skicka tillbaka data till Adobe Real-time Customer Data Platform som hör till dessa målgrupper, som utskick, öppningar och klick.

* Med **Destinationer** kan målgrupper från Adobe Experience Platform importeras till Campaign Classicen. På så sätt kan ni aktivera kända och okända data för era marknadsföringskampanjer.
* Med **Källor** exporterar du Campaign Classic-data (t.ex. skickar, öppnar, klickar) till Adobe Experience Platform. På så sätt kan ni centralisera data som ni samlar in från olika källor till en enda plats och använda de insikter ni får av den för att göra mer.

>[!IMPORTANT]
>
>Tänk på lagringsgränserna för SFTP, lagringsgränserna för databaser och de aktiva profilgränserna enligt ditt Adobe Campaign-avtal när du utför den här integreringen.

En mer detaljerad översikt över Adobe Real-time Customer Data Platform, Destinationer och Källor finns på följande sidor:

* [Adobe Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html?lang=sv)
* [Dokumentation om mål](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.htmll?lang=sv)
* [Dokumentation om källor](https://experienceleague.adobe.com/docs/experience-platform/sources/home.htmll?lang=sv)

## Koppla samman Campaign Classic med Adobe Experience Platform

För att kunna dela data mellan Adobe Experience Platform och Campaign Classic måste du först ansluta Adobe Campaign som **mål** och ansluta din AWS S3- eller Azure-blobblagringsplats som **Source** i Adobe Experience Platform.

När kopplingarna har konfigurerats kan du konfigurera en dataimport eller exportera till Campaign Classic med hjälp av arbetsflöden.

![](assets/rtcdp-schema.png)

Mer information om hur du konfigurerar dessa import- och exportprocesser finns i följande avsnitt:

* [Infoga Adobe Experience Platform-segment i Campaign](../../integrations/using/ingest-aep-data.md)
* [Exportera data från Campaign till Adobe Experience Platform](../../integrations/using/export-campaign-data.md)
