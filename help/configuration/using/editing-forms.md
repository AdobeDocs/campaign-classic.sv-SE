---
product: campaign
title: Redigera formulär
description: Redigera formulär
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: a6549ad4d94b93d65752df66aeec39b90e4c3ec5
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 5%

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

