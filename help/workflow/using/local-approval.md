---
product: campaign
title: Lokalt godkännande
description: Lokalt godkännande
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 2d9cbfc8-1f99-4b38-8460-77c7c986e9ca
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 1%

---

# Lokalt godkännande{#local-approval}

![](../../assets/common.svg)

När den är integrerad i ett målarbetsflöde kan du med aktiviteten **[!UICONTROL Local approval]** konfigurera en process för mottagarnas godkännande innan leveransen skickas.

![](assets/local_validation_0.png)

>[!CAUTION]
>
>För att kunna använda den här aktiviteten måste du ha köpt modulen Distribuerad marknadsföring, som är ett kampanjalternativ. Kontrollera licensavtalet.

Ett exempel på **[!UICONTROL Local approval]**-aktiviteten med en distributionsmall finns i [Använda den lokala godkännandeaktiviteten](using-the-local-approval-activity.md).

Börja med att ange en etikett för aktiviteten och fältet **[!UICONTROL Action to execute]**:

![](assets/local_validation_1.png)

* Välj alternativet **[!UICONTROL Target approval notification]** om du vill skicka ett e-postmeddelande till lokala arbetsledare före leveransen och be dem godkänna mottagarna som tilldelats dem.

   ![](assets/local_validation_intro_2.png)

* **Inkrementell fråga**: gör att du kan utföra en fråga och planera dess körning. Se avsnittet [Inkrementell fråga](incremental-query.md).

   ![](assets/local_validation_intro_3.png)

## Meddelande om målgodkännande {#target-approval-notification}

I det här fallet placeras aktiviteten **[!UICONTROL Local approval]** mellan mål och leverans uppströms:

![](assets/local_validation_2.png)

De fält som ska anges vid ett meddelande om målgodkännande är:

![](assets/local_validation_3.png)

* **[!UICONTROL Distribution context]**: markera  **[!UICONTROL Specified in the transition]** alternativet om du använder en  **[!UICONTROL Split]** typaktivitet för att begränsa målpopulationen. I det här fallet anges distributionsmallen i den delade aktiviteten. Om du inte begränsar målpopulationen väljer du alternativet **[!UICONTROL Explicit]** här och anger distributionsmallen i fältet **[!UICONTROL Data distribution]**.

   Mer information om hur du skapar en mall för datadistribution finns i [Begränsa antalet delmängdsposter per datadistribution](split.md#limiting-the-number-of-subset-records-per-data-distribution).

* **[!UICONTROL Approval management]**

   * Välj leveransmall och ämne som ska användas för e-postmeddelandet. En standardmall är tillgänglig: **[!UICONTROL Local approval notification]**. Du kan också lägga till en beskrivning som visas ovanför mottagarlistorna i godkännanderutorna och feedbackmeddelandena.
   * Ange det **[!UICONTROL Approval type]** som motsvarar godkännandedeadline (datum eller deadline från början av godkännandet). På det här datumet startar arbetsflödet igen och de mottagare som inte har godkänts tas inte med i målsättningen. När meddelandena har skickats står aktiviteten i kö så att de lokala granskarna kan godkänna sina kontakter.

      >[!NOTE]
      >
      >Som standard förlängs aktiviteten i tre dagar när godkännandeprocessen startas.

      Du kan också lägga till en eller flera påminnelser för att informera lokala arbetsledare om att tidsgränsen närmar sig. Det gör du genom att klicka på länken **[!UICONTROL Add a reminder]**.

* **[!UICONTROL Complementary set]**: Med  **[!UICONTROL Generate complement]** alternativet kan du skapa en andra uppsättning som innehåller alla ej godkända mål.

   >[!NOTE]
   >
   >Det här alternativet är inaktiverat som standard.

## Feedback-rapport {#delivery-feedback-report}

I det här fallet placeras aktiviteten **[!UICONTROL Local approval]** efter leveransen:

![](assets/local_validation_4.png)

Följande fält måste anges om det finns en leveransfeedback-rapport:

![](assets/local_validation_workflow_4.png)

* Välj alternativet **[!UICONTROL Specified in the transition]** om leveransen angavs under en tidigare aktivitet. Välj **[!UICONTROL Explicit]** för att ange leveransen i den lokala godkännandeaktiviteten.
* Välj leveransmall och objekt för e-postmeddelandet. Det finns en standardmall: **[!UICONTROL Local approval notification]**.

## Exempel: Godkänna leverans av arbetsflöde {#example--approving-a-workflow-delivery}

I det här exemplet visas hur du ställer in en godkännandeprocess för en arbetsflödesleverans. Mer information om hur du skapar leveransarbetsflöden finns i [Exempel: leveransarbetsflöde](delivery.md#example--delivery-workflow).

En operator kan godkänna en leverans på ett av två sätt: med webbsidan som är länkad i e-postmeddelandet eller via konsolen.

* Webbgodkännande

   Med e-postmeddelandet som skickas till operatorer i gruppen Administratör kan du godkänna leveransmålet. Meddelandet använder den definierade texten och JavaScript-uttrycket ersätts med det beräknade värdet (i det här fallet &quot;574&quot;)

   Klicka på länken och logga in på Adobe Campaign-konsolen för att godkänna leveransen.

   ![](assets/new-workflow-valid-webaccess.png)

   Gör ett val och klicka på knappen **[!UICONTROL Submit]**.

   ![](assets/new-workflow-valid-webaccess-confirm.png)

* Godkännande via konsolen

   I trädstrukturen innehåller noden **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** listan över uppgifter som ska godkännas av den operator som är ansluten. Listan ska innehålla en rad. Dubbelklicka på raden för att svara. Följande fönster visas:

![](assets/new-workflow-7.png)

Välj **Ja** och klicka sedan på **[!UICONTROL Approve]**. Du får ett meddelande om att svaret har registrerats.

Gå tillbaka till arbetsflödesfönstret: Efter tio sekunder visas diagrammet enligt följande:

![](assets/new-workflow-8.png)

Arbetsflödet har utfört uppgiften **[!UICONTROL Delivery control]**, vilket i det här fallet innebär att den leverans som skapades tidigare påbörjas. Arbetsflödet har slutförts utan fel.
