---
product: campaign
title: Kom igång med profiler
description: Arbeta med profiler i Adobe Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Profiles, Audiences
role: User, Data Architect
level: Beginner
exl-id: 54f1ad6c-54b0-4448-8c38-806dd75c1dae
source-git-commit: c4fa3ea6d5a9d9acae267fc1ca27cf3bc140683c
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 15%

---

# Kom igång med profiler{#about-profiles}



Profilerna är centraliserade i Adobe Campaign-databasen. Det finns många sätt att förvärva profiler och bygga upp databasen: insamling online via webbformulär, manuell eller automatisk import av textfiler, replikering med företagsdatabaser eller andra informationssystem. Med Adobe Campaign kan ni införliva marknadsföringshistorik, inköpsinformation, preferenser, CRM-data och alla relevanta PI-data i en samlad vy för att analysera och vidta åtgärder.

&quot;**Profil**&quot; innebär en informationspost (t.ex. en post i nmsRecipient-tabellen eller en extern tabell som innehåller ett cookie-ID, Kund-ID, mobilidentifierare eller annan information som är relevant för en viss kanal) som representerar en slutkund, potentiell kund eller lead.

I Adobe Campaign är mottagarna de standardprofiler som väljs för att skicka leveranser till (e-post, SMS etc.). Med mottagardata som lagras i databasen kan du filtrera målet som ska ta emot en viss leverans och lägga till personaliseringsdata i leveransinnehållet. Det finns andra typer av profiler i databasen. De är utformade för olika användningsfall. Exempelvis görs fröprofiler för att testa dina leveranser innan de skickas till det slutliga målet.

