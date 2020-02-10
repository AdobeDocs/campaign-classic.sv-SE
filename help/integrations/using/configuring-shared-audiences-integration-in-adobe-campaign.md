---
title: Konfigurera integrering av delade målgrupper i Adobe Campaign
seo-title: Konfigurera integrering av delade målgrupper i Adobe Campaign
description: Konfigurera integrering av delade målgrupper i Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: 6ed137e4-027f-4eb0-a0b5-4beb7deef51f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 4443b0ca-80c6-467d-a4df-50864aae8496
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6ae45cbd87fc0152fc654202e03501fc8d2abd06

---


# Konfigurera integrering av delade målgrupper i Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}

När du har skickat in din begäran fortsätter Adobe att distribuera integreringen åt dig och kontaktar dig för att ange information och information som du måste slutföra konfigurationen:

1. [Steg 1: Konfigurera eller kontrollera externa konton i Adobe Campaign](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Steg 2: Konfigurera datakällan](#step-2--configure-the-data-source)
1. [Steg 3: Konfigurera kampanjspårningsserver](#step-3--configure-campaign-tracking-server)
1. [Steg 4: Konfigurera besökar-ID-tjänsten](#step-4--configure-the-visitor-id-service)

## Steg 1: Konfigurera eller kontrollera externa konton i Adobe Campaign {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

Först måste vi konfigurera eller kontrollera de externa kontona i Adobe Campaign enligt följande:

1. Klicka på **[!UICONTROL Explorer]** ikonen.
1. Gå till **[!UICONTROL Administration > Platform > External accounts]**. Adobe borde ha konfigurerat SFTP-kontona och du borde ha fått den information du behöver.

   * **[!UICONTROL importSharedAudience]** : SFTP-konto för att importera målgrupper.
   * **[!UICONTROL exportSharedAudience]** : SFTP-konto för export av målgrupper.
   ![](assets/aam_config_1.png)

1. Fyll i **[!UICONTROL Server]** fältet: domänen **ftp-out.demdex.com** för det externa importkontot och domänen **ftp-in.demdex.com** för det externa exportkontot.

   Kom ihåg att en export från Campaign är en import för huvudtjänsten Audience Manager eller People.

   >[!NOTE]
   >
   >Om du använder S3 anger du **[!UICONTROL AWS S3 Account Server]** följande syntax:\
   `<S3bucket name>.s3.amazonaws.com/<s3object path>`\
   Mer information om hur du konfigurerar ditt S3-konto finns på den här [sidan](../../platform/using/external-accounts.md#amazon-simple-storage-service--s3--external-account).

   ![](assets/aam_config_2.png)

1. Lägg till **[!UICONTROL Account]** och **[!UICONTROL Password]** tillhandahålls av Adobe.

Dina externa konton har nu konfigurerats.

## Steg 2: Konfigurera datakällan {#step-2--configure-the-data-source}

Mottagar- **ID** för besökare skapas i Audience Manager. Detta är en användbar datakälla som konfigurerats som standard för besökar-ID. Segment som skapas från Campaign kommer att ingå i den här datakällan.

Så här konfigurerar du **[!UICONTROL Recipient - Visitor ID]** datakällan:

1. Välj från **[!UICONTROL Explorer]** noden **[!UICONTROL Administration > Platform > AMC Data sources]**.
1. Välj **[!UICONTROL Recipient - Visitor ID]**.
1. Ange **[!UICONTROL Data Source ID]** och **[!UICONTROL AAM Destination ID]** få information från Adobe.

   ![](assets/aam_config_3.png)

## Steg 3: Konfigurera kampanjspårningsserver {#step-3--configure-campaign-tracking-server}

För konfigurationen av integreringen med tjänsten People Core eller Audience Manager måste vi även konfigurera Campaign Tracking-servern.

Du måste kontrollera att Campaign Tracking Server är registrerad på domänen (CNAME). Mer information om delegering av domännamn finns i [den här artikeln](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html).

## Steg 4: Konfigurera besökar-ID-tjänsten {#step-4--configure-the-visitor-id-service}

Om din besökar-ID-tjänst aldrig har konfigurerats på dina webbegenskaper eller webbplatser kan du läsa följande [dokument](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid-setup-aam-analytics.html) för att lära dig hur du konfigurerar tjänsten eller följande [video](https://helpx.adobe.com/marketing-cloud/how-to/email-marketing.html#step-two) .

Din konfiguration och etablering är färdiga, och integreringen kan nu användas för att importera och exportera målgrupper eller segment.
