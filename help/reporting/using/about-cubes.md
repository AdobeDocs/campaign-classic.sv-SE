---
product: campaign
title: Kom igång med kuber
description: Kom igång med kuber
feature: Reporting
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 11%

---

# Kom igång med kuber{#about-cubes}

![](../../assets/common.svg)

Utforska data i databasen via **Marknadsföringsanalys** -modul. Det gör att ni kan analysera och mäta data, beräkna statistik, förenkla och optimera framtagning och beräkning av rapporter. Förutom detta kan ni med Marketing Analytics skapa rapporter och bygga upp målpopulationer. När de har identifierats lagras de i listor som kan användas i Adobe Campaign (målinriktning, segmentering osv.).

Kuber används för att generera vissa inbyggda rapporter, inklusive leveransrapporter (leveransspårning, klickningar, öppningar osv.). Rapporter som baseras på kuber får endast användas som standard för datavolymer under 5 miljoner faktarader.

Du kan utöka databasens undersöknings- och analyskapacitet samtidigt som det blir enklare för slutanvändarna att konfigurera rapporter och tabeller. Allt de behöver göra är att välja en befintlig (helt konfigurerad) kub när de skapar sin rapport eller tabell för att bearbeta beräkningar, mått och statistik.

När de har skapats och konfigurerats används kuber i frågeformulär för rapportering och webbapplikationer. De kan användas och ändras i pivottabeller.

>[!CAUTION]
>
>**Marknadsföringsanalys** är en Adobe Campaign-modul. Den måste installeras på din instans så att du kan använda de funktioner som beskrivs nedan.

Använd modulen Campaign Marketing Analytics för att:

1. Skapa kuber

   * sammanställa och lagra data i en arbetstabell för att på förhand beräkna indikatorer baserat på användarnas behov,
   * minska datavolymen i de olika beräkningar som används för rapporter och frågor, vilket avsevärt optimerar beräkningstiderna för indikatorn,
   * förenkla tillgången till data, göra det möjligt för användarna att hantera data (oavsett om de är i förväg aggregerade eller inte) beroende på olika dimensioner.

   Mer information finns i [Skapa indikatorer](../../reporting/using/creating-indicators.md).

1. Skapa pivottabeller

   * utforska beräknade data, konfigurerade mått,
   * välja vilka data som ska visas samt dess visningsläge,
   * personalisera de åtgärder och indikatorer som används,
   * erbjuder interaktiva analysverktyg till användare med icke-teknisk bakgrund.

   Mer information finns i [Använd kuber för att utforska data](../../reporting/using/using-cubes-to-explore-data.md).

1. Bygg en fråga med data som beräknas och aggregeras i en kub.
1. Identifiera populationer och referera till dem i listor.

## Terminologi {#terminology}

Specifika termer när du arbetar med kuber visas nedan.

* **Kub** - En kub är en representation av flerdimensionell information: ger slutanvändarna strukturer som utformats för interaktiv dataanalys.

* **Faktatabell/schema** - Faktatabellen (eller faktchemat) innehåller rådata eller elementära data som analyserna ska baseras på. Dessa är huvudsakligen stora volymtabeller (möjligen med länkade tabeller) med potentiellt långa beräkningar. En faktatabell kan till exempel vara: sändningstabellen, inköpstabellen osv.

* **Dimension** - Med Dimensioner kan du gruppera data i grupper: När de har skapats fungerar dimensionerna som analysaxlar. I de flesta fall definieras flera nivåer för en viss dimension. För en tidsdimension är nivåerna till exempel månader, dagar, timmar, minuter och så vidare. Den här nivåuppsättningen representerar dimensionshierarkin och möjliggör olika nivåer av dataanalys.

* **Bindning** - För vissa fält kan du definiera bindning till gruppvärden och göra det enklare att läsa information. Bindning används på nivåer. Vi rekommenderar att du definierar bindning när det kan finnas många olika värden.

* **Mät** - De vanligaste måtten är summa, genomsnitt, maximum, minimum, standardavvikelse osv. Mått kan beräknas: Antagandegraden för ett erbjudande är förhållandet mellan antalet gånger det presenterades och antalet gånger det accepterades.

## Arbetsytan Kub {#cube-workspace}

Kuber lagras i **[!UICONTROL Administration > Configuration > Cubes]** nod.

![](assets/s_advuser_cube_node.png)

De huvudsakliga användningsområdena för kuber är följande:

* Dataexport kan ske direkt i en rapport som utformas i **[!UICONTROL Reports]** på Adobe Campaign.

   Om du vill göra det skapar du en ny rapport och väljer den kub som du vill använda.

   ![](assets/cube_create_new.png)

   Kuber visas som mallar baserade på vilka rapporter skapas. När du har valt en mall klickar du på **[!UICONTROL Create]** för att konfigurera och visa matchande rapport.

   Du kan anpassa mått, ändra visningsläge eller konfigurera tabellen och sedan visa rapporten med huvudknappen.

   ![](assets/cube_display_new.png)

* Du kan även referera till en kub i **[!UICONTROL Query]** rutan för en rapport för att använda sina indikatorer, som visas nedan:

   ![](assets/s_advuser_query_using_a_cube.png)

* Du kan också infoga en pivottabell baserad på en kub på en rapportsida. Det gör du genom att referera till kuben som ska användas i **[!UICONTROL Data]** pivottabellens flik på den berörda sidan.

   ![](assets/s_advuser_cube_in_report.png)

   Mer information finns i [Utforska data i en rapport](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report).
