---
product: campaign
title: Åtkomst till marknadsföringskampanjer
description: Åtkomst till marknadsföringskampanjer
audience: campaign
content-type: reference
topic-tags: about-marketing-campaigns
exl-id: 1278bda1-f83c-4d38-8042-e6611755cf36
source-git-commit: ee3d643e4ba607b3d7ca816eabf862b867d1f3f4
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 1%

---

# Åtkomst till marknadsföringskampanjer{#accessing-marketing-campaigns}

Med Adobe Campaign kan ni skapa, konfigurera, genomföra och analysera marknadsföringskampanjer. Alla marknadsföringskampanjer kan hanteras från ett enhetligt kontrollcenter.

## Grundläggande om arbetsytan {#workspace-basics}

### Startsida {#home-page}

När du har anslutit till Adobe Campaign visas startsidan.

![](assets/campaign_global_view.png)

Klicka på länkarna i navigeringsfältet för att komma åt de olika funktionerna.

Kampanjelement finns på fliken **[!UICONTROL Campaigns]**: här kan du se en översikt över marknadsföringsprogram och -kampanjer samt deras undergrupper. Ett marknadsföringsprogram består av kampanjer, som består av leveranser, uppgifter, länkade resurser osv. När det gäller hantering av marknadsföringskampanjer med Campaign finns det information om leveranser, budgetar, granskare och länkade dokument i kampanjerna.

**[!UICONTROL Browsing]**-blocket på fliken **[!UICONTROL Campaigns]** erbjuder olika poster, beroende på vilka moduler som är installerade på instansen. Du kan till exempel få åtkomst till:

