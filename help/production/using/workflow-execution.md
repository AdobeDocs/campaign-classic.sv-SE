---
product: campaign
title: Arbetsflödeskörning
description: Arbetsflödeskörning
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-on-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: 0429c3608fbcec98a397cc17fd45cd173cf64b6e
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

I vissa fall startar inte arbetsflöden som körs från en kampanj när du klickar på **[!UICONTROL Start]** -knappen. I stället för att börja går den till läget&quot;Starta så snart som möjligt&quot;.

Det kan finnas flera orsaker till det här problemet, följ stegen nedan för att lösa det:

1. Kontrollera [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) teknisk arbetsflödesstatus. Det här arbetsflödet hanterar jobb eller arbetsflöden inuti en kampanj. Om det misslyckas resulterar det i arbetsflöden som inte startar/stoppas. Starta om den för att fortsätta köra kampanjarbetsflöden.

   Mer information om övervakning av tekniska arbetsflöden finns i [den här sidan](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >När arbetsflödet har startats om kontrollerar du att du kör väntande uppgifter (högerklicka på **[!UICONTROL Scheduler]** aktivitet / **[!UICONTROL Execute pending task(s) now]**) för att kontrollera om det inte fungerar igen på någon av aktiviteterna.

   Om arbetsflödet fortfarande inte fungerar kontrollerar du om det finns ett specifikt fel i granskningsloggen, felsöker därefter och startar sedan om arbetsflödet igen.

1. Kontrollera **[!UICONTROL wfserver]** modulläget i **[!UICONTROL Monitoring]** -flik, tillgänglig från Campaign Classic hemsida (se [Övervaka processer](../../production/using/monitoring-processes.md)). Den här processen ansvarar för att köra alla arbetsflöden.

   En administratörsanvändare kan även kontrollera att **wfserver@`<instance>`** -modulen startas på huvudprogramservern med hjälp av kommandot nedan.

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

   Mer information om hur du startar om moduler finns i [det här avsnittet](../../production/using/usual-commands.md#module-launch-commands).

1. Kontrollera om **antal kampanjprocesser som körs** på instansen är större än tröskelvärdet. Det finns en gräns som definieras av [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) alternativ för hur många kampanjprocesser som kan köras på instansen parallellt. När den här gränsen nås stannar arbetsflödet kvar i läget&quot;Starta så snart som möjligt&quot; så länge antalet arbetsflöden som körs är över gränsen.

   Du kan lösa problemet genom att stoppa oönskade arbetsflöden och ta bort misslyckade leveranser. Om tröskelvärdet uppnås kan nya processer köras.

   Om du vill kontrollera antalet arbetsflöden som körs för instansen rekommenderar vi att du använder de fördefinierade vyerna, som är tillgängliga som standard i **[!UICONTROL Administration]** / **[!UICONTROL Audit]** mapp. För mer information om detta hittar du i [det här avsnittet](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!IMPORTANT]
   >
   >Öka **[!UICONTROL NmsOperation_LimitConcurrency]** tröskelvärdet för alternativ kan leda till prestandaproblem i din instans. Utför inte detta på egen hand och kontakta Adobe Campaign.

Mer information om hur du övervakar arbetsflöden finns i [det här avsnittet](../../workflow/using/monitoring-workflow-execution.md).

## Pågående start {#start-in-progress}

Om arbetsflöden inte körs och deras status är **Pågående start** kan det innebära att arbetsflödesmodulen inte startas.

Gör så här om du vill kontrollera detta och starta modulen om det behövs:

1. Kontrollera **[!UICONTROL wfserver]** modulläget i **[!UICONTROL Monitoring]** -flik, tillgänglig från Campaign Classic hemsida (se [Övervaka processer](../../production/using/monitoring-processes.md)).

   En administratörsanvändare kan även kontrollera att **wfserver@`<instance>`** -modulen startas på huvudprogramservern med hjälp av kommandot nedan.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Mer information om hur du övervakar moduler finns i [det här avsnittet](../../production/using/usual-commands.md#monitoring-commands-).

1. Kontakta Adobe kundtjänst om modulen inte är igång. Om du har en lokal installation måste en administratör starta om den med kommandot nedan.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Ersätt **`<instancename>`** med namnet på din instans (produktion, utveckling osv.). Instansnamnet identifieras via konfigurationsfilerna:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Mer information om hur du startar om moduler finns i [det här avsnittet](../../production/using/usual-commands.md#module-launch-commands).

## Misslyckat arbetsflöde {#failed-workflow}

Om ett arbetsflöde misslyckas gör du så här:

1. Kontrollera arbetsflödesjournalen. Mer information finns i [Övervaka körning av arbetsflöde](../../workflow/using/monitoring-workflow-execution.md) och [Visningsloggar](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) -avsnitt.
1. Övervaka tekniska arbetsflöden. Mer information finns i [det här avsnittet](../../workflow/using/monitoring-technical-workflows.md).
1. Leta efter fel i de enskilda arbetsflödesaktiviteterna.
