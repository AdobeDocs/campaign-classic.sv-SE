---
product: campaign
title: LINJEKanal
description: LINJEKanal
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 8%

---


# LINJEKanal{#line-channel}



Arbetsflödena nedan installeras tillsammans med **LINE-kanal** som standard. Mer information om modulen finns i [section](../../delivery/using/line-channel.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Uppdatering av åtkomsttoken för LINE V2</span> <br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> Det här arbetsflödet uppdaterar åtkomsttoken till LINE V2.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ta bort blockerade LINE-användare</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> Det här arbetsflödet säkerställer att LINE V2-användarnas data tas bort efter att de har blockerat LINE-kontot i 180 dagar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MID till LineUserID-migrering</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span> <br /> </td> 
   <td> Det här arbetsflödet genererar användar-ID:t för LINE V2 för migrering från LINE V1 till LINE V2.<br /> </td> 
  </tr> 
 </tbody> 
</table>

