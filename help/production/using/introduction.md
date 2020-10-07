---
title: Introduktion
seo-title: Introduktion
description: Introduktion
seo-description: null
page-status-flag: never-activated
uuid: 4192a74e-1d4f-4784-80e3-53aaefa9141e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 772992bf-588f-42bd-a72a-986a88815264
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 2%

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

>[!NOTE]
>
>Mer information om de olika Adobe Campaign-processerna finns i [det här avsnittet](../../installation/using/general-architecture.md#logical-application-layer).\
>När du använder arkitekturen av typen Power Booster eller Power Cluster måste du tillämpa den här processen på alla Power Booster-/Cluster-servrar.

Om den nya versionen innebär en ändring av databasstrukturen rekommenderar vi att du startar om servrarna i följande ordning:

1. Programserver (nlserver web),
1. Omdirigeringsserver (webmdl),
1. Leveransserver (nlserver mta).

