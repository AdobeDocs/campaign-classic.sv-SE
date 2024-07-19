---
product: campaign
title: Åtkomst till marknadsföringskampanjer
description: Åtkomst till marknadsföringskampanjer
role: User
feature: Campaigns, Cross Channel Orchestration
exl-id: 1278bda1-f83c-4d38-8042-e6611755cf36
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 1%

---

# Åtkomst till marknadsföringskampanjer{#accessing-marketing-campaigns}

Med Adobe Campaign kan ni skapa, konfigurera, genomföra och analysera marknadsföringskampanjer. Alla marknadsföringskampanjer kan hanteras från ett enhetligt kontrollcenter.

## Grundläggande om Workspace {#workspace-basics}

### Startsida {#home-page}

När du är ansluten till Adobe Campaign kan du bläddra bland de olika funktionerna med hjälp av länkar i navigeringsfältet.


![](assets/campaign_global_view.png)


Kampanjelement finns på fliken **[!UICONTROL Campaigns]**: här kan du se en översikt över marknadsföringsprogram, kampanjer och deras undergrupper. Ett marknadsföringsprogram består av kampanjer, som består av leveranser, uppgifter, länkade resurser osv. När det gäller hantering av marknadsföringskampanjer med Campaign finns det information om leveranser, budgetar, granskare och länkade dokument i kampanjerna.

Blocket **[!UICONTROL Browsing]** på fliken **[!UICONTROL Campaigns]** innehåller olika poster, beroende på vilka moduler som är installerade på instansen. Du kan till exempel få åtkomst till:

