---
product: campaign
title: Skjut felsökning
description: Skjut felsökning
feature: Push
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: 8d635722b8961b3edac9cc98f00f17b86f4ee523
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 2%

---

# Felsökning{#troubleshooting}

![](../../assets/v7-only.svg)

Om din mobila enhet är ansluten till ett trådlöst nätverk och du inte får några meddelanden kontrollerar du att FCM-/APN-portarna inte blockeras av din brandvägg.

**Android**: Den mobila enheten ansluter till FCM-servrarna på portarna 5228 till 5230. Därför måste du konfigurera brandväggen så att den tillåter anslutning till FCM. De portar som ska öppnas är: 5228 (den mest använda), 5229 och 5230.

**iOS**:

HTTP/2-anslutning: du måste tillåta kommunikation till och från följande servrar:

* api.push.apple.com: port 443
* api.development.push.apple.com: port 443

>[!NOTE]
>
>Mer information om de två kopplingarna finns i [Konfigurera mobilprogrammet i Adobe Campaign](configuring-the-mobile-application.md).
