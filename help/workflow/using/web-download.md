---
product: campaign
title: Webbhämtning
description: Läs mer om arbetsflödet för nedladdning av webbsidor
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Workflows
exl-id: b6005eae-5fbc-4e22-ab3a-c9b7ed6506f6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 3%

---

# Webbhämtning{#web-download}



The **Webbnedladdning** startar nedladdningen av en fil på en explicit URL, ett externt konto eller en Adobe Campaign-instans. HTTP-protokollet används. Det kan vara en nedladdning av GET eller POST.

## Egenskaper {#properties}

1. **Välja webbfil**

   Om du vill ange vilken fil som ska laddas ned kan du ange fil-URL:en, använda det externa HTTP-kontot där filen lagras eller läsa in filen via en Adobe Campaign-instans. Tillgängliga parametrar beskrivs nedan:

   * Om du vill ange URL:en för filen som ska laddas ned direkt väljer du **[!UICONTROL Explicit URL]** och ange URL-adressen i lämpligt fält. Den här URL:en kan konstrueras med variabeldata.

     ![](assets/download_web_edit.png)

   * Så här använder du **[!UICONTROL External account]** väljer du kontot i listrutan och anger vilken fil som ska hämtas.

     Externa konton konfigureras från **[!UICONTROL Administration > Platform > External accounts]** noden i Adobe Campaign-trädet. Kontoparametrarna kan redigeras via **[!UICONTROL Edit link]** -ikon.

     ![](assets/download_web_edit_external.png)

   * Om du vill hämta filen från Adobe Campaign-instansen väljer du **[!UICONTROL Adobe Campaign Instance]** alternativ.

     ![](assets/download_web_edit_instance.png)

1. **Filhistorik**

   The **[!UICONTROL File historization settings...]** kan du ange lagringskatalogen för filen och tömningsfrekvensen för den här katalogen.

   ![](assets/download_web_edit_hist.png)

   Följande alternativ är tillgängliga:

   * **[!UICONTROL Use a default storage directory]**: filen flyttas alltid innan den bearbetas. Om det här alternativet är markerat flyttas filen till standardlagringskatalogen ( **vars** i Adobe Campaign installationsmapp). Om du vill ange en lagringskatalog avmarkerar du kryssrutan och anger sökvägen i dialogrutan **[!UICONTROL Storage directory]** fält
   * **[!UICONTROL Number of files]**: Ange det maximala antalet filer som ska lagras i lagringskatalogen.
   * **[!UICONTROL Maximum size (in Mb)]**: Ange maximal kapacitet för lagringskatalogen (i MB).

   Varje fil sparas i 24 timmar innan den omfattas av de definierade reningsreglerna. Rensa sker precis innan aktiviteten startas och tar därför inte hänsyn till den aktuella arbetsflödesfilen.

   Filerna tas bort som en funktion av deras ålder (äldsta till nyaste). De äldsta filerna rensas tills båda tömningsreglerna verifieras. Om du definierar en gräns på 100 filer innebär det därför att lagringskatalogen alltid innehåller de 100 senaste filerna innan arbetsflödet påbörjas, samt de som bearbetas i arbetsflödet som pågår.

   Om du inte längre vill ange en gräns för **[!UICONTROL Number of files]** och **[!UICONTROL Maximum size (in Mb)]** anger du 0 som värde.

1. **Avancerade parametrar**

   The **[!UICONTROL Advanced parameters...]** kan du ange ytterligare alternativ som visas nedan:

   ![](assets/download_web_edit_advanced.png)

   The **[!UICONTROL Process errors]** finns i [Bearbetningsfel](monitoring-workflow-execution.md#processing-errors).

## Utdataparametrar {#output-parameters}

* filnamn: Den hämtade filens fullständiga namn.
