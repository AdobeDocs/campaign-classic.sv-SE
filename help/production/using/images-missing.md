---
product: campaign
title: Bilder saknas
description: Bilder saknas
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%

---

# Bilder saknas{#images-missing}

![](../../assets/v7-only.svg)

I version 17.9 har flera filer flyttats (särskilt ikoner).

För kunder som använder värdtjänster påverkas inte. Läs följande för anläggningsinstallationer:

**Apache-användare:**

Apache-användare påverkas inte om de använder den medföljande **apache_neolane.conf**.

**IIS-användare:**

För IIS-användare (i Windows) visas flera ikoner som saknas i konsolen efter bygguppdateringen. Ytterligare IIS-uppdateringssteg krävs:

1. Efter bygguppdateringen dubbelklickar du **iis_neolane_setup.vbs** finns i installationskatalogen för Campaign. Standardsökvägen är C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Starta om IIS-webbplatsen som uppdaterades i föregående steg.
