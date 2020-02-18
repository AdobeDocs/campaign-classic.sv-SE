---
title: Power Booster och Power Cluster
seo-title: Power Booster och Power Cluster
description: Power Booster och Power Cluster
seo-description: null
page-status-flag: never-activated
uuid: 4d23ed42-a368-4bd6-afaf-48452e253d19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 715d2b69-5b47-4890-8b7d-1dc0a0d4ead8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c25e2a4f2280cdcc61e0522f8235149410b5dacf

---


# Power Booster och Power Cluster{#power-booster-and-power-cluster}

## Översikt {#overview}

Adobe Campaign innehåller två uppsättningar förpaketerade arkitektoniska alternativ för att dimensionera driftsättningen:

* **Power Booster**

   Det här alternativet ger stöd för en enda ytterligare körningsinstans som inte är kopplad till den primära programinstansen för Adobe Campaign. Dedikerade körningsinstanser kan fjärrhanteras eller hanteras av en tredje part. När det är implementerat hanteras e-postkörning, spårning, speglingssidor och studsmeddelanden oberoende av de centrala programfunktionerna.

* **Power Cluster**

   Det här alternativet ger stöd för 2 till N-klustrade körningsinstanser som inte är kopplade till den primära programinstansen för Adobe Campaign i förhållande till ett visst program. Kluster kan fjärrhanteras, distribueras och hanteras av tredje part. Förutom fördelarna med processisolering kan man med Adobe Campaign Power Cluster-alternativet få redundans och utbyggbara strategier med hjälp av maskinvara för förenklad utveckling av SLA eller prestanda.

![](assets/architectural_options_diagram.png)

## Berättigade ansökningar {#eligible-applications}

Alternativen Power Booster och Power Cluster kan användas av följande program:

* Campaign
* Leverans
* Meddelandecenter

## Matris för arkitektoniska rekommendationer {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Standardarkitektur</strong><br /> </td> 
   <td> <strong>Power Booster</strong><br /> </td> 
   <td> <strong>Power Cluster</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> E-postkampanjer och utgående interaktioner<br /> </td> 
   <td> Upp till ungefär 30 miljoner e-postmeddelanden per månad<br /> </td> 
   <td> 30 till 100 miljoner e-postmeddelanden per månad<br /> </td> 
   <td> Över 100 miljoner e-postmeddelanden per månad<br /> </td> 
  </tr> 
  <tr> 
   <td> Transaktionsmeddelanden<br /> </td> 
   <td> 50 000 per timme per körningsserver<br /> </td> 
   <td> 50 000 per timme per körningsserver<br /> </td> 
   <td> 50 000 per timme per körningsserver<br /> </td> 
  </tr> 
  <tr> 
   <td> Tillgänglighet<br /> </td> 
   <td> Den primära databasens placering<br /> </td> 
   <td> 24/7 utom underhållsfönster och driftstopp för körningsinstansen<br /> </td> 
   <td> Service 24/7/365 möjlig<br /> </td> 
  </tr> 
  <tr> 
   <td> Säkerhet<br /> </td> 
   <td> Datamarknaden är potentiellt tillgänglig via internet<br /> </td> 
   <td> Datamarknaden är isolerad från frontalkomponenter som riktas mot Internet<br /> </td> 
   <td> Datamarknaden är isolerad från frontalkomponenter som riktas mot Internet<br /> </td> 
  </tr> 
  <tr> 
   <td> Distributionsmall<br /> </td> 
   <td> Alla på en plats (kan finnas lokalt eller i molnet)<br /> </td> 
   <td> Marknadsföring på plats med körning i molnet möjligt<br /> </td> 
   <td> Marknadsföring lokalt med exekvering i molnet. exekvering i olika geografiska områden<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rekommendationer {#recommendations}

* En körningsinstans måste dedikeras till en tjänst. Du kan inte installera ett paket för en tjänst som du inte har prenumererat på. Om du till exempel prenumererar på alternativet **Power Booster** för tjänsten **Message Center** , kan du bara installera paketet på den dedikerade körningsinstansen **[!UICONTROL Execution of transactional messages]** . Kontrollera licensavtalet.
* Eftersom dedikerade instanser (eller kluster) är Adobe Campaign-instanser är rekommendationerna samma som för en huvudinstans. Mer information finns i [det här dokumentet](../../production/using/foreword.md).
* Kontakta Adobe Campaign Professional Services om du vill konfigurera instansen från en databas-/maskinvarukomponentvy.

