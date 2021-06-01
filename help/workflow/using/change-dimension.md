---
product: campaign
title: Ändra dimension
description: Ändra dimension
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: c3de99f8-089f-4c7c-be11-f375a9463eaa
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 2%

---

# Ändra dimension{#change-dimension}

Med aktiviteten för att ändra dimension kan du ändra måldimensionen under målkonstruktionscykeln. Axelväxling beror på datamallen och indatamängden. På så sätt kan du till exempel växla från dimensionen &quot;kontrakt&quot; till dimensionen &quot;kunder&quot;.

Du kan också använda den här aktiviteten för att definiera ytterligare kolumner för det nya målet.

Det går att definiera villkor för borttagning av dubbletter av data.

## Konfigurationsläge {#configuration-mode}

Så här konfigurerar du ändringsdimensionsaktiviteten:

1. Välj den nya måldimensionen via fältet **[!UICONTROL Change dimension]**.

   ![](assets/s_user_change_dimension_param1.png)

1. Vid dimensionsändring kan du behålla alla element eller välja de som ska bevaras i utdata. I följande exempel är max. antalet dubbletter anges till 2.

   ![](assets/s_user_change_dimension_limit.png)

   När du väljer att bara behålla en post visas en samling i arbetsschemat: Den här samlingen representerar alla poster som inte kommer att användas som mål i det slutliga resultatet (eftersom endast en post behålls). I likhet med alla andra samlingar kan du med den här metoden beräkna aggregeringar eller återställa information i kolumner.

   Om du till exempel ändrar dimensionen **[!UICONTROL Customers]** till dimensionen **[!UICONTROL Recipients]** kan du rikta in dig på kunder i en viss butik, samtidigt som du lägger till antalet inköp.

1. Om du väljer att inte behålla all den här informationen kan du konfigurera det duplicerade hanteringsläget.

   ![](assets/s_user_change_dimension_param2.png)

   Med de blå pilarna kan du definiera den duplicerade bearbetningsprioriteten.

   I exemplet ovan dedupliceras mottagarna först till sin e-postadress och sedan till sitt kontonummer om det behövs.

1. På fliken **[!UICONTROL Result]** kan du lägga till ytterligare information.

   Du kan till exempel återskapa regionen baserat på postnumret genom att använda en **delsträng**-typfunktion. Så här gör du:

   * Klicka på länken **[!UICONTROL Add data...]** och välj **[!UICONTROL Data linked to the filtering dimension]**.

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >Mer information om hur du skapar och hanterar ytterligare kolumner finns i [Lägga till data](../../workflow/using/query.md#adding-data).

   * Markera föregående måldimension (före axelväxling) och välj **[!UICONTROL Zip Code]** i mottagarens **[!UICONTROL Location]**-underträd och klicka sedan på **[!UICONTROL Edit expression]**.

      ![](assets/wf_change-dimension_sample_02.png)

   * Klicka på **[!UICONTROL Advanced selection]** och välj **[!UICONTROL Edit the formula using an expression]**.

      ![](assets/wf_change-dimension_sample_03.png)

   * Använd funktionerna i listan och ange vilken beräkning som ska utföras.

      ![](assets/wf_change-dimension_sample_04.png)

   * Ange slutligen etiketten för den kolumn som du nyss skapade.

      ![](assets/wf_change-dimension_sample_05.png)

1. Kör arbetsflödet för att visa resultatet av den här konfigurationen. Jämför data i tabellerna före och efter ändringsdimensionsaktiviteten och jämför arbetsflödestabellernas struktur, vilket visas i följande exempel:

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)
