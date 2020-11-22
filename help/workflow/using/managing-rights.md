---
solution: Campaign Classic
product: campaign
title: Hantera rättigheter
description: Hantera rättigheter
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 1%

---


# Hantera rättigheter{#managing-rights}

Om de inte är administratörer behöver Adobe Campaign-operatorer åtkomstbehörighet för att skapa, köra eller ändra arbetsflöden.

I allmänhet behöver operatorer som arbetar med arbetsflöden komma åt de filer som innehåller de data som används under de olika aktiviteterna (mottagare, mottagarlista, prenumerationer, leveranser osv.) och eventuellt deras underfiler.

De måste också mappas till namngivna rättigheter som sammanfaller med de åtgärder som utförs av arbetsflöden som de påverkar (mottagarimport, filåtkomst, fusion, SQL-skriptkörning osv.).

Mer information om hur du hanterar operatorer och behörigheter finns i det här [avsnittet](../../platform/using/access-management.md).

## Operatörsgrupper {#operator-groups}

Följande operatorgrupper är kopplade till arbetsflödet:

* Med **[!UICONTROL Workflow execution]** gruppen kan du styra körning och godkännande av målarbetsflöden: det WORKFLOW som namnges till höger mappas till den här gruppens operatorer. Det krävs för alla åtgärder i arbetsflöden, förutom åtkomsträttigheter till datafilerna. Som standard har **[!UICONTROL Workflow execution]** gruppen skrivskyddad åtkomst till arbetsflödesfiler och arbetsflödesmallar för målanpassning. Operatörer i den här gruppen har även läs- och skrivåtkomst till filen för väntande godkännanden.
* I gruppen kan **[!UICONTROL Workflow supervisors]** operatorer hantera arbetsflödesgodkännanden.
* Gruppen som **[!UICONTROL Operation Managers]** ska få tillgång till kampanjarbetsflöden.

## Namngivna rättigheter {#named-rights}

Endast arbetsflödet med namnet right är specifikt för arbetsflöden: Med kan du skapa, starta och stoppa arbetsflöden. Läsbehörighet för arbetsflödesfilen krävs för att den namngivna rättigheten ska kunna användas. För arbetsflöden med målinriktning krävs läsbehörighet för **[!UICONTROL Profiles and Targets]** filen.

## Konto för arbetsflödeskörning {#workflow-execution-account}

Du kan konfigurera det körningskonto som ska användas på arbetsflödesmallnivå. Med körningskontot kan du mappa auktoriseringar till arbetsflödet direkt, oavsett vilken Adobe Campaign-operator som startar körningen. Som standard körs varje arbetsflöde med behörigheten för den operator som startade det.

Om du vill mappa ett körningskonto till ett arbetsflöde går du till listan med arbetsflödesmallar och högerklickar på mallen som är länkad till arbetsflödet. Välj **[!UICONTROL Action > Change execution account...]** sedan det konto som ska användas.
