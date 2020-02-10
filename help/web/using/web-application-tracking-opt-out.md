---
title: Avanmäl dig till spårning av webbprogram
seo-title: Avanmäl dig till spårning av webbprogram
description: Avanmäl dig till spårning av webbprogram
seo-description: null
page-status-flag: never-activated
uuid: c9b9eee2-a5be-4378-b2d7-53ed7121eae8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 8f413002-bd32-426f-88b9-44cefae68593
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Avanmäl dig till spårning av webbprogram{#web-application-tracking-opt-out}

Med Adobe Campaign kan ni sluta spåra webbbeteenden för slutanvändare som avanmäler sig från beteendespårning via cookies eller webbfyrar. Funktionen innefattar möjligheten att visa en banderoll för att ge slutanvändaren det alternativet. kan du lägga till dessa banners i webbapplikationer eller landningssidor.

Om en slutanvändare väljer bort beteendespårning via cookies eller webbfyrar, överförs den informationen till Adobe Campaign-spårningsservern med JavaScript-API:er. Observera att vissa jurisdiktioner kan kräva att kunden gör en anmälan till slutanvändarna innan en avanmälan kan erbjudas (eller har andra juridiska krav), och det är kundens ansvar att följa tillämpliga lagar.

## Konfigurera banderollen {#configuring-the-banner-}

Banderollen måste konfigureras för att kunna visas i webbprogram eller på landningssidor.

Adobe Campaign levereras med en exempelbanderoll som ni måste anpassa efter era behov. Den här banderollversionen visas som ett anpassningsblock i mappen för innehållsmodellen. Se [den här sidan](../../delivery/using/personalization-blocks.md).

>[!CAUTION]
>
>Om du vill skapa en egen banderoll måste du anpassa den färdiga banderollen.

Om du vill aktivera banderollen måste du konfigurera webbprogrammets egenskaper. Se avsnittet [Designa ett webbprogram](../../web/using/designing-a-web-application.md) .

Om spårning av webbsidor är aktiverat kan du antingen ha:

* Ingen banderoll.
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

Du måste ersätta **Please insert your message here** with the block containing your tracking information. Ersättningen ska utföras i det nya anpassningsblocket som hör till avanvisningsbanderollen.

Banderollen levereras med en specifik CSS. Du kan dock skriva över formaten när du skapar och konfigurerar en webbsida. Se [den här sidan](../../web/using/content-editor-interface.md).

## Ange avanmälnings-cookie med API {#setting-the-opt-out-cookie-using-api}

Adobe Campaign levereras med API:er som gör att du kan hantera cookie-värdet och hämta användarinställningar.

Cookie-namnet är **acoptout**. De gemensamma värdena är:

* 0: användaren har tillåtit webbspårning (standardvärde)
* 1: användaren har förbjuden webbspårning
* null: användaren har inte valt, men webbspårning tillåts eftersom det är standardvärdet

De tillgängliga API:erna på klientsidan för att anpassa banderollen är:

* **NL.ClientWebTracking.allow()**: Ställer in värdet för avanmälningscookie så att webbspårning tillåts. Webbspårning är tillåtet som standard.
* **NL.ClientWebTracking.forbid()**: Ställer in värdet för cookie för avanmälan så att webbarklänkning förbjuds. Webbspårning kräver att användarindata är förbjudna.
* **NL.ClientWebTracking.closeOptOutBanner(bannerDomElt)**: Stänger bannern för att avanmäla sig efter att användaren har klickat på knappen Godkänn eller Avvisa. (under klickhändelsebubblingsfasen)

   bannerDomElt {DOMElement} är rotelementet DOM för den cookie-banderoll som behöver tas bort

* **NL.ClientWebTracking.hasUserPrefs()**: Returnerar true om användaren har valt sina inställningar för webbspårning.
* **NL.ClientWebTracking.getUserPrefs()**: Returnerar värdet för den cookie som definierar användarens inställningar.

Om du måste skriva en JSSP är API:er på serversidan tillgängliga:

* **NL.ServerWebTracking.generateOptOutBanner(escapeJs)**: Skapar koden för den avanmälningsbanderoll som ska infogas på JSSP-sidan

   **escapeJs {Boolean}**: true när den genererade koden måste escape-konverteras för att användas i JavaScript.

   Den returnerar HTML-koden för avanmälningsbanderollkoden som måste skrivas ut på sidan.

* **NL.ServerWebTracking._displayOptOutBanner()**

   Returnerar true om avanmälningsbanderollen ska visas efter att en avanmälningsbanderoll har valts av administratören

   Den här koden anropas när administratören redan har valt att använda bannern för avanmälan av webbspårning.

   Banderollen bör visas om användaren ännu inte har valt att spåras eller inte.

* **NL.ServerWebTracking.renderOptOutBanner(escapeJs)**

   Återger markeringen för avanmälningsbanderollen genom att infoga den på JSSP-sidan. Den anropas som i Jssp mellan &lt;% %>

   **escapeJs {Boolean}**: true när den genererade koden måste escape-konverteras för att användas i JavaScript

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

