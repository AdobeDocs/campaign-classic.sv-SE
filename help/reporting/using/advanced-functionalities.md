---
product: campaign
title: Avancerade funktioner
description: Avancerade funktioner
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: 8b51d0fc-1692-41cd-9aa8-3bb8f4ee454e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 5%

---

# Avancerade funktioner{#advanced-functionalities}

![](../../assets/common.svg)

Som teknisk användare kan du, förutom [allmänna egenskaper](../../reporting/using/properties-of-the-report.md), använda avancerade funktioner för att konfigurera rapporter, som:

* Skapa komplexa frågor för att bearbeta data i en **skriptaktivitet**. [Läs mer](#script-activity)

* Lägg till ett externt skript som ska köras på server- eller klientsidan. [Läs mer](#external-script)

* Anropa en rapport med en **hoppaktivitet**. [Läs mer](#calling-up-another-report)

* Lägg till en URL-parameter i en rapport för att göra den mer tillgänglig. [Läs mer](#calling-up-another-report)

* Lägg till variabler som ska användas i rapportens sammanhang. [Läs mer](#adding-variables)

## Arbeta med skript {#adding-a-script}

### Referera till externa skript {#external-script}

Du kan referera till JavaScript-koder som ska köras på klient- och/eller serversidan när rapportsidan anropas.

Så här gör du:

1. Redigera [rapportegenskaperna](../../reporting/using/properties-of-the-report.md) och klicka på **[!UICONTROL Scripts]**.
1. Klicka på **[!UICONTROL Add]** och välj det skript som ska refereras.
1. Välj sedan körningsläge.

   Om du lägger till flera skript använder du pilarna i verktygsfältet för att definiera deras körningssekvens.

   ![](assets/reporting_custom_js.png)

För normal körning på klientsidan måste de refererade skripten skrivas i JavaScript och måste vara kompatibla med vanliga webbläsare. Mer information om detta finns i [det här avsnittet](../../web/using/web-forms-answers.md).

### Lägga till en skriptaktivitet {#script-activity}

När [du utformar rapporten](../../reporting/using/creating-a-new-report.md#modelizing-the-chart) använder du aktiviteten **[!UICONTROL Script]** för att bearbeta data och enkelt skapa komplexa frågor som inte aktiverar SQL-språket. Du kan skriva in frågan direkt i skriptfönstret.

På fliken **[!UICONTROL Texts]** kan du definiera textsträngar. De kan sedan användas med följande syntax: **$(Identifierare)**. Mer information om hur du använder texter finns i [Lägga till ett sidhuvud och en sidfot](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>Vi rekommenderar INTE att du använder JavaScript-kod för att skapa aggregat.

Om du vill skapa en historik för rapporten lägger du till följande rad i JavaScript-frågan för att spara dina arkiverade data:

```
if( ctx.@_historyId.toString().length == 0 )
```

I annat fall visas bara aktuella data.

## Lägga till en URL-parameter {#defining-additional-settings}

På fliken **[!UICONTROL Parameters]** i [rapportegenskaperna](../../reporting/using/properties-of-the-report.md) kan du definiera ytterligare inställningar för rapporten: dessa inställningar skickas till URL:en under samtalet.

>[!CAUTION]
>
>Av säkerhetsskäl måste dessa parametrar användas med stor försiktighet.

Så här skapar du en ny inställning:

1. Klicka på knappen **[!UICONTROL Add]** och ange namnet på inställningen.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Ange vid behov om inställningen ska vara obligatorisk eller inte.

1. Välj den typ av inställning som du vill skapa: **[!UICONTROL Filter]** eller **[!UICONTROL Variable]**.

   Med alternativet **[!UICONTROL Filter entities]** kan du använda ett fält i databasen som en parameter.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   Data återställs direkt på entitetsnivå: **ctx/receive/@account**.

   Med alternativet **[!UICONTROL Variable]** kan du skapa eller välja en variabel som skickas som en parameter i URL:en och som kan användas i filtren.

Med **[!UICONTROL Response HTTP headers]** kan du förhindra clickjacking när du inkluderar rapportens sida på en HTML-sida med iframe. Du kan undvika klickjacking genom att välja **[!UICONTROL X-Frame-options header]**-beteendet:

* **[!UICONTROL None]**: Rapporten kommer inte att ha någon  **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Same as origin]**: Ange som standard för nya rapporter och ompublicerade rapporter. Värdnamnet är samma som rapportens URL.
* **[!UICONTROL Deny]**: Rapporten kan inte inkluderas på en HTML-sida med iframe.

![](assets/s_ncs_advuser_report_properties_09c.png)

## Lägga till variabler {#adding-variables}

Fliken **[!UICONTROL Variables]** innehåller listan med variabler som har konfigurerats i rapporten. Dessa variabler exponeras i rapportsammanhang och kan användas i beräkningar.

Klicka på knappen **[!UICONTROL Add]** för att skapa en ny variabel.

Om du vill visa definitionen för en variabel markerar du den och klickar på knappen **[!UICONTROL Detail...]**.

![](assets/s_ncs_advuser_report_properties_10.png)

## Användningsfall: använda variabler och parametrar i en rapport

I videoexemplet nedan får du lära dig hur du lägger till en &quot;_type&quot;-parameter för att skapa olika vyer av en rapport utifrån värdet för det här attributet.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&amp;ref=helpx.adobe.com)


## Anropa en annan rapport {#calling-up-another-report}

En **hoppaktivitet** är som en övergång utan pil: kan du gå från en aktivitet till en annan eller komma åt en annan rapport.
