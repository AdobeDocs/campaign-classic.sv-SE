---
product: campaign
title: Åtkomst till marknadsföringskampanjer
description: Åtkomst till marknadsföringskampanjer
role: User
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Campaigns, Cross Channel Orchestration
exl-id: 1278bda1-f83c-4d38-8042-e6611755cf36
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 2%

---

# Åtkomst till marknadsföringskampanjer{#accessing-marketing-campaigns}

Med Adobe Campaign kan ni skapa, konfigurera, genomföra och analysera marknadsföringskampanjer. Alla marknadsföringskampanjer kan hanteras från ett enhetligt kontrollcenter.

## Grundläggande om arbetsytan {#workspace-basics}

### Startsida {#home-page}

När du är ansluten till Adobe Campaign kan du bläddra bland de olika funktionerna med hjälp av länkar i navigeringsfältet.


![](assets/campaign_global_view.png)


Kampanjelementen finns i **[!UICONTROL Campaigns]** här kan du se en översikt över marknadsföringsprogram, kampanjer och deras undergrupper. Ett marknadsföringsprogram består av kampanjer, som består av leveranser, uppgifter, länkade resurser osv. När det gäller hantering av marknadsföringskampanjer med Campaign finns det information om leveranser, budgetar, granskare och länkade dokument i kampanjerna.

The **[!UICONTROL Browsing]** -block i **[!UICONTROL Campaigns]** På -fliken finns olika poster, beroende på vilka moduler som är installerade på instansen. Du kan till exempel få åtkomst till:

