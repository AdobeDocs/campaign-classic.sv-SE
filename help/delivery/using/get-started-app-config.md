---
solution: Campaign Classic
product: campaign
title: 'Konfigurera den mobila applikationen i Adobe Campaign '
description: Lär dig hur du börjar med konfigurationen för mobilprogrammet
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 1d7d48f52f69e4902eafa6806c2cd9170c21fe5a
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 9%

---


# Kom igång med konfigurationen av appen

I det här avsnittet hittar du ett konfigurationsexempel baserat på ett företag som säljer semesterpaket online. Hans mobilapplikation (Neotrips) finns i två versioner: Neotrips för Android och Neotrips för iOS.

Om du vill skicka push-meddelanden i Adobe Campaign måste du:

* Skapa en **[!UICONTROL Mobile application]**-typinformationstjänst för mobilprogrammet Neotrips. Se [det här avsnittet för iOS](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service). och [det här avsnittet för Android](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service).
* Lägg till iOS- och Android-versionerna av programmet i den här tjänsten.
* Skapa en leverans för både iOS och Android. [Se den här sidan](../../delivery/using/creating-notifications.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Gå till fliken **[!UICONTROL Subscriptions]** i tjänsten för att visa listan över prenumeranter på tjänsten, dvs. alla personer som har installerat programmet på sin mobiltelefon och gått med på att ta emot meddelanden.

## Installera paketet {#installing-package-ios}

![](assets/do-not-localize/how-to-video.png) [Lär dig hur du installerar mobilappspaketet i video](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=en#sending-messages)

Som hybrid-/värdkund kontaktar du kundtjänstteamet på Adobe för att få tillgång till push-meddelandekanalen i Campaign.

Som lokal kund måste du utföra följande installationssteg:

1. Öppna guiden för paketimport från **[!UICONTROL Tools > Advanced > Package import...]** i Adobe Campaign klientkonsol.

   ![](assets/package_ios.png)

1. Välj **[!UICONTROL Install a standard package]**.

1. Markera **[!UICONTROL Mobile App Channel]** i listan som visas.

   ![](assets/package_ios_2.png)

1. Klicka på **[!UICONTROL Next]** och **[!UICONTROL Start]** för att starta paketinstallationen.

   När paketen har installerats visas **100 %** i förloppsindikatorn och följande meddelande visas i installationsloggarna: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** installationsfönstret.

När det här steget är klart kan du konfigurera dina Android- och iOS-appar.
Se följande avsnitt:

* [Konfigurationssteg för iOS](../../delivery/using/configuring-the-mobile-application.md)

* [Konfigurationssteg för Android](../../delivery/using/configuring-the-mobile-application-android.md)
