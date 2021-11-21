---
product: campaign
title: Interaktion
description: Interaktion
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 6%

---


# Interaktion{#interaction}

![](../../assets/common.svg)

Arbetsflödena nedan installeras tillsammans med **Erbjudandemotor (interaktion)** tillägg som standard.

Beroende på vilken Campaign-version du har finns mer information i följande avsnitt:

![](assets/do-not-localize/v7.jpeg)[  Dokumentation om Campaign v7](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png)[  Dokumentation om Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html)


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
   <td> Det här arbetsflödet uppdaterar <strong>Fullständig</strong> aggregat för <strong>Erbjudandeförslag</strong> kub. Den aktiveras varje dag kl. 6.00 som standard. Den här sammanställningen fångar följande dimensioner: Kanal, leverans, marknadsföringserbjudande och datum.<br /> The <strong>Erbjudandeförslag</strong> kub används sedan för att generera rapporter baserat på erbjudanden. Du kan lära dig mer om kuber i <a href="../../reporting/using/about-cubes.md">det här avsnittet</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">Fullständig mängdberäkning för MessageCenter</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> Det här arbetsflödet uppdaterar <strong>Fullständig</strong> aggregat för <strong>Meddelandecenter</strong> kub. Den aktiveras varje dag klockan tre som standard. Den här sammanställningen fångar följande dimensioner: Typ av kanal, datum, status och händelse.<br /> The <strong>Meddelandecenter</strong> kub används sedan för att generera rapporter baserat på händelser. Du kan lära dig mer om kuber i <a href="../../reporting/using/about-cubes.md">det här avsnittet</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

