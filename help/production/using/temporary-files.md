---
title: Tillfälliga filer
seo-title: Tillfälliga filer
description: Tillfälliga filer
seo-description: null
page-status-flag: never-activated
uuid: ae7ec619-e93f-41fb-ba7c-fcbcf4cba84f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f18237b0-ef54-46a6-9c14-34b038f9de18
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# Tillfälliga filer{#temporary-files}

Om felmeddelanden som följande visas (särskilt i leveransloggar) när systemet aktiveras:

**Det går inte att byta namn på filen /tmp/tmp0000.tmp till /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link) (iRc=-52)**

Orsaken är följande:

Adobe Campaign genererar tillfälliga filer under **/tmp** och byter sedan namn på dem för att flytta dem till **/usr/local/neolane/nl6/var**. Det här felet inträffar när både mappar (**/tmp** och **/usr/local/neolane/nl6/var**, som i själva verket är en symbolisk länk till **/var/nl6**) motsvarar olika enheter. Kommandot **df** används för verifiering.

För att åtgärda det här problemet måste de temporära filerna genereras på samma enhet som målet. Genom att köra:

```
$ cd ~/nl6/var
$ mkdir tmp
$ vi ~/nl6/customer.sh
```

och sedan lägga till:

```
export TMPDIR=/usr/local/neolane/nl6/var/tmp 
```

