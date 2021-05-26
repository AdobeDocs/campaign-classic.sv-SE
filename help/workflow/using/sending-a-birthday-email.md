---
solution: Campaign Classic
product: campaign
title: Skicka ett födelsedagsmeddelande
description: Lär dig hur du skickar ett födelsedagsmeddelande med ett arbetsflöde
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 38006cca-e945-4b9d-8e2d-ed537b8541d9
source-git-commit: bce114f36d1ec4582fc79e750d48155ba0d7cd1f
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 1%

---

# Skicka ett födelsedagsmeddelande{#sending-a-birthday-email}

## Introduktion {#introduction}

I det här användningsexemplet visas hur du planerar att skicka ett återkommande e-postmeddelande till en lista över mottagare på dagen för deras födelsedag.

Vi har skapat följande arbetsflöde för målinriktning för att konfigurera det här användningsexemplet:

![](assets/birthday-workflow_usecase_1.png)

Det här arbetsflödet (daglig körning) markerar alla mottagare som har sin födelsedag det aktuella datumet.

![](assets/do-not-localize/how-to-video.png) Det här användningsexemplet finns också i form av en video. Mer information finns i videon [Skapa ett arbetsflöde](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/automating-with-workflows/creating-a-workflow.html).

Det gör du genom att skapa en kampanj och klicka på fliken **[!UICONTROL Targeting and workflows]**. Mer information finns i avsnittet [Bygga huvudmålet i ett arbetsflöde](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

Följ sedan dessa steg:

## Schemalägger sändning {#configuring-the-scheduler}

1. Lägg först till en **schemaläggare** som utlöser sändning varje dag. I exemplet nedan skapas leveransen varje dag kl. 6.00.

   ![](assets/recur_delivery2.png)


## Identifiera mottagare vars födelsedag är {#identifying-recipients-whose-birthday-it-is}

När du har konfigurerat aktiviteten **[!UICONTROL Scheduler]** så att arbetsflödet startar varje dag, identifierar du alla mottagare vars födelsedatum är lika med det aktuella datumet.

Gör så här:

1. Dra och släpp en **[!UICONTROL Query]**-aktivitet i arbetsflödet och dubbelklicka på den.
1. Klicka på länken **Redigera fråga** och välj **[!UICONTROL Filtering conditions]**.

   ![](assets/s_ncs_user_create_exp_exple00.png)

1. Klicka på den första cellen i kolumnen **[!UICONTROL Expression]** och klicka på **[!UICONTROL Edit expression]** för att öppna uttrycksredigeraren.

   ![](assets/s_ncs_user_create_exp_exple.png)

1. Klicka på **[!UICONTROL Advanced selection]** för att välja filtreringsläge.

   ![](assets/s_ncs_user_create_exp_exple_a.png)

1. Välj **[!UICONTROL Edit the formula using an expression]** och klicka på **[!UICONTROL Next]** för att visa uttrycksredigeraren.
1. Dubbelklicka på **[!UICONTROL Day]** i listan över funktioner, som du kommer åt via noden **[!UICONTROL Date]**. Den här funktionen returnerar talet som representerar dagen som motsvarar datumet som skickades som en parameter.

   ![](assets/s_ncs_user_create_exp_exple01.png)

1. Dubbelklicka på **[!UICONTROL Birth date]** i listan över tillgängliga fält. I den övre delen av redigeraren visas sedan följande formel:

   ```
   Day(@birthDate)
   ```

   Bekräfta genom att klicka på **[!UICONTROL Finish]**.

1. Välj **[!UICONTROL equal to]** i den första cellen i kolumnen **[!UICONTROL Operator]** i frågeredigeraren.

   ![](assets/s_ncs_user_create_exp_exple02.png)

1. Klicka sedan på den första cellen i den andra kolumnen (**[!UICONTROL Value]**) och klicka på **[!UICONTROL Edit expression]** för att öppna uttrycksredigeraren.
1. Dubbelklicka på **[!UICONTROL Day]** i listan över funktioner, som du kommer åt via noden **[!UICONTROL Date]**.
1. Dubbelklicka på funktionen **[!UICONTROL GetDate]** för att hämta aktuellt datum.

   ![](assets/s_ncs_user_create_exp_exple04.png)

   I den övre delen av redigeraren visas följande formel:

   ```
   Day(GetDate())
   ```

   Bekräfta genom att klicka på **[!UICONTROL Finish]**.

1. Upprepa den här proceduren för att hämta födelsemånaden som motsvarar den aktuella månaden. Om du vill göra det klickar du på knappen **[!UICONTROL Add]** och upprepar steg 3 till 10, och ersätter **[!UICONTROL Day]** med **[!UICONTROL Month]**.

   Den fullständiga frågan är följande:

   ![](assets/s_ncs_user_create_exp_exple03.png)

Länka resultatet av **[!UICONTROL Query]**-aktiviteten till en **[!UICONTROL Email delivery]**-aktivitet för att skicka ett e-postmeddelande till listan över alla dina mottagare på deras födelsedag.

## Inklusive mottagare födda den 29 februari (valfritt) {#including-recipients-born-on-february-29th--optional-}

Om du vill inkludera alla mottagare som föddes den 29 februari visar det här användningsexemplet hur du planerar att skicka ett återkommande e-postmeddelande till en lista med mottagare för deras födelsedag, oavsett om det är ett skottår eller inte.

De viktigaste implementeringsstegen för det här användningsexemplet är:

* Välja mottagare
* Välj om det är ett skottår eller inte
* Välja mottagare födda den 29 februari

Vi har skapat följande arbetsflöde för målinriktning för att konfigurera det här användningsexemplet:



Om det aktuella året **inte är ett skottår** och arbetsflödet körs den 1 mars, måste vi markera alla mottagare som skulle ha haft sin födelsedag i går (29 februari) och lägga till dem i mottagarlistan. I alla andra fall krävs ingen ytterligare åtgärd.

### Steg 1: Välja mottagare {#step-1--selecting-the-recipients}

När du har konfigurerat aktiviteten **[!UICONTROL Scheduler]** så att arbetsflödet startar varje dag, identifierar du alla mottagare vars årsdag är den aktuella dagen.

>[!NOTE]
>
>Om det aktuella året är ett skottår inkluderas automatiskt alla mottagare som är födda den 29 februari.

![](assets/birthday-workflow_usecase_2.png)

Väljer mottagare vars födelsedag motsvarar det aktuella datumet visas i avsnittet [Identifiera mottagare vars födelsedag är](#identifying-recipients-whose-birthday-it-is).

### Steg 2: Välj om det är ett skottår {#step-2--select-whether-or-not-it-is-a-leap-year} eller inte

Med aktiviteten **[!UICONTROL Test]** kan du kontrollera om det är ett skottår och om det aktuella datumet är den 1 mars eller inte.

Om testet verifieras (året är inte ett skottår - det finns ingen 29 februari - och det aktuella datumet är den 1 mars) aktiveras övergången **[!UICONTROL True]** och de mottagare som är födda den 29 februari läggs till den första leveransen från mars. Annars är övergången **[!UICONTROL False]** aktiverad och endast de mottagare som är födda på det aktuella datumet får leveransen.

Kopiera och klistra in koden nedan i avsnittet **[!UICONTROL Initialization script]** på fliken **[!UICONTROL Advanced]**.

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

Lägg till följande villkor i avsnittet **[!UICONTROL Conditional forks]**:

```
vars.currentIsALeapYear == 0 && vars.firstOfMarch == 1
```

![](assets/birthday-workflow_usecase_4.png)

### Steg 3: Markera alla mottagare som är födda den 29 februari {#step-3--select-any-recipients-born-on-february-29th}

Skapa en **[!UICONTROL Fork]**-aktivitet och länka en av de utgående övergångarna till en **[!UICONTROL Query]**-aktivitet.

I den här frågan väljer du alla mottagare vars födelsedatum är den 29 februari.

![](assets/birthday-workflow_usecase_5.png)

Kombinera resultaten med en **[!UICONTROL Union]**-aktivitet.

Länka resultaten från de två **[!UICONTROL Test]** aktivitetsgrenarna till en **[!UICONTROL Email delivery]**-aktivitet för att skicka ett e-postmeddelande till listan över alla dina mottagare på deras födelsedag, även till dem som föddes den 29 februari under ett år utan hopp.

## Skapar en återkommande leverans {#creating-a-recurring-delivery-in-a-targeting-workflow}

Lägg till en **Återkommande leverans**-aktivitet baserat på e-postmallen för födelsedagar som du vill skicka.

>[!CAUTION]
>
>För att arbetsflödena ska kunna köras måste de tekniska arbetsflödena för Campaign-paketet startas. Mer information finns i avsnittet [Lista över tekniska arbetsflöden](../../workflow/using/about-technical-workflows.md).
>
>Om godkännandestegen är aktiverade för kampanjen skickas leveranserna först när dessa steg har bekräftats. Mer information finns i avsnittet [Välja de processer som ska godkännas](../../campaign/using/marketing-campaign-approval.md#choosing-the-processes-to-be-approved).

![](assets/birthday-workflow_usecase_1.png)
