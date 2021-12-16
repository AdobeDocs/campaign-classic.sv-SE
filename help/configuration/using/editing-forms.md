---
product: campaign
title: Redigera formulär
description: Redigera formulär
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: f4b9ac3300094a527b5ec1b932d204f0e8e5ee86
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 4%

---


# Redigera formulär{#editing-forms}

![](../../assets/common.svg)

## Översikt

Marknadsförare och operatörer använder indataformulär för att skapa, ändra och förhandsgranska poster. Forms visar en visuell representation av information.

Du kan skapa och ändra indataformulär:

* Du kan ändra de fabriksinmatningsformulär som levereras som standard. Fabriksindataformulären är baserade på fabriksdatascheman.
* Du kan skapa anpassade inmatningsformulär baserade på datamappningar som du definierar.

Forms är enheter i `xtk:form` typ. Du kan visa indataformulärstrukturen i dialogrutan `xtk:form` schema. Om du vill visa det här schemat väljer du **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** på menyn. Läs mer om [formulärstruktur](form-structure.md).

Välj **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** på menyn:

![](assets/d_ncs_integration_form_arbo.png)

Om du vill utforma formulär redigerar du XML-innehållet i XML-redigeraren:

![](assets/d_ncs_integration_form_edit.png)

[Läs mer](form-structure.md#formatting).

Om du vill förhandsgranska ett formulär klickar du på **[!UICONTROL Preview]** tab:

![](assets/d_ncs_integration_form_preview.png)

## Formulärtyper

Du kan skapa olika typer av indataformulär. Formulärtypen avgör hur användarna navigerar i formuläret:

* Konsolskärm

   Det här är standardformulärtypen. Formuläret består av en enda sida.

   ![](assets/console_screen_form.png)

* Innehållshantering

   Använd den här formulärtypen för innehållshantering. Se det här [användningsfall](../../delivery/using/use-case--creating-content-management.md).

   ![](../../delivery/using/assets/d_ncs_content_form13.png)

* guide

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

   Det här formuläret innehåller en lista med objekt.

## Behållare

I formulär kan du använda behållare för olika syften:

* Ordna innehåll i formulär
* Definiera åtkomst till inmatningsfält
* Kapsla formulär i andra formulär

[Läs mer](form-structure.md#containers).

### Ordna innehåll

Använd behållare för att ordna innehåll i formulär:

* Du kan gruppera fält i avsnitt.
* Du kan lägga till sidor i flersidiga formulär.

Om du vill infoga en behållare använder du `<container>` -element. [Läs mer](form-structure.md#containers).

#### Gruppera fält

Använd behållare för att gruppera inmatningsfält i ordnade avsnitt.

Om du vill infoga ett avsnitt i ett formulär använder du det här elementet: `<container type="frame">`. Om du vill lägga till en avsnittsrubrik använder du `label` -attribut.

Syntax: `<container type="frame" label="`*section_title*`"> […] </container>`

I det här exemplet definierar en behållare **Skapande** som innehåller **[!UICONTROL Created by]** och **[!UICONTROL Name]** indatafält:

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

I det här exemplet visas behållare för **Allmänt** och **Detaljer** sidor i ett formulär:

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

Välj **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** på menyn.

Om du vill associera en bild med ett element i formuläret, till exempel en ikon, kan du lägga till en referens till en bild. Använd `img` -attribut, till exempel i `<container>` -element.

Syntax: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

I det här exemplet visas referenser till `book.png` och `detail.png` bilder från `ncm` namnutrymme:

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
