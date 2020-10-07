---
title: JSP-beteende
seo-title: JSP-beteende
description: JSP-beteende
seo-description: null
page-status-flag: never-activated
uuid: b9e9f348-968c-46e0-8340-df1f1fcaf3a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 5dcc4090-effe-479e-8d5c-67e6a6542fbb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '38'
ht-degree: 21%

---


# JSP-beteende{#jsp-behavior}

Om vissa **jsp** -jobb inte kan köras måste du tvinga dem att kompilera om.

Ange följande kommandon för detta:

```
nlserver stop web
cd nl6/tomcat-7
rm -r work/
nlserver start web
```

JSP- **jobben** återskapas nästa gång du ansluter.
