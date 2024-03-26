---
product: campaign
title: Överföring till Mid-sourcing
description: Läs mer om Överför till arbetsflöden från olika källor
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 7%

---


# Överföring till Mid-sourcing{#transfer-to-mid-sourcing}



Arbetsflödena nedan installeras tillsammans med **Överföring till medelkälla** som standard. Mer information om den här modulen finns i [Installationshandbok för Campaign Classic v7](../../installation/using/mid-sourcing-deployment.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mid-sourcing (leveransräknare)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingDlv</span> <br /> </td> 
   <td> <p>Det här arbetsflödet samlar in räkningsinformation för leveranser på servern för mellanlagring. Räkningsinformation omfattar allmänna leveransindikatorer, t.ex. antalet skickade leveranser.</p> <p>Spårningsinformation som öppningar inkluderas inte.</p> <p>Den aktiveras var tionde minut som standard.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Mid-sourcing (leveransloggar)</span> <br /> </td> 
   <td> <span class="uicontrol">defaultMidSourcingLog</span> <br /> </td> 
   <td> Det här arbetsflödet samlar in leveransloggar på servern med mellanleverantörer. Den aktiveras som standard varje timme.<br /> </td> 
  </tr> 
 </tbody> 
</table>

