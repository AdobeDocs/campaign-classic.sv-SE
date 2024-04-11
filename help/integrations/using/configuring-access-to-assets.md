---
product: campaign
title: Konfigurera åtkomst till resurser
description: Konfigurera åtkomst till resurser
feature: Asset Sharing
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Konfigurera åtkomst till resurser{#configuring-access-to-assets}



I det här avsnittet beskrivs de nödvändiga konfigurationsstegen i Adobe Campaign för att använda integreringsfunktionerna med bastjänsten Assets eller i Adobe Experience Manager Assets (AEM Assets) bibliotek.

>[!CAUTION]
>
>Dessa integreringar är samtidiga. Läs nedanstående information noggrant innan du gör någon konfiguration.

* Integrering med **Experience Cloud Assets**: den här integreringen gör att du kan infoga bilder från ditt Adobe Experience Cloud-bibliotek. Den här integreringen måste konfigureras genom att installera **[!UICONTROL Integration with the Adobe Experience Cloud]** inbyggd i Adobe Campaign.
* Integrering med **AEM Assets**: den här integreringen gör att du kan infoga bilder från ditt Adobe Experience Manager Assets-bibliotek. Den här integreringen måste konfigureras genom att installera **[!UICONTROL AEM Integration]** inbyggd i Adobe Campaign. Observera att denna integrering inte längre är tillgänglig från och med Adobe Experience Manager 6.4.

>[!NOTE]
>
>Om de två paketen (**[!UICONTROL AEM Integration]** och **[!UICONTROL Integration with the Adobe Experience Cloud]** ) är installerat kan endast de resurser som finns i Adobe Experience Cloud-biblioteket användas.

## Integrera med Experience Cloud Assets {#integrating-with-experience-cloud-assets}

För att kunna använda integreringen mellan Adobe Campaign och Experience Cloud Assets måste du ha:

* Adobe Experience Cloud
* Adobe IMS-autentiseringsläget är aktiverat

Om du vill aktivera anslutningen mellan Adobe Campaign och Adobe Experience Cloud konfigurerar du anslutningen via IMS (Adobe ID anslutningstjänst). Den här konfigurationen beskrivs i [Ansluta via en Adobe ID](../../integrations/using/about-adobe-id.md) -dokument. Den innehåller följande uppgifter:

* Installera **[!UICONTROL Integration with the Adobe Experience Cloud]** paket.
* Konfigurera ett externt Adobe Experience Cloud-konto.

>[!NOTE]
>
>De funktioner som är kopplade till den här integreringen är bara tillgängliga för användare som är anslutna till sin Adobe ID via IMS.

## Integrera med AEM Assets {#integrating-with-aem-assets}


>[!CAUTION]
>
>Denna funktion har avvecklats från och med Adobe Experience Manager 6.4. [Läs mer](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html#removed-features)

Om du vill integrera AEM Assets med Adobe Campaign måste du först konfigurera integreringen mellan Adobe Experience Manager och Adobe Campaign. Den här konfigurationen kräver i huvudsak:

* Installera **[!UICONTROL AEM Integration]** inbyggt paket
* Konfigurera ett externt konto som är specifikt för Adobe Experience Manager

Läs om hur du integrerar Adobe Campaign och Adobe Experience Manager i [detaljerad dokumentation](../../integrations/using/about-adobe-experience-manager.md).

När integreringen är klar kan du konfigurera en ny leveransmall i Adobe Campaign så att den kan använda AEM Assets-biblioteket. Gör så här:

1. Skapa en ny leveransmall - eller duplicera en befintlig. Mer information om leveransmallar finns i [den här sidan](../../delivery/using/about-templates.md).
1. Redigera **Egenskaper** för den här mallen.
1. I **[!UICONTROL Advanced]** -flik, ange **[!UICONTROL Content editing mode]** till **DCE**.
1. Välj det externa **[!UICONTROL AEM account]** som du behöver använda för att få tillgång till ditt AEM Assets-bibliotek.

   ![](assets/dam_aem_assets1.png)

När du infogar bilder i ett leveransinnehåll baserat på den här mallen **[!UICONTROL Select a shared asset]** kan du sedan bläddra bland bilderna i AEM Assets bibliotek. Läs mer i [det här avsnittet](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Om **[!UICONTROL Integration with the Adobe Experience Cloud]** paketet är även installerat på din Adobe Campaign-instans. Du kan bara använda resurserna som finns i Adobe Experience Cloud-biblioteket. Om du även vill få tillgång till resurserna i ditt AEM Assets-bibliotek måste du synkronisera AEM Assets och Adobe Experience Cloud. Resurserna i AEM Assets kommer då också att finnas i Adobe Experience Cloud bibliotek. I det här fallet behöver du inte skapa någon särskild leveransmall.
