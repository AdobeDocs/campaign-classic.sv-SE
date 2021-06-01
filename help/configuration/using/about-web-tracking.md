---
product: campaign
title: Om webbspårning
description: Om webbspårning
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---

# Om webbspårning{#about-web-tracking}

Utöver standardspårning som visar hur en internetanvändare klickar på en länk i ett e-postmeddelande kan du med Adobe Campaign-plattformen samla in information om hur internetanvändare surfar på din webbplats. Den här datainsamlingen utförs av webbspårningsmodulen.

När en internetanvändare klickar på en spårad länk i ett e-postmeddelande från en viss leverans, kommer den kontaktade omdirigeringsservern att lagra en sessions-cookie som innehåller sändnings-ID:t (broadlogId) och leveransidentifieraren (deliveryId).

Webbklienten skickar sedan denna cookie till servern varje gång användaren besöker en sida som innehåller en webbspårningstagg. Detta fortsätter under hela sessionen, dvs. tills webbklienten stängs.

Omdirigeringsservern samlar in följande data på det här sättet:

* URL för den visade sidan, via en identifierare som skickas som en parameter,
* Leveransen från vilken webbsidan besöktes via sessionscookie.
* Identifierare för den internetanvändare som klickade via sessionscookie.
* ytterligare information, t.ex. den genererade affärsvolymen.

I följande diagram visas de olika stegen i dialogen mellan klienten och de olika servrarna.

![](assets/d_ncs_integration_webtracking_structure1.png)