* **Kampanjkalender**: planeringskalender, marknadsföringsprogram, leveranser och kampanjer. Se [Kampanjkalender](#campaign-calendar).
* **Kampanjer**: tillgång till kampanjer i alla marknadsföringsprogram.
* **Leveranser**: åtkomst till leveranser som är kopplade till kampanjerna.
* **Webbprogram**: åtkomst till webbapplikationer (formulär, landningssidor osv.).

>[!NOTE]
>
>Mer information om Adobe Campaign allmänna funktioner för ergonomi, behörigheter och profilhantering finns i [det här avsnittet](../../platform/using/adobe-campaign-workspace.md).
>
>Alla funktioner som rör kanaler och leveranser beskrivs i [det här avsnittet](../../delivery/using/steps-about-delivery-creation-steps.md).

### Kampanjkalender {#campaign-calendar}

Varje kampanj tillhör ett program som i sin tur tillhör en plan. Planer, program och kampanjer nås via **[!UICONTROL Campaign calendar]** i **Kampanjer** -fliken.

Om du vill redigera en plan, ett program, en kampanj eller en leverans klickar du på namnet i kalendern och sedan på **[!UICONTROL Open...]**. Den visas sedan på en ny flik, enligt nedan:

![](assets/d_ncs_user_interface_hierar.png)

Du kan filtrera den information som visas i kampanjkalendern: klicka på **[!UICONTROL Filter]** och välj filtreringsvillkor.

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>När du filtrerar på ett datum visas alla kampanjer med ett startdatum som är senare än det angivna datumet och/eller med ett slutdatum som är tidigare än det angivna datumet. Välj datum med hjälp av kalendrarna till höger om varje fält.

Du kan också använda **[!UICONTROL Search]** för att filtrera de visade objekten.

Med ikonerna som är länkade till varje objekt kan du visa objektets status: färdig, pågående, redigerad osv.

### Sök i ett marknadsföringsprogram {#browsing-in-a-marketing-program}

Med Campaign kan ni hantera en uppsättning program som består av olika marknadsföringskampanjer. Varje kampanj innehåller leveranser och tillhörande processer och resurser.

#### Bläddra i ett program {#browsing-a-program}

När du redigerar ett program använder du flikarna nedan för att bläddra och konfigurera det.

* The **Schema** -fliken visar kalendern för program för en månad, vecka eller dag beroende på vilken flik du klickar på i kalenderrubriken.

  Om det behövs kan du skapa en kampanj, ett program eller en uppgift via den här sidan.

  ![](assets/s_ncs_user_interface_campaign02.png)

* The **Redigera** kan du anpassa programmet: namn, start- och slutdatum, budget, länkade dokument osv.

  ![](assets/s_ncs_user_interface_campaign05.png)

#### Söka efter kampanjer {#browsing-campaigns}

Kampanjer kan nås via kampanjkalendern, **[!UICONTROL Schedule]** -fliken i programmet eller en lista med kampanjer.

1. Välj den kampanj du vill visa via kampanjkalendern och klicka sedan på **[!UICONTROL Open]** länk.

   ![](assets/campaign_planning_edit_op.png)

   Kampanjen redigeras på en ny flik, vilket visas nedan:

   ![](assets/campaign_op_edit.png)

1. Via **[!UICONTROL Schedule]** redigeringsläget är detsamma som i kampanjkalendern.
1. Via **[!UICONTROL Campaigns]** länk till **[!UICONTROL Campaigns]** klickar du på namnet på den kampanj du vill redigera.

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
>Konfigurationen av kampanjmallar presenteras i [Kampanjmallar](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

#### Schema {#schedule}

En kampanj centraliserar en uppsättning leveranser. För varje kampanj ger schemat en global vy över alla komponenter: du kan visa uppgifter och leveranser och enkelt komma åt dem.

![](assets/campaign_planning_tab.png)

#### Forum {#forum}

För varje kampanj kan operatörerna utbyta meddelanden via ett särskilt forum.

Läs mer i [Diskussionsforum](../../mrm/using/discussion-forums.md).

#### Rapporter {#reports}

The **[!UICONTROL Reports]** kan du komma åt kampanjrapporterna.

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>Rapporterna beskrivs i [det här avsnittet](../../reporting/using/about-adobe-campaign-reporting-tools.md).

#### Konfiguration {#configuration}

Kampanjer skapas via kampanjmallar. Du kan konfigurera återanvändbara mallar för vilka vissa alternativ har valts och andra inställningar redan har sparats. För varje kampanj finns följande funktioner:

* Referens till [dokument och resurser](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents): du kan associera dokument med kampanjen (i korthet, rapport, bilder osv.). Alla dokumentformat stöds.
* Definiera kostnader: för varje kampanj kan Adobe Campaign definiera [kostnadsposter och kostnadsberäkningsstrukturer](../../campaign/using/providers--stocks-and-budgets.md#defining-cost-categories) som kan användas när marknadsföringskampanjen skapas. Exempel: tryckkostnader, användning av en extern byrå, rumshyrning.
* Definiera mål: du kan definiera kvantifierbara mål för en kampanj, t.ex. antal prenumeranter, affärsvolym osv. Den här informationen används senare i kampanjrapporter.
* Hantera [dirigeringsadresser](../../delivery/using/about-seed-addresses.md) och [kontrollgrupper](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).
* Hantera godkännanden: du kan välja de behandlingar som ska godkännas och, om det behövs, välja granskningsoperatorer eller grupper av operatorer. [Läs mer](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)

>[!NOTE]
>
>Om du vill komma åt kampanjkonfigurationerna och göra ändringar i dem klickar du på **[!UICONTROL Advanced campaign parameters...]** i **[!UICONTROL Edit]** -fliken.

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
| Leverans | Godkänn leveransinnehållet och målet<br/>Skicka leveransinnehållet<br/>Bekräfta leverans<br/>Pausa och stoppa leverans |
| Webbprogram | Skapa ett webbprogram<br/>Redigera programinnehåll och -egenskaper<br/>Spara programinnehållet som en mall<br/>Publicera programmet |
| Erbjudande | Godkänn erbjudandets innehåll och behörighet<br/>Inaktivera ett onlineerbjudande |
| Uppgift | Avsluta en uppgift<br/>Avbryt en uppgift |
| Marknadsföringsresurser | Godkänn en resurs<br/>Låsa och låsa upp en resurs |
| Kampanjpaket | Skicka ett paket för godkännande<br/>Godkänn eller avvisa ett paket<br/>Avbryt ett paket |
| Kampanjorder | Skapa en order<br/>Acceptera eller avvisa en order <!-- Je n'ai pas pu créer de campaign order pour vérifier cela. Peut-on accéder à ces fonctionnalités depuis l'accès web ? --> |
| Stock | Ta bort en aktierad |
| Simulering av erbjudanden | Starta och stoppa en simulering |
| Målarbetsflöde | Starta, pausa och stoppa ett arbetsflöde |
| Rapportera | Spara aktuella data i rapporthistoriken |
| Forum | Lägg till en diskussion<br/>Svara på ett meddelande i en diskussion<br/>Följ en diskussion och avsluta prenumerationen på den |

### Godkännanden

Godkännanden (till exempel av ett mål eller ett leveransinnehåll) kan utföras via webbåtkomst.

![](assets/campaign_web_interface_validation.png)

Du kan också använda länken i meddelandena. Mer information finns i [Kontrollera och godkänna leveranser](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).
