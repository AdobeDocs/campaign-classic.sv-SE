---
product: campaign
title: Integrering via SOAP (serversida)
description: Integrering via SOAP (serversida)
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
source-git-commit: b8a6a0db27826309456c285c08d4f1d85de70283
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 3%

---

# Integrering via SOAP (serversida){#integration-via-soap-server-side}



SOAP webbtjänster för hantering av erbjudanden skiljer sig från dem som vanligtvis används i Adobe Campaign. De kan nås via den interaktions-URL som beskrivs i föregående avsnitt och du kan presentera eller uppdatera erbjudanden för en viss kontakt.

## Erbjudandeförslag {#offer-proposition}

Lägg till kommandot **nms:proposition#Propose** följt av följande parametrar för ett erbjudande via SOAP:

* **targetId**: primärnyckel för mottagaren (kan vara en sammansatt nyckel).
* **maxCount**: anger antalet erbjudandeförslag för kontakten.
* **kontext**: gör att du kan lägga till kontextinformation i utrymmesschemat. Om schemat som används är **nms:interaction** bör **`<empty>`** läggas till.
* **kategorier**: anger den eller de kategorier som erbjudandena måste tillhöra.
* **teman**: anger teman som erbjudandena måste tillhöra.
* **uid**: värdet för Adobe Campaign permanenta cookie (&quot;uuid230&quot;).
* **nli**: värdet för Adobe Campaign sessionscookie (&quot;nlid&quot;).
* **noProp**: använd värdet true om du vill inaktivera infogning av förslag.

>[!NOTE]
>
>Inställningarna **targetId** och **maxCount** är obligatoriska. De andra är valfria.

Som svar på frågan returnerar SOAP-tjänsten följande parametrar:

* **interactionId**: ID för interaktionen.
* **propositioner**: XML-elementet innehåller en lista med förslag, där vart och ett har ett eget ID och en HTML-representation.

## Erbjudandeuppdatering {#offer-update}

Lägg till kommandot **nms:interaction#UpdateStatus** i URL:en, följt av följande parametrar:

* **proposition**: teckensträng, den innehåller det förslag-ID som angetts som utdata under ett erbjudande. Se [Erbjudandeerbjudande](#offer-proposition).
* **status**: strängtyp, den anger erbjudandets nya status. Möjliga värden visas i uppräkningen **propositionStatus** i schemat **nms:common**. Till exempel motsvarar talet 3 statusen **Accepterad**.
* **context**: Med XML-element kan du lägga till kontextinformation i utrymmesschemat. Om schemat som används är **nms:interaction** bör **`<empty>`** läggas till.

## Exempel på hur du använder ett SOAP-samtal {#example-using-a-soap-call}

Nedan finns ett exempel på kod för ett SOAP-samtal.

Här är ett exempel på URL:

```
http://<urlOfYourJSSP>?env=liveRcp&sp=<nameSpaceOfferSpace>&t=<targetID>
```

```
<%
  var env = request.getUTF8Parameter("env");
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
      for each( var propHtml in props.proposition.*.htmlSource )
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
