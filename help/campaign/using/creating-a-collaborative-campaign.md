---
product: campaign
title: Skapa en samverkanskampanj
description: Skapa en samverkanskampanj
audience: campaign
content-type: reference
topic-tags: distributed-marketing
exl-id: 17313fe5-ad42-45ca-a35a-1e7aa89380ef
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 3%

---

# Skapa en samverkanskampanj{#creating-a-collaborative-campaign-intro}

Den centrala enheten skapar samarbetskampanjer från **Distributed Marketing** kampanjmallar. Se [den här sidan](../../campaign/using/about-distributed-marketing.md#collaborative-campaign).

## Skapa en samverkanskampanj {#creating-a-collaborative-campaign}

Klicka på noden **[!UICONTROL Campaign management > Campaigns]** och sedan på ikonen **[!UICONTROL New]** för att konfigurera en samarbetskampanj.

>[!NOTE]
>
>Förutom **[!UICONTROL collaborative campaigns (by campaign)]** kan dessa kampanjer konfigureras och köras via ett webbgränssnitt.

Konfigurationsprocessen för en databas för en samarbetskampanj liknar den för en lokal kampanjmall. Specifikationerna för de olika typerna av samarbetskampanjer anges nedan.

### Efter formulär {#by-form}

Om du vill skapa en samarbetskampanj (efter formulär) måste du välja **[!UICONTROL Collaborative campaign (by form)]**-mallen.

![](assets/mkg_dist_mutual_op_form2.png)

På fliken **[!UICONTROL Edit]** klickar du på länken **[!UICONTROL Advanced campaign settings...]** för att komma åt fliken **Distributed Marketing**.

Välj webbgränssnittet **Efter formulär**. Med den här typen av gränssnitt kan du skapa anpassningsfält som ska användas av lokala enheter när du beställer en kampanj. Se [Skapa en lokal kampanj (efter formulär)](../../campaign/using/examples.md#creating-a-local-campaign--by-form-).

Spara kampanjen. Du kan nu använda den från vyn **Kampanjpaket** på fliken **Kampanj** genom att klicka på knappen **[!UICONTROL Create]**.

I vyn **[!UICONTROL Campaign Package]** kan du använda lokala kampanjmallar (körklara eller duplicerade) samt referenskampanjer för samarbetskampanjer, i syfte att skapa kampanjer för olika organisationsenheter.

![](assets/mkg_dist_mutual_op_form1b.png)

### Efter kampanj {#by-campaign}

Om du vill skapa en samarbetskampanj (per kampanj) måste du välja **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]**-mallen.

![](assets/mkg_dist_mutual_op_by_op2.png)

När kampanjen beställs kan den lokala enheten slutföra de villkor som den centrala enheten har fördefinierat och utvärdera kampanjen innan den beställs.

När en order för en **samarbetskampanj (efter kampanj)** har godkänts av den centrala enheten skapas en underordnad kampanj för den lokala enheten. När den lokala enheten är tillgänglig kan den sedan ändra:

* kampanjarbetsflödet,
* typologiregler,
* och personaliseringsfält.

Den lokala entiteten kör den underordnade kampanjen. Den centrala enheten kör den överordnade kampanjen.

Den centrala enheten kan visa alla underordnade kampanjer som är länkade till en **Samarbetskampanj (per kampanj)** från den här instrumentpanelen (via länken **[!UICONTROL List of associated campaigns]**).

![](assets/mkg_dist_mutual_op_by_op.png)

### Efter målgodkännande {#by-target-approval}

Om du vill skapa en samarbetskampanj (med målgodkännande) måste du välja mallen **[!UICONTROL Collaborative campaign (by target approval)]**.

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>I det här läget behöver den centrala enheten inte ange lokala enheter.

Kampanjarbetsflödet måste integrera typaktiviteten **Lokalt godkännande**. Aktivitetsparametrarna är följande:

* **[!UICONTROL Action to perform]** : Målmeddelande för godkännande.
* **[!UICONTROL Distribution context]** : Explicit.
* **[!UICONTROL Data distribution]** : Lokal entitetsdistribution.

**Distributionen av data** för den lokala entitetens distributionstyp måste skapas. Med mallen för datadistribution kan du begränsa antalet poster från en lista med grupperingsvärden. I **[!UICONTROL Resources > Campaign management > Data distribution]** klickar du på ikonen **[!UICONTROL New]** för att skapa en ny **[!UICONTROL Data distribution]**. Mer information om datadistribution finns i guiden [Arbetsflöden](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-).

![](assets/mkg_dist_data_distribution.png)

Markera **måldimensionen** och **[!UICONTROL Distribution field]**. För **[!UICONTROL Assignment type]** väljer du **Lokal enhet**.

Lägg till ett fält för varje lokal enhet och ange värdet på fliken **[!UICONTROL Distribution]**.

![](assets/mkg_dist_data_distribution2.png)

Du kan lägga till en andra **målgodkännande** efter **leveransaktiviteten** för att konfigurera en rapport för den.

I meddelandet om att kampanjen har skapats får den lokala enheten en kontaktlista som har fördefinierats av parametrarna för den centrala enheten.

![](assets/mkg_dist_mutual_op_by_valid1.png)

Den lokala enheten kan ta bort vissa kontakter baserat på kampanjinnehållet.

![](assets/mkg_dist_mutual_op_by_valid2.png)

### Enkel {#simple}

Om du vill skapa en enkel samarbetskampanj måste du välja **[!UICONTROL Collaborative campaign (simple)]**-mallen.

## Skapa ett kampanjpaket för samarbete {#creating-a-collaborative-campaign-package}

För att göra en kampanj tillgänglig för lokala enheter måste den centrala enheten skapa ett kampanjpaket.

Använd följande steg:

1. Klicka på länken **[!UICONTROL Campaign packages]** i avsnittet **[!UICONTROL Navigation]** på sidan **Kampanjer**.
1. Klicka på knappen **[!UICONTROL Create]**.
1. I avsnittet högst upp i fönstret kan du välja mallen **[!UICONTROL New collaborative package (mutualizedEmpty)]**.
1. Välj referenskampanj.
1. Ange etikett, mapp och körningsschema för kampanjpaketet.

### Datum {#dates}

Start- och slutdatumen definierar kampanjens synlighetsperiod i listan över kampanjpaket.

För **samarbetskampanjer** måste den centrala enheten ange deadline för registrering och personalisering.

>[!NOTE]
>
>Med **[!UICONTROL Personalization deadline]** kan den centrala enheten välja en tidsgräns inom vilken de lokala enheterna måste ha levererat de dokument (kalkylblad, bilder) som ska användas för att konfigurera kampanjen. Detta är inte ett obligatoriskt alternativ. Sidstegning av det här datumet påverkar inte kampanjens implementering.

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

När en samarbetskampanj läggs till i listan över kampanjpaket meddelas de lokala enheterna som tillhör den målgrupp som definieras av den centrala enheten (de **samarbetskampanjer (genom målgodkännande)** saknar en fördefinierad målgrupp). Det skickade meddelandet innehåller en länk som gör att du kan registrera dig för kampanjen, vilket visas nedan:

![](assets/mkg_dist_mutual_op_notification.png)

Det här meddelandet gör det även möjligt för lokala enheter att visa den beskrivning som anges av den centrala operatör som skapade paketet samt dokument som är länkade till kampanjen. Dessa tillhör inte själva kampanjen, även om de ger ytterligare information om den.

När lokala operatörer har loggat in via ett webbgränssnitt kan de ange personlig information till den samarbetskampanj de vill beställa:

![](assets/mkg_dist_mutual_op_command.png)

När en lokal enhet har slutfört sin registrering meddelas centrala enheter via e-post för att godkänna deras beställning.

![](assets/mkg_dist_mutual_op_valid_command.png)

Mer information finns i avsnittet [Godkännandeprocess](../../campaign/using/creating-a-local-campaign.md#approval-process).

## Godkänna en order {#approving-an-order}

Processen för att godkänna en kollaborativ kampanjpaketorder är densamma som för en lokal kampanj. Se [det här avsnittet](../../campaign/using/creating-a-local-campaign.md#approving-an-order).
