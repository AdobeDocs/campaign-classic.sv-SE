---
product: campaign
title: Technote - Apple Push Notification service server certificate update
description: Uppdatering av servercertifikat för tjänsten Apple Push Notification
feature: Technote, Push
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 4%

---

# Uppdatering av servercertifikat för tjänsten Apple Push Notification {#apns-certificate-update}



Den 29 mars 2021 påverkade en infrastrukturuppdatering för Apple Push Notification service (APNs) Adobe Campaign Classic iOS-kanal. En ändring av operativsystemets konfiguration är **obligatoriskt** för att undvika avbrott i iOS-kanaler.

Läs mer om ändringar i APN:er [på den här sidan](https://developer.apple.com/news/?id=7gx0a2lp).

Som värdkund behövs ingen åtgärd: Adobe har redan införlivat det nya rotcertifikatet i din miljö.

Som lokal/hybridkund måste du uppdatera din konfiguration för att säkerställa en smidig övergång **före den 29 mars 2021**.

Följ stegen nedan för att införliva det nya certifikatet:

1. Ladda ned **AAACertificateServices 5/12/2020** rotcertifikat [från den här sidan](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. Kontrollera att AAA-certifikatet finns i både ditt operativsystem och JAVA-förtroenden. Om inte, lägg till den.

1. Starta om Adobe Campaign webbtjänst:

   ```
   nlserver restart web
   ```
