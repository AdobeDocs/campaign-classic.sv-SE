---
solution: Campaign Classic
product: campaign
title: Om det här användningsexemplet
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# Om det här användningsfallet {#about-use-case}

I det här fallet ska vi jämföra två e-postleveranser via ett arbetsflöde för målinriktning. Meddelandet och texten är identiska i båda leveranserna: bara layouten ändras.

Målgruppen är uppdelad i tre delar: två testgrupper och den återstående populationen. En annan version av leveransen skickas till varje testgrupp.

Efter leveransen konfigureras en 5-dagars vänteperiod innan resultaten av de bästa öppningsfrekvenserna samlas in. Innehållet i leveransen med det högsta poängtalet återskapas sedan av ett skript och skickas till populationen som inte användes som testgrupp.

Observera att de kriterier som avgör vilken leverans som är bäst kan ändras efter dina behov. Det kan vara öppningsfrekvensen, klickfrekvensen, prenumerationstakten, reaktiviteten osv.

Testet som beskrivs i det här fallet avser endast två leveranser, men du kan testa så många versioner som behövs. Lägg bara till aktiviteter i arbetsflödet.

De viktigaste stegen för att utföra den här åtgärden är:

* [Steg 1: Skapa ett målarbetsflöde](#step-1--creating-a-targeting-workflow)
* [Steg 2: Konfigurera populationsexempel](#step-2--configuring-population-samples)
* [Steg 3: Skapa två leveransmallar](#step-3--creating-two-delivery-templates)
* [Steg 4: Konfigurera leveranser i arbetsflödet](#step-4--configuring-the-deliveries-in-the-workflow)
* [Steg 5: Skapa skriptet](#step-5--creating-the-script)
* [Steg 7: Starta arbetsflödet](#step-7--starting-the-workflow)
* [Steg 8: Analysera resultatet](#step-8--analyzing-the-result).

**Relaterade ämnen:**

* [Kom igång med A/B-tester](../../delivery/using/get-started-a-b-testing.md)
* [Konfigurera A/B-testning](../../delivery/using/configuring-a-b-testing.md)