* **Kampanjkalender**: planeringskalender, marknadsföringsprogram, leveranser och kampanjer. Se [Kampanjkalender](#campaign-calendar).
* **Kampanjer**: tillgång till kampanjer i alla marknadsföringsprogram.
* **Leveranser**: åtkomst till leveranser som är kopplade till kampanjerna.
* **Webbprogram**: tillgång till webbapplikationer (formulär, landningssidor osv.).

>[!NOTE]
>
>Mer information om Adobe Campaign allmänna ergonomi, behörigheter och profilhanteringsfunktioner finns i [det här avsnittet](../../platform/using/adobe-campaign-workspace.md).
>
>Alla funktioner som rör kanaler och leveranser beskrivs i [det här avsnittet](../../delivery/using/steps-about-delivery-creation-steps.md).

### Kampanjkalender {#campaign-calendar}

Varje kampanj tillhör ett program som i sin tur tillhör en plan. Planer, program och kampanjer nås via menyn **[!UICONTROL Campaign calendar]** på fliken **Kampanjer**.

Om du vill redigera en plan, ett program, en kampanj eller en leverans klickar du på namnet i kalendern och sedan på **[!UICONTROL Open...]**. Den visas sedan på en ny flik, enligt nedan:

![](assets/d_ncs_user_interface_hierar.png)

Du kan filtrera den information som visas i kampanjkalendern. Det gör du genom att klicka på länken **[!UICONTROL Filter]** och välja filtervillkoren.

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>När du filtrerar på ett datum visas alla kampanjer med ett startdatum som är senare än det angivna datumet och/eller med ett slutdatum som är tidigare än det angivna datumet. Datum måste väljas med hjälp av kalendrarna till höger om varje fält.

Du kan också använda fältet **[!UICONTROL Search]** för att filtrera de visade objekten.

Med ikonerna som är länkade till varje objekt kan du visa objektets status: klart, pågående, redigeras osv.

### Bläddra i ett marknadsföringsprogram {#browsing-in-a-marketing-program}

Med Campaign kan ni hantera en uppsättning program som består av olika marknadsföringskampanjer. Varje kampanj innehåller leveranser och tillhörande processer och resurser.

#### Bläddra i ett program {#browsing-a-program}

När du redigerar ett program använder du flikarna nedan för att bläddra och konfigurera det.

* På fliken **Schema** visas kalendern med program för en månad, vecka eller dag beroende på vilken flik du klickar på i kalenderrubriken.

   Om det behövs kan du skapa en kampanj, ett program eller en uppgift via den här sidan.

   ![](assets/s_ncs_user_interface_campaign02.png)

* På fliken **Redigera** kan du anpassa programmet: namn, start- och slutdatum, budget, länkade dokument osv.

   ![](assets/s_ncs_user_interface_campaign05.png)

#### Bläddra bland kampanjer {#browsing-campaigns}

Kampanjer kan nås via kampanjkalendern, fliken **[!UICONTROL Schedule]** i programmet eller listan över kampanjer.

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

Kontrollpanelen för en kampanj används som ett kontrollgränssnitt. Här kommer man åt de viktigaste faserna för att skapa och hantera kampanjer direkt: leveranser, extraheringsfiler, meddelanden, budgetar osv.

![](assets/s_ncs_user_op_board_start_del.png)

Med Adobe Campaign kan ni skapa samarbetsprocesser för framtagning och godkännande av de olika stadierna av marknadsförings- och kommunikationskampanjer: godkännande av budget, mål, innehåll osv.

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>Konfigurationen av kampanjmallar presenteras i [Kampanjmallar](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

#### Schema {#schedule}

En kampanj centraliserar en uppsättning leveranser. För varje kampanj ger schemat en global vy över alla komponenter: På så sätt kan du visa uppgifter och leveranser och enkelt komma åt dem.

![](assets/campaign_planning_tab.png)

#### Forum {#forum}

För varje kampanj kan operatörerna utbyta meddelanden via ett särskilt forum.

Mer information finns i [Diskussionsforum](../../mrm/using/discussion-forums.md).

#### Rapporter {#reports}

Med länken **[!UICONTROL Reports]** kommer du åt kampanjrapporterna.

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>Rapporterna beskrivs i [det här avsnittet](../../reporting/using/about-adobe-campaign-reporting-tools.md).

#### Konfiguration {#configuration}

Kampanjer skapas via kampanjmallar. Du kan konfigurera återanvändbara mallar för vilka vissa alternativ har valts och andra inställningar redan har sparats. För varje kampanj finns följande funktioner:

* Hänvisning till dokument och resurser: du kan associera dokument med kampanjen (i korthet, rapport, bilder osv.). Alla dokumentformat stöds. Se [Hantera associerade dokument](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents).
* Definiera kostnader: För varje kampanj kan Adobe Campaign definiera kostnadsposter och kostnadsberäkningsstrukturer som kan användas när marknadsföringskampanjen skapas. Till exempel: tryckkostnader, användning av en extern byrå, hyra av rum osv. Se [Definiera kostnadskategorier](../../campaign/using/providers--stocks-and-budgets.md#defining-cost-categories).
* Definiera mål: kan ni definiera kvantifierbara mål för en kampanj, t.ex. antal prenumeranter, affärsvolym osv. Den här informationen används senare i kampanjrapporter.
* Hantera dirigerade adresser (mer information om detta finns i [det här avsnittet](../../delivery/using/about-seed-addresses.md)) och kontrollgrupper (se [Definiera en kontrollgrupp](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)).
* Hantera godkännanden: Du kan välja vilka behandlingar som ska godkännas och vid behov välja granskningsoperatorer eller grupper av operatorer. Se [Kontrollera och godkänna leveranser](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

>[!NOTE]
>
>Klicka på länken **[!UICONTROL Advanced campaign parameters...]** på fliken **[!UICONTROL Edit]** om du vill komma åt kampanjkonfigurationerna och göra ändringar i dem. Mer information om att ställa in parametrar på kampanjnivå så att leveranser automatiskt ärver värden finns i [vår Technote](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Setparametersatthecampaignlevelsodeliveriesinheritvaluesautomatically).

## Använda webbgränssnittet {#using-the-web-interface-}

Du kan öppna Adobe Campaign konsolskärmar via en webbläsare och visa alla kampanjer och leveranser samt rapporter och information om profilerna i din databas. Det går inte att skapa poster med den här åtkomsten. Beroende på användarrättigheterna kan du visa och/eller agera på data i databasen. Du kan till exempel godkänna kampanjinnehåll och målinriktning, starta om eller stoppa en leverans osv.

1. Logga in som vanligt via https://`<your instance>:<port>/view/home`.
1. Använd menyerna för att komma åt översikterna.

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

Godkännanden (till exempel av ett mål eller ett leveransinnehåll) kan utföras via webbåtkomst.

![](assets/campaign_web_interface_validation.png)

Du kan också använda länken i meddelandena. Mer information finns i [Kontrollera och godkänna leveranser](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).
