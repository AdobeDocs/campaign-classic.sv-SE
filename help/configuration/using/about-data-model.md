---
title: Om datamodellen Adobe Campaign Classic
description: I det här dokumentet beskrivs grunderna i datamodellen för Adobe Campaign Classic.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2ce2a1a55e244180a4e62d6f3b5a5ed5bb8aff6e

---


# Om datamodellen Campaign Classic{#about-data-model}

I det här avsnittet beskrivs grunderna i datamodellen för Adobe Campaign Classic, vilket ger en bättre förståelse för de inbyggda tabellerna i Campaign och deras interaktion.

Adobe Campaign-databasens konceptuella datamodell består av en uppsättning inbyggda tabeller och deras interaktion.

Om du vill få åtkomst till beskrivningen av varje tabell går du till **[!UICONTROL Admin > Configuration > Data schemas]**, väljer en resurs i listan och klickar på **[!UICONTROL Documentation]** fliken.

![](assets/data-model_documentation-tab.png)

Mer information om standardbeskrivningen för Campaign Classic-datamodellen finns i det här [dokumentet](https://final-docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html).

Den fysiska och logiska strukturen hos de data som medföljer programmet beskrivs i XML. Den lyder under en grammatik som är specifik för Adobe Campaign, som kallas schema. Mer information om Adobe Campaign-scheman finns i det här [avsnittet](../../configuration/using/about-schema-reference.md).

## Översikt {#data-model-overview}

Adobe Campaign bygger på en relationsdatabas som innehåller tabeller som är länkade tillsammans.

Den grundläggande strukturen i Adobe Campaign-datamodellen beskrivs nedan.

## Mottagarregister {#recipient-table}

Datamodellen bygger på en huvudtabell som som standard är mottagartabellen (**NmsRecipient**). Med den här tabellen kan alla marknadsföringsprofiler lagras.

Mer information om mottagartabellen finns i det här [avsnittet](../../configuration/using/default-recipient-table.md).

## Leveransregister {#delivery-table}

Datamodellen innehåller också en del som är avsedd för lagring av alla marknadsföringsaktiviteter. Vanligtvis är det leveransregistret (**NmsDelivery**). Varje post i den här tabellen representerar en leveransåtgärd eller en leveransmall. Den innehåller alla parametrar som krävs för att utföra leveranser som mål, innehåll osv.

## Loggtabeller {#log-tables}

En annan del av datamodellen gör det möjligt att tillfälligt lagra alla loggar som är associerade med kampanjkörningen.

Leveransloggar är alla meddelanden som skickas till mottagare eller enheter i alla kanaler. Huvudtabellen för leveransloggar (**NmsBroadLog**) innehåller leveransloggarna för alla mottagare.
I huvudspårningsloggtabellen (**NmsTrackingLog**) lagras spårningsloggarna för alla mottagare. Spårningsloggarna refererar till mottagarnas reaktioner, t.ex. öppningar och klickningar via e-post. Varje reaktion motsvarar en spårningslogg.
Leveransloggar och spårningsloggar tas bort efter en viss period, som anges i Adobe Campaign och kan ändras. Vi rekommenderar därför att du exporterar loggarna regelbundet.

## Tekniska tabeller {#technical-tables}

Slutligen består en del av datamodellen av tekniska data som används för ansökningsprocessen, inklusive operatorer och användarrättigheter (**NmsGroup**), mappar (**XtkFolder**).