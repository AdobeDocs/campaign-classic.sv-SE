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
source-git-commit: 580be39d09bd59770d490945c3ba2b29e12fb3c4
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 0%

---


# Om Campaign-datamodellen{#about-data-model}

I det här avsnittet beskrivs grunderna i datamodellen för Adobe Campaign Classic, vilket ger en bättre förståelse för de inbyggda tabellerna i Campaign och deras interaktion.

Adobe Campaign-databasens konceptuella datamodell består av en uppsättning inbyggda tabeller och deras interaktion.

Om du vill få åtkomst till beskrivningen av varje tabell går du till **[!UICONTROL Admin > Configuration > Data schemas]**, väljer en resurs i listan och klickar på **[!UICONTROL Documentation]** fliken.

![](assets/data-model_documentation-tab.png)

Mer information om standardbeskrivningen för datamodellen i Campaign Classic finns i [det här avsnittet](../../configuration/using/data-model-description.md).

Den fysiska och logiska strukturen hos de data som medföljer programmet beskrivs i XML. Den lyder under en grammatik som är specifik för Adobe Campaign, som kallas schema. Mer information om Adobe Campaign-scheman finns i [det här avsnittet](../../configuration/using/about-schema-reference.md).

## Översikt {#data-model-overview}

Adobe Campaign bygger på en relationsdatabas som innehåller tabeller som är länkade tillsammans. Den grundläggande strukturen i Adobe Campaign-datamodellen beskrivs nedan.

>[!NOTE]
>
>Mer information om arkitekturen för Campaigns datamodell och relaterade bästa metoder finns i [det här avsnittet](../../configuration/using/data-model-best-practices.md#data-model-architecture).

### Mottagarregister {#recipient-table}

Datamodellen bygger på en huvudtabell som som standard är mottagartabellen (**NmsRecipient**). Med den här tabellen kan alla marknadsföringsprofiler lagras.

Mer information om mottagartabellen finns i [det här avsnittet](#default-recipient-table).

### Leveransregister {#delivery-table}

Datamodellen innehåller också en del som är avsedd för lagring av alla marknadsföringsaktiviteter. Vanligtvis är det leveransregistret (**NmsDelivery**). Varje post i den här tabellen representerar en leveransåtgärd eller en leveransmall. Den innehåller alla parametrar som krävs för att utföra leveranser som mål, innehåll osv.

### Loggtabeller {#log-tables}

En annan del av datamodellen gör det möjligt att tillfälligt lagra alla loggar som är associerade med kampanjkörningen.

Leveransloggar är alla meddelanden som skickas till mottagare eller enheter i alla kanaler. Huvudtabellen för leveransloggar (**NmsBroadLog**) innehåller leveransloggarna för alla mottagare.
I huvudspårningsloggtabellen (**NmsTrackingLog**) lagras spårningsloggarna för alla mottagare. Spårningsloggarna refererar till mottagarnas reaktioner, t.ex. öppningar och klickningar via e-post. Varje reaktion motsvarar en spårningslogg.
Leveransloggar och spårningsloggar tas bort efter en viss period, som anges i Adobe Campaign och kan ändras. Vi rekommenderar därför att du exporterar loggarna regelbundet.

### Tekniska tabeller {#technical-tables}

Slutligen består en del av datamodellen av tekniska data som används för ansökningsprocessen, inklusive operatorer och användarrättigheter (**NmsGroup**), mappar (**XtkFolder**).

## Använda standardmottagartabellen {#default-recipient-table}

Den körklara mottagartabellen i Adobe Campaign är en bra startpunkt för att skapa din datamodell. Den har ett antal fördefinierade fält och tabelllänkar som enkelt kan utökas. Detta är särskilt användbart när du främst riktar dig till mottagare, eftersom det passar en enkel mottagarorienterad datamodell.

Fördelarna med att använda standardmottagartabellen är följande:

* Arbeta direkt med funktioner som prenumerationer, listor, undersökningar, sociala medier och så vidare.
* Tillhandahåller en marknadsföringsdatabas med en mottagarcentrerad datamodell.
* Snabbare implementering.
* Enkelt underhåll av support och partners.

Det går dock att utöka mottagartabellen, men inte att minska antalet fält eller länkar i tabellen.

>[!IMPORTANT]
>
>Vi rekommenderar att du inte tar bort fält (även om de är oanvändbara) i mottagartabellen eftersom det kan leda till fel i de inbyggda modulerna.

Och eftersom mottagartabellen är en del av produkten utvecklas både tabellen och dess tillhörande form allt eftersom produkten ändras. Det krävs därför extra underhåll för att kontrollera att eventuella tillägg fortfarande är giltiga vid uppgraderingen.

## Utöka datamodellen {#extending-data-model}

När ni börjar med Adobe Campaign måste ni utvärdera standarddatamodellen för att kontrollera vilken tabell som är bäst lämpad för att lagra era marknadsföringsdata.

Om det är relevant kan du använda den förvalda mottagartabellen med de färdiga fälten, som beskrivs i [det här avsnittet](#default-recipient-table).

Om det behövs kan du utöka den med två mekanismer:

* Utöka en befintlig tabell med nya fält. Du kan till exempel lägga till ett nytt&quot;Lojalitet&quot;-fält i mottagartabellen.
* Skapa en ny tabell, t.ex. en&quot;Inköpstabell&quot; med alla inköp som gjorts av varje profil i databasen, och länka den till mottagartabellen.

Mer information om hur du konfigurerar tilläggsscheman för att utöka den konceptuella datamodellen finns i [Om schemautgåva](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>Att utöka datamodellen är reserverat för avancerade användare.

## Använda en anpassad mottagartabell {#custom-recipient-table}

När du utformar din Adobe Campaign-datamodell kan du använda [den körklara mottagartabellen](#default-recipient-table)eller välja att skapa en mottagartabell som inte är standard för att lagra dina marknadsföringsprofiler.

Om er datamodell inte passar den mottagarcentrerade strukturen kan ni skapa andra tabeller som målgruppsdimension i Adobe Campaign. Detta kan till exempel vara relevant när du behöver rikta in dig på hushåll, konton (som mobiltelefoner) och företag/webbplatser i stället för bara mottagare.

>[!NOTE]
>
>I så fall måste du skapa en ny [målmappning](../../configuration/using/target-mapping.md).

Alla principer och steg som behövs när du använder en anpassad mottagartabell beskrivs i [det här avsnittet](../../configuration/using/about-custom-recipient-table.md).

Fördelarna med att använda en anpassad mottagartabell är följande:

### Flexibel datamodell {#flexible-data-model}

Mottagartabellen är inte användbar om du inte behöver de flesta av mottagartabellfälten eller om datamodellen inte är mottagarcentrerad.

### Skalbarhet {#scalability}

Stora volymer kräver en effektiv tabell med få fält för en effektiv design. Den färdiga mottagartabellen skulle ha för många oanvändbara fält, vilket skulle kunna påverka prestanda och bristande effektivitet.

### Dataplats {#data-location}

Om data finns i en extern befintlig marknadsföringsdatabas kan det kräva för mycket arbete för att använda den körklara mottagartabellen. Det är enklare att skapa en ny som baseras på en befintlig struktur.

### Smidig migrering {#easy-migration}

Inget underhåll krävs för att kontrollera att alla tillägg fortfarande är giltiga vid uppgraderingen.

>[!IMPORTANT]
>
>Användningen av en anpassad mottagartabell är reserverad för avancerade användare och är begränsad. Mer information finns i [det här avsnittet](../../configuration/using/about-custom-recipient-table.md).
