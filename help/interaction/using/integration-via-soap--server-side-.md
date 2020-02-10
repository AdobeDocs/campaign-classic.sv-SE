---
title: Integrering via SOAP (serversida)
seo-title: Integrering via SOAP (serversida)
description: Integrering via SOAP (serversida)
seo-description: null
page-status-flag: never-activated
uuid: 678371c5-4246-4886-994e-30dbbc70f14a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: unitary-interactions
discoiquuid: 477a2c31-0403-4db1-a372-c75dca58380d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Integrering via SOAP (serversida){#integration-via-soap-server-side}

SOAP-webbtjänster för erbjudandehantering skiljer sig från dem som vanligtvis används i Adobe Campaign. De kan nås via den interaktions-URL som beskrivs i föregående avsnitt och du kan presentera eller uppdatera erbjudanden för en viss kontakt.

## Erbjudandeförslag {#offer-proposition}

Lägg till kommandot **nms:proposition#Propose** följt av följande parametrar för ett erbjudande via SOAP:

* **targetId**: mottagarens primärnyckel (kan vara en sammansatt nyckel).
* **maxCount**: Anger antalet erbjudandeförslag för kontakten.
* **kontext**: I kan du lägga till kontextinformation i utrymmesschemat. Om schemat som används är **nms:interaction**, **`<empty>`** bör läggas till.
* **kategorier**: anger den eller de kategorier som erbjudandena måste tillhöra.
* **teman**: anger temat som erbjudandet eller erbjudandena måste tillhöra.
* **uuid**: värdet på den permanenta cookie-filen för Adobe Campaign (&quot;uuid230&quot;).
* **nli**: värdet på Adobe Campaign-sessionens cookie (&quot;nlid&quot;).
* **noProp**: Använd värdet &quot;true&quot; för att inaktivera infogning av förslag.

>[!NOTE]
>
>Inställningarna **targetId** och **maxCount** är obligatoriska. De andra är valfria.

SOAP-tjänsten returnerar följande parametrar som svar på frågan:

* **interactionId**: ID för interaktionen.
* **förslag**: XML-element, innehåller listan med förslag, där vart och ett har ett eget ID och en HTML-representation.

## Erbjudandeuppdatering {#offer-update}

Lägg till kommandot **nms:interaction#UpdateStatus** i URL:en, följt av följande parametrar:

* **Föreslå**: teckensträng, innehåller det förslags-ID som anges som utdata under ett erbjudande. Se [Erbjudandeförslag](#offer-proposition).
* **status**: strängtyp, anger erbjudandets nya status. Möjliga värden visas i uppräkningen **propositionStatus** i schemat **nms:common** . Till exempel motsvarar siffran 3 statusen **Godkänd** .
* **kontext**: Med XML-element kan du lägga till kontextinformation i utrymmesschemat. Om schemat som används är **nms:interaction**, **`<empty>`** bör läggas till.

## Exempel på hur du använder ett SOAP-anrop {#example-using-a-soap-call}

Här är ett exempel på kod för ett SOAP-anrop:

```
<%
  var space = request.parameters.sp
  var cnx = new HttpSoapConnection(
    "https://" + request.serverName + ":" + request.serverPort + "/interaction/" + env + "/" + space,
    "utf-8",
    HttpSoapConnection.SOAP_12)
  var session = new SoapService(cnx, "nms:interaction")
  var action = request.parameters.a
  if( action == undefined )
    action = 'propose'

  try
  {
    switch( action )
    {
    case "update":
      var proposition = request.parameters.p
      var status      = request.parameters.st
      session.addMethod("UpdateStatus", "nms:interaction#UpdateStatus",
       ["proposition", "string",
        "status",      "string",
        "context",     "NLElement"],
       [])
      session.UpdateStatus(proposition, status, <undef/>)
      var redirect = request.parameters.r
      if( redirect != undefined )
        response.sendRedirect(redirect)
      break;

    case "propose":
      var count = request.parameters.n
      var target = request.parameters.t
      var categorie = request.parameters.c
      var theme = request.parameters.th
      var layout = request.parameters.l
      if( count == undefined )
        count = 1
      session.addMethod("Propose", "nms:proposition#Propose",
       ["targetId",      "string",
        "maxCount",      "string",
         "categories",    "string",
         "themes",        "string",
        "context",       "NLElement"],
       ["interactionId", "string",
        "propositions",  "NLElement"])
      response.setContentType("text/html")
      var result = session.Propose(target, count, category, theme, <empty/>)
      var props = result[1]
  %><table><tr><%
      for each( var propHtml in props.proposition.*.mdSource )
      {
        %><td><%=propHtml%></td><%
      }
  %></tr></table><%
      break;
    }
  }
  catch( e )
  {
  }
  %>
```
