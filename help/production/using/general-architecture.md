---
title: Allmän arkitektur
seo-title: Allmän arkitektur
description: Allmän arkitektur
seo-description: null
page-status-flag: never-activated
uuid: a565a10c-cbef-455a-aa1d-9be9cd207c7a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: introduction
discoiquuid: f4879774-afe5-4556-ab60-9297cabbca2c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 6%

---


# Allmän arkitektur{#general-architecture}

## Minimiarkitektur {#minimum-architecture}

Adobe Campaign har minst följande konfigurationer:

* adobe campaign programserver,
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

Distributionen av moduler på flera datorer ger stor flexibilitet och förbättrad anpassningsbarhet.

>[!NOTE]
>
>For more on the various architectures, refer to [this section](../../installation/using/general-architecture.md).

## Lista över öppna portar {#list-of-open-ports}

| Portnummer | Berörd Adobe Campaign-modul eller tillämpning | Konfigurerbar |
|---|---|---|
| 443/tcp eller 80/tcp | Webbservrar (Apache/IIS) | JA |
| 6666/udp (lokal) | Adobe Campaign: Syslogd | JA |
| 8005/tcp (lokal) | Adobe Campaign: webbmodul | JA |
| 8080/tcp | Adobe Campaign: webbmodul (tomcat) | JA |
| 7777 | Statistikserver (startserver) | JA |

