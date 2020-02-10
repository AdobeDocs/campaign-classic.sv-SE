---
title: Konfigurera åtkomst till resurser
seo-title: Konfigurera åtkomst till resurser
description: Konfigurera åtkomst till resurser
seo-description: null
page-status-flag: never-activated
uuid: dc8c0016-92c8-41ab-98c6-d0fe0bfd6c41
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: asset-sharing
discoiquuid: df1b6ead-3471-404a-b43f-a68fb86cb14c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Konfigurera åtkomst till resurser{#configuring-access-to-assets}

I det här avsnittet beskrivs de konfigurationssteg som krävs i Adobe Campaign för att använda integreringsfunktionerna med bastjänsten Assets eller Adobe Experience Manager-biblioteket.

>[!CAUTION]
>
>Dessa integreringar är samtidiga. Läs nedanstående information noggrant innan du gör någon konfiguration.

* Integrering med **Experience Cloud Assets**: Med den här integreringen kan du infoga bilder från ditt Adobe Experience Cloud-bibliotek. Beroende på din konfigurations- och licensieringsmodell kan det här biblioteket vara kärntjänsten Resurser eller Assets on Demand. Integrationen måste konfigureras genom att det **[!UICONTROL Integration with the Adobe Experience Cloud]** inbyggda paketet installeras i Adobe Campaign.
* Integrering med **AEM Assets**: Med den här integreringen kan du infoga bilder från ditt resursbibliotek i Adobe Experience Manager. Integrationen måste konfigureras genom att det **[!UICONTROL AEM Integration]** inbyggda paketet installeras i Adobe Campaign.

>[!NOTE]
>
>Om de två paketen (**[!UICONTROL AEM Integration]** och **[!UICONTROL Integration with the Adobe Experience Cloud]** ) är installerade kan bara de resurser som finns i Adobe Experience Cloud-biblioteket användas. Om du även vill få tillgång till resurserna i ditt AEM Assets-bibliotek måste du synkronisera AEM Assets och Adobe Experience Cloud. Resurserna i AEM Assets är sedan också tillgängliga i Adobe Experience Cloud-biblioteket. Mer information om synkronisering av AEM Assets och Adobe Experience Cloud finns i den [detaljerade dokumentationen](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html).

## Integrera med Experience Cloud Assets {#integrating-with-experience-cloud-assets}

För att kunna använda integreringen mellan Adobe Campaign och Experience Cloud Assets måste ni ha:

* En Adobe Experience Cloud-organisation
* Verifieringsläget för Adobe IMS är aktiverat

Om du vill aktivera anslutningen mellan Adobe Campaign och Adobe Experience Cloud konfigurerar du anslutningen via IMS (Adobe ID-anslutningstjänsten). Den här konfigurationen beskrivs i [Ansluta via ett Adobe ID](../../integrations/using/about-adobe-id.md) -dokument. Den innehåller följande uppgifter:

* Installerar **[!UICONTROL Integration with the Adobe Experience Cloud]** paketet.
* Konfigurera ett externt Adobe Experience Cloud-konto.

>[!NOTE]
>
>De funktioner som är kopplade till den här integreringen är bara tillgängliga för användare som är anslutna med sitt Adobe ID via IMS.

## Integrera med AEM Assets {#integrating-with-aem-assets}

Om du vill integrera AEM Assets med Adobe Campaign måste du först konfigurera integreringen mellan Adobe Experience Manager och Adobe Campaign. Den här konfigurationen kräver i huvudsak:

* Installera det **[!UICONTROL AEM Integration]** inbyggda paketet
* Konfigurera ett externt konto som är specifikt för Adobe Experience Manager

Lär dig hur du integrerar Adobe Campaign och Adobe Experience Manager i den [detaljerade dokumentationen](../../integrations/using/about-adobe-experience-manager.md).

När integreringen är klar kan du konfigurera en ny leveransmall i Adobe Campaign så att du kan använda AEM Assets-biblioteket. Gör så här:

1. Skapa en ny leveransmall - eller duplicera en befintlig. Mer information om leveransmallar finns på [den här sidan](../../delivery/using/about-templates.md).
1. Redigera mallens **egenskaper** .
1. På **[!UICONTROL Advanced]** fliken ställer du in **[!UICONTROL Content editing mode]** till **DCE**.
1. Välj den externa **[!UICONTROL AEM account]** som du behöver för att komma åt ditt AEM Resurser-bibliotek.

   ![](assets/dam_aem_assets1.png)

När du infogar bilder i ett leveransinnehåll som är baserat på den här mallen kan du sedan bläddra bland bilderna i AEM Resurser-biblioteket med det här **[!UICONTROL Select a shared asset]** alternativet. Läs mer i [det här avsnittet](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Om paketet också är installerat på din Adobe Campaign-instans kan du bara använda resurserna som finns i Adobe Experience Cloud-biblioteket. **[!UICONTROL Integration with the Adobe Experience Cloud]** Om du även vill få tillgång till resurserna i ditt AEM Assets-bibliotek måste du synkronisera AEM Assets och Adobe Experience Cloud. Resurserna i AEM Assets är sedan också tillgängliga i Adobe Experience Cloud-biblioteket. I det här fallet behöver du inte skapa någon särskild leveransmall. Mer information om synkronisering mellan AEM Assets och Adobe Experience Cloud finns i den [detaljerade dokumentationen](https://docs.adobe.com/docs/en/aod/overview/collaborating/aem-assets-aod-sync.html).

