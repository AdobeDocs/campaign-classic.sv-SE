---
solution: Campaign Classic
product: campaign
title: Konfigurera Adobe I/O för utlösare i Adobe Experience Cloud
description: Lär dig konfigurera Adobe I/O för Adobe Experience Cloud-utlösare
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 57093a687534ed1e7f77738ca233d4cc86cf40cf
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 5%

---


# Konfigurera Adobe I/O för utlösare i Adobe Experience Cloud {#configuring-adobe-io}

>[!CAUTION]
>
>Om du använder en äldre version av integreringen av utlösare via autentisering, **måste du flytta till Adobe I/O enligt beskrivningen nedan**. Det äldre autentiseringsläget för autentisering kommer att upphöra den 30 april 2021. [Läs mer](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)

## Förutsättningar {#adobe-io-prerequisites}

Den här integreringen gäller endast från och med **Campaign Classic 20.3- och Gold Standard 11-utgåvorna**.

Kontrollera att du har:

* en giltig **organisationsidentifierare**: organisationsidentifieraren för Identity Management System (IMS) är den unika identifieraren inom Adobe Experience Cloud, som används t.ex. för VisitorID-tjänsten och IMS Single-Sign On (SSO). [Läs mer](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)
* a **Developer access** to your Organization.  Om du behöver begära behörighet som systemadministratör för IMS-organisationen följer du proceduren [på den här sidan](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html) för att ge åtkomst till alla produktprofiler.
>
## Steg 1: Skapa/uppdatera Adobe I/O Project {#creating-adobe-io-project}

1. Öppna Adobe I/O och logga in med systemadministratörsbehörighet för IMS-organisationen.

   >[!NOTE]
   >
   > Se till att du är inloggad på rätt organisationsportal.

1. Extrahera befintligt integrationsklient-ID från instanskonfigurationsfilen ims/authIMSTAClientId. Ett attribut som inte finns eller är tomt anger att klientidentifieraren inte har konfigurerats.

   >[!NOTE]
   >
   >Om klientidentifieraren är tom kan du direkt **[!UICONTROL Create a New project]** i Adobe I/O.

1. Identifiera det befintliga projektet med hjälp av den extraherade klientidentifieraren. Leta efter befintliga projekt med samma klientidentifierare som det som extraherades i föregående steg.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Välj **[!UICONTROL + Add to Project]** och välj **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. I fönstret **[!UICONTROL Add an API]** väljer du **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Välj **[!UICONTROL Service Account (JWT)]** som autentiseringstyp.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Om ditt klient-ID var tomt väljer du **[!UICONTROL Generate a key pair]** för att skapa ett offentligt och privat nyckelpar.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Ladda upp din offentliga nyckel och klicka på **[!UICONTROL Next]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Välj produktprofilen **Analytics-&lt; Org Name >** och klicka på **[!UICONTROL Save configured API]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. Välj **[!UICONTROL Service Account (JWT)]** i projektet och kopiera följande information:
   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

## Steg 2: Lägg till projektautentiseringsuppgifterna i Adobe Campaign {#add-credentials-campaign}

Om du vill lägga till projektautentiseringsuppgifterna i Adobe Campaign kör du följande kommando som &quot;neolane&quot;-användare på alla behållare i Adobe Campaign-instansen för att infoga **[!UICONTROL Technical Account]**-autentiseringsuppgifterna i instanskonfigurationsfilen.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Du bör koda den privata nyckeln i base64 UTF-8-format. Kom ihåg att ta bort den nya raden från nyckeln innan du kodar den, förutom den privata nyckeln. Den privata nyckeln måste vara densamma som användes för att skapa integreringen.

## Steg 3: Uppdatera tagg för pipelines {#update-pipelined-tag}

Om du vill uppdatera taggen [!DNL pipelined] måste du uppdatera autentiseringstypen till Adobe I/O-projektet i konfigurationsfilen **config-&lt; instance-name >.xml** enligt följande:

```
<pipelined ... authType="imsJwtToken"  ... />
```
