---
solution: Campaign Classic
product: campaign
title: JSP-beteende
description: JSP-beteende
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
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
