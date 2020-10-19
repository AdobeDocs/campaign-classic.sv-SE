---
title: 'Förutsättningar och rekommendationer '
description: Lär dig förutsättningarna innan du installerar Campaign (lokalt)
page-status-flag: never-activated
uuid: b3fb7485-1200-4699-af40-98c94f632ae1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 2c5e0004-2a5d-4e89-ae6c-6bad186bd958
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 10%

---


# Före start{#before-starting}

Innan du börjar driftsätta Campaign Classic som en lokal kund måste du uppfylla följande krav och rekommendationer.

* Se [Adobe Campaign Classic Compatibility-matrisen](../../rn/using/compatibility-matrix.md) som visar alla versioner av de system och komponenter som stöds för Adobe Campaign.

   >[!NOTE]
   >
   >Den här matrisen uppdateras regelbundet för den senaste versionen av Adobe Campaign. Därför rekommenderar vi att du kontrollerar kompatibiliteten systematiskt innan du implementerar eller migrerar dina system och komponenter.

* Beroende på din miljö kan du läsa igenom [förutsättningarna för Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) och [förutsättningarna för Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) -installationer.
* Läs rekommendationer om databasmotorer [i det här avsnittet](../../installation/using/database.md).
* Kontrollera att de nödvändiga lagren för databasåtkomst är installerade på servern och tillgängliga från Adobe Campaign-kontot. Mer information hittar du i [det här avsnittet](../../installation/using/application-server.md).
* Konfigurera dina nätverk som vissa processer i programmet behöver för att kommunicera med andra eller för att få åtkomst till nätverket och Internet. Detta innebär att vissa TCP-portar måste vara öppna för dessa processer. Läs [det här avsnittet](../../installation/using/network-configuration.md) om du vill veta mer om kraven för nätverkskonfiguration.
* Läs checklistan för kampanjsäkerhet och sekretess [i den här artikeln](https://helpx.adobe.com/se/campaign/kb/acc-security.html).
* Läs allmänna riktlinjer för hur du beräknar maskinvarukrav för lokal distribution [i den här artikeln](https://helpx.adobe.com/se/campaign/kb/hardware-sizing-guide.html).
