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
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

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
>Mer information om de två kontakterna finns i [Kopplingar](../../delivery/using/setting-up-mobile-app-channel.md#connectors).
