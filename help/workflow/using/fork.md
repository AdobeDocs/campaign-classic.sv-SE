---
product: campaign
title: Förgrening
description: Läs mer om arbetsflödesaktiviteten för gafflar
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: 1113afb573bad958ec7cc2cf008f71c8e751e8f9
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# Förgrening{#fork}

![](../../assets/common.svg)

Du kan använda aktiviteten **[!UICONTROL Fork]** för att skapa flera utgående övergångar och köra flera aktiviteter oberoende av varandra i samma arbetsflöde.

>[!IMPORTANT]
>
>De utgående övergångar som du lägger till efter en **[!UICONTROL Fork]**-aktivitet körs inte samtidigt. Det här beteendet kan påverka arbetsflödets prestanda. Använd aktiviteten **[!UICONTROL Fork]** om du behöver köra flera aktiviteter oberoende av varandra. Du kan även ansluta till de utgående aktiviteterna före den efterföljande delen av arbetsflödet.

Så här konfigurerar du en **[!UICONTROL Fork]**-aktivitet och dess relaterade aktiviteter:

1. Öppna aktiviteten **[!UICONTROL Fork]** och definiera namn och etikett för utgående övergångar.

   ![](assets/s_user_segmentation_fork.png)

1. Öppna varje utgående övergång och konfigurera den.
1. Om du vill ansluta till utgående övergångar lägger du till en AND-join-aktivitet. [Läs mer](and-join.md).

   Den efterföljande delen av arbetsflödet körs endast när de kopplade utgående övergångarna har slutförts.

## Exempel: segmentering

I det här exemplet skickas olika e-postmeddelanden till olika populationsgrupper. En **[!UICONTROL Fork]**-aktivitet används efter en fråga för att utföra två parallella åtgärder:

* Spara frågeresultatet
* Segmentera resultatet för att skicka flera leveranser

   ![Aktiviteten för gaffeln följer skärningspunkten mellan två frågor och föregår en listuppdateringsaktivitet och en delad aktivitet.](assets/wkf_fork_example.png)

Arbetsflödet omfattar följande:

1. **[!UICONTROL Query]** aktivitet

   Två populationsgrupper har valts: kvinnor och pariser.

1. **[!UICONTROL Intersection]** aktivitet

   Korsningen mellan frågeresultaten, dvs. Parisiska kvinnor, markeras.

1. **[!UICONTROL Fork]** aktivitet

   Den beräknade populationen sparas och segmenteras parallellt i två grupper:

   1. Parisiska kvinnor mellan 18 och 40 år
   1. Parisiska kvinnor över 40

1. **[!UICONTROL Delivery]** aktivitet

   Ett annat e-postmeddelande skickas till varje populationsgrupp.

## Användningsfall: skicka ett födelsedagsmeddelande

Ett återkommande e-postmeddelande skickas till en lista över mottagare på deras födelsedag. En **[!UICONTROL Fork]**-aktivitet används för att inkludera mottagare som är födda den 29 februari på ett skottår. [Läs ](sending-a-birthday-email.md) mer om det här användningsexemplet.

![Aktiviteten för förgreningar följer en testaktivitet och föregår två frågeaktiviteter.](assets/birthday-workflow_usecase_1.png)

## Användningsfall: automatisera innehåll med ett arbetsflöde

Skapandet och leveransen av ett innehållsblock sker automatiskt. En **[!UICONTROL Fork]**-aktivitet används för att beräkna målet och, parallellt, skapa innehållet. [Läs ](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) mer om det här användningsexemplet.

![Aktiviteten för förgreningar följer en leveransaktivitet och föregår en frågeaktivitet och en innehållshanteringsaktivitet, som båda förenas via en AND-join-aktivitet.](../../delivery/using/assets/d_ncs_content_workflow10.png)

Du kan sedan konfigurera varje utgående övergång och sedan förena dem med en [AND-join](and-join.md)-aktivitet om det behövs. På så sätt körs resten av arbetsflödet bara när **[!UICONTROL Fork]**-aktivitetens utgående övergångar är klara.

## Relaterade ämnen

* [AND-join activity](and-join.md)
* [Användningsfall: födelsedagsmeddelande](sending-a-birthday-email.md)
* [Användningsfall: skapa och leverera innehåll](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)