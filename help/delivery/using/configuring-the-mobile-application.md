---
solution: Campaign Classic
product: campaign
title: Konfigurera iOS-mobilprogrammet i Adobe Campaign
description: Lär dig hur du konfigurerar ditt mobilprogram för iOS
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: a1bd8dc2b5946b74cb880eff934e3b35cadfb2d2
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 7%

---


# Konfigurationssteg för iOS {#configuring-the-mobile-application-in-adobe-campaign-ios}

När paketet har installerats kan du definiera dina iOS-appinställningar i Adobe Campaign Classic.

>[!NOTE]
>
>Mer information om hur du konfigurerar din app för Android och hur du skapar en leverans för Android finns i det här [avsnittet](../../delivery/using/configuring-the-mobile-application-android.md).

## Konfigurera externt iOS-konto {#configuring-external-account-ios}

För iOS skickar iOS HTTP/2-anslutningen meddelanden till HTTP/2 APN:er.

Så här konfigurerar du den här kopplingen:

1. Gå till **[!UICONTROL Administration > Platform > External accounts]**.
1. Select the **[!UICONTROL iOS routing]** external account.
1. På fliken **[!UICONTROL Connector]** fyller du i **[!UICONTROL Access URL of the connector]** fältet med följande URL: ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   >[!NOTE]
   >
   > Från och med Campaign version 20.3 är den gamla binära kopplingen för iOS inaktuell. Om du använder den här kopplingen måste du anpassa implementeringen i enlighet med detta. [Läs mer](https://helpx.adobe.com/se/campaign/kb/migrate-to-apns-http2.html)

   ![](assets/nmac_connectors.png)

1. Klicka på **[!UICONTROL Save]**.

Din iOS-anslutning är nu konfigurerad. Du kan börja skapa tjänsten.

## Konfigurerar iOS-tjänsten {#configuring-ios-service}

>[!CAUTION]
>
>Programmet måste ha konfigurerats för push-åtgärder FÖRE integrering med Adobe Campaign SDK.
>
>Om så inte är fallet, se [den här sidan](https://developer.apple.com/documentation/usernotifications).

1. Gå till **[!UICONTROL Profiles and Targets > Services and subscriptions]** noden och klicka på **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Define a **[!UICONTROL Label]** and an **[!UICONTROL Internal name]**.
1. Gå till **[!UICONTROL Type]** fältet och välj **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >Standardmålmappningen **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** är länkad till mottagartabellen. Om du vill använda en annan målmappning måste du skapa en ny målmappning och ange den i **[!UICONTROL Target mapping]** fältet för tjänsten. Mer information om hur du skapar målmappning finns i [konfigurationsguiden](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Klicka sedan på **[!UICONTROL Add]** knappen för att välja programtyp.

   ![](assets/nmac_service_2.png)

1. Skapa iOS-utvecklings- och produktionsprogram. Mer information om detta hittar du i det här [avsnittet](../../delivery/using/configuring-the-mobile-application.md#creating-ios-app).

## Skapa iOS-mobilprogram {#creating-ios-app}

När du har skapat tjänsten måste du nu skapa iOS-programmet:

1. Klicka på knappen för att välja programtyp i den nya tjänsten **[!UICONTROL Add]** .

   ![](assets/nmac_service_2.png)

1. Följande fönster visas. Markera **[!UICONTROL Create an iOS application]** och börja med att ange **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. Som ett alternativ kan du utöka ett push-meddelandeinnehåll med vissa **[!UICONTROL Application variables]** om det behövs. Dessa är helt anpassningsbara och utgör en del av den meddelandenyttolast som skickas till den mobila enheten.
I följande exempel lägger vi till **mediaURl** och **mediaExt** för att skapa ett omfattande push-meddelande och förser sedan programmet med den bild som ska visas i meddelandet.

   ![](assets/nmac_ios_3.png)

1. På fliken **[!UICONTROL Subscription parameters]** kan du definiera mappningen med ett tillägg till **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** schemat.

   >[!NOTE]
   >
   >Se till att du inte använder samma certifikat för utvecklingsversionen (sandlådan) och produktionsversionen av programmet.

1. På fliken **[!UICONTROL Sounds]** kan du ange vilket ljud som ska spelas upp. Klicka **[!UICONTROL Add]** och fyll i **[!UICONTROL Internal name]** fält som måste innehålla namnet på filen som är inbäddad i programmet eller namnet på systemljudet.

1. Klicka **[!UICONTROL Next]** för att börja konfigurera utvecklingsprogrammet.

1. Se till att samma **[!UICONTROL Integration key]** är definierat i Adobe Campaign och i programkoden via SDK. Mer information finns i: [Integrera Campaign SDK i mobilapplikationen](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md). Med den här integrationsnyckeln, som är specifik för varje program, kan du länka mobilprogrammet till Adobe Campaign-plattformen.

   >[!NOTE]
   >
   > Det går **[!UICONTROL Integration key]** att anpassa med strängvärde, men det måste vara exakt detsamma som det som anges i SDK:n.

1. Välj en av de användningsklara ikonerna i fältet för att anpassa mobilapplikationen i din tjänst. **[!UICONTROL Application icon]**

1. Markera **[!UICONTROL Authentication mode]**. Observera att du alltid kan ändra ditt autentiseringsläge senare på fliken **[!UICONTROL Certificate]** i ditt mobilprogram.
   * **[!UICONTROL Certificate-based authentication]**: Klicka **[!UICONTROL Enter the certificate...]** sedan på din p12-nyckel och ange lösenordet som utvecklaren av mobilprogrammet angett.
   * **[!UICONTROL Token-based authentication]**: Fyll i anslutningsinställningarna **[!UICONTROL Key ID]** och välj **[!UICONTROL Team ID]** sedan ditt p8-certifikat genom att klicka på **[!UICONTROL Bundle ID]** **[!UICONTROL Enter the private key]**. For more on **[!UICONTROL Token-based authentication]**, refer to [Apple documentation](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns).

   >[!NOTE]
   >
   > Adobe rekommenderar att du använder **[!UICONTROL Token-based authentication]** för din iOS-konfiguration eftersom det här autentiseringsläget är säkrare och inte bundet till certifikatets förfallodatum.

   ![](assets/nmac_ios_4.png)

1. Du kan klicka **[!UICONTROL Test the connection]** för att kontrollera att det fungerar.

1. Klicka **[!UICONTROL Next]** för att börja konfigurera produktionsprogrammet och följ stegen som beskrivs ovan.

   ![](assets/nmac_ios_5.png)

1. Klicka på **[!UICONTROL Finish]**.

iOS-programmet är nu klart att användas i Campaign Classic.

## Skapa ett iOS-meddelande {#creating-ios-delivery}

I iOS 10 eller senare är det möjligt att generera omfattande meddelanden. Adobe Campaign kan skicka meddelanden med variabler som gör att enheten kan visa ett omfattande meddelande.

Nu måste du skapa en ny leverans och länka den till mobilappen som du har skapat.

1. Gå till **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klicka på **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Välj **[!UICONTROL Deliver on iOS (ios)]** i **[!UICONTROL Delivery template]** listrutan. Lägg till en **[!UICONTROL Label]** till leveransen.

1. Klicka **[!UICONTROL To]** för att definiera målpopulationen. Som standard används **[!UICONTROL Subscriber application]** målmappningen. Klicka **[!UICONTROL Add]** för att välja den tjänst du skapade tidigare.

   ![](assets/nmac_ios_9.png)

1. I **[!UICONTROL Target type]** fönstret markerar du **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** och klickar **[!UICONTROL Next]**.

1. I **[!UICONTROL Service]** listrutan väljer du den tjänst du skapat tidigare, det program du vill ha som mål och klickar på **[!UICONTROL Finish]**.
De **[!UICONTROL Application variables]** läggs automatiskt till beroende på vad som lades till under konfigurationsstegen.

   ![](assets/nmac_ios_6.png)

1. Redigera dina meddelanden.

   ![](assets/nmac_ios_7.png)

1. Markera **[!UICONTROL Mutable content]** rutan i fönstret för redigeringsmeddelanden så att mobilprogrammet kan hämta medieinnehåll.

1. Klicka **[!UICONTROL Save]** och skicka leveransen.

Bilden och webbsidan ska visas i push-meddelandet när de tas emot på prenumerantens mobila iOS-enheter.

![](assets/nmac_ios_8.png)
