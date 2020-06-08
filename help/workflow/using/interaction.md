---
title: Interaktion
seo-title: Interaktion
description: Interaktion
seo-description: null
page-status-flag: never-activated
uuid: 5c8e2353-bb76-4e8d-95d7-61b6c111b6b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 1683477a-9233-4a25-b0d0-0c81051eb440
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---


# Interaktion{#interaction}

Arbetsflödena som beskrivs nedan installeras som standard med **modulen Erbjudandemotor (interaktion)** . Mer information om den här modulen finns i det här [avsnittet](../../interaction/using/interaction-and-offer-management.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Fullständig aggregerad beräkning (propositionskub)</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositioncp_full</span> <br /> </td> 
   <td> Det här arbetsflödet uppdaterar den <strong>fullständiga</strong> sammanställningen för <strong>erbjudandekuben</strong> . Den aktiveras varje dag kl. 6.00 som standard. Den här sammanställningen fångar följande dimensioner: Kanal, leverans, marknadsföringserbjudande och datum.<br /> Kuben <strong>för erbjudandeförslag</strong> används sedan för att generera rapporter baserat på erbjudanden. Du kan läsa mer om kuber i <a href="../../reporting/using/about-cubes.md">det här avsnittet</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Fullständig mängdberäkning för MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

