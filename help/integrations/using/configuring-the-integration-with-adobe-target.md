---
title: Konfigurera integreringen med Adobe Target
seo-title: Konfigurera integreringen med Adobe Target
description: Konfigurera integreringen med Adobe Target
seo-description: null
page-status-flag: never-activated
uuid: b9337e92-e4e5-4cba-a559-75db7460d5c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-target
discoiquuid: 378d5ff9-88c0-43f1-beb8-454701e9f1d1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Konfigurera integreringen med Adobe Target{#configuring-the-integration-with-adobe-target}

## Förutsättningar {#prerequisites}

För att kunna använda integrationen mellan Adobe Campaign och Adobe Target måste ni ha:

* Adobe Experience Cloud och Adobe Target-organisationer
* En Adobe Target-ruta har angetts för att upprätta anslutningen till Adobe Campaign

## Konfigurera Adobe Campaign {#configuring-adobe-campaign}

Så här konfigurerar du Adobe Campaign:

1. Installera **[!UICONTROL Integration with the Adobe Experience Cloud]** standardpaketet. Att installera ett integrationspaket är detsamma som att installera ett standardpaket, vilket beskrivs i avsnittet [Paketimport](../../platform/using/working-with-data-packages.md#importing-packages) . Detta ger dig åtkomst till de delade resurserna via Digital Asset Manager.
1. Aktivera anslutning via IMS (Adobe ID-anslutningstjänsten) för att använda bilder som delas via Adobe Experience Cloud i dina e-postmeddelanden. Läs avsnittet om [IMS](../../integrations/using/about-adobe-id.md).
1. I **[!UICONTROL Administration > Platform > Options]** konfigurerar du alternativen för server och organisation (klientorganisation) för Adobe Target:

   * **[!UICONTROL TNT_EdgeServer]** :Adobe Target-servern som används för integreringen. Det här alternativet är redan markerat som standard. Värdet motsvarar Adobe Target **[!UICONTROL Domain Server]** följt av värdet **/m2**. Till exempel: **tt.omtrdc.net/m2**.
   * **[!UICONTROL TNT_TenantName]** :Organisationsnamn för Adobe Target. Värdet motsvarar namnet på Adobe Target **[!UICONTROL Client]**.
   ![](assets/tar_options.png)

