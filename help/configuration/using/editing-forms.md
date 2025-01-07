---
product: campaign
title: Redigera formulär
description: Redigera formulär
feature: Configuration
role: Data Engineer, Developer
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1707'
ht-degree: 1%

---


# Redigera formulär{#editing-forms}

## Översikt

Marknadsförare och operatörer använder indataformulär för att skapa, ändra och förhandsgranska poster. Forms visar en visuell representation av information.

Du kan skapa och ändra indataformulär:

* Du kan ändra de fabriksinmatningsformulär som levereras som standard. Fabriksindataformulären är baserade på fabriksdatascheman.
* Du kan skapa anpassade inmatningsformulär baserade på datamappningar som du definierar.

Forms är entiteter av typen `xtk:form`. Du kan visa indataformulärstrukturen i schemat `xtk:form`. Om du vill visa det här schemat väljer du **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** på menyn. Läs mer om [formulärstrukturen](form-structure.md).

Välj **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** på menyn för att få åtkomst till indataformulär:

![](assets/d_ncs_integration_form_arbo.png)

Om du vill utforma formulär redigerar du XML-innehållet i XML-redigeraren:

![](assets/d_ncs_integration_form_edit.png)

[Läs mer](form-structure.md#formatting).

Om du vill förhandsgranska ett formulär klickar du på fliken **[!UICONTROL Preview]**:

![](assets/d_ncs_integration_form_preview.png)

## Formulärtyper

Du kan skapa olika typer av indataformulär. Formulärtypen avgör hur användarna navigerar i formuläret:

* Konsolskärm

  Det här är standardformulärtypen. Formuläret består av en enda sida.

  ![](assets/console_screen_form.png)

* Innehållshantering

  Använd den här formulärtypen för innehållshantering. Se det här [användningsexemplet](../../delivery/using/use-case-creating-content-management.md).

  ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Assistent

  Formuläret innehåller flera flytande skärmar som ordnas i en viss sekvens. Användarna navigerar från en skärm till nästa. [Läs mer](form-structure.md#wizards).

* Ikoner

  Formuläret består av flera sidor. Användarna kan navigera i formuläret genom att markera ikoner till vänster om formuläret.

  ![](assets/iconbox_form_preview.png)

* Anteckningsbok

  Formuläret består av flera sidor. Användarna kan navigera i formuläret genom att markera flikar högst upp i formuläret.

  ![](assets/notebook_form_preview.png)

* Lodrät ruta

  I det här formuläret visas ett navigeringsträd.

* Vågrät ruta

  I det här formuläret visas en lista med objekt.

## Behållare

I formulär kan du använda behållare för olika syften:

* Ordna innehåll i formulär
* Definiera åtkomst till inmatningsfält
* Kapsla in formulär i andra formulär

[Läs mer](form-structure.md#containers).

### Ordna innehåll

Använd behållare för att ordna innehåll i formulär:

* Du kan gruppera fält i avsnitt.
* Du kan lägga till sidor i flersidiga formulär.

Använd elementet `<container>` om du vill infoga en behållare. [Läs mer](form-structure.md#containers).

#### Gruppera fält

Använd behållare för att gruppera inmatningsfält i ordnade avsnitt.

Använd följande element om du vill infoga ett avsnitt i ett formulär: `<container type="frame">`. Om du vill lägga till en avsnittsrubrik använder du attributet `label`.

Syntax: `<container type="frame" label="`*section_title*`"> […] </container>`

I det här exemplet definierar en behållare avsnittet **Skapa** som omfattar indatafälten **[!UICONTROL Created by]** och **[!UICONTROL Name]**:

```xml
<form _cs="Coupons (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Coupons"
      name="coupon" namespace="nms" type="default" xtkschema="xtk:form">
  <input xpath="@code"/>
  <input xpath="@type"/>
  <container label="Creation" type="frame">
    <input xpath="createdBy"/>
    <input xpath="createdBy/@name"/>
  </container>
</form>
```

![](assets/console_screen_form.png)

#### Lägga till sidor i flersidiga formulär

För flersidiga formulär använder du en behållare för att skapa en formulärsida.

I det här exemplet visas behållare för sidorna **Allmänt** och **Detaljer** i ett formulär:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### Definiera åtkomst till fält

Använd behållare för att definiera vad som är synligt och för att definiera åtkomst till fält. Du kan aktivera och inaktivera fältgrupper.

### Kapsla formulär

Använd behållare för att kapsla in formulär i andra formulär. [Läs mer](#add-pages-to-multipage-forms).

## Referenser till bilder

Om du vill söka efter bilder väljer du **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** på menyn.

Om du vill associera en bild med ett element i formuläret, till exempel en ikon, kan du lägga till en referens till en bild. Använd attributet `img` i elementet `<container>`.

Syntax: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

I det här exemplet visas referenser till bilderna `book.png` och `detail.png` från namnområdet `ncm`:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

De här bilderna används för ikoner som användare klickar på för att navigera i ett flersidigt formulär:

![](assets/nested_forms_preview.png)


## Skapa ett enkelt formulär {#create-simple-form}

Så här skapar du ett formulär:

1. Välj **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]** på menyn.
1. Klicka på knappen **[!UICONTROL New]** överst till höger i listan.

   ![](assets/input-form-create-1.png)

1. Ange formuläregenskaperna:

   * Ange formulärnamnet och namnutrymmet.

     Formulärnamnet och namnutrymmet kan matcha det relaterade dataschemat.  I det här exemplet visas ett formulär för databasschemat `cus:order`:

     ```xml
     <form entitySchema="xtk:form" img="xtk:form.png" label="Order" name="order" namespace="cus" type="iconbox" xtkschema="xtk:form">
       […]
     </form>
     ```

     Du kan också uttryckligen ange dataschemat i attributet `entity-schema`.

     ```xml
     <form entity-schema="cus:stockLine" entitySchema="xtk:form" img="xtk:form.png" label="Stock order" name="stockOrder" namespace="cus" xtkschema="xtk:form">
       […]
     </form>
     ```

   * Ange etiketten som ska visas i formuläret.
   * Du kan också ange formulärtypen. Om du inte anger någon formulärtyp används skärmtypen för konsolen som standard.

     ![](assets/input-form-create-2.png)

     Om du utformar ett flersidigt formulär kan du utelämna formulärtypen i elementet `<form>` och ange typen i en behållare.

1. Klicka på **[!UICONTROL Save]**.

1. Infoga formulärelementen.

   Om du till exempel vill infoga ett inmatningsfält använder du elementet `<input>`. Ange attributet `xpath` som fältreferens som ett XPath-uttryck. [Läs mer](schema-structure.md#referencing-with-xpath).

   I det här exemplet visas indatafält baserade på schemat `nms:recipient`.

   ```xml
   <input xpath="@firstName"/>
   <input xpath="@lastName"/>
   ```

1. Om formuläret baseras på en viss schematyp kan du söka efter fälten för det här schemat:

   1. Klicka på **[!UICONTROL Insert]** > **[!UICONTROL Document fields]**.

      ![](assets/input-form-create-4.png)

   1. Markera fältet och klicka på **[!UICONTROL OK]**.

      ![](assets/input-form-create-5.png)

1. Du kan även ange fältredigeraren.

   En standardredigerare för fält är associerad med varje datatyp:
   * För datumfält visar formuläret en indatakalender.
   * För ett uppräkningstypfält visas en urvalslista i formuläret.

   Du kan använda dessa fältredigerartyper:

   | Fältredigerare | Formulärattribut |
   | --- | --- |
   | Alternativknapp | `type="radiobutton"` |
   | Kryssruta | `type="checkbox"` |
   | Redigera träd | `type="tree"` |

   Läs mer om [minneslistkontroller](form-structure.md#memory-list-controls).

1. Du kan även definiera åtkomst till fälten:

   | Element | Attribut | Beskrivning |
   | --- | --- | --- |
   | `<input>` | `read-only="true"` | Ger skrivskyddad åtkomst till ett fält |
   | `<container>` | `type="visibleGroup" visibleIf="`*edit-expr*`"` | Visar en grupp fält villkorligt |
   | `<container>` | `type="enabledGroup" enabledIf="`*edit-expr*`"` | Aktiverar en grupp fält villkorligt |

   Exempel:

   ```xml
   <container type="enabledGroup" enabledIf="@gender=1">
     […]
   </container>
   <container type="enabledGroup" enabledIf="@gender=2">
     […]
   </container>
   ```

1. Du kan också använda behållare för att gruppera fält i avsnitt.

   ```xml
   <container type="frame" label="Name">
      <input xpath="@firstName"/>
      <input xpath="@lastName"/>
   </container>
   <container type="frame" label="Contact details">
      <input xpath="@email"/>
      <input xpath="@phone"/>
   </container>
   ```

   ![](assets/input-form-create-3.png)

## Skapa ett flersidigt formulär {#create-multipage-form}

Du kan skapa flersidiga formulär. Du kan också kapsla in formulär i andra formulär.

### Skapa ett `iconbox`-formulär

Använd formulärtypen `iconbox` för att visa ikoner till vänster om formuläret, som tar användarna till olika sidor i formuläret.

![](assets/iconbox_form_preview.png)

Så här ändrar du typen av ett befintligt formulär till `iconbox`:

1. Ändra attributet `type` för elementet `<form>` till `iconbox`:

   ```xml
   <form […] type="iconbox">
   ```

1. Ange en behållare för varje formulärsida:

   1. Lägg till ett `<container>`-element som underordnat element till elementet `<form>`.
   1. Om du vill definiera en etikett och en bild för ikonen använder du attributen `label` och `img`.

      ```xml
      <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="iconbox" xtkschema="xtk:form">
          <container img="xtk:properties.png" label="General">
              <input xpath="@label"/>
              <input xpath="@name"/>
              […]
          </container>
          <container img="nms:msgfolder.png" label="Details">
              <input xpath="@address"/>
              […]
          </container>
          <container img="nms:supplier.png" label="Services">
              […]
          </container>
      </form>
      ```

   Du kan också ta bort attributet `type="frame"` från de befintliga `<container>`-elementen.

### Skapa ett anteckningsboksformulär

Använd formulärtypen `notebook` om du vill visa flikar högst upp i formuläret, vilket tar användarna till olika sidor.

![](assets/notebook_form_preview.png)

Så här ändrar du typen av ett befintligt formulär till `notebook`:

1. Ändra attributet `type` för elementet `<form>` till `notebook`:

   ```xml
   <form […] type="notebook">
   ```

1. Lägg till en behållare för varje formulärsida:

   1. Lägg till ett `<container>`-element som underordnat element till elementet `<form>`.
   1. Använd attributen `label` och `img` för att definiera ikonens etikett och bild.

   ```xml
     <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="notebook" xtkschema="xtk:form">
         <container label="General">
             <input xpath="@label"/>
             <input xpath="@name"/>
             […]
         </container>
         <container label="Details">
             <input xpath="@address"/>
             […]
         </container>
         <container label="Services">
             […]
         </container>
     </form>
   ```

   Du kan också ta bort attributet `type="frame"` från de befintliga `<container>`-elementen.

### Kapsla formulär

Du kan kapsla in formulär i andra formulär. Du kan t.ex. kapsla anteckningsboksformulär i ikonboxformulär.

Nivån för navigering i kapslingskontroller. Användare kan gå ned på djupet i delformulär.

Om du vill kapsla ett formulär i ett annat formulär infogar du ett `<container>`-element och ställer in attributet `type` på formulärtypen. För formuläret på den översta nivån kan du ange formulärtypen i en yttre behållare eller i elementet `<form>`.

### Exempel

I det här exemplet visas ett komplext formulär:

* Formuläret på den översta nivån är ett ikonformulär. Det här formuläret består av två behållare med etiketterna **Allmänt** och **Detaljer**.

  Det innebär att det yttre formuläret visar sidorna **Allmänt** och **Detaljer** på den översta nivån. Användarna kommer åt dessa sidor genom att klicka på ikonerna till vänster i formuläret.

* Delformuläret är ett anteckningsboksformulär som är kapslat i behållaren **Allmänt** . Delformuläret består av två behållare med etiketterna **Namn** och **Kontakt**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

På sidan **Allmänt** i det yttre formuläret visas flikarna **Namn** och **Kontakt**.

![](assets/nested_forms_preview.png)

Om du vill kapsla ett formulär i ett annat formulär infogar du ett `<container>`-element och ställer in attributet `type` på formulärtypen. För formuläret på den översta nivån kan du ange formulärtypen i en yttre behållare eller i elementet `<form>`.

### Exempel

I det här exemplet visas ett komplext formulär:

* Formuläret på den översta nivån är ett ikonformulär. Det här formuläret består av två behållare med etiketterna **Allmänt** och **Detaljer**.

  Det innebär att det yttre formuläret visar sidorna **Allmänt** och **Detaljer** på den översta nivån. Användarna kommer åt dessa sidor genom att klicka på ikonerna till vänster i formuläret.

* Delformuläret är ett anteckningsboksformulär som är kapslat i behållaren **Allmänt** . Delformuläret består av två behållare med etiketterna **Namn** och **Kontakt**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

På sidan **Allmänt** i det yttre formuläret visas flikarna **Namn** och **Kontakt**.

![](assets/nested_forms_preview.png)



## Ändra ett fabriksinmatningsformulär {#modify-factory-form}

Så här ändrar du ett fabriksformulär:

1. Ändra fabriksinmatningsformuläret:

   1. Välj **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]** på menyn.
   1. Markera ett inmatningsformulär och ändra det.

   Du kan utöka fabriksdatamappningar, men du kan inte utöka fabriksinmatningsformulär. Vi rekommenderar att du ändrar fabriksinmatningsformulär direkt utan att återskapa dem. Vid uppgraderingar sammanfogas ändringarna i fabriksinmatningsformulären med uppgraderingarna. Om den automatiska sammanfogningen misslyckas kan du lösa konflikterna. [Läs mer](../../production/using/upgrading.md#resolving-conflicts).

   Om du till exempel utökar ett fabriksschema med ett extra fält kan du lägga till det här fältet i det relaterade fabriksformuläret.

## Validera formulär {#validate-forms}

Du kan inkludera valideringskontroller i formulär.

### Bevilja skrivskyddad åtkomst till fält

Använd attributet `readOnly="true"` om du vill ge skrivskyddad åtkomst till ett fält. Du kanske vill visa primärnyckeln för en post, men med skrivskyddad åtkomst. [Läs mer](form-structure.md#non-editable-fields).

I det här exemplet visas primärnyckeln (`iRecipientId`) för schemat `nms:recipient` med skrivskyddad åtkomst:

```xml
<value xpath="@iRecipientId" readOnly="true"/>
```

### Kontrollera obligatoriska fält

Du kan kontrollera obligatorisk information:

* Använd attributet `required="true"` för de obligatoriska fälten.
* Använd noden `<leave>` för att kontrollera fälten och visa felmeddelanden.

I det här exemplet krävs e-postadressen och ett felmeddelande visas om användaren inte har angett den här informationen:

```xml
<input xpath="@email" required="true"/>
<leave>
  <check expr="@email!=''">
    <error>The email address is required.</error>
  </check>
</leave>
```

Läs mer om [uttrycksfält](form-structure.md#expression-field) och [formulärkontext](form-structure.md#context-of-forms).

### Validera värden

Du kan använda JavaScript SOAP-anrop för att validera formulärdata från konsolen. Använd dessa anrop för komplex validering, till exempel för att kontrollera ett värde mot en lista över godkända värden. [Läs mer](form-structure.md#soap-methods).

1. Skapa en valideringsfunktion i en JS-fil.

   Exempel:

   ```js
   function nms_recipient_checkValue(value)
   {
     logInfo("checking value " + value)
     if (…)
     {
       logError("Value " + value + " is not valid")
     }
     return 1
   }
   ```

   I det här exemplet heter funktionen `checkValue`. Den här funktionen används för att kontrollera datatypen `recipient` i namnutrymmet `nms`. Värdet som kontrolleras loggas. Om värdet inte är giltigt loggas ett felmeddelande. Om värdet är giltigt returneras värdet 1.

   Du kan använda det returnerade värdet för att ändra formuläret.

1. Lägg till elementet `<soapCall>` i elementet `<leave>` i formuläret.

   I det här exemplet används ett SOAP-anrop för att validera strängen `@valueToCheck`:

   ```xml
   <form name="recipient" (…)>
   (…)
     <leave>
       <soapCall name="checkValue" service="nms:recipient">
         <param exprIn="@valueToCheck" type="string"/>
       </soapCall>
     </leave>
   </form>
   ```

   I det här exemplet används metoden `checkValue` och tjänsten `nms:recipient`:

   * Tjänsten är namnutrymmet och datatypen.
   * Metoden är funktionsnamnet. Namnet är versalkänsligt.

   Anropet utförs synkront.

   Alla undantag visas. Om du använder elementet `<leave>` kan användarna inte spara formuläret förrän den angivna informationen har validerats.

I det här exemplet visas hur du kan ringa tjänstanrop inifrån formulär:

```xml
<enter>
  <soapCall name="client" service="c4:ybClient">
    <param exprIn="@id" type="string"/>
    <param type="boolean" xpathOut="/tmp/@count"/>
  </soapCall>
</enter>
```

I det här exemplet är indata ett ID, som är en primärnyckel. När användarna fyller i formuläret för detta ID görs ett SOAP med detta ID som indataparameter. Utdata är ett booleskt värde som skrivs till det här fältet: `/tmp/@count`. Du kan använda det här booleska innehållet i formuläret. Läs mer om [formulärkontext](form-structure.md#context-of-forms).
