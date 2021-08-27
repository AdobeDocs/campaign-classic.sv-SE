---
product: campaign
title: Förgrening
description: Läs mer om arbetsflödesaktiviteten för gafflar
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 1%

---

# Förgrening{#fork}

![](../../assets/common.svg)

Med aktiviteten **[!UICONTROL Fork]** kan du skapa flera utgående övergångar, så att du kan utföra flera aktiviteter oberoende av varandra i samma arbetsflöde.

Du kan till exempel använda aktiviteten efter en fråga för att utföra två åtgärder parallellt:

* Spara resultatet av frågan till en målgrupp,
* Utför en segmentering av resultatet för att skicka flera leveranser.

Du kan också använda aktiviteten när du skapar innehåll och skickar ut automatisering för att starta målberäkningen och skapa innehåll parallellt. Ett användningsexempel finns i [det här avsnittet](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content).

>[!IMPORTANT]
>
>Utgående övergångar som lagts till efter en **[!UICONTROL Fork]**-aktivitet **kommer inte att köras samtidigt.** Detta kan påverka arbetsflödets prestanda. Använd den här aktiviteten om du behöver utföra flera aktiviteter oberoende av varandra och så småningom förena dem innan du kör resten av arbetsflödet.

Om du vill konfigurera aktiviteten **[!UICONTROL Fork]** öppnar du den och definierar antalet utgående övergångar och etiketten.

![](assets/s_user_segmentation_fork.png)

Du kan sedan konfigurera varje utgående övergång och sedan förena dem med en [AND-join](and-join.md)-aktivitet om det behövs. På så sätt körs resten av arbetsflödet bara när **[!UICONTROL Fork]**-aktivitetens utgående övergångar är klara.
