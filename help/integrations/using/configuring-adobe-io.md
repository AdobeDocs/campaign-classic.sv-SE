---
title: Konfigurera Adobe IO för Adobe Experience Cloud-utlösare
seo-title: Konfigurera Adobe IO för Adobe Experience Cloud-utlösare
description: Konfigurera Adobe IO för Adobe Experience Cloud-utlösare
seo-description: null
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
source-git-commit: d15e953740b0a4dd8073b36fd59b4c4e44906340
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---


# Konfigurera Adobe IO för Adobe Experience Cloud-utlösare {#configuring-adobe-io}

Nödvändiga konfigurationer är:

* Adobe Campaign Classic bygger ACC-19.1.9 eller ACC-20.2.1 och senare.
* ett giltigt IMSOrgID.
* en utvecklare har tillgång till IMS-organisationen. Du måste begära behörighet som systemadministratör för IMS-organisationen för att följa proceduren som beskrivs på den här [sidan](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) för att ge åtkomst till alla produktprofiler.

## Steg 1: Skapa/uppdatera Adobe IO-projekt {#creating-adobe-io-project}

1. Gå till Adobe IO och logga in med systemadministratörsbehörighet för IMSorg.

   >[!NOTE]
   >
   > Kontrollera att du är inloggad på rätt IMSorg-portal.

1. Extrahera befintligt integrationsklient-ID från instanskonfigurationsfilen ims/authIMSTAClientId. Ett attribut som inte finns eller är tomt anger att klient-ID inte har konfigurerats.

   >[!NOTE]
   >
   >Om ditt klient-ID är tomt kan du göra det direkt **[!UICONTROL Create a New project]** i Adobe IO.

1. Du måste nu identifiera det befintliga projektet med det extraherade klient-ID:t. Sök efter befintliga projekt med samma klient-ID som det som extraherades i föregående steg.

   ![](assets/adobe_io_8.png)

1. Markera **[!UICONTROL + Add to Project]** och välj **[!UICONTROL API]**.

   ![](assets/adobe_io_1.png)

1. I fönstret **[!UICONTROL Add an API]** väljer du **[!UICONTROL Adobe Analytics]**.

   ![](assets/adobe_io_2.png)

1. Välj **[!UICONTROL Service Account (JWT)]** som autentiseringstyp.

   ![](assets/adobe_io_3.png)

1. Om du inte har angett något klient-ID väljer du **[!UICONTROL Generate a key pair]** att skapa ett offentligt och privat nyckelpar.

   ![](assets/adobe_io_4.png)

1. Ladda upp din offentliga nyckel och klicka **[!UICONTROL Next]**.

   ![](assets/adobe_io_5.png)

1. Välj produktprofilen **Analytics-&lt; Org Name >** och klicka på **[!UICONTROL Save configured API]**.

   ![](assets/adobe_io_6.png)

1. Välj **[!UICONTROL Service Account (JWT)]** och kopiera följande information från projektet:
   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/adobe_io_7.png)

## Steg 2: Lägg till projektautentiseringsuppgifter i Adobe Campaign {#add-credentials-campaign}

Om du vill lägga till projektautentiseringsuppgifterna i Adobe Campaign kör du följande kommando som neolane-användare på alla behållare i Adobe Campaign-instansen för att infoga autentiseringsuppgifterna i **[!UICONTROL Technical Account]** instanskonfigurationsfilen.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>Du bör koda den privata nyckeln i base64 UTF-8-format. Kom ihåg att ta bort den nya raden från nyckeln innan du kodar den, förutom den privata nyckeln. Den privata nyckeln måste vara densamma som användes för att skapa integreringen.

## Steg 3: Uppdatera tagg för pipeline {#update-pipelined-tag}

Om du vill uppdatera [!DNL pipelined] taggen måste du uppdatera autentiseringstypen till Adobe IO-projektet i konfigurationsfilen **config-&lt; instance-name >.xml** enligt följande:

```
<pipelined ... authType="imsJwtToken"  ... />
```

>[!NOTE]
>
>Om du använder den äldre versionen av Triggers Integration med äldre JWT-tokens bör du också lägga till Adobe IO-API:t, som beskrivs i det första steget, för att automatiskt migrera till den nya utlösarautentiseringen. [!DNL Adobe Analytics]
