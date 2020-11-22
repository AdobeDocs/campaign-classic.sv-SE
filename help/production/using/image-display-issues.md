---
solution: Campaign Classic
product: campaign
title: Bildvisningsproblem
description: Bildvisningsproblem
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 6%

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

