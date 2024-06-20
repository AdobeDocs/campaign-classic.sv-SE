---
product: campaign
title: Felsökning
description: Felsökning
feature: Audiences, People Core Service Integration, Troubleshooting
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
hide: true
hidefromtoc: true
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 3%

---

# Felsökning{#troubleshooting}



Om fel uppstår bör du kontrollera att följande element är korrekt konfigurerade:

* **Externa konton**

  I **[!UICONTROL Administration > Platform > External accounts]** kontrollerar du att följande externa SFTP-konton är korrekt konfigurerade. Dessa SFTP-servrar bör ha konfigurerats i Adobe Experience Cloud av din konsult.

   * **[!UICONTROL importSharedAudience]** : SFTP-konto för att importera målgrupper.
   * **[!UICONTROL exportSharedAudience]** : SFTP-konto för export av målgrupper.

* **AMC-datakälla**

  I **[!UICONTROL Administration > Platform > AMC Data sources]** kontrollerar du att AMC-datakällan är korrekt inställd.

Det kan inträffa att vissa data saknas när en målgrupp delas via Experience Cloud eller när en målgrupp importeras. Det är bara poster som ID:t (&#39;besökar-ID&#39; eller &#39;Deklarerat ID&#39;) kunde förenas med profildimensionen som överförs. ID:n från segment som inte känns igen av Adobe Campaign importeras inte.
