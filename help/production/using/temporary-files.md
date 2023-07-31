---
product: campaign
title: Tillfälliga filer
description: Tillfälliga filer
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 10%

---

# Tillfälliga filer{#temporary-files}



Felmeddelanden som följande kan visas (särskilt i leveransloggar) när systemet tas i produktion:

*Det går inte att byta namn på filen /tmp/tmp0000.tmp till /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link) (iRc=-52)*

Orsaken är följande:

Adobe Campaign genererar temporära filer under **/tmp** och byter sedan namn på dem för att flytta dem till **/usr/local/neolane/nl6/var**. Det här felet inträffar när båda mapparna (**/tmp** och **/usr/local/neolane/nl6/var**, som är en symbolisk länk till **/var/nl6**) motsvarar olika enheter. The **df** -kommandot används för verifiering.

För att åtgärda det här problemet måste de temporära filerna genereras på samma enhet som målet.

Kör till exempel följande:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

Lägg sedan till:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```
