---
product: campaign
title: Om webbspårning
feature: Configuration, Instance Settings
description: Om webbspårning
role: User, Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 8%

---

# Om webbspårning{#about-web-tracking}

Utöver standardspårning som visar hur en internetanvändare klickar på en länk i ett e-postmeddelande kan du med Adobe Campaign-plattformen samla in information om hur internetanvändare surfar på din webbplats. Den här datainsamlingen utförs av webbspårningsmodulen.

När en Internetanvändare klickar på en spårad länk i ett e-postmeddelande från en viss leverans, kommer den kontaktade omdirigeringsservern att lagra en sessions-cookie som innehåller sändnings-ID:t (broadlogId) och leveransidentifieraren (deliveryId).

Webbklienten skickar sedan denna cookie till servern varje gång användaren besöker en sida som innehåller en webbspårningstagg. Detta fortsätter under hela sessionen, dvs. tills webbklienten stängs.

Omdirigeringsservern samlar in följande data på det här sättet:

* URL för den visade sidan, via en identifierare som skickas som en parameter,
* Leveransen från vilken webbsidan besöktes via sessionscookie.
* Identifierare för den internetanvändare som klickade via sessionscookie.
* ytterligare information, t.ex. den genererade affärsvolymen.

I följande diagram visas de olika stegen i dialogen mellan klienten och de olika servrarna.

![](assets/d_ncs_integration_webtracking_structure1.png)
