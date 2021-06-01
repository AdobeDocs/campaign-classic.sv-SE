---
product: campaign
title: Interaktion
description: Interaktion
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---


# Interaktion{#interaction}

Arbetsflödena som anges nedan installeras som standard med modulen **Erbjudandemotor (interaktion)**. Mer information om den här modulen finns i [avsnittet](../../interaction/using/interaction-and-offer-management.md).

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
   <td> Det här arbetsflödet uppdaterar <strong>Fullständig</strong>-aggregering för <strong>erbjudandedispositionen</strong>-kuben. Den aktiveras varje dag kl. 6.00 som standard. Den här sammanställningen fångar följande dimensioner: Kanal, leverans, marknadsföringserbjudande och datum.<br /> Erbjudandets  <strong></strong> propositionkub används sedan för att generera rapporter baserade på erbjudanden. Du kan läsa mer om kuber i <a href="../../reporting/using/about-cubes.md">det här avsnittet</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Fullständig mängdberäkning för MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Det här arbetsflödet uppdaterar <strong>Fullständig</strong>-aggregering för <strong>Message center</strong>-kuben. Den aktiveras varje dag klockan tre som standard. Den här sammanställningen fångar följande dimensioner: Typ av kanal, datum, status och händelse.<br /> Därefter används  <strong>Message </strong> Center för att generera rapporter baserade på händelser. Du kan läsa mer om kuber i <a href="../../reporting/using/about-cubes.md">det här avsnittet</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

