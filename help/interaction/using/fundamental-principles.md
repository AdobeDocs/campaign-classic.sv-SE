---
solution: Campaign Classic
product: campaign
title: Grundläggande principer
description: Grundläggande principer
audience: interaction
content-type: reference
topic-tags: general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 1%

---


# Grundläggande principer{#fundamental-principles}

## Distribuerar miljöer {#deploying-environments}

Det finns två miljöer för varje målinriktningsdimension som används vid hantering av erbjudanden:

* En designmiljö där den som ansvarar för erbjudandet tar hand om att skapa och kategorisera erbjudanden, redigera dem och starta godkännandeprocessen så att de kan användas. Reglerna för varje kategori, erbjudandeutrymmet som erbjudandena kan presenteras på och de fördefinierade filter som används för att definiera ett erbjudandes behörighet definieras också i den här miljön.

   Kategorier kan också publiceras manuellt i onlinemiljön.

   Processen för att godkänna erbjudanden beskrivs i avsnittet [Godkänna och aktivera ett erbjudande](../../interaction/using/approving-and-activating-an-offer.md).

* En aktiv miljö där man kan hitta godkända erbjudanden från designmiljön, liksom de olika erbjudanden, filter, kategorier och regler som är konfigurerade i designmiljön. Under ett anrop till erbjudandemotorn kommer motorn alltid att använda erbjudanden från den aktiva miljön.

Erbjudandet gäller endast de erbjudanden som valts under godkännandeprocessen. Därför kan ett erbjudande vara direktsänt men oanvändbart på ett erbjudande som också är direktsänt.

![](assets/architecture_interaction1.png)

## Interaktionstyper och kontaktmetoder {#interaction-types-and-contact-methods}

Det finns två möjliga typer av interaktioner: inkommande interaktioner (initierad av en kontakt) och utgående interaktioner (initierad av den som skapat erbjudandet).

Dessa två typer av interaktioner kan utföras antingen i enhetligt läge (erbjudandet beräknas för en enskild kontakt) eller i batchläge (erbjudandet beräknas för en uppsättning kontakter). I allmänhet utförs inkommande interaktioner i enställigt läge och utgående interaktioner utförs i batchläge. Det kan dock finnas vissa undantag, t.ex. för transaktionsmeddelanden, där den utgående interaktionen utförs i enhetligt läge (se [detta avsnitt](../../message-center/using/about-transactional-messaging.md)).

Så snart ett erbjudande kan eller måste presenteras (i enlighet med de konfigurationer som gjorts) spelar den erbjudandemotorn rollen som mellanhand: beräknas automatiskt bästa möjliga erbjudande för en kontakt bland de tillgängliga genom att man kombinerar mottagna data om kontakten och de olika regler som kan tillämpas enligt applikationen.

![](assets/architecture_interaction2.png)

