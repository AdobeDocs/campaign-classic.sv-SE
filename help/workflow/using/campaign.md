---
product: campaign
title: Campaign
description: Campaign
feature: Workflows
hide: true
hidefromtoc: true
topic-tags: technical-workflows
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%

---


# Campaign{#campaign}



Arbetsflödena som anges nedan installeras som standard med modulen **Campaign** . Mer information om den här modulen finns i [avsnittet](../../campaign/using/designing-marketing-campaigns.md).

>[!CAUTION]
>
>Dessa arbetsflöden MÅSTE startas för att kampanjprocesserna ska kunna köras på kampanjnivå.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Kostnadsberäkning</span> <br /> </td> 
   <td> <span class="uicontrol">budgetMgt</span> <br /> </td> 
   <td> Det här arbetsflödet startar beräkningen av utgifts- och kostnadsrader för budgetar, planer, program, kampanjer, leveranser och aktiviteter.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Stock: Beställningar och aviseringar</span> <br /> </td> 
   <td> <span class="uicontrol">stockMgt</span> <br /> </td> 
   <td> Det här arbetsflödet startar lagerberäkning på orderraderna och hanterar varningsaviseringströsklar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Jobb för leveranser i kampanjer</span> <br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span> <br /> </td> 
   <td> Det här arbetsflödet utlöser de godkända leveranserna och påbörjar efterbearbetning av tjänsteleverantören för en extern leverans. Det skickar även godkännandemeddelanden och påminnelser.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Kampanjjobb</span> <br /> </td> 
   <td> <span class="uicontrol">operationMgt</span> <br /> </td> 
   <td> Det här arbetsflödet hanterar jobben för marknadsföringskampanjer (lanserar målinriktning, filextrahering osv.). Det skapar också arbetsflöden som är relaterade till återkommande och periodiska kampanjer.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Jobb på tjänstleverantörer</span> <br /> </td> 
   <td> <span class="uicontrol">providerMgt</span> <br /> </td> 
   <td> Det här arbetsflödet börjar bearbeta providern (e-post till routern och efterbearbetning) när leveranser har godkänts. <br /> </td> 
  </tr> 
 </tbody> 
</table>

