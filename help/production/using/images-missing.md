---
solution: Campaign Classic
product: campaign
title: Bilder saknas
description: Bilder saknas
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 5%

---


# Bilder saknas{#images-missing}

I version 17.9 har flera filer flyttats (särskilt ikoner).

För kunder som använder värdtjänster påverkas inte. Läs följande för anläggningsinstallationer:

**Apache-användare:**

Apache-användare påverkas inte om de använder angiven **apache_neolane.conf**

**IIS-användare:**

För IIS-användare (i Windows) visas flera ikoner som saknas i konsolen efter bygguppdateringen. Ytterligare IIS-uppdateringssteg krävs:

1. Efter bygguppdateringen dubbelklickar du på **iis_neolane_setup.vbs** i installationskatalogen för Campaign. Standardsökvägen är C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Starta om IIS-webbplatsen som uppdaterades i föregående steg.

