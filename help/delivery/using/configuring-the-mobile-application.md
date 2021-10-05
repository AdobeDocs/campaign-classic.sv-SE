---
product: campaign
title: Konfigurera iOS-mobilprogrammet i Adobe Campaign
description: Lär dig hur du konfigurerar ditt mobilprogram för iOS
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 5%

---

# Konfigurationssteg för iOS {#configuring-the-mobile-application-in-adobe-campaign-ios}

![](../../assets/common.svg)

När paketet har installerats kan du definiera dina iOS-appinställningar i Adobe Campaign Classic.

>[!NOTE]
>
>Mer information om hur du konfigurerar din app för Android och hur du skapar en leverans för Android finns i [avsnittet](configuring-the-mobile-application-android.md).

Viktiga steg är:

1. [Konfigurera det externa iOS-kontot](#configuring-external-account-ios)
1. [Konfigurera iOS-tjänsten](#configuring-ios-service)
1. [Integrera iOS-mobilappen i Campaign](#creating-ios-app)

Du kan sedan [skapa ett push-meddelande för iOS-enheter](create-notifications-ios.md).


## Konfigurera externt iOS-konto {#configuring-external-account-ios}

För iOS skickar iOS HTTP/2-anslutningen meddelanden till HTTP/2 APN:er.

Så här konfigurerar du den här kopplingen:

1. Gå till **[!UICONTROL Administration > Platform > External accounts]**.
1. Välj det externa **[!UICONTROL iOS routing]**-kontot.
1. På fliken **[!UICONTROL Connector]** fyller du i fältet **[!UICONTROL Access URL of the connector]** med följande URL: ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. Klicka på **[!UICONTROL Save]**.

Din iOS-anslutning är nu konfigurerad. Du kan börja skapa tjänsten.

## Konfigurera iOS-tjänsten {#configuring-ios-service}

>[!CAUTION]
>
>Programmet måste ha konfigurerats för push-åtgärder FÖRE integrering med Adobe Campaign SDK.
>
>Om så inte är fallet, se [den här sidan](https://developer.apple.com/documentation/usernotifications).

1. Gå till noden **[!UICONTROL Profiles and Targets > Services and subscriptions]** och klicka på **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Definiera en **[!UICONTROL Label]** och en **[!UICONTROL Internal name]**.
1. Gå till fältet **[!UICONTROL Type]** och välj **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >Standardmålmappningen för **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** är länkad till mottagartabellen. Om du vill använda en annan målmappning måste du skapa en ny målmappning och ange den i fältet **[!UICONTROL Target mapping]** för tjänsten. Mer information om hur du skapar målmappning finns i [Konfigurationshandboken](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Klicka sedan på knappen **[!UICONTROL Add]** för att välja programtyp.

   ![](assets/nmac_service_2.png)

1. Skapa iOS-utvecklings- och produktionsprogram. Mer information om detta hittar du i det här [avsnittet](configuring-the-mobile-application.md#creating-ios-app).

## Skapa iOS-mobilapp {#creating-ios-app}

Skapa iOS-programmet i Campaign när du har skapat tjänsten. Följ stegen nedan:

1. Klicka på knappen **[!UICONTROL Add]** för att välja programtyp i den nya tjänsten.

   ![](assets/nmac_service_2.png)

1. Följande fönster visas. Välj **[!UICONTROL Create an iOS application]** och börja med att ange **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. Som ett alternativ kan du utöka ett push-meddelandeinnehåll med **[!UICONTROL Application variables]** om det behövs. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.
I följande exempel lägger vi till **mediaURl** och **mediaExt** för att skapa ett omfattande push-meddelande och förser sedan programmet med bilden som ska visas i meddelandet.

   ![](assets/nmac_ios_3.png)

1. På fliken **[!UICONTROL Subscription parameters]** kan du definiera mappningen med ett tillägg till schemat **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**.

   >[!NOTE]
   >
   >Se till att du inte använder samma certifikat för utvecklingsversionen (sandlådan) och produktionsversionen av programmet.

1. På fliken **[!UICONTROL Sounds]** kan du ange vilket ljud som ska spelas upp. Klicka på **[!UICONTROL Add]** och fyll i fältet **[!UICONTROL Internal name]** som måste innehålla namnet på filen som är inbäddad i programmet eller namnet på systemljudet.

1. Klicka på **[!UICONTROL Next]** för att börja konfigurera utvecklingsprogrammet.

1. Se till att samma **[!UICONTROL Integration key]** är definierat i Adobe Campaign och i programkoden via SDK. Mer information finns i: [Integrera Campaign SDK i mobilprogrammet](integrating-campaign-sdk-into-the-mobile-application.md). Med den här integrationsnyckeln, som är specifik för varje program, kan du länka mobilprogrammet till Adobe Campaign-plattformen.

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]** är helt anpassningsbar med strängvärde, men måste vara exakt densamma som den som anges i SDK:n.

1. Välj en av de färdiga ikonerna i fältet **[!UICONTROL Application icon]** för att anpassa mobilprogrammet i tjänsten.

1. Markera **[!UICONTROL Authentication mode]**. Observera att du alltid kan ändra autentiseringsläget senare på fliken **[!UICONTROL Certificate]** i ditt mobilprogram.
   * **[!UICONTROL Certificate-based authentication]**: Klicka  **[!UICONTROL Enter the certificate...]**  sedan på din p12-nyckel och ange lösenordet som utvecklaren av mobilprogrammet angett.
   * **[!UICONTROL Token-based authentication]**: Fyll i anslutningsinställningarna  **[!UICONTROL Key ID]** och välj  **[!UICONTROL Team ID]** sedan ditt p8-certifikat genom att klicka på  **[!UICONTROL Bundle ID]**   **[!UICONTROL Enter the private key]**. Mer information om **[!UICONTROL Token-based authentication]** finns i [Apple-dokumentation](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns).

   >[!NOTE]
   >
   > Adobe rekommenderar att du använder **[!UICONTROL Token-based authentication]** för din iOS-konfiguration eftersom det här autentiseringsläget är säkrare och inte bundet till certifikatets förfallodatum.

   ![](assets/nmac_ios_4.png)

1. Du kan klicka på **[!UICONTROL Test the connection]** för att kontrollera att det fungerar.

1. Klicka på **[!UICONTROL Next]** för att börja konfigurera produktionsprogrammet och följ stegen som anges ovan.

   ![](assets/nmac_ios_5.png)

1. Klicka på **[!UICONTROL Finish]**.

iOS-programmet är nu klart att användas i Campaign Classic.
