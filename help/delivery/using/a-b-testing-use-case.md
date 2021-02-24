---
solution: Campaign Classic
product: campaign
title: Om det här användningsexemplet
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---


# Om det här användningsfallet {#about-use-case}

I det här fallet ska vi jämföra två e-postleveranser via ett arbetsflöde för målinriktning. Meddelandet och texten är identiska i båda leveranserna: bara layouten ändras.

Målgruppen är uppdelad i tre delar: två testgrupper och den återstående populationen. En annan version av leveransen skickas till varje testgrupp.

Efter leveransen konfigureras en 5-dagars vänteperiod innan resultaten av de bästa öppningsfrekvenserna samlas in. Innehållet i leveransen med det högsta poängtalet återskapas sedan av ett skript och skickas till populationen som inte användes som testgrupp.

Observera att de kriterier som avgör vilken leverans som är bäst kan ändras efter dina behov. Det kan vara öppningsfrekvensen, klickfrekvensen, prenumerationstakten, reaktiviteten osv.

Testet som beskrivs i det här fallet avser endast två leveranser, men du kan testa så många versioner som behövs. Lägg bara till aktiviteter i arbetsflödet.

De viktigaste stegen för att utföra den här åtgärden är:

* [Steg 1: Skapa ett målarbetsflöde](../../delivery/using/a-b-testing-uc-targeting-workflow.md)
* [Steg 2: Konfigurera populationsexempel](../../delivery/using/a-b-testing-uc-population-samples.md)
* [Steg 3: Skapa två leveransmallar](../../delivery/using/a-b-testing-uc-delivery-templates.md)
* [Steg 4: Konfigurera leveranser i arbetsflödet](../../delivery/using/a-b-testing-uc-configuring-deliveries.md)
* [Steg 5: Skapa skriptet](../../delivery/using/a-b-testing-uc-script.md)
* [Steg 6: Definiera den slutliga leveransen](../../delivery/using/a-b-testing-uc-final-delivery.md)
* [Steg 7: Starta arbetsflödet](../../delivery/using/a-b-testing-uc-start-workflow.md)
* [Steg 8: Analysera resultatet](../../delivery/using/a-b-testing-uc-analyzing.md)

**Relaterade ämnen:**

* [Kom igång med A/B-tester](../../delivery/using/get-started-a-b-testing.md)
* [Konfigurera A/B-testning](../../delivery/using/configuring-a-b-testing.md)
