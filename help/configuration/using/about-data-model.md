---
product: campaign
title: Kom igång med Campaign Classicens datamodell
description: Lär dig hur du utökar datamodellen i Campaign, redigerar scheman, använder API:er med mera
feature: Data Model, Configuration
role: Data Engineer, Developer
exl-id: 655b5928-b005-442f-b026-2f1b0c1abb99
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 5%

---

# Kom igång med Campaign-datamodellen{#about-data-model}

Den konceptuella datamodellen av databasen i Adobe Campaign består av en uppsättning inbyggda tabeller och deras interaktion. Huvudtabeller och begrepp listas på den här sidan.

## Översikt {#data-model-overview}

Adobe Campaign förlitar sig på en relationsdatabas som innehåller tabeller som är länkade tillsammans. Den grundläggande strukturen i Adobe Campaign datamodell beskrivs på följande sätt.

### Mottagarregister {#recipient-table}

Datamodellen bygger på en huvudtabell som som standard är mottagartabellen (**NmsRecipient**). Med den här tabellen kan alla marknadsföringsprofiler lagras.

Mer information om mottagartabellen finns i [det här avsnittet](#default-recipient-table).

### Leveransregister {#delivery-table}

Datamodellen innehåller också en del som är avsedd för lagring av alla marknadsföringsaktiviteter. Vanligtvis är det leveranstabellen (**NmsDelivery**). Varje post i den här tabellen representerar en leveransåtgärd eller en leveransmall. Den innehåller alla parametrar som krävs för att utföra leveranser som mål, innehåll osv.

### Loggtabeller {#log-tables}

En annan del av datamodellen gör det möjligt att tillfälligt lagra alla loggar som är associerade med kampanjkörningen.

Leveransloggar är alla meddelanden som skickas till mottagare eller enheter i alla kanaler. Huvudtabellen för leveransloggar (**NmsBroadLog**) innehåller leveransloggarna för alla mottagare.
Huvudspårningsloggtabellen (**NmsTrackingLog**) lagrar spårningsloggarna för alla mottagare. Spårningsloggarna refererar till mottagarnas reaktioner, t.ex. öppningar och klickningar via e-post. Varje reaktion motsvarar en spårningslogg.
Leveransloggar och spårningsloggar tas bort efter en viss period, som anges i Adobe Campaign och kan ändras. Vi rekommenderar därför att du exporterar loggarna regelbundet.

### Tekniska tabeller {#technical-tables}

Slutligen består en del av datamodellen av tekniska data som används för programprocessen, inklusive operatorer och användarrättigheter (**NmsGroup**), mappar (**XtkFolder**).

## Använda den inbyggda mottagartabellen {#default-recipient-table}

Den inbyggda mottagartabellen i Adobe Campaign är en bra startpunkt för att skapa din datamodell. Den har ett antal fördefinierade fält och tabelllänkar som enkelt kan utökas. Detta är särskilt användbart när du främst riktar dig till mottagare, eftersom det passar en enkel mottagarorienterad datamodell.

Fördelarna med den inbyggda mottagartabellen är följande:

* Arbeta med funktioner som prenumerationer, listor med mera.
* Tillhandahåller en marknadsföringsdatabas med en mottagarcentrerad datamodell.
* Snabbare implementering.
* Enkelt underhåll av support och partners.

Det går dock att utöka mottagartabellen, men inte att minska antalet fält eller länkar i tabellen.

>[!IMPORTANT]
>
>Vi rekommenderar att du inte tar bort fält (även om de är oanvändbara) i mottagartabellen eftersom det kan leda till fel i de inbyggda modulerna.

Och eftersom mottagartabellen är en del av produkten utvecklas både tabellen och dess tillhörande form allt eftersom produkten ändras. Det krävs därför extra underhåll för att kontrollera att eventuella tillägg fortfarande är giltiga vid uppgraderingen.

## Utöka datamodellen {#extending-data-model}

När du börjar med Adobe Campaign måste du utvärdera standarddatamodellen för att kontrollera vilken tabell som är bäst lämpad för att lagra dina marknadsföringsdata.

Om det är relevant kan du använda den förvalda mottagartabellen med körklara fält, som beskrivs i [det här avsnittet](#default-recipient-table).

Om det behövs kan du utöka den med två mekanismer:

* Utöka en befintlig tabell med nya fält. Du kan till exempel lägga till ett nytt&quot;Lojalitet&quot;-fält i mottagartabellen.
* Skapa en ny tabell, t.ex. en&quot;Inköpstabell&quot; med alla inköp som gjorts av varje profil i databasen, och länka den till mottagartabellen.

Mer information om hur du konfigurerar tilläggsscheman för att utöka den konceptuella datamodellen finns i [Om schemaversionen](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>Att utöka datamodellen är reserverat för avancerade användare.

## Använda en anpassad mottagartabell {#custom-recipient-table}

När du utformar din Adobe Campaign-datamodell kan du använda den [inbyggda mottagartabellen](#default-recipient-table) eller välja att skapa en [anpassad mottagartabell](../../configuration/using/about-custom-recipient-table.md) för att lagra dina marknadsföringsprofiler.

Om datamodellen inte passar den mottagarcentrerade strukturen kan du skapa andra tabeller som målningsdimension inom Adobe Campaign. Detta kan till exempel vara relevant när du behöver rikta in dig på hushåll, konton (som mobiltelefoner) och företag/webbplatser i stället för bara mottagare.

>[!NOTE]
>
>I det här fallet måste du skapa en ny [målmappning](../../configuration/using/target-mapping.md).

Alla principer och steg som behövs när du använder en anpassad mottagartabell beskrivs i [det här avsnittet](../../configuration/using/about-custom-recipient-table.md).

Fördelarna med att använda en anpassad mottagartabell är följande:

* **Flexibel datamodell** - Den inbyggda mottagartabellen är värdelös om du inte behöver de flesta av mottagartabellfälten eller om datamodellen inte är mottagarcentrerad.

* **Skalbarhet** - Stora volymer kräver en strömlinjeformad tabell med få fält för en effektiv design. Den inbyggda mottagartabellen har för många oanvändbara fält, vilket kan påverka prestanda och bristande effektivitet.

* **Dataplats** - Om data finns i en extern befintlig marknadsföringsdatabas kan det krävas för mycket arbete för att använda den inbyggda mottagartabellen. Det är enklare att skapa en ny som baseras på en befintlig struktur.

* **Enkel migrering** - Inget underhåll krävs för att kontrollera att alla tillägg fortfarande är giltiga vid uppgradering.

>[!IMPORTANT]
>
>Användningen av en anpassad mottagartabell är reserverad för avancerade användare och är begränsad. Mer information finns i [det här avsnittet](../../configuration/using/about-custom-recipient-table.md).

## Relaterade ämnen

Läs mer om Campaign-datamodellen i följande avsnitt:

* **Beskrivning av huvudtabellerna** - Mer information om standarddatamodellsbeskrivningen för Campaign Classicen finns i [det här avsnittet](../../configuration/using/data-model-description.md).

* **Fullständig beskrivning av varje tabell** - Om du vill få tillgång till den fullständiga beskrivningen av varje tabell går du till **[!UICONTROL Admin > Configuration > Data schemas]**, markerar en resurs i listan och klickar på fliken **[!UICONTROL Documentation]**.

  ![](assets/data-model_documentation-tab.png)


* **Kampanjscheman** - Den fysiska och logiska strukturen för de data som finns i programmet beskrivs i XML. Den följer en grammatik som är specifik för Adobe Campaign och som kallas för ett schema. Mer information om Adobe Campaign-scheman finns i [det här avsnittet](../../configuration/using/about-schema-reference.md).

* **Bästa praxis för datamodell** - Lär dig mer om arkitektur för kampanjdatamodell och besläktade bästa metoder i [det här avsnittet](../../configuration/using/data-model-best-practices.md#data-model-architecture).
