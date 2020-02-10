---
title: Om profiler
seo-title: Om profiler
description: Om profiler
seo-description: null
page-status-flag: never-activated
uuid: 9a3fcb58-a356-4eee-bc26-c64825de5f99
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 5addada8-0185-488f-9825-83f60981c139
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0ce6e5277c32bc18c20dca62e5b276f654d1ace5

---


# Om profiler{#about-profiles}

## Profiltyper {#profile-types}

Med Adobe Campaign kan ni hantera profiler under hela deras livscykel: skapa, importera, målinrikta, åtgärdsspårning, uppdateringar osv.

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
>Mer information om hur filer och webbformulär importeras finns i [Allmän import och export](../../platform/using/generic-imports-and-exports.md).

## Profiler och mål {#profiles-and-targets}

Med hjälp av **[!UICONTROL Profiles and targets]** länken kan du visa mottagare som lagras i Adobe Campaign-databasen. Du kan skapa en ny mottagare, redigera en befintlig mottagare och komma åt dess profil. Mer information finns på [den här sidan](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

Du får även tillgång till

* förteckningar, se [Skapa och hantera listor](../../platform/using/creating-and-managing-lists.md),
* prenumerationstjänster, hänvisa till [denna sida](../../delivery/using/managing-subscriptions.md),
* webbapplikationer, hänvisa till [denna sida](../../web/using/about-web-applications.md),
* Import och export (sysselsättning). hänvisa till [allmän import och export](../../platform/using/generic-imports-and-exports.md),
* riktade arbetsflöden, se [den här sidan](../../workflow/using/building-a-workflow.md#implementation-steps-).

På mottagarsidan kan du utföra vanliga åtgärder på profiler: redigeringar, uppdateringar, tillägg, borttagningar, sortering.

För mer avancerade profiländringar måste du redigera Adobe Campaign-trädet. Det gör du genom att klicka på **[!UICONTROL Explorer]** länken på startsidan för Adobe Campaign.

Som standard lagras mottagarna i trädnoden **[!UICONTROL Profiles and Targets > Recipients]** . Du kan skapa mottagare från den här vyn, liksom:

* sortera och filtrera databasens profiler, se [Filtreringsalternativ](../../platform/using/filtering-options.md),
* flytta, kopiera eller ta bort profiler från databasen, se [Hantera profiler](../../platform/using/managing-profiles.md),
* uppdateringsprofiler; se [Uppdatera data](../../platform/using/updating-data.md),
* Exportmottagare. se [Exportera och importera profiler](../../platform/using/exporting-and-importing-profiles.md),
* skapa mottagargrupper, se [Skapa och hantera listor](../../platform/using/creating-and-managing-lists.md).

Om du vill komma åt avancerade funktioner och konfigurationer måste du klicka på **[!UICONTROL Explorer]** ikonen .

![](assets/d_ncs_user_interface01.png)

Den allmänna layouten för Adobe Campaign Explorer presenteras i [Använda Adobe Campaign Explorer](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer).

>[!NOTE]
>
>Du kan även visa en avancerad vy av den här listan från Adobe Campaign-trädet genom att klicka på **[!UICONTROL Profiles and targets > Recipients]** länken. Listvisningen kan konfigureras så att den passar dina behov. Du kan lägga till eller ta bort kolumner, definiera kolumnordning, sortera data osv. Listvisningskonfigurationen beskrivs i [Använda Adobe Campaign Explorer](../../platform/using/adobe-campaign-workspace.md#using-adobe-campaign-explorer).
>
>Du kan också definiera mottagarvyer. Mer information om den här funktionen finns i [Mappar och vyer](../../platform/using/access-management.md#folders-and-views).

## Aktiva profiler {#active-profiles}

Aktiva profiler är de profiler som räknas i faktureringssyfte.

&quot;**profil**&quot; innebär ett register över information (t.ex.: en post i nmsRecipient-tabellen eller en extern tabell som innehåller ett cookie-ID, Kund-ID, mobilidentifierare eller annan information som är relevant för en viss kanal) som representerar en slutkund, potentiell kund eller lead.

Fakturering gäller endast profiler som är **aktiva**. En profil anses vara aktiv om profilen har delats eller kommunicerats med via någon kanal under de senaste 12 månaderna.

>[!NOTE]
>
>Facebook- och Twitter-kanaler beaktas inte.

Du kan visa en översikt över **[!UICONTROL Number of active profiles]** menyerna på **[!UICONTROL Administration > Campaign Management > Customer metrics]** menyn.

Det faktiska antalet utförs av det **[!UICONTROL Number of active billing profiles]** (**[!UICONTROL billingActiveContactCount]**) [tekniska arbetsflödet](../../workflow/using/delivery.md), som körs varje dag och lägger till nya data i den befintliga rapporten för den aktuella perioden på **[!UICONTROL Customer metrics]** menyn. Varje period varar i 12 månader.

De profiler som uteslöts under färdigställandet (typologiregler, karantänregler) beaktas inte. En profil som har valts av flera leveranser räknas bara en gång.
