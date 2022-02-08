---
product: campaign
title: Om schemareferens i Adobe Campaign Classic
description: Lär dig hur du konfigurerar tilläggsscheman för att utöka den konceptuella datamodellen för Adobe Campaign Classic-databasen
feature: Schema Extension
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 7%

---

# Om schemareferens{#about-schema-reference}

![](../../assets/v7-only.svg)

I det här kapitlet beskrivs hur du konfigurerar tilläggsscheman för att utöka Adobe Campaign-databasens konceptuella datamodell.

Om du vill få en bättre förståelse för de inbyggda tabellerna i Campaign och deras interaktion kan du läsa [Campaign Classic datamodell](https://helpx.adobe.com/se/campaign/kb/acc-datamodel.html).

Den fysiska och logiska strukturen hos de data som medföljer programmet beskrivs i XML. Den lyder under en grammatik som är specifik för Adobe Campaign och som kallas **schema**.

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

I följande bild visas schemats placering i Adobe Campaign datasystem:

![](assets/reference_schema_intro.png)

## Syntax för scheman {#syntax-of-schemas}

Schemats rotelement är **`<srcschema>`**. Den innehåller **`<element>`** och **`<attribute>`** delelement.

Den första **`<element>`** delelement sammanfaller med entitetens rot.

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

The **`<element>`** -taggar definierar namnen på enhetselement. **`<attribute>`** -taggar i schemat definierar namnen på attributen i **`<element>`** -taggar som de har länkats till.

## Identifiering av ett schema {#identification-of-a-schema}

Ett dataschema identifieras med sitt namn och namnutrymme.

Med ett namnutrymme kan du gruppera en uppsättning scheman efter intresseområde. Till exempel **kus** namnutrymme används för kundspecifik konfiguration (**kunder**).

Identifieringsnyckeln för ett schema är en sträng som byggts med namnutrymmet och namnet avgränsat med ett kolon. till exempel: **cus:mottagare**.

>[!IMPORTANT]
>
>Namnutrymmets namn måste vara kortfattat och får endast innehålla tillåtna tecken enligt reglerna för XML-namngivning.
>
>Identifierare får inte börja med numeriska tecken.
>
>Följande namnutrymmen är reserverade för beskrivningar av de systemenheter som krävs för att Adobe Campaign-programmet ska fungera och får inte användas: **xtk**, **nl**, **nms**, **ncm**, **temp**, **ncl**, **crm**, **xxl**.

