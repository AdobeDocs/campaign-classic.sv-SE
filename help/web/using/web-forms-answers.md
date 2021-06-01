---
product: campaign
title: Svar från webbformulär
description: Svar från webbformulär
audience: web
content-type: reference
topic-tags: web-forms
exl-id: 5d48bb27-1884-47f1-acb7-dff5113565bc
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 1%

---

# Svar från webbformulär{#web-forms-answers}

## Svarslagringsfält {#response-storage-fields}

Svar på formulär kan sparas i ett databasfält eller tillfälligt i en lokal variabel. Lagringsläget för svar väljs när fält skapas. Den kan redigeras via länken **[!UICONTROL Edit storage...]**.

För varje inmatningsfält i ett formulär finns följande lagringsalternativ tillgängliga:

![](assets/s_ncs_admin_survey_select_storage.png)

* **[!UICONTROL Edit a recipient]**

   Du kan välja ett fält i databasen: användarnas svar lagras i det här fältet. För varje användare sparas endast det senast angivna värdet: den läggs till i deras profil: Se [Lagra data i databasen](#storing-data-in-the-database).

* **[!UICONTROL Variable]**

   Om du inte vill lagra information i databasen kan du använda en variabel. Lokala variabler kan deklareras uppströms. Se [Lagra data i en lokal variabel](#storing-data-in-a-local-variable).

### Lagra data i databasen {#storing-data-in-the-database}

Om du vill spara data i ett befintligt fält i databasen klickar du på ikonen **[!UICONTROL Edit expression]** och väljer den i listan med tillgängliga fält.

![](assets/s_ncs_admin_survey_storage_type1.png)

>[!NOTE]
>
>Standardreferensdokumentet är schemat **nms:receive**. Om du vill visa det eller välja ett nytt, markerar du formuläret i listan och klickar på knappen **[!UICONTROL Properties]**.

### Lagra data i en lokal variabel {#storing-data-in-a-local-variable}

Du kan använda lokala variabler så att även om data inte lagras i databasen kan de återanvändas på sidan eller de andra sidorna, till exempel för att placera villkor på visningen av ett fält eller för att anpassa ett meddelande.

Det innebär att du kan använda värdet för ett osparat fält för att godkänna visningen av en grupp alternativ på sidan. På sidan nedan lagras fordonstypen inte i databasen:

![](assets/s_ncs_admin_survey_no_storage_variable.png)

Den lagras i en variabel som måste markeras när listrutan skapas, eller via länken **[!UICONTROL Edit storage...]**.

![](assets/s_ncs_admin_survey_no_storage_variable2.png)

Du kan visa befintliga variabler och skapa nya via länken **[!UICONTROL Edit variables...]**. Klicka på knappen **[!UICONTROL Add]** för att skapa en ny variabel.

![](assets/s_ncs_admin_survey_add_a_variable.png)

Den tillagda variabeln är tillgänglig i listan med lokala variabler när sidans inmatningsfält skapas.

>[!NOTE]
>
>För varje formulär kan du skapa variabler uppströms. Om du vill göra det markerar du formuläret och klickar på knappen **[!UICONTROL Properties]**. Fliken **[!UICONTROL Variables]** innehåller de lokala variablerna för formuläret.

**Exempel på lokal lagring med konditionering**

I exemplet ovan visas behållaren som innehåller data om privata fordon endast om alternativet **[!UICONTROL Private]** väljs i listrutan, vilket anges i synlighetsvillkoret:

![](assets/s_ncs_admin_survey_add_a_condition.png)

Om användaren väljer ett privat fordon finns följande alternativ i webbformuläret:

![](assets/s_ncs_admin_survey_no_storage_conda.png)

Behållaren som innehåller uppgifter om nyttofordon visas om alternativet Professional väljs, uttryckt i synlighetsvillkoret:

![](assets/s_ncs_admin_survey_view_a_condition.png)

Detta innebär att om användaren väljer ett nyttofordon, erbjuder formuläret följande alternativ:

![](assets/s_ncs_admin_survey_no_storage_condb.png)

## Använda insamlad information {#using-collected-information}

För varje formulär kan svaren återanvändas i fälten eller etiketterna. Följande syntaxer måste användas:

* För innehåll som lagras i ett fält i databasen:

   ```
   <%=ctx.recipient.@field name%
   ```

* För innehåll som lagras i en lokal variabel:

   ```
   <%= ctx.vars.variable name %
   ```

* För innehåll som lagras i ett HTML-textfält:

   ```
   <%== HTML field name %
   ```

   >[!NOTE]
   >
   >Till skillnad från andra fält där `<%=`-tecken ersätts med escape-tecken, sparas HTML-innehållet som det är med syntaxen `<%==`.

## Sparar svar på webbformulär {#saving-web-forms-answers}

Om du vill spara den information som samlas in på sidorna i ett formulär måste du placera en lagringsruta i diagrammet.

![](assets/s_ncs_admin_survey_save_box.png)

Det finns två sätt att använda den här rutan:

* Om webbformuläret nås via en länk som skickas i ett e-postmeddelande, och om användaren som använder programmet redan finns i databasen, kan du markera alternativet **[!UICONTROL Update the preloaded record]**. Mer information finns i [Leverera ett formulär via e-post](../../web/using/publishing-a-web-form.md#delivering-a-form-via-email).

   I det här fallet använder Adobe Campaign den krypterade primärnyckeln för användarprofilen, som är en unik identifierare som tilldelas varje profil av Adobe Campaign. Du måste konfigurera informationen så att den kan läsas in i förväg via förinläsningsrutan. Mer information finns i [Förhandsladda formulärdata](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

   >[!CAUTION]
   >
   >Det här alternativet åsidosätter användardata, inklusive e-postadressen om det finns ett fält där de ska anges. Den kan inte användas för att skapa nya profiler och kräver en förinläsningsruta i formuläret.

* Om du vill utöka data för mottagare i databasen redigerar du lagringsrutan och väljer avstämningsnyckeln. För intern användning (vanligtvis ett intranätsystem) eller för ett formulär som används för att skapa nya profiler, till exempel, kan du välja avstämningsfält. I rutan finns alla fält i databasen som används på de olika sidorna i webbprogrammet:

   ![](assets/s_ncs_admin_survey_save_box_edit.png)

Som standard importeras data till databasen med en **[!UICONTROL Update or insertion]**-åtgärd: om det finns i databasen uppdateras elementet (till exempel det valda nyhetsbrevet eller den e-postadress som har angetts). Om den inte finns läggs informationen till.

Du kan dock ändra det här beteendet. Det gör du genom att markera elementets rot och välja den åtgärd som ska utföras i listrutan:

![](assets/s_ncs_admin_survey_save_operation.png)

Du kan välja en sökmapp för avstämning och skapandemappen för nya profiler. Om dessa fält är tomma söks profilerna igenom och skapas i operatorns standardmapp.

>[!NOTE]
>
>Möjliga åtgärder är: **[!UICONTROL Simple reconciliation]**, **[!UICONTROL Update or insertion]**, **[!UICONTROL Insertion]**, **[!UICONTROL Update]**, **[!UICONTROL Deletion]**.\
>Operatorns standardmapp är den första mappen som operatorn har skrivbehörighet för.\
>Se [det här avsnittet](../../platform/using/access-management.md).
