---
product: campaign
title: JSP-beteende
description: JSP-beteende
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---

# JSP-beteende{#jsp-behavior}

Om vissa **jsp**-jobb inte kan köras måste du tvinga dem att kompilera om.

Ange följande kommandon för detta:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

**jsp**-jobben återskapas nästa gång du ansluter.
