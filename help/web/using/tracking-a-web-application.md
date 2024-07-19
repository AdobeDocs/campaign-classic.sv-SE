---
product: campaign
title: Spåra besök i en webbapplikation
description: Spåra besök i en webbapplikation
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Web Apps, Reporting, Monitoring
exl-id: 07bd36ce-c701-4998-974f-81fd4fac22a0
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 4%

---

# Spåra besök i en webbapplikation{#tracking-a-web-application}



Med Adobe Campaign kan du spåra och mäta besök på webbprogramsidor genom att infoga spårningstaggar. Den här funktionen kan användas för alla typer av webbprogram (formulär, webbsidor etc.).

Därför kan du definiera flera navigeringsvägar och utvärdera hur de fungerar. Återskapade data är sedan tillgängliga i rapporter för respektive program.

De viktigaste förbättringarna i den här versionen är följande:

* Möjlighet att infoga flera spårningstaggar på samma sida för att underlätta definitionen av navigeringssökvägar (t.ex. köp, prenumeration, retur osv.).
* Visa navigeringssökvägar och spårningstaggar för de olika sidorna på kontrollpanelen för webbprogram.

  ![](assets/trackers_1.png)

* Genererar en fullständig spårningsrapport.

  ![](assets/trackers_5.png)

  De viktigaste indikatorerna är följande:

   * **Konverteringsfrekvens**: antal personer som visade alla steg i en navigeringssökväg.
   * **Studsfrekvens**: antal personer som endast visade det första steget
   * **Konverteringstratt**: förlustfrekvens mellan varje steg.

  Dessutom visar ett **sektordiagram** populationen enligt dess källa.

## Identifiera trafikkällan {#identifying-the-traffic-source}

Två olika lägen kan användas för att identifiera var besökaren kommer ifrån när han eller hon öppnar ett webbprogram:

1. Skicka en viss leverans för att ge åtkomst till webbsidorna: i det här fallet är trafikkällan den här leveransen,
1. Kopplar webbprogrammet till en dedikerad trafikkälla: i det här fallet måste det vara en extern leverans av typen &quot;trafikkälla&quot;. Den kan väljas från webbprogrammets egenskaper eller från målmappningen.

   ![](assets/trackers_6.png)

För att identifiera trafikkällan i ett webbprogram söker Adobe Campaign efter följande information i följd:

1. källans leveransidentifierare, om den finns (nlId cookie),
1. Identifieraren för den externa leveransen som definieras i webbprogrammets egenskaper, om sådan finns.
1. identifieraren för den externa leveransen som definieras i målmappningen, om den finns.

>[!NOTE]
>
>Anonym spårning är bara tillgängligt om alternativet har aktiverats i distributionsguiden när Campaign installeras.

## Webbprogram utformade med DCE (Digital Content Editor) {#web-applications-designed-with-digital-content-editor--dce-}

När ett webbprogram skapas med HTML-innehållsredigeraren - **Digital Content Editor (DCE)** - infogas spårningstaggar på fliken **[!UICONTROL Properties]** i redigeraren. Mer information om Digital Content Editor (DCE) finns i [det här avsnittet](about-campaign-html-editor.md).

![](assets/trackers_2.png)

När du använder webbgränssnittet måste spårningstaggar infogas från sidegenskaperna.

![](assets/trackers_3.png)

Med ikonen **[!UICONTROL Display blocks]** kan du visa antalet spårningstaggar som har definierats för sidan.

![](assets/trackers_4.png)
