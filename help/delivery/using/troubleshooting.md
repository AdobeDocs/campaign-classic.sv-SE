---
title: Felsökning
seo-title: Felsökning
description: Felsökning
seo-description: null
page-status-flag: never-activated
uuid: 02bd48cf-3928-4817-97b0-1e64cc8ad8ef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: b64c9729-cfe2-4d02-8c59-9e53efd34a96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fa2b6890d3c9eaf7b4b6521b2edfb494faa4798c

---


# Felsökning{#troubleshooting}

Om din mobila enhet är ansluten till ett trådlöst nätverk och du inte får några meddelanden kontrollerar du att FCM/APNS-portarna inte blockeras av din brandvägg.

**Android**: Den mobila enheten ansluter till FCM-servrarna på portarna 5228 till 5230. Därför måste du konfigurera brandväggen så att den tillåter anslutning till FCM. De portar som ska öppnas är: 5228 (den mest använda), 5229 och 5230.

**iOS**:

Binär koppling: Om du vill skicka meddelanden måste du tillåta inkommande och utgående TCP-trafik på port 2195. Enheter som är anslutna till push-tjänsten måste auktorisera inkommande och utgående TCP-trafik på port 5223.

HTTP/2-anslutning: du måste tillåta kommunikation till och från följande servrar:

* api.push.apple.com: port 443
* api.development.push.apple.com: port 443

>[!NOTE]
>
>Mer information om de två anslutningarna finns i [Konfigurera mobilprogrammet i Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).
