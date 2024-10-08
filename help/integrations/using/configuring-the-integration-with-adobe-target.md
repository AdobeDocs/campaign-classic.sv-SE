---
product: campaign
title: Konfigurera integreringen med Adobe Target
description: Lär dig konfigurera integrationen med Adobe Target
feature: Target Integration
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 2%

---

# Konfigurera integreringen med Adobe Target{#configuring-the-integration-with-adobe-target}




>[!CAUTION]
>
> Som värdkund eller hybridkund kan du kontakta din Adobe-representant för att konfigurera integreringen. Stegen nedan gäller endast lokala kunder.

Den här integreringen kräver:

* Adobe Experience Cloud och Adobe Target
* En Adobe Target-ruta har angetts för att upprätta anslutningen till Adobe Campaign

Så här konfigurerar du integreringen i Adobe Campaign:

1. Installera det **[!UICONTROL Integration with the Adobe Experience Cloud]** inbyggda paketet. [Läs mer](../../platform/using/working-with-data-packages.md#importing-packages)

   Det här paketet ger dig tillgång till de delade resurserna via Digital Asset Manager.

1. Aktivera anslutning via IMS (Adobe ID anslutningstjänst) för att använda bilder som delas via Adobe Experience Cloud i dina e-postmeddelanden. [Läs mer](../../integrations/using/about-adobe-id.md)
1. Bläddra till **[!UICONTROL Administration > Platform > Options]** för att konfigurera alternativ för server och organisation (klientorganisation) för Adobe Target:

   ![](assets/tar_options.png)

   * **[!UICONTROL TNT_EdgeServer]** : Adobe Target-server som används för integreringen. Det här alternativet är redan markerat som standard. Detta värde motsvarar Adobe Target **[!UICONTROL Domain Server]**, följt av värdet **/m2**. Till exempel: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]**: Adobe Target organisationsnamn. Det här värdet motsvarar namnet på Adobe Target **[!UICONTROL Client]**.


>[!CAUTION]
>
>För hybridarkitekturer och värdbaserade arkitekturer måste dessa alternativ anges på alla servrar, inklusive [mittkällservern](../../installation/using/mid-sourcing-server.md) och [körningsinstansen](../../message-center/using/configuring-instances.md#execution-instance).