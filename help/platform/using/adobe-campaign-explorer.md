---
product: campaign
title: Använda Adobe Campaign Explorer
description: Lär dig använda Campaign Explorer
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: f91d69a4-b794-40f0-b450-de862d7333e2
source-git-commit: fdb840a9e6349f074378899e07f794b62fb5b054
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 3%

---

# Använda Adobe Campaign Explorer {#using-adobe-campaign-explorer}

![](../../assets/v7-only.svg)

Utforskaren i Adobe Campaign är tillgänglig via verktygsfältsikonen. Du får tillgång till Adobe Campaign alla funktioner, konfigurationsskärmar och en mer detaljerad översikt över några av plattformselementen.

The **[!UICONTROL Explorer]** arbetsytan är uppdelad i tre zoner:

![](assets/s_ncs_user_navigation.png)

**1 - träd**: kan du anpassa innehållet i trädet (lägga till, flytta eller ta bort noder). Den här proceduren är endast avsedd för expertanvändare. Mer information om detta finns i [det här avsnittet](#about-navigation-hierarchy).).

**2 - Lista**: kan du filtrera den här listan, köra sökningar, lägga till information eller sortera data. [Läs mer](adobe-campaign-ui-lists.md).

**3 - Detaljer**: Du kan visa information om det markerade elementet. Med ikonen i det övre högra avsnittet kan du visa den här informationen i helskärmsläge.

## Mappar och navigeringsträd{#about-navigation-hierarchy}

Navigeringsträdet fungerar som en filläsare (t.ex. Utforskaren i Windows). Mappar kan innehålla undermappar. Om du väljer en nod visas vyn som motsvarar noden.

Den vy som visas är en lista som är associerad med ett schema och ett inmatningsformulär för att redigera den markerade raden.

![](assets/d_ncs_integration_navigation.png)

Om du vill lägga till en ny mapp i trädet högerklickar du på den mapp i grenen där du vill infoga en mapp och väljer **[!UICONTROL Add new folder]** . På snabbmenyn väljer du vilken typ av fil som ska skapas.

![](assets/d_ncs_integration_navigation_create.png)

Lär dig hur du konfigurerar Campaign-navigeringsträdet [i det här avsnittet](../../configuration/using/configuration.md).

Lär dig hur du anger behörigheter för mappar [i det här avsnittet](access-management-folders.md).

## Bästa praxis för mappkonfiguration

* **Använd inbyggda mappar**

   Genom att använda de inbyggda mapparna blir det enklare för personer som inte deltar i projektet att använda, underhålla och felsöka programmet. Du bör inte skapa anpassade mappstrukturer för mottagare, listor, leveranser osv., utan använda standardmapparna som Administration, Profiler och mål, Kampanjhantering.

* **Skapa undermappar**

   Placera tekniska arbetsflöden i standardmappen: Administration/produktion/tekniska arbetsflöden och skapa underkataloger per arbetsflödestyp.

* **Ange en namnkonvention**

   Du kan till exempel namnge arbetsflödena i alfabetisk ordning så att de visas sorterade i körningsordningen.

   Exempel:

   * A1 - importmottagare, börjar 10:00;
   * A2 - importbiljetter, börjar klockan 11:00.

* **Skapa mallar som användarna kan börja med**

   Skapa leveransmallar, arbetsflödesmallar och kampanjmallar som är specifika för användarna. Strukturen kan spara tid och säkerställa att rätt leveranskarta och -typologier används för varje användare.

## Skärmupplösning {#screen-resolution}

För optimal navigering och användbarhet rekommenderar Adobe att du använder en skärmupplösning på minst 1 600 × 900 pixlar.

>[!CAUTION]
>
>Upplösningar på mindre än 1 600 × 900 pixlar stöds inte av Adobe Campaign.

I **[!UICONTROL Explorer]** arbetsytan, om vissa delar av **[!UICONTROL Details]** -zonen verkar vara trunkerad, expandera den med pilen ovanför zonen eller klicka på **[!UICONTROL Enlarge]** -knappen.

![](assets/s_ncs_user_resolution.png)

## Bläddra bland och anpassa listor {#browsing-lists}

Lär dig hur du bläddrar i, hanterar och anpassar listor [i det här avsnittet](adobe-campaign-ui-lists.md).
