---
product: campaign
title: TechNote - uppdatering av servercertifikat för Apple Push Notification-tjänsten
description: Uppdatering av servercertifikat för Apple Push Notification-tjänst
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 0c97efef21bfd3b8671847c3e1c27bb76cf167e4
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Uppdatering av servercertifikat för Apple Push Notification-tjänst {#apns-certificate-update}

![](../../assets/v7-only.svg)

Den 29 mars 2021 påverkade en infrastrukturuppdatering för Apple Push Notification service (APNs) Adobe Campaign Classic iOS-kanal. En ändring av operativsystemets konfiguration är **obligatorisk** för att undvika avbrott i push-kanalen i iOS.

Läs mer om ändringar av APN:er [på den här sidan](https://developer.apple.com/news/?id=7gx0a2lp).

Som värdkund behövs ingen åtgärd: Adobe har redan införlivat det nya rotcertifikatet i din miljö.

Som lokal/hybridkund måste du uppdatera konfigurationen för att säkerställa en sömlös övergång **före den 29 mars 2021**.

Följ stegen nedan för att införliva det nya certifikatet:

1. Hämta rotcertifikatet **AACertificateServices 5/12/2020** [från den här sidan](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Kontrollera att AAA-certifikatet finns i både ditt operativsystem och JAVA-förvaltare. Om inte, lägg till den.

1. Starta om Adobe Campaign webbtjänst:

   ```
   nlserver restart web
   ```
