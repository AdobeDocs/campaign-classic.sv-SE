---
product: campaign
title: Formulärstruktur
description: Formulärstruktur
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: e61f2b63-06d3-4b8c-867f-1c729176d2da
source-git-commit: 898353f80a93052cd25088098c9570c2b44ceac4
workflow-type: tm+mt
source-wordcount: '2385'
ht-degree: 0%

---

# Formulärstruktur{#form-structure}

![](../../assets/common.svg)

Beskrivningen av ett formulär är ett strukturerat XML-dokument som observerar formulärschemats grammatik **xtk:formulär**.

XML-dokumentet i indataformuläret måste innehålla `<form>` rotelementet med **name** och **namespace** attribut för att fylla i formulärnamnet och namnutrymmet.

```xml
<form name="form_name" namespace="name_space">
…
</form>
```

Som standard är ett formulär kopplat till dataschemat med samma namn och namnutrymme. Om du vill associera ett formulär med ett annat namn anger du **enhetstabell** attributet för `<form>` -element till schemanyckelns namn. Om du vill visa strukturen för ett inmatningsformulär kan du beskriva ett gränssnitt med exempelschemat &quot;cus:mottagare&quot;:

```xml
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="Male" value="1"/>   
    <value name="female" label="Female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    <attribute name="birthDate" type="datetime" label="Date"/>
    <attribute name="gender" type="byte" label="Gender" enum="gender"/>
  </element>
</srcSchema>
```

Indataformuläret baserat på exempelschemat:

![](assets/d_ncs_integration_form_exemple1.png)

```xml
<form name="recipient" namespace="cus">
  <input xpath="@gender"/>
  <input xpath="@birthDate"/>
  <input xpath="@email"/>
</form>
```

Beskrivningen av redigeringskontrollerna startar från `<form>` rotelement. En redigeringskontroll anges i en **`<input>`** -element med **xpath** attribut som innehåller sökvägen för fältet i dess schema.

Redigeringskontrollen anpassas automatiskt till motsvarande datatyp och använder den etikett som definierats i schemat.

>[!NOTE]
>
>Du kan överlagra etiketten som definierats i dess dataschema genom att lägga till **label** attributet till `<input>` element:\
>`<input label="Email address" xpath="@name" />`

Som standard visas varje fält på en rad och tar upp allt tillgängligt utrymme beroende på datatypen.

## Formatering {#formatting}

Layouten på kontrollerna ser ut som den layout som används i tabeller i HTML, med möjlighet att dela upp en kontroll i flera kolumner, sammanflätade element eller ange hur mycket utrymme som finns tillgängligt. Tänk dock på att du bara kan dela upp området efter proportioner med formateringen. Du kan inte ange fasta dimensioner för ett objekt.

Så här visar du kontrollerna i exemplet ovan i två kolumner:

![](assets/d_ncs_integration_form_exemple2.png)

```xml
<form name="recipient" namespace="cus">
  <container colcount="2">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email"/>
  </container>
</form>
```

The **`<container>`** -element med **colcount** kan du tvinga fram visning av underordnade kontroller i två kolumner.

The **kolspan** -attribut i en kontroll utökar kontrollen med antalet kolumner som anges i värdet:

![](assets/d_ncs_integration_form_exemple3.png)

```xml
<form name="recipient" namespace="cus">
  <container colcount="2">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
</form> 
```

Genom att fylla i **type=&quot;frame&quot;** -attributet lägger behållaren till en ram runt de underordnade kontrollerna med etiketten som finns i **label** attribute:

![](assets/d_ncs_integration_form_exemple4.png)

```xml
<form name="recipient" namespace="cus">
  <container colcount="2" type="frame" label="General">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
</form>
```

A **`<static>`** -element kan användas för att formatera indataformuläret:

![](assets/d_ncs_integration_form_exemple5.png)

```xml
<form name="recipient" namespace="cus">
  <static type="separator" colspan="2" label="General"/>
  <input xpath="@gender"/>
  <input xpath="@birthDate"/>
  <input xpath="@email" colspan="2"/>
  <static type="help" label="General information about recipient with date of birth, gender, and email address." colspan="2"/>
</form>
```

The **`<static>`** -taggen med **avgränsare** kan du lägga till en avgränsare med en etikett i **label** -attribut.

En hjälptext lades till med `<static>` med hjälptyp. Innehållet i texten anges i **label** -attribut.

## Behållare {#containers}

