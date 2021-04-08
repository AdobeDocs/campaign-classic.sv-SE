---
solution: Campaign Classic
product: campaign
title: Förfrågningar om användarens information
description: Lär dig hur du hanterar sekretessförfrågningar
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: c7688c2a-f0a7-4c51-a4cf-bf96fe8bf9b6
translation-type: tm+mt
source-git-commit: 5b1c4426a0d59861aa61a7e53154b9adfda31d71
workflow-type: tm+mt
source-wordcount: '2415'
ht-degree: 21%

---

# Hantera sekretessbegäranden {#privacy-requests}

Se [det här avsnittet](../../platform/using/privacy-management.md) för en allmän presentation om sekretesshantering.

Denna information gäller för GDPR, CCPA, PDPA och LGPD. Se [det här avsnittet](../../platform/using/privacy-management.md#privacy-management-regulations) för mer information om dessa regelverk.

[Det här avsnittet](#sale-of-personal-information-ccpa) förklarar avanmälan till försäljning av personuppgifter vilken är specifik för CCPA.

<!--Installation procedures described in this document are applicable starting Campaign Classic 18.4 (build 8931+). If you are running on a previous version, refer to this [technote](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html).-->

## Om sekretessförfrågningar {#about-privacy-requests}

För att underlätta beredskapen gällande din integritet kan du hantera förfrågningar om åtkomst och borttagning med Adobe Campaign. **Det här avsnittet** beskriver **åtkomsträttigheter** och [rätten att glömmas](../../platform/using/privacy-management.md#right-access-forgotten) (borttagningsbegäran).

Låt oss se hur du kan skapa förfrågningar om åtkomst och borttagning, samt hur de behandlas i Adobe Campaign.

### Principer {#principles}

Adobe Campaign erbjuder datakontroller två möjligheter att utföra förfrågningar om sekretessåtkomst och -borttagning:

* Via **Adobe Campaign-gränssnittet**: för varje sekretessförfrågan skapar Data Controller en ny sekretessförfrågan i Adobe Campaign. Se [det här avsnittet](#create-privacy-request-ui).
* Via **API**: Adobe Campaign tillhandahåller ett API som tillåter automatisk behandling av sekretessförfrågningar med SOAP. Se [det här avsnittet](#automatic-privacy-request-api).

>[!NOTE]
>
>Mer information om personuppgifter och de olika enheter som hanterar data (personuppgiftsansvarig, personuppgiftsbiträde och registrerad) finns i [Personuppgifter och personer](../../platform/using/privacy-and-recommendations.md#personal-data).

### Förutsättningar {#prerequesites}

Adobe Campaign erbjuder verktyg för personuppgiftsansvarig som låter dig skapa och bearbeta förfrågningar om användarens information gällande data som lagras i Adobe Campaign. Det är dock den personuppgiftsansvariges ansvar att hantera relationen med den registrerade (e-post, kundtjänst eller en webbportal).

Det är därför ditt ansvar som personuppgiftsansvarig att bekräfta identiteten på den registrerade som gör förfrågan och bekräfta att de uppgifter som skickas tillbaka till den som utförde förfrågan avser den registrerade.

### Installera sekretesspaketet {#install-privacy-package}

Om du vill använda den här funktionen måste du installera **[!UICONTROL Privacy Data Protection Regulation]**-paketet via **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** > **[!UICONTROL Adobe Campaign Package]**-menyn. Mer information om hur du installerar paket finns i [den detaljerade dokumentationen](../../installation/using/installing-campaign-standard-packages.md).

Två nya mappar, som är specifika för sekretess, skapas under **[!UICONTROL Administration]** > **[!UICONTROL Platform]**:

* **[!UICONTROL Privacy Requests]**: Här skapar du dina förfrågningar om sekretess och följer deras utveckling.
* **[!UICONTROL Namespaces]**: Här definierar du vilket fält som ska användas för att identifiera den registrerade i Adobe Campaign-databasen.

![](assets/privacy-folders.png)

I **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** körs tre tekniska arbetsflöden varje dag för att behandla sekretessförfrågningar.

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**: det här arbetsflödet genererar mottagarens data som lagras i Adobe Campaign och gör dem tillgängliga för hämtning på skärmen för sekretesspolicy.
* **[!UICONTROL Delete privacy requests data]**: det här arbetsflödet tar bort mottagarens data som lagras i Adobe Campaign.
* **[!UICONTROL Privacy request cleanup]**: Med det här arbetsflödet raderas de filer för åtkomstbegäran som är äldre än 90 dagar.

I **[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]** har den namngivna rättigheten **[!UICONTROL Privacy Data Right]** lagts till. Den här namngivna rättigheten krävs för Data Controllers för att de ska kunna använda sekretessverktyg. På så sätt kan de skapa nya förfrågningar, spåra deras utveckling, använda API:t osv.

![](assets/privacy-right.png)

### Namnrymder {#namesspaces}

Innan du skapar förfrågningar om användarens information måste du definiera den namnrymd som ska användas. Detta är nyckeln som kommer att användas för att identifiera den registrerade i Adobe Campaign-databasen.

Tre namnutrymmen är tillgängliga direkt: e-post, telefon och mobiltelefon. Om du behöver ett annat namnutrymme (till exempel ett anpassat mottagarfält) kan du skapa ett nytt från **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**.

## Skapa en förfrågan om användarens information {#create-privacy-request-ui}

Med **Adobe Campaign-gränssnittet** kan du skapa dina sekretessförfrågningar och spåra deras utveckling. Följ dessa anvisningar för att skapa en ny sekretessförfrågan:

1. Gå till mappen Privacy request under **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Privacy Requests]**.

   ![](assets/privacy-requests-folder.png)

1. På den här skärmen kan du visa alla aktuella sekretessförfrågningar, deras status och loggar. Klicka på **[!UICONTROL New]** för att skapa en sekretessförfrågan.

   ![](assets/privacy-request-new.png)

1. Markera **[!UICONTROL Regulation]** (GDPR, CCPA, PDPA eller LGPD), **[!UICONTROL Request type]** (Access eller Delete), välj en **[!UICONTROL Namespace]** och ange **[!UICONTROL Reconciliation value]**. Om du använder e-post som namnutrymme skriver du den registrerades e-postadress.

   ![](assets/privacy-request-properties.png)

De tekniska arbetsflödena för sekretess körs en gång om dagen och varje ny begäran behandlas:

* Ta bort begäran: mottagarens data som lagras i Adobe Campaign raderas.
* Åtkomstbegäranden: mottagarens data som lagras i Adobe Campaign genereras och görs tillgängliga som en XML-fil till vänster på skärmen.

![](assets/privacy-request-download.png)

### Lista över tabeller {#list-of-tables}

När Adobe Campaign utför en begäran om att ta bort eller få åtkomst till sekretess söker igenom alla den registrerade personens data baserat på **[!UICONTROL Reconciliation value]** i alla tabeller som har en länk till mottagartabellen (egen typ).

Här är en lista över färdiga tabeller som beaktas vid sekretessförfrågningar:

* Mottagare (mottagare)
* Mottagarens leveranslogg (wideLogRcp)
* Logg för mottagarspårning (trackingLogRcp)
* Arkiverad händelselogg (broadLogEventHistory)
* Innehåll i mottagarlista (rcpGrpRel)
* Erbjudandeförslag för besökare (propositionVisitor)
* Besökare (besökare)
* Prenumerationshistorik (subHistory)
* Prenumerationer (prenumeration)
* Erbjudandeförslag för mottagare (propositionRcp)

Om du har skapat anpassade tabeller som har en länk till mottagartabellen (egen typ), kommer de också att tas med i beräkningen. Om du t.ex. har ett transaktionsregister länkat till mottagarregistret och en transaktionsdetaljtabell länkad till transaktionsregistret, kommer båda att beaktas.

>[!IMPORTANT]
>
>Om du utför sekretessbatchbegäranden med arbetsflöden för profilborttagning bör du tänka på följande:
>* Borttagning av profiler via arbetsflöden bearbetar inte underordnade tabeller.
>* Du måste hantera borttagningen för alla underordnade tabeller.
>* Adobe rekommenderar att du skapar ett ETL-arbetsflöde som lägger till de rader som ska tas bort i tabellen för sekretessåtkomst och låter arbetsflödet **[!UICONTROL Delete privacy requests data]** utföra borttagningen. Vi rekommenderar att du av prestandaskäl begränsar till 200 profiler per dag att ta bort.


### Status gällande förfrågningar om användarens information {#privacy-request-statuses}

Här följer de olika statusarna gällande förfrågningar om användarens information:

* **[!UICONTROL New]**/**[!UICONTROL Retry pending]**: arbetsflödet har inte bearbetat förfrågan ännu.
* **[!UICONTROL Processing]**/**[!UICONTROL Retry in progress]**: arbetsflödet bearbetar förfrågan.
* **[!UICONTROL Delete pending]**: arbetsflödet har identifierat alla mottagardata för borttagning.
* **[!UICONTROL Delete in progress]**: arbetsflödet bearbetar borttagningen.
* **[!UICONTROL Delete Confirmation Pending]** (Ta bort begäran i processläge i två steg): arbetsflödet har bearbetat åtkomstbegäran. Manuell bekräftelse krävs för att utföra borttagningen. Knappen är tillgänglig i 15 dagar.
* **[!UICONTROL Complete]**: behandlingen av förfrågan har slutförts utan fel.
* **[!UICONTROL Error]**: arbetsflödet har påträffat ett fel. Orsaken visas i listan över sekretessbegäranden i kolumnen **[!UICONTROL Request status]**. Till exempel innebär **[!UICONTROL Error data not found]** att inga mottagardata som matchar den registrerades **[!UICONTROL Reconciliation value]** har hittats i databasen.

### 2-stegsprocess {#two-step-process}

Som standard är **tvåstegsprocessen** aktiverad. När du skapar en ny Delete-begäran i det här läget utförs alltid en Access-begäran först i Adobe Campaign. På så sätt kan du kontrollera data innan du bekräftar borttagningen.

Du kan ändra det här läget från skärmen för utgåva av sekretessförfrågningar. Klicka på **[!UICONTROL Advanced settings]**.

![](assets/privacy-request-advanced-settings.png)

När tvåstegsläget är aktiverat ändras statusen för en ny Delete-begäran till **[!UICONTROL Confirm Delete Pending]**. Hämta den genererade XML-filen från skärmen för sekretessförfrågningar och kontrollera data. Bekräfta att du vill radera data genom att klicka på knappen **[!UICONTROL Confirm delete data]**.

![](assets/privacy-request-delete-data.png)

### JSSP-URL {#jspp-url}

När Access-begäranden behandlas genererar Adobe Campaign en JSSP som hämtar mottagarens data från databasen och exporterar dem till en XML-fil som lagras på den lokala datorn. JSSP-URL:en definieras så här:

```
"$(serverUrl)+'/nms/gdpr.jssp?id='+@id"
```

där @id är ID för sekretesspolicy.

Den här URL:en lagras i fältet **[!UICONTROL "File location" (@urlFile)]** i schemat **[!UICONTROL Privacy Requests (gdprRequest)]**.

Informationen är tillgänglig i databasen i 90 dagar. När begäran har rensats bort av det tekniska arbetsflödet tas informationen bort från databasen och URL:en blir inaktuell. Kontrollera att URL:en fortfarande är giltig innan du hämtar data från en webbsida.

Här är ett exempel på en registrerade persons datafil:

![](assets/privacy-access-file.png)

Datakontrollanter kan enkelt skapa ett webbprogram med motsvarande JSSP-URL för att göra den registrerade personens datafil tillgänglig från en webbsida.

![](assets/privacy-gdpr-jssp.png)

Här är ett kodfragment som du kan använda som exempel i webbprogramaktiviteten **[!UICONTROL Page]**.

![](assets/privacy-page-activity.png)

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head> <meta http-equiv="Content-Language" content="en"> <meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> <link rel="stylesheet" type="text/css" href="/nl/webForms/landingPage.css"/> <title>Clickthrough</title> <style type="text/css" media="all"> /* override formulary area */ .formulary { top: 200px; position: absolute; left: 0; } </style> </head> <body style="" class="">
<center>
<div id="wrap">
<div id="header"><img class="nlui-widget" alt="placeholder_header" src="/nms/img/contentModels/placeholder_header.png" unselectable="on" />
<div class="header-title center-title">DOWNLOAD GDPR DATA</div>
<div class="formulary center-formulary"><form>
<div class="button large-button"><a href=[SERVER_URL]/nms/gdpr.jssp?id=13000" data-nl-type="externalLink">CLICK TO DOWNLOAD</a></div>
</form></div>
</div>
<div id="content">
<div class="row">
<div class="info">
<div class="desc">
<div class="title">EFFICIENCY</div>
<div class="desc">Our service is guaranteed to improve your efficiency. Increase performance and use our high-technology service to implement even the most ambitious of projects.</div>
</div>
</div>
</div>
</div>
<div id="footer">
<div style="text-align: center;">
<div style="float: left;"><a href="#">Contact us</a></div>
<div style="float: right;">&copy; Copyrights</div>
<div><a href="#"><img title="facebook" class="nlui-widget" alt="facebook" src="/xtk/img/facebook.png" unselectable="on" /></a> <a href="#"><img title="Twitter" class="nlui-widget" alt="twitter" src="/xtk/img/twitter.png" unselectable="on" /></a> <a href="#"><img title="Google" class="nlui-widget" alt="google_plus" src="/xtk/img/google_plus.png" unselectable="on" /></a> <a href="#"><img title="Linkedin" class="nlui-widget" alt="Linkedin" src="/xtk/img/linkedin.png" unselectable="on" /></a></div>
</div>
</div>
</div>
</center>
</body> </html>
```

Eftersom åtkomsten till den registrerade personens datafil är begränsad måste webbsidans anonyma åtkomst inaktiveras. Det är bara operatorn med namngiven **[!UICONTROL Privacy Data Right]**-behörighet som kan logga in på sidan och hämta data.

## Automatisk process för begäran om sekretess {#automatic-privacy-request-api}

Adobe Campaign tillhandahåller ett **API** som gör att du kan konfigurera en automatisk process för sekretessförfrågningar.

Med API:t är den allmänna sekretessprocessen densamma som [när du använder gränssnittet](#create-privacy-request-ui). Den enda skillnaden är att begäran om sekretess har skapats. I stället för att skapa begäran i Adobe Campaign skickas en POST med begärandeinformationen till Campaign. För varje begäran läggs en ny post till på skärmen **[!UICONTROL Privacy Requests]**. De tekniska arbetsflödena för integritetsskydd behandlar sedan begäran på samma sätt som en begäran som läggs till via gränssnittet.

Om du använder API:t för att skicka in sekretessförfrågningar rekommenderar vi att du låter den **tvåstegsprocess** som är aktiverad för de första Delete-förfrågningarna vara kvar för att testa returnerade data. När testerna är klara kan du inaktivera tvåstegsprocessen så att processen för borttagningsbegäran kan köras automatiskt.

JS-API:t **[!UICONTROL CreateRequestByName]** definieras så här.

>[!NOTE]
>
>Om du använde API:t **gdprRequest** kan du fortfarande använda det, men vi rekommenderar att du använder det nya API:t **privacyRequest**.

>[!IMPORTANT]
>
>Den namngivna **[!UICONTROL Privacy Data Right]**-rättigheten krävs för att använda API:t.

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
>Fältet&quot;Reglering&quot; är bara tillgängligt om du använder Campaign Classic 20.2 (build 9178+).
>
>Om du migrerar till 20.2 och om du redan använde API:t måste du lägga till fältet&quot;Regel&quot; enligt ovan. Om du använder en tidigare version kan du fortsätta att använda API:t utan fältet för regler.

### Anropa API:t externt {#invoking-api-externally}

Här är ett exempel på hur du kan anropa API:t externt (autentisering via API:t och information om API:t för sekretess specifikt). Mer information om sekretess-API:t finns i [API-dokumentationen](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/s-nms-privacyRequest.html). Du kan även läsa [dokumentationen för webbtjänstanrop](../../configuration/using/web-service-calls.md).

Först och främst måste du utföra autentiseringen via API:

1. Hämta WSDL för **xtk:session** via den här webbadressen: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=xtk:session**.

1. Använd metoden &quot;Logon&quot; och ange ett användarnamn och lösenord som parametrar i begäran. Du får ett svar som innehåller en sessionstoken. Här är ett exempel som använder SoapUI.

   ![](assets/privacy-api.png)

1. Använd den returnerade sessionstoken som autentisering för alla efterföljande API-anrop. Den går ut efter 24 timmar.

Anropa sedan sekretess-API:

1. Hämta WSDL från den här URL:en: **`<server url>`/nl/jsp/schemawsdl.jsp?schema=nms:privacyRequest**.

1. Använd **[!UICONTROL CreateRequestByName]** för att skapa en specifik sekretessförfrågan.

   Här är ett exempel med **[!UICONTROL CreateRequestByName]**. Observera hur vi använder sessionstoken ovan som autentisering. Svaret är ID:t för den skapade begäran.

   ![](assets/privacy-api-2.png)

   Om du vill ha hjälp med att utföra stegen ovan bör du tänka på följande:

   * Du kan använda ett **queryDef**-schema på **nms:gdprRequest**-schemat för att kontrollera status för åtkomstbegäran.
   * Du kan använda ett **queryDef**-schema på **nms:gdprRequestData**-schemat för att få resultatet av åtkomstbegäran.
   * Om du vill kunna hämta XML-filen från **&quot;$(serverUrl)&#39;/nms/gdpr.jssp?id=&#39;@id&quot;**, måste du vara inloggad och komma åt den från en vitlistad IP. Det gör du genom att skapa ett webbprogram som ger dig åtkomst till filen som genereras av JSSP.

### Anropa API:t från en JS {#invoking-api-from-js}

Här är ett exempel på hur du kan anropa API:t från en JS i Campaign Classic.

>[!NOTE]
>
>Fältet&quot;Reglering&quot; är bara tillgängligt om du använder Campaign Classic 20.2 (build 9178+).
>
>Om du migrerar till 20.2 och om du redan använde API:t måste du lägga till fältet&quot;Regel&quot;. Om du använder en tidigare version kan du fortsätta att använda API:t utan fältet för regler.

* Om du **använder en tidigare version (med GDPR-paket)** kan du fortsätta använda API:t utan fältet&quot;regler&quot; enligt nedan:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privay request on the DB.
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

* Om du **migrerar till 20.2** och om du redan använder API:t, måste du lägga till fältet för regler enligt nedan:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privay request on the DB.
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

* Om du använder **Campaign Classic 20.2 (build 9178+) eller senare** är fältet &#39;Regulation&#39; valfritt, vilket visas nedan:

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privay request on the DB.
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

## Avanmäl dig till försäljning av personuppgifter (CCPA) {#sale-of-personal-information-ccpa}

**CCPA (California Consumer Privacy Act)** ger personer bosatta i Kalifornien nya rättigheter när det gäller deras personuppgifter och ålägger vissa företag som bedriver verksamhet i Kalifornien skyldigheter när det gäller uppgiftsskydd.

Konfigurationen och användningen av förfrågningar gällande åtkomst och borttagning är gemensamma för både GDPR och CCPA. Det här avsnittet presenterar avanmälan för försäljning av personuppgifter vilken är specifik för CCPA.

Förutom verktygen [Samtyckeshantering](../../platform/using/privacy-management.md#consent-management) som tillhandahålls av Adobe Campaign kan du spåra om en konsument har valt att sälja personuppgifter.

En konsument bestämmer genom ert system att denne inte tillåter att sina personuppgifter säljs till tredje part. I Adobe Campaign kan du lagra och spåra den här informationen.

För att detta ska fungera måste du utöka profiltabellen och lägga till ett **[!UICONTROL Opt-Out for CCPA]**-fält.

>[!IMPORTANT]
>
>Det är ditt ansvar som personuppgiftsansvarig att ta emot den registrerades förfrågan och att hålla reda på förfrågningsdatum för CCPA. Som teknikleverantör erbjuder vi bara ett sätt att avanmäla sig. Mer information om din roll som personuppgiftsansvarig finns i [Personuppgifter och personer](../../platform/using/privacy-and-recommendations.md#personal-data).

### Förutsättning {#ccpa-prerequisite}

För att kunna utnyttja denna information måste du skapa det här fältet i Adobe Campaign Classic. För detta kommer du att lägga till ett booleskt fält i tabellen **[!UICONTROL Recipient]**. När ett nytt fält skapas stöds det automatiskt av API:et i Campaign.

Om du använder en anpassad mottagartabell måste du också utföra den här åtgärden.

Mer detaljerad information om hur du skapar ett nytt fält finns i [dokumentationen för schemaversionen](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>Att ändra scheman är en känslig åtgärd som bara måste utföras av expertanvändare.

1. Gå till **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Add new fields]**, välj **[!UICONTROL Recipients]** som **[!UICONTROL Document type]** och klicka på **[!UICONTROL Next]**. Mer information om hur du lägger till fält i en tabell finns i [det här avsnittet](../../configuration/using/new-field-wizard.md).

   ![](assets/privacy-ccpa-1.png)

1. Välj **[!UICONTROL SQL field]** för **[!UICONTROL Field type]**. Använd **[!UICONTROL Opt-Out for CCPA]** som etikett. Välj typen **[!UICONTROL 8-bit integer (boolean)]** och definiera följande unika **[!UICONTROL Relative path]**: @OPTOUTCCPA. Klicka på **[!UICONTROL Finish]**.

   ![](assets/privacy-ccpa-2.png)

   Detta utökar eller skapar **[!UICONTROL Recipient (cus)]**-schemat. Kontrollera att fältet har lagts till korrekt genom att klicka på det.

   ![](assets/privacy-ccpa-3.png)

1. Klicka på noden **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]** i Utforskaren. I **[!UICONTROL Recipient (nms)]**, under Allmänt paket, lägger du till ett `<input>`-element och använder, för xpath-värdet, den relativa sökvägen som definieras i steg 2. Mer information om hur du identifierar ett formulär finns i [det här avsnittet](../../configuration/using/identifying-a-form.md).

   ```
   <input  colspan="2" type="checkbox" xpath="@OPTOUTCCPA"/>
   ```

   ![](assets/privacy-ccpa-4.png)

1. Koppla från och återanslut. Följ stegen som beskrivs i nästa avsnitt för att verifiera att fältet är tillgängligt på information om en mottagare.

### Användning {#usage}

Det är den personuppgiftsansvariges ansvar att fylla i fältets värde och följa CCPA:s riktlinjer och regler för försäljning av personuppgifter.

Du kan använda flera olika metoder för att fylla i värdena:

* Använda Campaigns gränssnitt genom att redigera mottagarinformationen
* Använda API
* Via ett arbetsflöde för dataimport

Du ska sedan se till att du aldrig säljer personuppgifter, från profiler som har avanmält sig, till någon tredje part.

1. Om du vill ändra avanmälningsstatus går du till **[!UICONTROL Profiles and Target]** > **[!UICONTROL Recipients]** och väljer en mottagare. På fliken **[!UICONTROL General]** ser du fältet som konfigurerats i föregående avsnitt.

   ![](assets/privacy-ccpa-5.png)

1. Konfigurera mottagarlistan så att den översta kolumnen visas. Mer information om hur du konfigurerar listor finns i [den detaljerade dokumentationen](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

   ![](assets/privacy-ccpa-6.png)

1. Du kan klicka på kolumnen för att sortera mottagare enligt avanmälningsinformationen. Du kan också skapa ett filter så att endast mottagare som har avanmält sig visas. Mer information om hur du skapar filter finns i [det här avsnittet](../../platform/using/creating-filters.md).

   ![](assets/privacy-ccpa-7.png)
