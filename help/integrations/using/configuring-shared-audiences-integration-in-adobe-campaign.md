---
product: campaign
title: Konfigurera integrering av delade målgrupper i Adobe Campaign
description: Lär dig konfigurera integrering av delade målgrupper
feature: Audiences
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: a3e26cff-9609-4d91-8976-9213a30c3fd2
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Konfigurera integrering av delade målgrupper i Adobe Campaign{#configuring-shared-audiences-integration-in-adobe-campaign}


När du har skickat in den här begäran fortsätter Adobe till att tillhandahålla integreringen åt dig och kontaktar dig för att ange information och information som du måste slutföra konfigurationen:

1. [Steg 1: Konfigurera eller kontrollera externa konton i Adobe Campaign](#step-1--configure-or-check-the-external-accounts-in-adobe-campaign)
1. [Steg 2: Konfigurera Data Source](#step-2--configure-the-data-source)
1. [Steg 3: Konfigurera kampanjspårningsserver](#step-3--configure-campaign-tracking-server)
1. [Steg 4: Konfigurera besökar-ID-tjänsten](#step-4--configure-the-visitor-id-service)

>[!IMPORTANT]
>
>Om du använder demodomänen och följer syntaxen **ftp-out.demdex.com** för det externa importkontot och **ftp-in.demdex.com** för det externa exportkontot måste du anpassa implementeringen och gå över till kopplingen för Amazon Simple Storage Service (S3) för att importera eller exportera data. Mer information om hur du konfigurerar externa konton med Amazon S3 finns i [avsnittet](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md#step-1--configure-or-check-the-external-accounts-in-adobe-campaign).

Följande diagram visar hur den här integreringen fungerar. Här står AAM för Adobe Audience Manager och AC för Adobe Campaign.

![](assets/aam_diagram.png){align="center"}

## Steg 1: Konfigurera eller kontrollera externa konton i Adobe Campaign {#step-1--configure-or-check-the-external-accounts-in-adobe-campaign}

Först måste vi konfigurera eller kontrollera externa konton i Adobe Campaign enligt följande:

1. Klicka på ikonen **[!UICONTROL Explorer]**.
1. Gå till **[!UICONTROL Administration > Platform > External accounts]**. Adobe borde ha konfigurerat SFTP-kontona och du borde ha fått den information som behövs.

   * **[!UICONTROL importSharedAudience]**: konto som är dedikerat till att importera målgrupper.
   * **[!UICONTROL exportSharedAudience]**: konto som är dedikerat för att exportera målgrupper.

   ![](assets/aam_config_1.png)

1. Välj det **[!UICONTROL Export audiences to the Adobe Marketing Cloud]** externa kontot.

1. Välj **[!UICONTROL AWS S3]** i listrutan **[!UICONTROL Type]**.

1. Ange följande information:

   * **[!UICONTROL AWS S3 Account Server]**
URL-adressen till servern ska fyllas i enligt följande:

     ```
     <S3bucket name>.s3.amazonaws.com/<s3object path>
     ```

   * **[!UICONTROL AWS access key ID]**
Information om var du hittar ditt ID för AWS-åtkomstnyckel finns på [sidan ](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

   * **[!UICONTROL Secret access key to AWS]**
Om du vill veta var du hittar din hemliga åtkomstnyckel till AWS kan du läsa den här [sidan ](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/) .

   * **[!UICONTROL AWS Region]**
Mer information om AWS finns på [sidan ](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/) .

   ![](assets/aam_config_2.png)

1. Klicka på **[!UICONTROL Save]** och konfigurera det **[!UICONTROL Import audiences from the Adobe Marketing Cloud]** externa kontot så som beskrivs i föregående steg.

Dina externa konton har nu konfigurerats.

## Steg 2: Konfigurera Data Source {#step-2--configure-the-data-source}

**Mottagaren - besökar-ID** har skapats i Audience Manager. Detta är en användbar datakälla som konfigurerats som standard för besökar-ID. Segment som skapas från Campaign kommer att ingå i den här datakällan.

Så här konfigurerar du datakällan **[!UICONTROL Recipient - Visitor ID]**:

1. Välj **[!UICONTROL Administration > Platform > AMC Data sources]** från noden **[!UICONTROL Explorer]**.
1. Välj **[!UICONTROL Recipient - Visitor ID]**.
1. Ange **[!UICONTROL Data Source ID]** och **[!UICONTROL AAM Destination ID]** från Adobe.

   ![](assets/aam_config_3.png)

## Steg 3: Konfigurera kampanjspårningsserver {#step-3--configure-campaign-tracking-server}

För konfigurationen av integreringen med Audience Manager måste vi också konfigurera Campaign Tracking-servern.

Om du vill att delade målgrupper ska kunna fungera med besökar-ID, måste spårningsserverdomänen vara en underdomän till den klickade URL:en eller huvudwebbplatsen.

>[!IMPORTANT]
>
>Du måste kontrollera att Campaign Tracking Server är registrerad på domänen (CNAME). Mer information om domännamnsdelegering finns i [den här artikeln](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=sv).

## Steg 4: Konfigurera besökar-ID-tjänsten {#step-4--configure-the-visitor-id-service}

Om din besökar-ID-tjänst aldrig har konfigurerats på dina webbegenskaper eller webbplatser kan du läsa följande [dokument](https://experienceleague.adobe.com/docs/id-service/using/implementation/setup-aam-analytics.html?lang=sv-SE) om du vill veta mer om hur du konfigurerar tjänsten eller följande [video](https://helpx.adobe.com/marketing-cloud/how-to/email-marketing.html#step-two).

Synkronisera kundidentifierare med deklarerat ID med funktionen `setCustomerID` i Experience Cloud ID-tjänsten med integreringskoden: `AdobeCampaignID`. `AdobeCampaignID` ska matcha värdet för avstämningsnyckeln som angetts i Source-konfigurationen för mottagardata som konfigurerats i [Steg 2: Konfigurera datakällorna](#step-2--configure-the-data-sources).

Din konfiguration och etablering är färdiga, och integreringen kan nu användas för att importera och exportera målgrupper eller segment.
