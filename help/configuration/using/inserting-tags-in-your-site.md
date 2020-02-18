---
title: Infoga taggar på platsen
seo-title: Infoga taggar på platsen
description: Infoga taggar på platsen
seo-description: null
page-status-flag: never-activated
uuid: e5e4a431-2093-4d5a-acd2-0040b6ce3519
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 57988b00-62cc-43d3-a2eb-bfed5bff7dc1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Infoga taggar på platsen{#inserting-tags-in-your-site}

## Enkel metod {#simple-method}

Den här metoden består av att skicka ett HTTP-anrop till omdirigeringsservern genom att infoga en **`<img>`** HTML-tagg i HTML-källkoden för den webbsida som du vill spåra.

>[!IMPORTANT]
>
>Den här metoden använder de cookies som skickas av webbläsaren för att identifiera mottagaren, och är inte helt tillförlitlig.

**Exempel**:

```
<img height='0' width='0' alt='' src='https://localhost/r/12343?tagid=home'
```

Den infogade taggen kontaktar omdirigeringsservern.

![](assets/d_ncs_integration_webtracking_structure2.png)

När du definierar en sida som ska spåras i konsolen kan du generera ett exempel på en webbspårningstagg som kopieras och klistras in i webbsidans källkod.

När du använder taggar av typen TRANSACTION måste du emellertid ändra exempeltaggen med JavaScript för att kunna infoga transaktionsinformationen (mängd, antal objekt) och all information som definieras av ett tilläggsschema.

### Statisk infogning av taggar {#static-insertion-of-tags}

Om du vill infoga statiska taggar kopierar och klistrar du bara in de taggar som genererats av konsolen eller som konstruerats manuellt i webbsidans källa.

**Exempel**: infogning av en webbspårningstagg på en sida som visar ett formulär.

```
<html>
  <...>
  <body>
  <script>
      document.write("<img height='0' width='0' alt='' src='https://localhost/r/" + Math.random().toString() + "?tagid=home'>");
    </script>
    <noscript>
     <img height='0' width='0' alt='' src='https://localhost/r/?tagid=home'>
    </noscript>
    <h1>My site</h1>
    <form action="http://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

Infogning av en webbspårningstagg av typen TRANSACTION på bekräftelsesidan (&quot;amount.md&quot;).

```
<html>
  <body>
    <script>
      function getURLparam(name) 
      {
        var m = location.search.match new RegExp("[?&]" + name + "=([^&]+)"));
        return m ? unescape(m[1]) : "";
      }
 
       var params = "https://localhost/r/" + Math.random().toString() + "?tagid=amount&amount="
                      +getURLparam("amount")+"&article="+getURLparam("quantity");
       document.write("<img height='0' width='0' src='"+params+"'/>");
    </script>

    <h1>Approval confirmation</h1>
  </body>
</html>
```

### Dynamisk generering av webbspårningstaggar {#dynamic-generation-of-web-tracking-tags}

När dina webbsidor genereras dynamiskt kan du lägga till spårningstaggen vid sidgenerering.

**Exempel**: Webbspårning har lagts till i JSP:er.

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <img height='0' width='0' alt='' src='https://localhost/r/<%=new Random().nextInt()%>?tagid=home'>
    <h1>My site</h1>
    <form action="https://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <%  
      String strParams = new Random().nextInt() + "?tagid=amount";
      strParams += "&amount="+request.getParameter("amount");
      strParams += "&article="+request.getParameter("quantity");
    %>
    <img height='0' width='0' alt=''
     src='http://localhost/r/<%=strParams%>'>
    <h1>Approval confirmation</h1>
    </body>
</html>
```

## Optimummetod {#optimum-method-}

Om du vill styra informationen som skickas till omdirigeringsservern är det mest tillförlitliga sättet att utföra HTTP-frågan synkront själv med ett sidgenereringsspråk.

Den URL som du skapar måste följa de syntaxregler som definieras i [webbspårningstaggen: definition](../../configuration/using/web-tracking-tag--definition.md).

![](assets/d_ncs_integration_webtracking_structure3.png)

>[!NOTE]
>
>Omdirigering och webbspårning använder cookies, och det är viktigt att webbservern som utför det synkrona HTTP-anropet finns i samma domän som omdirigeringsservern. De olika HTTP-utbytena måste förmedla cookies av typen id, uuid och uuid230.

**Exempel**: Dynamisk generering i Java, med mottagarautentisering med sitt kontonummer.

```
[...]
  // Recipient account, amount and articles
  String strAccount = request.getParameter("account");
  String strAmount = request.getParameter("amount");
  String strArticle = request.getParameter("article");

  StringBuffer strCookies = new StringBuffer();
  String strSetCookie = null;

  // Get cookies from client request
  Cookie[] cookies = request.getCookies();
  for(int i=0; i< cookies.length; i++ )
  {
    Cookie c = cookies[i];
    String strName = c.getName();
    if( strName.equals("id") || strName.equals("uuid") || strName.equals("uuid230") )
      // Helper function to add cookies in string
      AddCookie(strCookies, c);
  }
  // Now perform a synchronous HTTP request to inform redirection server
  // Add a tagid in auto-discover mode, and a default jobId to use (in hexa)
  StringBuffer strURL = new StringBuffer("https://www.adobe.com/r/a?tagid=cmd_page%7Ct&jobid=27EE");
  if( strAccount != null )
    AddParameter(strURL, "rcpid", "saccount="+strAccount);
  if( strAmount != null )
    AddParameter(strURL, "amount", strAmount);
  if( strArticle != null )
    AddParameter(strURL, "article", strArticle);
  
  URL url = new URL(strURL.toString());
  HttpURLConnection connection = (HttpURLConnection)url.openConnection();
  // Add the client cookies
  if( strCookies.length() > 0 )
    connection.setRequestProperty("Cookie", strCookies.toString());

  int errcode = connection.getResponseCode();

  // Now add the Adobe Campaign cookies if the server returned one :
  if( errcode == 200 )
  {
    strSetCookie = connection.getHeaderField("Set-Cookie");
    if( strSetCookie != null && strSetCookie.length() > 0 )
      response.addHeader("Set-Cookie", strSetCookie);
  }
  [...]
```

