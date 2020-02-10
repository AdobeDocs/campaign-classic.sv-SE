---
title: Viktiga anteckningar
seo-title: Viktiga anteckningar
description: Viktiga anteckningar
seo-description: null
page-status-flag: never-activated
uuid: 4325b16b-eaa8-4b14-922d-7f24e5e548f0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: d13d2f12-92b9-4ff5-b70d-a7ecf2ced71a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Viktiga anteckningar{#important-notes}

* Transactional Messaging-instanserna ska inte användas för att behålla/exportera/överföra filer eller data. Det används bara för händelsedata och relaterad information. De bör inte betraktas som ett fillagringssystem.
* Eftersom det inte finns någon direkt åtkomst till Transactional Messaging-instanser eller -servrar utanför Adobe finns det inget standardsätt att skicka sådana filer till dessa servrar (ingen FTP-åtkomst).
* Det är enligt avtalet inte korrekt att använda diskutrymmet på Transactional Messaging-instansdisken för att lagra filer av någon typ, inte ens för bilagor.
* Du måste använda ett annat onlinesystem för att ha dessa filer. Du behöver FTP-åtkomst till det här systemet och kan skriva och ta bort filer.

