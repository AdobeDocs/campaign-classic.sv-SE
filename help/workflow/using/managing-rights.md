---
product: campaign
title: Hantera arbetsflödesbehörigheter
description: Lär dig hur du hanterar arbetsflödesbehörigheter
feature: Workflows
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Hantera arbetsflödesbehörigheter{#managing-rights}



Om de inte är administratörer behöver Adobe Campaign-operatorer åtkomstbehörighet för att skapa, köra eller ändra arbetsflöden.

I allmänhet behöver operatorer som arbetar med arbetsflöden komma åt de filer som innehåller de data som används under de olika aktiviteterna (mottagare, mottagarlista, prenumerationer, leveranser osv.) och eventuellt deras underfiler.

De måste också mappas till namngivna rättigheter som sammanfaller med de åtgärder som utförs av arbetsflöden som de påverkar (mottagarimport, filåtkomst, fusion, SQL-skriptkörning osv.).

Mer information om hur du hanterar operatorer och behörigheter finns i [section](../../platform/using/access-management.md).

## Operatörsgrupper {#operator-groups-wf}

Följande operatorgrupper är kopplade till arbetsflödet:

* The **[!UICONTROL Workflow execution]** kan du styra körning och godkännande av målarbetsflöden: det namngivna högerarbetsflödet mappas till den här gruppens operatorer. Det krävs för alla åtgärder i arbetsflöden, förutom åtkomsträttigheter till datafilerna. Som standard är **[!UICONTROL Workflow execution]** -gruppen har skrivskyddad åtkomst till arbetsflödesfiler och arbetsflödesmallar som är avsedda för målinriktning. Operatörer i den här gruppen har även läs- och skrivåtkomst till filen för väntande godkännanden.
* The **[!UICONTROL Workflow supervisors]** grupp låter operatorer hantera arbetsflödesgodkännanden.
* The **[!UICONTROL Operation Managers]** grupp för att få tillgång till kampanjarbetsflöden.

## Namngivna rättigheter {#named-rights}

Endast arbetsflödet med namnet right är specifikt för arbetsflöden: du kan skapa, starta och stoppa arbetsflöden. Läsbehörighet för arbetsflödesfilen krävs för att den namngivna rättigheten ska kunna användas. För arbetsflöden med målinriktning **[!UICONTROL Profiles and Targets]** filen är nödvändig.

## Konto för arbetsflödeskörning {#workflow-execution-account}

Du kan konfigurera det körningskonto som ska användas på arbetsflödesmallnivå. Med körningskontot kan du mappa auktoriseringar till arbetsflödet direkt, oavsett vilken Adobe Campaign-operator som startar körningen. Som standard körs varje arbetsflöde med behörigheten för den operator som startade det.

Om du vill mappa ett körningskonto till ett arbetsflöde går du till listan med arbetsflödesmallar och högerklickar på mallen som är länkad till arbetsflödet. Välj **[!UICONTROL Action > Change execution account...]** välj det konto som ska användas.
