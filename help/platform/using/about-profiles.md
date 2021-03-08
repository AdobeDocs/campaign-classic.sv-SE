---
solution: Campaign Classic
product: campaign
title: Om profiler
description: Om profiler
audience: platform
content-type: reference
topic-tags: profile-management
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 17%

---


# Om profiler{#about-profiles}

Profiler (kunder, prospekt och prenumeranter på nyhetsbrev osv.) är centraliserade i databasen i Adobe Campaign. Det finns många sätt att förvärva profiler och bygga upp databasen: insamling online via webbformulär, manuell eller automatisk import av textfiler, replikering med företagsdatabaser eller andra informationssystem. Med Adobe Campaign kan ni införliva marknadsföringshistorik, inköpsinformation, preferenser, CRM-data och alla relevanta PI-data i en samlad vy för att analysera och vidta åtgärder.

I Adobe Campaign är mottagarna de standardprofiler som väljs för att skicka leveranser till (e-post, SMS etc.). Tack vare mottagardata som lagras i databasen kan du filtrera det mål som ska ta emot en viss leverans och lägga till personaliseringsdata i leveransinnehållet. Det finns andra typer av profiler i databasen. De är utformade för olika användningsfall. Exempelvis görs fröprofiler för att testa dina leveranser innan de skickas till det slutliga målet.

