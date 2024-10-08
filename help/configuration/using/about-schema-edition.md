---
product: campaign
title: Om schemautgåva
description: Kom igång med schemautgåvan
feature: Schema Extension
role: Data Engineer, Developer
exl-id: 9e10b24e-c4de-4e76-bbed-0d05f62120b7
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 6%

---

# Om schemautgåva{#about-schema-edition}

Adobe Campaign använder datascheman för att

* Definiera hur dataobjekt i programmet länkas till underliggande databastabeller.
* Definiera länkar mellan olika dataobjekt i programmet Campaign.
* Definiera och beskriva de enskilda fälten som ingår i varje objekt.

Mer information om inbyggda tabeller i Campaign och hur de fungerar finns i [det här avsnittet](https://helpx.adobe.com/se/campaign/kb/acc-datamodel.html).

## Utöka eller skapa scheman {#extending-or-creating-schemas}

Om du vill lägga till ett fält eller index eller något annat element i ett av de centrala datamappningarna i Campaign, t.ex. mottagartabellen (nms:mottagare), måste du utöka det schemat. Mer information finns i avsnittet [Utöka ett schema](../../configuration/using/extending-a-schema.md).

Om du vill lägga till en helt ny typ av data som inte finns i körklart läge i Adobe Campaign (till exempel en kontraktstabell) kan du skapa ett anpassat schema direkt. Mer information finns i avsnittet [Datascheman](../../configuration/using/data-schemas.md).

![](assets/schemaextension_getting_started_1.png)

När du har utökat eller skapat ett schema att arbeta i är det bästa sättet att definiera elementen för XML-innehållet i samma ordning som de visas nedan.

## Uppräkningar {#enumerations}

Uppräkningar definieras först, före huvudelementet i schemat. De gör att du kan visa värden i en lista för att begränsa vilka val användaren har för ett visst fält.

Exempel:

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

När du definierar fält kan du sedan använda den här uppräkningen så här:

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>Du kan också använda användarhanterade uppräkningar (vanligtvis under **[!UICONTROL Administration]** > **[!UICONTROL Platform]** ) för att ange värden för ett visst fält. Detta är effektivt globala uppräkningar och ett bättre alternativ om uppräkningen kan användas utanför det specifika schema som du arbetar i.

Mer information om uppräkningar finns i avsnitten [Uppräkningar](../../configuration/using/schema-structure.md#enumerations) och [`<enumeration>` element](../../configuration/using/schema/enumeration.md).

## Index {#index}

Index är de första elementen som deklarerats i schemats huvudelement.

De kan vara unika eller inte, och referera till ett eller flera fält.

Exempel:

```
<dbindex name="email" unique="true">
  <keyfield xpath="@email"/>
</dbindex>
```

```
<dbindex name="lastNameAndZip">
  <keyfield xpath="@lastName"/>
  <keyfield xpath="location/@zipCode"/>
</dbindex>
```

Attributet **xpath** pekar på det fält i ditt schema som du vill indexera.

>[!IMPORTANT]
>
>Det är viktigt att komma ihåg att prestandavinster för läsning av SQL-frågor som tillhandahålls av index även har en prestandaförsämring när du skriver poster. Index bör därför användas med försiktighet.

Mer information om index finns i avsnittet [Indexerade fält](../../configuration/using/database-mapping.md#indexed-fields).

## Tangenter {#keys}

Alla tabeller måste ha minst en nyckel och upprättas ofta automatiskt i schemats huvudelement med attributet **@autopk=true** inställt på &quot;true&quot;.

Primärnyckeln kan också definieras med attributet **internal**.

Exempel:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

I det här exemplet, i stället för att attributet **@autopk** ska kunna skapa en standardprimärnyckel med namnet&quot;id&quot;, anger vi vår egen primärnyckel för&quot;houseId&quot;.

>[!IMPORTANT]
>
>När du skapar ett nytt schema eller under ett schematillägg måste du behålla samma sekvensvärde för primärnyckeln (@pkSequence) för hela schemat.

Mer information om nycklar finns i avsnittet [Nyckelhantering](../../configuration/using/database-mapping.md#management-of-keys).

## Attribut (fält) {#attributes--fields-}

Med attribut kan du definiera fälten som utgör dataobjektet. Du kan använda knappen **[!UICONTROL Insert]** i verktygsfältet för schemaversionen för att släppa tomma attributmallar i XML-filen där markören finns. Mer information finns i avsnittet [Datascheman](../../configuration/using/data-schemas.md).

![](assets/schemaextension_getting_started_2.png)

Den fullständiga listan med attribut är tillgänglig i avsnittet [`<attribute>` element ](../../configuration/using/schema/attribute.md). Här är några av de vanligaste attributen:

* **@advanced**
* **@dataPolicy**
* **@default**
* **@desc**
* **@enum**
* **@expr**
* **@label**
* **@length**
* **@name**
* **@notNull**
* **@required**
* **@ref**
* **@xml**
* **@type**

  Om du vill visa en tabell med mappningar för datatyperna som genereras av Adobe Campaign för de olika databashanteringssystemen kan du läsa avsnittet [Mappa typer av Adobe Campaign-/DBMS-data](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data).

Mer information om varje attribut finns i avsnittet [Attributbeskrivning](../../configuration/using/schema/attribute.md).

### Exempel {#examples}

Exempel på hur du definierar ett standardvärde:

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

Exempel på hur du använder ett gemensamt attribut som mall för ett fält som också är markerat som obligatoriskt:

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

Exempel på ett beräknat fält som är dolt med attributet **@advanced**:

```
<attribute name="domain" label="Email domain" desc="Domain of recipient email address" expr="GetEmailDomain([@email])" advanced="true" />
```

Exempel på ett XML-fält som också lagras i ett SQL-fält och som har ett **@dataPolicy** -attribut.

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>Även om de flesta attribut är länkade enligt en 1-1-kardinalitet till ett fysiskt fält i databasen är detta inte fallet för XML-fälten eller de beräknade fälten.\
>Ett XML-fält sparas i ett PM-fält (&quot;mData&quot;) i tabellen.\
>Ett beräknat fält skapas dock dynamiskt varje gång en fråga startas, och därför finns det bara i det aktuella lagret.

## Länkar {#links}

Länkar är några av de sista elementen i huvudelementet i schemat. De definierar hur alla olika scheman i din instans relaterar till varandra.

Länkarna deklareras i schemat som innehåller **sekundärnyckeln** för den tabell som den är länkad till.

Det finns tre typer av kardinalitet: 1-1, 1-N och N-N. Det är typen 1-N som används som standard.

### Exempel {#examples-1}

Ett exempel på en 1-N-länk mellan mottagartabellen (ett schema som inte är installerat) och en tabell med anpassade transaktioner:

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

Ett exempel på en 1-1-länk mellan det anpassade schemat &quot;Car&quot; (i &quot;cus&quot;-namnutrymmet) och mottagartabellen:

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

Exempel på en extern koppling mellan mottagartabellen och en adresstabell som baseras på e-postadressen och inte på en primärnyckel:

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

Här motsvarar &quot;xpath-dst&quot; primärnyckeln i målschemat och &quot;xpath-src&quot; den externa nyckeln i källschemat.

## Granskningskedja {#audit-trail}

Ett användbart element som du kanske vill ta med längst ned i schemat är ett spårningselement (granskningsspår).

Använd exemplet nedan för att inkludera fält som relaterar till datumet då data skapades, användaren som skapade data, datumet och författaren till den senaste ändringen för alla data i tabellen:

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## Uppdatera databasstrukturen {#updating-the-database-structure}

När ändringarna är klara och sparade måste alla ändringar som kan påverka SQL-strukturen tillämpas på databasen. Använd databasuppdateringsassistenten för att göra detta.

![](assets/schemaextension_getting_started_3.png)

Mer information om detta hittar du i avsnittet [Uppdatera databasstrukturen](../../configuration/using/updating-the-database-structure.md) .

>[!NOTE]
>
>Om ändringarna inte påverkar databasstrukturen behöver du bara generera om scheman. Om du vill göra det markerar du schemat som ska uppdateras, högerklickar och väljer **[!UICONTROL Actions > Regenerate selected schemas...]**. Mer information finns i avsnittet [Återskapa scheman](../../configuration/using/regenerating-schemas.md).
