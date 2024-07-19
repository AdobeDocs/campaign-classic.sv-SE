---
product: campaign
title: Konfigurationsfaser
description: Konfigurationsfaser
feature: Configuration
role: Data Engineer, Developer
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 2%

---

# Konfigurationsfaser{#setup-stages}

Den grundläggande principen är att infoga webbspårningstaggar på vissa sidor på webbplatsen.

Det finns två typer av taggar:

* **WEB**: den här taggen anger om sidan har besöktes,
* **TRANSACTION**: fungerar som en webbtagg, men med möjligheten att lägga till information om den genererade affärsvolymen, till exempel (transaktionsbelopp, antal inköpta objekt osv.).

Använd följande steg för att konfigurera de här taggarna:

1. Identifiera de sidor som du vill spåra och fastställa deras typ (WEB eller TRANSACTION).
1. Ta reda på vilken ytterligare information du vill samla in och utöka schemat **nms:webTrackingLog** med en beskrivning av den här informationen. Som standard kan det här schemat lagra transaktionsbelopp och antal artiklar per transaktion.
1. Skapa webbspårningstaggar. Det finns två sätt att göra detta:

   * Infoga de URL:er som motsvarar de här sidorna på din Adobe Campaign-plattform och generera och extrahera sedan de associerade webbspårningstaggarna (från noden **[!UICONTROL Campaign execution>Resources>Web tracking tags]** i klientkonsolen).
   * Skapa webbspårningstaggarna själv i läget&quot;när de skapas&quot;: URL:erna som motsvarar de här sidorna infogas automatiskt på din Adobe Campaign-plattform.

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
