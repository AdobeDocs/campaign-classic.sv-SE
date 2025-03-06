---
product: campaign
title: Interaktion
description: Interaktion
hide: true
hidefromtoc: true
feature: Workflows, Interaction, Offers
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 1%

---


# Interaktion{#interaction}



Arbetsflödena som anges nedan installeras som standard med tillägget **Erbjudandemotor (interaktion)**.

Beroende på vilken Campaign-version du har finns mer information i följande avsnitt:

![](assets/do-not-localize/v7.jpeg)[Kampanjdokumentation v7](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png)[Kampanjdokumentation v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Fullständig aggregeringsberäkning (propositionscp-kub)</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmsproposicp_full</span> <br /> </td> 
   <td> Det här arbetsflödet uppdaterar sammanställningen <strong>Fullständig</strong> för kuben <strong>Erbjudandeerbjudande</strong>. Den aktiveras varje dag kl. 6.00 som standard. Sammanställningen innehåller följande dimensioner: kanal, leverans, marknadsföringserbjudande och datum.<br /> Kuben <strong>Erbjudandeerbjudande</strong> används sedan för att generera rapporter baserat på erbjudanden. Du kan läsa mer om kuber i <a href="../../reporting/using/ac-cubes.md">det här avsnittet</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Fullständig mängdberäkning för MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Det här arbetsflödet uppdaterar sammanställningen <strong>Fullständig</strong> för kuben <strong>Meddelandecenter</strong>. Den aktiveras varje dag klockan tre som standard. Den här sammanställningen fångar följande dimensioner: Kanal, Datum, Status och Händelsetyp.<br /> Kuben <strong>Message center</strong> används sedan för att generera rapporter baserat på händelser. Du kan läsa mer om kuber i <a href="../../reporting/using/ac-cubes.md">det här avsnittet</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

