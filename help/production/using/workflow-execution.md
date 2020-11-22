---
solution: Campaign Classic
product: campaign
title: Arbetsflödeskörning
description: Arbetsflödeskörning
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 3%

---


# Arbetsflödeskörning{#workflow-execution}

I avsnittet nedan visas information om vanliga problem som rör körning av arbetsflöden och hur du felsöker dem.

Mer information om arbetsflöden finns i följande avsnitt:

* [Om arbetsflöden](../../workflow/using/about-workflows.md)
* [Starta ett arbetsflöde](../../workflow/using/starting-a-workflow.md)
* [Arbetsflödets livscykel](../../workflow/using/workflow-life-cycle.md)
* [Bästa tillvägagångssätt när du använder arbetsflöden](../../workflow/using/workflow-best-practices.md)

## Börja så snart som möjligt i kampanjer {#start-as-soon-as-possible-in-campaigns}

I vissa fall startar inte arbetsflöden som körs från en kampanj när du klickar på **[!UICONTROL Start]** knappen. I stället för att börja går den till läget&quot;Starta så snart som möjligt&quot;.

Det kan finnas flera orsaker till det här problemet, följ stegen nedan för att lösa det:

1. Kontrollera den [**[!UICONTROL operationMgt]**](../../workflow/using/campaign.md) tekniska arbetsflödesstatusen. Det här arbetsflödet hanterar jobb eller arbetsflöden inuti en kampanj. Om det misslyckas resulterar det i arbetsflöden som inte startar/stoppas. Starta om den för att fortsätta köra kampanjarbetsflöden.

   Mer information om övervakning av tekniska arbetsflöden finns på [den här sidan](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >När arbetsflödet har startats om kontrollerar du att du kör väntande uppgifter (högerklicka på **[!UICONTROL Scheduler]** aktiviteten / **[!UICONTROL Execute pending task(s) now]**) för att kontrollera om det misslyckas igen på någon av aktiviteterna.

   Om arbetsflödet fortfarande inte fungerar kontrollerar du om det finns ett specifikt fel i granskningsloggen, felsöker därefter och startar sedan om arbetsflödet igen.

1. Kontrollera modulläget på **[!UICONTROL wfserver]** fliken **[!UICONTROL Monitoring]** , som du kommer åt från Campaign Classic hemsida (se [Övervaka processer](../../production/using/monitoring-processes.md)). Den här processen ansvarar för att köra alla arbetsflöden.

   En admin-användare kan också kontrollera att modulen **wfserver@`<instance>`** startas på huvudprogramservern med hjälp av kommandot nedan.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Kontakta Adobe kundtjänst om modulen inte är igång. Om du har en lokal installation måste en administratörsanvändare starta om tjänsten med kommandot nedan.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Ersätt **`<instancename>`** med namnet på din instans (produktion, utveckling osv.). Instansnamnet identifieras via konfigurationsfilerna:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   For more on how to restart modules, refer to [this section](../../production/using/usual-commands.md#module-launch-commands).

1. Kontrollera om **antalet kampanjprocesser som körs** på instansen överstiger tröskelvärdet. Det finns en gräns som definieras av [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) alternativet för hur många kampanjprocesser som kan köras på instansen parallellt. När den här gränsen nås stannar arbetsflödet kvar i läget&quot;Starta så snart som möjligt&quot; så länge antalet arbetsflöden som körs är över gränsen.

   Du kan lösa problemet genom att stoppa oönskade arbetsflöden och ta bort misslyckade leveranser. Om tröskelvärdet uppnås kan nya processer köras.

   Om du vill kontrollera antalet arbetsflöden som körs för instansen rekommenderar vi att du använder de fördefinierade vyerna, som är tillgängliga som standard i mappen **[!UICONTROL Administration]** / **[!UICONTROL Audit]** . För mer information om detta hittar du i [det här avsnittet](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!IMPORTANT]
   >
   >Om du ökar tröskelvärdet för **[!UICONTROL NmsOperation_LimitConcurrency]** alternativet kan det leda till prestandaproblem i instansen. Utför inte detta på egen hand och kontakta Adobe Campaign.

Mer information om hur du övervakar arbetsflöden finns i [det här avsnittet](../../workflow/using/monitoring-workflow-execution.md).

## Pågående start {#start-in-progress}

Om arbetsflöden inte körs och deras status är **Påbörja**, kan det innebära att arbetsflödesmodulen inte startas.

Gör så här om du vill kontrollera detta och starta modulen om det behövs:

1. Kontrollera modulläget på **[!UICONTROL wfserver]** fliken **[!UICONTROL Monitoring]** , som du kommer åt från Campaign Classic hemsida (se [Övervaka processer](../../production/using/monitoring-processes.md)).

   En admin-användare kan också kontrollera att modulen **wfserver@`<instance>`** startas på huvudprogramservern med hjälp av kommandot nedan.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   For more on how to monitor modules, refer to [this section](../../production/using/usual-commands.md#monitoring-commands-).

1. Kontakta Adobe kundtjänst om modulen inte är igång. Om du har en lokal installation måste en administratör starta om den med kommandot nedan.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Ersätt **`<instancename>`** med namnet på din instans (produktion, utveckling osv.). Instansnamnet identifieras via konfigurationsfilerna:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   For more on how to restart modules, refer to [this section](../../production/using/usual-commands.md#module-launch-commands).

## Misslyckat arbetsflöde {#failed-workflow}

Om ett arbetsflöde misslyckas gör du så här:

1. Kontrollera arbetsflödesjournalen. Mer information finns i avsnitten [Övervaka arbetsflödeskörning](../../workflow/using/monitoring-workflow-execution.md) och [Visningsloggar](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) .
1. Övervaka tekniska arbetsflöden. For more on this refer to the [this section](../../workflow/using/monitoring-technical-workflows.md).
1. Leta efter fel i de enskilda arbetsflödesaktiviteterna.
