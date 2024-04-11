---
product: campaign
title: Konfigurera integrering av delade målgrupper i Adobe Campaign
description: Lär dig konfigurera integrering av delade målgrupper
feature: Audiences, People Core Service Integration
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: a3e26cff-9609-4d91-8976-9213a30c3fd2
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# Konfigurera integrering av delade målgrupper i Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}



När du har skickat in den här begäran fortsätter Adobe till att tillhandahålla integreringen åt dig och kontaktar dig för att ange information och information som du måste slutföra konfigurationen:

1. [Steg 1: Konfigurera eller kontrollera externa konton i Adobe Campaign](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Steg 2: Konfigurera datakällan](#step-2--configure-the-data-source)
1. [Steg 3: Konfigurera kampanjspårningsserver](#step-3--configure-campaign-tracking-server)
1. [Steg 4: Konfigurera besökar-ID-tjänsten](#step-4--configure-the-visitor-id-service)

>[!IMPORTANT]
>
>Om du använder demodomänen och följer syntaxen **ftp-out.demdex.com** för det externa importkontot och **ftp-in.demdex.com** för det externa exportkontot måste du anpassa implementeringen och gå över till kopplingen för Amazon Simple Storage Service (S3) för att importera eller exportera data. Mer information om hur du konfigurerar dina externa konton med Amazon S3 finns i [section](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md#step-1--configure-or-check-the-external-accounts-in-adobe-campaign).

Följande diagram visar hur den här integreringen fungerar. Här står AAM för Adobe Audience Manager och AC för Adobe Campaign.

![](assets/aam_diagram.png){align="center"}

## Steg 1: Konfigurera eller kontrollera externa konton i Adobe Campaign {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

Först måste vi konfigurera eller kontrollera externa konton i Adobe Campaign enligt följande:

1. Klicka på **[!UICONTROL Explorer]** -ikon.
1. Gå till **[!UICONTROL Administration > Platform > External accounts]**. Adobe borde ha konfigurerat SFTP-kontona och du borde ha fått den information som behövs.

   * **[!UICONTROL importSharedAudience]**: konto som används för att importera målgrupper.
   * **[!UICONTROL exportSharedAudience]**: konto som används för att exportera målgrupper.

   ![](assets/aam_config_1.png)

1. Välj **[!UICONTROL Export audiences to the Adobe Marketing Cloud]** externt konto.

1. Från **[!UICONTROL Type]** nedrullningsbar meny, välja **[!UICONTROL AWS S3]**.

1. Ange följande information:

   * **[!UICONTROL AWS S3 Account Server]**
URL-adressen till servern ska fyllas i enligt följande:

     ```
     <S3bucket name>.s3.amazonaws.com/<s3object path>
     ```

   * **[!UICONTROL AWS access key ID]**
Om du vill veta var du hittar ditt ID för AWS-åtkomstnyckel kan du läsa detta [page](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

   * **[!UICONTROL Secret access key to AWS]**
Om du vill veta var du hittar din hemliga åtkomstnyckel till AWS kan du läsa detta [page](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

   * **[!UICONTROL AWS Region]**
Läs mer om AWS [page](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

   ![](assets/aam_config_2.png)

1. Klicka **[!UICONTROL Save]** och konfigurera **[!UICONTROL Import audiences from the Adobe Marketing Cloud]** externt konto enligt beskrivningen i föregående steg.

Dina externa konton har nu konfigurerats.

## Steg 2: Konfigurera datakällan {#step-2--configure-the-data-source}

The **Mottagare - besökar-ID** skapas inuti Audience Manager. Detta är en användbar datakälla som konfigurerats som standard för besökar-ID. Segment som skapas från Campaign kommer att ingå i den här datakällan.

Konfigurera **[!UICONTROL Recipient - Visitor ID]** datakälla:

1. Från **[!UICONTROL Explorer]** nod, markera **[!UICONTROL Administration > Platform > AMC Data sources]**.
1. Välj **[!UICONTROL Recipient - Visitor ID]**.
1. Ange **[!UICONTROL Data Source ID]** och **[!UICONTROL AAM Destination ID]** tillhandahålls av Adobe.

   ![](assets/aam_config_3.png)

## Steg 3: Konfigurera kampanjspårningsserver {#step-3--configure-campaign-tracking-server}

För konfigurationen av integreringen med tjänsten People Core eller Audience Manager måste vi även konfigurera Campaign Tracking-servern.

Om du vill att delade målgrupper ska kunna fungera med besökar-ID, måste spårningsserverdomänen vara en underdomän till den klickade URL:en eller huvudwebbplatsen.

>[!IMPORTANT]
>
>Du måste kontrollera att Campaign Tracking Server är registrerad på domänen (CNAME). Mer information om delegering av domännamn finns i [den här artikeln](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=sv).

## Steg 4: Konfigurera besökar-ID-tjänsten {#step-4--configure-the-visitor-id-service}

Om din Visitor ID-tjänst aldrig har konfigurerats på dina webbegenskaper eller webbplatser kan du läsa följande [dokument](https://experienceleague.adobe.com/docs/id-service/using/implementation/setup-aam-analytics.html) om du vill veta mer om hur du konfigurerar tjänsten eller följande [video](https://helpx.adobe.com/marketing-cloud/how-to/email-marketing.html#step-two).

Synkronisera kundidentifierare med deklarerat ID med `setCustomerID` i Experience Cloud ID-tjänsten med integreringskoden: `AdobeCampaignID`. The `AdobeCampaignID` ska matcha värdet för avstämningsnyckeln som angetts i mottagardatakällan som konfigurerats i [Steg 2: Konfigurera datakällorna](#step-2--configure-the-data-sources).

Din konfiguration och etablering är färdiga, och integreringen kan nu användas för att importera och exportera målgrupper eller segment.
