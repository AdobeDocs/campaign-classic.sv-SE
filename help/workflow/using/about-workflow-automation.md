---
product: campaign
title: Om arbetsflöden
description: Automatisera processerna med arbetsflöden, hantera data och målgrupper, skicka meddelanden med mera
feature: Workflows, Data Management
exl-id: 024a7344-9376-4ff3-926a-003148229f9f
source-git-commit: dd6bcb16fe41b6a3f1e3f5aaf2f753b29ad4bc1d
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 57%

---

# Automatisera med arbetsflöden {#gs-workflows}

Adobe Campaign har en arbetsflödesmodul som gör att du kan ställa in alla processer och uppgifter i olika moduler på programservern. I den omfattande grafiska miljön kan du utforma processer såsom segmentering, kampanjkörning, filhantering och mänskligt deltagande osv. Arbetsflödesmotorn kör och spårar dessa processer.

Du kan till exempel använda ett arbetsflöde för att ladda ned en fil från en server, expandera den och sedan importera poster som finns i databasen i Adobe Campaign.

Ett arbetsflöde kan även innefatta en eller flera operatörer som ska meddelas eller som kan göra val och godkänna processer. På så sätt kan du skapa en leveransinstruktion, tilldela en eller flera operatörer uppgiften att arbeta med innehåll, ange mål och godkänna korrekturer innan leveransen påbörjas.

Arbetsflöden sker i olika sammanhang och under olika faser av kampanjhanteringsprocessen.

Mer information om arbetsflödeshantering finns i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html){target=_blank}.

![](assets/do-not-localize/workflow.jpg){width="40%"}

Lär dig de viktigaste stegen för hantering av arbetsflöden:

* [Arbetsflödesaktiviteter](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/activities.html){target=_blank}: En aktivitet beskriver en uppgiftsmall. Arbetsflödena innefattar målinriktning, flödeskontroll, åtgärder och händelseaktiviteter.

* [Bygg ett arbetsflöde](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html){target=_blank}: Lär dig hur du skapar och kör målgruppsanpassning, kampanjer och tekniska arbetsflöden.

* [God praxis](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html){target=_blank}: Lär dig mer om riktlinjerna för att optimera prestanda för Campaign-arbetsflöden, förbättra arbetsflödesdesignen och välja rätt inställningar.

* [Övervaka arbetsflöden](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target=_blank}: Lär dig hur du övervakar arbetsflödeskörningen för att se till att allt körs korrekt.

* [Exempel på arbetsflödesanvändning](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/workflow-use-cases.html){target=_blank}: Lär dig olika sammanhang i vilka arbetsflöden kan användas och hur du implementerar dem genom hela användningsexempel.

<!--

Adobe Campaign uses workflows to:

* Carry out targeting campaigns. [Learn more](building-a-workflow.md#implementation-steps-)
* Build campaigns: for each campaign, the **[!UICONTROL Workflow]** tab lets you build the target and create the deliveries. [Learn more](building-a-workflow.md#campaign-workflows)
* Perform technical processes: cleanup, collecting tracking information or provisional calculations. [Learn more](building-a-workflow.md#technical-workflows)

A workflow can mean both a process definition (the workflow model, which is a representation of what is supposed to happen) and an instance of this process (a workflow instance, which is a representation of what is actually happening).

The workflow template describes the various tasks to be performed and how they are linked together. The task templates are called activities and are represented by icons. They are linked together by transitions.

![](assets/example1.png)

Each workflow contains:

* **[!UICONTROL Activities]**

  An activity describes a task template. The various activities available are represented on the diagram by icons. Each type has common properties and specific properties. For example, while all activities have a name and label, only the **[!UICONTROL Approval]** activity has an assignment.

  In a workflow diagram, a given activity can produce multiple tasks, in particular when there is a loop or recurrent (periodic) actions.

  All workflow activities are listed in [this section](about-activities.md), including use cases and samples.

* **[!UICONTROL Transitions]**

  Transitions enable you to link activities and to define their sequence. A transition links a source activity to a destination activity. There are several sorts of transitions, which depend on the source activity. Some transitions have additional parameters such as a duration, a condition or a filter.

  A transition which is not linked to a destination activity is colored orange and the arrow head is shown as a diamond.

  >[!NOTE]
  >
  >A workflow containing unterminated transitions can still be executed: a warning message will be generated and the workflow will pause once it reaches the transition but it will not generate an error. It is thus possible to start a workflow without it being finished and to add to it as you go along.

  For more information about how to build a workflow, refer to [this section](building-a-workflow.md).

* **[!UICONTROL Worktables]**

  The worktable contains all the information carried by the transition. Each workflow uses several worktables. The data conveyed in these tables can be accelerated and used throughout the workflow's life cycle, as long as it is not purged. Indeed, unneeded tables are purged each time the workflow is passivated, and possibly during the execution of the largest workflows to avoid overloading the server.

  Learn more on workflow data and tables in [this section](how-to-use-workflow-data.md).

## Key principles and best practices{#principles-workflows}

Refer to these sections to find guidance and best practices to automate processes with workflows:

* Learn more about workflow activities in [this page](how-to-use-workflow-data.md).
* Learn how to build a workflow in [this section](building-a-workflow.md).
* Discover how to use workflows to import data in Campaign in [this section](../../platform/using/import-export-workflows.md).
* Workflow best practices are detailed in [this page](workflow-best-practices.md).
* Find guidance about workflow execution in [this section](starting-a-workflow.md).
* Learn how to monitor workflows in [this page](monitoring-workflow-execution.md).
* Learn how to grant access to users to use workflows in [this page](managing-rights.md).

-->