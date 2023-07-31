---
product: campaign
title: Om kuber
description: Kom igång med kuber
feature: Reporting, Monitoring
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
hide: true
hidefromtoc: true
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 3%

---

# Kom igång med kuber{#about-cubes}



## Terminologi {#terminology}

Specifika termer när du arbetar med kuber visas nedan.

* **Kub** - En kub är en representation av flerdimensionell information: den ger slutanvändarna strukturer som utformats för interaktiv dataanalys.

* **Faktatabell/schema** - Faktatabellen (eller faktchemat) innehåller rådata eller elementära data som analyserna ska baseras på. Dessa är huvudsakligen stora volymtabeller (möjligen med länkade tabeller) med potentiellt långa beräkningar. En faktatabell kan t.ex. vara utsändningstabellen, inköpstabellen osv.

* **Dimension** - Med Dimensioner kan du segmentera data i grupper: när de har skapats fungerar dimensionerna som analysaxlar. I de flesta fall definieras flera nivåer för en viss dimension. För en tidsdimension är nivåerna till exempel månader, dagar, timmar, minuter och så vidare. Den här nivåuppsättningen representerar dimensionshierarkin och möjliggör olika nivåer av dataanalys.

* **Bindning** - För vissa fält kan du definiera bindning till gruppvärden och göra det enklare att läsa information. Bindning används på nivåer. Vi rekommenderar att du definierar bindning när det kan finnas många olika värden.

* **Mät** - De vanligaste måtten är summa, genomsnitt, maximum, minimum, standardavvikelse osv. Åtgärder kan beräknas: Antagandegraden för ett erbjudande är förhållandet mellan det antal gånger det presenterades och det antal gånger det accepterades.

## Arbetsytan Kub {#cube-workspace}

Kuber lagras i **[!UICONTROL Administration > Configuration > Cubes]** nod.

![](assets/s_advuser_cube_node.png)

De huvudsakliga användningsområdena för kuber är följande:

* Dataexport kan ske direkt i en rapport som utformas i **[!UICONTROL Reports]** på Adobe Campaign-plattformen.

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
