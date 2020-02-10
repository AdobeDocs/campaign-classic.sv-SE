---
title: Åtkomst till leveransinformation
seo-title: Åtkomst till leveransinformation
description: Åtkomst till leveransinformation
seo-description: null
page-status-flag: never-activated
uuid: dc8f0267-1884-4a39-9a7d-d5ef21932928
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: d2631c67-7781-4baa-b24e-e7921353d131
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 211556bbf023731ffeab2e90692410a852ab3555

---


# Åtkomst till leveransinformation{#accessing-deliveries-information}

## Åtkomst till listan över leveranser {#accessing-the-list-of-deliveries}

Om du vill visa listan över leveranser går du till **[!UICONTROL Campaigns]** universum och klickar på **[!UICONTROL Deliveries]** länken.

Om du använder [Utforskarvyn](../../platform/using/adobe-campaign-workspace.md#about-adobe-campaign-explorer)kan du komma åt alla leveranser via noden **[!UICONTROL Campaign management > Deliveries]** i trädet.

>[!NOTE]
>
>Arbetsytan i Adobe Campaign visas i [det här avsnittet](../../platform/using/adobe-campaign-workspace.md).

På den här sidan får du tillgång till en övergripande vy över dina leveranser: visas alla leveranser i databasen. Du kan visa deras status, antal lyckade åtgärder och ändringsdatum.

![](assets/d_ncs_user_filter_interface_delivery01.png)

>[!NOTE]
>
>Informationsfiltrering presenteras i [det här avsnittet](../../platform/using/filtering-options.md).

Med leveransguiden kan du konfigurera leveranser, starta godkännandeprocessen och skicka. Innehållet i guiden beror på kommunikationskanalen (e-post, mobil, push, direktreklam) och operatörsrättigheterna.

Om du vill ändra leveranserna i listan klickar du på en leverans. Den öppnas i ett nytt fönster och du kan bekräfta leveransen eller pausa den, till exempel.

![](assets/s_ncs_user_interface_delivery02.png)

Beroende på leveranscykelns stadium är de huvudsakliga statusvärdena:

* Avbruten
* Misslyckades
* Väntande
* Slutförd
* Pausad
* Försök igen väntar
* Pågår
* Klart för leverans
* Förberedelser pågår
* Målberäkning
* Redigeras

Varje status har sin egen färg och etikett.

![](assets/s_ncs_user_status_campaigns_120.png)

Med listrutan bredvid **[!UICONTROL Create]** knappen kan du filtrera leveranser baserat på deras status.

![](assets/delivery_filter_status.png)

## Åtkomst till leveranskalendern {#accessing-the-delivery-calendar}

Gå till **[!UICONTROL Campaign]** universum och klicka på **[!UICONTROL Campaign calendar]** länken för att komma åt leveranskalendern. Den här kalendern visar hur kampanjerna ser ut över tid. Du kan anpassa visningen efter månad, vecka eller dag.

![](assets/s_ncs_user_interface_delivery04.png)

Klicka på namnet på en leverans för att visa huvudinformationen om den. Du kan även öppna kampanjen genom att klicka **[!UICONTROL Open]**.

![](assets/s_ncs_user_interface_delivery05.png)

## Åtkomst till leveransdataflödesinformation {#accessing-deliveries-throughput-information}

Informationen på **[!UICONTROL Delivery throughput]** sidan avser alla leveranser av plattformen. För att mäta den hastighet med vilken meddelandena levereras är kriterierna antalet meddelanden som skickas per timme och meddelandets storlek (i bitar per sekund). I exemplet nedan visar det första diagrammet de lyckade leveranserna i blått och antalet felaktiga leveranser i orange.

Du kan välja den tidsrymd som genomflödet beräknas för. Det gör du genom att markera värdet i listrutan och sedan klicka på **[!UICONTROL Refresh]**.

![](assets/s_ncs_user_interface_delivery06.png)

>[!NOTE]
>
>Om du har uppgraderat till Förbättrat MTA för värdbaserade eller hybridbaserade installationer kommer **[!UICONTROL Delivery throughput]** sidan inte längre att visa dataflödet för e-postmottagarna. Den visar dataöverföringshastigheten för vidarebefordran av meddelanden från Campaign till det förbättrade MTA-avtalet.
>
>Mer information om Adobe Campaign Enhanced MTA finns i det här [dokumentet](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).