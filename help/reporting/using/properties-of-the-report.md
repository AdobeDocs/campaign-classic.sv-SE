---
title: Rapportens egenskaper
seo-title: Rapportens egenskaper
description: Rapportens egenskaper
seo-description: null
page-status-flag: never-activated
uuid: 56163f53-d115-45b8-94a5-c173ac4c6533
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 5ec88743-be51-438c-9064-dd0196fdd7d3
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 3%

---


# Rapportens egenskaper{#properties-of-the-report}

## Översikt {#overview}

Ni kan anpassa och konfigurera rapporten efter era behov. Om du vill göra det redigerar du egenskaperna för den. Rapportegenskaper nås via egenskapsknappen ovanför aktivitetssekvensdiagrammet.

![](assets/s_ncs_advuser_report_properties_01.png)

## Övergripande egenskaper {#overall-properties}

På fliken **[!UICONTROL General]** kan du visa eller ändra etiketten och schemat som rapporten gäller. Dessa element anges när rapporten skapas.

Vi rekommenderar inte att du ändrar **[!UICONTROL Internal name]** : detta används i URL:en för rapportåtkomst.

Rapportmallen väljs när rapporten skapas och kan inte ändras senare.

Om du vill ändra tabellen som rapporten gäller klickar du på **[!UICONTROL Select link]** ikonen till höger om **[!UICONTROL Document type]** fältet. Om du vill visa de tillgängliga fälten i den markerade tabellen klickar du på **[!UICONTROL Magnifier]** ikonen .

![](assets/s_ncs_advuser_report_properties_02.png)

## Rapportera tillgänglighet {#report-accessibility}

En rapport kan nås utanför Adobe Campaign-konsolen, till exempel via en webbläsare. I så fall kan det vara nödvändigt att konfigurera åtkomstkontrollen för rapporten enligt nedan.

![](assets/s_ncs_advuser_report_properties_02b.png)

Den övergripande principen är följande:

* Alternativet **[!UICONTROL Anonymous access]** ger obegränsad åtkomst till rapporten. Det går dock inte att manipulera något.

   Rättigheterna för standardrapportoperatorn (&#39;webapp&#39;) används för att visa rapportelement.

* Med det här **[!UICONTROL Access control]** alternativet kan Adobe Campaign-operatörer få åtkomst till det när de har loggat in.
* Med det här **[!UICONTROL Specific account]** alternativet kan du köra rapporten med rättigheter för den operator som är vald i **[!UICONTROL Operator]** fältet.

Egenskaper för webbformulär finns på [den här sidan](../../web/using/about-web-forms.md).

## Hantera rapportlokalisering {#managing-report-localization}

Du kan konfigurera de språk som du vill att rapporten ska översättas till. Klicka på **[!UICONTROL Localization]** fliken om du vill göra det.

![](assets/s_ncs_advuser_report_properties_06.png)

Redigeringsspråket är det språk du skriver på. När du lägger till ett språk visas underfliken på rapportredigeringssidan.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Mer information finns i respektive avsnitt i [detta avsnitt](../../web/using/translating-a-web-form.md).

## Anpassa HTML-återgivning {#personalizing-html-rendering}

På fliken **[!UICONTROL Rendering]** kan du anpassa sidans datavisningsläge. Du kan välja:

* Diagramåtergivningsmotorn: Adobe Campaign har två olika lägen för att generera diagramåtergivning. Som standard är återgivningsmotorn HTML 5. Om det behövs kan du välja Flash-återgivning.
* Navigeringstypen i rapporten: via knappar eller länkar.
* Standardpositionen för etiketter för rapportelement. Den här positionen kan laddas över för varje element.
* Den mall eller det tema som används för att generera rapportsidor.

Egenskaper för webbformulär finns på [den här sidan](../../web/using/about-web-forms.md).

![](assets/s_ncs_advuser_report_properties_08.png)

## Definiera ytterligare inställningar {#defining-additional-settings}

På fliken **[!UICONTROL Parameters]** kan du skapa ytterligare inställningar för rapporten: dessa inställningar skickas till URL:en under samtalet.

Egenskaper för webbformulär finns på [den här sidan](../../web/using/about-web-forms.md).

>[!CAUTION]
>
>Av säkerhetsskäl måste dessa parametrar användas med stor försiktighet.

Så här skapar du en ny inställning:

1. Klicka på **[!UICONTROL Add]** knappen och ange namnet på inställningen.

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. Ange vid behov om inställningen ska vara obligatorisk eller inte.
1. Select the type of setting you want to create: **[!UICONTROL Filter]** or **[!UICONTROL Variable]**.

   Med det här **[!UICONTROL Filter entities]** alternativet kan du använda ett databasfält som parameter.

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   Data återställs direkt på entitetsnivå: **ctx/mottagare/@konto**.

   Med det här **[!UICONTROL Variable]** alternativet kan du skapa eller välja en variabel som ska skickas som en parameter i URL-adressen och som kan användas i filtren.

Med **[!UICONTROL Response HTTP headers]** den kan du förhindra clickjacking när du inkluderar rapportens sida på en HTML-sida med iframe. Du kan undvika klickbara objekt genom att välja **[!UICONTROL X-Frame-options header]** beteendet:

* **[!UICONTROL None]**: Rapporten kommer inte att ha någon **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Same as origin]**: Ange som standard för nya rapporter och ompublicerade rapporter. Värdnamnet är samma som rapportens URL.
* **[!UICONTROL Deny]**: Rapporten kan inte inkluderas på en HTML-sida med iframe.

![](assets/s_ncs_advuser_report_properties_09c.png)

## Lägga till variabler {#adding-variables}

Fliken innehåller **[!UICONTROL Variables]** en lista med variabler som har konfigurerats i rapporten. Dessa variabler exponeras i rapportsammanhang och kan användas i beräkningar.

Klicka på **[!UICONTROL Add]** knappen för att skapa en ny variabel.

Om du vill visa definitionen för en variabel markerar du den och klickar på **[!UICONTROL Detail...]** knappen.

![](assets/s_ncs_advuser_report_properties_10.png)

## Referera skript {#referencing-scripts}

På fliken **[!UICONTROL Scripts]** kan du referera till JavaScript-koder som ska köras på klient- och/eller serversidan när rapportsidan anropas.

För normal körning på klientsidan måste de refererade skripten skrivas i JavaScript och måste vara kompatibla med de flesta webbläsare. Mer information om detta finns i [det här avsnittet](../../web/using/web-forms-answers.md).

## Anpassa felsidan {#personalizing-the-error-page}

På fliken **[!UICONTROL Error page]** kan du konfigurera det meddelande som visas om ett fel uppstår i rapportvisningen.

Du kan definiera texter och länka dem till specifika identifierare för att hantera rapportlokalisering. Mer information finns i [Lägga till ett sidhuvud och en sidfot](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)

