---
title: Skapa en samverkanskampanj
seo-title: Skapa en samverkanskampanj
description: Skapa en samverkanskampanj
seo-description: null
page-status-flag: never-activated
uuid: 13d8ff65-1480-422a-85b6-40b553a3c151
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 01d8be92-7312-4386-b5f5-651af31308f7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# Skapa en samverkanskampanj{#creating-a-collaborative-campaign-intro}

Den centrala enheten skapar samarbetskampanjer utifrån mallar för **distribuerade marknadsföringskampanjer** . Se [den här sidan](../../campaign/using/about-distributed-marketing.md#collaborative-campaign).

## Skapa en samverkanskampanj {#creating-a-collaborative-campaign}

Om du vill konfigurera en kampanj för samarbete klickar du på **[!UICONTROL Campaign management > Campaigns]** noden och sedan på **[!UICONTROL New]** ikonen .

>[!NOTE]
>
>Förutom **[!UICONTROL collaborative campaigns (by campaign)]** dessa kampanjer kan konfigureras och köras via ett webbgränssnitt.

Konfigurationsprocessen för en databas för en samarbetskampanj liknar den för en lokal kampanjmall. Specifikationerna för de olika typerna av samarbetskampanjer anges nedan.

### Per formulär {#by-form}

Om du vill skapa en samarbetskampanj (per formulär) måste du välja **[!UICONTROL Collaborative campaign (by form)]** mallen.

![](assets/mkg_dist_mutual_op_form2.png)

Klicka på länken på **[!UICONTROL Edit]** fliken för att **[!UICONTROL Advanced campaign settings...]** öppna fliken **Distribuerad marknadsföring** .

Välj webbgränssnittet **Efter formulär** . Med den här typen av gränssnitt kan du skapa anpassningsfält som ska användas av lokala enheter när du beställer en kampanj. Se [Skapa en lokal kampanj (per formulär)](../../campaign/using/examples.md#creating-a-local-campaign--by-form-).

Spara kampanjen. Nu kan du använda den från **vyn Campaign-paket** i **Campaign** -universum genom att klicka på **[!UICONTROL Create]** -knappen.

I **[!UICONTROL Campaign Package]** vyn kan ni använda lokala kampanjmallar (färdiga eller duplicerade) samt referenskampanjer för samarbetskampanjer, i syfte att skapa kampanjer för olika organisatoriska enheter.

![](assets/mkg_dist_mutual_op_form1b.png)

### Per kampanj {#by-campaign}

Om du vill skapa en samarbetskampanj (per kampanj) måste du välja **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]** mallen.

![](assets/mkg_dist_mutual_op_by_op2.png)

När kampanjen beställs kan den lokala enheten slutföra de villkor som den centrala enheten har fördefinierat och utvärdera kampanjen innan den beställs.

När en order för en **samarbetskampanj (per kampanj)** har godkänts av den centrala enheten skapas en underordnad kampanj för den lokala enheten. När den lokala enheten är tillgänglig kan den sedan ändra:

* kampanjarbetsflödet,
* typologiregler,
* och personaliseringsfält.

Den lokala entiteten kör den underordnade kampanjen. Den centrala enheten kör den överordnade kampanjen.

Den centrala enheten kan visa alla underordnade kampanjer som är länkade till en **samarbetskampanj (per kampanj)** från den här instrumentpanelen (via **[!UICONTROL List of associated campaigns]** länken).

![](assets/mkg_dist_mutual_op_by_op.png)

### Efter målgodkännande {#by-target-approval}

Om du vill skapa en samarbetskampanj (genom målgodkännande) måste du välja **[!UICONTROL Collaborative campaign (by target approval)]** mallen.

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>I det här läget behöver den centrala enheten inte ange lokala enheter.

Kampanjarbetsflödet måste integrera aktiviteten **Lokal typ av godkännande** . Aktivitetsparametrarna är följande:

* **[!UICONTROL Action to perform]** : Målmeddelande för godkännande.
* **[!UICONTROL Distribution context]** : Explicit.
* **[!UICONTROL Data distribution]** : Lokal entitetsdistribution.

**Datadistributionen för den lokala entitetens distributionstyp** måste skapas. Med mallen för datadistribution kan du begränsa antalet poster från en lista med grupperingsvärden. Klicka **[!UICONTROL Resources > Campaign management > Data distribution]** på **[!UICONTROL New]** ikonen för att skapa en ny **[!UICONTROL Data distribution]**. Mer information om datadistribution finns i handboken [Arbetsflöden](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-) .

![](assets/mkg_dist_data_distribution.png)

Välj **Måldimension** och **[!UICONTROL Distribution field]**. För **[!UICONTROL Assignment type]** väljer du **Lokal entitet**.

Lägg till ett fält för varje lokal enhet på **[!UICONTROL Distribution]** fliken och ange värdet.

![](assets/mkg_dist_data_distribution2.png)

Du kan lägga till ett andra **målgodkännande** efter aktiviteten **Leveranstyp** för att konfigurera en rapport för det.

I meddelandet om att kampanjen har skapats får den lokala enheten en kontaktlista som har fördefinierats av de centrala enhetsparametrarna.

![](assets/mkg_dist_mutual_op_by_valid1.png)

Den lokala enheten kan ta bort vissa kontakter baserat på kampanjinnehållet.

![](assets/mkg_dist_mutual_op_by_valid2.png)

### Enkel {#simple}

Om du vill skapa en enkel samarbetskampanj måste du välja **[!UICONTROL Collaborative campaign (simple)]** en mall.

## Skapa ett kampanjpaket för samarbete {#creating-a-collaborative-campaign-package}

För att göra en kampanj tillgänglig för lokala enheter måste den centrala enheten skapa ett kampanjpaket.

Använd följande steg:

1. Klicka på **[!UICONTROL Navigation]** länken i avsnittet **på sidan** Kampanjer **[!UICONTROL Campaign packages]** .
1. Klicka på **[!UICONTROL Create]** knappen.
1. I avsnittet högst upp i fönstret kan du välja **[!UICONTROL New collaborative package (mutualizedEmpty)]** mallen.
1. Välj referenskampanj.
1. Ange etikett, mapp och körningsschema för kampanjpaketet.

### Datum {#dates}

Start- och slutdatumen definierar kampanjens synlighetsperiod i listan över kampanjpaket.

För **samarbetskampanjer** måste den centrala enheten ange en deadline för registrering och personalisering.

>[!NOTE]
>
>På **[!UICONTROL Personalization deadline]** så sätt kan den centrala enheten välja en tidsgräns inom vilken de lokala enheterna måste ha levererat de dokument (kalkylblad, bilder) som ska användas för att konfigurera kampanjen. Detta är inte ett obligatoriskt alternativ. Sidstegning av det här datumet påverkar inte kampanjens implementering.

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### Målgrupp {#audience}

Den centrala enheten måste specificera de lokala enheter som är inblandade per kampanj så snart en samarbetskampanj har skapats.

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** kan inte godkännas om inte de relevanta lokala enheterna har specificerats.

### Godkännandelägen {#approval-modes}

För **samarbetskampanjer** kan du ange ordergodkännandeläge.

![](assets/mkg_dist_edit_kit1.png)

I manuellt läge måste den lokala enheten prenumerera på kampanjen för att kunna delta.

I automatiskt läge är den lokala enheten förregistrerad för kampanjen. Den kan avbryta kampanjprenumerationen eller ändra parametrarna utan att den centrala enheten behöver godkänna prenumerationen.

![](assets/mkg_dist_edit_kit2.png)

### Meddelanden {#notifications}

Konfigurationen för meddelanden är identisk med aviseringar för en lokal enhet. Se [det här avsnittet](../../campaign/using/creating-a-local-campaign.md#notifications).

## Beställa en kampanj {#ordering-a-campaign}

När en samarbetskampanj läggs till i listan över kampanjpaket meddelas de lokala enheter som tillhör den målgrupp som definieras av den centrala enheten ( **samarbetskampanjer (med målgodkännande)** har ingen fördefinierad målgrupp). Det skickade meddelandet innehåller en länk som gör att du kan registrera dig för kampanjen, vilket visas nedan:

![](assets/mkg_dist_mutual_op_notification.png)

Det här meddelandet gör det även möjligt för lokala enheter att visa den beskrivning som anges av den centrala operatör som skapade paketet samt dokument som är länkade till kampanjen. Dessa tillhör inte själva kampanjen, även om de ger ytterligare information om den.

När lokala operatörer har loggat in via ett webbgränssnitt kan de ange personlig information till den samarbetskampanj de vill beställa:

![](assets/mkg_dist_mutual_op_command.png)

När en lokal enhet har slutfört sin registrering meddelas centrala enheter via e-post för att godkänna deras beställning.

![](assets/mkg_dist_mutual_op_valid_command.png)

Mer information finns i avsnittet [Godkännandeprocess](../../campaign/using/creating-a-local-campaign.md#approval-process) .

## Godkänna en order {#approving-an-order}

Processen för att godkänna en kollaborativ kampanjpaketorder är densamma som för en lokal kampanj. Se [det här avsnittet](../../campaign/using/creating-a-local-campaign.md#approving-an-order).
