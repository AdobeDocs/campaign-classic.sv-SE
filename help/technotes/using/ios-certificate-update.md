---
product: campaign
title: Technote - Apple Push Notification service server certificate update
description: Uppdatering av servercertifikat för tjänsten Apple Push Notification
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 0143e0d6ebcdbd96d183ddd0c7f07beb149a9670
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Uppdatering av servercertifikat för tjänsten Apple Push Notification {#apns-certificate-update}



Den 17 oktober 2024 påverkade en infrastrukturuppdatering för Apple Push Notification service (APNs) Adobe Campaign Classic iOS-kanalen. En ändring av operativsystemets konfiguration är **obligatorisk** för att undvika avbrott i iOS push-kanaler.

Läs mer om ändringar av APN:er [på den här sidan](https://developer.apple.com/news/?id=09za8wzy).

Som värdkund behövs ingen åtgärd: Adobe har redan införlivat det nya rotcertifikatet i din miljö.

Som lokal/hybridkund måste du uppdatera konfigurationen för att säkerställa en sömlös övergång **före den 24 februari 2025**.

Följ stegen nedan för att införliva det nya certifikatet:

1. Hämta **SHA-2 Root: USERTrust RSA Certification Authority-certifikatet** root certificate [ från den här sidan](https://www.sectigo.com/knowledge-base/detail/Sectigo-Intermediate-Certificates/kA01N000000rfBO).

1. Kontrollera att AAA-certifikatet finns i både ditt operativsystem och JAVA-förtroenden. Om inte, lägg till den.

1. Starta om Adobe Campaign webbtjänst:

   ```
   nlserver restart web
   ```
