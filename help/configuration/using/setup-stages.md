---
title: Inställningsfaser
seo-title: Inställningsfaser
description: Inställningsfaser
seo-description: null
page-status-flag: never-activated
uuid: 4111a805-95ab-4e26-be51-2db1e5c20f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 76174374-af73-4da0-b62b-6979bca0102b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Inställningsfaser{#setup-stages}

Den grundläggande principen är att infoga webbspårningstaggar på vissa sidor på webbplatsen.

Det finns två typer av taggar:

* **WEB**: den här taggen anger om sidan har besöktes,
* **TRANSAKTION**: fungerar som en webbtagg, men med möjlighet att lägga till information om den genererade affärsvolymen, t.ex. (transaktionsbelopp, antal inköpta objekt osv.).

Använd följande steg för att konfigurera de här taggarna:

1. Identifiera de sidor som du vill spåra och fastställa deras typ (WEB eller TRANSACTION).
1. Avgör vilken ytterligare information du vill samla in och utöka schemat **nms:webTrackingLog** med en beskrivning av informationen. Som standard kan det här schemat lagra transaktionsbelopp och antal artiklar per transaktion.
1. Skapa webbspårningstaggar. Det finns två sätt att göra detta:

   * Infoga de URL:er som motsvarar de här sidorna i Adobe Campaign-plattformen och generera och extrahera sedan de associerade webbspårningstaggarna (från **[!UICONTROL Campaign execution>Resources>Web tracking tags]** noden i klientkonsolen).
   * Skapa webbspårningstaggarna själv i läget&quot;när du skapar&quot;: URL:er som motsvarar dessa sidor infogas automatiskt på din Adobe Campaign-plattform.

1. Lägg till dessa taggar statiskt eller dynamiskt på de sidor som du vill spåra.

   >[!NOTE]
   >
   >Alla taggar av WEB-typ kan läggas till som de är på webbplatsens sidor. TRANSACTION-taggar måste ändras eller läggas till dynamiskt för att den extra informationen ska kunna behållas (belopp, objekt osv.).

**Exempel**:

```
<script type="text/javascript">
var _f = "nmsWebTracking"
var _t = window.location.href.match(/.*://[^/]*(/[^?#&]*)/)[1] + "|w|" + _f
document.write("<img height='0' width='0' alt='' src='" +
window.location.protocol + "//tsupport/r/" +
Math.random().toString() + "?tagid=" + escape(_t) + "'/>")
</script>
```

