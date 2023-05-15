---
product: campaign
title: Power Booster och Power Cluster
description: Power Booster och Power Cluster
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 6%

---

# Power Booster och Power Cluster{#power-booster-and-power-cluster}



## Översikt {#overview}

Adobe Campaign tillhandahåller två uppsättningar färdiga arkitektoniska alternativ för att dimensionera driftsättningen:

* **Power Booster**

   Det här alternativet har stöd för ytterligare en körningsinstans som är fristående från den primära programinstansen i Adobe Campaign. Dedikerade körningsinstanser kan fjärrhanteras eller hanteras av en tredje part. När det är implementerat hanteras e-postkörning, spårning, speglingssidor och studsmeddelanden oberoende av de centrala programfunktionerna.

* **Power Cluster**

   Det här alternativet ger stöd för 2 till N klustrade körningsinstanser som är frikopplade från den primära Adobe Campaign-programinstansen i förhållande till ett visst program. Kluster kan fjärrhanteras, distribueras och hanteras av tredje part. Förutom fördelarna med processisolering möjliggör Adobe Campaign Power Cluster-alternativet redundans och utskalning av strategier med hjälp av maskinvara för förenklad utveckling av SLA eller prestanda.

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

* En körningsinstans måste dedikeras till en tjänst. Du kan inte installera ett paket för en tjänst som du inte har prenumererat på. Om du till exempel prenumererar på **Power Booster** för **Meddelandecenter** kan du endast installera **[!UICONTROL Execution of transactional messages]** paket på den dedikerade körningsinstansen. Kontrollera licensavtalet.
* Eftersom dedikerade instanser (eller kluster) är Adobe Campaign-instanser är rekommendationerna samma som för en huvudinstans. Mer information finns i [det här dokumentet](../../production/using/foreword.md).
* Kontakta Adobe Campaign Professional Services om du vill konfigurera instansen från en databas-/maskinvarukomponentvy.