Med behållare kan du gruppera en uppsättning kontroller. De representeras av **`<container>`** -element. De användes ovan för att formatera kontroller över flera kolumner.

The **xpath** attribut på en `<container>` gör det enklare att referera till underordnade kontroller. Referensen för kontroller är sedan relativ till den överordnade `<container>` -element.

Exempel på en behållare utan &quot;xpath&quot;:

```xml
<container colcount="2">
  <input xpath="location/@zipCode"/>
  <input xpath="location/@city"/>
</container>
```

Exempel med tillägget &quot;xpath&quot; i elementet &quot;location&quot;:

```xml
<container colcount="2" xpath="location">
  <input xpath="@zipCode"/>
  <input xpath="@city"/>
</container>
```

### Behållartyper {#types-of-container}

Behållare används för att skapa komplexa kontroller med hjälp av en uppsättning fält som är formaterade på sidor.

#### Tabbbehållare {#tab-container}

En flikbehållare formaterar data på sidor som är tillgängliga från flikar.

![](assets/d_ncs_integration_form_exemple6.png)

```xml
<container type="notebook">
  <container colcount="2" label="General">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
  <container colcount="2" label="Location">
    …
  </container>
</container>
```

Huvudbehållaren definieras av **type=&quot;anteckningsbok&quot;** -attribut. Tabbar deklareras i de underordnade behållarna och etiketten för flikarna fylls i från **label** -attribut.

![](assets/d_ncs_integration_form_exemple7.png)

>[!NOTE]
>
>A **style=&quot;down|up**(som standard)**&quot;** -funktionen tvingar den lodräta placeringen av tabbetiketter under eller över kontrollen. Den här funktionen är valfri.  
>`<container style="down" type="notebook">  … </container>`

#### Ikonlista {#icon-list}

Den här behållaren visar ett lodrätt ikonfält där du kan välja vilka sidor som ska visas.

![](assets/d_ncs_integration_form_exemple8.png)

```xml
<container type="iconbox">
  <container colcount="2" label="General" img="xtk:properties.png">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
  <container colcount="2" label="Location" img="nms:msgfolder.png">
    …
  </container>
</container>
```

Huvudbehållaren definieras av **type=&quot;iconbox&quot;** -attribut. De sidor som är associerade med ikonerna deklareras i de underordnade behållarna. Etiketten för ikonerna fylls i från **label** -attribut.

Ikonen för en sida fylls i från `img="<image>"` attribute, where `<image>` är namnet på bilden som motsvarar bildens nyckel som består av namnet och namnutrymmet (t.ex. &quot;xtk:properties.png&quot;).

Bilderna finns på **[!UICONTROL Administration > Configuration > Images]** nod.

#### Synlighetsbehållare {#visibility-container}

Du kan maskera en uppsättning kontroller via ett dynamiskt villkor.

I det här exemplet visas synligheten för kontroller av värdet i fältet &quot;Kön&quot;:

```xml
<container type="visibleGroup" visibleIf="@gender=1">
  …
</container>
<container type="visibleGroup" visibleIf="@gender=2">
  …
</container>
```

En synlighetsbehållare definieras av attributet **type=&quot;visibleGroup&quot;**. The **visibleIf** -attributet innehåller synlighetsvillkoret.

Exempel på villkorssyntax:

* **visibleIf=&quot;@email=&#39;peter.martinezATneolane.net&#39;&quot;**: testar likhet för strängtypsdata. Jämförelsevärdet måste anges inom citattecken.
* **visibleIf=&quot;@kön >= 1 och @kön != 2&quot;**: villkor för ett numeriskt värde.
* **visibleIf=&quot;@boolean1=true eller @boolean2=false&quot;**: test on Boolean fields.

#### Aktivera behållare {#enabling-container}

Med den här behållaren kan du aktivera eller inaktivera en uppsättning data från ett dynamiskt villkor. Om du inaktiverar en kontroll kan du inte redigera den. I följande exempel visas aktiveringen av kontroller från värdet i fältet Genus:

```xml
<container type="enabledGroup" enabledIf="@gender=1">
  …
</container>
<container type="enabledGroup" enabledIf="@gender=2">
  …
</container>
```

En aktiveringsbehållare definieras av **type=&quot;enabledGroup&quot;** -attribut. The **enabledIf** -attributet innehåller aktiveringsvillkoret.

## Redigera en länk {#editing-a-link}

