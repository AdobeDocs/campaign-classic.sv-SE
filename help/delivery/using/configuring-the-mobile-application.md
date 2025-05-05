---
product: campaign
title: Konfigurera iOS-mobilprogrammet i Adobe Campaign
description: Läs om hur du ställer in din mobilapp för iOS
feature: Push
role: User, Developer
level: Intermediate, Experienced
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 3%

---

# Konfigurationssteg för iOS {#configuring-the-mobile-application-in-adobe-campaign-ios}

När paketet har installerats kan du definiera inställningarna för iOS-appen i Adobe Campaign Classic.

De viktigaste stegen är:

1. [Konfigurera det externa iOS-kontot](#configuring-external-account-ios)
1. [Konfigurera iOS-tjänsten](#configuring-ios-service)
1. [Integrera iOS-mobilappen i Campaign](#creating-ios-app)

Du kommer då att [kunna skapa ett push-meddelande för iOS-enheter](create-notifications-ios.md).

## Konfigurera externt iOS-konto {#configuring-external-account-ios}

För iOS skickar iOS HTTP/2-anslutningsappen meddelanden till HTTP/2 APN:erna.

Följ dessa steg för att konfigurera den här anslutningsappen:

1. Gå till **[!UICONTROL Administration > Platform > External accounts]**.
1. Välj det **[!UICONTROL iOS routing]** externa kontot.
1. **[!UICONTROL Connector]** På fliken fyller du i **[!UICONTROL Access URL of the connector]** fältet med följande URL:```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. Klicka på **[!UICONTROL Save]**.

iOS-anslutningsappen är nu konfigurerad. Du kan börja skapa din tjänst.

## Konfigurera iOS-tjänsten {#configuring-ios-service}

>[!CAUTION]
>
>Programmet måste ha konfigurerats för push-åtgärder INNAN du integrerar med Adobe SDK.
>
>Om så inte är fallet, se [den här sidan](https://developer.apple.com/documentation/usernotifications).

1. Gå till noden **[!UICONTROL Profiles and Targets > Services and subscriptions]** och klicka på **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. Definiera a **[!UICONTROL Label]** och en **[!UICONTROL Internal name]**.
1. Gå till fältet **[!UICONTROL Type]** och välj **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >Standardmålmappningen **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** är länkad till mottagartabellen. Om du vill använda en annan målmappning måste du skapa en ny målmappning och ange den i fältet för **[!UICONTROL Target mapping]** tjänsten. Mer information om hur du skapar målmappning finns i konfigurationsguiden[&#128279;](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. Klicka sedan på **[!UICONTROL Add]** knappen för att välja programtyp.

   ![](assets/nmac_service_2.png)

1. Skapa dina iOS-utvecklings- och produktionsprogram. Mer information om detta hittar du i det här [avsnittet](configuring-the-mobile-application.md#creating-ios-app).

## Skapa iOS-mobilapp {#creating-ios-app}

När du har skapat tjänsten skapar du ditt iOS-program i Campaign. Följ stegen nedan:

1. Från den nyligen skapade tjänsten klickar du på knappen för **[!UICONTROL Add]** att välja programtyp.

   ![](assets/nmac_service_2.png)

1. Följande fönster visas. Välj **[!UICONTROL Create an iOS application]** och börja med att ange .**[!UICONTROL Label]**

   ![](assets/nmac_ios_2.png)

1. Som ett alternativ kan du utöka innehållet i ett push-meddelande med lite **[!UICONTROL Application variables]** om det behövs. Dessa är helt anpassningsbara och en del av meddelandenyttolasten som skickas till den mobila enheten.
I följande exempel lägger vi till **mediaURl** och **mediaExt** för att skapa omfattande push-meddelanden och förser sedan programmet med bilden som ska visas i meddelandet.

   ![](assets/nmac_ios_3.png)

1. På fliken **[!UICONTROL Subscription parameters]** kan du definiera mappningen med ett tillägg till schemat **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**.

   >[!NOTE]
   >
   >Se till att du inte använder samma certifikat för utvecklingsversionen (sandbox-miljön) och produktionsversionen av programmet.

1. På **[!UICONTROL Sounds]** fliken kan du ange ett ljud som ska spelas upp. Klicka **[!UICONTROL Add]** och fyll i **[!UICONTROL Internal name]** fält som måste innehålla namnet på filen som är inbäddad i programmet eller namnet på systemljudet.

1. Klicka för **[!UICONTROL Next]** att börja konfigurera utvecklingsprogrammet.

1. Se till att samma **[!UICONTROL Integration key]** definieras i Adobe Campaign och i programkoden via SDK. <!--For more on this, refer to [this page](integrating-campaign-sdk-into-the-mobile-application.md).--> Med den här integreringsnyckeln, som är specifik för varje program, kan du länka mobilprogrammet till Adobe Campaign-plattformen.

   >[!NOTE]
   >
   > Den **[!UICONTROL Integration key]** är helt anpassningsbar med strängvärdet men måste vara exakt samma som den som anges i SDK:n.

1. Välj en av de färdiga ikonerna i fältet **[!UICONTROL Application icon]** för att anpassa mobilprogrammet i din tjänst.

1. Markera **[!UICONTROL Authentication mode]**.

   ![](assets/nmac_ios_5.png)

   Det finns två lägen:

   * (Rekommenderas) **[!UICONTROL Token-based authentication]**: Fyll i APNs anslutningsinställningar **[!UICONTROL Key Id]**&#x200B;**[!UICONTROL Team Id]** och **[!UICONTROL Bundle Id]** välj sedan ditt p8-certifikat genom att klicka på **[!UICONTROL Enter the private key...]**. Mer information **[!UICONTROL Token-based authentication]** finns i [Apples dokumentation](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns){target="_blank"}.

   * **[!UICONTROL Certificate-based authentication]**: Klicka och **[!UICONTROL Enter the certificate...]**  välj sedan din p12-nyckel och ange lösenordet som tillhandahölls av mobilapplikationsutvecklaren.

   >[!NOTE]
   >
   > Adobe rekommenderar att du använder **[!UICONTROL Token-based authentication]** det för din iOS-konfiguration eftersom P8-autentiseringsnycklar är nyare och säkrare.

1. Använd knappen för att verifiera konfigurationen **[!UICONTROL Test the connection]** .

1. Klicka för **[!UICONTROL Next]** att börja konfigurera produktionsprogrammet och följ samma steg som beskrivs ovan.


1. Klicka på **[!UICONTROL Finish]**.

Ditt iOS-program är nu redo att användas i Campaign Classic.
