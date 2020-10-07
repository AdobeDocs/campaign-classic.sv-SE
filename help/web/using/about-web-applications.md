---
title: Om webbapplikationer
description: Skapa och dela dynamiska webbapplikationer, landningssidor och enkäter.
page-status-flag: never-activated
uuid: acfa6e5e-b503-4a1a-871e-e70007874f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 3af763ad-6b0d-4f4c-aed1-c5e12efd4760
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 19%

---


# Kom igång med webbprogram{#about-web-applications}

Med Adobe Campaign kan du skapa och publicera dynamiska och interaktiva webbapplikationer med data från databasen och innehåll som är anpassat efter den anslutna användarens rättigheter.

Du kan skapa sidor, t.ex. ett redigeringsformulär på ett extranät, eller meddelandeformulär som innehåller data från databasen med tabeller, diagram, indataformulär osv. Med den här funktionen kan du utforma och publicera webbsidor där användarna kan leta upp eller ange information.

Detta kan vara ett prenumerationsformulär som innehåller data som har förinlästs med information som finns i Adobe Campaign-databasen, vilket visas nedan:

![](assets/webapp_form_sample.png)

I det här kapitlet finns en översikt över hur du hanterar webbprogram.

>[!NOTE]
>
>Läs checklistan [för](https://helpx.adobe.com/se/campaign/kb/acc-security.html) säkerhet och sekretess om du vill veta hur du optimerar säkerheten för webbprogram.

>[!CAUTION]
>
>Av sekretesskäl rekommenderar vi att du använder HTTPS för alla externa resurser.

## Webbprogramsomfång {#web-application-scope}

Webbprogram i Adobe Campaign har följande funktioner:

* Skapa flersidiga formulär. Se denna [sida](../../web/using/about-web-forms.md) för mer information om detta.
* Hantering av flerspråkiga enkäter med ett integrerat översättningsverktyg. Se denna [sida](../../web/using/translating-a-web-application.md) för mer information om detta.
* Grafiskt sidhanteringsgränssnitt, sidlayout med flera kolumner. Se denna [sida](../../web/using/designing-a-web-application.md) för mer information om detta.
* Återger personalisering och fältposition. Se denna [sida](../../web/using/editing-content.md#adding-personalization-content) för mer information om detta.
* Villkorlig visning av undersökningsfält enligt svar. Se denna [sida](../../web/using/form-rendering.md#defining-fields-conditional-display) för mer information om detta.
* Slumpmässig visning av frågor. Se denna [sida](../../web/using/building-a-survey.md#adding-questions) för mer information om detta.
* Villkorlig sidvisning. Se denna [sida](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display) för mer information om detta.
* Informationskontroll före validering beroende på den förväntade datatypen (nummer, e-postadress, datum osv.) och de obligatoriska fälten. Se denna [sida](../../web/using/form-rendering.md#defining-control-settings) för mer information om detta.
* Skicka inbjudningar eller meddelanden via e-post. Se denna [sida](../../web/using/publishing-a-web-form.md#delivering-a-form-via-email) för mer information om detta.
* Personalisering av fel- och slutmeddelanden. Se denna [sida](../../web/using/defining-web-forms-properties.md#setting-up-an-error-page) för mer information om detta.
* Användning av bilder, videor, hypertextlänkar, captcha osv. Se denna [sida](../../web/using/editing-content.md) för mer information om detta.
* Övervakning av svar i realtid. Se denna [sida](../../web/using/publish--track-and-use-collected-data.md#response-tracking) för mer information om detta.

Den valfria modulen för att skapa **enkäter** har följande extrafunktioner:

* Databasens dynamiska tillägg: Skapa svar som inte ingår i den ursprungliga datamallen. Se denna [sida](../../web/using/managing-answers.md#storing-collected-answers) för mer information om detta.
* Genererar dedikerade rapporter. Se denna [sida](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys) för mer information om detta.

Jämfört med webbprogram har enkäterna ett förenklat grafiskt gränssnitt med ett reducerat antal redigeringskontroller.

>[!NOTE]
>
>Undersökningar finns i [detta avsnitt](../../web/using/about-surveys.md).
>
>De allmänna funktionerna för webbformulär i Adobe Campaign beskrivs i [detta avsnitt](../../web/using/about-web-forms.md).

## Implementering av webbapplikationer {#web-application-implementation}

Om du vill skapa och publicera ett webbprogram måste du:

1. Skapa innehållet (fält, listor, tabeller, diagram osv.).

   Du kan även visa avsnittet som innehåller information om tillgängliga formulärfält: alla dessa fält är också tillgängliga för webbprogram. Den här informationen finns på [den här sidan](../../web/using/adding-fields-to-a-web-form.md).

1. Vid behov kan du lägga till förinläsnings-, test- och sparningssteg och konfigurera åtkomstkontrollsystemet (huvudsakligen inom ramen för en extranätpublikation).
1. Publicera webbprogrammet så att det blir tillgängligt på ett extranät eller i Adobe Campaign.

## Ursprunglig konfiguration för webbprogram {#web-application-initial-configuration}

Webbprogram skapas via **[!UICONTROL Web Applications]** länken på flikarna **[!UICONTROL Campaigns]** och **[!UICONTROL Profiles and targets]** .

Webbprogram lagras i noden **[!UICONTROL Resources > Online > Web Applications]** i Adobe Campaign-trädet. Konfigurationerna är uppdelade i följande mappar:

* **[!UICONTROL Administration > Configuration > Form renderings]**: innehåller återgivningsmallar för webbformulärpresentationen (program och undersökningar). Med mallen kan du generera formuläret. En CSS-formatmall används också. Den här formatmallen kan överladdas på mallnivå. Se denna [sida](../../web/using/form-rendering.md#selecting-the-form-rendering-template) för mer information om detta.
* **[!UICONTROL Resources > Templates > Web application templates]**: innehåller formulärmallar. Om du vill skapa ett formulär eller ett webbprogram måste du utgå från en mall.

## Mallar för webbprogram {#web-application-templates}

Som standard tillhandahåller Adobe Campaign en mall per tillgängligt webbprogram.

>[!NOTE]
>
>Du kan konvertera ett befintligt webbprogram till en mall. Om du vill göra det markerar du formuläret och högerklickar. Välj **[!UICONTROL Actions > Save as template...]**.

Du kan skapa nya mallar via noden **[!UICONTROL Resources > Templates > Web Application templates]** i Adobe Campaign-trädet.

Med guiden Skapa kan du välja de alternativ som du vill aktivera, vilket visas nedan.

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>Vilka program som är tillgängliga beror på vilka alternativ och moduler du har. Kontrollera licensavtalet.

