---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: false
hidefromtoc: true
translation-type: tm+mt
source-git-commit: a21f970b6b81105517a11bcbd7f334173acc76e4
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# Certifikatuppdatering för Apple Push Notification-tjänstens servercertifikat {#apns-certificate-update}

Den 29 mars 2021 kommer en infrastrukturuppdatering för Apple Push Notification service (APNs) att påverka Adobe Campaign Classic iOS-kanal. En ändring av operativsystemets konfiguration är **obligatorisk** för att undvika avbrott i push-kanalen i iOS.

Läs mer om ändringar av APN:er [på den här sidan](https://developer.apple.com/news/?id=7gx0a2lp).

Som värdkund behövs ingen åtgärd: Adobe har redan införlivat det nya rotcertifikatet i din miljö.

Som lokal/hybridkund måste du uppdatera konfigurationen för att säkerställa en sömlös övergång **före den 29 mars 2021**.

Följ stegen nedan för att införliva det nya certifikatet:

1. Hämta rotcertifikatet **AACertificateServices 5/12/2020** [från den här sidan](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Lägg till den i OS Trust Store.

1. Starta om Adobe Campaign webbtjänst:

   ```
   nlserver restart web
   ```
