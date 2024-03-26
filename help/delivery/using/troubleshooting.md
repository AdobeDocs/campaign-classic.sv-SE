---
product: campaign
title: Push-felsökning
description: Push-felsökning
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Push, Troubleshooting
role: User
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 6%

---

# Felsökning{#troubleshooting}

Om din mobila enhet är ansluten till ett trådlöst nätverk och du inte får några meddelanden kontrollerar du att FCM-/APN-portarna inte blockeras av din brandvägg.

**Android**: Den mobila enheten ansluter till FCM-servrarna på portarna 5228 till 5230. Därför måste du konfigurera brandväggen så att den tillåter anslutning till FCM. Portarna som ska öppnas är: 5228 (den vanligaste), 5229 och 5230.

**iOS**:

HTTP/2-anslutning: Du måste tillåta kommunikation till och från följande servrar:

* api.push.apple.com: port 443
* api.development.push.apple.com: port 443

>[!NOTE]
>
>Mer information om de två kopplingarna finns i [Konfigurera mobilprogrammet i Adobe Campaign](configuring-the-mobile-application.md).
