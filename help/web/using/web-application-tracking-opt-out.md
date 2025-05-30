---
product: campaign
title: Välj att inte delta i spårning i webbapplikation
description: Välj att inte delta i spårning i webbapplikation
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Web Apps
exl-id: 4bff6b55-3335-433e-a2ff-5d8c83e8f0d3
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 2%

---

# Välj att inte delta i spårning i webbapplikation{#web-application-tracking-opt-out}



Med Adobe Campaign kan du sluta spåra webbbeteenden för slutanvändare som avanmäler sig från beteendespårning via cookies eller webbfyrar. Funktionen inkluderar möjligheten att visa en banderoll för att ge slutanvändaren det alternativet. Du kan lägga till dessa banderoller i webbprogram eller landningssidor.

Om en slutanvändare väljer bort beteendespårning via cookies eller webbfyrar, överförs den informationen till Adobe Campaign spårningsserver med JavaScript API:er. Observera att vissa jurisdiktioner kan kräva att kunden gör en anmälan till slutanvändarna innan en avanmälan kan erbjudas (eller har andra juridiska krav), och det är kundens ansvar att följa tillämpliga lagar.

>[!NOTE]
>
>När du använder skript ska du alltid följa riktlinjerna som beskrivs i [checklistan för säkerhet och sekretess](https://helpx.adobe.com/se/campaign/kb/acc-security.html#dev).

## Konfigurera banderollen {#configuring-the-banner-}

Banderollen måste konfigureras för att kunna visas i webbprogram eller på landningssidor.

Adobe Campaign levereras med en exempelbanderoll som du måste anpassa efter dina behov. Den här banderollversionen visas som ett anpassningsblock i mappen för innehållsmodellen. Se [den här sidan](../../delivery/using/personalization-blocks.md).

>[!IMPORTANT]
>
>Om du vill skapa en egen banderoll måste du anpassa den färdiga banderollen.

Om du vill aktivera banderollen måste du konfigurera webbprogrammets egenskaper. Se avsnittet [Designa ett webbprogram](designing-a-web-application.md).

Om spårning av webbsidor är aktiverat kan du antingen ha:

* Ingen banner.
* Konfigurera banderollen manuellt på varje sida: markera det här alternativet och markera banderollen på varje sida i sidegenskaperna.

  ![](assets/pageproperties.png)

* Lägg automatiskt till banderollen på alla sidor: markera banderollen direkt i webbprogrammets egenskaper.

  ![](assets/optoutconfig.png)

>[!NOTE]
>
>Det finns ett kompatibilitetsläge tillgängligt för v5-webbprogrammet med samma beteende.

Standardbanderollen har följande struktur:

```
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
      
```

Du måste ersätta **Infoga meddelandet här** med blocket som innehåller din spårningsinformation. Ersättningen ska utföras i det nya anpassningsblocket som hör till avanvisningsbanderollen.

Banderollen levereras med en specifik CSS. Du kan dock skriva över formaten när du skapar och konfigurerar en webbsida. Se [den här sidan](content-editor-interface.md).

## Ange avanmälnings-cookie med API {#setting-the-opt-out-cookie-using-api}

Adobe Campaign levereras med API:er som gör att du kan hantera cookie-värdet och hämta användarinställningar.

Cookie-namnet är **acoptout**. De gemensamma värdena är:

* 0: användaren har tillåtit webbspårning (standardvärde)
* 1: användaren har förbjuden webbspårning
* null: användaren har inte valt, men webbspårning tillåts eftersom det är standardvärdet

De tillgängliga API:erna på klientsidan för att anpassa banderollen är:

* **NL.ClientWebTracking.allow()**: Anger cookie-värdet för avanmälan så att webbspårning tillåts. Webbspårning är tillåtet som standard.
* **NL.ClientWebTracking.forbid()**: Anger att cookie-värdet för avanmälan ska förhindra webbspårning. Webbspårning kräver att användarindata tillåts.
* **NL.ClientWebTracking.closeOptOutBanner(bannerDomElt)**: Stänger cookie-banderollen för avanmälan när användaren har klickat på knappen Acceptera eller Avvisa. (under klickhändelsebubblingsfasen)

  bannerDomElt {DOMElement} är rot-DOM-elementet för den cookie-banderoll som måste tas bort

* **NL.ClientWebTracking.hasUserPrefs()**: Returnerar true om användaren har valt sina inställningar för webbspårning.
* **NL.ClientWebTracking.getUserPrefs()**: Returnerar cookie-värdet för avanmälan som definierar användarens inställningar.

Om du måste skriva en JSSP är API:er på serversidan tillgängliga:

* **NL.ServerWebTracking.generateOptOutBanner(escapeJs)**: Skapar koden för den avanmälningsbanderoll som ska infogas på JSSP-sidan

  **escapeJs {Boolean}**: true när den genererade koden måste escape-konverteras för att kunna användas i JavaScript.

  Den returnerar HTML till den avanmälningsbanderollkod som måste skrivas ut på sidan.

* **NL.ServerWebTracking._displayOptOutBanner()**

  Returnerar &quot;true&quot; om avanmälningsbanderollen ska visas efter att en avanmälningsbanderoll har valts av administratören

  Den här koden anropas när administratören redan har valt att använda bannern för avanmälan av webbspårning.

  Banderollen bör visas om användaren ännu inte har valt att spåras eller inte.

* **NL.ServerWebTracking.renderOptOutBanner(escapeJs)**

  Återger markeringen för avanmälningsbanderollen genom att infoga den på JSSP-sidan. Den anropas som i Jssp mellan &lt;% %>

  **escapeJs {Boolean}**: true när den genererade koden måste escape-konverteras för att kunna användas i JavaScript

JSSP-exempel:

```
<%@ page import="/nl/core/shared/nl.js" %>
<!doctype html>
<%
NL.require('/nl/core/shared/webTracking.js');
NL.client.require('/nl/core/shared/webTracking.js');
%>
<html>
<head>
<%==NL.client.deps()%>
</head>

<body>

<!-- TEST USING SERVER API IN JSSP -->
<% 
var webTracking = new NL.ServerWebTracking(request, 'optOutBanner');
webTracking.renderOptOutBanner();
%>

<!-- TEST USING SERVER API IN A SCRIPT -->
<!--
<% 
var webTracking = new NL.ServerWebTracking(request, 'optOutBanner');
%>
<script>var el = document.createElement('div'); el.innerHTML =  "<% webTracking.renderOptOutBanner(true); %>";document.body.appendChild(el);</script>
-->

<!-- TEST OF THE CLIENT API -->
<!--
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
-->
</body>
</html>
```
