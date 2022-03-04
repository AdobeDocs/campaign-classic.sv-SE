---
product: campaign
title: 'Kom igång med webbapplikationer '
description: Skapa och dela dynamiska webbapplikationer, landningssidor och enkäter
feature: Landing Pages, Web Apps
exl-id: df58221f-f71b-49d5-a6a1-c81ddff27fdb
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 20%

---

# Kom igång med webbapplikationer {#about-web-applications}

![](../../assets/common.svg)

Med Adobe Campaign kan du skapa och publicera dynamiska och interaktiva webbapplikationer med data från databasen och innehåll som är anpassat efter den anslutna användarens rättigheter.

Du kan skapa sidor, t.ex. ett redigeringsformulär på ett extranät, eller meddelandeformulär som innehåller data från databasen med tabeller, diagram, indataformulär osv. Med den här funktionen kan du utforma och publicera webbsidor där användarna kan leta upp eller ange information.

Detta kan vara ett prenumerationsformulär som innehåller data som har förinlästs med information som finns i Adobe Campaign-databasen, vilket visas nedan:

![](assets/webapp_form_sample.png)

I det här kapitlet finns en översikt över hur du hanterar webbprogram.

>[!NOTE]
>
>Se [Checklista för säkerhet och integritet](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/security-privacy/get-started-security-privacy.html?lang=sv) om du vill veta hur du optimerar säkerheten för webbprogram.

>[!CAUTION]
>
>Av sekretesskäl rekommenderar vi att du använder HTTPS för alla externa resurser.

## Webbprogramsomfång {#web-application-scope}

Webbprogram i Adobe Campaign har följande funktioner:

* Skapa flersidiga formulär. Se denna [sida](about-web-forms.md) för mer information om detta.
* Hantering av flerspråkiga enkäter med ett integrerat översättningsverktyg. Se denna [sida](translating-a-web-application.md) för mer information om detta.
* Grafiskt sidhanteringsgränssnitt, sidlayout med flera kolumner. Se denna [sida](designing-a-web-application.md) för mer information om detta.
* Återger personalisering och fältposition. Se denna [sida](editing-content.md#adding-personalization-content) för mer information om detta.
* Villkorlig visning av undersökningsfält enligt svar. Se denna [sida](form-rendering.md#defining-fields-conditional-display) för mer information om detta.
* Slumpmässig visning av frågor. Se denna [sida](../../surveys/using/building-a-survey.md#adding-questions) för mer information om detta.
* Villkorlig sidvisning. Se denna [sida](defining-web-forms-page-sequencing.md#conditional-page-display) för mer information om detta.
* Informationskontroll före validering beroende på den förväntade datatypen (nummer, e-postadress, datum osv.) och de obligatoriska fälten. Se denna [sida](form-rendering.md#defining-control-settings) för mer information om detta.
* E-postinbjudningar eller meddelanden. Se denna [sida](publishing-a-web-form.md#delivering-a-form-via-email) för mer information om detta.
* Personalisering av fel- och slutmeddelanden. Se denna [sida](defining-web-forms-properties.md#setting-up-an-error-page) för mer information om detta.
* Användning av bilder, videor, hypertextlänkar, captcha osv. Se denna [sida](editing-content.md) för mer information om detta.
* Övervakning av svar i realtid. Se denna [sida](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking) för mer information om detta.

Valfritt **Undersökning** i modulen Skapa finns följande funktioner:

* Databasens dynamiska tillägg: Skapa svar som inte ingår i den ursprungliga datamallen. Se denna [sida](../../surveys/using/managing-answers.md#storing-collected-answers) för mer information om detta.
* Genererar dedikerade rapporter. Se denna [sida](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys) för mer information om detta.

Jämfört med webbprogram har enkäterna ett förenklat grafiskt gränssnitt med ett reducerat antal redigeringskontroller.

>[!NOTE]
>
>Undersökningar finns i [det här avsnittet](../../surveys/using/about-surveys.md).
>
>De allmänna funktionerna för webbformulär i Adobe Campaign beskrivs i [det här avsnittet](about-web-forms.md).

## Implementering av webbapplikationer {#web-application-implementation}

Om du vill skapa och publicera ett webbprogram måste du:

1. Skapa innehållet (fält, listor, tabeller, diagram osv.).

   Du kan även visa avsnittet som innehåller information om tillgängliga formulärfält: alla dessa fält är också tillgängliga för webbprogram. Denna information finns i [den här sidan](adding-fields-to-a-web-form.md).

1. Vid behov kan du lägga till förinläsnings-, test- och sparningssteg och konfigurera åtkomstkontrollsystemet (huvudsakligen inom ramen för en extranätpublikation).
1. Publicera webbprogrammet så att det blir tillgängligt på ett extranät eller i Adobe Campaign.

## Ursprunglig konfiguration för webbprogram {#web-application-initial-configuration}

Webbprogram skapas via **[!UICONTROL Web Applications]** i **[!UICONTROL Campaigns]** och **[!UICONTROL Profiles and targets]** -tabbar.

Webbprogram lagras i **[!UICONTROL Resources > Online > Web Applications]** noden i Adobe Campaign-trädet. Konfigurationerna är uppdelade i följande mappar:

* **[!UICONTROL Administration > Configuration > Form renderings]**: innehåller återgivningsmallar för webbformulärpresentationen (program och undersökningar). Med mallen kan du generera formuläret. En CSS-formatmall används också. Den här formatmallen kan överladdas på mallnivå. Mer information finns på [den här sidan](form-rendering.md#selecting-the-form-rendering-template).
* **[!UICONTROL Resources > Templates > Web application templates]**: innehåller formulärmallar. Om du vill skapa ett formulär eller ett webbprogram måste du utgå från en mall.

## Mallar för webbprogram {#web-application-templates}

Som standard tillhandahåller Adobe Campaign en mall per tillgängligt webbprogram.

>[!NOTE]
>
>Du kan konvertera ett befintligt webbprogram till en mall. Om du vill göra det markerar du formuläret och högerklickar. Välj **[!UICONTROL Actions > Save as template...]**.

Du kan skapa nya mallar via **[!UICONTROL Resources > Templates > Web Application templates]** noden i Adobe Campaign-trädet.

Med guiden Skapa kan du välja de alternativ som du vill aktivera, vilket visas nedan.

![](assets/webapp_create_template.png)

>[!CAUTION]
>
>Vilka program som är tillgängliga beror på vilka alternativ och moduler du har. Kontrollera licensavtalet.
