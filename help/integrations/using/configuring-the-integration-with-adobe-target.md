---
product: campaign
title: Konfigurera integreringen med Adobe Target
description: Konfigurera integreringen med Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: af40fe822c69979a478604595790d4deefd6d5b0
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 2%

---

# Konfigurera integreringen med Adobe Target{#configuring-the-integration-with-adobe-target}

![](../../assets/v7-only.svg)


>[!CAUTION]
>
> Som värdkund eller hybridkund kan du kontakta din Adobe-representant för att konfigurera integreringen. Stegen nedan gäller endast lokala kunder.

Den här integreringen kräver:

* Adobe Experience Cloud- och Adobe Target-organisationer
* En Adobe Target-ruta har angetts för att upprätta anslutningen till Adobe Campaign

Så här konfigurerar du integreringen i Adobe Campaign:

1. Installera **[!UICONTROL Integration with the Adobe Experience Cloud]** inbyggt paket. [Läs mer](../../platform/using/working-with-data-packages.md#importing-packages)

   Det här paketet ger dig tillgång till de delade resurserna via Digital Asset Manager.

1. Aktivera anslutning via IMS (Adobe ID anslutningstjänst) för att använda bilder som delas via Adobe Experience Cloud i dina e-postmeddelanden. [Läs mer](../../integrations/using/about-adobe-id.md)
1. Bläddra till **[!UICONTROL Administration > Platform > Options]** för att konfigurera alternativ för server och organisation (klientorganisation) för Adobe Target:

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** : Adobe Target-server som används för integreringen. Det här alternativet är redan markerat som standard. Detta värde motsvarar Adobe Target **[!UICONTROL Domain Server]**, följt av värdet **/m2**. Till exempel: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** : Adobe Target organisationsnamn. Detta värde motsvarar namnet på Adobe Target **[!UICONTROL Client]**.


>[!CAUTION]
>
>För hybridarkitekturer och hostingarkitekturer måste dessa alternativ anges på alla servrar, inklusive [server med mellanleverantörer](../../installation/using/mid-sourcing-server.md) och [körningsinstans](../../message-center/using/configuring-instances.md#execution-instance).