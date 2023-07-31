---
product: campaign
title: Bildvisningsproblem
description: Bildvisningsproblem
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 7%

---

# Bildvisningsproblem{#image-display-issues}



Om du får problem med att visa bilder i ett skickat meddelande kan orsaken vara länkad till en felaktig plats:

* Platserna matchar kanske inte, eller så har bilderna inte överförts korrekt till en dubblettspårningsserver: kontrollera konfigurationen.
* Bilder kanske inte finns i resursmappen för marknadsföring: överför bilderna till resursmappen för att lösa problemet.
* Om du arbetar i en medelkällkodsarkitektur: kontrollera att bilder överförs utan fel när korrektur skickas (information visas i analysloggarna).

Felsöka:

1. Skicka ett bevis som visar bilderna.
1. Verifiera att resurskonfigurationen i instansinställningarna är korrekt.
1. Kontrollera mappen för offentliga resurser eller, om den inte finns i mappen för offentliga resurser, den mapp som refereras i leveransen.
