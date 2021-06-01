---
product: campaign
title: Konfigurera åtkomst till resurser
description: Konfigurera åtkomst till resurser
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 1%

---

# Konfigurera åtkomst till resurser{#configuring-access-to-assets}

I det här avsnittet beskrivs de konfigurationssteg som krävs i Adobe Campaign för att använda integreringsfunktionerna med bastjänsten Assets eller Adobe Experience Manager resursbibliotek.

>[!CAUTION]
>
>Dessa integreringar är samtidiga. Läs nedanstående information noggrant innan du gör någon konfiguration.

* Integrering med **Experience Cloud Assets**: Med den här integreringen kan du infoga bilder från ditt Adobe Experience Cloud-bibliotek. Beroende på din konfigurations- och licensieringsmodell kan det här biblioteket vara kärntjänsten Resurser eller Assets on Demand. Integrationen måste konfigureras genom att det inbyggda **[!UICONTROL Integration with the Adobe Experience Cloud]**-paketet installeras i Adobe Campaign.
* Integrering med **AEM Assets**: Med den här integreringen kan du infoga bilder från ditt Adobe Experience Manager resursbibliotek. Integrationen måste konfigureras genom att det inbyggda **[!UICONTROL AEM Integration]**-paketet installeras i Adobe Campaign.

>[!NOTE]
>
>Om de två paketen (**[!UICONTROL AEM Integration]** och **[!UICONTROL Integration with the Adobe Experience Cloud]**) är installerade kan endast de resurser som är tillgängliga i Adobe Experience Cloud-biblioteket användas.

## Integrera med Experience Cloud Assets {#integrating-with-experience-cloud-assets}

För att kunna använda integrationen mellan Adobe Campaign och Experience Cloud Assets måste du ha:

* En Adobe Experience Cloud-organisation
* Verifieringsläget Adobe IMS är aktiverat

Om du vill aktivera anslutningen mellan Adobe Campaign och Adobe Experience Cloud konfigurerar du anslutningen via IMS (Adobe ID anslutningstjänst). Den här konfigurationen beskrivs i [Ansluta via ett Adobe ID](../../integrations/using/about-adobe-id.md)-dokument. Den innehåller följande uppgifter:

* Installerar **[!UICONTROL Integration with the Adobe Experience Cloud]**-paketet.
* Konfigurera ett externt Adobe Experience Cloud-konto.

>[!NOTE]
>
>De funktioner som är kopplade till den här integreringen är bara tillgängliga för användare som är anslutna till sin Adobe ID via IMS.

## Integrera med AEM Assets {#integrating-with-aem-assets}

Om du vill integrera AEM Assets med Adobe Campaign måste du först konfigurera integreringen mellan Adobe Experience Manager och Adobe Campaign. Den här konfigurationen kräver i huvudsak:

* Installera det inbyggda **[!UICONTROL AEM Integration]**-paketet
* Konfigurera ett externt konto som är specifikt för Adobe Experience Manager

Lär dig hur du integrerar Adobe Campaign och Adobe Experience Manager i [den detaljerade dokumentationen](../../integrations/using/about-adobe-experience-manager.md).

När integreringen är klar kan du konfigurera en ny leveransmall i Adobe Campaign så att den kan använda AEM Assets-biblioteket. Följ stegen nedan för att göra detta:

1. Skapa en ny leveransmall - eller duplicera en befintlig. Mer information om leveransmallar finns på [den här sidan](../../delivery/using/about-templates.md).
1. Redigera **egenskaperna** för den här mallen.
1. På fliken **[!UICONTROL Advanced]** anger du **[!UICONTROL Content editing mode]** till **DCE**.
1. Välj den externa **[!UICONTROL AEM account]** som du behöver använda för att komma åt ditt AEM Assets-bibliotek.

   ![](assets/dam_aem_assets1.png)

När du infogar bilder i en leverans baserat på den här mallen kan du med **[!UICONTROL Select a shared asset]**-alternativet bläddra bland bilderna i AEM Assets-biblioteket. Läs mer i [det här avsnittet](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Om **[!UICONTROL Integration with the Adobe Experience Cloud]**-paketet också är installerat på din Adobe Campaign-instans kan du bara använda resurserna som finns i Adobe Experience Cloud-biblioteket. Om du även vill få tillgång till resurserna i ditt AEM Assets-bibliotek måste du synkronisera AEM Assets och Adobe Experience Cloud. Resurserna i AEM Assets finns sedan också i Adobe Experience Cloud bibliotek. I det här fallet behöver du inte skapa någon särskild leveransmall. Mer information om synkronisering mellan AEM Assets och Adobe Experience Cloud finns i [den detaljerade dokumentationen](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/configure-assets-cc-integration.html#integration).