![](assets/do-not-localize/how-to-video.png) [Förstå begreppet profiler i video](#create-profiles-video)

## Profiltyper {#profile-types}

Med Adobe Campaign kan du hantera profiler under hela deras livscykel: skapande, import, målgruppsanpassning, åtgärdsspårning, uppdateringar osv.

Varje profil matchar en databaspost. De innehåller all information som krävs för att målinrikta, kvalificera och spåra individer.

Profiler kan identifieras baserat på lagringsutrymme. Det innebär att en profil kan matcha: en mottagare, en besökare, en operatör, en prenumerant, en potentiell kund, osv.

## Mottagarprofiler {#recipient-profiles}

Leveransmottagare lagras i databasen som profiler med information som är länkad till dem: efternamn, förnamn, adress, prenumerationer, leveranser osv. När du skapar kampanjer kan du definiera målet för leveranserna till ett urval av profilerna i basen enligt enkla eller avancerade kriterier.

Du kan också skapa kampanjer som riktar sig till mottagare vars profiler inte lagras i databasen utan i filer. Dessa kallas för &quot;externa&quot; leveranser. Mer information om den här typen av leverans finns i [den här sidan](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

De viktigaste metoderna för att skapa mottagarprofiler är följande:

* direkt inmatning på skärmar i det grafiska gränssnittet,
* importera mottagarlistor,
* onlinesamling via webbformulär.

>[!NOTE]
>
>Om du vill ta reda på hur filer och webbformulär importeras går du till [Allmän import och export](../../platform/using/get-started-data-import-export.md).

## Profiler och mål {#profiles-and-targets}

The **[!UICONTROL Profiles and targets]** -länken kan du visa mottagare som lagras i Adobe Campaign-databasen. Du kan skapa en ny mottagare, redigera en befintlig mottagare och komma åt dess profil. Mer information finns på [den här sidan](../../platform/using/editing-a-profile.md).

![](assets/d_ncs_user_interface_target_link.png)

Du får även tillgång till

* listor - [Läs mer](../../platform/using/creating-and-managing-lists.md)
* prenumerationstjänster - [Läs mer](../../delivery/using/managing-subscriptions.md)
* webbprogram - [Läs mer](../../web/using/about-web-applications.md)
* import och export (jobb) - [Läs mer](../../platform/using/about-generic-imports-exports.md)
* riktade arbetsflöden - [Läs mer](../../workflow/using/building-a-workflow.md#implementation-steps-)

På mottagarsidan kan du utföra vanliga åtgärder för profiler: redigeringar, uppdateringar, tillägg, borttagningar, sorteringar.

För mer avancerade profiländringar måste du redigera Adobe Campaign-trädet. Klicka på **[!UICONTROL Explorer]** på Adobe Campaign hemsida.

Som standard lagras mottagarna i **[!UICONTROL Profiles and Targets > Recipients]** trädnod. Du kan skapa mottagare från den här vyn, liksom:

* sortera och filtrera databasens profiler - [Läs mer](../../platform/using/filtering-options.md)
* flytta, kopiera eller ta bort profiler från databasen - [Läs mer](../../platform/using/managing-profiles.md),
* uppdateringsprofiler - [Läs mer](../../platform/using/updating-data.md)
* exportmottagare - [Läs mer](../../platform/using/exporting-and-importing-profiles.md)
* skapa mottagargrupper - [Läs mer](../../platform/using/creating-and-managing-lists.md)

Om du vill komma åt avancerade funktioner och konfigurationer måste du klicka på **[!UICONTROL Explorer]** -ikon.

![](assets/d_ncs_user_interface01.png)

Den allmänna layouten för Adobe Campaign Explorer presenteras i [den här sidan](../../platform/using/adobe-campaign-explorer.md).

>[!NOTE]
>
>Du kan även visa en avancerad vy av listan från Adobe Campaign-trädet genom att klicka på **[!UICONTROL Profiles and targets > Recipients]** länk. Listvisningen kan konfigureras efter dina behov. Du kan lägga till eller ta bort kolumner, definiera kolumnordning, sortera data osv. Konfigurationen för listvisning beskrivs i [den här sidan](../../platform/using/adobe-campaign-ui-lists.md).
>
>Du kan också definiera mottagarvyer. Mer information om den här funktionen finns i [det här avsnittet](../../platform/using/access-management-folders.md).

## Aktiva profiler {#active-profiles}

En aktiv profil är en profil som kunden har försökt kommunicera med under de senaste 12 månaderna via valfri kanal.

Enligt avtalet har var och en av instanserna i Campaign ett visst antal aktiva profiler som räknas för faktureringsändamål. Se ditt senaste kontrakt för referens om antalet köpta aktiva profiler. Läs mer i [Adobe Campaign produktbeskrivning](https://helpx.adobe.com/se/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

Du kan övervaka antalet aktiva profiler på instansen direkt från Campaign-kontrollpanelen. Mer information finns i [Dokumentation för kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/active-profiles-monitoring.html){target="_blank"}.

Följande skyddsräcken och begränsningar gäller:

* En profil som har valts av flera leveranser räknas bara en gång.
* Profiler som är inriktade på social marknadsföring på X (Twitter) eller Facebook räknas inte som aktiva profiler.
* Antalet aktiva profiler är tillgängligt för **Marknadsföringsinstanser** endast. Den är inte tillgänglig för körningsinstanser, vilket innebär MID-instanser (mellanleverantörer) och RT-instanser (Message Center/Real-time Messaging).
* Antalet baseras på mottagarens primärnyckel. Om det finns en profil i två olika mottagartabeller kan den därför räknas två gånger som en aktiv profil.


## Självstudievideo {#create-profiles-video}

Lär dig hur du får åtkomst till profildata, sorterar och filtrerar profiler och skapar och hanterar profiler manuellt.

I den här videon förklaras också Adobe Campaign Classic överensstämmelse med de allmänna dataskyddsreglerna.

>[!VIDEO](https://video.tv.adobe.com/v/35611?quality=12)

Det finns fler videor med Campaign Classic om hur man gör [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).

**Se även**

* [Integritetshantering i Campaign](https://helpx.adobe.com/se/campaign/kb/acc-privacy.html)

* [Definiera målpopulationen](../../delivery/using/define-the-right-audience.md)

* [Skapa frågor och segmentdata i arbetsflöden](../../workflow/using/targeting-data.md)

* [Välj målmappning](../../delivery/using/selecting-a-target-mapping.md)

* [Definiera målgruppen - bästa praxis](../../delivery/using/define-the-right-audience.md)