Kom ihåg att en länk deklareras i dataschemat enligt följande:

```xml
<element label="Company" name="company" target="cus:company" type="link"/>
```

Redigeringskontrollen för länken i indataformuläret är följande:

![](assets/d_ncs_integration_form_exemple9.png)

```xml
<input xpath="company"/>
```

Målmarkeringen är tillgänglig via redigeringsfältet. Posten assisteras av typen ahead så att ett målelement enkelt kan hittas från de första tecknen som anges. Sökningen baseras sedan på **Beräkningssträng** definieras i målschemat. Om schemat inte finns efter valideringen i kontrollen visas ett bekräftelsemeddelande om att målet har skapats direkt. Bekräftelsen skapar en ny post i måltabellen och kopplar den till länken.

En nedrullningsbar lista används för att välja ett målelement från listan med poster som redan har skapats.

The **[!UICONTROL Modify the link]** (mapp) öppnar ett markeringsformulär med listan över målelement och en filterzon:

![](assets/d_ncs_integration_form_exemple10.png)

The **[!UICONTROL Edit link]** (förstorare) öppnar redigeringsformen för det länkade elementet. Formuläret som används dras som standard av nyckeln för målschemat. The **formulär** gör att du kan tvinga fram namnet på redigeringsformuläret (t.ex. &quot;cus:company2&quot;).

Du kan begränsa valet av målelement genom att lägga till **`<sysfilter>`** -element från länkdefinitionen i indataformuläret:

```xml
<input xpath="company">
  <sysFilter>
    <condition expr="[location/@city] =  'Newton"/>
  </sysFilter>
</input>
```

Du kan också sortera listan med **`<orderby>`** element:

```xml
<input xpath="company">
  <orderBy>
    <node expr="[location/@zipCode]"/>
  </orderBy>
</input>
```

### Kontrollegenskaper {#control-properties}

* **noAutoComplete**: inaktiverar type-ahead (med värdet &quot;true&quot;)
* **createMode**: skapar länken i farten om den inte finns. Möjliga värden är:

   * **ingen**: inaktiverar skapande. Ett felmeddelande visas om länken inte finns
   * **inline**: skapar länken med innehållet i redigeringsfältet
   * **utgåva**: visar redigeringsformuläret på länken. När formuläret valideras sparas data (standardläge)

* **noZoom**: inget redigeringsformulär på länken (med värdet &quot;true&quot;)
* **formulär**: överför målelementets redigeringsform

## Länklista {#list-of-links}

En länk som anges i dataschemat som ett samlingselement (unbound=&quot;true&quot;) måste gå igenom en lista för att alla element som är associerade med den ska kunna visas.

Principen består i att visa listan med länkade element med optimerad datainläsning (nedladdning per datauppsättning, körning av listan endast om den är synlig).

Exempel på en samlingslänk i ett schema:

```xml
<element label="Events" name="rcpEvent" target="cus:event" type="link" unbound="true">
…
</element>
```

Listan i indataformuläret:

![](assets/d_ncs_integration_form_exemple11.png)

```xml
 <input xpath="rcpEvent" type="linklist">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

Listkontrollen definieras av **type=&quot;linklist&quot;** -attribut. Listsökvägen måste referera till samlingslänken.

Kolumnerna deklareras via **`<input>`** -element i listan. The **xpath** attribute refererar till sökvägen för fältet i målschemat.

Ett verktygsfält med en etikett (som definieras på länken i schemat) placeras automatiskt ovanför listan.

Listan kan filtreras via **[!UICONTROL Filters]** och konfigurerad att lägga till och sortera kolumner.

The **[!UICONTROL Add]** och **[!UICONTROL Delete]** Med -knappar kan du lägga till och ta bort samlingselement på länken. Om du lägger till ett element startas målschemats redigeringsformulär som standard.

The **[!UICONTROL Detail]** knappen läggs till automatiskt när **zoom=&quot;true&quot;** attributet har fyllts i på **`<input>`** -tagg i listan: kan du starta redigeringsformuläret för den markerade raden.

Filtrering och sortering kan användas när listan läses in:

```xml
 <input xpath="rcpEvent" type="linklist">
  <input xpath="@label"/>
  <input xpath="@date"/>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
  <orderBy>
    <node expr="@date" sortDesc="true"/>
  </orderBy>
