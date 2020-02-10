---
title: Om webbspårning
seo-title: Om webbspårning
description: Om webbspårning
seo-description: null
page-status-flag: never-activated
uuid: 59d18ffb-c26e-4571-8364-5e85ec587349
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 38ba9be9-dabc-41d4-878c-d772955301fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Om webbspårning{#about-web-tracking}

Utöver standardspårning som visar hur en internetanvändare klickar på en länk i ett e-postmeddelande kan du med Adobe Campaign-plattformen samla in information om hur internetanvändare surfar på webbplatsen. Den här datainsamlingen utförs av webbspårningsmodulen.

När en internetanvändare klickar på en spårad länk i ett e-postmeddelande från en viss leverans, kommer den kontaktade omdirigeringsservern att lagra en sessions-cookie som innehåller sändnings-ID:t (broadlogId) och leveransidentifieraren (deliveryId).

Webbklienten skickar sedan denna cookie till servern varje gång användaren besöker en sida som innehåller en webbspårningstagg. Detta fortsätter under hela sessionen, dvs. tills webbklienten stängs.

Omdirigeringsservern samlar in följande data på det här sättet:

* URL för den visade sidan, via en identifierare som skickas som en parameter,
* Leveransen från vilken webbsidan besöktes via sessionscookie.
* Identifierare för den internetanvändare som klickade via sessionscookie.
* ytterligare information, t.ex. den genererade affärsvolymen.

I följande diagram visas de olika stegen i dialogen mellan klienten och de olika servrarna.

![](assets/d_ncs_integration_webtracking_structure1.png)

