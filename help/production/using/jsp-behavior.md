---
product: campaign
title: JSP-beteende
description: JSP-beteende
feature: Monitoring
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '46'
ht-degree: 15%

---

# JSP-beteende{#jsp-behavior}



Om vissa **jsp** jobb inte kan köras, du måste tvinga dem att kompilera om.

Ange följande kommandon för detta:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

The **jsp** jobb genereras om nästa gång du ansluter.
