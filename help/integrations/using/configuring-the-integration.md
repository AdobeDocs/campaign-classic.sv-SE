---
title: Konfigurera integrering med Adobe Experience Manager
description: Lär dig hur du konfigurerar Campaign-AEM-integrering
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 48acf8cbc52a54a2dd08f0b8f29be57d4e5e006f
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 2%

---


# Konfigurera integreringen{#configuring-the-integration}

## Configuring in Adobe Campaign {#configuring-in-adobe-campaign}

Om du vill använda dessa två lösningar tillsammans måste du konfigurera dem så att de ansluter till varandra.

Så här startar du konfigurationen i Adobe Campaign:

1. [Installera AEM integreringspaket i Adobe Campaign](#install-the-aem-integration-package-in-adobe-campaign)
1. [Konfigurera det externa kontot](#configure-the-external-account)
1. [Konfigurera AEM](#configure-aem-resources-filtering)

För avancerade konfigurationer som hantering av personaliseringsfält och -block. Läs Adobe Experience Manager- [dokumentationen](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html).

### Installera AEM integreringspaket i Adobe Campaign {#install-the-aem-integration-package-in-adobe-campaign}

Du måste först installera **[!UICONTROL AEM integration]** paketet.

1. I din Adobe Campaign-instans väljer du **[!UICONTROL Tools]** i det övre verktygsfältet.
1. Välj **[!UICONTROL Tools > Advanced > Import package...]**.

   ![](assets/aem_config_1.png)

1. Välj **[!UICONTROL Install a standard package]**.
1. Markera **[!UICONTROL AEM integration]** och klicka sedan på **[!UICONTROL Next]** knappen.

   ![](assets/aem_config_2.png)

1. I nästa fönster klickar du på **[!UICONTROL Start]** knappen för att starta installationen av paketet. Stäng fönstret när installationen är klar.

### Konfigurera säkerhetszonen för AEM {#configure-the-security-zone-for-aem-operator}

Paketet **[!UICONTROL AEM integration]** anger **[!UICONTROL aemserver]** operatorn i Campaign. Den här operatorn används för att ansluta Adobe Experience Manager-servern till Adobe Campaign.

Du måste konfigurera en säkerhetszon så att den här operatorn kan ansluta till Adobe Campaign via Adobe Experience Manager.

>[!CAUTION]
>
>Vi rekommenderar starkt att du skapar en säkerhetszon som är dedikerad till AEM för att undvika säkerhetsproblem. For more on this, refer to the Installation [guide](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Om din Campaign-instans hanteras av Adobe kontaktar du Adobe support. Om du använder Campaign lokalt följer du stegen nedan:

1. Öppna konfigurationsfilen **serverConf.xml** .
1. Få åtkomst till attributet **allowUserPassword** i den markerade säkerhetszonen och ange det till **true**.

   Detta gör att Adobe Experience Manager kan ansluta Adobe Campaign via inloggning/lösenord.

### Konfigurera det externa kontot {#configure-the-external-account}

Paketet skapade det externa kontot för Adobe Experience Cloud. **[!UICONTROL AEM integration]** Nu måste du konfigurera den för att ansluta till din Adobe Experience Manager-instans.

Följ stegen nedan för att konfigurera det AEM externa kontot:

1. Klicka på knappen **[!UICONTROL Explorer]**.

   ![](assets/aem_config_3.png)

1. Välj **[!UICONTROL Administration > Platform > External accounts]**.
1. From the **[!UICONTROL External account]** list, select **[!UICONTROL AEM instance]**.
1. Ange parametrarna för AEM:

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**

   >[!NOTE]
   >
   >Se till att din **[!UICONTROL Server]** adress inte avslutas med ett avslutande snedstreck.

   ![](assets/aem_config_4.png)

1. Markera **[!UICONTROL Enabled]** rutan.
1. Klicka på knappen **[!UICONTROL Save]**.

### Konfigurera AEM {#configure-aem-resources-filtering}

Alternativet **AEMResourceTypeFilter** används för att filtrera typer av Experience Manager-resurser som kan användas i Adobe Campaign. På så sätt kan Adobe Campaign hämta innehåll i Experience Manager som är särskilt utformat för att endast användas i Adobe Campaign.

Så här kontrollerar du om **[!UICONTROL AEMResourceTypeFilter]** alternativet är konfigurerat:

1. Klicka på knappen **[!UICONTROL Explorer]**.
1. Välj **[!UICONTROL Administration > Platform > Options]**.
1. From the **[!UICONTROL Options]** list, select **[!UICONTROL AEMResourceTypeFilter]**.
1. I **[!UICONTROL Value (text)]** fältet ska sökvägen vara följande:

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   Eller i vissa fall:

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## Konfigurera i Adobe Experience Manager {#configuring-in-adobe-experience-manager}

Så här startar du konfigurationen i Adobe Experience Manager:

1. Konfigurera **replikeringen** som ska replikeras från AEM till den AEM publiceringsinstansen.

   Mer information om hur du konfigurerar replikering finns i Adobe Experience Manager- [dokumentationen](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html).

1. Installera integreringen **FeaturePack** på redigeringsinstansen och replikera sedan installationen på publiceringsinstansen. (Endast för AEM version 5.6.1 och 6.0).

   Mer information om hur du installerar FeaturePack finns i Adobe Experience Manager- [dokumentationen](https://helpx.adobe.com/experience-manager/aem-previous-versions.html).

1. Anslut Adobe Experience Manager till Adobe Campaign genom att konfigurera en dedikerad **Cloud Service**.

   Om du vill veta hur du kopplar ihop båda lösningarna via Cloud Services kan du läsa Adobe Experience Manager- [dokumentationen](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) .

1. Konfigurera **tjänsten** Externalizer.

   Mer information om hur du konfigurerar den finns i Adobe Experience Manager- [dokumentationen](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html).

