---
product: campaign
title: Konfigurera mobilprogrammet i Adobe Campaign
description: Lär dig hur du börjar med konfigurationen för mobilprogrammet
feature: Push
role: User, Developer
level: Intermediate, Experienced
hide: true
hidefromtoc: true
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
source-git-commit: 89e350c727fb9379d28916f79d9749f22fd4974f
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 5%

---

# Kom igång med konfigurationen av appen



I det här avsnittet hittar du ett konfigurationsexempel baserat på ett företag som säljer semesterpaket online. Dess mobilapplikation (Neotrips) är tillgänglig för kunderna i två versioner: Neotrips för Android och Neotrips för iOS.

Om du vill skicka push-meddelanden i Adobe Campaign måste du:

* Skapa en **[!UICONTROL Mobile application]**-typinformationstjänst för mobilprogrammet Neotrips. Se [det här avsnittet för iOS](configuring-the-mobile-application.md#configuring-ios-service). och [det här avsnittet för Android](configuring-the-mobile-application-android.md#configuring-android-service).
* Lägg till iOS- och Android-versionerna av programmet i den här tjänsten.
* Skapa en leverans för [iOS](create-notifications-ios.md) och [Android](create-notifications-android.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Gå till fliken **[!UICONTROL Subscriptions]** i tjänsten om du vill visa en lista över prenumeranter på tjänsten, dvs. alla personer som har installerat programmet på mobilen och gått med på att ta emot meddelanden.

## Installera paketet {#installing-package-ios}

[!BADGE Lokal och hybrid]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"}

![](assets/do-not-localize/how-to-video.png) [Lär dig hur du installerar mobilappspaketet i video](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=sv-SE#sending-messages)

Kontakta [Adobe Customer Care](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) -teamet om du vill få åtkomst till en push-meddelandekanal i Campaign som hybridkund/värdkund.

Som lokal kund måste du installera ett inbyggt paket.

>[!CAUTION]
>
>Läs mer om Campaigns inbyggda paket, metodtips och rekommendationer i [den här sidan](../../installation/using/installing-campaign-standard-packages.md).

Installationsstegen är:

1. Få åtkomst till paketimportassistenten från **[!UICONTROL Tools > Advanced > Import package]** i Adobe Campaign klientkonsol.

   ![](assets/package_ios.png)

1. Välj **[!UICONTROL Install a standard package]**.

1. Markera **[!UICONTROL Mobile App Channel]** i listan som visas.

   ![](assets/package_ios_2.png)

1. Klicka på **[!UICONTROL Next]** och sedan på **[!UICONTROL Start]** för att starta paketinstallationen.

   När paketen har installerats visas **100%** i förloppsindikatorn och följande meddelande visas i installationsloggarna: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** installationsfönstret.

När det här steget är klart kan du konfigurera dina Android- och iOS-appar.
Se följande avsnitt:

* [Konfigurationssteg för iOS](configuring-the-mobile-application.md)

* [Konfigurationssteg för Android](configuring-the-mobile-application-android.md)