</input>
```

### Relationstabell {#relationship-table}

Med en relationstabell kan du länka två tabeller med N-N-kardinalitet. Relationstabellen innehåller bara länkarna till de två tabellerna.

Om du lägger till ett element i listan bör du därför kunna fylla i en lista från en av de två länkarna i relationstabellen.

Exempel på en relationstabell i ett schema:

```xml
<srcSchema name="subscription" namespace="cus">
  <element name="recipient" type="link" target="cus:recipient" label="Recipient"/>
  <element name="service" type="link" target="cus:service" label="Subscription service"/>
</srcSchema>
```

Vi börjar t.ex. med indataformen för &quot;cus:mottagare&quot;-schemat. Listan måste visa associationer med abonnemang på tjänster och du måste kunna lägga till en prenumeration genom att välja en befintlig tjänst.

![](assets/d_ncs_integration_form_exemple12.png)

```xml
<input type="linklist" xpath="subscription" xpathChoiceTarget="service" xpathEditTarget="service" zoom="true">
  <input xpath="recipient"/>
  <input xpath="service"/>
</input>
```

The **xpathChoiceTarget** kan du starta ett urvalsformulär från den angivna länken. Om du skapar relationstabellposten uppdateras länken till den aktuella mottagaren och den valda tjänsten automatiskt.

>[!NOTE]
>
>The **xpathEditTarget** kan du tvinga fram redigering av den markerade raden på den angivna länken.

### Listegenskaper {#list-properties}

* **noToolbar**: döljer verktygsfältet (med värdet &quot;true&quot;)
* **toolbarCaption**: överför verktygsfältsetiketten
* **toolbarAlign**: ändrar verktygsfältets lodräta eller vågräta geometri (möjliga värden: &quot;vertical&quot;|&quot;horizontal&quot;)
* **img**: visar bilden som är associerad med listan
* **formulär**: överför målelementets redigeringsform
* **zooma**: lägger till **[!UICONTROL Zoom]** för att redigera målelementet
* **xpathEditTarget**: anger redigering för den angivna länken
* **xpathChoiceTarget**: dessutom startar urvalsformuläret på den angivna länken

## Minneslistekontroller {#memory-list-controls}

Med minneslistor kan du redigera samlingselementen med förinläsning av listdata. Listan kan inte filtreras eller konfigureras.

De här listorna används för XML-mappade samlingselement eller på länkar med låg volym.

### Kolumnlista {#column-list}

Den här kontrollen visar en redigerbar kolumnlista med ett verktygsfält som innehåller knapparna Lägg till och Ta bort.

![](assets/d_ncs_integration_form_exemple13.png)

```xml
<input xpath="rcpEvent" type="list">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

Listkontrollen måste fyllas i med **type=&quot;list&quot;** och listans sökväg måste referera till samlingselementet.

Kolumnerna deklareras i det underordnade objektet **`<input>`** -taggar i listan. Kolumnetikett och storlek kan tvingas med **label** och **colSize** attribut.

>[!NOTE]
>
>Sorteringspilarna läggs till automatiskt när **ordered=&quot;true&quot;** -attributet läggs till i samlingselementet i dataschemat.

Verktygsfältsknapparna kan justeras vågrätt:

![](assets/d_ncs_integration_form_exemple14.png)

```xml
<input nolabel="true" toolbarCaption="List of events" type="list" xpath="rcpEvent" zoom="true">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

The **toolbarCaption** -attributet tvingar verktygsfältets vågräta justering och anger titeln ovanför listan.

#### Zooma in en lista {#zoom-in-a-list}

Du kan infoga och redigera data i en lista i ett separat redigeringsformulär.

![](assets/d_ncs_integration_form_exemple15.png)

```xml
<input nolabel="true" toolbarCaption="List of events" type="list" xpath="rcpEvent" zoom="true" zoomOnAdd="true">
  <input xpath="@label"/>
  <input xpath="@date"/>

  <form colcount="2" label="Event">
    <input xpath="@label"/>
    <input xpath="@date"/>
  </form>
