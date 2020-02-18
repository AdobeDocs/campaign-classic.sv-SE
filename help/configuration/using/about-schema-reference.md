---
title: Om schemareferens i Adobe Campaign Classic
description: Lär dig hur du konfigurerar tilläggsscheman för att utöka den konceptuella datamodellen för Adobe Campaign Classic-databasen.
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
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Om schemareferens{#about-schema-reference}

I det här kapitlet beskrivs hur du konfigurerar tilläggsscheman för att utöka den konceptuella datamodellen för Adobe Campaign-databasen.

Om du vill ha en bättre förståelse för de inbyggda tabellerna i Campaign och deras interaktion kan du läsa datamodellen [för](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)Campaign Classic.

Den fysiska och logiska strukturen hos de data som medföljer programmet beskrivs i XML. Den lyder under en grammatik som är specifik för Adobe Campaign, vilket kallas ett **schema**.

Ett schema är ett XML-dokument som är associerat med en databastabell. Den definierar datastrukturen och beskriver tabellens SQL-definition:

* Tabellens namn
* Fält
* Index
* Länkar till andra tabeller

Här beskrivs också XML-strukturen som används för att lagra data:

* Element och attribut
* Elementhierarki
* Element- och attributtyper
* Standardvärden
* Etiketter, beskrivningar och andra egenskaper.

Med scheman kan du definiera en enhet i databasen. Det finns ett schema för varje entitet.

Följande bild visar var scheman finns i Adobe Campaign-datasystemet:

![](assets/reference_schema_intro.png)

## Syntax för scheman {#syntax-of-schemas}

Schemats rotelement är **`<srcschema>`**. Den innehåller ** **`<element>`** och **`<attribute>`** delelementen.

Det första **`<element>`** underelementet sammanfaller med entitetens rot.

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">  
    <attribute name="lastName"/>
    <attribute name="email"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

>[!NOTE]
>
>Entitetens rotelement har samma namn som schemat.

![](assets/s_ncs_configuration_schema_and_entity.png)

Taggarna **`<element>`** definierar namnen på enhetselementen. **`<attribute>`** -taggar i schemat definierar namnen på attributen i de **`<element>`** -taggar som de har länkats till.

## Identifiering av ett schema {#identification-of-a-schema}

Ett dataschema identifieras med sitt namn och namnutrymme.

Med ett namnutrymme kan du gruppera en uppsättning scheman efter intresseområde. Exempelvis används **cus** -namnutrymmet för kundspecifik konfiguration (**kunder**).

>[!IMPORTANT]
>
>Som standard måste namnutrymmets namn vara kortfattat och får endast innehålla tillåtna tecken i enlighet med XML-namngivningsreglerna.
>
>Identifierare får inte börja med numeriska tecken.

Vissa namnutrymmen är reserverade för beskrivningar av de systemenheter som krävs för att Adobe Campaign-programmet ska fungera:

* **xtk**: när det gäller plattformssystemdata,
* **nl**: om den övergripande användningen av ansökan,
* **nms**: om leverans (mottagare, leverans, spårning osv.),
* **ncm**: om innehållshantering,
* **temp**: reserveras för temporära scheman.

Identifieringsnyckeln för ett schema är en sträng som byggts med namnutrymmet och namnet avgränsat med ett kolon. till exempel: **cus:mottagare**.
