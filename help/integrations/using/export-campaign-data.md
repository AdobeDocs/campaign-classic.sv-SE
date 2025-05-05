---
product: campaign
title: Exportera data från Campaign till Adobe Experience Platform
description: Lär dig hur du exporterar data från Campaign Classic till Adobe Experience Platform
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 8d1404c5-030b-47fe-a4c3-e72f15f09bbb
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 3%

---

# Exportera data från Campaign till Adobe Experience Platform {#sources}



Om du vill exportera data till Adobe Real-time Customer Data Platform (RTCDP) måste du först skapa ett arbetsflöde i Campaign Classic för att kunna exportera de data du vill dela till din S3- eller Azure-blob-lagringsplats.

När arbetsflödet har konfigurerats och data har skickats till din lagringsplats måste du ansluta din S3- eller Azure-blobblagringsplats som en **Source** i Adobe Experience Platform.

>[!NOTE]
>
>Observera att vi rekommenderar att du bara exporterar kampanjgenererade data (t.ex. för att skicka, öppna, klicka osv.) till Adobe Experience Platform. Data som hämtas från en tredje parts källa (som din CRM) ska importeras direkt till Adobe Experience Platform.

## Skapa ett exportarbetsflöde i Campaign Classic

Om du vill exportera data från Campaign Classic till din S3- eller Azure Blob-lagringsplats måste du skapa ett arbetsflöde för de data du vill exportera och skicka dem till lagringsplatsen.

Lägg till och konfigurera:

* En **[!UICONTROL Data extraction (file)]**-aktivitet som extraherar måldata till en CSV-fil. Mer information om hur du konfigurerar den här aktiviteten finns i [det här avsnittet](../../workflow/using/extraction-file.md).

  ![](assets/rtcdp-extract-file.png)

* En **[!UICONTROL File transfer]**-aktivitet som överför CSV-filen till din lagringsplats. Mer information om hur du konfigurerar den här aktiviteten finns i [det här avsnittet](../../workflow/using/file-transfer.md).

  ![](assets/rtcdp-file-transfer.png)

Arbetsflödet nedan extraherar till exempel regelbundet loggar in i en CSV-fil och överför sedan filen till en lagringsplats.

![](assets/aep-export.png)

## Anslut lagringsplatsen som en Source

De viktigaste stegen för att ansluta din S3- eller Azure-blobblagringsplats som **Source** i Adobe Experience Platform anges nedan. Detaljerad information om de här stegen finns i [Source Connectors-dokumentationen](https://experienceleague.adobe.com/docs/experience-platform/sources/home.htmll?lang=sv).

1. Skapa en anslutning till din lagringsplats på Adobe Experience-plattformen **[!UICONTROL Sources]**:

   * [Skapa en Amazon S3-källanslutning](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/s3.html?lang=sv-SE)
   * [Azure Blob-koppling](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/cloud-storage/blob.html?lang=sv-SE)

   >[!NOTE]
   >
   >Lagringsplatsen kan vara Amazon S3, SFTP med lösenord, SFTP med SSH-nyckel eller Azure Blob-anslutningar. Den metod som rekommenderas för att skicka data till Adobe Campaign är via Amazon S3 eller Azure Blob:

   ![](assets/rtcdp-connector.png)

1. Konfigurera ett dataflöde för en batchanslutning till molnlagring. Ett dataflöde är en schemalagd aktivitet som hämtar och importerar data från lagringsplatsen till en Adobe Experience Platform-datauppsättning. Med det här steget kan du konfigurera datainmatningen från lagringsplatsen, inklusive dataval och mappning av CSV-fälten till ett XDM-schema.

   Detaljerad information finns på [den här sidan](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html?lang=sv-SE).

   ![](assets/rtcdp-map-xdm.png)

1. När Source har konfigurerats kommer Adobe Experience Platform att importera filen från lagringsplatsen som du angav.

   Den här åtgärden kan schemaläggas efter dina behov. Vi rekommenderar att du exporterar upp till 6 gånger per dag, beroende på vilken belastning som redan finns på instansen.
