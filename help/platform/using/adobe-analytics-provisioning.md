---
solution: Campaign Classic
product: campaign
title: Adobe Analytics Connector
description: Läs mer om Adobe Analytics Connector provisionering
feature: Overview
role: User, Admin
level: Beginner
source-git-commit: 5f596c14639e085edab9c08c2e3abba36e76acd3
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 5%

---

# Adobe Analytics Connector-etablering {#adobe-analytics-connector-provisioning}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
> Dessa åtgärder bör endast utföras av Hybrid- och On-Premise-implementeringar.
>
>Kontakta [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team för implementeringar hos värdtjänster.

Integrationen mellan Adobe Campaign Classic och Adobe Analytics autentisering stöder Adobe Identity Management Service (IMS). Du måste implementera Adobe IMS och ansluta till Campaign [via en Adobe ID](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/connect-to-campaign/connecting-via-an-adobe-id/about-adobe-id.html?lang=en) innan du startar implementeringen av Analytics Connector.

För att den här integreringen ska fungera måste du skapa en Adobe Analytics-produktprofil som används exklusivt för Analytics-kontakten. Sedan måste du skapa ett Adobe I/O-projekt.

## Skapa en Adobe Analytics-produktprofil {#analytics-product-profile}

Produktprofilen avgör vilken åtkomstnivå en användare har till dina olika Analytics-komponenter.

Om du redan har en Analytics-produktprofil bör du ändå skapa en ny Adobe Analytics-produktprofil som används exklusivt för Analytics-kontakten. Detta säkerställer att din produktprofil är inställd med rätt behörigheter för den här integreringen.

Mer information om produktprofiler finns i [Admin Console-dokumentationen](https://helpx.adobe.com/mt/enterprise/admin-guide.html).

1. På [Admin console](https://adminconsole.adobe.com/) väljer du din Adobe Analytics **[!UICONTROL Product]**.

   ![](assets/do-not-localize/triggers_1.png)

1. Klicka på **[!UICONTROL New Profile]**.

   ![](assets/do-not-localize/triggers_2.png)

1. Lägg till en **[!UICONTROL Product profile name]**, vi rekommenderar att du använder följande syntax: `reserved_campaign_classic_<Company Name>`. Klicka sedan på **[!UICONTROL Next]**.

   Denna **[!UICONTROL Product profile]** ska endast användas för Analytics Connector för att förhindra felkonfigurationsfel.

1. Öppna din nyskapade **[!UICONTROL Product profile]** och välj fliken **[!UICONTROL Permissions]**.

   ![](assets/do-not-localize/triggers_3.png)

1. Konfigurera de olika funktionerna genom att klicka på **[!UICONTROL Edit]** och markera de behörigheter som ska tilldelas till din **[!UICONTROL Product profile]** genom att klicka på plusikonen (+).

   Mer information om hur du hanterar behörigheter finns i [Admin Console-dokumentationen](https://helpx.adobe.com/mt/enterprise/using/manage-permissions-and-roles.html).

1. För **[!UICONTROL Report Suites]**-funktionen lägger du till **[!UICONTROL Report Suites]** som du behöver använda senare.

   Om du inte har några rapportsviter kan du skapa den enligt [de här stegen](../../platform/using/adobe-analytics-connector.md#report-suite-analytics).

   ![](assets/do-not-localize/triggers_4.png)

1. För **[!UICONTROL Metrics]**-funktionen lägger du till **[!UICONTROL Metrics]** som du måste konfigurera senare.

   Om det behövs kan du aktivera alternativet Inkludera automatiskt som lägger till alla behörighetsobjekt i den inkluderade listan och automatiskt lägger till nya behörighetsobjekt.

   ![](assets/do-not-localize/triggers_13.png)

1. För **[!UICONTROL Dimensions]**-funktionen lägger du till **[!UICONTROL Dimensions]** som du måste konfigurera senare.

1. Lägg till följande behörigheter för **[!UICONTROL Report Suite Tools]**-funktionen:

   * **[!UICONTROL Report suite Mgmt]**
   * **[!UICONTROL Conversion variables]**
   * **[!UICONTROL Success events]**
   * **[!UICONTROL Custom data Warehouse report]**
   * **[!UICONTROL Data sources manager]**
   * **[!UICONTROL Classifications]**

1. Lägg till följande behörigheter för **[!UICONTROL Analytics Tools]**-funktionen:

   * **[!UICONTROL Code Manager - Web services]**
   * **[!UICONTROL Logs - Web services]**
   * **[!UICONTROL Web services]**
   * **[!UICONTROL Web service access]**
   * **[!UICONTROL Calculated metric creation]**
   * **[!UICONTROL Segment creation]**

Din produktprofil är nu konfigurerad. Sedan måste du skapa projektet Adobe I/O.

## Skapa Adobe I/O-projekt {#create-adobe-io}

1. Öppna Adobe I/O och logga in som **systemadministratör** för IMS-organisationen.

   Mer information om administratörsroller finns på den här [sidan](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. Klicka på **[!UICONTROL Create a new project]**.

   ![](assets/do-not-localize/triggers_5.png)

1. Klicka på **[!UICONTROL Add to Project]** och välj **[!UICONTROL API]**.

   ![](assets/do-not-localize/triggers_6.png)

1. Markera [!DNL Adobe Analytics] och klicka på **[!UICONTROL Next]**.

   ![](assets/do-not-localize/triggers_7.png)

1. Välj **[!UICONTROL Service Account (JWT)]** som autentiseringstyp och klicka på **[!UICONTROL Next]**.

   ![](assets/do-not-localize/triggers_8.png)

1. Välj alternativet **[!UICONTROL Option 1: Generate a Key-Pair]** och klicka på **[!UICONTROL Generate a Key-Pair]**.

   Filen config.zip laddas sedan ned automatiskt.

   ![](assets/do-not-localize/triggers_9.png)

1. Klicka på **[!UICONTROL Next]**.

   ![](assets/do-not-localize/triggers_10.png)

1. Markera **[!UICONTROL Product profile]** som skapats i föregående steg som beskrivs i det här [avsnittet](#analytics-product-profile).

1. Klicka sedan på **[!UICONTROL Save Configured API]**.

   ![](assets/do-not-localize/triggers_11.png)

1. Välj [!DNL Adobe Analytics] i projektet och kopiera följande information under **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/triggers_12.png)

1. Klistra in dessa autentiseringsuppgifter för tjänstkontot på servern med följande kommando:

   ```
   nlserver config -instance:<instanceName> -setimsjwtauth::<ImsOrgId>/<ClientId>/<TechnicalAccountId>/<ClientSecret>/<$(base64 -w0 /path/to/private.key)>
   ```

Nu kan ni börja använda Analytics-kontakten och spåra kundbeteenden.
