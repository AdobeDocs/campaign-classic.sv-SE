---
title: Campaign
seo-title: Campaign
description: Campaign
seo-description: null
page-status-flag: never-activated
uuid: 9e5cf203-e5e9-4383-b628-aa6f131491e0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: de892ec4-c378-4b22-875e-aa9345f82552
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0d687b57f75b432547baef57021b716a8ce37ad4

---


# Campaign{#campaign}

Arbetsflödena som beskrivs nedan installeras som standard med **Campaign** -modulen. Mer information om den här modulen finns i det här [avsnittet](../../campaign/using/designing-marketing-campaigns.md).

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
   <td> <span class="uicontrol">Kostnadsberäkning</span><br /> </td> 
   <td> <span class="uicontrol">budgetMgt</span><br /> </td> 
   <td> Det här arbetsflödet startar beräkningen av utgifts- och kostnadsrader för budgetar, planer, program, kampanjer, leveranser och uppgifter.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Stock: Beställningar och varningar</span><br /> </td> 
   <td> <span class="uicontrol">stockMgt</span><br /> </td> 
   <td> Det här arbetsflödet startar lagerberäkning på orderraderna och hanterar varningsaviseringströsklar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Jobb för leveranser i kampanjer</span><br /> </td> 
   <td> <span class="uicontrol">deliveryMgt</span><br /> </td> 
   <td> Det här arbetsflödet utlöser de godkända leveranserna och påbörjar efterbearbetning av tjänsteleverantören för en extern leverans. Dessutom skickas meddelanden och påminnelser om godkännande.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Kampanjjobb</span><br /> </td> 
   <td> <span class="uicontrol">operationMgt</span><br /> </td> 
   <td> Det här arbetsflödet hanterar jobben för marknadsföringskampanjer (lanserar målinriktning, filextrahering osv.). Det skapar också arbetsflöden för återkommande och periodiska kampanjer.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Jobb för tjänsteleverantörer</span><br /> </td> 
   <td> <span class="uicontrol">providerMgt</span><br /> </td> 
   <td> Det här arbetsflödet börjar bearbeta providern (e-post till routern och efterbearbetning) när leveranser har godkänts. <br /> </td> 
  </tr> 
 </tbody> 
</table>

