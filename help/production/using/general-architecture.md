---
product: campaign
title: Allmän arkitektur
description: Allmän arkitektur
feature: Monitoring, Architecture
audience: production
content-type: reference
topic-tags: introduction
exl-id: 3bfb5448-6996-4080-bf9a-434f1207637e
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 3%

---

# Allmän arkitektur{#general-architecture}



## Minimiarkitektur {#minimum-architecture}

Adobe Campaign har minst följande konfigurationer:

* Adobe Campaign programserver,
* databasen.

  ![](assets/formation_exploitation.png)

Bilden visar att den enda trafik som berörs av en minimiarkitektur är:

1. HTTP-protokolltrafik till Adobe Campaign-servern via Internet,
1. SMTP-protokolltrafik från och till Adobe Campaign-servern via Internet.

## Distribuerad arkitektur {#distributed-architecture}

Adobe Campaign består av flera moduler som kan delas upp på flera datorer. Det här operativläget har flera fördelar:

* lastbalansering,
* upprättande av modulredundans,
* uppbyggnad av en arkitektur uppdelad på flera tjänsteleverantörer (segmentering av de tjänster som tillhandahålls).

![](assets/architecturerepartie.png)

Distributionen av moduler på flera datorer ger stor flexibilitet vid användning och förbättrad anpassningsbarhet.

>[!NOTE]
>
>Mer information om de olika arkitekturerna finns i [det här avsnittet](../../installation/using/general-architecture.md).

## Lista över öppna portar {#list-of-open-ports}

| Portnummer | Berörd Adobe Campaign-modul eller tillämpning | Konfigurerbar |
|---|---|---|
| 443/tcp eller 80/tcp | Webbservrar (Apache/IIS) | JA |
| 6666/udp (lokal) | Adobe Campaign: Syslogd | JA |
| 8005/tcp (lokal) | Adobe Campaign: webbmodul | JA |
| 8080/tcp | Adobe Campaign: webbmodul (tomcat) | JA |
| 7777 | Statistikserver (startserver) | JA |
