---
title: Ändra dimension
seo-title: Ändra dimension
description: Ändra dimension
seo-description: null
page-status-flag: never-activated
uuid: 6cb309c0-4096-47ce-b1d4-37a3ddafaaa1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 61583062-2349-4ab3-a3bf-310d21894f34
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Ändra dimension{#change-dimension}

Med aktiviteten för att ändra dimension kan du ändra måldimensionen under målkonstruktionscykeln. Axelväxling beror på datamallen och indatamängden. På så sätt kan du till exempel växla från dimensionen &quot;kontrakt&quot; till dimensionen &quot;kunder&quot;.

Du kan också använda den här aktiviteten för att definiera ytterligare kolumner för det nya målet.

Det går att definiera villkor för borttagning av dubbletter av data.

## Konfigurationsläge {#configuration-mode}

Så här konfigurerar du ändringsdimensionsaktiviteten:

1. Välj den nya måldimensionen via **[!UICONTROL Change dimension]** fältet.

   ![](assets/s_user_change_dimension_param1.png)

1. Vid dimensionsändring kan du behålla alla element eller välja de som ska bevaras i utdata. I följande exempel är max. antalet dubbletter anges till 2.

   ![](assets/s_user_change_dimension_limit.png)

   När du väljer att bara behålla en post visas en samling i arbetsschemat: Den här samlingen representerar alla poster som inte kommer att användas som mål i det slutliga resultatet (eftersom endast en post behålls). I likhet med alla andra samlingar kan du med den här metoden beräkna aggregeringar eller återställa information i kolumner.

   Om du till exempel ändrar dimensionen **[!UICONTROL Customers]** till **[!UICONTROL Recipients]** dimensionen kan du rikta in dig på kunder i en viss butik, samtidigt som du lägger till antalet inköp.

1. Om du väljer att inte behålla all den här informationen kan du konfigurera det duplicerade hanteringsläget.

   ![](assets/s_user_change_dimension_param2.png)

   Med de blå pilarna kan du definiera den duplicerade bearbetningsprioriteten.

   I exemplet ovan dedupliceras mottagarna först till sin e-postadress och sedan till sitt kontonummer om det behövs.

1. På fliken **[!UICONTROL Result]** kan du lägga till ytterligare information.

   Du kan till exempel återskapa regionen baserat på postnumret med hjälp av en **delsträngtypsfunktion** . Så här gör du:

   * Klicka på **[!UICONTROL Add data...]** länken och välj **[!UICONTROL Data linked to the filtering dimension]**.

      ![](assets/wf_change-dimension_sample_01.png)

      >[!NOTE]
      >
      >Mer information om hur du skapar och hanterar ytterligare kolumner finns i [Lägga till data](../../workflow/using/query.md#adding-data).

   * Markera den tidigare måldimensionen (före axelväxling) och markera den **[!UICONTROL Zip Code]** i mottagarens **[!UICONTROL Location]** underträd och klicka sedan på **[!UICONTROL Edit expression]**.

      ![](assets/wf_change-dimension_sample_02.png)

   * Klicka **[!UICONTROL Advanced selection]** och välj **[!UICONTROL Edit the formula using an expression]**.

      ![](assets/wf_change-dimension_sample_03.png)

   * Använd funktionerna i listan och ange vilken beräkning som ska utföras.

      ![](assets/wf_change-dimension_sample_04.png)

   * Ange slutligen etiketten för den kolumn som du nyss skapade.

      ![](assets/wf_change-dimension_sample_05.png)

1. Kör arbetsflödet för att visa resultatet av den här konfigurationen. Jämför data i tabellerna före och efter ändringsdimensionsaktiviteten och jämför arbetsflödestabellernas struktur, vilket visas i följande exempel:

   ![](assets/wf_change-dimension_sample_06.png)

   ![](assets/wf_change-dimension_sample_07.png)

