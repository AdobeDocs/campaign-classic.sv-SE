---
title: Om arbetsflöden
seo-title: Om arbetsflöden
description: Om arbetsflöden
seo-description: null
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
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Om arbetsflöden{#about-workflows}

Adobe Campaign innehåller en arbetsflödesmodul som gör det möjligt att samordna alla processer och uppgifter i olika moduler på programservern. I den omfattande grafiska miljön kan ni utforma processer som segmentering, kampanjhantering, filhantering, medarbetare osv. Arbetsflödesmotorn kör och spårar dessa processer.

Du kan till exempel använda ett arbetsflöde för att hämta en fil från en server, expandera den och sedan importera poster i Adobe Campaign-databasen.

Ett arbetsflöde kan även omfatta en eller flera operatorer som ska meddelas eller som kan göra val och godkänna processer. På så sätt kan du skapa en leveransåtgärd, tilldela en eller flera operatorer en uppgift att arbeta med innehåll, ange mål och godkänna korrektur innan leveransen påbörjas.

Arbetsflöden sker i olika sammanhang och under olika faser av kampanjhanteringsprocessen.

Adobe Campaign använder arbetsflöden för att

* Utför riktade kampanjer. Mer information finns i [Implementeringssteg](../../workflow/using/building-a-workflow.md#implementation-steps-).
* Skapa kampanjer: för varje kampanj kan du med fliken **[!UICONTROL Workflow]** skapa målet och leveranserna. Mer information finns i [Kampanjarbetsflöden](../../workflow/using/building-a-workflow.md#campaign-workflows).
* Utför tekniska processer: rensning, insamling av spårningsinformation eller preliminära beräkningar. Mer information finns i [Tekniska arbetsflöden](../../workflow/using/building-a-workflow.md#technical-workflows).

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

