---
product: campaign
title: Felsökning
description: Felsökning
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 313eae5f-40db-4b1a-b013-f4adf8781763
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 4%

---

# Felsökning{#troubleshooting}

Om din mobila enhet är ansluten till ett trådlöst nätverk och du inte får några meddelanden kontrollerar du att FCM-/APN-portarna inte blockeras av din brandvägg.

**Android**: Den mobila enheten ansluter till FCM-servrarna på portarna 5228 till 5230. Därför måste du konfigurera brandväggen så att den tillåter anslutning till FCM. De portar som ska öppnas är: 5228 (den mest använda), 5229 och 5230.

**iOS**:

HTTP/2-anslutning: du måste tillåta kommunikation till och från följande servrar:

* api.push.apple.com: port 443
* api.development.push.apple.com: port 443

>[!NOTE]
>
>Mer information om de två anslutningarna finns i [Konfigurera mobilprogrammet i Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).
