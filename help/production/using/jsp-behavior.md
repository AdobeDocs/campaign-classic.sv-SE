---
product: campaign
title: JSP-beteende
description: JSP-beteende
feature: Monitoring
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 757e3a5395f24e0bdd04737aba0458881e4ea780
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 14%

---

# JSP-beteende{#jsp-behavior}



Om vissa **jsp** jobb inte kan köras, du måste tvinga dem att kompilera om.

Ange följande kommandon för detta:

```
nlserver stop web
cd nl6/tomcat-X
rm -r work/
nlserver start web
```

The **jsp** jobb genereras om nästa gång du ansluter.
