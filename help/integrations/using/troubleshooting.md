---
product: campaign
title: Felsökning
description: Felsökning
feature: Audiences, People Core Service Integration, Troubleshooting
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 4%

---

# Felsökning{#troubleshooting}



Om fel uppstår bör du kontrollera att följande element är korrekt konfigurerade:

* **Externa konton**

  I **[!UICONTROL Administration > Platform > External accounts]** kontrollerar du att följande externa SFTP-konton är korrekt konfigurerade. Dessa SFTP-servrar bör ha konfigurerats i Adobe Experience Cloud av din konsult.

   * **[!UICONTROL importSharedAudience]** : SFTP-konto för att importera målgrupper.
   * **[!UICONTROL exportSharedAudience]** : SFTP-konto för export av målgrupper.

* **AMC-datakälla**

  I **[!UICONTROL Administration > Platform > AMC Data sources]** kontrollerar du att AMC-datakällan är korrekt inställd.

Det kan inträffa att vissa data saknas när en målgrupp delas via personbastjänsten eller när en målgrupp importeras. Det är bara poster som ID:t (&#39;besökar-ID&#39; eller &#39;Deklarerat ID&#39;) kunde förenas med profildimensionen som överförs. ID:n från People core service segments som inte känns igen av Adobe Campaign importeras inte.
