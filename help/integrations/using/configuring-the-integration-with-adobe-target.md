---
product: campaign
title: Konfigurera integreringen med Adobe Target
description: Konfigurera integreringen med Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: 94e609f3df94c553e2ec84ee427887a767b9af21
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Konfigurera integreringen med Adobe Target{#configuring-the-integration-with-adobe-target}

## Förhandskrav {#prerequisites}

För att kunna använda integrationen mellan Adobe Campaign och Adobe Target måste du ha:

* Adobe Experience Cloud- och Adobe Target-organisationer
* En Adobe Target-ruta har angetts för att upprätta anslutningen till Adobe Campaign

## Konfigurera Adobe Campaign {#configuring-adobe-campaign}

Så här konfigurerar du Adobe Campaign:

1. Installera **[!UICONTROL Integration with the Adobe Experience Cloud]**-standardpaketet. Att installera ett integrationspaket är detsamma som att installera ett standardpaket, vilket beskrivs i avsnittet [Paketimport](../../platform/using/working-with-data-packages.md#importing-packages). Detta ger dig åtkomst till de delade resurserna via Digital Asset Manager.
1. Aktivera anslutning via IMS (Adobe ID anslutningstjänst) för att använda bilder som delas via Adobe Experience Cloud i dina e-postmeddelanden. Läs avsnittet om [IMS](../../integrations/using/about-adobe-id.md).
1. I **[!UICONTROL Administration > Platform > Options]** konfigurerar du alternativ för server och organisation (klientorganisation) för Adobe Target:

   * **[!UICONTROL TNT_EdgeServer]** : Adobe Target-server som används för integreringen. Det här alternativet är redan markerat som standard. Detta värde motsvarar Adobe Target **[!UICONTROL Domain Server]**, följt av värdet **/m2**. Till exempel: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : Adobe Target organisationsnamn. Detta värde motsvarar namnet på Adobe Target **[!UICONTROL Client]**.

   ![](assets/tar_options.png)

>[!CAUTION]
>
>För hybridarkitekturer och värdbaserade arkitekturer måste dessa alternativ anges på alla servrar, inklusive [mittkällservern](../../installation/using/mid-sourcing-server.md) och [körningsinstansen](../../message-center/using/configuring-instances.md#execution-instance).