![](assets/do-not-localize/how-to-video.png) [Förstå begreppet profiler i video](#create-profiles-video)

## Profiltyper {#profile-types}

Med Adobe Campaign kan du hantera profiler under hela livscykeln: skapa, importera, målinrikta, åtgärdsspårning, uppdateringar osv.

Varje profil matchar en databaspost. De innehåller all information som krävs för att målinrikta, kvalificera och spåra individer.

Profiler kan identifieras baserat på lagringsutrymme. Detta innebär att en profil kan matcha: en mottagare, en besökare, en operatör, en prenumerant, en potentiell kund osv.

## Mottagarprofiler {#recipient-profiles}

Leveransmottagarna lagras i databasen som profiler med den information som är länkad till dem: efternamn, förnamn, adress, prenumerationer, leveranser osv. När du skapar kampanjer kan du definiera målet för leveranserna till ett urval av profilerna i basen enligt enkla eller avancerade kriterier.

Du kan också skapa kampanjer som riktar sig till mottagare vars profiler inte lagras i databasen utan i filer. Dessa kallas för &quot;externa&quot; leveranser. Mer information om den här typen av leverans finns på [den här sidan](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

De viktigaste metoderna för att skapa mottagarprofiler är följande:

* direkt inmatning på skärmar i det grafiska gränssnittet,
* importera mottagarlistor,
* onlinesamling via webbformulär.

>[!NOTE]
>
>Mer information om hur filer och webbformulär importeras finns i [Allmän import och export](../../platform/using/get-started-data-import-export.md).

## Profiler och mål {#profiles-and-targets}

Med länken **[!UICONTROL Profiles and targets]** kan du visa mottagare som lagras i Adobe Campaign-databasen. Du kan skapa en ny mottagare, redigera en befintlig mottagare och komma åt dess profil. Se denna [sida](../../platform/using/editing-a-profile.md) för mer information om detta.

![](assets/d_ncs_user_interface_target_link.png)

Du får även tillgång till

* förteckningar, se [Skapa och hantera listor](../../platform/using/creating-and-managing-lists.md),
* prenumerationstjänster, hänvisa till [den här sidan](../../delivery/using/managing-subscriptions.md),
* webbapplikationer, hänvisa till [den här sidan](../../web/using/about-web-applications.md),
* Import och export (sysselsättning). hänvisa till [Allmän import och export](../../platform/using/about-generic-imports-exports.md),
* riktade arbetsflöden, hänvisar till [den här sidan](../../workflow/using/building-a-workflow.md#implementation-steps-).

På mottagarsidan kan du utföra vanliga åtgärder på profiler: redigeringar, uppdateringar, tillägg, borttagningar, sortering.

För mer avancerade profiländringar måste du redigera Adobe Campaign-trädet. Det gör du genom att klicka på länken **[!UICONTROL Explorer]** på Adobe Campaign hemsida.

Som standard lagras mottagarna i noden **[!UICONTROL Profiles and Targets > Recipients]** i trädet. Du kan skapa mottagare från den här vyn, liksom:

* sortera och filtrera databasens profiler, se [Filtreringsalternativ](../../platform/using/filtering-options.md),
* flytta, kopiera eller ta bort profiler från databasen, se [Hantera profiler](../../platform/using/managing-profiles.md),
* uppdateringsprofiler; se [Uppdatera data](../../platform/using/updating-data.md),
* Exportmottagare. se [Exportera och importera profiler](../../platform/using/exporting-and-importing-profiles.md),
* skapa mottagargrupper, se [Skapa och hantera listor](../../platform/using/creating-and-managing-lists.md).

Om du vill komma åt avancerade funktioner och konfigurationer måste du klicka på ikonen **[!UICONTROL Explorer]**.

![](assets/d_ncs_user_interface01.png)

Den allmänna layouten för Adobe Campaign Explorer visas i [Använda Adobe Campaign Explorer](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer).

>[!NOTE]
>
>Du kan även visa en avancerad vy av den här listan från Adobe Campaign-trädet genom att klicka på länken **[!UICONTROL Profiles and targets > Recipients]**. Listvisningen kan konfigureras så att den passar dina behov. Du kan lägga till eller ta bort kolumner, definiera kolumnordning, sortera data osv. Listvisningskonfigurationen beskrivs i [Använda Adobe Campaign Utforskaren](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer).
>
>Du kan också definiera mottagarvyer. Mer information om den här funktionen finns i [Mappar och vyer](../../platform/using/access-management-folders.md).

## Aktiva profiler {#active-profiles}

Aktiva profiler är de profiler som räknas i faktureringssyfte.

>[!NOTE]
>
>Om du är värd på AWS och använder Campaign Classic från build 8931 kan du även övervaka antalet aktiva profiler som används på dina instanser direkt från Kontrollpanelen. Mer information finns i [dokumentationen till kontrollpanelen](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/active-profiles-monitoring.html).
>
>Observera att antalet aktiva profiler endast är tillgängligt för **Marknadsinstanser**. Den är inte tillgänglig för körningsinstanser, vilket innebär MID-instanser (mellanleverantörer) och RT-instanser (Message Center/Real-time Messaging).

&quot;**Profil**&quot; betyder en informationspost (t.ex.: en post i nmsRecipient-tabellen eller en extern tabell som innehåller ett cookie-ID, Kund-ID, mobilidentifierare eller annan information som är relevant för en viss kanal) som representerar en slutkund, potentiell kund eller lead.

Fakturering gäller endast profiler som är **aktiva**. En profil anses vara aktiv om profilen har delats eller kommunicerats med via någon kanal under de senaste 12 månaderna.

De profiler som uteslöts under färdigställandet (typologiregler, karantänregler) beaktas inte. En profil som har valts av flera leveranser räknas bara en gång.

>[!NOTE]
>
>Facebook- och Twitter-kanaler beaktas inte.

Du kan få en översikt över **[!UICONTROL Number of active profiles]** på Campaign Standard **[!UICONTROL Administration > Campaign Management > Customer metrics]**-menyn. Det faktiska antalet utförs av **[!UICONTROL Number of active billing profiles]** (**[!UICONTROL billingActiveContactCount]**) [det tekniska arbetsflödet](../../workflow/using/about-technical-workflows.md), som körs varje dag och lägger till nya data i den befintliga rapporten för den aktuella perioden på **[!UICONTROL Customer metrics]**-menyn. Varje period varar i 12 månader.

## Självstudievideo {#create-profiles-video}

Lär dig hur du får åtkomst till profildata, sorterar och filtrerar profiler och skapar och hanterar profiler manuellt.

I den här videon förklaras också Adobe Campaign Classic överensstämmelse med de allmänna dataskyddsreglerna.

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

Ytterligare Campaign Classic-instruktionsvideor finns [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).

**Se även**

* [Integritetshantering i Campaign](https://helpx.adobe.com/se/campaign/kb/acc-privacy.html)

* [Definiera målpopulationen](../../delivery/using/define-the-right-audience.md)

* [Skapa frågor och segmentdata i arbetsflöden](../../workflow/using/targeting-data.md)

* [Välj målmappning](../../delivery/using/selecting-a-target-mapping.md)

* [Definiera målgruppen - bästa praxis](../../delivery/using/define-the-right-audience.md)
