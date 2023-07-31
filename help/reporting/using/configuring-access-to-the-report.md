---
product: campaign
title: Konfigurera åtkomst till rapporten
description: Konfigurera åtkomst till rapporten
feature: Reporting, Monitoring
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
exl-id: 1e5ab922-481c-4dce-a05e-a58408002e24
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 2%

---

# Konfigurera åtkomst till rapporten{#configuring-access-to-the-report}



## Rapportens visningssammanhang {#report-display-context}

Definiera rapportens visningssammanhang på Adobe Campaign-plattformen med **[!UICONTROL Display]** -fliken. Åtkomsten till en rapport beror på dess urvalstyp, visningsvillkor och åtkomstauktoriseringar.

### Markeringstyp {#selection-type}

Åtkomsten till rapporten kan begränsas till ett specifikt sammanhang eller ett visst utrymme för erbjudandet, t.ex. en leverans, en mottagare, ett urval av mottagare. Den här åtkomsten har konfigurerats i **[!UICONTROL Selection type]** i **[!UICONTROL Display]** -fliken.

![](assets/s_ncs_advuser_report_visibility_4.png)

* **[!UICONTROL Single selection]** : rapporten är bara tillgänglig när en viss enhet har valts.
* **[!UICONTROL Multiple selection]** : rapporten nås när flera enheter har valts.
* **[!UICONTROL Global]** : rapporten hämtas via en lista över tillgängliga rapporter i **[!UICONTROL Reports]** -fliken.

### Visningssekvens {#display-sequence}

The **[!UICONTROL Sequence]** I kan du ange ett numeriskt värde som anger rapportens visningssekvens i listan.

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

Om du vill göra rapporten tillgänglig väljer du **[!UICONTROL Report shared with other operators]** alternativ. Om det här alternativet inte är markerat kan bara den operator som skapade rapporten få åtkomst till rapporten.

Rapporten kan också delas med specifika operatorer eller grupper av operatorer som läggs till via tillståndsfönstret.

![](assets/s_ncs_advuser_report_visibility_8.png)

### Definiera filtreringsalternativen {#defining-the-filtering-options}

The **[!UICONTROL Reports]** På -fliken visas alla tillgängliga rapporter på plattformen som den anslutna operatorn har åtkomstbehörighet till.

Som standard sorteras de efter relevans, men du kan använda andra typer av filter: i bokstavsordning, efter ålder, osv.

Du kan även filtrera visningen baserat på rapportkategorin:

![](assets/report_ovv_select_type.png)

Om du vill definiera kategorin för en rapport väljer du den via **[!UICONTROL Display]** enligt nedan:

![](assets/report_select_category.png)

Du kan ange en ny kategori här och lägga till den i listan över tillgängliga kategorier. Den matchande uppräkningen uppdateras automatiskt.

## Skapa en länk till en rapport {#creating-a-link-to-a-report-}

Det går att göra en rapport tillgänglig via en viss nod i trädet, som en lista, en mottagare, en leverans osv. Det gör du genom att skapa en länk till den aktuella rapporten och ange den enhet där du vill göra den tillgänglig.

Vi ska till exempel skapa en länk till en rapport som gör den tillgänglig via en lista över mottagare.

1. Klicka **[!UICONTROL New]** och markera **[!UICONTROL Create a link to an existing report]** i guiden för att skapa rapporter.

   ![](assets/s_ncs_advuser_report_wizard_link_01.png)

1. Välj den rapport som du vill skapa en länk till med hjälp av listrutan. I det här exemplet ska vi välja **Uppdelning per land** rapport.

   ![](assets/s_ncs_advuser_report_wizard_link_02.png)

1. Ange en etikett och välj schemat. I det här exemplet ska vi välja tabellen med mottagarlistor.

   ![](assets/s_ncs_advuser_report_wizard_link_03.png)

   Det innebär att rapporten kommer att vara tillgänglig via en mottagarlista och att statistiken kommer att beröra mottagarna i den valda listan.

1. Spara och visa rapporten.
1. Ange länknyckeln. I det här fallet sekundärnyckeln för länken &quot;Mappar&quot;.

   ![](assets/s_ncs_advuser_report_wizard_link_04.png)

1. Publicera rapporten.
1. Gå till en av mottagarlistorna och klicka på **[!UICONTROL Reports]** länk: den rapport du just har skapat är tillgänglig.

   ![](assets/s_ncs_advuser_report_wizard_link_05.png)

## Förhandsgranskning av rapporten {#preview-of-the-report}

Innan du publicerar rapporten bör du kontrollera att den visas korrekt i **[!UICONTROL Preview]** -fliken.

![](assets/s_ncs_advuser_report_preview_01.png)

Om du vill visa en förhandsgranskning av rapporten väljer du **[!UICONTROL Global]** eller **[!UICONTROL Selection]** alternativ.

Dessa två alternativ väljs baserat på rapportens visningsinställningar. Om visningsinställningen är **[!UICONTROL Global]** måste du välja **[!UICONTROL Global]** förhandsvisningsalternativ. Om visningsinställningarna är **[!UICONTROL Single selection]** eller **[!UICONTROL Multiple selection]**, **[!UICONTROL Selection]** Förhandsvisningsalternativet måste vara markerat.

Mer information finns i [Rapportens visningssammanhang](#report-display-context).

Med specifika inställningar kan du kontrollera fel. The **uuuid** -inställningen finns i rapportens URL. Du kan lägga till **&amp;_preview** eller **&amp;_debug** inställningar.

Mer information om de här inställningarna finns i **Definiera egenskaper för webbformulär** i [Webbformulär](../../web/using/about-web-forms.md) kapitel.

## Publicera rapporten {#publishing-the-report}

Det är obligatoriskt att publicera rapporten för att dela den med andra operatorer och visa den i listan över tillgängliga rapporter (se även [Rapportens visningssammanhang](#report-display-context)). Denna åtgärd måste utföras igen varje gång rapporten ändras.

1. Öppna publiceringsguiden genom att klicka **[!UICONTROL Publish]** i verktygsfältet.

   ![](assets/s_ncs_advuser_report_publish_01.png)

1. Klicka **[!UICONTROL Start]** att publicera.

   ![](assets/s_ncs_advuser_report_publish_02.png)

1. Klicka på **[!UICONTROL Enlarge]** om du vill öppna rapporten i en webbläsare.
