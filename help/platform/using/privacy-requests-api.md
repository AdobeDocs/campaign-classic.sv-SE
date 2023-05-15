---
product: campaign
title: Automatisk process med förfrågan om användarens information
description: Läs om hur du konfigurerar en automatisk process för förfrågningar om användarens information
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: a93bac61-f615-4178-bc12-0f056e48687d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 100%

---

# Automatisk process med förfrågan om användarens information {#automatic-privacy-request-api}



Adobe Campaign tillhandahåller ett **API** som gör att du kan konfigurera en automatisk process för förfrågningar om användarens information.

Med API:et är den allmänna sekretessprocessen densamma som när du [använder gränssnittet](privacy-requests-ui.md). Den enda skillnaden är hur förfrågan om användarens information skapas. I stället för att skapa förfrågan i Adobe Campaign skickas en POST med förfrågningsinformationen till Campaign. För varje förfrågan läggs en ny post till på skärmen **[!UICONTROL Privacy Requests]**. De tekniska arbetsflödena för sekretess behandlar sedan förfrågan på samma sätt som en förfrågan som läggs till via gränssnittet.

Om du använder API:et för att skicka in förfrågningar om användarens information rekommenderar vi att du låter **tvåstegsprocessen** vara aktiverad för de första raderingsförfrågningarna för att testa returnerade data. När testerna är klara kan du inaktivera tvåstegsprocessen så att processen för raderingsförfrågan kan köras automatiskt.

JS-API:t **[!UICONTROL CreateRequestByName]** definieras så här.

>[!NOTE]
>
>Om du använde API:et **gdprRequest** kan du fortfarande använda det, men vi rekommenderar att du använder det nya API:et **privacyRequest**.

>[!IMPORTANT]
>
>Den namngivna behörigheten **[!UICONTROL Privacy Data Right]** krävs för att använda API:et.

```
<method library="nms:gdpr.js" name="CreateRequestByName" static="true">
 <help>Create a new GDPR Request using namespace internal name</help>
 <parameters>
  <param name="namespaceName" type="string" desc="Namespace internal name"/>
  <param name="reconciliationValue" type="string" desc="Reconciliation value"/>
  <param name="type" type="long" desc="Reconciliation value"/>
  <param name="confirmDeletePending" type="boolean" desc="Request confirm before deleting data"/>
  <param name="regulation" type="long" desc="regulation of newly created request"/>
  <param name="id" type="long" inout="out" desc="ID of newly created request"/>
 </parameters>
</method>
```

>[!NOTE]
>
>Fältet ”regulation” är bara tillgängligt om du använder Campaign Classic 20.2 (build 9178+).
>
>Om du migrerar till 20.2 och om du redan använde API:et måste du lägga till fältet ”regulation” enligt ovan. Om du använder en tidigare build kan du fortsätta att använda API:et utan fältet ”regulation”.

## Anropa API:et externt {#invoking-api-externally}

Här är ett exempel på hur du kan anropa API:et externt (specifikt autentisering via API:et och information om sekretess-API:et). Mer information om sekretess-API:et finns i [API-dokumentationen](https://experienceleague.adobe.com/developer/campaign-api/api/s-nms-privacyRequest.html?lang=sv). Du kan även läsa [dokumentationen om webbtjänstanrop](../../configuration/using/web-service-calls.md).

Först och främst måste du utföra autentiseringen via API:et:

1. Hämta WSDL för **xtk:session** via den här webbadressen: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=xtk:session**.

1. Använd metoden Logon och ange ett användarnamn och lösenord som parametrar i förfrågan. Du får ett svar som innehåller en sessionstoken. Här är ett exempel som använder SoapUI.

   ![](assets/do-not-localize/privacy-api.png)

1. Använd den returnerade sessionstoken som autentisering för alla efterföljande API-anrop. Den går ut efter 24 timmar.

Anropa sedan sekretess-API:et:

1. Hämta WSDL från den här URL:en: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=nms:privacyRequest**.

1. Använd **[!UICONTROL CreateRequestByName]** för att skapa en specifik förfrågan om användarens information.

   Här är ett exempel som använder **[!UICONTROL CreateRequestByName]**. Observera hur vi använder sessionstoken ovan som autentisering. Svaret är ID:et för den skapade förfrågan.

   ![](assets/do-not-localize/privacy-api-2.png)

   Om du vill ha hjälp med att utföra stegen ovan bör du tänka på följande:

   * Du kan använda ett **queryDef**-schema på **nms:gdprRequest**-schemat för att kontrollera statusen på åtkomstförfrågan.
   * Du kan använda ett **queryDef**-schema på **nms:gdprRequestData**-schemat för att få resultatet av åtkomstförfrågan.
   * Om du vill kunna hämta XML-filen från **&quot;$(serverUrl)&#39;/nms/gdpr.jssp?id=&#39;@id&quot;**, måste du vara inloggad och komma åt den från en IP-adress som ingår i tillåtelselistan. Detta gör du genom att skapa ett webbprogram som ger dig åtkomst till filen som genereras av JSSP.

## Anropa API:et med JS {#invoking-api-from-js}

Här är ett exempel på hur du kan anropa API:et med JS i Campaign Classic.

>[!NOTE]
>
>Fältet ”regulation” är bara tillgängligt om du använder Campaign Classic 20.2 (build 9178+).
>
>Om du migrerar till 20.2 och om du redan använde API:et måste du lägga till fältet ”regulation”. Om du använder en tidigare build kan du fortsätta att använda API:et utan fältet ”regulation”.

* Om du **använder en tidigare build (med GDPR-paket)** kan du fortsätta använda API:et utan fältet ”regulation” enligt nedan:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
   It requires 4 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // GDPR_REQUEST_TYPE_ACCESS = 1;
   // GDPR_REQUEST_TYPE_DELETE = 2;
   var requestType = GDPR_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* Om du **migrerar till 20.2** och om du redan använder API:et måste du lägga till fältet ”regulation” enligt nedan:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is mandatory parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* Om du använder **Campaign Classic 20.2 (build 9178+) eller senare** är fältet ”regulation” valfritt enligt nedan:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values 
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is optional parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```
