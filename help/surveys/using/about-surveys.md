---
product: campaign
title: Kom igång med undersökningar
description: Kom igång med Campaign-enkäter
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Surveys
exl-id: 7061a4f1-006f-4f19-8761-918d8930d885
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 4%

---

# Kom igång med undersökningar{#about-surveys}



Adobe Campaign innehåller en grafisk modul för att definiera och publicera webbapplikationer. Detta används för att skapa sidor, t.ex. ett redigeringsformulär på ett extranät, eller meddelandeformulär som innehåller data från databasen med tabeller, diagram, indataformulär osv. Använd den här funktionen för att utforma och publicera webbsidor där användarna kan söka efter eller ange information.

Valfritt **Undersökning** Med kan du skapa en ny typ av webbprogram för att skapa och hantera onlineenkäter, t.ex. formulär för att lägga till eller ändra profilinformation, för att prenumerera på eller avbryta en prenumeration på en informationstjänst eller ett tävlingsformulär. När svaren har samlats in lagras de i databasen eller i lokala variabler. Datamodellen kan utökas dynamiskt via svar på enkäter. Du kan visa resultaten i realtid, filtrera svaren och analysera dem med dedikerade diagram.

I det här kapitlet beskrivs hur du skapar och hanterar **Undersökningar**, fält- och sidhantering, lagringslägen och poster.

Lär dig hur du skapar din första enkät i [den här sidan](getting-started-with-surveys.md).

>[!NOTE]
>
>* Detaljerade steg för hur du skapar ett standardwebbformulär finns i [det här dokumentet](../../web/using/about-web-forms.md).
>
>* Hantering av webbapplikationer beskrivs i [det här dokumentet](../../web/using/about-web-applications.md). Mer information finns i det här kapitlet.


## Funktionsomfång {#campaign-surveys-scope}

I Adobe Campaign använder du [Webbprogram](../../web/using/about-web-forms.md) till:

* Skapa flersidiga formulär,
* Hantera flerspråkiga formulär med ett integrerat översättningsverktyg,
* Hantera grafiskt gränssnitt, sidlayout med flera kolumner,
* Lägg till personalisering och definiera fältposition,
* Villkorlig visning av undersökningsfält enligt svar,
* Villkorsidvisning,
* Kontrollera informationen före godkännande, beroende på vilken typ av data som förväntas (nummer, e-postadress, datum osv.) och obligatoriska fält,
* Skicka inbjudningar/meddelanden via e-post,
* Anpassa fel- och slutsidor,
* Lägg till bilder, videor, hypertextlänkar, captcha osv. i formulär

Modulen för att skapa enkäter erbjuder ett användarvänligt gränssnitt och följande extrafunktioner:

* Databasens dynamiska tillägg: skapa svar som inte ingår i den ursprungliga datamodellen. [Läs mer](../../surveys/using/managing-answers.md#storing-collected-answers).
* Poänghantering. [Läs mer](../../surveys/using/managing-answers.md#score-management).
* Slumpmässig visning av frågor. [Läs mer](../../surveys/using/building-a-survey.md#adding-questions).
* Spårning av svar i realtid. [Läs mer](../../surveys/using/publish--track-and-use-collected-data.md#response-tracking).
* Genererar dedikerade rapporter. [Läs mer](../../surveys/using/publish--track-and-use-collected-data.md#reports-on-surveys).


## Implementeringssteg {#surveys-implementation-steps}

Följ de här stegen för att skapa och leverera en enkät och bearbeta resultaten:

1. Skapa sidorna i undersökningen och deras innehåll (inmatningsfält, nedrullningsbara listor, frågor osv.).
1. Definiera hur svaren ska sparas. Det går att infoga ett steg för förhandsladdning av data så att formuläret kan läsas in i förväg med data som redan finns i databasen. Du kan också lägga till en testruta.
1. Publicera och skicka sedan enkäten till mottagarna (t.ex. ta med en länk i en leverans eller på en webbplats).
1. Övervaka svar och visa rapporter.

Mer information om konfiguration och sekvensering av dessa steg finns i [det här dokumentet](../../web/using/about-web-forms.md). Endast konfigurationer som är specifika för undersökningar beskrivs i det här kapitlet.

>[!CAUTION]
>
>Av sekretesskäl rekommenderar vi att du använder HTTPS för alla externa resurser.

## Inställningar {#settings}

Enkäter är som standard tillgängliga i **[!UICONTROL Resources > Online > Web Applications]** noden i Adobe Campaign-trädet.

Inställningarna sparas i följande mappar:

* **[!UICONTROL Administration > Configuration > Form rendering]**: innehåller återgivningsmallar för webbformulärpresentation (program och undersökningar).
* **[!UICONTROL Resources > Templates > Web application templates]**: innehåller formulärmallarna. Om du vill skapa ett formulär måste du börja med en mall.

>[!NOTE]
>
>Inställningsinformation finns i [det här dokumentet](../../web/using/about-web-forms.md).
