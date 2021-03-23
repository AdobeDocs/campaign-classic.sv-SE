---
solution: Campaign Classic
product: campaign
title: Konfigurera Adobe I/O för utlösare i Adobe Experience Cloud
description: Lär dig hur du konfigurerar Adobe I/O för Adobe Experience Cloud Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b77a56a97e499f60c092fae45c7809f7bfd9f2ea
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 4%

---


# Konfigurera Adobe I/O för utlösare i Adobe Experience Cloud {#configuring-adobe-io}

>[!CAUTION]
>
>Om du använder en äldre version av utlösare-integrering via autentisering, **måste du gå till Adobe I/O enligt beskrivningen nedan**. Det gamla autentiseringsläget Autentisering med Campaign med Campaign kommer att upphöra den 30 november 2021. [Läs mer](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)
>
>Observera att under den här flyttningen till [!DNL Adobe I/O] kan vissa inkommande utlösare gå förlorade.

## Förutsättningar {#adobe-io-prerequisites}

Den här integreringen gäller endast från och med **Campaign Classic 20.3, 20.2.4, 19.1.8 och [!DNL Gold Standard] 11 versioner**.

Kontrollera att du har:

* en giltig **organisationsidentifierare**: organisationsidentifieraren för Identity Management System (IMS) är den unika identifieraren inom Adobe Experience Cloud, som används t.ex. för VisitorID-tjänsten och IMS Single-Sign On (SSO). [Läs mer](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)
* a **Developer access** to your Organization.  Om du behöver begära behörighet som systemadministratör för IMS-organisationen följer du proceduren [på den här sidan](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html) för att ge åtkomst till alla produktprofiler.

## Steg 1: Skapa/uppdatera Adobe I/O-projekt {#creating-adobe-io-project}

1. Åtkomst till [!DNL Adobe I/O] och inloggning med systemadministratörsbehörighet för IMS-organisationen.

   >[!NOTE]
   >
   > Se till att du är inloggad på rätt organisationsportal.

1. Extrahera befintlig integrationsklientidentifierare (klient-ID) från instanskonfigurationsfilen ims/authIMSTAClientId. Ett attribut som inte finns eller är tomt anger att klientidentifieraren inte har konfigurerats.

   >[!NOTE]
   >
   >Om din klientidentifierare är tom kan du direkt **[!UICONTROL Create a New project]** i Adobe I/O.

1. Identifiera det befintliga projektet med hjälp av den extraherade klientidentifieraren. Leta efter befintliga projekt med samma klientidentifierare som det som extraherades i föregående steg.

   ![](assets/do-not-localize/adobe_io_8.png)

1. Välj **[!UICONTROL + Add to Project]** och välj **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. I fönstret **[!UICONTROL Add an API]** väljer du **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. Välj **[!UICONTROL Service Account (JWT)]** som autentiseringstyp.

   ![](assets/do-not-localize/adobe_io_3.png)

1. Om ditt klient-ID var tomt väljer du **[!UICONTROL Generate a key pair]** för att skapa ett nyckelpar för offentlig och privat nyckel.

   Nycklarna laddas sedan ned automatiskt med ett standardutgångsdatum på 365 dagar. När det har gått ut måste du skapa ett nytt nyckelpar och uppdatera integreringen i konfigurationsfilen. Med alternativ 2 kan du välja att manuellt skapa och överföra din **[!UICONTROL Public key]** med ett längre förfallodatum.

   ![](assets/do-not-localize/adobe_io_4.png)

1. Klicka på **[!UICONTROL Next]**.

   ![](assets/do-not-localize/adobe_io_5.png)

1. Välj en befintlig **[!UICONTROL Product profile]** eller skapa en ny vid behov. Klicka sedan på **[!UICONTROL Save configured API]**.

   Mer information om [!DNL Analytics] **[!UICONTROL Product Profiles]** finns i [Adobe Analytics-dokumentation](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html#admin-console).

   ![](assets/do-not-localize/adobe_io_6.png)

1. Välj **[!UICONTROL Adobe Analytics]** i projektet och kopiera följande information under **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>Adobe I/O certifikat upphör att gälla efter 12 månader. Du måste generera ett nytt nyckelpar varje år.

## Steg 2: Lägg till projektautentiseringsuppgifterna i Adobe Campaign {#add-credentials-campaign}

Om du vill lägga till projektautentiseringsuppgifterna i Adobe Campaign kör du följande kommando som &quot;neolane&quot;-användare på alla behållare i Adobe Campaign-instansen för att infoga **[!UICONTROL Technical Account]**-autentiseringsuppgifterna i instanskonfigurationsfilen.

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
```

Den privata nyckeln ska kodas i base64 UTF-8-format. För att göra detta:

1. Använd den privata nyckeln som genererats i [steg 1: Skapa/uppdatera projektavsnittet för Adobe I/O](#creating-adobe-io-project). Den privata nyckeln måste vara samma som den som används för att skapa integreringen.

1. Koda den privata nyckeln med följande kommando: ```base64 ./private.key```.

   >[!NOTE]
   >
   >Extra rader kan ibland läggas till automatiskt när du kopierar/klistrar in den privata nyckeln. Kom ihåg att ta bort den innan du kodar din privata nyckel.

1. Använd den nyligen genererade privata nyckeln som är kodad i base64 UTF-8-format för att köra kommandot som beskrivs ovan.

## Steg 3: Uppdatera tagg för pipelines {#update-pipelined-tag}

Om du vill uppdatera taggen [!DNL pipelined] måste du uppdatera autentiseringstypen till Adobe I/O-projektet i konfigurationsfilen **config-&lt; instance-name >.xml** enligt följande:

```
<pipelined ... authType="imsJwtToken"  ... />
```
