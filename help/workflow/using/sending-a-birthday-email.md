---
product: campaign
title: Skicka ett födelsedagsmeddelande
description: Lär dig hur du skickar ett födelsedagsmeddelande med ett arbetsflöde
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 38006cca-e945-4b9d-8e2d-ed537b8541d9
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 1%

---

# Skicka ett födelsedagsmeddelande{#sending-a-birthday-email}

![](../../assets/common.svg)

## Introduktion {#introduction}

I det här användningsexemplet visas hur du planerar att skicka ett återkommande e-postmeddelande till en lista över mottagare på dagen för deras födelsedag.

Vi har skapat följande arbetsflöde för målinriktning för att konfigurera det här användningsexemplet:

![](assets/birthday-workflow_usecase_1.png)

Det här arbetsflödet (daglig körning) markerar alla mottagare som har sin födelsedag det aktuella datumet.

![](assets/do-not-localize/how-to-video.png) Det här användningsexemplet finns också i form av en video. Mer information finns i [Skapa ett arbetsflöde](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/automating-with-workflows/creating-a-workflow.html) video.

Skapa en kampanj och klicka på **[!UICONTROL Targeting and workflows]** -fliken. Mer information finns i [Bygga huvudmålet i ett arbetsflöde](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow) -avsnitt.

Följ sedan dessa steg:

## Schemalägga sändning {#configuring-the-scheduler}

1. Lägg först till en **Schemaläggare** för att utlösa att leveransen skickas varje dag. I exemplet nedan skapas leveransen varje dag kl. 6.00.

   ![](assets/recur_delivery2.png)


## Identifiera mottagare vars födelsedag det är {#identifying-recipients-whose-birthday-it-is}

När du har konfigurerat **[!UICONTROL Scheduler]** så att arbetsflödet startar varje dag och identifierar alla mottagare vars födelsedatum är lika med det aktuella datumet.

Gör så här:

1. Dra och släpp en **[!UICONTROL Query]** -aktiviteten i arbetsflödet och dubbelklicka på den.
1. Klicka på **Redigera fråga** länk och markera **[!UICONTROL Filtering conditions]**.

   ![](assets/s_ncs_user_create_exp_exple00.png)

1. Klicka på den första cellen i **[!UICONTROL Expression]** kolumn och klicka **[!UICONTROL Edit expression]** för att öppna uttrycksredigeraren.

   ![](assets/s_ncs_user_create_exp_exple.png)

1. Klicka **[!UICONTROL Advanced selection]** för att välja filtreringsläge.

   ![](assets/s_ncs_user_create_exp_exple_a.png)

1. Välj **[!UICONTROL Edit the formula using an expression]** och klicka **[!UICONTROL Next]** för att visa uttrycksredigeraren.
1. Dubbelklicka i listan med funktioner **[!UICONTROL Day]**, som du når via **[!UICONTROL Date]** nod. Den här funktionen returnerar talet som representerar dagen som motsvarar datumet som skickades som en parameter.

   ![](assets/s_ncs_user_create_exp_exple01.png)

1. Dubbelklicka i listan med tillgängliga fält **[!UICONTROL Birth date]**. I den övre delen av redigeraren visas sedan följande formel:

   ```
   Day(@birthDate)
   ```

   Klicka **[!UICONTROL Finish]** för att bekräfta.

1. I frågeredigeraren, i den första cellen i **[!UICONTROL Operator]** kolumn, markera **[!UICONTROL equal to]**.

   ![](assets/s_ncs_user_create_exp_exple02.png)

1. Klicka sedan på den första cellen i den andra kolumnen (**[!UICONTROL Value]**) och klicka på **[!UICONTROL Edit expression]** för att öppna uttrycksredigeraren.
1. Dubbelklicka i listan med funktioner **[!UICONTROL Day]**, som du når via **[!UICONTROL Date]** nod.
1. Dubbelklicka på **[!UICONTROL GetDate]** funktion för att hämta aktuellt datum.

   ![](assets/s_ncs_user_create_exp_exple04.png)

   I den övre delen av redigeraren visas följande formel:

   ```
   Day(GetDate())
   ```

   Klicka **[!UICONTROL Finish]** för att bekräfta.

1. Upprepa den här proceduren för att hämta födelsemånaden som motsvarar den aktuella månaden. Om du vill göra det klickar du på **[!UICONTROL Add]** och upprepa steg 3 till 10, ersätta **[!UICONTROL Day]** med **[!UICONTROL Month]**.

   Den fullständiga frågan är följande:

   ![](assets/s_ncs_user_create_exp_exple03.png)

Länka resultatet av **[!UICONTROL Query]** aktivitet till **[!UICONTROL Email delivery]** aktivitet för att skicka ett e-postmeddelande till listan över alla dina mottagare på deras födelsedag.

## Inklusive mottagare födda den 29 februari (valfritt) {#including-recipients-born-on-february-29th--optional-}

