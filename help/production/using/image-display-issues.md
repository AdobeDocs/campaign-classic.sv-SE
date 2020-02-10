---
title: Bildvisningsproblem
seo-title: Bildvisningsproblem
description: Bildvisningsproblem
seo-description: null
page-status-flag: never-activated
uuid: 8fc51459-ee46-4c05-8011-f0651e6b451b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: dfccfe8c-b826-4648-9a0b-23d7e6a4808a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Bildvisningsproblem{#image-display-issues}

Om du får problem med att visa bilder i ett skickat meddelande kan orsaken vara länkad till en felaktig plats:

* platserna matchar kanske inte, eller så har bilderna inte flyttats korrekt till den duplicerade spårningsservern: kontrollera konfigurationen.
* Bilderna får inte finnas i resursmappen för marknadsföring: överför bilderna till din resursmapp för att lösa problemet.
* om du arbetar i en arkitektur med flera källor: kontrollera bilder överförs utan fel när korrektur skickas (information visas i analysloggarna).

Så här felsöker du:

1. Skicka ett korrektur som visar bilderna.
1. Verifiera att resurskonfigurationen i instansinställningarna är korrekt.
1. Kontrollera mappen för offentliga resurser eller, om den inte finns i mappen för offentliga resurser, den mapp som refereras i leveransen.

