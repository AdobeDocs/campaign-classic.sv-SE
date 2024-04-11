---
product: campaign
title: Integrering via SOAP (serversida)
description: Integrering via SOAP (serversida)
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 3%

---

# Integrering via SOAP (server-side){#integration-via-soap-server-side}



SOAP-webbtjänster för erbjudandehantering skiljer sig från dem som vanligtvis används i Adobe Campaign. De kan nås via den interaktions-URL som beskrivs i föregående avsnitt och du kan presentera eller uppdatera erbjudanden för en viss kontakt.

## Erbjudandeförslag {#offer-proposition}

Lägg till **nms:proposition#Propose** följt av följande parametrar:

* **targetId**: primärnyckel för mottagaren (kan vara en sammansatt nyckel).
* **maxCount**: anger antalet erbjudandeförslag för kontakten.
* **kontext**: gör att du kan lägga till kontextinformation i utrymmesschemat. Om schemat som används är **nms:interaktion**, **`<empty>`** bör läggas till.
* **kategorier**: anger vilken kategori/vilka erbjudanden måste tillhöra.
* **teman**: anger det eller de teman som erbjudandena måste tillhöra.
* **uuid**: värdet för Adobe Campaign permanenta cookie (&quot;uuid230&quot;).
* **nli**: värdet för Adobe Campaign sessionscookie (&quot;nlid&quot;).
* **noProp**: använd värdet &quot;true&quot; för att inaktivera infogning av förslag.

>[!NOTE]
>
>The **targetId** och **maxCount** är obligatoriska. De andra är valfria.

SOAP-tjänsten returnerar följande parametrar som svar på frågan:

* **interactionId**: ID för interaktionen.
* **förslag**: XML-element, innehåller en lista med förslag, där vart och ett har ett eget ID och HTML.

## Erbjudandeuppdatering {#offer-update}

Lägg till **nms:interaction#UpdateStatus** till URL:en, följt av följande parametrar:

* **offert**: teckensträng, innehåller det förslags-ID som anges som utdata under ett erbjudande. Se [Erbjudandeförslag](#offer-proposition).
* **status**: string type, it specifies the new status of the offer. Möjliga värden visas i **propositionStatus** uppräkning, i **nms:vanliga** schema. Till exempel motsvarar talet 3 **Accepterad** status.
* **kontext**: XML-element, gör att du kan lägga till kontextinformation i utrymmesschemat. Om schemat som används är **nms:interaktion**, **`<empty>`** bör läggas till.

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