Om du vill inkludera alla mottagare som föddes den 29 februari visar det här användningsexemplet hur du planerar att skicka ett återkommande e-postmeddelande till en lista med mottagare för deras födelsedag, oavsett om det är ett skottår eller inte.

De viktigaste implementeringsstegen för det här användningsexemplet är:

* Välja mottagare
* Välj om det är ett skottår eller inte
* Välja mottagare födda den 29 februari

Vi har skapat följande arbetsflöde för målinriktning för att konfigurera det här användningsexemplet:



Om aktuellt år **är inte ett skottår** och arbetsflödet körs den 1 mars måste alla mottagare som skulle ha haft sin födelsedag i går (29 februari) markeras och läggas till i mottagarlistan. I alla andra fall krävs ingen ytterligare åtgärd.

### Steg 1: Välja mottagare {#step-1--selecting-the-recipients}

När du har konfigurerat **[!UICONTROL Scheduler]** så att arbetsflödet startar varje dag, identifiera alla mottagare vars årsdag är den aktuella dagen.

>[!NOTE]
>
>Om det aktuella året är ett skottår inkluderas automatiskt alla mottagare som är födda den 29 februari.

![](assets/birthday-workflow_usecase_2.png)

Välja mottagare vars födelsedag motsvarar det aktuella datumet visas i dialogrutan [Identifiera mottagare vars födelsedag det är](#identifying-recipients-whose-birthday-it-is) -avsnitt.

### Steg 2: Välj om det är ett skottår eller inte {#step-2--select-whether-or-not-it-is-a-leap-year}

The **[!UICONTROL Test]** Med -aktiviteten kan du kontrollera om det är ett skottår och om det aktuella datumet är den 1 mars eller inte.

Om testet verifieras (året är inte ett skottår - det finns ingen 29 februari - och det aktuella datumet är den 1 mars) är **[!UICONTROL True]** övergången är aktiverad och de mottagare som är födda den 29 februari kommer att läggas till den 1 mars. I annat fall visas **[!UICONTROL False]** övergången är aktiverad och endast de mottagare som är födda det aktuella datumet kommer att få leveransen.

Kopiera och klistra in koden nedan i **[!UICONTROL Initialization script]** i **[!UICONTROL Advanced]** -fliken.

```
function isLeapYear(iYear)
{
    if(iYear/4 == Math.floor(iYear/4))
    {
        if(iYear/100 != Math.floor(iYear/100))
        {
            // Divisible by 4 only -> Leap Year
            return 1;
        }
        else
        {
            if(iYear/400 == Math.floor(iYear/400))
            {
                // Divisible by 4, 100 and 400 -> Leap year
                return 1;
            }
        }
    }
    // all others: no leap year
    return 0;
}

// Return today's date and time
var currentTime = new Date()
// returns the month (from 0 to 11)
var month = currentTime.getMonth() + 1
// returns the day of the month (from 1 to 31)
var day = currentTime.getDate()
// returns the year (four digits)
var year = currentTime.getFullYear()

// is current year a leap year?
vars.currentIsALeapYear = isLeapYear(year);

// is current date the first of march?
if(month == 3 && day == 1) {
  // today is 1st of march
vars.firstOfMarch = 1;
}
```

![](assets/birthday-workflow_usecase_3.png)

Lägg till följande villkor i **[!UICONTROL Conditional forks]** avsnitt:

```
vars.currentIsALeapYear == 0 && vars.firstOfMarch == 1
```

![](assets/birthday-workflow_usecase_4.png)

### Steg 3: Markera alla mottagare som är födda den 29 februari {#step-3--select-any-recipients-born-on-february-29th}

Skapa en **[!UICONTROL Fork]** aktivitet och länka en av de utgående övergångarna till en **[!UICONTROL Query]** aktivitet.

I den här frågan väljer du alla mottagare vars födelsedatum är den 29 februari.

![](assets/birthday-workflow_usecase_5.png)

Kombinera resultaten med en **[!UICONTROL Union]** aktivitet.

Länka resultaten av de två **[!UICONTROL Test]** aktivitetsgrenar till **[!UICONTROL Email delivery]** aktivitet för att skicka ett e-postmeddelande till listan över alla dina mottagare på deras födelsedag, även till dem som föddes den 29 februari under ett år utan hopp.

## Skapa en återkommande leverans {#creating-a-recurring-delivery-in-a-targeting-workflow}

Lägg till en **Återkommande leverans** aktiviteten baserat på den födelsedagsmall som du vill skicka.

>[!CAUTION]
>
>För att arbetsflödena ska kunna köras måste de tekniska arbetsflödena för Campaign-paketet startas. Mer information finns i [Förteckning över tekniska arbetsflöden](about-technical-workflows.md) -avsnitt.
>
>Om godkännandestegen är aktiverade för kampanjen skickas leveranserna först när dessa steg har bekräftats. Mer information finns i [Välja de processer som ska godkännas](../../campaign/using/marketing-campaign-approval.md#choosing-the-processes-to-be-approved) -avsnitt.

![](assets/birthday-workflow_usecase_1.png)
