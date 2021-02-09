---
solution: Campaign Classic
product: campaign
title: Kom igång med A/B-tester
description: Läs mer om A/B-testning i Campaign Classic.
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 346b72d522c947b2a2552176b910ded8d622f3ab
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---


# Kom igång med A/B-testning {#get-started-a-b-testing}

A/B-testning gör det möjligt att jämföra flera versioner av en leverans med varandra för att identifiera vilken som kommer att få störst effekt på målpopulationen.

För att göra detta måste du först definiera flera varianter av leveransen. Varje variant skickas sedan till populationsprover för att fastställa vilken som fungerar bäst beroende på vilka kriterier du väljer (öppnar, skräppost, klickar på en specifik länk, ...).

I exemplet nedan har leveransmålet delats upp i två grupper som representerar 50 % av målpopulationen. Varje grupp får två versioner av leveransen med två olika kampanjerbjudanden. När leveransen har skickats dras slutsatsen att variant A har utförts bättre, baserat på antalet klick i kampanjerbjudandena.

![](assets/a-b-testing-schema.png)

Med Campaign Classic implementeras A/B-testning via arbetsflöden, där du anger målpopulationen samt de grupper som ska ta emot varje variant (se [Konfigurera a/b-testning](../../delivery/using/configuring-a-b-testing.md)).

Huvudstegen är:

1. **Rikta** in er på den önskade populationen.
1. **Dela upp** populationen i undergrupper där du ska testa varianterna av leveransen.

   Du kan till exempel skicka en version av en leverans till en liten del av målpopulationen och en annan version till den återstående populationen. På så sätt kan ni testa en ny version av en leverans i stället för den leverans som normalt skickas till kunderna. Du kan också dela in målpopulationen i tre grupper för att skicka dem tre olika versioner av en leverans.

1. **Skapa flera** versioner av leveransen som motsvarar varje delmängd. Varianten som ska testas kan vara ämnet, meddelandeinnehållet, avsändarens namn osv.
1. Starta arbetsflödet och använd sedan **leveransloggarna** för att analysera beteendet hos delmängderna med varje variant.

>[!NOTE]
>
>Med arbetsflöden kan ni också automatisera era processer genom att automatiskt identifiera den bättre levererade varianten och sedan skicka den till den återstående populationen. Mer information finns i det här dedikerade [användningsexemplet](../../delivery/using/a-b-testing-use-case.md).
