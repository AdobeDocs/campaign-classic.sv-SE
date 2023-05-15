---
product: campaign
title: Konfigurera åtkomst till resurser
description: Konfigurera åtkomst till resurser
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: asset-sharing
exl-id: f3897a40-b080-47e5-9e31-4d861c1bacd5
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 1%

---

# Konfigurera åtkomst till resurser{#configuring-access-to-assets}



I det här avsnittet beskrivs de konfigurationssteg som krävs i Adobe Campaign för att använda integreringsfunktionerna med bastjänsten Assets eller Adobe Experience Manager Assets-biblioteket (AEM Assets).

>[!CAUTION]
>
>Dessa integreringar är samtidiga. Läs nedanstående information noggrant innan du gör någon konfiguration.

* Integration med **Experience Cloud Assets**: Med den här integreringen kan du infoga bilder från ditt Adobe Experience Cloud-bibliotek. Integrationen måste konfigureras genom att installera **[!UICONTROL Integration with the Adobe Experience Cloud]** inbyggt paket i Adobe Campaign.
* Integration med **AEM Assets**: Med den här integreringen kan du infoga bilder från ditt Adobe Experience Manager Assets-bibliotek. Integrationen måste konfigureras genom att installera **[!UICONTROL AEM Integration]** inbyggt paket i Adobe Campaign. Observera att den här integreringen inte längre är tillgänglig från och med Adobe Experience Manager 6.4.

>[!NOTE]
>
>Om de två paketen (**[!UICONTROL AEM Integration]** och **[!UICONTROL Integration with the Adobe Experience Cloud]** ) är installerat kan endast de resurser som finns i Adobe Experience Cloud-biblioteket användas.

## Integrera med Experience Cloud Assets {#integrating-with-experience-cloud-assets}

För att kunna använda integreringen mellan Adobe Campaign och Experience Cloud Assets måste du ha:

* En Adobe Experience Cloud-organisation
* Autentiseringsläget för Adobe IMS är aktiverat

Om du vill aktivera anslutningen mellan Adobe Campaign och Adobe Experience Cloud konfigurerar du anslutningen via IMS (Adobe ID anslutningstjänst). Den här konfigurationen beskrivs i [Ansluta via en Adobe ID](../../integrations/using/about-adobe-id.md) -dokument. Den innehåller följande uppgifter:

* Installera **[!UICONTROL Integration with the Adobe Experience Cloud]** paket.
* Konfigurera ett externt Adobe Experience Cloud-konto.

>[!NOTE]
>
>De funktioner som är kopplade till den här integreringen är bara tillgängliga för användare som är anslutna till sin Adobe ID via IMS.

## Integrera med AEM Assets {#integrating-with-aem-assets}


>[!CAUTION]
>
>Denna funktion har avvecklats från och med Adobe Experience Manager 6.4. [Läs mer](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html?lang=en#removed-features)

Om du vill integrera AEM Assets med Adobe Campaign måste du först konfigurera integreringen mellan Adobe Experience Manager och Adobe Campaign. Den här konfigurationen kräver i huvudsak:

* Installera **[!UICONTROL AEM Integration]** inbyggt paket
* Konfigurera ett externt konto som är specifikt för Adobe Experience Manager

Läs om hur du integrerar Adobe Campaign och Adobe Experience Manager i [detaljerad dokumentation](../../integrations/using/about-adobe-experience-manager.md).

När integreringen är klar kan du konfigurera en ny leveransmall i Adobe Campaign så att den kan använda AEM Assets-biblioteket. Följ stegen nedan för att göra detta:

1. Skapa en ny leveransmall - eller duplicera en befintlig. Mer information om leveransmallar finns i [den här sidan](../../delivery/using/about-templates.md).
1. Redigera **Egenskaper** för den här mallen.
1. I **[!UICONTROL Advanced]** -fliken, ange **[!UICONTROL Content editing mode]** till **DCE**.
1. Välj externa **[!UICONTROL AEM account]** som du behöver använda för att få tillgång till ditt AEM Assets-bibliotek.

   ![](assets/dam_aem_assets1.png)

När du infogar bilder i ett leveransinnehåll baserat på den här mallen **[!UICONTROL Select a shared asset]** kan du sedan bläddra bland bilderna i AEM Assets-biblioteket. Läs mer i [det här avsnittet](../../integrations/using/inserting-a-shared-asset.md).

>[!NOTE]
>
>Om **[!UICONTROL Integration with the Adobe Experience Cloud]** paketet är även installerat på din Adobe Campaign-instans. Du kan bara använda resurserna som finns i Adobe Experience Cloud-biblioteket. Om du även vill få tillgång till resurserna i ditt AEM Assets-bibliotek måste du synkronisera AEM Assets och Adobe Experience Cloud. Resurserna i AEM Assets finns sedan också i Adobe Experience Cloud bibliotek. I det här fallet behöver du inte skapa någon särskild leveransmall.
