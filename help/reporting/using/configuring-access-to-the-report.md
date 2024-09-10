---
product: campaign
title: Konfigurera åtkomst till rapporten
description: Konfigurera åtkomst till rapporten
feature: Reporting, Monitoring
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
exl-id: 1e5ab922-481c-4dce-a05e-a58408002e24
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 1%

---

# Konfigurera åtkomst till rapporten{#configuring-access-to-the-report}



## Rapportens visningssammanhang {#report-display-context}

Definiera rapportens visningssammanhang på Adobe Campaign-plattformen med fliken **[!UICONTROL Display]**. Åtkomsten till en rapport beror på dess urvalstyp, visningsvillkor och åtkomstauktoriseringar.

### Markeringstyp {#selection-type}

Åtkomsten till rapporten kan begränsas till ett specifikt sammanhang eller ett visst utrymme för erbjudandet, t.ex. en leverans, en mottagare, ett urval av mottagare. Den här åtkomsten har konfigurerats i avsnittet **[!UICONTROL Selection type]** på fliken **[!UICONTROL Display]**.

![](assets/s_ncs_advuser_report_visibility_4.png)

* **[!UICONTROL Single selection]** : rapporten är bara tillgänglig när en specifik entitet har valts.
* **[!UICONTROL Multiple selection]** : rapporten nås när flera entiteter har valts.
* **[!UICONTROL Global]** : rapporten nås via listan med tillgängliga rapporter på fliken **[!UICONTROL Reports]**.

### Visningssekvens {#display-sequence}

I fältet **[!UICONTROL Sequence]** kan du ange ett numeriskt värde som anger rapportens visningssekvens i listan.

Som standard visas rapporter efter relevans: med det värde som anges i det här fältet kan du sortera rapporter från det högsta (högsta värdet) till det minsta (minsta värdet) som är relevant.

Du kan välja vilken skala som ska användas baserat på dina behov: 1 till 10, 0 till 100, -10 till 10 osv.

### Visningsvillkor {#display-conditions}

Du kan även ställa in hur rapporten ska visas via en fråga.

![](assets/s_ncs_advuser_report_visibility_5.png)

I följande exempel visas rapporten om huvudkampanjkanalen är e-post.

![](assets/s_ncs_advuser_report_visibility_6.png)

Det innebär att om kampanjens huvudkanal är direktreklam kommer rapporten inte att vara tillgänglig i kampanjrapporterna.

### Åtkomstbehörighet {#access-authorization}

Rapporten kan delas med andra operatorer.

Markera alternativet **[!UICONTROL Report shared with other operators]** om du vill att rapporten ska vara tillgänglig. Om det här alternativet inte är markerat kan bara den operator som skapade rapporten få åtkomst till rapporten.

Rapporten kan också delas med specifika operatorer eller grupper av operatorer som läggs till via tillståndsfönstret.

![](assets/s_ncs_advuser_report_visibility_8.png)

### Definiera filtreringsalternativen {#defining-the-filtering-options}

Fliken **[!UICONTROL Reports]** visar alla tillgängliga rapporter på plattformen och för vilka den anslutna operatorn har åtkomstbehörighet.

Som standard sorteras de efter relevans, men du kan använda andra typer av filter: i bokstavsordning, efter ålder, osv.

Du kan även filtrera visningen baserat på rapportkategorin:

![](assets/report_ovv_select_type.png)

Om du vill definiera kategorin för en rapport väljer du den på fliken **[!UICONTROL Display]** enligt nedan:

![](assets/report_select_category.png)

Du kan ange en ny kategori här och lägga till den i listan över tillgängliga kategorier. Den matchande uppräkningen uppdateras automatiskt.

## Skapa en länk till en rapport {#creating-a-link-to-a-report-}

Det går att göra en rapport tillgänglig via en viss nod i trädet, som en lista, en mottagare, en leverans osv. Det gör du genom att skapa en länk till den aktuella rapporten och ange den enhet där du vill göra den tillgänglig.

Vi ska till exempel skapa en länk till en rapport som gör den tillgänglig via en lista över mottagare.

1. Klicka på **[!UICONTROL New]** och välj **[!UICONTROL Create a link to an existing report]** i rapportskaparassistenten.

   ![](assets/s_ncs_advuser_report_wizard_link_01.png)

1. Välj den rapport som du vill skapa en länk till med hjälp av listrutan. I det här exemplet ska vi välja rapporten **Uppdelning efter land**.

   ![](assets/s_ncs_advuser_report_wizard_link_02.png)

1. Ange en etikett och välj schemat. I det här exemplet ska vi välja tabellen med mottagarlistor.

   ![](assets/s_ncs_advuser_report_wizard_link_03.png)

   Det innebär att rapporten kommer att vara tillgänglig via en mottagarlista och att statistiken kommer att beröra mottagarna i den valda listan.

1. Spara och visa rapporten.
1. Ange länknyckeln. I det här fallet sekundärnyckeln för länken &quot;Mappar&quot;.

   ![](assets/s_ncs_advuser_report_wizard_link_04.png)

1. Publish din rapport.
1. Gå till en av mottagarlistorna och klicka på länken **[!UICONTROL Reports]**: den rapport du just har skapat är tillgänglig.

   ![](assets/s_ncs_advuser_report_wizard_link_05.png)

## Förhandsgranskning av rapporten {#preview-of-the-report}

Innan du publicerar rapporten bör du kontrollera att den visas korrekt på fliken **[!UICONTROL Preview]**.

![](assets/s_ncs_advuser_report_preview_01.png)

Om du vill visa förhandsgranskningen av rapporten väljer du alternativet **[!UICONTROL Global]** eller **[!UICONTROL Selection]**.

Dessa två alternativ väljs baserat på rapportens visningsinställningar. Om visningsinställningen är **[!UICONTROL Global]** måste du välja förhandsvisningsalternativet **[!UICONTROL Global]**. Om visningsinställningarna är **[!UICONTROL Single selection]** eller **[!UICONTROL Multiple selection]** måste du välja alternativet **[!UICONTROL Selection]** för förhandsgranskning.

Mer information finns i [Rapportvisningssammanhang](#report-display-context).

Med specifika inställningar kan du kontrollera fel. Inställningen **_uid** finns i rapportens URL. Du kan lägga till inställningarna **&amp;_preview** eller **&amp;_debug** i den.

Mer information om de här inställningarna finns i avsnittet **Definiera webbformuläregenskaper** i kapitlet [Webbformulär](../../web/using/about-web-forms.md).

## Publish rapporten {#publishing-the-report}

Det är obligatoriskt att publicera rapporten för att dela den med andra operatorer och visa den i listan över tillgängliga rapporter (se även [Rapportvisningssammanhang](#report-display-context)). Denna åtgärd måste utföras igen varje gång rapporten ändras.

1. Öppna publiceringsassistenten genom att klicka på **[!UICONTROL Publish]** i verktygsfältet.

   ![](assets/s_ncs_advuser_report_publish_01.png)

1. Klicka på **[!UICONTROL Start]** för att publicera.

   ![](assets/s_ncs_advuser_report_publish_02.png)

1. Klicka på ikonen **[!UICONTROL Enlarge]** för att öppna rapporten i en webbläsare.
