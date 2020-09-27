---
title: Om arbetsflöden
description: Automatisera processerna med arbetsflöden, hantera data och målgrupper, skicka meddelanden med mera.
page-status-flag: never-activated
uuid: 19adb0e5-042d-47a0-9f92-24e4b3045dbe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: introduction
discoiquuid: 868940d1-f19d-4e9a-bffa-8654abb4441c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: eccf0e9899426c2517748c7a72611ff098291cd2
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 16%

---


# Kom igång med arbetsflöden{#about-workflows}

## Om arbetsflöden

Adobe Campaign innehåller en arbetsflödesmodul som gör det möjligt att samordna alla processer och uppgifter i de olika modulerna i programservern. I den omfattande grafiska miljön kan du utforma processer såsom segmentering, kampanjkörning, filhantering och mänskligt deltagande osv. Arbetsflödesmotorn kör och spårar dessa processer.

Du kan till exempel använda ett arbetsflöde för att ladda ned en fil från en server, expandera den och sedan importera poster som finns i databasen i Adobe Campaign.

Ett arbetsflöde kan även innefatta en eller flera operatörer som ska meddelas eller som kan göra val och godkänna processer. På så sätt kan du skapa en leveransinstruktion, tilldela en eller flera operatörer uppgiften att arbeta med innehåll, ange mål och godkänna korrekturer innan leveransen påbörjas.

Arbetsflöden sker i olika sammanhang och under olika faser av kampanjhanteringsprocessen.

Adobe Campaign använder arbetsflöden för att

* Utför riktade kampanjer. For more on this, refer to [Implementation steps](../../workflow/using/building-a-workflow.md#implementation-steps-).
* Skapa kampanjer: för varje kampanj kan du med fliken **[!UICONTROL Workflow]** skapa målet och leveranserna. For more on this, refer to [Campaign workflows](../../workflow/using/building-a-workflow.md#campaign-workflows).
* Utför tekniska processer: rensning, insamling av spårningsinformation eller preliminära beräkningar. For more on this, refer to [Technical workflows](../../workflow/using/building-a-workflow.md#technical-workflows).

Ett arbetsflöde kan betyda både en processdefinition (arbetsflödesmodellen, som är en representation av vad som ska hända) och en instans av den här processen (en arbetsflödesinstans, som är en representation av vad som faktiskt händer).

Arbetsflödesmallen beskriver de olika uppgifter som ska utföras och hur de länkas samman. Uppgiftsmallarna kallas aktiviteter och representeras av ikoner. De länkas ihop av övergångar.

![](assets/example1.png)

Varje arbetsflöde innehåller:

* **[!UICONTROL Activities]**

   En aktivitet beskriver en uppgiftsmall. De olika aktiviteterna som är tillgängliga visas i diagrammet med ikoner. Varje typ har gemensamma egenskaper och specifika egenskaper. Alla aktiviteter har till exempel ett namn och en etikett, men bara **[!UICONTROL Approval]** aktiviteten har ett uppdrag.

   I ett arbetsflödesdiagram kan en viss aktivitet producera flera uppgifter, särskilt när det finns en slinga eller återkommande (periodiska) åtgärder.

   Alla arbetsflödesaktiviteter listas i [det här avsnittet](../../workflow/using/about-activities.md), inklusive användningsexempel och exempel.

* **[!UICONTROL Transitions]**

   Med övergångar kan du länka aktiviteter och definiera deras sekvens. En övergång länkar en källaktivitet till en målaktivitet. Det finns flera typer av övergångar, som är beroende av källaktiviteten. Vissa övergångar har ytterligare parametrar som längd, villkor eller filter.

   En övergång som inte är länkad till en målaktivitet får färgen orange och pilhuvudet visas som en romb.

   >[!NOTE]
   >
   >Ett arbetsflöde som innehåller oavslutade övergångar kan fortfarande köras: ett varningsmeddelande genereras och arbetsflödet pausas när övergången är klar, men det genererar inget fel. Det är alltså möjligt att starta ett arbetsflöde utan att det är färdigt och att lägga till i det när du går vidare.

   Mer information om hur du skapar ett arbetsflöde finns i [det här avsnittet](../../workflow/using/building-a-workflow.md).

* **[!UICONTROL Worktables]**

   Arbetstabellen innehåller all information som övergången innehåller. Varje arbetsflöde använder flera arbetstabeller. Data som förmedlas i dessa tabeller kan accelereras och användas under arbetsflödets hela livscykel, så länge de inte rensas. Det går att tömma tabeller som inte behövs varje gång arbetsflödet är passivat och eventuellt under körningen av de största arbetsflödena för att undvika att servern överbelastas.

   Läs mer om arbetsflödesdata och tabeller i [det här avsnittet](../../workflow/using/how-to-use-workflow-data.md).

## Viktiga principer och bästa metoder

I dessa avsnitt hittar du vägledning och bästa metoder för att automatisera processer med arbetsflöden:

* Läs mer om arbetsflödesaktiviteter på [den här sidan](../../workflow/using/how-to-use-workflow-data.md).
* Lär dig hur du skapar ett arbetsflöde i [det här avsnittet](../../workflow/using/building-a-workflow.md).
* Lär dig hur du använder arbetsflöden för att importera data i Campaign i [det här avsnittet](../../workflow/using/importing-data.md).
* De effektivaste arbetsflödena beskrivs närmare på [den här sidan](../../workflow/using/workflow-best-practices.md).
* Mer information om arbetsflödeskörning finns i [det här avsnittet](../../workflow/using/starting-a-workflow.md).
* Lär dig hur du övervakar arbetsflöden på [den här sidan](../../workflow/using/monitoring-workflow-execution).
* Lär dig hur du ger användare åtkomst till arbetsflöden på [den här sidan](../../workflow/using/managing-rights.md).
