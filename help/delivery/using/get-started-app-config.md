---
product: campaign
title: 'Konfigurera den mobila applikationen i Adobe Campaign '
description: Lär dig hur du börjar med konfigurationen för mobilprogrammet
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
source-git-commit: 00b8a9b4a693920aa6b4be9e7c41f08c2e53a0c6
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 10%

---

# Kom igång med konfigurationen av appen

I det här avsnittet hittar du ett konfigurationsexempel baserat på ett företag som säljer semesterpaket online. Hans mobilapplikation (Neotrips) finns i två versioner: Neotrips för Android och Neotrips för iOS.

Om du vill skicka push-meddelanden i Adobe Campaign måste du:

* Skapa en **[!UICONTROL Mobile application]** Type Information Service för mobilappen Neotrips. Se [det här avsnittet för iOS](configuring-the-mobile-application.md#configuring-ios-service). och [det här avsnittet för Android](configuring-the-mobile-application-android.md#configuring-android-service).
* Lägg till iOS- och Android-versionerna av programmet i den här tjänsten.
* Skapa en leverans för [iOS](create-notifications-ios.md) och [Android](create-notifications-android.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Gå till **[!UICONTROL Subscriptions]** -fliken för tjänsten om du vill visa en lista över prenumeranter på tjänsten, dvs. alla personer som har installerat programmet på mobilen och gått med på att ta emot meddelanden.

## Installera paketet {#installing-package-ios}

![](assets/do-not-localize/how-to-video.png) [Lär dig hur du installerar mobilappspaketet i video](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=en#sending-messages)

Som hybridkund/värdkund kontaktar du [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team för att komma åt push-meddelandekanalen i Campaign.

Som lokal kund måste du installera ett inbyggt paket.

>[!CAUTION]
>
>Läs mer om Campaigns inbyggda paket, bästa praxis och rekommendationer i [den här sidan](../../installation/using/installing-campaign-standard-packages.md).

Installationsstegen är:

1. Öppna guiden för paketimport från **[!UICONTROL Tools > Advanced > Import package]** i Adobe Campaign klientkonsol.

   ![](assets/package_ios.png)

1. Välj **[!UICONTROL Install a standard package]**.

1. I listan som visas markerar du **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Klicka **[!UICONTROL Next]** sedan **[!UICONTROL Start]** för att starta paketinstallationen.

   När paketen har installerats visas förloppsindikatorn **100 %** och följande meddelande visas i installationsloggarna: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** installationsfönstret.

När det här steget är klart kan du konfigurera dina Android- och iOS-appar.
Se följande avsnitt:

* [Konfigurationssteg för iOS](configuring-the-mobile-application.md)

* [Konfigurationssteg för Android](configuring-the-mobile-application-android.md)
