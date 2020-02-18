---
title: Bilder saknas
seo-title: Bilder saknas
description: Bilder saknas
seo-description: null
page-status-flag: never-activated
uuid: 0dc73ea0-70bc-476d-bdff-2e62d6929f21
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: e001db7a-7c53-477e-a534-ce4d83d68559
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3801665574d0cdc9c0caf46fb2f0eede38f1b2cc

---


# Bilder saknas{#images-missing}

I version 17.9 har flera filer flyttats (särskilt ikoner).

För kunder som använder värdtjänster påverkas inte. Läs följande för anläggningsinstallationer:

**Apache-användare:**

Apache-användare påverkas inte om de använder angiven **apache_neolane.conf**

**IIS-användare:**

För IIS-användare (i Windows) visas flera ikoner som saknas i konsolen efter bygguppdateringen. Ytterligare IIS-uppdateringssteg krävs:

1. Efter bygguppdateringen dubbelklickar du på **iis_neolane_setup.vbs** i installationskatalogen för Campaign. Standardsökvägen är C:\Program Files (x86)\Adobe\Adobe Campaign v7\tomcat-7\conf
1. Starta om IIS-webbplatsen som uppdaterades i föregående steg.

