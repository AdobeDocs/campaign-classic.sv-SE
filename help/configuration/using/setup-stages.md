---
product: campaign
title: Konfigurationsfaser
description: Konfigurationsfaser
feature: Configuration
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 5%

---

# Konfigurationsfaser{#setup-stages}

Den grundläggande principen är att infoga webbspårningstaggar på vissa sidor på webbplatsen.

Det finns två typer av taggar:

* **WEB**: den här taggen talar om för dig om sidan har besökts,
* **TRANSAKTION**: fungerar som en webbtagg, men med möjlighet att lägga till information om den genererade affärsvolymen, t.ex. (transaktionsbelopp, antal inköpta objekt osv.).

Använd följande steg för att konfigurera de här taggarna:

1. Identifiera de sidor som du vill spåra och fastställa deras typ (WEB eller TRANSACTION).
1. Bestäm vilken ytterligare information du vill samla in och utöka **nms:webTrackingLog** schema med en beskrivning av informationen. Som standard kan det här schemat lagra transaktionsbelopp och antal artiklar per transaktion.
1. Skapa webbspårningstaggar. Det finns två sätt att göra detta:

   * Infoga de URL:er som motsvarar dessa sidor på din Adobe Campaign-plattform och generera och extrahera sedan de associerade webbspårningstaggarna (från **[!UICONTROL Campaign execution>Resources>Web tracking tags]** klientkonsolens nod).
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
