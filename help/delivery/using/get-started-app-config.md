---
title: 'Konfigurera den mobila applikationen i Adobe Campaign '
description: Lär dig hur du börjar med konfigurationen för mobilprogrammet
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
translation-type: tm+mt
source-git-commit: fd75f7f75e8e77d7228233ea311dd922d100417c
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 4%

---


# Kom igång med appkonfigurationen

I det här avsnittet hittar du ett konfigurationsexempel baserat på ett företag som säljer semesterpaket online. Hans mobilapplikation (Neotrips) finns i två versioner: Neotrips för Android och Neotrips för iOS.

Om du vill skicka push-meddelanden i Adobe Campaign måste du:

* Skapa en **[!UICONTROL Mobile application]** typinformationstjänst för mobilappen Neotrips. Se [det här avsnittet för iOS](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service). och [det här avsnittet för Android](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service).
* Lägg till iOS- och Android-versionerna av programmet i den här tjänsten.
* Skapa en leverans för både iOS och Android. [Se den här sidan](../../delivery/using/creating-notifications.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>Gå till fliken **[!UICONTROL Subscriptions]** för tjänsten för att visa en lista över prenumeranter på tjänsten, dvs. alla personer som har installerat programmet på sin mobiltelefon och gått med på att ta emot meddelanden.

## Installera paketet {#installing-package-ios}

Som hybrid-/värdkund kontaktar du kundtjänstteamet på Adobe för att få tillgång till push-meddelandekanalen i Campaign.

Som lokal kund måste du utföra följande installationssteg:

1. Öppna guiden för paketimport från **[!UICONTROL Tools > Advanced > Package import...]** Adobe Campaign klientkonsol.

   ![](assets/package_ios.png)

1. Välj **[!UICONTROL Install a standard package]**.

1. Markera i listan som visas **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. Klicka **[!UICONTROL Next]** och sedan **[!UICONTROL Start]** för att starta paketinstallationen.

   När paketen har installerats visar förloppsindikatorn **100 %** och följande meddelande visas i installationsloggarna: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** installationsfönstret.

När det här steget är klart kan du konfigurera dina Android- och iOS-appar.
Se följande avsnitt:

* [Konfigurationssteg för iOS](../../delivery/using/configuring-the-mobile-application.md)

* [Konfigurationssteg för Android](../../delivery/using/configuring-the-mobile-application-android.md)
