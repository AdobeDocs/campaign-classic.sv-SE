---
product: campaign
title: Konfigurera Adobe Experience Manager-integrering
description: Lär dig hur du konfigurerar Campaign-AEM-integrering
audience: integrations
content-type: reference
exl-id: 54ee88b2-e646-4fb9-abec-957f0096f15f
source-git-commit: 6c23dadb5b6523e17e242de43a908ca86ed7cc23
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 3%

---

# Konfigurera integrering AEM Campaign{#configuring-the-integration}

![](../../assets/common.svg)

## Konfigurationssteg i Adobe Campaign {#configuring-in-adobe-campaign}

Om du vill använda dessa två lösningar tillsammans måste du konfigurera dem så att de ansluter till varandra.

Så här startar du konfigurationen i Adobe Campaign:

1. [Installera AEM integreringspaket i Adobe Campaign](#install-the-aem-integration-package-in-adobe-campaign)
1. [Konfigurera det externa kontot](#configure-the-external-account)
1. [Konfigurera AEM](#configure-aem-resources-filtering)

För avancerade konfigurationer som hantering av personaliseringsfält och -block. Se Adobe Experience Manager [dokumentation](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html).

### Installera AEM integreringspaket i Adobe Campaign {#install-the-aem-integration-package-in-adobe-campaign}

Du måste först installera **[!UICONTROL AEM integration]** paket.

1. I din Adobe Campaign-instans väljer du **[!UICONTROL Tools]** i det övre verktygsfältet.
1. Välj **[!UICONTROL Tools > Advanced > Import package...]**.

   ![](assets/aem_config_1.png)

1. Välj **[!UICONTROL Install a standard package]**.
1. Kontrollera **[!UICONTROL AEM integration]** klickar du på **[!UICONTROL Next]** -knappen.

   ![](assets/aem_config_2.png)

1. I nästa fönster klickar du på **[!UICONTROL Start]** för att starta installationen av paketet. Stäng fönstret när installationen är klar.

### Konfigurera säkerhetszonen för AEM {#configure-the-security-zone-for-aem-operator}

The **[!UICONTROL AEM integration]** paketet anger **[!UICONTROL aemserver]** -operator i Campaign. Den här operatorn används för att ansluta Adobe Experience Manager-servern till Adobe Campaign.

Du måste konfigurera en säkerhetszon så att den här operatorn kan ansluta till Adobe Campaign via Adobe Experience Manager.

>[!CAUTION]
>
>Vi rekommenderar starkt att du skapar en säkerhetszon som är dedikerad till AEM för att undvika säkerhetsproblem. Mer information finns i installationsprogrammet [guide](../../installation/using/security-zones.md).

Om din Campaign-instans hanteras av Adobe kontaktar du [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team. Om du använder Campaign lokalt följer du stegen nedan:

1. Öppna **serverConf.xml** konfigurationsfil.
1. Öppna **allowUserPassword** den markerade säkerhetszonens attribut och ange den som **true**.

   Detta gör att Adobe Experience Manager kan ansluta Adobe Campaign via inloggning/lösenord.

### Konfigurera det externa kontot {#configure-the-external-account}

The **[!UICONTROL AEM integration]** paketet skapade det externa kontot för Adobe Experience Cloud. Nu måste du konfigurera den för att ansluta till din Adobe Experience Manager-instans.

Så här konfigurerar du det AEM externa kontot:

1. Klicka på knappen **[!UICONTROL Explorer]**.

   ![](assets/aem_config_3.png)

1. Välj **[!UICONTROL Administration > Platform > External accounts]**.
1. Från **[!UICONTROL External account]** lista, välj **[!UICONTROL AEM instance]**.
1. Ange parametrarna för AEM:

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**

   >[!NOTE]
   >
   >Se till att **[!UICONTROL Server]** adressen avslutas inte med ett avslutande snedstreck.

   ![](assets/aem_config_4.png)

1. Kontrollera **[!UICONTROL Enabled]** box.
1. Klicka på knappen **[!UICONTROL Save]**.

### Konfigurera AEM {#configure-aem-resources-filtering}

The **AEMResourceTypeFilter** används för att filtrera olika typer av Experience Manager-resurser som kan användas i Adobe Campaign. På så sätt kan Adobe Campaign hämta innehåll i Experience Manager som är särskilt utformat för att endast användas i Adobe Campaign.

Om du vill kontrollera om **[!UICONTROL AEMResourceTypeFilter]** är konfigurerat:

1. Klicka på knappen **[!UICONTROL Explorer]**.
1. Välj **[!UICONTROL Administration > Platform > Options]**.
1. Från **[!UICONTROL Options]** lista, välj **[!UICONTROL AEMResourceTypeFilter]**.
1. I **[!UICONTROL Value (text)]** ska sökvägen vara följande:

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   Eller i vissa fall:

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## Konfigurationssteg i Adobe Experience Manager {#configuring-in-adobe-experience-manager}

Så här startar du konfigurationen i Adobe Experience Manager:

1. Konfigurera **replikering** för att replikera från AEM till den AEM publiceringsinstansen.

   Mer information om hur du konfigurerar replikering finns i Adobe Experience Manager [dokumentation](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html).

1. Installera integreringen **FeaturePack** replikera sedan installationen på publiceringsinstansen. (Endast för AEM version 5.6.1 och 6.0).

   Mer information om hur du installerar FeaturePack finns i Adobe Experience Manager [dokumentation](https://helpx.adobe.com/experience-manager/aem-previous-versions.html).

1. Anslut Adobe Experience Manager till Adobe Campaign genom att konfigurera en dedikerad **Cloud Service**.

   Om du vill veta hur du kopplar ihop båda lösningarna via Cloud Services kan du läsa Adobe Experience Manager [dokumentation](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) .

1. Konfigurera **Tjänsten Externalizer**.

   Läs mer om hur du konfigurerar den i Adobe Experience Manager [dokumentation](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html).
