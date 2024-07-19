---
product: campaign
title: Bilder saknas
description: Bilder saknas
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 5%

---

# Bilder saknas{#images-missing}



I version 17.9 har flera filer flyttats (särskilt ikoner).

För kunder som använder värdtjänster påverkas inte. Läs följande om du har installationer på plats:

**Apache-användare:**

Apache-användare påverkas inte om de använder angiven **apache_neolane.conf**.

**IIS-användare:**

För IIS-användare (i Windows) visas flera ikoner som saknas i konsolen efter bygguppdateringen. Ytterligare IIS-uppdateringssteg krävs:

1. Efter bygguppdateringen dubbelklickar du på **iis_neolane_setup.vbs** i installationskatalogen för Campaign. Standardsökvägen är C:\Program filer (x86)\Adobe\Adobe Campaign v7\conf
1. Starta om IIS-webbplatsen som uppdaterades i föregående steg.
