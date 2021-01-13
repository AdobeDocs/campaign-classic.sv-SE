---
solution: Campaign Classic
product: campaign
title: Förgrening
description: Läs mer om arbetsflödesaktiviteten för gafflar
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: d35b22386bd2681ba02e4379c627821b35a7d04e
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# Förgrening{#fork}

Med aktiviteten **[!UICONTROL Fork]** kan du skapa flera utgående övergångar, så att du kan utföra flera aktiviteter oberoende av varandra i samma arbetsflöde.

Du kan till exempel använda aktiviteten efter en fråga för att utföra två åtgärder parallellt:

* Spara resultatet av frågan till en målgrupp,
* Utför en segmentering av resultatet för att skicka flera leveranser.

Du kan också använda aktiviteten när du skapar innehåll och skickar ut automatisering för att starta målberäkningen och skapa innehåll parallellt. Ett användningsexempel finns i [det här avsnittet](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content).

>[!IMPORTANT]
>
>Kom ihåg att utgående övergångar som läggs till efter en Fork-aktivitet inte körs samtidigt.
>
>Aktiviteten bör därför inte användas för att förbättra arbetsflödets prestanda, utan för att utföra flera aktiviteter oberoende av varandra och så småningom förena dem innan resten av arbetsflödet körs.

Om du vill konfigurera aktiviteten öppnar du den och definierar sedan antal och etikett för de utgående övergångarna.

![](assets/s_user_segmentation_fork.png)

Du kan sedan konfigurera varje utgående övergång och sedan förena dem med en [AND-join](../../workflow/using/and-join.md)-aktivitet om det behövs. På så sätt körs resten av arbetsflödet bara när **[!UICONTROL Fork]**-aktivitetens utgående övergångar har slutförts.
