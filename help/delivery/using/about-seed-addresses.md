---
product: campaign
title: Om dirigerade adresser
description: Kom igång med dirigerade adresser
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Seed Address
role: User
exl-id: 1f55eda8-c393-4f86-9118-01bcd981c6df
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 8%

---

# Om dirigerade adresser{#about-seed-addresses}

Fröadresser används för mottagare i målgruppen som inte matchar dess definierade villkor. På så sätt kan mottagare som ligger utanför leveransomfånget ta emot leveransen, precis som andra målmottagare gör.

En av de viktigaste skälen att använda dem är **skydd av din e-postlista**. Genom att infoga dirigerade adresser i din e-postlista kan du lägga märke till om de används av en tredje part, eftersom de dirigerade adresserna som finns där kommer att få leveranserna som skickas till din e-postlista.

Dessutom kan du använda fröadresser **förhandsgranska och testa leveranspersonalisering och rendering** innan de skickas, genom att skicka korrektur (se [Använd dirigerade adresser som bevis](steps-defining-the-target-population.md#using-seed-addresses-as-proof)).

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](steps-defining-the-target-population.md#seeds-and-proofs-video)

Funktionen för dirigerade adresser har följande fördelar:

* Slumpmässig ersättning av fält med data från mottagarprofiler: Detta gör att du bara kan ange e-postadressen, till exempel i avsnittet dirigerad adress, och låta Campaign automatiskt fylla i de andra fälten från profilen (se [Användningsfall: konfigurera fältersättning](use-case-configuring-the-field-substitution.md)).
* När du använder ett arbetsflöde med datahanteringsfunktioner kan ytterligare data som bearbetas i leveranser anges på dirigeringsadressnivå för att framtvinga värden: detta innebär att slumpmässiga värden ersätts.
* dirigeringsadresser exkluderas automatiskt från rapporter om följande leveransstatistik: **[!UICONTROL Clicks]**, **[!UICONTROL Opens]**, **[!UICONTROL Unsubscriptions]**.

Seed-adresser läggs till i målet för leveranser genom att importeras eller skapas direkt i leveransen eller kampanjen.

>[!NOTE]
>
>Seed-adresserna tillhör inte mottagartabellen, de skapas i en separat tabell. Om du utökar mottagartabellen med nya data måste du utöka både dirigerade adresstabellen och samma data. I annat fall kommer de utökade fälten inte att beaktas för dirigerade adresser.
>
>Ett exempel på hur du kan utöka tabellen med dirigerade adresser visas i det här avsnittet: [Använd skiftläge: välj startadresser på villkor](use-case-selecting-seed-addresses-on-criteria.md).

Vid direktutskick läggs startadresser till under extraheringen och blandas i utdatadokumentet.

>[!IMPORTANT]
>
>För direktreklam måste extraheringsfilformatet uppfylla följande begränsningar:
>
>* Det får inte använda alternativet **[!UICONTROL Handle groupings (GROUP BY+HAVING)]**.
>* Om elementsamlingar extraheras får dessa fält ett tomt värde för startadresserna, såvida inte **[!UICONTROL Single row (expert user)]** är markerat. Mer information om detta finns i [det här avsnittet](../../platform/using/executing-export-jobs.md#step-7---data-formatting).
>
