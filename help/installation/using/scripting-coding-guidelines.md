---
product: campaign
title: Riktlinjer för skript och kodning
description: Läs mer om riktlinjerna som du bör följa när du utvecklar i Adobe Campaign (arbetsflöden, JavaScript, JSSP osv.).
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 1f96c3df-0ef2-4f5f-9c36-988cbcc0769f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 5%

---

# Riktlinjer för skript och kodning {#scripting-coding-guidelines}

![](../../assets/v7-only.svg)

## Skript

Mer information finns i [Kampanj-JSAPI-dokumentation](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

Om du skriptar med arbetsflöde, webbprogram, jssp, ska du följa dessa rutiner:

* Undvik att använda SQL-satser så mycket du kan.

* Om du behöver det använder du parametriserade funktioner (förbered-sats) i stället för strängsammanfogning.

   Felaktig praxis:

   ```
   sqlGetInt( "select iRecipientId from NmsRecipient where sEmail ='" + request.getParameter('email') +  "'  limit 1" )
   ```

   God praxis:

   ```
   sqlGetInt( "select iRecipientId from NmsRecipient where sEmail = $(sz) limit 1", request.getParameter('email'));
   ```

   >[!IMPORTANT]
   >
   >sqlSelect stöder inte den här funktionen, så du måste använda frågefunktionen i klassen DBEngine:

   ```
   var cnx = application.getConnection()
   var stmt = cnx.query("SELECT sFirstName, sLastName FROM NmsRecipient where sEmail = $(sz)", request.getParameter('email'))
   for each(var row in stmt) logInfo(row[0] + " : " + row[1])
   cnx.dispose()
   ```

För att undvika SQL-injektioner måste SQL-funktioner läggas till i tillåtelselista för att användas i Adobe Campaign. När de har lagts till i tillåtelselista blir de synliga för dina operatorer i uttrycksredigeraren. Se [den här sidan](../../configuration/using/adding-additional-sql-functions.md).

>[!IMPORTANT]
>
>Om du använder en version som är äldre än 8140 kan alternativet **XtkPassUnknownSQLFunactionsToRDBMS** anges till 1. Om du vill skydda databasen tar du bort det här alternativet (eller anger värdet 0).

Om du använder användarindata för att skapa filter i frågor eller SQL-satser måste du alltid undvika dem (se [Kampanj-JSAPI-dokumentation](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) - Dataskydd: funktioner). De här funktionerna är:

* NL.XML.escape(data)
* NL.SQL.escape(data)
* NL.JS.escape(data)
* NL.XML.escapeAttribute(data)

## Skydda din nya datamodell

### Mappbas

Se följande sidor:

* [Egenskaper för mappåtkomst](../../platform/using/access-management.md)
* [Länkad mapp](../../configuration/using/configuration.md#linked-folder)

### Namngivna rättigheter

Förutom den mappbaserade säkerhetsmodellen kan du använda namngivna rättigheter för att begränsa operatoråtgärder:

* Du kan lägga till systemfilter (sysFilter) för att förhindra att data läses/skrivs (se [den här sidan](../../configuration/using/filtering-schemas.md)).

   ```
   <sysFilter name="writeAccess">    
       <condition enabledIf="hasNamedRight('myNewRole')=false" expr="FALSE"/>  
   </sysFilter>
   ```

* Du kan även skydda vissa åtgärder (SOAP-metod) som definieras i scheman. Ange bara åtkomstattributet med motsvarande namngiven rättighet som värde.

   ```
   <method name="grantVIPAccess" access="myNewRole">
       <parameters>
   ...
       </parameters>
   </method>
   ```

   Mer information finns på [den här sidan](../../configuration/using/implementing-soap-methods.md).

>[!IMPORTANT]
>
>Du kan använda namngivna rättigheter i kommandonoden i ett navigeringsträd. Det ger en bättre användarupplevelse men ger inget skydd (använd bara klientsidan för att dölja/inaktivera dem). Du måste använda åtkomstattributet.

### Spilltabell

Om du behöver skydda konfidentiella data (del av ett schema) beroende på operatörens åtkomstnivå, ska du inte dölja dem i formulärdefinitionen (enabledIf/visibleIf-villkor).

Den fullständiga enheten läses in av skärmen och du kan även visa dem i kolumndefinitionen. För att göra detta måste du skapa en flödestabell. Se [den här sidan](../../configuration/using/examples-of-schemas-edition.md#overflow-table).

## Lägga till bildtexter i webbprogram

Det är god praxis att lägga till en captcha på offentliga landningssidor/prenumerationssidor. Tyvärr är det inte så enkelt att lägga till en captcha på DCE-sidor (Digital Content Editor). Vi visar hur du lägger till en v5-captcha eller en Google reCAPTCHA.

Det allmänna sättet att lägga till en captcha i DCE är att skapa ett personaliseringsblock som enkelt kan inkluderas i sidinnehållet. Du måste lägga till en **Script**-aktivitet och en **Test**.

### Personaliseringsblock

1. Gå till **[!UICONTROL Resources]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Personalization blocks]** och skapa en ny.

1. Använd innehållstypen **[!UICONTROL Web application]** och markera **[!UICONTROL Visible in the customization menus]**.

   För mer information om detta hittar du i [det här avsnittet](../../delivery/using/personalization-blocks.md).

   Här är ett exempel på en **kampanjbeskrivning**:

   ```javascript
   <%
   var captchaID = CaptchaIDGen();
   %>
   <img src="/nms/jsp/captcha.jsp?captchaID=<%=captchaID%>&width=200&height=50&minWordSize=8&maxWordSize=8"/>
   <input id="captchaValue" name="captchaValue" <%= String(ctx.vars.captchaValid) === "false" ? class="ui-state-error" : "" %>>
   <input type="hidden" name="captchaID" value="<%=captchaID%>"/>
   <%
   if( serverForm.isInputErroneous("captchaValue") ) {
   %>
   <script type="text/javascript"> 
   $("#captchaValue").addClass("ui-state-error")
   </script>
   <%
   }
   %>
   ```

   * Rader 1 till 6 genererar alla indata som behövs.
   * Rader 7 till slutet hanterar fel.
   * Med rad 4 kan du ändra storleken på den inmatade gråa rutan (bredd/höjd) och längden på det genererade ordet (minWordSize/maxWordSize).
   * Innan du använder Google reCAPTCHA måste du registrera dig på Google och skapa en ny reCAPTCHA-webbplats.

      `<div class="g-recaptcha" data-sitekey="YOUR_SITE_KEY"></div>`
   Du bör kunna inaktivera valideringsknappen, men eftersom vi inte har någon standardknapp/länk är det bättre att göra det i själva HTML-koden. Mer information finns på [den här sidan](https://developers.google.com/recaptcha/).

### Uppdatera ditt webbprogram

1. Kom åt egenskaperna för webbprogrammet och lägg till en boolesk variabel med namnet **captchaValid**.

   ![](assets/scripting-captcha.png)

1. Lägg till en **[!UICONTROL Script]** och en **[!UICONTROL Test]** mellan den sista sidan och aktiviteten **[!UICONTROL Storage]**.

   Koppla grenen **[!UICONTROL True]** till **[!UICONTROL Storage]** och den andra till sidan som ska ha captcha.

   ![](assets/scripting-captcha2.png)

1. Redigera villkoret för grenen True med `"[vars/captchaValid]"` är lika med True.

   ![](assets/scripting-captcha3.png)

1. Redigera aktiviteten **[!UICONTROL Script]**. Innehållet beror på den valda captcha-motorn.

1. Slutligen kan du lägga till ditt personliga block på sidan: hänvisar till [den här sidan](../../web/using/editing-content.md).

   ![](assets/scripting-captcha4.png)

   ![](assets/scripting-captcha5.png)

>[!IMPORTANT]
>
>För reCAPTCHA-integrering måste du lägga till JavaScript på klientsidan i HTML (i `<head>...</head>`):
>
>`<script src="https://www.google.com/recaptcha/api.js" async defer></script>`

### Campaign captcha

```javascript
var captchaID = request.getParameter("captchaID");
var captchaValue = request.getParameter("captchaValue");
  
if( !CaptchaValidate(captchaID, captchaValue) ) {
  serverForm.logInputError("captchaValue",
                           "The characters you typed for the captcha must match the image ones.",
                           "captchaValue")
  ctx.vars.captchaValid = false
}
else
  ctx.vars.captchaValid = true
```

Rad 6: kan du skicka vilket felmeddelande som helst.

### Google recaptcha

Se [den officiella dokumentationen](https://developers.google.com/recaptcha/docs/verify).

```javascript
ctx.vars.captchaValid = false
var gReCaptchaResponse = request.getParameter("g-recaptcha-response");
  
// Call reCaptcha API to validate it
var req = new HttpClientRequest("https://www.google.com/recaptcha/api/siteverify")
req.method = "POST"
req.header["Content-Type"] = "application/x-www-form-urlencoded"
req.body = "secret=YOUR_SECRET_HERE&response=" + encodeURIComponent(gReCaptchaResponse)
req.execute()
var response = req.response
if( response.code == 200 ) {
  captchaRes = JSON.parse(response.body.toString(response.codePage));
  ctx.vars.captchaValid = captchaRes.success
}
  
if( ctx.vars.captchaValid == false ) {
  serverForm.logInputError("reCaptcha",
                           "Please validate the captcha",
                           "reCaptcha")
  logInfo("reCaptcha not validated")
}
```

Om du vill använda JSON.parse måste du inkludera&quot;shared/json2.js&quot; i din webApp:

![](assets/scripting-captcha6.png)

Sedan build 8797 måste du lägga till den i tillåtelselista i filen serverConf för att kunna använda URL:en för verifierings-API genom att lägga till den i noden urlPermission:

`<url dnsSuffix="www.google.com" urlRegEx="https://www.google.com/recaptcha/api/siteverify"/>`
