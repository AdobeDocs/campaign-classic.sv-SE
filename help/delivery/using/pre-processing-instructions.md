---
product: campaign
title: Förbearbetningsinstruktioner för spårade URL:er
description: Läs mer om förbearbetningsinstruktioner som du kan använda för att skripta URL:en för ett e-postmeddelande och fortfarande spåra den
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Monitoring
role: User, Data Engineer, Developer
exl-id: 9d3f5c74-377a-4e24-81e5-bb605f69cf8a
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 1%

---

# Instruktioner för förbehandling {#pre-processing-instructions}

Du kan använda en specifik syntax i leveransinnehållet för att lägga till instruktioner och skripta URL:en för det spårade e-postmeddelandet. &lt;%@-instruktionerna är inte JavaScript: den här syntaxen är specifik för Adobe Campaign.

De gäller endast för leveransinnehåll. Det är det enda sättet att skripta URL:en för ett e-postmeddelande och fortfarande spåra den (förutom URL-parametrar). De kan ses som en automatisk kopiera/klistra in som tillämpas under leveransanalysen innan länkarna som ska spåras identifieras.

Det finns tre typer av instruktioner:

* **[!DNL include]**: huvudsakligen för att faktorisera viss kod i alternativ, anpassningsblock, externa filer eller sidor. [Läs mer](#include)
* **[!DNL value]**: för att ge åtkomst till fält för leveransen, leveransvariabler och anpassade objekt som lästs in i leveransen. [Läs mer](#value)
* **[!DNL foreach]**: för att loopa en array som har lästs in som ett anpassat objekt. [Läs mer](#foreach)

De kan testas direkt från leveransguiden. De används i innehållsförhandsgranskningen och när du klickar på spårningsknappen för att visa en lista över URL-adresser.

## [!DNL include] {#include}

Följande exempel är bland de vanligaste:

* Inklusive spegelsidans länk:

  ```
  <%@ include view="MirrorPage" %>  
  ```

* URL för speglingssida:

  ```
  View as a <a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page.
  ```

* Oanvändbar url för avprenumeration:

  ```
  <%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>
  ```

* Andra exempel:

  ```
  <%@ include file='http://www.google.com' %>
  <%@ include file='file:///X:/france/service/test.html' %>
  <%@ include option='NmsServer_URL' %>
  ```

  Använd personaliseringsknappen i leveransguiden för att få rätt syntax.

## [!DNL value] {#value}

Den här instruktionen ger åtkomst till parametrar för leveransen som är konstanta för alla mottagare.

Syntax:

```
<%@ value object="myObject" xpath="@myField" index="1" %>
```

Var:

* **[!DNL object]**: objektets namn (exempel: leverans, provider och så vidare).
Objektet kan vara:
   * **[!DNL delivery]**: för aktuell leverans (se detaljer och begränsningar i underavsnittet nedan).
   * **[!DNL provider]**: för aktuell leveransleverantör/routning (nms:externalAccount).
   * Ett extra skriptobjekt: Om ett objekt läses in i kontexten via: **Egenskaper** > **Personalisering** > **Lägga till objekt i körningskontexten**.
   * Objekt i foreach-slingan: se [Foreach](#foreach) nedan.
* **[!DNL xpath]**: xpath of the field.
* **[!DNL index]** (valfritt): om **[!DNL object]** är en array (för extra skriptobjekt), objektindex i arrayen (börjar vid 0).

### [!DNL delivery] object {#delivery-object}

För e-postpersonalisering är leveransobjektet tillgängligt på två sätt:

* Använda JavaScript:

  ```
  <%= delivery.myField %>`.
  ```

  I JavaScript-objektet stöds inte anpassade fält för leverans. De fungerar i förhandsgranskningen, men inte i MTA eftersom MTA bara kan komma åt leveransschemat som är klart att användas.

* Med förbehandling:

  ```
  <%@ value object="delivery"
  ```


**Varning**

Om du använder följande anvisningar för leveranser som skickas via mellanleverantörer, är det anpassade fältet **@myCustomField** måste läggas till i nms:delivery-schemat på både marknadsförings- och mellanleverantörsplattformar:

```
<%@ value object="delivery" xpath="@myCustomField" %>
```

Använd följande syntax för leveransparametrar/variabler (med leveransobjektet):

```
<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>
```

### [!DNL value] i ett Javascript-avsnitt {#value-in-javascript}

Om du vill tillåta användning av &lt;%@ värde i JavaScript-avsnitt ersätts två specialobjekt med &lt;% och %>:

```
<%@ value object='startScript' %>
<%@ value object='endScript' %>
```

Exempel:

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## [!DNL foreach] {#foreach}

Den här instruktionen tillåter upprepning i en array med objekt som lästs in i leveransen för att spåra enskilda länkar som är relaterade till objekten.

Syntax:

```
<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>
```

Var:

* **[!DNL object]**: namnet på objektet som ska börja från, vanligtvis ett extra skriptobjekt, men det kan vara en leverans.
* **[!DNL xpath]** (valfritt): XPath för samlingen som ska slingas. Standardvärdet är &quot;.&quot;, vilket innebär att objektet är den array som ska upprepas.
* **[!DNL index]** (valfritt): om xpath inte är &quot;.&quot; och objektet är en array, objektindex för objektet (börjar vid 0).
* **[!DNL item]** (valfritt): namn på ett nytt objekt som är tillgängligt med värdet &lt;%@ inuti förgreningsslingan. Standard med länknamnet i schemat.

Exempel:

Läs in en array med artiklar och en relationstabell mellan mottagare och artiklar i leveransegenskaperna/personaliseringen.

Du kan visa länkar till de här artiklarna med hjälp av ett JavaScript-skript på följande sätt:

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

Med den lösningen spåras länkarna till alla artiklar utan åtskillnad. Du vet att en mottagare har klickat på en artikellänk, men du vet inte vilken artikel.

Lösningen är att

1. Läs in alla möjliga artiklar i en extra skriptmatris för leveransen - articleList[] - vilket innebär att det måste finnas ett begränsat antal möjliga artiklar.
1. Skriv en JavaScript-funktion i början av innehållet.

   ```
   <%@ value object='startScript' %>
   function displayArticle(articleId)
   {
     <%@ foreach object="articleList" item="article" %>
       if( articleId == <% value object="article" xpath="@id" %> ) 
       {
         <%@ value object='endScript' %>
           <a href="http://nl.net?a.jsp?article=<%@ value object="article" xpath="@id" %>">article</a>
         <%@ value object='startScript' %>
       } 
     <%@ end @%>
   }
   <%@ value object='endScript' %>
   ```

1. Visa artikeln genom att anropa funktionen.

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```