</input>
```

Redigeringsformuläret har fyllts i från `<form>` element under listdefinition. Dess struktur är identisk med strukturen för ett indataformulär. The **[!UICONTROL Detail]** knappen läggs till automatiskt när **zoom=&quot;true&quot;** attributet har fyllts i på **`<input>`** -taggen i listan. Med det här attributet kan du starta redigeringsformuläret för den markerade raden.

>[!NOTE]
>
>Lägga till **zoomOnAdd=&quot;true&quot;** gör att redigeringsformuläret anropas när ett listelement infogas.

### Listegenskaper {#list-properties-1}

* **noToolbar**: döljer verktygsfältet (med värdet &quot;true&quot;)
* **toolbarCaption**: överför verktygsfältsetiketten
* **toolbarAlign**: ändrar verktygsfältets placering (möjliga värden: &quot;vertical&quot;|&quot;horizontal&quot;)
* **img**: visar bilden som är associerad med listan
* **formulär**: överför målelementets redigeringsform
* **zooma**: lägger till **[!UICONTROL Zoom]** för att redigera målelementet
* **zoomOnAdd**: öppnar redigeringsformuläret samtidigt
* **xpathChoiceTarget**: dessutom startar urvalsformuläret på den angivna länken

## Icke-redigerbara fält {#non-editable-fields}

Om du vill visa ett fält och förhindra att det redigeras använder du **`<value>`** eller slutföra **readOnly=&quot;true&quot;** på **`<input>`** -tagg.

Exempel på fältet&quot;Kön&quot;:

![](assets/d_ncs_integration_form_exemple16.png)

```xml
<value value="@gender"/>
<input xpath="@gender" readOnly="true"/>
```

## Alternativknapp {#radio-button}

Med en alternativknapp kan du välja mellan flera alternativ. The **`<input>`** -taggar används för att lista möjliga alternativ och **checkedValue** attribute anger värdet som är associerat med valet.

Exempel på fältet&quot;Kön&quot;:

```xml
<input type="RadioButton" xpath="@gender" checkedValue="0" label="Choice 1"/>
<input type="RadioButton" xpath="@gender" checkedValue="1" label="Choice 2"/>
<input type="RadioButton" xpath="@gender" checkedValue="2" label="Choice 3"/>
```

![](assets/d_ncs_integration_form_exemple17.png)

## Kryssruta {#checkbox}

En kryssruta återspeglar ett booleskt läge (markerat eller inte). Som standard används den här kontrollen av fälten &quot;Boolean&quot; (true/false). En variabel med standardvärdet 0 eller 1 kan kopplas till den här knappen. Det här värdet kan laddas över via **checkValue** attribut.

```xml
<input xpath="@boolean1"/>
<input xpath="@field1" type="checkbox" checkedValue="Y"/>
```

![](assets/d_ncs_integration_form_exemple20.png)

## Uppräkning {#enumeration}

<!-- to be completed -->

## Redigera navigeringshierarki {#navigation-hierarchy-edit}

Den här kontrollen skapar ett träd i en uppsättning fält som ska redigeras.

Kontrollerna som ska redigeras grupperas i en **`<container>`** anges under **`<input>`** -tagg för trädkontrollen:

```xml
<input nolabel="true" type="treeEdit">
  <container label="Text fields">
    <input xpath="@text1"/>
    <input xpath="@text2"/>
  </container>
  <container label="Boolean fields">
    <input xpath="@boolean1"/>
    <input xpath="@boolean2"/>
  </container>
</input>
```

![](assets/d_ncs_integration_form_exemple18.png)

## Uttrycksfält {#expression-field}

Ett uttrycksfält uppdaterar ett fält dynamiskt från ett uttryck; den **`<input>`** -taggen används med **xpath** för att ange sökvägen till fältet som ska uppdateras och ett **visa** attribut som innehåller uppdateringsuttrycket.

```xml
<!-- Example: updating the boolean1 field from the value contained in the field with path /tmp/@flag -->
<input expr="Iif([/tmp/@flag]=='On', true, false)" type="expr" xpath="@boolean1"/>
<input expr="[/ignored/@action] == 'FCP'" type="expr" xpath="@launchFCP"/>
```

## Formulärsammanhang {#context-of-forms}

Körningen av ett inmatningsformulär initierar ett XML-dokument som innehåller data för enheten som redigeras. Det här dokumentet representerar formulärets kontext och kan användas som en arbetsyta.

### Uppdaterar kontexten {#updating-the-context}

Om du vill ändra formulärets sammanhang använder du `<set expr="<value>" xpath="<field>"/>` tagg, var `<field>` är målfältet, och `<value>` är uppdateringsuttrycket eller -värdet.

Exempel på användning av `<set>` tagg:

* **`<set expr="'Test'" xpath="/tmp/@test" />`**: placerar värdet för Test på den temporära platsen /tmp/@test1
* **`<set expr="'Test'" xpath="@lastName" />`**: uppdaterar entiteten för attributet lastName med värdet Test
* **`<set expr="true" xpath="@boolean1" />`**: ställer in värdet för fältet &quot;boolean1&quot; till &quot;true&quot;
* **`<set expr="@lastName" xpath="/tmp/@test" />`**: uppdateras med innehållet i attributet&quot;lastName&quot;

Formulärets sammanhang kan uppdateras när formuläret initieras och stängs via **`<enter>`** och **`<leave>`** -taggar.

```xml
<form name="recipient" namespace="cus">
  <enter>
    <set…
  </enter>
  …
  <leave>
    <set…
  </leave>