* **Kampanjkalender**: kalender med planer, marknadsföringsprogram, leveranser och kampanjer. Se [Kampanjkalender](#campaign-calendar).
* **Kampanjer**: åtkomst till kampanjer i alla marknadsföringsprogram.
* **Leveranser**: åtkomst till leveranser som är länkade till kampanjerna.
* **Webbprogram**: åtkomst till webbprogram (formulär, landningssidor osv.).

>[!NOTE]
>
>Mer information om Adobe Campaign allmänna inställningar för ergonomi, behörigheter och profilhanteringsfunktioner finns i [det här avsnittet](../../platform/using/adobe-campaign-workspace.md).
>
>Alla funktioner som rör kanaler och leveranser beskrivs i [det här avsnittet](../../delivery/using/steps-about-delivery-creation-steps.md).

### Kampanjkalender {#campaign-calendar}

Varje kampanj tillhör ett program som i sin tur tillhör en plan. Planer, program och kampanjer nås via menyn **[!UICONTROL Campaign calendar]** på fliken **Kampanjer**.

Om du vill redigera en plan, ett program, en kampanj eller en leverans klickar du på namnet i kalendern och sedan på **[!UICONTROL Open...]**. Den visas sedan på en ny flik, enligt nedan:

![](assets/d_ncs_user_interface_hierar.png)

Du kan filtrera informationen som visas i kampanjkalendern: klicka på länken **[!UICONTROL Filter]** och välj filtreringsvillkor.

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>När du filtrerar på ett datum visas alla kampanjer med ett startdatum som är senare än det angivna datumet och/eller med ett slutdatum som är tidigare än det angivna datumet. Välj datum med hjälp av kalendrarna till höger om varje fält.

Du kan också använda fältet **[!UICONTROL Search]** för att filtrera de visade objekten.

Med ikonerna som är länkade till varje objekt kan du visa objektets status: färdig, pågående, redigerad osv.

### Sök i ett marknadsföringsprogram {#browsing-in-a-marketing-program}

Med Campaign kan ni hantera en uppsättning program som består av olika marknadsföringskampanjer. Varje kampanj innehåller leveranser och tillhörande processer och resurser.

#### Bläddra i ett program {#browsing-a-program}

När du redigerar ett program använder du flikarna nedan för att bläddra och konfigurera det.

* På fliken **Schema** visas kalendern med program för en månad, vecka eller dag beroende på vilken flik du klickar på i kalenderrubriken.

  Om det behövs kan du skapa en kampanj, ett program eller en uppgift via den här sidan.

  ![](assets/s_ncs_user_interface_campaign02.png)

* På fliken **Redigera** kan du anpassa programmet: namn, start- och slutdatum, budget, länkade dokument osv.

  ![](assets/s_ncs_user_interface_campaign05.png)

#### Söka efter kampanjer {#browsing-campaigns}

Det går att komma åt kampanjer via kampanjkalendern, fliken **[!UICONTROL Schedule]** i programmet eller listan med kampanjer.

1. Välj den kampanj du vill visa via kampanjkalendern och klicka sedan på länken **[!UICONTROL Open]**.

   ![](assets/campaign_planning_edit_op.png)

   Kampanjen redigeras på en ny flik, vilket visas nedan:

   ![](assets/campaign_op_edit.png)

1. Via fliken **[!UICONTROL Schedule]** i programmet är redigeringsläget detsamma som via kampanjkalendern.
1. Klicka på namnet på den kampanj du vill redigera via länken **[!UICONTROL Campaigns]** på fliken **[!UICONTROL Campaigns]**.

   ![](assets/campaign_edit_from_list.png)

### Styra en kampanj {#controlling-a-campaign}

#### Kontrollpanel {#dashboard}

För varje kampanj finns jobb, resurser och leveranser samlade på en enda skärm - dashboard - där ni kan hantera marknadsföringsåtgärder i samarbete med andra.

Kontrollpanelen för en kampanj används som ett kontrollgränssnitt. Den får direkt åtkomst till de viktigaste faserna för att skapa och hantera kampanjer: leveranser, extraheringsfiler, meddelanden, budgetar osv.

![](assets/s_ncs_user_op_board_start_del.png)

Med Adobe Campaign kan ni skapa samarbetsprocesser för framtagning och godkännande av de olika stadierna av marknadsförings- och kommunikationskampanjer: godkännande av budget, mål, innehåll osv.

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>Konfigurationen av kampanjmallar visas i [Campaign-mallar](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

#### Schema {#schedule}

En kampanj centraliserar en uppsättning leveranser. För varje kampanj ger schemat en global vy över alla komponenter: du kan visa uppgifter och leveranser och enkelt komma åt dem.

![](assets/campaign_planning_tab.png)

#### Forum {#forum}

För varje kampanj kan operatörerna utbyta meddelanden via ett särskilt forum.

Läs mer i [Diskussionsforum](../../mrm/using/discussion-forums.md).

#### Rapporter {#reports}

Länken **[!UICONTROL Reports]** ger dig åtkomst till kampanjrapporterna.

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>Rapporterna beskrivs i [det här avsnittet](../../reporting/using/about-adobe-campaign-reporting-tools.md).

#### Konfiguration {#configuration}

Kampanjer skapas via kampanjmallar. Du kan konfigurera återanvändbara mallar för vilka vissa alternativ har valts och andra inställningar redan har sparats. För varje kampanj finns följande funktioner:

* Referens för [dokument och resurser](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents): du kan associera dokument med kampanjen (kort, rapport, bilder osv.). Alla dokumentformat stöds.
* Definiera kostnader: för varje kampanj kan du i Adobe Campaign definiera [kostnadsposter och kostnadsberäkningsstrukturer](../../campaign/using/providers-stocks-and-budgets.md#defining-cost-categories) som kan användas när marknadsföringskampanjen skapas. Exempel: tryckkostnader, användning av en extern byrå, rumshyrning.
* Definiera mål: du kan definiera kvantifierbara mål för en kampanj, t.ex. antal prenumeranter, affärsvolym osv. Den här informationen används senare i kampanjrapporter.
* Hantera [dirigerade adresser](../../delivery/using/about-seed-addresses.md) och [kontrollgrupper](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).
* Hantera godkännanden: du kan välja de behandlingar som ska godkännas och, om det behövs, välja granskningsoperatorer eller grupper av operatorer. [Läs mer](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)

>[!NOTE]
>
>Klicka på länken **[!UICONTROL Advanced campaign parameters...]** på fliken **[!UICONTROL Edit]** om du vill komma åt kampanjkonfigurationerna och göra ändringar i dem.

## Använda webbgränssnittet {#using-the-web-interface-}

Du kan öppna Adobe Campaign konsolskärmar via en webbläsare och visa alla kampanjer och leveranser samt rapporter och information om profilerna i din databas. Det går inte att skapa poster med den här åtkomsten. Beroende på användarrättigheterna kan du visa och/eller agera på data i databasen. Du kan till exempel godkänna kampanjinnehåll och målinriktning, starta om eller stoppa en leverans osv.

1. Logga in som vanligt via https://`<your instance>:<port>/view/home`.
1. Använd menyerna för att komma åt översikterna.

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

Förutom att navigera mellan kampanjer och visa dem kan du utföra följande typer av uppgifter:

* Övervaka aktivitet i en instans
* Delta i valideringsprocesser, till exempel godkänna eller avvisa ett leveransinnehåll
* Utför andra snabbåtgärder, till exempel pausa ett arbetsflöde
* Få tillgång till alla rapportfunktioner
* Delta i forumdiskussioner

I tabellen sammanfattas de åtgärder du kan vidta i kampanjer från en webbläsare:

| Sida  | Åtgärd |
| --- | --- |
| Lista över kampanjer, leveranser, erbjudanden osv. | Ta bort ett listobjekt |
| Campaign | Avbryta en kampanj |
| Leverans | Godkänn leveransinnehållet och målet<br/>Skicka leveransinnehållet<br/>Bekräfta en leverans<br/>Pausa och stoppa en leverans |
| Webbprogram | Skapa ett webbprogram<br/>Redigera programinnehåll och -egenskaper<br/>Spara programinnehållet som en mall<br/>Publish programmet |
| Erbjudande | Godkänn erbjudandets innehåll och behörighet<br/>Inaktivera ett onlineerbjudande |
| Uppgift | Avsluta en aktivitet<br/>Avbryt en aktivitet |
| Marknadsföringsresurser | Godkänn en resurs<br/>Lås och lås upp en resurs |
| Kampanjpaket | Skicka ett paket för godkännande<br/>Godkänn eller avvisa ett paket<br/>Avbryt ett paket |
| Kampanjorder | Skapa en order<br/>Acceptera eller avvisa en order <!-- Je n'ai pas pu créer de campaign order pour vérifier cela. Peut-on accéder à ces fonctionnalités depuis l'accès web ? --> |
| Stock | Ta bort en aktierad |
| Simulering av erbjudanden | Starta och stoppa en simulering |
| Målarbetsflöde | Starta, pausa och stoppa ett arbetsflöde |
| Rapport | Spara aktuella data i rapporthistoriken |
| Forum | Lägg till en diskussion<br/>Svara på ett meddelande i en diskussion<br/>Följ en diskussion och avsluta prenumerationen på den |

### Godkännanden

Godkännanden (till exempel av ett mål eller ett leveransinnehåll) kan utföras via webbåtkomst.

![](assets/campaign_web_interface_validation.png)

Du kan också använda länken i meddelandena. Mer information finns i [Kontrollera och godkänna leveranser](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).
