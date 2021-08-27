---
product: campaign
title: Technote
description: Technote
hide: false
hidefromtoc: true
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Uppdatering av servercertifikat för Apple Push Notification-tjänst {#apns-certificate-update}

![](../../assets/v7-only.svg)

Den 29 mars 2021 kommer en infrastrukturuppdatering för Apple Push Notification service (APNs) att påverka Adobe Campaign Classic iOS-kanal. En ändring av operativsystemets konfiguration är **obligatorisk** för att undvika avbrott i push-kanalen i iOS.

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
