---
product: campaign
title: Om schemautgåva
description: Kom igång med schemaversionen
feature: Schema Extension
exl-id: 9e10b24e-c4de-4e76-bbed-0d05f62120b7
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '1004'
ht-degree: 7%

---

# Om schemautgåva{#about-schema-edition}

![](../../assets/v7-only.svg)

Adobe Campaign använder datascheman för att

* Definiera hur dataobjekt i programmet länkas till underliggande databastabeller.
* Definiera länkar mellan olika dataobjekt i programmet Campaign.
* Definiera och beskriva de enskilda fälten som ingår i varje objekt.

Om du vill få en bättre förståelse för de inbyggda tabellerna i Campaign och deras interaktion kan du läsa [det här avsnittet](https://helpx.adobe.com/se/campaign/kb/acc-datamodel.html).

## Utöka eller skapa scheman {#extending-or-creating-schemas}

Om du vill lägga till ett fält eller index eller något annat element i ett av de centrala datamappningarna i Campaign, t.ex. mottagartabellen (nms:mottagare), måste du utöka det schemat. Mer information finns i [Utöka ett schema](../../configuration/using/extending-a-schema.md) -avsnitt.

Om du vill lägga till en helt ny typ av data som inte finns i körklart läge i Adobe Campaign (till exempel en kontraktstabell) kan du skapa ett anpassat schema direkt. Mer information finns i [Datamodeller](../../configuration/using/data-schemas.md) -avsnitt.

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

Mer information om uppräkningar finns i [Uppräkningar](../../configuration/using/schema-structure.md#enumerations) och [`<enumeration>` element](../../configuration/using/schema/enumeration.md) -avsnitt.

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

The **xpath** attributet pekar på det fält i schemat som du vill indexera.

>[!IMPORTANT]
>
>Det är viktigt att komma ihåg att prestandavinster för läsning av SQL-frågor som tillhandahålls av index även har en prestandaförsämring när du skriver poster. Index bör därför användas med försiktighet.

Mer information om index finns i [Indexerade fält](../../configuration/using/database-mapping.md#indexed-fields) -avsnitt.

## Tangenter {#keys}

Alla tabeller måste ha minst en nyckel och ofta etableras de automatiskt i schemats huvudelement med hjälp av **@autopk=true** -attributet är inställt på &quot;true&quot;.

Primärnyckeln kan också definieras med **internal** -attribut.

Exempel:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

I det här exemplet ska du i stället för att låta **@autopk** för att skapa en standardprimärnyckel med namnet&quot;id&quot; anger vi vår egen primärnyckel för&quot;houseid&quot;.

>[!IMPORTANT]
>
>När du skapar ett nytt schema eller under ett schematillägg måste du behålla samma sekvensvärde för primärnyckeln (@pkSequence) för hela schemat.

Mer information om tangenter finns i [Nyckelhantering](../../configuration/using/database-mapping.md#management-of-keys) -avsnitt.

## Attribut (fält) {#attributes--fields-}

Med attribut kan du definiera fälten som utgör dataobjektet. Du kan använda **[!UICONTROL Insert]** i verktygsfältet för schemautgåvor om du vill släppa tomma attributmallar i XML-filen där markören finns. Mer information finns i [Datamodeller](../../configuration/using/data-schemas.md) -avsnitt.

![](assets/schemaextension_getting_started_2.png)

Den fullständiga listan med attribut finns i [`<attribute>` element](../../configuration/using/schema/attribute.md) -avsnitt. Här är några av de vanligaste attributen:

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

   Om du vill visa en tabell över mappningarna för de datatyper som genereras av Adobe Campaign för de olika databashanteringssystemen, se [Mappa typer av Adobe Campaign-/DBMS-data](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) -avsnitt.

Mer information om respektive attribut finns i [Attributbeskrivning](../../configuration/using/schema/attribute.md) -avsnitt.

### Exempel {#examples}

Exempel på hur du definierar ett standardvärde:

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

Exempel på hur du använder ett gemensamt attribut som mall för ett fält som också är markerat som obligatoriskt:

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

Exempel på ett beräknat fält som är dolt med **@advanced** attribute:

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

Länkarna deklareras i schemat som innehåller **sekundärnyckel** för den tabell som den är länkad till.

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

När ändringarna är klara och sparade måste alla ändringar som kan påverka SQL-strukturen tillämpas på databasen. Använd guiden för databasuppdatering om du vill göra det.

![](assets/schemaextension_getting_started_3.png)

Mer information om detta hittar du i avsnittet [Uppdatera databasstrukturen](../../configuration/using/updating-the-database-structure.md) .

>[!NOTE]
>
>Om ändringarna inte påverkar databasstrukturen behöver du bara generera om scheman. Det gör du genom att markera de scheman som ska uppdateras, högerklicka och välja **[!UICONTROL Actions > Regenerate selected schemas...]** . Mer information finns i [Återskapar scheman](../../configuration/using/regenerating-schemas.md) -avsnitt.
