---
product: campaign
title: Konfigurera iOS mobilprogram i Adobe Campaign
description: Lär dig hur du konfigurerar ditt mobilprogram för iOS
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Push
role: User, Developer
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: 466f04bce8f4c62b5dbb0e9d15150ab0c3bf2fbd
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 4%

---

# Konfigurationssteg för iOS {#configuring-the-mobile-application-in-adobe-campaign-ios}

När paketet har installerats kan du definiera dina programinställningar för iOS i Adobe Campaign Classic.

Viktiga steg är:

1. [Konfigurera iOS externa konto](#configuring-external-account-ios)
1. [Konfigurera iOS-tjänsten](#configuring-ios-service)
1. [Integrera iOS mobilapp i Campaign](#creating-ios-app)

Då kan du [skapa ett push-meddelande för iOS-enheter](create-notifications-ios.md).

## Konfigurera iOS externa konto {#configuring-external-account-ios}

För iOS skickar iOS HTTP/2-anslutningen meddelanden till HTTP/2 APN:er.

Så här konfigurerar du den här kopplingen:

1. Gå till **[!UICONTROL Administration > Platform > External accounts]**.
1. Välj **[!UICONTROL iOS routing]** externt konto.
1. I **[!UICONTROL Connector]** -flik, fylla i **[!UICONTROL Access URL of the connector]** fält med följande URL: ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. Klicka på **[!UICONTROL Save]**.

Din iOS-anslutning är nu konfigurerad. Du kan börja skapa tjänsten.

## Konfigurera iOS-tjänsten {#configuring-ios-service}

>[!CAUTION]
>
>Programmet måste ha konfigurerats för push-åtgärder FÖRE integrering med Adobe SDK.
>
>Om så inte är fallet, se [den här sidan](https://developer.apple.com/documentation/usernotifications).

1. Gå till **[!UICONTROL Profiles and Targets > Services and subscriptions]** och klicka på **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Definiera en **[!UICONTROL Label]** och **[!UICONTROL Internal name]**.
1. Gå till **[!UICONTROL Type]** fält och markera **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >Standardvärdet **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** målmappningen är länkad till mottagartabellen. Om du vill använda en annan målmappning måste du skapa en ny målmappning och ange den i **[!UICONTROL Target mapping]** tjänstens fält. Mer information om hur du skapar målmappning finns i [Konfigurationsguide](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Klicka sedan på **[!UICONTROL Add]** för att välja programtyp.

   ![](assets/nmac_service_2.png)

1. Skapa dina iOS-program för utveckling och produktion. Mer information om detta hittar du i det här [avsnittet](configuring-the-mobile-application.md#creating-ios-app).

## Skapa iOS mobilapp {#creating-ios-app}

Skapa iOS-programmet i Campaign när du har skapat tjänsten. Följ stegen nedan:

1. Klicka på **[!UICONTROL Add]** för att välja programtyp.

   ![](assets/nmac_service_2.png)

1. Följande fönster visas. Välj **[!UICONTROL Create an iOS application]** och börja med att ange **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. Som ett alternativ kan du utöka ett push-meddelandeinnehåll med **[!UICONTROL Application variables]** vid behov. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.
I följande exempel lägger vi till **mediaURl** och **mediaExt** för att skapa omfattande push-meddelanden och sedan förse programmet med den bild som ska visas i meddelandet.

   ![](assets/nmac_ios_3.png)

1. The **[!UICONTROL Subscription parameters]** kan du definiera mappningen med ett tillägg till **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** schema.

   >[!NOTE]
   >
   >Se till att du inte använder samma certifikat för utvecklingsversionen (sandlådan) och produktionsversionen av programmet.

1. The **[!UICONTROL Sounds]** kan du ange vilket ljud som ska spelas upp. Klicka **[!UICONTROL Add]** och fylla **[!UICONTROL Internal name]** fält som måste innehålla namnet på filen som är inbäddad i programmet eller namnet på systemljudet.

1. Klicka **[!UICONTROL Next]** för att börja konfigurera utvecklingsprogrammet.

1. Se till att samma **[!UICONTROL Integration key]** definieras i Adobe Campaign och i programkoden via SDK. Mer information finns i [den här sidan](integrating-campaign-sdk-into-the-mobile-application.md). Med den här integrationsnyckeln, som är specifik för varje program, kan du länka mobilprogrammet till Adobe Campaign-plattformen.

   >[!NOTE]
   >
   > The **[!UICONTROL Integration key]** är helt anpassningsbart med strängvärde, men måste vara exakt densamma som den som anges i SDK:n.

1. Välj en av de färdiga ikonerna i dialogrutan **[!UICONTROL Application icon]** för att personalisera mobilapplikationer i din tjänst.

1. Markera **[!UICONTROL Authentication mode]**.

   ![](assets/nmac_ios_5.png)

   Det finns två lägen:

   * (Rekommenderas) **[!UICONTROL Token-based authentication]**: Fyll i APN-anslutningsinställningarna **[!UICONTROL Key Id]**, **[!UICONTROL Team Id]** och **[!UICONTROL Bundle Id]** välj sedan ditt p8-certifikat genom att klicka på **[!UICONTROL Enter the private key...]**. Om du vill ha mer **[!UICONTROL Token-based authentication]**, se [Apple-dokumentation](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns){target="_blank"}.

   * **[!UICONTROL Certificate-based authentication]**: Klicka **[!UICONTROL Enter the certificate...]**  välj sedan din p12-nyckel och ange lösenordet som angavs av mobilprogramutvecklaren.

   >[!NOTE]
   >
   > Adobe rekommenderar att du använder **[!UICONTROL Token-based authentication]** för din iOS-konfiguration eftersom autentiseringsnycklarna för P8 är nyare och säkrare.

1. Använd **[!UICONTROL Test the connection]** för att validera konfigurationen.

1. Klicka **[!UICONTROL Next]** för att börja konfigurera produktionsprogrammet och följa de steg som beskrivs ovan.


1. Klicka på **[!UICONTROL Finish]**.

Ditt iOS-program kan nu användas i Campaign Classic.
