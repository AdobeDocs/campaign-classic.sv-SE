---
product: campaign
title: Introduktion
description: Introduktion
feature: Monitoring, Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 5%

---

# Introduktion{#introduction}



I det här avsnittet beskrivs hur du uppgraderar Adobe Campaign, klientsidan och serversidan, och hur du går över till Unicode för en befintlig instans.

>[!NOTE]
>
>För instanser av värdbaserade/hanterade tjänster måste du koordinera med Adobe-administratören.\
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
