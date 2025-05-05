---
product: campaign
title: Konfigurera åtkomst till Assets
description: Konfigurera åtkomst till Assets
feature: Asset Sharing
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# Konfigurera åtkomst till Assets {#configuring-access-to-assets}

I det här avsnittet beskrivs de nödvändiga konfigurationsstegen i Adobe Campaign för att använda integreringsfunktionerna i Assets- eller Adobe Experience Manager Assets-biblioteket (AEM Assets).

>[!CAUTION]
>
>Dessa integreringar är samtidiga. Läs nedanstående information noggrant innan du gör någon konfiguration.

* Integrering med **Experience Cloud Assets**: med den här integreringen kan du infoga bilder från ditt Adobe Experience Cloud-bibliotek. Den här integreringen måste konfigureras genom att det inbyggda paketet **[!UICONTROL Integration with the Adobe Experience Cloud]** installeras i Adobe Campaign.
* Integrering med **AEM Assets**: med den här integreringen kan du infoga bilder från ditt Adobe Experience Manager Assets-bibliotek. Den här integreringen måste konfigureras genom att det inbyggda paketet **[!UICONTROL AEM Integration]** installeras i Adobe Campaign. Observera att denna integrering inte längre är tillgänglig från och med Adobe Experience Manager 6.4.

>[!NOTE]
>
>Om de två paketen (**[!UICONTROL AEM Integration]** och **[!UICONTROL Integration with the Adobe Experience Cloud]** ) är installerade kan endast de resurser som är tillgängliga i Adobe Experience Cloud-biblioteket användas.

## Integrera med Experience Cloud Assets {#integrating-with-experience-cloud-assets}

För att kunna använda integreringen mellan Adobe Campaign och Experience Cloud Assets måste du ha:

* Adobe Experience Cloud
* Adobe IMS-autentiseringsläget är aktiverat

Om du vill aktivera anslutningen mellan Adobe Campaign och Adobe Experience Cloud konfigurerar du anslutningen via IMS (Adobe ID anslutningstjänst). Den här konfigurationen beskrivs i dokumentet [Ansluta via Adobe ID](../../integrations/using/about-adobe-id.md). Den innehåller följande uppgifter:

* Installerar paketet **[!UICONTROL Integration with the Adobe Experience Cloud]**.
* Konfigurera ett externt Adobe Experience Cloud-konto.

>[!NOTE]
>
>De funktioner som är kopplade till den här integreringen är bara tillgängliga för användare som är anslutna till sin Adobe ID via IMS.

## Integrera med AEM Assets {#integrating-with-aem-assets}


>[!CAUTION]
>
>Den här funktionen har tagits bort från Adobe Experience Manager 6.4. [Läs mer](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html?lang=sv-SE#removed-features)

Om du vill integrera AEM Assets med Adobe Campaign måste du först konfigurera integreringen mellan Adobe Experience Manager och Adobe Campaign. Den här konfigurationen kräver i huvudsak:

* Installerar det inbyggda paketet **[!UICONTROL AEM Integration]**
* Konfigurera ett externt konto som är specifikt för Adobe Experience Manager

Lär dig hur du integrerar Adobe Campaign och Adobe Experience Manager i den [detaljerade dokumentationen](../../integrations/using/about-adobe-experience-manager.md).

När integreringen är klar kan du konfigurera en ny leveransmall i Adobe Campaign så att den kan använda AEM Assets-biblioteket. Gör så här:

1. Skapa en ny leveransmall - eller duplicera en befintlig. Mer information om leveransmallar finns på [den här sidan](../../delivery/using/about-templates.md).
1. Redigera **egenskaperna** för mallen.
1. På fliken **[!UICONTROL Advanced]** ställer du in **[!UICONTROL Content editing mode]** på **DCE**.
1. Välj den externa **[!UICONTROL AEM account]** som du behöver använda för att komma åt ditt AEM Assets-bibliotek.

   ![](assets/dam_aem_assets1.png)

När du infogar bilder i ett leveransinnehåll som är baserat på den här mallen kan du med alternativet **[!UICONTROL Select a shared asset]** bläddra bland bilder i AEM Assets-biblioteket. Läs mer i [det här avsnittet](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Om **[!UICONTROL Integration with the Adobe Experience Cloud]**-paketet också är installerat på din Adobe Campaign-instans kan du bara använda resurserna som finns i Adobe Experience Cloud-biblioteket. Om du även vill få tillgång till resurserna i ditt AEM Assets-bibliotek måste du synkronisera AEM Assets och Adobe Experience Cloud. Resurserna i AEM Assets kommer då också att finnas i Adobe Experience Cloud bibliotek. I det här fallet behöver du inte skapa någon särskild leveransmall.
