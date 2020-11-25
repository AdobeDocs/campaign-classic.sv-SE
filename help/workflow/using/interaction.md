---
solution: Campaign Classic
product: campaign
title: Interaktion
description: Interaktion
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: affc541c480ad7e618120fe90270841add06b711
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---


# Interaktion{#interaction}

Arbetsflödena som beskrivs nedan installeras som standard med **modulen Erbjudandemotor (interaktion)** . For more on this module, refer to this [section](../../interaction/using/interaction-and-offer-management.md).

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
   <td> Det här arbetsflödet uppdaterar den <strong>fullständiga</strong> sammanställningen för <strong>erbjudandekuben</strong> . Den aktiveras varje dag kl. 6.00 som standard. Den här sammanställningen fångar följande dimensioner: Kanal, leverans, marknadsföringserbjudande och datum.<br /> Buffertkub <strong>för</strong> erbjudanden används sedan för att generera rapporter baserade på erbjudanden. Du kan läsa mer om kuber i <a href="../../reporting/using/about-cubes.md">det här avsnittet</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Fullständig mängdberäkning för MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Det här arbetsflödet uppdaterar den <strong>fullständiga</strong> sammanställningen för <strong>meddelandecenterkuben</strong> . Den aktiveras varje dag klockan tre som standard. Den här sammanställningen fångar följande dimensioner: Typ av kanal, datum, status och händelse.<br /> Kuben för <strong>meddelandecentret</strong> används sedan för att generera rapporter baserade på händelser. Du kan läsa mer om kuber i <a href="../../reporting/using/about-cubes.md">det här avsnittet</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

