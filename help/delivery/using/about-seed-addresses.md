---
title: Om fröadresser
seo-title: Om fröadresser
description: Om fröadresser
seo-description: null
page-status-flag: never-activated
uuid: 80ab5abc-3ae0-484d-88c0-be039aac360d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: b49acfd0-b601-4694-88e3-cc0a169cb866
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 9%

---


# Om fröadresser{#about-seed-addresses}

Fröadresser används för mottagare i målgruppen som inte matchar dess definierade villkor. På så sätt kan mottagare som ligger utanför leveransomfånget ta emot leveransen, precis som andra målmottagare gör.

En av de främsta anledningarna till att använda dem är **ditt skydd** av e-postlistan. Om du infogar dirigerade adresser i din e-postlista kan du lägga märke till om de används av en tredje part, eftersom de dirigerade adresserna som finns där kommer att få leveranserna som skickas till din e-postlista.

Med dirigerade adresser kan du dessutom **förhandsgranska och testa leveranspersonalisering och återgivning** innan de skickas, genom att skicka korrektur (se [Använda dirigerade adresser som bevis](../../delivery/using/steps-defining-the-target-population.md#using-seed-addresses-as-proof).

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i video](../../delivery/using/steps-defining-the-target-population.md#seeds-and-proofs-video)

Funktionen för dirigerade adresser har följande fördelar:

* Slumpmässig ersättning av fält med data från mottagarprofiler: Detta gör att du bara kan ange e-postadressen, till exempel i avsnittet för dirigerad adress, och låta Campaign automatiskt fylla i de andra fälten från profilen (se [Användningsfall: konfigurera fältersättning](../../delivery/using/use-case--configuring-the-field-substitution.md)).
* När du använder ett arbetsflöde med datahanteringsfunktioner kan ytterligare data som bearbetas i leveranser anges på dirigeringsadressnivå för att framtvinga värden: den här sidan gör att slumpmässiga värden byts ut.
* dirigeringsadresser exkluderas automatiskt från rapporter om följande leveransstatistik: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

Seed-adresser läggs till i målet för leveranser genom att importeras eller skapas direkt i leveransen eller kampanjen.

>[!NOTE]
>
>Seed-adresserna tillhör inte mottagartabellen, utan skapas i en separat tabell. Om du utökar mottagartabellen med nya data måste du utöka både dirigerade adresstabellen och samma data. I annat fall kommer de utökade fälten inte att beaktas för dirigerade adresser.
>
>Ett exempel på hur du kan utöka tabellen med dirigerade adresser visas i det här avsnittet: [Användningsfall: välja startadresser enligt villkor](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)

Vid direktutskick läggs startadresser till under extraheringen och blandas i utdatadokumentet.

>[!IMPORTANT]
>
>För direktreklam måste extraheringsfilformatet uppfylla följande begränsningar:
>
>* Det får inte använda alternativet **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* Om elementsamlingar extraheras får dessa fält ett tomt värde för startadresserna, såvida inte **[!UICONTROL Single row (expert user)]** alternativet är markerat. Mer information om detta finns i [det här avsnittet](../../platform/using/exporting-data.md#step-7---data-formatting).

>


