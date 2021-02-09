---
solution: Campaign Classic
product: campaign
title: Tillfälliga filer
description: Tillfälliga filer
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 4%

---


# Tillfälliga filer{#temporary-files}

Felmeddelanden som följande kan visas (särskilt i leveransloggar) när systemet tas i produktion:

*Det går inte att byta namn på filen /tmp/tmp0000.tmp till /usr/local/neolane/nl6/bin/..//var/XXX/mta/86510470.xml ;(errno=18, Invalid cross-device link) (iRc=-52)*

Orsaken är följande:

Adobe Campaign genererar temporära filer under **/tmp** och byter namn på dem sedan så att de flyttas till **/usr/local/neolane/nl6/var**. Det här felet inträffar när båda mapparna (**/tmp** och **/usr/local/neolane/nl6/var**, som i själva verket är en symbolisk länk till **/var/nl6**) motsvarar olika enheter. Kommandot **df** används för verifiering.

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
