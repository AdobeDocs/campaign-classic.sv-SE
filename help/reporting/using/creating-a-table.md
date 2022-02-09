---
product: campaign
title: Skapa en tabell
description: Skapa en tabell
exl-id: 05f76bdf-6dcd-4360-9e72-0ba6a4dd0d5e
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '2495'
ht-degree: 1%

---

# Skapa en tabell{#creating-a-table}

![](../../assets/common.svg)

Du kan lägga till en tabell i en rapport för att visa data. Detta kan vara en pivottabell som skapas baserat på kubmått, en lista med en grupp eller en tabell som innehåller en uppdelning av värden.

![](assets/s_advuser_report_page_activity_05.png)

## Skapa en lista med en grupp {#creating-a-list-with-group}

A **[!UICONTROL List with group]** Med typtabell kan du gruppera data i tabellen och producera statistik för den. Du kan t.ex. skapa summor och delsummor för data. Varje grupp har sin egen rubrik, detalj- och sidfotsrad.

>[!CAUTION]
>
>The **[!UICONTROL Page]** aktiviteten som innehåller tabellen måste föregås av en **[!UICONTROL Query]** eller **[!UICONTROL Script]** verksamhet för att samla in de uppgifter som ska analyseras i rapporten. Mer information om dessa aktiviteter finns i [Samla in data som ska analyseras](../../reporting/using/collecting-data-to-analyze.md) och [Skriptaktivitet](../../reporting/using/advanced-functionalities.md#script-activity).

### Verksamhetsprincip {#operating-principle}

Det kan hända att du måste analysera flera datakategorier samtidigt. Med en lista med grupper kan du kombinera data och skapa statistik för olika grupper av data i samma tabell. Det gör du genom att skapa en grupp i tabellen.

I följande exempel visar gruppen alla kampanjer i databasen, leveranser och antalet meddelanden som skickas per leverans och per kampanj.

Här kan ni lista kampanjerna (**[!UICONTROL Label (Campaign)]**, förteckningen över leveranser (**[!UICONTROL Label]** ) som är länkad till kampanjen och låter dig räkna antalet skickade meddelanden per leverans (**[!UICONTROL Processed)]** innan de läggs till för varje kampanj (**[!UICONTROL Sum(@processed)]** ).

![](assets/s_advuser_ergo_listgroup_005.png)

### Implementeringssteg {#implementation-steps}

Ett exempel på fullständig implementering finns här: [Användningsfall: Skapa en rapport med en grupplista](#use-case--create-a-report-with-a-group-list).

Observera följande steg för att skapa en List med group-typtabell:

1. Gå till rapportdiagrammet och placera en **[!UICONTROL Query]** aktivitet. Se [Samla in data som ska analyseras](../../reporting/using/collecting-data-to-analyze.md).
1. Fyll i källtabellen och markera fälten i tabellen som statistiken ska beröra.
1. Placera en **[!UICONTROL Page]** aktivitet i diagrammet. Mer information finns i [Statiska element](../../reporting/using/creating-a-new-report.md#static-elements).
1. Infoga en **[!UICONTROL List with group]** skriv tabellen på sidan.
1. Ange datasökvägen eller den tabell som har valts som datakälla i frågan.

   Det här steget är obligatoriskt om du vill återställa fälten i källtabellen senare och infoga dem i tabellens celler.

1. Skapa tabellen och dess innehåll.
1. Visa den färdigställda rapporten i **[!UICONTROL Preview]** -fliken. Du kan sedan publicera rapporten och exportera den till ett annat format om det behövs. Mer information finns i [Exportera en rapport](../../reporting/using/actions-on-reports.md#exporting-a-report).

### Lägga till rader och kolumner {#adding-lines-and-columns}

Som standard är **[!UICONTROL List with group]** texttabellen innehåller ett sidhuvud, en detaljrad och en sidfotsrad.

Själva gruppen innehåller rubrik-, detalj- och sidfotsrader.

* **Rubrikrad**: På den här raden kan du ge tabellkolumnerna en rubrik.

   ![](assets/s_advuser_ergo_listgroup_003a.png)

* **Detaljrad**: den här raden innehåller statistiska värden.

   ![](assets/s_advuser_ergo_listgroup_004.png)

* **Sidfotsrad**: På den här raden kan du visa de totala värdena.

   ![](assets/s_advuser_ergo_listgroup_003.png)

Linjer och kolumner kan läggas till efter behov.

Gruppen kan placeras på vilken rad som helst i tabellen och innehåller egna huvud-, detalj- och sidfotsrader.

![](assets/s_advuser_ergo_listgroup_019.png)

**Linje och kolumn**: Om du vill lägga till eller ta bort en rad eller en kolumn går du till en befintlig rad eller kolumn och använder högerklicksmenyn.

![](assets/s_advuser_ergo_listgroup_006.png)

Vilken typ av rad du lägger till beror på var markören är placerad. Om du till exempel vill lägga till en rubrikrad placerar du markörerna i en rubrik och klickar sedan på **[!UICONTROL Add > A line above/below]**.

![](assets/s_advuser_ergo_listgroup_006a.png)

Bredden på kolumnerna kan ändras via **[!UICONTROL Column format]** objekt.

**Grupp**: Om du vill lägga till en grupp går du till en rad och väljer matchande alternativ i listrutan.

![](assets/s_advuser_ergo_listgroup_007.png)

### Definiera cellinnehåll {#defining-cell-content}

Om du vill redigera en cell i tabellen och definiera dess innehåll och format går du till cellen och använder högerklicksmenyn.

Använd **[!UICONTROL Expression]** menyalternativ för att välja vilka värden som ska visas.

![](assets/s_advuser_ergo_listgroup_010.png)

* Om du vill infoga värdena som ska analyseras direkt i tabellen markerar du dem bland de tillgängliga fälten.

   Listan med tillgängliga fält sammanfaller med innehållet i frågan före tabellen i rapportkonstruktionsdiagrammet.

   ![](assets/s_advuser_ergo_listgroup_011.png)

* Ange en etikett för en cell, till exempel rubrikens.

   Om du vill göra det använder du samma process som när du infogar ett fält i databasen, men markerar inget uttryck. Ange etiketten i dialogrutan **[!UICONTROL Label]** fält. Den visas som den är.

* Beräkna ett aggregat (ett genomsnitt, en summa osv.) och visa den i cellen.

   Om du vill göra det använder du **[!UICONTROL Aggregates]** menyalternativ och välj önskad kampanj.

   ![](assets/s_advuser_ergo_listgroup_008.png)

### Definiera cellformat {#defining-cell-format}

![](assets/s_advuser_ergo_listgroup_017.png)

Om du vill definiera cellformatet väljer du **[!UICONTROL Cell format...]** kan du använda alla formateringsalternativ som är tillgängliga för den markerade cellen.

Med dessa alternativ kan du anpassa den slutliga återgivningen av rapporten och göra det enklare att läsa information.

Använd **[!UICONTROL Carriage return]** fält vid export av data till Excel: välj **[!UICONTROL Yes]** värde för att framtvinga vagnreturen. Detta värde behålls vid export. Mer information finns i [Exportera en rapport](../../reporting/using/actions-on-reports.md#exporting-a-report).

The **[!UICONTROL Cell format]** -fönstret ger dig åtkomst till följande flik:

* The **[!UICONTROL Value]** tab
* The **[!UICONTROL Borders]** tab
* The **[!UICONTROL Click]** tab
* The **[!UICONTROL Extra]** tab

The **[!UICONTROL Value]** Med -fliken kan du ändra teckensnitt och olika värdeattribut eller definiera ett format baserat på deras karaktär.

![](assets/s_advuser_ergo_listgroup_009.png)

Formatet ändrar visningen av data: till exempel **[!UICONTROL Number]**, **[!UICONTROL Monetary]** och **[!UICONTROL Percentage]** Med kan du justera siffrorna till höger och visa decimalpunkter.

Exempel på hur du konfigurerar ett valutaformat: Du kan ange i vilken valuta värdena ska uttryckas, välja om du vill separera tusentals och visa negativa värden i rött. Valutasymbolens position beror på vilket språk operatorn har i sin profil.

![](assets/s_advuser_ergo_listgroup_012.png)

Konfigurationsexempel för datum: du kan välja om du vill visa tiden eller inte.

![](assets/s_advuser_ergo_listgroup_013.png)

The **Kantlinjer** Med -fliken kan du lägga till kantlinjer i rader och kolumner i tabellen. Om du lägger till kantlinjer i cellerna kan det leda till prestandaproblem när du exporterar stora rapporter till Excel.

![](assets/s_advuser_ergo_listgroup_014.png)

Om det behövs kan du definiera kantlinjer i tabellmallen (**[!UICONTROL Administration > Configuration > Form rendering]** ).

I det här fallet har du följande syntax:

På fliken Webb:

```
 .tabular td {
 border: solid 1px #000000;
 }
```

På fliken Excel:

```
 <style name="odd" fillColor="#fdfdfd">
  <border>
   <borderTop value="solid 0.05pt #000000" />
   <borderBottom value="solid 0.05pt #000000" />
   <borderLeft value="solid 0.05pt #000000" />
   <borderRight value="solid 0.05pt #000000" />
  </border>
 </style> 
 
 <style name="even" fillColor="#f7f8fa">
  <border>
   <borderTop value="solid 0.05pt #000000" />
   <borderBottom value="solid 0.05pt #000000" />
   <borderLeft value="solid 0.05pt #000000" />
   <borderRight value="solid 0.05pt #000000" />
  </border>
 </style> 
```

The **[!UICONTROL Click]** kan du definiera en åtgärd när användaren klickar på innehållet i en cell eller i tabellen.

I exemplet nedan kan du klicka på värdet i cellen för att visa den andra sidan i rapporten: den kommer att innehålla information om leveransen i cellen.

![](assets/s_advuser_ergo_listgroup_015.png)

The **Extra** kan du länka en visuell bild till dina data, t.ex. en färgmarkering eller ett värdefält. Färgmarkeringen används när tabellen visas som en förklaring i ett diagram. Mer information finns i implementeringsexemplet: [Steg 5 - Skapa den andra sidan](#step-5---create-the-second-page)

![](assets/s_advuser_ergo_listgroup_016.png)

## Användningsfall: Skapa en rapport med en grupplista {#use-case--create-a-report-with-a-group-list}

I det här exemplet ska vi skapa en tvåsidig rapport: den första sidan innehåller listan och de totala leveranserna per kampanj samt antalet skickade meddelanden. Leveransnamnen är klickbara länkar och du kan gå vidare till den andra sidan av rapporten för att visa fördelningen av leveranser per e-postdomän för den valda leveransen med en tabell och ett diagram. På den andra sidan fungerar tabellen som förklaring för diagrammet.

![](assets/reporting_quick_start_report-final.png)

### Steg 1 - Skapa en rapport {#step-1---create-a-report}

Skapa en ny rapport om kampanjschemat, **[!UICONTROL Campaigns (nms)]**.

![](assets/s_advuser_report_listgroup_001.png)

Klicka **[!UICONTROL Save]** för att skapa rapporten.

Gå till diagrammet och lägg till de första komponenterna som ska användas för att utforma rapportinnehållet: en första fråga och en första sida.

![](assets/reporting_quick_start_diagram.png)

### Steg 2 - Skapa den första frågan {#step-2---create-the-first-query}

Med den första frågan kan ni samla in leveranser som är länkade till varje kampanj. Målet är att visa en rapport om de olika leveranserna av Adobe Campaign-databasen som är länkad till varje kampanj.

Dubbelklicka på den första frågan för att redigera den och använd sedan följande steg för att konfigurera den:

1. Börja med att ändra schemat som frågans källa ska användas på: välj **[!UICONTROL Deliveries (nms)]** schema.
1. Klicka på **[!UICONTROL Edit query]** länka och visa de avancerade fälten.

   ![](assets/reporting_quick_start_query-1.png)

1. Markera följande fält:

   * Leveransetiketten.
   * Leveransens primärnyckel.
   * kampanjetiketten,
   * Indikatorn för bearbetade leveranser.
   * den utländska nyckeln för Campaign-länken,
   * Indikatorn för felfrekvens.

   ![](assets/s_advuser_report_listgroup_002.png)

   Länka ett alias till varje fält: Vi rekommenderar att du gör det enklare att välja data från tabellen som ska läggas till på rapportens första sida.

   I det här exemplet använder vi följande alias:

   * Etikett: **@label**
   * Primär nyckel: **@deliveryId**
   * Etikett (Campaign): **@label1**
   * Behandlad: **@bearbetad**
   * Sekundärnyckel för länken&quot;Campaign&quot; (ID-fält): **@operationId**
   * Felfrekvens: **@errorRatio**


1. Klicka på **[!UICONTROL Next]** två gånger för att komma till **[!UICONTROL Data filtering]** steg.

   Lägg till ett filtreringsvillkor om du bara vill samla in de leveranser som är kopplade till en kampanj.

   Syntaxen för det här filtret är följande: &quot;Sekundärnyckel för länken &#39;Campaigns&#39; som är större än 0&quot;.

   ![](assets/reporting_quick_start_query_filter.png)

1. Klicka **[!UICONTROL Finish]** om du vill spara dessa villkor klickar du på **[!UICONTROL Ok]** för att stänga frågeredigeraren.

### Steg 3: Skapa den första sidan {#step-3--create-the-first-page}

I det här steget ska vi konfigurera den första sidan i rapporten. Så här konfigurerar du den:

1. Öppna **[!UICONTROL Page]** aktivitet och ange dess titel, till exempel **Leveranser** i detta fall.

   ![](assets/s_advuser_report_listgroup_003.png)

1. Infoga en lista med grupper via verktygsfältet och ange dess etikett, till exempel: Lista över leveranser per kampanj.

   ![](assets/s_advuser_report_listgroup_004.png)

1. Klicka på **[!UICONTROL Table data XPath...]** och välj leveranslänk, dvs. `[query/delivery]`.

   ![](assets/s_advuser_report_listgroup_005.png)

1. Klicka på **[!UICONTROL Data]** och ändra tabellens layout: lägg till tre kolumner till höger.

   ![](assets/s_advuser_report_listgroup_006.png)

1. Lägg till en grupp.

   ![](assets/s_advuser_report_listgroup_008.png)

   Med den här gruppen kan ni gruppera kampanjer och de leveranser som är kopplade till dem.

1. I gruppfönstret refererar du till **Sekundärnyckel för Campaign-länken** och stänger fönstret.

   ![](assets/s_advuser_report_listgroup_007.png)

1. Redigera den första cellen i grupprubriken och infoga **[!UICONTROL Label]** kampanjfält som ett uttryck.

   ![](assets/s_advuser_report_listgroup_009.png)

1. Redigera den andra cellen på informationsraden och välj leveranser **[!UICONTROL Label]**.

   ![](assets/s_advuser_report_listgroup_011.png)

1. Redigera cellens format och öppna **[!UICONTROL Click]** -fliken. Konfigurera lämpliga alternativ så att den öppnas i samma fönster när användaren klickar på namnet på en leverans.

   ![](assets/s_advuser_report_listgroup_0111.png)

   Välj en **[!UICONTROL Next page]** typåtgärd och markera **[!UICONTROL In the same window]** som ett öppet alternativ.

   ![](assets/s_advuser_report_listgroup_0112.png)

1. Klicka på i fönstrets nedre del **[!UICONTROL Add]** och ange **`/vars/selectedDelivery`** bana och **[!UICONTROL @deliveryId]** uttryck som matchar aliaset för leveransens primärnyckel, enligt definitionen i den fråga som skapades tidigare. Med den här formeln kan du komma åt den valda leveransen.

   ![](assets/s_advuser_report_listgroup_010.png)

1. Redigera den andra cellen i gruppens sidfotsrad och ange **[!UICONTROL Total per campaign]** som en etikett.

   ![](assets/s_advuser_report_listgroup_012.png)

1. Redigera den tredje cellen i gruppens rubrikrad och ange **[!UICONTROL Number of messages sent]** som en etikett.

   ![](assets/s_advuser_report_listgroup_013.png)

   Den här informationen sammanfaller med kolumnrubriken.

1. Redigera den tredje cellen på detaljraden och välj den bearbetade meddelandeindikatorn som ett uttryck.

   ![](assets/s_advuser_report_listgroup_014.png)

1. Redigera den tredje cellen i sidfotsraden i gruppen, markera indikatorn för bearbetad leverans och tillämpa kommandot **[!UICONTROL Sum]** aggregera till den.

   ![](assets/s_advuser_report_listgroup_015.png)

1. Redigera den fjärde cellen på detaljraden och markera **felfrekvens vid felleverans** som ett uttryck.

   ![](assets/s_advuser_report_listgroup_016.png)

1. Markera den här cellen om du vill visa ett värdefält som representerar leveransfelprocenten.

   Det gör du genom att gå till cellformatet och sedan gå till **[!UICONTROL More]** -fliken. Välj **[!UICONTROL Value bar]** i listrutan och välj **[!UICONTROL Hide the cell value]** alternativ.

   ![](assets/s_advuser_report_listgroup_023.png)

   Nu kan du visa en återgivning av rapporten. Klicka på **[!UICONTROL Preview]** och väljer **[!UICONTROL Global]** alternativ: Här visas en lista över alla leveranser i Adobe Campaign-databasen som är länkade till en kampanj.

   ![](assets/s_advuser_report_listgroup_025.png)

   Vi rekommenderar att du använder **[!UICONTROL Preview]** för att säkerställa att data i tabellen är korrekt markerade och konfigurerade. När du är klar kan du fortsätta formatera tabellen.

1. Använd **[!UICONTROL Bold]** formatera cellerna som visar det totala antalet per kampanj och det totala antalet bearbetade meddelanden.

   ![](assets/s_advuser_report_listgroup_024.png)

1. Klicka på den första cellen i grupprubrikraden, den som visar kampanjnamnet, och välj **[!UICONTROL Edit > Merge to right]**.

   ![](assets/s_advuser_report_listgroup_026.png)

   Om du sammanfogar de två första cellerna i grupprubrikraden justeras kampanjtiteln och listan över leveranser som är länkade till den på nytt.

   ![](assets/s_advuser_report_listgroup_027.png)

   >[!CAUTION]
   >
   >Vi rekommenderar att du väntar tills rapporten har byggts innan du sammanfogar celler eftersom sammanfogningen är oåterkallelig.

### Steg 4 - Skapa den andra frågan {#step-4---create-the-second-query}

Vi vill lägga till en andra fråga och en andra sida för att visa detaljerna för en leverans när rapportanvändaren klickar på den. Innan du lägger till frågan redigerar du sidan som du har skapat och aktiverar den utgående övergången så att den kan länkas till frågan.

1. Lägg till en ny fråga efter **[!UICONTROL Page]** och redigera schemat: välj **[!UICONTROL Recipient delivery logs]** schema.

   ![](assets/reporting_quick_start_query-2.png)

1. Redigera frågan och definiera utdatakolumner. Om du vill visa antalet leveranser per e-postdomän måste du:

   * beräkna summan av primärnycklar för att räkna antalet leveransloggar:

      ![](assets/reporting_quick_start_query-2_count.png)

   * samla in mottagarnas e-postdomäner och gruppinformation om detta fält: för att göra detta väljer du **[!UICONTROL Group]** i domännamnskolumnen.

   ![](assets/reporting_quick_start_query-2_filter.png)

   Länka följande alias till fälten:

   * count(primär nyckel): **@count**
   * E-postdomän (mottagare): **@domän**

      ![](assets/reporting_quick_start_query-2_alias.png)


1. Klicka på **[!UICONTROL Next]** två gånger: det här tar dig till **[!UICONTROL Data filtering]** steg.

   Lägg till ett filtreringsvillkor om du bara vill samla in den information som är länkad till den valda leveransen.

   Syntaxen är följande: Sekundärnyckeln för länken &#39;Leverans&#39; är lika med värdet för inställningen `$([vars/selectedDelivery])`

   ![](assets/s_advuser_report_listgroup_017.png)

1. Stäng frågekonfigurationsfönstret och lägg till en sida i diagrammet, precis efter den andra frågan.

### Steg 5 - Skapa den andra sidan {#step-5---create-the-second-page}

1. Redigera sidan och ange dess etikett: **E-postdomäner**.
1. Avmarkera **[!UICONTROL Enable output transitions]** alternativ: detta är sista sidan i rapporten och kommer inte att följas av någon annan aktivitet.

   ![](assets/s_advuser_report_listgroup_028.png)

1. Lägg till en ny lista med en grupp med högerklicksmenyn och kalla den **E-postdomäner per mottagare**.
1. Klicka på **[!UICONTROL Table data XPath...]** och väljer **[!UICONTROL Recipient delivery logs]** länk.

   ![](assets/s_advuser_report_listgroup_029.png)

1. I **[!UICONTROL Data]** anpassar du tabellen enligt följande:

   * Lägg till två kolumner till höger.
   * Lägg till **[!UICONTROL rowNum()-1]** -uttryck för att räkna antalet rader. Ändra sedan cellens format: i **[!UICONTROL Extra]** flik, välja **[!UICONTROL Color tab]** och klicka **[!UICONTROL Ok]**.

      ![](assets/s_advuser_report_listgroup_018.png)

      Med den här konfigurationen kan du använda tabellen som bildtext för diagrammet.

   * Lägg till **[!UICONTROL Email domain(Recipient)]** -uttryck.
   * Lägg till **[!UICONTROL count(primary key)]** -uttryck.

   ![](assets/s_advuser_report_listgroup_019.png)

1. Lägg till ett cirkeldiagram på sidan med högerklicksmenyn och tilldela **E-postdomäner** etikett. Mer information finns i [Diagramtyper och varianter](../../reporting/using/creating-a-chart.md#chart-types-and-variants).
1. Klicka på **[!UICONTROL Variants]** och avmarkera **[!UICONTROL Display label]** och **[!UICONTROL Display caption]** alternativ.
1. Kontrollera att ingen värdesortering har konfigurerats. Mer information om detta finns i [det här avsnittet](../../reporting/using/processing-a-report.md#configuring-the-layout-of-a-descriptive-analysis-report).

   ![](assets/s_advuser_report_listgroup_0191.png)

1. I **[!UICONTROL Data]** ändrar du datakälla på fliken: välj **[!UICONTROL Context data]** i listrutan.

   ![](assets/s_advuser_report_listgroup_020.png)

1. Klicka sedan på **[!UICONTROL Advanced settings]** och välj länken till mottagarens leveransloggar.

   ![](assets/s_advuser_report_listgroup_0201.png)

1. I **[!UICONTROL Chart type]** väljer du **[!UICONTROL Email domain]** variabel.
1. Lägg sedan till den beräkning som ska utföras: markera summan som en operator.

   ![](assets/s_advuser_report_listgroup_0202.png)

1. Klicka på **[!UICONTROL Detail]** för att markera det fält som räkningen gäller och stänga sedan konfigurationsfönstret.

   ![](assets/s_advuser_report_listgroup_030.png)

1. Spara rapporten.

   Sidan är nu konfigurerad.

### Steg 6 - Visa rapporten {#step-6---viewing-the-report}

Om du vill visa resultatet av den här konfigurationen klickar du på **[!UICONTROL Preview]** och väljer **[!UICONTROL Global]** alternativ.

Den första sidan i rapporten innehåller en lista över alla leveranser som ingår i databasen.

![](assets/s_advuser_report_listgroup_021.png)

Om du klickar på länken för någon av dessa leveranser visas ett diagram med uppdelningen av e-postdomäner för den här leveransen. Du är nu på andra sidan av rapporten och kan gå tillbaka till föregående sida genom att klicka på lämplig knapp.

![](assets/s_advuser_report_listgroup_022.png)

## Skapa ett detaljerat register eller pivottabell {#creating-a-breakdown-or-pivot-table}

Med den här tabelltypen kan du visa statistik som beräknas på data i databasen.

Konfigurationen för de här typerna av rapporter liknar den som används för den beskrivande analysguiden. Mer information finns på [den här sidan](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-quantitative-distribution-template).

Mer information om hur du skapar en pivottabell finns i [det här avsnittet](../../reporting/using/using-cubes-to-explore-data.md).
