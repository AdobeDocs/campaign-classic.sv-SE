---
title: Konfigurera Adobe I/O för Adobe Experience Cloud-utlösare
description: Lär dig hur du konfigurerar Adobe I/O för Adobe Experience Cloud-utlösare
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8486213403bf848f1632aff06f3f1528b199f86d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 2%

---


# Configuring Adobe I/O for Adobe Experience Cloud Triggers {#configuring-adobe-io}

>[!CAUTION]
>
>Om du använder en äldre version av integreringen av utlösare via autentisering måste **du gå till Adobe I/O enligt beskrivningen nedan**. Det äldre autentiseringsläget för autentisering kommer att upphöra den 30 april 2021. [Läs mer](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md)

## Förutsättningar {#adobe-io-prerequisites}

Kontrollera att du har:

* en ny version av Adobe Campaign (20.2.1 och senare),
* ett giltigt IMSOrgID: Organisationsidentifieraren för Identity Management System (IMS) är den unika identifieraren inom Adobe Experience Cloud, som används t.ex. för VisitorID-tjänsten och IMS Single-Sign On (SSO).
* en utvecklare har tillgång till IMS-organisationen.

>[!NOTE]
>
>Om du behöver begära behörighet som systemadministratör för IMS-organisationen följer du anvisningarna [på den här sidan](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) för att ge åtkomst till alla produktprofiler.


## Steg 1: Skapa/uppdatera Adobe I/O-projekt {#creating-adobe-io-project}

1. Gå till Adobe I/O och logga in med systemadministratörsbehörighet för IMSorg.

   >[!NOTE]
   >
   > Kontrollera att du är inloggad på rätt IMSorg-portal.

1. Extrahera befintligt integrationsklient-ID från instanskonfigurationsfilen ims/authIMSTAClientId. Ett attribut som inte finns eller är tomt anger att klient-ID inte har konfigurerats.

   >[!NOTE]
   >
   >Om ditt klient-ID är tomt kan du göra det direkt **[!UICONTROL Create a New project]** i Adobe.

1. Identifiera det befintliga projektet med hjälp av det extraherade klient-ID:t. Sök efter befintliga projekt med samma klient-ID som det som extraherades i föregående steg.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Markera **[!UICONTROL + Add to Project]** och välj **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. In the **[!UICONTROL Add an API]** window, select **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Välj **[!UICONTROL Service Account (JWT)]** som autentiseringstyp.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Om ditt klient-ID var tomt väljer du **[!UICONTROL Generate a key pair]** att skapa ett offentligt och privat nyckelpar.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Ladda upp din offentliga nyckel och klicka **[!UICONTROL Next]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Välj produktprofilen **Analytics-&lt; Org Name >** och klicka på **[!UICONTROL Save configured API]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. Välj **[!UICONTROL Service Account (JWT)]** och kopiera följande information från projektet:
   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

## Steg 2: Lägg till projektautentiseringsuppgifter i Adobe Campaign {#add-credentials-campaign}

Om du vill lägga till projektautentiseringsuppgifterna i Adobe Campaign kör du följande kommando som &quot;neolane&quot;-användare på alla behållare i Adobe Campaign-instansen för att infoga autentiseringsuppgifterna i **[!UICONTROL Technical Account]** instanskonfigurationsfilen.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Du bör koda den privata nyckeln i base64 UTF-8-format. Kom ihåg att ta bort den nya raden från nyckeln innan du kodar den, förutom den privata nyckeln. Den privata nyckeln måste vara densamma som användes för att skapa integreringen.

## Steg 3: Uppdatera tagg för pipeline {#update-pipelined-tag}

Om du vill uppdatera [!DNL pipelined] taggen måste du uppdatera autentiseringstypen till Adobe I/O-projektet i konfigurationsfilen **config-&lt; instance-name >.xml** enligt följande:

```
<pipelined ... authType="imsJwtToken"  ... />
```
