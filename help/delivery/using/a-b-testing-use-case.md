---
product: campaign
title: Användningsexempel för AB-tester
description: Lär dig hur du utför A/B-testning via ett dedikerat användningsfall
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: A/B Testing
role: User
exl-id: 4eb139a0-5342-4084-9f6d-d736e05bf1c6
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 4%

---

# AB-testning: A/B Testing this use case {#ab-testing-use-case}

I det här fallet ska vi jämföra två e-postleveranser via ett arbetsflöde för målinriktning. Meddelandet och texten är identiska i båda leveranser: endast layouten ändras.

Målpopulationen är uppdelad i tre: två testgrupper och den återstående populationen. En annan version av leveransen skickas till varje testgrupp.

Efter leveransen konfigureras en 5-dagars vänteperiod innan resultaten av de bästa öppningsfrekvenserna samlas in. Innehållet i leveransen med det högsta poängtalet återskapas sedan av ett skript och skickas till populationen som inte användes som testgrupp.

Observera att de kriterier som avgör vilken leverans som är bäst kan ändras efter dina behov. Det kan vara öppningsfrekvensen, klickfrekvensen, prenumerationstakten, reaktiviteten osv.

Testet som beskrivs i det här fallet avser endast två leveranser, men du kan testa så många versioner som behövs. Lägg bara till aktiviteter i arbetsflödet.

De viktigaste stegen för att utföra den här åtgärden är:

* [Steg 1: Skapa ett målarbetsflöde](a-b-testing-uc-targeting-workflow.md)
* [Steg 2: Konfigurera populationsexempel](a-b-testing-uc-population-samples.md)
* [Steg 3: Skapa två leveransmallar](a-b-testing-uc-delivery-templates.md)
* [Steg 4: Konfigurera leveranserna i arbetsflödet](a-b-testing-uc-configuring-deliveries.md)
* [Steg 5: Skapa skriptet](a-b-testing-uc-script.md)
* [Steg 6: Definiera den slutliga leveransen](a-b-testing-uc-final-delivery.md)
* [Steg 7: Starta arbetsflödet](a-b-testing-uc-start-workflow.md)
* [Steg 8: Analysera resultatet](a-b-testing-uc-analyzing.md)

**Relaterade ämnen:**

* [Kom igång med A/B-tester](get-started-a-b-testing.md)
* [Konfigurera A/B-tester](configuring-a-b-testing.md)