</form>
```

>[!NOTE]
>
>The `<enter>` och `<leave>` -taggar kan användas på `<container>` av sidor (&quot;anteckningsbok&quot; och&quot;ikon&quot;).

### Uttrycksspråk {#expression-language-}

Ett makrospråk kan användas i formulärdefinitionen för att utföra villkorstester.

The **`<if expr="<expression>" />`** -taggen kör instruktionerna som anges under -taggen om uttrycket verifieras:

```xml
<if expr="([/tmp/@test] == 'Test' or @lastName != 'Doe') and @boolean2 == true">
  <set xpath="@boolean1" expr="true"/>
</if>
```

The **`<check expr="<condition>" />`** -taggen kombinerat med **`<error>`** -taggen förhindrar validering av formuläret och visar ett felmeddelande om villkoret inte uppfylls:

```xml
<leave>
  <check expr="/tmp/@test != ''">
    <error>You must populate the 'Test' field!</error> 
  </check>
</leave>
```

<!-- changer exemple par un exemple plus parlant. cf. vidéo validation 02:27. noter aussi l'attribut required dans l'exemple de la vidéo. -->

## Guider {#wizards}

En guide hjälper dig genom en uppsättning datainmatningssteg i form av sidor. De data som anges sparas när du validerar formuläret.

En guide har följande struktur:

```xml
<form type="wizard" name="example" namespace="cus" img="nms:rcpgroup32.png" label="Wizard example" entity-schema="nms:recipient">
  <container title="Title of page 1" desc="Long description of page 1">
    <input xpath="@lastName"/>
    <input xpath="comment"/>
  </container>
  <container title="Title of page 2" desc="Long description of page 2">
    …
  </container>
  …
</form>
```

![](assets/d_ncs_integration_form_exemple19.png)

Förekomsten av **type=&quot;wizard&quot;** på `<form>` kan du definiera guideläget när du skapar formuläret. Sidorna har fyllts i från `<container>` -element, som är underordnade `<form>` -element. The `<container>` -elementet på en sida fylls i med rubrikattributen för rubriken och desc för att visa beskrivningen under sidrubriken. The **[!UICONTROL Previous]** och **[!UICONTROL Next]** läggs knappar automatiskt till så att du kan bläddra mellan sidor.

The **[!UICONTROL Finish]** sparar de data som anges och stänger formuläret.

### SOAP-metoder {#soap-methods}

Körning av SOAP-metoder kan startas från en ifylld **`<leave>`** -taggen i slutet av en sida.

The **`<soapcall>`** -taggen innehåller anropet till metoden med följande indataparametrar:

```xml
<soapCall name="<name>" service="<schema>">
  <param  type="<type>" exprIn="<xpath>"/>  
  …
</soapCall>
```

Namnet på tjänsten och dess implementeringsschema anges via **name** och **service** attribut för **`<soapcall>`** -tagg.

Indataparametrarna beskrivs på **`<param>`** element under **`<soapcall>`** -tagg.

Parametertypen måste anges via **type** -attribut. Möjliga typer är:

* **string**: teckensträng
* **boolesk**: Boolean
* **byte**: 8-bitars heltal
* **kort**: 16-bitars heltal
* **long**: 32-bitars heltal
* **kort**: 16-bitars heltal
* **double**: flyttal med dubbel precision
* **DOMElement**: elementtypsnod

The **exprIn** -attributet innehåller platsen för de data som ska skickas som en parameter.

**Exempel**:

```xml
<leave>
  <soapCall name="RegisterGroup" service="nms:recipient">         
    <param  type="DOMElement"    exprIn="/tmp/entityList"/>         
    <param  type="DOMElement"    exprIn="/tmp/choiceList"/>         
    <param  type="boolean"       exprIn="true"/>       
  </soapCall>
</leave>
```
