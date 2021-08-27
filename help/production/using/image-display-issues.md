---
product: campaign
title: Bildvisningsproblem
description: Bildvisningsproblem
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---

# Bildvisningsproblem{#image-display-issues}

![](../../assets/v7-only.svg)

Om du får problem med att visa bilder i ett skickat meddelande kan orsaken vara länkad till en felaktig plats:

* Platserna matchar kanske inte, eller så har bilderna inte överförts korrekt till den duplicerade spårningsservern: kontrollera konfigurationen.
* Bilderna får inte finnas i resursmappen för marknadsföring: överför bilderna till din resursmapp för att lösa problemet.
* Om du arbetar i en medelkällkodsarkitektur: kontrollera bilder överförs utan fel när korrektur skickas (information visas i analysloggarna).

Så här felsöker du:

1. Skicka ett korrektur som visar bilderna.
1. Verifiera att resurskonfigurationen i instansinställningarna är korrekt.
1. Kontrollera mappen för offentliga resurser eller, om den inte finns i mappen för offentliga resurser, den mapp som refereras i leveransen.
