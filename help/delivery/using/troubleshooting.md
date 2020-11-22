---
solution: Campaign Classic
product: campaign
title: Felsökning
description: Felsökning
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 3%

---


# Felsökning{#troubleshooting}

Om din mobila enhet är ansluten till ett trådlöst nätverk och du inte får några meddelanden kontrollerar du att FCM-/APN-portarna inte blockeras av din brandvägg.

**Android**: Den mobila enheten ansluter till FCM-servrarna på portarna 5228 till 5230. Därför måste du konfigurera brandväggen så att den tillåter anslutning till FCM. De portar som ska öppnas är: 5228 (den mest använda), 5229 och 5230.

**iOS**:

Binär koppling: Om du vill skicka meddelanden måste du tillåta inkommande och utgående TCP-trafik på port 2195. Enheter som är anslutna till push-tjänsten måste auktorisera inkommande och utgående TCP-trafik på port 5223.

HTTP/2-anslutning: du måste tillåta kommunikation till och från följande servrar:

* api.push.apple.com: port 443
* api.development.push.apple.com: port 443

>[!NOTE]
>
>Mer information om de två anslutningarna finns i [Konfigurera mobilprogrammet i Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).
