---
solution: Campaign Classic
product: campaign
title: Om fröadresser
description: Om fröadresser
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 9%

---


# Om fröadresser{#about-seed-addresses}

Fröadresser används för mottagare i målgruppen som inte matchar dess definierade villkor. På så sätt kan mottagare som ligger utanför leveransomfånget ta emot leveransen, precis som andra målmottagare gör.

En av de viktigaste skälen att använda dem är **ditt skydd av e-postlistan**. Om du infogar dirigerade adresser i din e-postlista kan du lägga märke till om de används av en tredje part, eftersom de dirigerade adresserna som finns där kommer att få leveranserna som skickas till din e-postlista.

Med dirigerade adresser kan du dessutom **förhandsgranska och testa leveranspersonalisering och återgivning** innan de skickas, genom att skicka korrektur (se [Använda dirigerade adresser som bevis](../../delivery/using/steps-defining-the-target-population.md#using-seed-addresses-as-proof).

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](../../delivery/using/steps-defining-the-target-population.md#seeds-and-proofs-video)

Funktionen för dirigerade adresser har följande fördelar:

* Slumpmässig ersättning av fält med data från mottagarprofiler: Detta gör att du bara kan ange e-postadressen, till exempel i avsnittet för startadressen, och låta Campaign automatiskt fylla i de andra fälten från profilen (se [Användningsfall: konfigurerar fältersättningen](../../delivery/using/use-case--configuring-the-field-substitution.md)).
* När du använder ett arbetsflöde med datahanteringsfunktioner kan ytterligare data som bearbetas i leveranser anges på dirigeringsadressnivå för att framtvinga värden: den här sidan gör att slumpmässiga värden byts ut.
* dirigeringsadresser exkluderas automatiskt från rapporter om följande leveransstatistik: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

Seed-adresser läggs till i målet för leveranser genom att importeras eller skapas direkt i leveransen eller kampanjen.

>[!NOTE]
>
>Seed-adresserna tillhör inte mottagartabellen, utan skapas i en separat tabell. Om du utökar mottagartabellen med nya data måste du utöka både dirigerade adresstabellen och samma data. I annat fall kommer de utökade fälten inte att beaktas för dirigerade adresser.
>
>Ett exempel på hur du kan utöka tabellen med dirigerade adresser visas i det här avsnittet: [Användningsfall: välja startadresser på villkor](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md)

Vid direktutskick läggs startadresser till under extraheringen och blandas i utdatadokumentet.

>[!IMPORTANT]
>
>För direktreklam måste extraheringsfilformatet uppfylla följande begränsningar:
>
>* Det får inte använda alternativet **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* Om elementsamlingar extraheras har dessa fält ett tomt värde för startadresserna, såvida inte alternativet **[!UICONTROL Single row (expert user)]** är markerat. Mer information om detta finns i [det här avsnittet](../../platform/using/executing-export-jobs.md#step-7---data-formatting).
>


