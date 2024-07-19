---
product: campaign
title: Power Booster och Power Cluster
description: Power Booster och Power Cluster
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 5%

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
   <td> E-postkampanjer och utgående interaktioner <br /> </td> 
   <td> Upp till ungefär 30 miljoner e-postmeddelanden per månad<br /> </td> 
   <td> 30 till 100 miljoner e-postmeddelanden per månad<br /> </td> 
   <td> Över 100 miljoner e-postmeddelanden per månad<br /> </td> 
  </tr> 
  <tr> 
   <td> Transaktionsmeddelanden <br /> </td> 
   <td> 50 000 per timme per körningsserver <br /> </td> 
   <td> 50 000 per timme per körningsserver <br /> </td> 
   <td> 50 000 per timme per körningsserver <br /> </td> 
  </tr> 
  <tr> 
   <td> Tillgänglighet <br /> </td> 
   <td> Den för den primära databasen <br /> </td> 
   <td> 24/7 utom underhållsfönster och driftstopp för körningsinstansen <br /> </td> 
   <td> Service kan utföras dygnet runt, alla dagar, året om <br /> </td> 
  </tr> 
  <tr> 
   <td> Säkerhet <br /> </td> 
   <td> Datamarkeringen kan nås från det offentliga Internet<br /> </td> 
   <td> Datamarkeringen är isolerad från komponenter som riktas mot Internet framifrån <br /> </td> 
   <td> Datamarkeringen är isolerad från komponenter som riktas mot Internet framifrån <br /> </td> 
  </tr> 
  <tr> 
   <td> Distributionsmall<br /> </td> 
   <td> Alla på en plats (kan finnas lokalt eller i molnet)<br /> </td> 
   <td> Marknadsföring på plats med körning i molnet möjligt<br /> </td> 
   <td> Marknadsföring lokalt med körning i molnet; körning i olika geografiska områden är möjlig<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rekommendationer {#recommendations}

* En körningsinstans måste dedikeras till en tjänst. Du kan inte installera ett paket för en tjänst som du inte har prenumererat på. Om du till exempel prenumererar på alternativet **Power Booster** för tjänsten **Message Center** kan du bara installera paketet **[!UICONTROL Execution of transactional messages]** på den dedikerade körningsinstansen. Kontrollera licensavtalet.
* Eftersom dedikerade instanser (eller kluster) är Adobe Campaign-instanser är rekommendationerna samma som för en huvudinstans. Mer information finns i [det här dokumentet](../../production/using/foreword.md).
* Kontakta Adobe Campaign Professional Services om du vill konfigurera instansen från en databas-/maskinvarukomponentvy.
