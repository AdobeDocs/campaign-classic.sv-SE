---
product: campaign
title: Tillfälliga filer
description: Tillfälliga filer
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: e77800f5-c0ae-446d-8ff3-bc8a18c97dbd
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---

# Tillfälliga filer{#temporary-files}



Felmeddelanden som följande kan visas (särskilt i leveransloggar) när systemet tas i produktion:

*Det går inte att byta namn på filen /tmp/tmp0000.tmp till /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link) (iRc=-52)*

Orsaken är följande:

Adobe Campaign genererar tillfälliga filer under **/tmp** och byter sedan namn på dem för att flytta dem till **/usr/local/neolane/nl6/var**. Det här felet inträffar när båda mapparna (**/tmp** och **/usr/local/neolane/nl6/var**, som i själva verket är en symbolisk länk till **/var/nl6**) motsvarar olika enheter. The **df** -kommandot används för verifiering.

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
