---
solution: Campaign Classic
product: campaign
title: Introduktion
description: Introduktion
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 5b35d2ffdd0f591e2fe31dc98a54be9ea0c0c18d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 1%

---


# Introduktion{#introduction}

I det här avsnittet beskrivs hur du uppgraderar Adobe Campaign, klientsidan och serversidan, och hur du går över till Unicode för en befintlig instans.

>[!NOTE]
>
>För värdbaserade instanser måste du koordinera med din Adobe-administratör.\
>För lokala instanser kan du få hjälp av Adobe Consultants.

Uppgraderingen måste utföras på alla servrar där Adobe Campaign är installerat.

1. Migrera omdirigerings- och spårningsservrar (Apache/IIS).
1. Migrera Power Booster-/klusterservrarna.
1. Migrera marknadsföringsservern.

Adobe Campaign bygger på flera processer som körs på serversidan och som du måste hantera under uppdateringar, särskilt:

* Programserver (nlserver web)
* Leveransserver (nlserver mta)
* Omdirigeringsserver (webmdl)

>[!CAUTION]
>
>Klientkonsolen ska finnas på samma version som serverinstansen.

>[!NOTE]
>
>Mer information om de olika Adobe Campaign-processerna finns i [det här avsnittet](../../installation/using/general-architecture.md#logical-application-layer).\
>När du använder arkitekturen av typen Power Booster eller Power Cluster måste du tillämpa den här processen på alla Power Booster-/Cluster-servrar.

Om den nya versionen innebär en ändring av databasstrukturen rekommenderar vi att du startar om servrarna i följande ordning:

1. Programserver (nlserver web),
1. Omdirigeringsserver (webmdl),
1. Leveransserver (nlserver mta).

