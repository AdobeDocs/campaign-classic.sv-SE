---
solution: Campaign Classic
product: campaign
title: Förbearbetningsinstruktioner för spårade URL:er
description: Läs mer om förbearbetningsinstruktioner som du kan använda för att skripta URL:en för ett e-postmeddelande och fortfarande spåra den.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 151667637a12667f5eda1590e64e01de493be9ce
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 1%

---


# Instruktioner för förbehandling {#pre-processing-instructions}

Instruktionerna för &lt;%@ är inte JavaScript. Syntaxen är specifik för Adobe Campaign.

De gäller endast för leveransinnehåll. Det är det enda sättet att skripta URL:en för ett e-postmeddelande och fortfarande spåra den (förutom URL-parametrar). De kan ses som en automatisk kopiera/klistra in som tillämpas under leveransanalysen innan länkarna som ska spåras identifieras.

Det finns tre typer av instruktioner:

* &quot;**include**&quot;: huvudsakligen för att faktorisera viss kod i alternativ, anpassningsblock, externa filer eller sidor
* &quot;**värde**&quot;: för att ge åtkomst till fält för leverans, leveransvariabler och anpassade objekt som lästs in i leveransen
* &quot;**foreach**&quot;: för att slinga en array som lästs in som ett anpassat objekt.

De kan testas direkt från leveransguiden. De används i innehållsförhandsgranskningen och när du klickar på spårningsknappen för att visa en lista över URL-adresser.

## &lt;>{#<%@-include}

Följande exempel är bland de vanligaste:

* Inklusive spegelsidans länk: `<%@ include view="MirrorPage" %>`
* URL för speglingssida: &quot;Visa som en `<a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page"`
* Oanvändbar url för avprenumeration: `<%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>`
* Andra exempel:
   * `<%@ include file='http://www.google.com' %>`
   * `<%@ include file='file:///X:/france/service/test.html' %>`
   * `<%@ include option='NmsServer_URL' %>`

Använd personaliseringsknappen i leveransguiden för att få rätt syntax.

## &lt;>{#<%@-value}

Den här instruktionen ger åtkomst till parametrar för leveransen som är konstanta för alla mottagare.

Syntax:

`<%@ value object="myObject" xpath="@myField" index="1" %>`

Var:

* &quot;object&quot;: objektets namn (exempel: leverans, provider och så vidare).
* &quot;xpath&quot;: fältets xpath.
* &quot;index&quot; (valfritt): Om &quot;object&quot; är en array (för extra skriptobjekt), objektindex i arrayen (Börjar på 0).

Objektet kan vara:

* *&quot;leverans&quot;: för aktuell leverans (se närmare uppgifter och begränsningar i underavsnittet nedan).
* &quot;provider&quot;: för aktuell leveransleverantör/routning (nms:externalAccount).
* Ett extra skriptobjekt: om ett objekt läses in i kontexten via: **Egenskaper** > **Personalisering** > **Lägg till objekt i körningskontexten**.
* Objekt i foreach-slingan: se avsnittet [Foreach](#<%@-foreach) nedan.

### &quot;delivery&quot;, objekt {#delivery-object}

För e-postpersonalisering är leveransobjektet tillgängligt på två sätt:

* I JavaScript. Exempel: `<%= delivery.myField %>`.

   I JavaScript-objektet stöds inte anpassade fält för leverans. De fungerar i förhandsgranskningen, men inte i MTA eftersom MTA bara kan komma åt leveransschemat som är klart att användas.

* Genom `<%@ value object="delivery"` förbearbetning.

För `<%@ value object="delivery" xpath="@myCustomField" %>`-instruktionen finns det en annan begränsning för leveranser som skickas via mellanleverantörer. Det anpassade fältet @myCustomField måste läggas till i nms:delivery-schemat på både marknadsförings- och medelkällplattformar.

>[!NOTE]
>
>Använd följande syntax för leveransparametrar/variabler (med leveransobjektet):
>
>`<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>`

### &lt;>{#<%@-value-in-javascript}

Om du vill tillåta att &lt;%@-värdet används i skriptavsnitt ersätts två specialobjekt med &lt;% och %>:

* `<%@ value object='startScript' %>`
* `<%@ value object='endScript' %>`

Exempel:

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## &lt;>{#<%@-foreach}

Den här instruktionen tillåter upprepning i en array med objekt som lästs in i leveransen för att spåra enskilda länkar som är relaterade till objekten.

Syntax:

`<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>`

Var:

* &quot;object&quot;: namnet på objektet som ska börja från, vanligtvis ett extra skriptobjekt, men det kan vara en leverans.
* &quot;xpath&quot; (valfritt): xpath för den samling som ska slingas. Standardvärdet är &quot;.&quot;, vilket innebär att objektet är den array som ska upprepas.
* &quot;index&quot; (valfritt): om xpath inte är &quot;.&quot; och objektet är en array, objektindex för objektet (börjar vid 0).
* &quot;objekt&quot; (valfritt): namnet på ett nytt objekt som är tillgängligt med värdet &lt;%@ inuti förgreningsslingan. Standard med länknamnet i schemat.

Exempel:

Läs in en array med artiklar och en relationstabell mellan mottagare och artiklar i leveransegenskaperna/personaliseringen.

Du kan visa länkar till dessa artiklar med ett JavaScript-skript på följande sätt:

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

1. Läs in alla möjliga artiklar i en extra skriptmatris för leveransen i förväg - articleList[] - vilket innebär att det måste finnas ett begränsat antal möjliga artiklar.
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

