---
product: campaign
title: Kom igång med undersökningar
description: Kom igång med Campaign-enkäter
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 1%

---

# Kom igång med undersökningar{#about-surveys}

Adobe Campaign innehåller en grafisk modul för att definiera och publicera webbapplikationer. Detta används för att skapa sidor, t.ex. ett redigeringsformulär på ett extranät, eller meddelandeformulär som innehåller data från databasen med tabeller, diagram, indataformulär osv. Med den här funktionen kan du utforma och publicera webbsidor där användarna kan leta upp eller ange information.

Med den valfria modulen **Survey** kan du skapa en ny typ av webbprogram för att skapa och hantera onlineenkäter, t.ex. formulär för att lägga till eller ändra profilinformation, för att prenumerera på eller avbryta en prenumeration på en informationstjänst eller ett tävlingsformulär. När svaren har samlats in lagras de i databasen eller i lokala variabler. Datamodellen kan utökas dynamiskt via svar på enkäter. Du kan visa resultaten i realtid, filtrera svaren och analysera dem med dedikerade diagram.

I det här kapitlet beskrivs metoden för att skapa och hantera **undersökningar**, fält- och sidhantering, lagringslägen och poster.

Stegen för att skapa ett standardwebbformulär beskrivs i [det här avsnittet](../../web/using/about-web-forms.md).

Hantering av webbprogram beskrivs i [det här avsnittet](../../web/using/about-web-applications.md). Mer information finns i det här kapitlet.

>[!CAUTION]
>
>Av sekretesskäl rekommenderar vi att du använder HTTPS för alla externa resurser.

## Funktionsomfång {#campaign-surveys-scope}

I Adobe Campaign kan du använda följande funktioner i webbprogram:

* Skapa formulär på flera sidor,
* Hantering av flerspråkiga enkäter med ett integrerat översättningsverktyg
* Grafiskt sidhanteringsgränssnitt, sidlayout med flera kolumner,
* Återgivning av personalisering och fältposition,
* Villkorlig visning av undersökningsfält enligt svar,
* Villkorlig sidvisning,
* Kontrollera information före godkännande, beroende på vilken typ av data som förväntas (nummer, e-postadress, datum osv.) och obligatoriska fält,
* Inbjudningar/meddelanden via e-post
* Anpassning av fel- och slutmeddelanden.
* Användning av bilder, videor, hypertextlänkar, captcha osv.

>[!NOTE]
>
>Alla konfigurationer som är länkade till webbformulär beskrivs i [det här avsnittet](../../web/using/about-web-forms.md). Läs det här dokumentet för mer information om koncept och om webbformulärsfunktioner som använder Adobe Campaign.

Modulen för att skapa enkäter (**Enkät**) erbjuder följande extrafunktioner:

* Databasens dynamiska tillägg: skapa svar som inte ingår i den ursprungliga datamodellen. Mer information finns i [Lagra insamlade svar](../../web/using/managing-answers.md#storing-collected-answers).
* Poänghantering. Mer information finns i [Scores Management](../../web/using/managing-answers.md#score-management).
* Slumpmässig visning av frågor. Mer information finns i [Lägga till frågor](../../web/using/building-a-survey.md#adding-questions).
* Spårning av svar i realtid. Mer information finns i [Svarsspårning](../../web/using/publish--track-and-use-collected-data.md#response-tracking).
* Genererar dedikerade rapporter. Mer information finns i [Undersökningsrapporter](../../web/using/publish--track-and-use-collected-data.md#reports-on-surveys).

Jämfört med webbprogram har enkäterna ett förenklat grafiskt gränssnitt med ett reducerat antal redigeringskontroller.

## Undersöker implementeringssteg {#surveys-implementation-steps}

Följ de här stegen för att skapa och leverera en enkät och bearbeta resultaten:

1. Skapa sidorna i undersökningen och deras innehåll (inmatningsfält, nedrullningsbara listor, frågor osv.).
1. Definiera hur svaren ska sparas.

   Det går att infoga ett steg för förhandsladdning av data så att formuläret kan läsas in i förväg med data som redan finns i databasen. Du kan också lägga till en testruta.

1. Publicera och skicka sedan enkäten till mottagarna (t.ex. ta med en länk i en leverans eller på en webbplats).
1. Övervaka svar och visa rapporter.

Mer information om konfiguration och sekvensering av dessa steg finns i [det här avsnittet](../../web/using/about-web-forms.md). Endast konfigurationer som är specifika för undersökningar beskrivs i det här kapitlet.

## Konfiguration av enkäter {#surveys-configuration}

Undersökningar lagras i noden **[!UICONTROL Resources > Online > Web Applications]** i Adobe Campaign-trädet. Konfigurationer finns i följande mappar:

* **[!UICONTROL Administration > Configuration > Form rendering]**: innehåller återgivningsmallar för webbformulärpresentation (program och undersökningar).
* **[!UICONTROL Resources > Templates > Web application templates]**: innehåller formulärmallarna. Om du vill skapa ett formulär måste du börja med en mall.

>[!NOTE]
>
>Konfigurationsinformation finns i [det här avsnittet](../../web/using/about-web-forms.md).
