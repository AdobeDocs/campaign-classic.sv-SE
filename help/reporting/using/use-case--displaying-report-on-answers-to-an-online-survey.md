---
title: '"Användningsfall: visa rapport om svar på en nätundersökning"'
seo-title: '"Användningsfall: visa rapport om svar på en nätundersökning"'
description: '"Användningsfall: visa rapport om svar på en nätundersökning"'
seo-description: null
page-status-flag: never-activated
uuid: 2c0a5b7d-c606-4bcb-9600-8f89e6fce32a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: 5404a227-6cfb-463b-9a56-af46a022eb38
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Användningsfall: visa rapport om svar på en nätundersökning{#use-case-displaying-report-on-answers-to-an-online-survey}

Svar på Adobe Campaign-enkäter kan samlas in och analyseras med dedikerade rapporter.

I följande exempel vill vi samla in svar på en onlineundersökning och visa dem i en pivottabell

Använd följande steg:

1. Skapa ett arbetsflöde för att återskapa svar på enkäten och lagra dem i en lista.
1. Skapa en kub med hjälp av data i listan.
1. Skapa en rapport med pivottabellen och visa detaljerna för svaren.

Innan du börjar använda det här användningsexemplet måste du ha tillgång till en enkät och en uppsättning svar som du kan analysera.

>[!NOTE]
>
>Det här användningsexemplet kan bara implementeras om du har skaffat alternativet **Undersökningshanteraren** . Kontrollera licensavtalet.

## Steg 1 - Skapa arbetsflödet för datainsamling och lagring {#step-1---creating-the-data-collection-and-storage-workflow}

Så här samlar du in svaren på enkäten:

1. Skapa ett arbetsflöde och placera en **[!UICONTROL Answers to a survey]** aktivitet. Mer information om hur du använder den här aktiviteten finns i [det här avsnittet](../../web/using/publish--track-and-use-collected-data.md#using-the-collected-data).
1. Redigera aktiviteten och välj den undersökning vars svar du vill analysera.
1. Aktivera alternativet **[!UICONTROL Select all the answer data]** att samla in all information.

   ![](assets/reporting_usecase_1_01.png)

1. Markera de kolumner som ska extraheras (i det här fallet: välj: alla arkiverade fält. Det här är fälten som innehåller svaren.

   ![](assets/reporting_usecase_1_02.png)

1. När svarssamlingsrutan har konfigurerats placerar du en **[!UICONTROL List update]** typaktivitet för att spara data.

   ![](assets/reporting_usecase_1_04.png)

   I den här aktiviteten anger du listan som ska uppdateras och avmarkerar **[!UICONTROL Purge and re-use the list if it exists (otherwise add to the list)]** alternativet: svaren läggs till i den befintliga tabellen. Med det här alternativet kan du referera till listan i en kub. Schemat som är länkat till listan genereras inte om för varje uppdatering, vilket garanterar integriteten för kuben som använder den här listan.

   ![](assets/reporting_usecase_1_03.png)

1. Starta arbetsflödet för att bekräfta dess konfiguration.

   ![](assets/reporting_usecase_1_05.png)

   Den angivna listan skapas och innehåller schemat för svaren på enkäten.

1. Lägg till en schemaläggare för att automatisera den dagliga samlingen av svar och uppdateringen av listan.

   Verksamheterna **[!UICONTROL List update]** och **[!UICONTROL Scheduler]** verksamheterna beskrivs närmare i .

## Steg 2 - Skapa kuben, dess mått och indikatorer {#step-2---creating-the-cube--its-measures-and-its-indicators}

Sedan kan du skapa kuben och konfigurera dess mått: De kommer att användas för att skapa de indikatorer som kommer att visas i rapporten. Mer information om hur du skapar och konfigurerar kuber finns i [Om kuber](../../reporting/using/about-cubes.md).

I det här exemplet baseras kuben på data i listan som matats av det arbetsflöde som skapats tidigare.

![](assets/reporting_usecase_2_01.png)

Definiera måtten och måtten som ska visas i rapporten. Här vill vi visa avtalsdatumet och svarandens land.

![](assets/reporting_usecase_2_02.png)

På fliken **[!UICONTROL Preview]** kan du styra rapportens återgivning.

## Steg 3 - Skapa rapporten och konfigurera datalayouten i tabellen {#step-3---creating-the-report-and-configuring-the-data-layout-within-the-table}

Du kan sedan skapa en rapport baserad på den här kuben och bearbeta data och information.

![](assets/reporting_usecase_3_01.png)

Anpassa informationen efter behov.

![](assets/reporting_usecase_3_02.png)

