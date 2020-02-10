---
title: Spåra ett webbprogram
seo-title: Spåra ett webbprogram
description: Spåra ett webbprogram
seo-description: null
page-status-flag: never-activated
uuid: c087b40c-fd14-440f-8f38-33f5f68120a9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 8e52f927-dadd-44c8-a51d-f717bc083eef
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# Spåra ett webbprogram{#tracking-a-web-application}

Med Adobe Campaign kan ni spåra och mäta besök på webbprogramsidor genom att infoga spårningstaggar. Den här funktionen kan användas för alla webbapplikationstyper (formulär, onlineundersökningar, webbsidor som skapats med DCE etc.).

Därför kan du definiera flera navigeringsvägar och utvärdera hur de fungerar. Återskapade data är sedan tillgängliga i rapporter för respektive program.

De viktigaste förbättringarna i den här versionen är följande:

* Möjlighet att infoga flera spårningstaggar på samma sida för att underlätta definitionen av navigeringssökvägar (t.ex. köp, prenumeration, retur osv.).
* Visa navigeringssökvägar och spårningstaggar för de olika sidorna på kontrollpanelen för webbprogram.

   ![](assets/trackers_1.png)

* Genererar en fullständig spårningsrapport.

   ![](assets/trackers_5.png)

   De viktigaste indikatorerna är följande:

   * **Konverteringsgrad**: antal personer som visade alla steg i en navigeringssökväg.
   * **Studsfrekvens**: antal personer som endast visade det första steget
   * **Konverteringstunnel**: förlustnivå mellan varje steg.
   Dessutom visar ett **sektortypdiagram** populationen utifrån dess källa.

## Identifiera trafikkällan {#identifying-the-traffic-source}

Två olika lägen kan användas för att identifiera var besökaren kommer ifrån när han eller hon öppnar ett webbprogram:

1. Skicka en viss leverans för att ge åtkomst till webbsidorna: i detta fall är trafikkällan denna leverans,
1. Koppla webbprogrammet till en dedikerad trafikkälla: i det här fallet måste det vara en extern leverans av typen &quot;trafikkälla&quot;. Den kan väljas från webbprogrammets egenskaper eller från målmappningen.

   ![](assets/trackers_6.png)

Adobe Campaign söker efter följande information för att identifiera trafikkällan i ett webbprogram:

1. källans leveransidentifierare, om den finns (nlId cookie),
1. Identifieraren för den externa leveransen som definieras i webbprogrammets egenskaper, om sådan finns.
1. identifieraren för den externa leveransen som definieras i målmappningen, om den finns.

>[!NOTE]
>
>Kom ihåg att anonym spårning bara är möjligt om motsvarande alternativ har aktiverats i distributionsguiden.
>
>Mer information finns i [installationshandboken](../../installation/using/deploying-an-instance.md).

## Webbprogram utformade med DCE (Digital Content Editor) {#web-applications-designed-with-digital-content-editor--dce-}

När ett webbprogram skapas med HTML-redigeraren - **Digital Content Editor (DCE)** infogas spårningstaggar på **[!UICONTROL Properties]** fliken i redigeraren. Mer information om Digital Content Editor (DCE) finns i [det här avsnittet](../../web/using/about-campaign-html-editor.md).

![](assets/trackers_2.png)

När du använder webbgränssnittet måste spårningstaggar infogas från sidegenskaperna.

![](assets/trackers_3.png)

Med **[!UICONTROL Display blocks]** ikonen kan du visa antalet spårningstaggar som har definierats för sidan.

![](assets/trackers_4.png)

