---
product: campaign
title: Arbetsflödeskörning
description: Arbetsflödeskörning
feature: Monitoring, Workflows
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 2%

---

# Arbetsflödeskörning{#workflow-execution}



I avsnittet nedan visas information om vanliga problem som rör körning av arbetsflöden och hur du felsöker dem.

Mer information om arbetsflöden finns i följande avsnitt:

* [Om arbetsflöden](../../workflow/using/about-workflows.md)
* [Starta ett arbetsflöde](../../workflow/using/starting-a-workflow.md)
* [Arbetsflödets livscykel](../../workflow/using/workflow-life-cycle.md)
* [Bästa tillvägagångssätt när du använder arbetsflöden](../../workflow/using/workflow-best-practices.md)

## Börja så snart som möjligt i kampanjer {#start-as-soon-as-possible-in-campaigns}

I vissa fall startar inte arbetsflöden som körs från en kampanj när du klickar på knappen **[!UICONTROL Start]**. I stället för att börja går den till läget&quot;Starta så snart som möjligt&quot;.

Det kan finnas flera orsaker till det här problemet, följ stegen nedan för att lösa det:

1. Kontrollera den tekniska arbetsflödesstatusen för [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md). Det här arbetsflödet hanterar jobb eller arbetsflöden inuti en kampanj. Om det misslyckas resulterar det i arbetsflöden som inte startar/stoppas. Starta om den för att fortsätta köra kampanjarbetsflöden.

   Mer information om övervakning av tekniska arbetsflöden finns på [den här sidan](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >När arbetsflödet har startats om kontrollerar du att du har utfört väntande uppgifter (högerklicka på aktiviteten **[!UICONTROL Scheduler]** / **[!UICONTROL Execute pending task(s) now]**) för att kontrollera om det inte fungerar igen på någon av aktiviteterna.

   Om arbetsflödet fortfarande inte fungerar kontrollerar du om det finns ett specifikt fel i granskningsloggen, felsöker därefter och startar sedan om arbetsflödet igen.

1. Kontrollera modulläget **[!UICONTROL wfserver]** på fliken **[!UICONTROL Monitoring]** som är tillgänglig från Campaign Classicens hemsida (se [Övervaka processer](../../production/using/monitoring-processes.md)). Den här processen ansvarar för att köra alla arbetsflöden.

   En administratörsanvändare kan också kontrollera att modulen **wfserver@`<instance>`** startas på huvudprogramservern med hjälp av kommandot nedan.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Kontakta Adobe kundtjänst om modulen inte är igång. Om du har en lokal installation måste en administratörsanvändare starta om tjänsten med kommandot nedan.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Ersätt **`<instance-name>`** med namnet på din instans (produktion, utveckling osv.). Instansnamnet identifieras via konfigurationsfilerna:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Mer information om hur du startar om moduler finns i [det här avsnittet](../../production/using/usual-commands.md#module-launch-commands).

1. Kontrollera om **antalet kampanjprocesser som körs** på instansen överstiger tröskelvärdet. Det finns en gräns som definieras av alternativet [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) för hur många kampanjprocesser som kan köras på instansen parallellt. När den här gränsen nås stannar arbetsflödet kvar i läget&quot;Starta så snart som möjligt&quot; så länge antalet arbetsflöden som körs är över gränsen.

   Du kan lösa problemet genom att stoppa oönskade arbetsflöden och ta bort misslyckade leveranser. Om tröskelvärdet uppnås kan nya processer köras.

   Om du vill kontrollera antalet arbetsflöden som körs för instansen rekommenderar vi att du använder de fördefinierade vyerna, som är tillgängliga som standard i mappen **[!UICONTROL Administration]** / **[!UICONTROL Audit]**. För mer information om detta hittar du i [det här avsnittet](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!IMPORTANT]
   >
   >Om du ökar tröskelvärdet för alternativet **[!UICONTROL NmsOperation_LimitConcurrency]** kan det leda till prestandaproblem i din instans. Utför inte detta på egen hand och kontakta Adobe Campaign.

Mer information om hur du övervakar arbetsflöden finns i [det här avsnittet](../../workflow/using/monitoring-workflow-execution.md).

## Pågående start {#start-in-progress}

Om arbetsflöden inte körs och deras status är **Påbörja** kan det innebära att arbetsflödesmodulen inte startas.

Gör så här om du vill kontrollera detta och starta modulen om det behövs:

1. Kontrollera modulläget **[!UICONTROL wfserver]** på fliken **[!UICONTROL Monitoring]** som är tillgänglig från Campaign Classicens hemsida (se [Övervaka processer](../../production/using/monitoring-processes.md)).

   En administratörsanvändare kan också kontrollera att modulen **wfserver@`<instance>`** startas på huvudprogramservern med hjälp av kommandot nedan.

   ```sql
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Mer information om hur du övervakar moduler finns i [det här avsnittet](../../production/using/usual-commands.md#monitoring-commands-).

1. Kontakta Adobe kundtjänst om modulen inte är igång. Om du har en lokal installation måste en administratör starta om den med kommandot nedan.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Ersätt **`<instance-name>`** med namnet på din instans (produktion, utveckling osv.). Instansnamnet identifieras via konfigurationsfilerna:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Mer information om hur du startar om moduler finns i [det här avsnittet](../../production/using/usual-commands.md#module-launch-commands).

## Arbetsflödet misslyckades {#failed-workflow}

Om ett arbetsflöde misslyckas gör du så här:

1. Kontrollera arbetsflödesjournalen. Mer information finns i avsnitten [Övervaka arbetsflödeskörning](../../workflow/using/monitoring-workflow-execution.md) och [Visningsloggar](../../workflow/using/monitoring-workflow-execution.md#displaying-logs).
1. Övervaka tekniska arbetsflöden. Mer information finns i avsnittet [this](../../workflow/using/monitoring-technical-workflows.md).
1. Leta efter fel i de enskilda arbetsflödesaktiviteterna.
